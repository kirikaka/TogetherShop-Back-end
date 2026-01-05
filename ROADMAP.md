# 6주 프로젝트 로드맵 (취업용 백엔드 역량 강화)

대상: `kirikaka/TogetherShop-Back-end`

목표: 기존 Spring Boot 백엔드에 **테스트/문서/CI/CD/컨테이너/관측가능성(운영)** + **Kafka 이벤트 기반 비동기 처리(확장성)** 를 6주 동안 단계적으로 도입해, 대기업 신입 백엔드 수준의 포트폴리오 산출물을 만든다.

---

## Definition of Done (공통)
- 작업은 PR 단위로 쪼개서 진행한다.
- PR 머지 전 CI(빌드/테스트)가 통과한다.
- 변경사항은 테스트 또는 API 문서(REST Docs/OpenAPI) 업데이트를 포함한다.
- 로컬에서 `docker compose up`으로 구동 가능하다.
- 운영 관점(헬스/메트릭/로그)이 확인 가능하다.

---

## Week 1 — CI + 품질 게이트
목표: PR을 올리면 자동으로 검증되는 최소 품질 체계를 만든다.

- GitHub Actions로 Gradle build/test 실행
- Gradle 캐시 + Java 17 toolchain 설정
- (선택) Spotless/Checkstyle 등 포맷/규칙 적용
- `build.gradle` 의존성 정리(중복 제거 등)

산출물:
- `.github/workflows/ci.yml`
- PR 체크에서 build/test 결과 확인

---

## Week 2 — 통합 테스트(Testcontainers)
목표: DB/Redis 포함한 “실제에 가까운” 테스트로 신뢰성을 확보한다.

- Testcontainers 도입
- MySQL 컨테이너 기반 JPA Repository 통합 테스트
- Redis 컨테이너 기반 기능 테스트(캐시/채팅 pubsub 등 중 1개 이상)
- 테스트 데이터/픽스처 표준화

산출물:
- 통합 테스트 3~5개
- CI에서 컨테이너 기반 테스트 통과

---

## Week 3 — API 문서 자동화
목표: 계약(Contract)이 관리되는 API를 만든다.

- 문서화 방식 선택
  - A) Spring REST Docs(테스트 기반)
  - B) OpenAPI/Swagger(springdoc)
- 핵심 API 5개 문서화(인증/쿠폰/제휴/공구/채팅 중 우선)
- 공통 에러 응답 규격 정의 + 문서 포함

산출물:
- 문서 페이지 또는 Swagger UI
- 문서 생성이 CI에 포함

---

## Week 4 — Docker/Compose로 로컬 실행 표준화
목표: 누구나 1분 안에 로컬 환경을 띄울 수 있게 만든다.

- Dockerfile로 애플리케이션 컨테이너화
- `docker-compose.yml`: app + mysql + redis (+ 선택: kafka)
- 환경변수 표준화(`.env.example`, `application-*.yml` 분리)
- 로컬 실행 가이드 README 추가

산출물:
- `docker compose up`으로 전체 구동
- README: 실행 방법/환경변수

---

## Week 5 — Observability(운영)
목표: 운영 중 상태를 관찰할 수 있게 만든다.

- Spring Boot Actuator(health/info/metrics) 구성
- Micrometer 메트릭 노출(Prometheus 포맷)
- (선택) Prometheus + Grafana를 compose에 추가
- 구조화 로그(JSON 또는 MDC request-id) 도입

산출물:
- `/actuator/health` 확인
- 메트릭 수집(선택: 대시보드)

---

## Week 6 — Kafka 이벤트 기반 기능 1개
목표: 이벤트 기반 아키텍처 경험을 프로젝트에 녹인다.

- Kafka 도입(로컬은 docker-compose)
- 이벤트 모델 정의(예: `CouponUsedEvent`, `NotificationRequestedEvent`)
- Producer/Consumer 구현
- 이벤트 기반 기능 1개 완성
  - 예: 쿠폰 사용 → 이벤트 발행 → 소비자가 알림(Firebase/DB 저장) 처리
- (가능하면) Testcontainers Kafka 또는 최소 E2E 시나리오 문서

산출물:
- 이벤트 기반 기능 데모
- README에 아키텍처/흐름 설명(텍스트 다이어그램)

---

## 최종 제출 체크리스트(취업용)
- 실행: docker-compose로 1분 내 기동
- 신뢰성: CI + 통합테스트
- 협업: PR 단위 작업, 커밋/브랜치 규칙
- 운영: actuator/metrics/logging
- 확장: Kafka 이벤트 기반 기능
