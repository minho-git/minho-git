# 김민호

백엔드 개발자입니다. 기능을 새로 붙이는 일보다 **이미 돌아가는 것이 언제 어떻게 무너지는지 재보고 막는 일**을 합니다.

- **SW마에스트로 부산 17기** — B2B 플랫폼 `Ondo` 백엔드
- **크래프톤 정글** — C로 OS·동적 메모리 할당기·웹 프록시 서버를 밑바닥부터 구현
- 정보처리기사 · SQLD

<br>

## Stack

`Java 21` `Spring Boot` `Python` `FastAPI` `C`

`PostgreSQL` `MySQL` `Kafka` `Spark` `Airflow`

`Docker` `Kubernetes` `AWS` `Terraform`

<br>

## Ondo — 동대문 도매·소매 B2B 플랫폼

> 도매 재고관리(POS)와 소매 발주를 하나로 잇는 플랫폼 · [ondo-commerce/ondo-api](https://github.com/ondo-commerce/ondo-api)

도매 API와 소매 API가 **서버 둘 · DB 둘**로 나뉘어 있어 한 트랜잭션으로 묶을 수 없는 구조입니다.
백엔드 2인 중 정산·집계·주문 연동을 맡았습니다.

**정산 원장 — 잠금은 값이 아니라 순서를 지킨다**

미수 잔액이 출고·입금·입금취소·배분 네 경로에서 동시에 바뀝니다. 원장을 추가 전용으로 두어 값을
덮어쓰지 않는데도, 두 요청이 같은 잔액을 읽고 각자 이어 쓰면 `balance_after`가 어긋납니다.
잠금을 뺀 채 동시 640건을 넣어 확인하니 잔액 64만 원이 **7만 원**으로 집계됐습니다.
낙관적 락은 정확했지만 재시도가 4,556회 쌓이고 1건이 유실되어, 비관적 락을 골랐습니다(+38ms).

**대시보드 집계 — 원인은 트래픽이 아니라 커넥션 두 개**

도매처 3만 곳 규모에서 초당 11건에 멈추고 189개가 대기했습니다. 요약 갱신이 읽기 트랜잭션 안에서
`REQUIRES_NEW`를 열어 요청 하나가 커넥션을 두 개 잡고 있었습니다. 갱신을 읽기 밖으로 빼서
**354ms → 0.2ms**. 이어서 넣으려던 캐시는 켜고 꺼 본 차이가 0.5ms라 **도입하지 않고 근거를 남겼습니다**.

**주문 접수 대기함 — 도매 서버가 멈춰도 주문을 잃지 않게**

주문 의사를 같은 트랜잭션에 먼저 적고(Outbox) 워커가 `FOR UPDATE SKIP LOCKED`로 집어 다시 보냅니다.
장애를 주입해 고정·지수·지수+지터 세 정책을 비교했고, 지터를 섞으면 복구가 36% 느려지지만
재시도가 한 시점에 몰리지 않아 그쪽을 택했습니다.

`Java 21` `Spring Boot 4` `PostgreSQL` `Flyway` `Testcontainers` `k6` `ECS` `Terraform`

<br>

## XFlow — 코드 없는 데이터 파이프라인 플랫폼

> 웹 UI에서 ETL/ELT 파이프라인을 구성·실행하는 데이터 플랫폼 · 5인 팀 · [저장소](https://github.com/minho-git/xflow) · [시연 영상](https://www.youtube.com/watch?v=WNXGnw_Wg8Q)

드래그 앤 드롭으로 워크플로우를 설계하면 **Spark가 실행하고 Airflow가 오케스트레이션**합니다.
PostgreSQL·MySQL·MongoDB·S3·REST API 등 다중 소스에서 CDC 실시간 수집과 배치 ETL을 지원하고,
메타데이터 카탈로그 · 품질 체크 · 리니지 추적과 Trino 기반 SQL Lab을 붙였습니다.

**맡은 부분 — 수집·변환 파이프라인** (FastAPI 백엔드 · Spark 잡 · ETL 에디터)

- **Kafka 스트리밍 수집** — 정규식 파싱으로 비정형 로그를 컬럼으로 풀고, 원본 포맷 보존과
  오프셋 재시작을 붙여 파이프라인을 다시 띄워도 이어서 읽게 했습니다
- **조인 자동 탐지** — 소스를 샘플링해 조인 키 후보를 찾아 제안합니다. 타입이 어긋난 컬럼은
  캐스팅으로 맞추고, S3 소스는 조건을 밀어 넣어(pushdown) 전체를 읽지 않게 했습니다
- Helm 차트로 EKS 배포 구성

`FastAPI` `Spark` `Kafka` `Airflow` `Trino` `React` `Kubernetes` `Helm`

<br>

## Contact

[![GitHub](https://img.shields.io/badge/minho--git-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/minho-git)
[![Solved.ac](https://img.shields.io/badge/solved.ac-0093FF?style=flat-square&logo=leetcode&logoColor=white)](https://solved.ac/profile/alsgh1552)
