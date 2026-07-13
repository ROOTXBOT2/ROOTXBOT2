# ROOTXBOT2 | Java / Spring Boot Backend Developer

사이버보안 전공과 보안제품개발 교육에서 쌓은 기반 위에 Java와 Spring Boot 백엔드 역량을 확장했습니다.
인증·인가, 주문·재고 상태 전이, 비관적 락, Redis Streams 비동기 처리, PostGIS 위치 검색을 구현했고,
테스트와 CI, 구조화 로깅, Prometheus 지표를 통해 검증과 운영 가시성까지 고려합니다.

## Focus

- Backend: Java 21, Spring Boot, Spring Security, Spring Data JPA, REST API
- Data: PostgreSQL, PostGIS, MySQL, Redis, Redis Streams
- Quality / Ops: JUnit 5, Testcontainers, GitHub Actions, Docker, Prometheus, Grafana, k6
- Security / Design: JWE/JWT, 역할 기반 인가, 비관적 락, Idempotency-Key
- Collaboration: API First, GitHub Issues/PR, 코드 리뷰, 기능 분해와 일정 관리

## Representative Projects

### Dandi-Onna - O2O 예약·주문 플랫폼

7명 협업팀에서 백엔드를 전담했습니다.

- 인증·인가, 매장·메뉴, 노쇼 게시·예약, 주문, 알림, 매출 조회와 엑셀 내보내기 API 구현
- 주문 생성 시 비관적 락과 서버 재검증을 적용해 수량 차감 및 품절 상태 전이 처리
- Redis Streams 기반 FCM 알림 및 매출 엑셀 비동기 워커, 재시도와 DLQ 구성
- Micrometer/Prometheus 지표, MDC JSON 로깅, k6·Docker 측정 환경 구성

[Portfolio](https://github.com/goorm-ynot/dandi-onna-be/blob/docs/dandi-onna-portfolio/PORTFOLIO.md) · [Representative PR](https://github.com/goorm-ynot/dandi-onna-be/pull/36)

### MATJOM - 위치 기반 점심 추천 서비스

백엔드 3명 팀의 팀장으로 요구사항 분해, 업무·일정 관리, 코드 리뷰와 병합, 설계 결정을 주도했습니다.

- PostGIS 반경 검색과 거리순 커서 페이지네이션, Redis 60초 캐싱 구현
- Idempotency-Key 기반 룰렛 추천과 seed 기반 결과 재현 구성
- 사용자당 활성 방문 세션 1개 제한, 위치 이벤트와 세션 만료, 지오펜스 도착 판정 구현
- Testcontainers로 회원가입부터 장소 검색, 방문 세션과 도착 확정까지 통합 검증

[Portfolio](https://github.com/ROOTXBOT2/MATJOM_BACKEND/blob/docs/matjom-portfolio/PORTFOLIO.md) · [Representative PR](https://github.com/MATJOM/BACKEND/pull/41)

## Additional Project Experience

- 이커머스 백엔드: 장바구니-주문-결제 상태 흐름, 가격·재고 재검증, 인증·인가, CI와 운영 지표 구성
- 교육 커뮤니티 백엔드: 인증 흐름, 질문·답변·댓글, 역할 및 트랙 기반 접근 제어 구현

## How I Work

- 요구사항을 기능과 검증 기준으로 분해하고 GitHub Issue와 PR로 근거를 남깁니다.
- 상태 전이, 권한, 재시도, 동시성, 예외 케이스를 구현 단계에서 함께 검토합니다.
- 코드가 실행되는 것에 그치지 않고 테스트 방법과 운영 관측 지점을 문서화합니다.
