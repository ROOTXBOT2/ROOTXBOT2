# ROOTXBOT2 | Backend Developer

Spring Boot 기반 백엔드 개발자입니다.  
도메인 흐름을 코드로 구현하고, 인증/인가, 캐싱, 테스트, CI, 운영 관측성까지 고려하는 백엔드 개발을 지향합니다.

최근에는 AI 도구를 활용해 요구사항 분석, 기능 분해, 이슈/PR 기반 작업 관리, 테스트 보강, 문서화를 함께 진행하며 백엔드 프로젝트를 고도화하고 있습니다.

---

## Focus

- Spring Boot 기반 REST API 설계 및 구현
- 인증/인가: Spring Security, JWE/JWT, Role 기반 접근 제어
- 데이터 처리: JPA, JDBC Template, PostgreSQL/PostGIS, MySQL, Redis
- 안정성: Redis Stream, RateLimit, token blacklist, 상태 전이 검증
- 테스트: 단위 테스트, 통합 테스트, Testcontainers
- 협업: API First, GitHub Issues, Pull Requests, 기능 브랜치, 코드 리뷰 대응
- 운영 관점: CI, 구조화 로깅, Actuator, Prometheus, k6 성능 측정

---

## Projects

### Dandi-Onna

> 노쇼 재고 손실을 판매 기회로 전환하는 O2O 예약·주문 플랫폼

음식점 노쇼로 발생한 재고 손실을 줄이기 위해, 사장님이 노쇼 메뉴를 등록하면 소비자가 할인된 가격으로 바로 주문할 수 있도록 만든 서비스입니다.  
백엔드 단독 개발자로 인증/인가, 매장/메뉴, 노쇼 게시글, 예약 게시, 소비자 주문, 알림, 매출 조회·엑셀 export, 운영/성능 측정 체계를 담당했습니다.

Key Contributions

- MVP 출시 일정을 기준으로 구현 난이도와 소요 시간을 산정해 PM과 스펙을 조율하고, 핵심 기능 중심으로 범위를 정리
- API 명세를 먼저 확정하는 API First 방식을 제안해 프론트엔드와 병렬 개발이 가능하도록 협업 구조 구성
- 기획자·디자이너와는 ERD 중심 설명보다 UI 흐름에 맞춘 데이터 설명 방식으로 소통해 화면별 상태와 API 요구사항 정리
- Spring Security 기반 Stateless 보안 구조와 JWE Access/Refresh Token 구현
- Redis token blacklist, OWNER / CONSUMER / ADMIN 역할 기반 접근 제어, Redis RateLimit 적용
- 노쇼 게시글 등록·예약 게시·소비자 주문 생성 흐름 구현
- PESSIMISTIC_WRITE 기반 게시글 잠금 조회, 방문 시간/금액/할인율/원가 재검증, 잔여 수량 차감과 sold_out 상태 전이 적용
- Redis Stream 기반 FCM 알림 worker와 알림 이력 저장, DLQ 이동 / 수동 replay 구조 구현
- Redis Stream 기반 매출 엑셀 export worker, Apache POI 엑셀 생성, S3-compatible storage 업로드, presigned download URL 제공
- 단품/세트 메뉴 구성, effectiveStatus 계산, Redis upload token과 ETag 검증 기반 메뉴 이미지 임시 업로드/확정 흐름 구현
- Prometheus business metric, MDC 기반 JSON 로깅, k6 + Docker 성능 측정 스크립트와 seed SQL 정리

Tech Stack

`Java 21` `Spring Boot` `Spring Security` `JWE/JWT` `PostgreSQL/PostGIS` `Redis` `Redis Stream` `Firebase FCM` `MinIO/S3-compatible Storage` `Apache POI` `Micrometer` `Prometheus` `k6` `Docker`

Links

- Portfolio: https://github.com/goorm-ynot/dandi-onna-be/blob/docs/dandi-onna-portfolio/PORTFOLIO.md
- Repository Notes: https://github.com/goorm-ynot/dandi-onna-be/blob/docs/dandi-onna-portfolio/docs/repo-notes.md
- Repository: https://github.com/goorm-ynot/dandi-onna-be

---

### MATJOM

> 위치 기반 점심 추천 백엔드 프로젝트

직장인의 점심 선택 시간을 줄이기 위해 위치 기반 장소 검색, 룰렛 추천, 방문 세션, 지오펜스 도착 판정을 구현한 프로젝트입니다.

Key Contributions

- PostGIS 기반 반경 검색과 거리 ASC 커서 페이징 구현
- Redis 60초 검색 캐싱 적용
- Idempotency-Key 기반 룰렛 추천 API 구현
- 방문 세션 lifecycle 구현
- 30m / 180초 dwell / 10초 grace window 기반 지오펜스 도착 판정
- Testcontainers 기반 통합 테스트로 회원가입 → 장소 검색 → 방문 세션 → 도착 확정 흐름 검증

Tech Stack

`Java 21` `Spring Boot` `PostgreSQL/PostGIS` `Redis` `JPA` `JDBC Template` `JWT` `Testcontainers`

Links

- Portfolio: https://github.com/ROOTXBOT2/MATJOM_BACKEND/blob/docs/matjom-portfolio/PORTFOLIO.md
- Repository Notes: https://github.com/ROOTXBOT2/MATJOM_BACKEND/blob/docs/matjom-portfolio/docs/repo-notes.md

---

### Cou-Commerce

> 고객 요구사항 기반 이커머스 백엔드 개발 전주기 프로젝트

Cart → Order → Payment로 이어지는 이커머스 핵심 흐름과 JWT/RBAC 인증 구조, CI, 로깅/모니터링 기반을 구현한 팀 프로젝트입니다.

Key Contributions

- Redis Hash 기반 Cart API 구현
- Cart → Order → Payment 구매 흐름 구현
- 가격/재고 재검증, 셀러별 주문 분할, 주문 취소 시 재고 복구 처리
- Mock Payment 승인/실패, 중복 결제 방지, 환불 요청 흐름 구현
- Spring Security + JWT 기반 BUYER / SELLER / ADMIN 접근 제어 구현
- GitHub Actions 기반 MySQL/Redis 컨테이너 CI 구성
- MDC 기반 요청 추적과 Prometheus/Grafana 모니터링 수집 환경 구성

Tech Stack

`Java 24` `Spring Boot` `Spring Security` `JWT` `MySQL` `Redis` `JPA` `GitHub Actions` `Prometheus` `Grafana`

Links

- Portfolio: https://github.com/backsuend/Cou-commerce/blob/docs/cou-commerce-portfolio/PORTFOLIO.md
- Repository Notes: https://github.com/backsuend/Cou-commerce/blob/docs/cou-commerce-portfolio/docs/repo-notes.md

---

### EduConnect

> 교육 커뮤니티 백엔드 협업 프로젝트

학생과 강사가 트랙별로 질문과 답변을 주고받는 교육 커뮤니티 백엔드 프로젝트입니다.  
Auth, JWT, Spring Security, QnA 게시판, 역할/트랙 기반 권한 로직을 구현했습니다.

Key Contributions

- 회원가입, 로그인, 로그아웃, 토큰 재발급 API 구현
- JWT 기반 Access/Refresh Token 구조 구현
- 로그아웃 Access Token 블랙리스트 처리
- Spring Security Filter Chain 구성
- 질문/답변/댓글 CRUD 구현
- 학생/강사 역할과 트랙 기반 접근 제어 구현
- 검색, 필터, 정렬, 페이징 기능 구현

Tech Stack

`Java` `Spring Boot` `Spring Security` `JWT` `JPA` `H2` `Swagger` `JUnit`

Links

- Portfolio: https://github.com/ROOTXBOT2/EduConnect-/blob/docs/educonnect-portfolio/PORTFOLIO.md
- Code Walkthrough: https://github.com/ROOTXBOT2/EduConnect-/blob/docs/educonnect-portfolio/docs/educonnect-code-walkthrough.md

---

## Tech Stack

### Backend

`Java` `Spring Boot` `Spring Security` `Spring Data JPA` `JWE/JWT` `Gradle`

### Database / Cache / Messaging

`MySQL` `PostgreSQL` `PostGIS` `Redis` `Redis Stream` `H2`

### Testing

`JUnit5` `Mockito` `AssertJ` `Spring Boot Test` `Testcontainers`

### DevOps / Observability

`GitHub Actions` `Docker Compose` `Actuator` `Micrometer` `Prometheus` `Grafana` `Logstash` `k6`

### Collaboration

`API First` `GitHub Issues` `Pull Requests` `Branch Strategy` `Code Review` `Swagger / OpenAPI`

---

## How I Work

- 요구사항을 기능 단위로 분해하고 GitHub Issue로 관리합니다.
- API 명세를 먼저 정리해 프론트엔드와 병렬 개발 가능한 협업 구조를 만듭니다.
- 기능 브랜치와 PR 단위로 구현 범위를 명확히 남깁니다.
- 단순 구현보다 예외 처리, 상태 전이, 권한 검증, 테스트 가능성을 함께 고려합니다.
- 구현 후 README, 포트폴리오 문서, 코드 흐름 문서를 정리해 근거를 남깁니다.
- AI 도구를 활용하되, 최종 의사결정은 요구사항과 코드 근거를 기준으로 검증합니다.

---
