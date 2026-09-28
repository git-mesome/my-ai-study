# 나의 AI & CS 학습 레포

Claude Code를 학습 코치로 활용하는 개인 학습 기록 저장소.

## AI 개념 학습 ([ai-concepts/](./ai-concepts/))

| 문서 | 주제 |
|------|------|
| [260807-하네스-컨텍스트엔지니어링.md](./ai-concepts/260807-하네스-컨텍스트엔지니어링.md) | 하네스 & 컨텍스트 엔지니어링 — 압축 기법 정리 |
| [260807-루프엔지니어링.md](./ai-concepts/260807-루프엔지니어링.md) | 루프 엔지니어링 — 종료 조건/stuck 감지 설계 |
| [260807-rag-파이프라인.md](./ai-concepts/260807-rag-파이프라인.md) | RAG 파이프라인 — 검색/보강/생성 구조 |
| [260817-agent-native-sre-self-healing.md](./ai-concepts/260817-agent-native-sre-self-healing.md) | Agent-Native SRE/Self-Healing — 에이전트 기반 장애 진단·조치 |
| [260817-멀티에이전트-오케스트레이션.md](./ai-concepts/260817-멀티에이전트-오케스트레이션.md) | 멀티에이전트 오케스트레이션 — 패턴, 프레임워크 비교, 하네스/세션/에이전트 구분 |
| [260817-툴-가드레일-엔지니어링.md](./ai-concepts/260817-툴-가드레일-엔지니어링.md) | 툴 엔지니어링 & 가드레일 엔지니어링 — 도구 설계, 훅(hook) 설정법 |
| [260817-메모리엔지니어링.md](./ai-concepts/260817-메모리엔지니어링.md) | 메모리 엔지니어링 — MemGPT, 세션 vs 메모리 저장소, 정리 전략 |
| [260817-이벨엔지니어링.md](./ai-concepts/260817-이벨엔지니어링.md) | 이벨(Eval) 엔지니어링 — LLM-as-Judge, 자동/사람 평가 |
| [260817-그래프엔지니어링-graphrag.md](./ai-concepts/260817-그래프엔지니어링-graphrag.md) | 그래프 엔지니어링(GraphRAG) — 지식그래프 결합 RAG |
| [260817-ai-엔지니어링-역사.md](./ai-concepts/260817-ai-엔지니어링-역사.md) | AI 엔지니어링 용어 통합 타임라인 — 전체 계열 정리 |
| [260928-파인튜닝-vs-결정모델.md](./ai-concepts/260928-파인튜닝-vs-결정모델.md) | 파인튜닝(LoRA/QLoRA, 인코더 분류) vs 결정 모델(Ollaya) — N2SF 등급 분류 설계안 유지 판단 |
| [BACKLOG.md](./ai-concepts/BACKLOG.md) | 앞으로 공부할 주제 목록 |
| [dictionary.md](./ai-concepts/dictionary.md) | AI 용어 사전 |

## CS 학습 ([cs-study/](./cs-study/))

주제별 폴더로 구성: [network](./cs-study/network/), [db](./cs-study/db/), [os-linux](./cs-study/os-linux/), [language](./cs-study/language/), [distributed-systems](./cs-study/distributed-systems/), [misc](./cs-study/misc/)

| 문서 | 주제 |
|------|------|
| [network/260816-네트워크-기초-면접정리.md](./cs-study/network/260816-네트워크-기초-면접정리.md) | 네트워크 기초 — OSI/TCP-IP, DNS, ARP, 방화벽, 트러블슈팅 (면접 대비) |
| [network/260915-비대칭라우팅-ecmp-pbr.md](./cs-study/network/260915-비대칭라우팅-ecmp-pbr.md) | 비대칭 라우팅 — ECMP/PBR, Stateful 방화벽·conntrack, 블랙홀/루프/traceroute (수습 기간 사내 온보딩 학습) |
| [network/260916-vlan-트렁크-주소객체.md](./cs-study/network/260916-vlan-트렁크-주소객체.md) | VLAN/트렁크/802.1Q, inter-VLAN 라우팅(router-on-a-stick·L3 스위치), 주소 객체(FortiGate) (수습 기간 사내 온보딩 학습) |
| [network/260921-인터페이스-논리인터페이스-dmz.md](./cs-study/network/260921-인터페이스-논리인터페이스-dmz.md) | 물리/논리 인터페이스(VLAN sub-interface·링크 묶음·터널), 인터페이스 이름 규칙, 존(trust/untrust/DMZ)·존 단위 정책의 이점 (수습 기간 사내 온보딩 학습) |
| [db/260816-dbms-기초-면접정리.md](./cs-study/db/260816-dbms-기초-면접정리.md) | DBMS 기초 — RDBMS vs NoSQL, ACID, 트랜잭션 격리 수준 (면접 대비) |
| [os-linux/260817-리눅스-기초-면접정리.md](./cs-study/os-linux/260817-리눅스-기초-면접정리.md) | 리눅스 기초 — 프로세스/시그널/파일디스크립터/메모리/트러블슈팅 명령어 (면접 대비) |
| [language/260817-java-기초-면접정리.md](./cs-study/language/260817-java-기초-면접정리.md) | Java 기초 — JVM/GC, 컬렉션 내부동작, 동시성, 제네릭/스트림 (면접 대비) |
| [distributed-systems/260718-dlq-outbox-패턴.md](./cs-study/distributed-systems/260718-dlq-outbox-패턴.md) | DLQ & Outbox 패턴 — 장애 대응 기초 |
| [misc/260718-nft-블록체인-해시인증.md](./cs-study/misc/260718-nft-블록체인-해시인증.md) | NFT vs 블록체인 해시 타임스탬핑 — 요구사항 재정의 |

## 실습 프로젝트 ([hands-on/](./hands-on/))

| 프로젝트 | 주제 |
|----------|------|

## 업무 적용 사례 ([work-application/](./work-application/))

| 문서 | 내용 |
|------|------|
| [260623-spring-cloud-개요.md](./work-application/260623-spring-cloud-개요.md) | Spring Cloud 개요 — MSA 인프라 문제 해결 도구 모음 |
