# AI & CS 용어 사전

학습하면서 정리한 용어 모음. 공부할수록 채워나가기.

---

## ㄱ

### 가드레일 엔지니어링 (Guardrail Engineering)
- 에이전트가 위험하거나 의도치 않은 행동을 못 하게 막는 안전장치 설계
- 입력/출력/행동(Action)/구조적 가드레일로 구분, 프롬프트 텍스트 지침은 약한 가드레일, 훅·권한체크 같은 코드 레벨 강제가 강한 가드레일
- 상세: [툴 & 가드레일 엔지니어링](./260817-툴-가드레일-엔지니어링.md)

### 그래프 엔지니어링 (GraphRAG)
- 문서에서 개체·관계를 추출해 지식그래프로 구성하고 벡터 검색과 결합하는 RAG 방식
- 여러 단계를 거쳐야 답이 나오는 질문(multi-hop reasoning)에 강함, 구축 비용이 큼
- 상세: [그래프 엔지니어링](./260817-그래프엔지니어링-graphrag.md)

---

## ㄴ

### 네임서버 (Nameserver, NS)
- 특정 도메인의 실제 DNS 레코드(A, CNAME 등)를 들고 답해주는 서버
- "네임서버를 바꾼다" = 그 도메인의 주소록 관리 권한을 위임한다는 뜻

### NAT (Network Address Translation)
- 여러 사설 IP를 공인 IP 하나로 변환해 내보내는 기술
- 외부(방화벽 등)에서는 NAT 뒤 여러 사용자가 공인 IP 하나로만 보임

### NGFW (Next-Generation Firewall, 차세대 방화벽)
- 패킷 필터링 + Stateful + L7/WAF를 통합하고, 애플리케이션 인식·IPS·SSL 복호화까지 더한 방화벽
- 포트 기반이 아니라 트래픽 내용/애플리케이션 기반으로 정교하게 제어

---

## ㄷ

### 딥러닝 (Deep Learning)
- 신경망(Neural Network)을 여러 층으로 쌓아 학습하는 머신러닝 기법
- LLM의 기반 기술

### DNS (Domain Name System)
- 도메인 이름(google.com)을 IP 주소로 변환해주는 시스템
- 로컬 캐시 → 리졸버 → 루트 DNS → TLD DNS → 네임서버 순으로 조회

---

## ㄹ

### LLM (Large Language Model, 대규모 언어 모델)
- 대량의 텍스트 데이터로 학습한 AI 모델
- 문장을 이해하고 생성하는 데 특화
- 예: GPT-4, Claude, Gemini

### 라우팅 (Routing)
- 패킷이 출발지에서 목적지까지 갈 최적 경로를 찾아 전달하는 3계층(네트워크 계층) 핵심 역할
- 목적지가 다른 네트워크면 게이트웨이(라우터)로, 라우팅 테이블을 보고 다음 홉으로 전달

### RAG (Retrieval-Augmented Generation, 검색 증강 생성)
- 문서를 청크로 쪼개 임베딩 후 벡터DB에 저장 → 질문이 오면 유사한 청크를 검색(Retrieval) → LLM 프롬프트에 삽입(Augmented) → 답변 생성(Generation)
- 벡터 검색만 쓰면 관계 추론(multi-hop)에 약함 → [그래프 엔지니어링](./260817-그래프엔지니어링-graphrag.md)이 보완
- 상세: [RAG 파이프라인](./260807-rag-파이프라인.md)

### 루프 엔지니어링 (Loop Engineering)
- 에이전트의 "모델 호출 → 행동 → 관찰" 반복 루프를 언제/어떻게 멈출지 설계
- 상세: [루프 엔지니어링](./260807-루프엔지니어링.md)

### 리졸버 (Resolver)
- DNS 조회(resolution)를 실제로 수행하는 서버, 보통 ISP가 제공 (또는 8.8.8.8 등 퍼블릭 DNS)

---

## ㅁ

### MAC 주소 (Media Access Control Address)
- 랜카드에 고유하게 박힌 물리 주소, 2계층(데이터링크)에서 사용
- 라우터를 거칠 때마다 값이 바뀜 (IP는 목적지까지 고정, MAC은 매 구간 다음 장비로 바뀜)

### MCP (Model Context Protocol)
- 에이전트가 외부 도구/데이터에 접근하도록 도구 정의를 표준 프로토콜로 노출하는 규격
- [툴 엔지니어링](./260817-툴-가드레일-엔지니어링.md) 산출물을 배포하는 형태 중 하나

### 멀티에이전트 오케스트레이션 (Multi-Agent Orchestration)
- 역할을 나눠 여러 에이전트가 협업하게 설계 — Orchestrator-Worker, Pipeline, Fan-out/Fan-in, Debate/Voting, Hierarchical 패턴
- 프레임워크: LangGraph(그래프 기반 흐름 제어), CrewAI(역할 기반), AutoGen(대화 기반)
- 상세: [멀티에이전트 오케스트레이션](./260817-멀티에이전트-오케스트레이션.md)

### 메모리 엔지니어링 (Memory Engineering)
- 에이전트가 세션 안/세션 간 정보를 어떻게 저장하고 언제 불러올지 설계
- MemGPT(2023)가 컨텍스트=RAM, 외부 저장소=디스크 비유를 제시
- 상세: [메모리 엔지니어링](./260817-메모리엔지니어링.md)

---

## ㅂ

### 방화벽 (Firewall)
- 규칙에 따라 네트워크 트래픽을 허용/차단하는 장비·소프트웨어
- 패킷 필터링(3~4계층) → Stateful(연결 상태 추적) → L7/WAF(응용계층 내용 검사) 순으로 정교해짐

### 비정규화 (Denormalization)
- 조회 성능을 위해 일부러 데이터 중복을 허용해 JOIN을 줄이는 설계
- 정규화가 과하면 JOIN이 늘어나 조회 성능이 떨어지는 트레이드오프를 완화

---

## ㅅ

### 서브넷 마스크 (Subnet Mask)
- IP 주소를 네트워크 부분/호스트 부분으로 나누는 값 (`/24` = CIDR 표기)
- 내 IP와 목적지 IP의 네트워크 부분이 같은지 비교해 같은 네트워크인지 판단

### 세션 (Session)
- 하네스(고정된 틀)를 한 번 실행시킨 인스턴스. 세션이 도구를 써서 스스로 판단·행동하면 그 세션을 "에이전트"라 부름
- `/clear`는 세션(RAM)만 초기화, 메모리 파일(디스크)은 그대로 남음

### SRE / Self-Healing / Agent-Native SRE
- SRE: 서비스 안정성을 엔지니어링 문제로 다루는 방법론 (모니터링, 온콜, 에러 버짓 등)
- Self-Healing: 사람 개입 없이 시스템이 스스로 복구 (규칙 기반 자동화)
- Agent-Native SRE: 장애 감지→진단→조치까지 LLM 에이전트가 스스로 수행하는 접근
- 상세: [Agent-Native SRE/Self-Healing](./260817-agent-native-sre-self-healing.md)

---

## ㅇ

### 에이전트 (Agent)
- 도구를 써서 스스로 판단하고 행동하는 패턴/행동 관점의 용어 (세션의 정체성이 아니라 동작 방식을 설명)

### ACID
- 트랜잭션이 지켜야 할 4가지 성질: 원자성(Atomicity), 일관성(Consistency), 격리성(Isolation), 지속성(Durability)
- 상세: [DBMS 기초 정리](../cs-study/260816-dbms-기초-면접정리.md)

### ARP (Address Resolution Protocol)
- 같은 네트워크 안에서 IP 주소를 MAC 주소로 변환 (브로드캐스트로 질의 → 유니캐스트로 응답)
- ARP 스푸핑: 가짜 응답으로 중간자 공격(MITM)

### 이더넷 (Ethernet)
- 유선 LAN의 2계층 표준 — 프레임 형식, MAC 주소 체계, 케이블 신호 규격을 정의. 대표 장비는 스위치

### 이벨 엔지니어링 (Eval Engineering)
- LLM/에이전트 시스템의 성능을 어떻게 측정·검증할지 설계
- 자동 메트릭, LLM-as-Judge(다른 LLM이 채점), 사람 평가를 조합
- 상세: [이벨 엔지니어링](./260817-이벨엔지니어링.md)

### ISP (Internet Service Provider)
- 인터넷 회선 자체를 제공하는 통신사 (KT, SKT 등). Cloudflare 같은 부가 서비스와는 역할이 다름

---

## ㅈ

### 정규화 (Normalization)
- 데이터 중복을 줄이고 갱신/삽입/삭제 이상을 방지하기 위해 테이블을 분리하는 설계 (1NF~3NF)
- 상세: [DBMS 기초 정리](../cs-study/260816-dbms-기초-면접정리.md)

### JOIN
- 두 테이블을 공통 컬럼 기준으로 합쳐 조회 — INNER(교집합), LEFT(왼쪽 전체), RIGHT, FULL OUTER(합집합), CROSS, SELF

---

## ㅋ

### 컨텍스트 엔지니어링 (Context Engineering)
- 한정된 컨텍스트 윈도우 안에 이번 턴에 모델한테 정확히 뭘 넣을지 설계
- 압축 기법: 슬라이딩 윈도우, 요약 압축, 도구 결과 절삭, 외부 저장+선택적 불러오기
- 상세: [하네스 & 컨텍스트 엔지니어링](./260807-하네스-컨텍스트엔지니어링.md)

### CIDR (Classless Inter-Domain Routing)
- 클래스(A/B/C) 고정 크기 대신 원하는 크기로 자유롭게 네트워크 대역을 나누는 표기법 (`/24` 등)
- `/32`는 호스트 1개만 지정 (방화벽 규칙 등에서 단일 IP 지정 시 사용)

---

## ㅌ

### 토큰 (Token)
- LLM이 텍스트를 처리하는 단위
- 단어 또는 단어의 일부분
- 한국어는 영어보다 토큰 수가 더 많이 필요한 경우가 많음

### 툴 엔지니어링 (Tool Engineering)
- 에이전트가 실제 행동을 하도록 도구(함수)의 이름·설명·파라미터 스키마를 설계하는 일
- 설명이 모호하면 에이전트가 잘못된 도구를 고르거나 잘못된 값을 채움
- 상세: [툴 & 가드레일 엔지니어링](./260817-툴-가드레일-엔지니어링.md)

### 트랜잭션 격리 수준 (Isolation Level) / MVCC
- Read Uncommitted < Read Committed < Repeatable Read < Serializable — 낮을수록 빠르지만 Dirty/Non-Repeatable/Phantom Read 위험
- MVCC(Multi-Version Concurrency Control): 값을 덮어쓰지 않고 버전을 새로 만들어 읽기가 쓰기를 막지 않게 하는 구현 방식
- 상세: [DBMS 기초 정리](../cs-study/260816-dbms-기초-면접정리.md)

### TLD (Top-Level Domain)
- 도메인 이름의 가장 끝부분(`.com`, `.io`, `.kr`). gTLD/ccTLD/sTLD로 구분

---

## ㅍ

### 프롬프트 (Prompt)
- LLM에게 전달하는 입력 텍스트
- 질문, 지시, 맥락 등을 포함

### 프롬프트 엔지니어링 (Prompt Engineering)
- LLM이 원하는 결과를 내도록 프롬프트를 설계하는 기술
- 시스템 프롬프트뿐 아니라 사용자 프롬프트, few-shot 예시, 도구 결과 포맷팅 등 여러 지점에 걸쳐 적용되는 가로지르는 기법

---

## ㅎ

### 하네스 (Harness)
- LLM 모델을 감싸서 실제로 동작하게 만드는 소프트웨어 전체 (시스템 프롬프트, 도구 실행 루프, 권한 체크, 메모리 시스템)
- Claude Code 자체가 하나의 하네스
- 상세: [하네스 & 컨텍스트 엔지니어링](./260807-하네스-컨텍스트엔지니어링.md)

### 훅 (Hook)
- 도구 실행 직전/직후 등 특정 이벤트 시점에 하네스가 실행하는 검사 스크립트 (`.claude/settings.json`에 등록)
- 모델의 판단과 무관하게 코드 레벨에서 강제되는 구조적 가드레일 — PreToolUse 훅이 실행을 물리적으로 차단 가능
- 상세: [툴 & 가드레일 엔지니어링](./260817-툴-가드레일-엔지니어링.md)

### RDBMS vs NoSQL
- RDBMS: 스키마 고정, 테이블 간 관계(FK)와 JOIN, ACID 강하게 보장 (MySQL, PostgreSQL 등)
- NoSQL: 스키마 유연, 관계 대신 중복 저장, 수평 확장에 유리 (MongoDB, Redis, Cassandra, Neo4j 등)
- 상세: [DBMS 기초 정리](../cs-study/260816-dbms-기초-면접정리.md)

### 실행계획 (Execution Plan) / N+1 문제
- 실행계획: DB가 쿼리를 실제로 어떻게 실행할지 계획, `EXPLAIN`으로 확인 (type=ALL, key=NULL이면 풀스캔 위험 신호)
- N+1 문제: ORM의 지연 로딩으로 반복문에서 연관 엔티티에 접근할 때마다 추가 쿼리가 나가는 문제, Fetch Join/Batch Size로 해결
- 상세: [DBMS 기초 정리](../cs-study/260816-dbms-기초-면접정리.md)

### 하이브리드 검색 (Hybrid Search)
- 텍스트 검색(BM25/Elasticsearch)과 벡터 검색(kNN)을 함께 돌려 RRF(Reciprocal Rank Fusion)로 순위 병합, 재랭커로 상위 후보 재평가
- 벡터 검색 단독보다 정밀도를 높이는 발전형 RAG 구성

### XSS (Cross-Site Scripting)
- 악성 스크립트를 웹페이지에 심어 다른 사용자 브라우저에서 실행되게 하는 공격, 쿠키/세션 탈취가 주 목적
- Stored(DB 저장) vs Reflected(URL 파라미터) 구분

---

(새 용어 학습 시 가나다 순으로 추가)
