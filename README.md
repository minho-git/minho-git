## Ondo — 동대문 도매·소매 B2B 플랫폼

> SW마에스트로 부산 17기 · [저장소](https://github.com/minho-git/ondo-api)

서버 둘 · DB 둘 구조. 백엔드 2인 중 **정산·집계·주문 연동** 담당.

- **정산 원장** — 동시 쓰기에 잔액 순서가 뒤집히는 문제. 잠금 3종을 동시 640건으로 비교해
  비관적 락 선택 (낙관적 락은 재시도 4,556회 · 1건 유실)
- **대시보드 집계** — 요청 하나가 커넥션을 둘 잡던 구조를 고쳐 **354ms → 0.2ms**.
  캐시는 켜고 끈 차이가 0.5ms라 도입하지 않음
- **주문 접수 대기함** — Outbox + `SKIP LOCKED` 워커로 도매 서버가 멈춰도 주문 유지.
  재시도 정책 3종 중 지터 선택 (복구 36% 느리지만 몰림 없음)

`Java 21` `Spring Boot 4` `PostgreSQL` `Testcontainers` `k6` `ECS` `Terraform`

<br>

## XFlow — 코드 없는 데이터 파이프라인 플랫폼

> 5인 팀 · [저장소](https://github.com/minho-git/xflow) · [시연 영상](https://www.youtube.com/watch?v=WNXGnw_Wg8Q)

웹 UI로 ETL/ELT를 구성하면 Spark가 실행하고 Airflow가 오케스트레이션.
**수집·변환 파이프라인** 담당 (FastAPI · Spark 잡 · ETL 에디터).

- **Kafka 스트리밍 수집** — 정규식 파싱으로 비정형 로그를 컬럼화, 오프셋 재시작
- **조인 자동 탐지** — 샘플링으로 조인 키 제안, 타입 캐스팅, S3 pushdown

`FastAPI` `Spark` `Kafka` `Airflow` `Trino` `React` `Kubernetes` `Helm`
