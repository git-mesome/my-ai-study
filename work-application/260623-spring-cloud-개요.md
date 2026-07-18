# Spring Cloud 개요

> MSA 작업 중 발견, 2026-06-23

## Spring Cloud란?

분산 환경(여러 서버에 서비스가 나뉘어 있는 MSA 구조)에서 발생하는 인프라 레벨 문제를 Spring 생태계 안에서 해결해주는 라이브러리 묶음.

## MSA에서 생기는 문제 → Spring Cloud 솔루션

| 문제 | Spring Cloud 솔루션 |
|------|---------------------|
| 서비스가 서로를 어떻게 찾지? | **Spring Cloud Eureka** (Service Discovery) |
| 동기 요청 시 장애 대응 | **Resilience4j** (Circuit Breaker) |
| API 진입점 단일화 | **Spring Cloud Gateway** |
| 서비스마다 설정이 다른데? | **Spring Cloud Config** |
| 분산 환경에서 요청 추적 | **Micrometer + Zipkin** (Distributed Tracing) |

## 주의: Spring Cloud 영역이 아닌 것

아웃박스 패턴, 보상 트랜잭션(Saga)은 **애플리케이션 레벨 패턴**으로 직접 구현해야 한다.

```
[비즈니스 패턴] 아웃박스, Saga, 보상 트랜잭션  ← 직접 구현
[인프라 패턴]   Service Discovery, Gateway, Config  ← Spring Cloud
```

## 다음 학습 후보

- Eureka 동작 원리 + 코드
- Spring Cloud Gateway 설정 실습
- Resilience4j 서킷 브레이커 구현
