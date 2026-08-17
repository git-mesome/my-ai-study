# 앞으로 공부할 주제

- 벡터 DB (Vector Database)
- 파인튜닝 (Fine-tuning)
- GraphQL

## 면접 대비 - Java 심화 (주 사용 언어)

- JVM 구조 — 클래스 로더, 런타임 데이터 영역(힙/스택/메소드 영역/PC 레지스터)
- GC(가비지 컬렉션) 동작 방식 — Young/Old 영역, Serial/Parallel/G1 GC 차이
- == vs equals(), hashCode()/equals() 오버라이드 규칙
- HashMap 내부 동작 — 해시 충돌 처리, 리사이징, HashMap vs TreeMap vs LinkedHashMap
- ArrayList vs LinkedList 차이와 시간복잡도
- String vs StringBuilder vs StringBuffer, String Pool
- 제네릭(Generics)과 타입 소거(Type Erasure)
- Checked vs Unchecked Exception, try-with-resources
- 멀티스레딩 — Thread vs Runnable, synchronized, volatile, ExecutorService/스레드풀
- ConcurrentHashMap 등 동시성 컬렉션
- 인터페이스 vs 추상 클래스, default 메서드
- 람다 표현식과 Stream API
- static 키워드 의미와 활용
- 객체지향 4대 특성(캡슐화/상속/다형성/추상화)을 실무 코드로 설명하는 법

## 면접 대비 - 리눅스

- 프로세스 vs 스레드 차이, 멀티프로세스/멀티스레드 장단점
- 프로세스 상태(생성/실행/대기/종료)와 컨텍스트 스위칭
- 시그널(SIGKILL vs SIGTERM 차이, 시그널 핸들링)
- 파일 디스크립터 개념, 열린 파일 디스크립터 확인 방법(lsof)
- 하드 링크 vs 심볼릭 링크
- 파일 권한(rwx), umask, chmod/chown 숫자 표기 의미
- inode란 무엇인가, 파일 시스템 구조
- 프로세스 확인/관리 명령어 — ps, top/htop, kill, nice/renice
- 메모리 관리 — 가상 메모리, swap, OOM killer 동작 원리
- 디스크 사용량 확인 — df vs du 차이
- 네트워크 상태 확인 — netstat/ss, 포트 점유 프로세스 찾기
- 로그 확인 — journalctl, /var/log, dmesg
- 셸 스크립트 기초 — 변수, 조건문, 반복문, 파이프(|)와 리다이렉션(>, >>, 2>&1)
- 표준 입출력/에러 스트림(stdin/stdout/stderr) 개념
- grep/find/sed/awk 텍스트 처리 기본 사용법
- 크론(cron)으로 주기적 작업 예약
- 부팅 과정과 init 시스템 — systemd 기본 개념, systemctl 사용법
- 사용자/그룹 관리, sudo 권한 구조
- 방화벽 기초 — iptables/firewalld 개념
- 좀비 프로세스 vs 고아 프로세스 차이
- 로드 애버리지(load average) 의미와 해석

## AX Product Engineer 지원 대비 (사전지식 보강용)

- 하이브리드 검색 — 텍스트 검색(BM25/Elasticsearch) + 벡터 kNN 병행, RRF(Reciprocal Rank Fusion)로 순위 병합
- 리랭킹(Reranking) — Jina reranker 등으로 검색 상위 후보 재평가
- LangGraph — 에이전트 오케스트레이션 프레임워크 (CrewAI/AutoGen과 비교), Neo4j 실습
- MCP 서버 직접 구현 — 클라이언트 사용 경험(GitHub/Playwright/Notion)은 있으나 서버 제작 경험 없음
- forward-auth 패턴 — 중앙집중형 인가(Authorization) 구조, 서비스별 auth 분산 방식과 비교
