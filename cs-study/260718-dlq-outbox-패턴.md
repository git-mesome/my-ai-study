# DLQ & Outbox 패턴 — 장애 대응 기초

> 장애 대응 패턴 학습 중 발견, 2026-07-18

## 문제 상황

MSA에서 서비스가 "DB에 데이터 저장"과 "이벤트 발행"을 각각 별도 시스템(DB, 메시지 브로커)에 순차적으로 수행하면 정합성이 깨질 수 있다.

```
OrderService: db.save(order) → kafka.send(event)
```

- DB save 성공 + kafka send 실패 → 주문은 있는데 이벤트가 안 나감
- kafka send 성공 + DB 트랜잭션 롤백 → 이벤트는 나갔는데 주문이 없음

DLQ와 Outbox는 각각 이 파이프라인의 **아웃바운드(발행)** / **인바운드(처리)** 쪽 장애를 다루는 패턴이다.

## Outbox 패턴 — 발행 신뢰성 보장

DB 트랜잭션 안에서 "비즈니스 데이터 저장"과 "발행할 이벤트 저장"을 같은 트랜잭션으로 묶는다.

```sql
BEGIN TRANSACTION;
  INSERT INTO orders (id, status) VALUES (1, 'CREATED');
  INSERT INTO outbox (event_id, event_type, payload, status)
    VALUES ('uuid-1', 'ORDER_CREATED', '{"orderId":1,"status":"CREATED"}', 'PENDING');
COMMIT;
```

- **Relay**(별도 프로세스, 또는 Debezium 같은 CDC 툴)가 `PENDING` row를 읽어 카프카로 발행하고 `PUBLISHED`로 변경
- relay는 payload를 그대로 발행할 뿐, orders 테이블과 값을 재검증하지 않는다 — 같은 트랜잭션에서 쓴 값이라 애초에 다를 수 없는 게 이 패턴의 핵심
- relay 발행 자체가 반복 실패하면 그 row는 `FAILED`로 격리 (DLQ와 같은 아이디어, 위치만 DB 테이블)

## DLQ — 처리 신뢰성 보장 (컨슈머 쪽)

카프카 컨슈머가 메시지 처리 중 예외가 나면:

1. 에러 핸들러가 설정된 backoff로 **같은 메시지를 N번 재시도**
2. N번 다 실패 → `DeadLetterPublishingRecoverer`가 메시지를 `{원본토픽}.DLT`로 그대로 발행
3. 그제서야 원본 파티션의 offset 커밋 → 다음 메시지로 진행

offset이 순서대로만 커밋되는 카프카 특성상, DLQ 없이 무한 재시도만 하면 뒤에 있는 멀쩡한 메시지까지 전부 막힌다. DLQ는 "막힌 메시지를 옆으로 치워서 뒤엣것들을 흐르게" 하는 역할.

```java
@Bean
public DefaultErrorHandler errorHandler(KafkaTemplate<Object, Object> template) {
    var recoverer = new DeadLetterPublishingRecoverer(template);
    var backOff = new FixedBackOff(1000L, 3); // 1초 간격, 3번 재시도
    return new DefaultErrorHandler(recoverer, backOff);
}
```

- **poison pill**: 재시도해도 절대 성공 못 하는 메시지 (예: JSON 파싱 자체가 깨짐)
- DLQ 도착 = 자동 재시도가 이미 끝난 상태. 카프카는 스스로 재발행하지 않는다 — 재처리(replay)는 별도로 만든 컨슈머/도구가 담당해야 하는 애플리케이션 로직

## 재처리(Replay) 시 멱등성 필요

DLQ 메시지를 replay하면 이미 부분 처리된 메시지가 다시 처리되어 중복이 발생할 수 있다. → **멱등 컨슈머(Idempotent Consumer)** 패턴으로 방어.

```sql
CREATE TABLE processed_events (
  event_id VARCHAR PRIMARY KEY,  -- outbox에서 발행 시 부여한 UUID
  processed_at TIMESTAMP
);
```

```java
try {
    processedEventRepository.insert(eventId); // PK 충돌 시 예외
    // 실제 비즈니스 로직 수행
} catch (DuplicateKeyException e) {
    log.info("이미 처리한 이벤트, skip: {}", eventId);
}
```

`orderId`가 아니라 **이벤트 자체의 고유 ID**를 키로 써야 한다 — 같은 주문에 생성/취소/변경 등 여러 이벤트가 있을 수 있기 때문.

## 전체 흐름

```
Outbox(DB 트랜잭션과 이벤트 발행 원자성 보장)
  → Relay가 비동기 발행
  → 컨슈머 처리 실패 시 재시도
  → 그래도 실패하면 DLQ로 격리 (뒤 메시지 안 막히게)
  → 사람 또는 자동화가 원인 해결 후 replay
  → replay는 멱등 컨슈머로 방어 (중복 처리 차단)
```

## 다음 학습 후보

- Kafka consumer의 backoff 전략 (Fixed vs Exponential) 실습
- DLQ 모니터링/알림 구성 (컨슈머 랙, 메시지 적체 알람)
- Saga / 보상 트랜잭션과 Outbox의 관계
