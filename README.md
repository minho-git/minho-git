## 👋 About Me

**백엔드 개발자를 목표로 공부하고 있는 김민호입니다.**

동작하는 코드를 넘어서, **왜 이렇게 설계했는지 설명할 수 있는 개발자**가 되고 싶습니다.
그래서 운영체제·네트워크 같은 기본기부터 직접 구현해보고, 실제 서비스에 가까운 구조로 프로젝트를 만들어보고 있습니다.

- 🔭 지금은 **SW마에스트로 부산 17기**에서 B2B 플랫폼 **Ondo**의 백엔드를 만들고 있습니다
- 🌱 관심사는 **분산 시스템**, **컨테이너 오케스트레이션**, **대용량 데이터 처리**
- 🧩 크래프톤 정글에서 **C로 OS·메모리 할당기·웹 프록시 서버**를 밑바닥부터 구현했습니다

<br>

## 🛠 Tech Stack

**Languages**

![Java](https://img.shields.io/badge/Java-007396?style=for-the-badge&logo=openjdk&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![C](https://img.shields.io/badge/C-A8B9CC?style=for-the-badge&logo=c&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)

**Backend & Data**

![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![Apache Kafka](https://img.shields.io/badge/Kafka-231F20?style=for-the-badge&logo=apachekafka&logoColor=white)
![Apache Spark](https://img.shields.io/badge/Spark-E25A1C?style=for-the-badge&logo=apachespark&logoColor=white)
![Apache Airflow](https://img.shields.io/badge/Airflow-017CEE?style=for-the-badge&logo=apacheairflow&logoColor=white)

**Infra & Tools**

![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonwebservices&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)

<br>

## 📌 Projects

### 🧵 Ondo — 동대문 도매 B2B 플랫폼 *(SW마에스트로, 진행 중)*

> 재고관리(POS)와 상품노출(마켓플레이스)을 하나로 합친 도매업자용 플랫폼

동대문 도매 현장은 재고·상품노출·소매 소통을 전부 다른 도구로 씁니다.
그중 아무도 못 푼 **미송(재고 부족 주문) 처리**를 자동화하고,
여러 소매처가 동시에 주문할 때의 **재고 동시성 제어**를 설계 중심으로 풀고 있습니다.
실제 도매 사장님 인터뷰로 가설을 검증하고, 도메인 모델링(ERD)부터 탄탄히 쌓아가는 중입니다.

`Java 21` `Spring Boot` `MySQL` `Next.js` `AWS`

<br>

### 🌊 [XFlow](https://github.com/minho-git/xflow)

> 코드 없이 웹 UI에서 ETL/ELT 파이프라인을 구성·실행하는 데이터 플랫폼

드래그 앤 드롭으로 데이터 워크플로우를 설계하면 **Spark가 실행하고 Airflow가 오케스트레이션**하는 구조입니다.
PostgreSQL·MongoDB·S3·REST API 등 다중 소스, 실시간 CDC와 배치 처리를 지원하고,
메타데이터 카탈로그 · 데이터 리니지 추적 · 자연어→SQL 어시스턴트까지 붙였습니다.
로컬은 Docker Compose, 프로덕션은 AWS EKS(Kubernetes) 배포를 지원합니다.

`FastAPI` `React` `Spark` `Airflow` `Trino` `OpenSearch` `Kubernetes` `Terraform`

<br>

### 🎮 [game-telemetry-pipeline](https://github.com/minho-git/game-telemetry-pipeline)

> 게임 매치 이벤트 로그 파이프라인

실무 데이터 파이프라인 구조(**Kafka → Spark → Medallion Architecture → Airflow**)를
Docker Compose 기반 로컬 환경에서 재현한 프로젝트입니다.
PUBG 개발자 API의 실제 텔레메트리 스펙을 참고해 합성 이벤트 로그를 설계했고,
이벤트 타입별로 필드가 다른 문제를 **envelope + payload 스키마**로 풀었습니다.

`Python` `Kafka` `Spark` `Airflow` `Docker Compose`

<br>

### 🏗️ [devops-3-tier-practice](https://github.com/minho-git/devops-3-tier-practice)

> AWS 3-Tier 아키텍처 실습 — 방명록 애플리케이션

**CloudFront → S3(정적) / ALB → EC2 ×2 → RDS MySQL**로 이어지는 3계층 구조를 직접 구축했습니다.
새로고침으로 로드밸런싱을 검증하고, EC2를 중지시켜 장애 상황에서의 서비스 지속성을 테스트했습니다.

`AWS` `CloudFront` `ALB` `EC2` `RDS` `Node.js`

<br>

### 🐳 [sw-maestro-docker-master](https://github.com/minho-git/sw-maestro-docker-master)

> Docker 실습 15선 — 하나의 앱을 단계별로 고도화하며 Docker 익히기

Go 방문 카운터 앱 하나를 15단계에 걸쳐 고도화하는 실습 시리즈입니다.
**이미지 경량화**와 **데이터 영속성**이라는 두 서사를 축으로,
패키징 → 빌드 최적화 → 운영·공유 → 네트워크 → 영속성 → 리소스까지 문제/해설 구조로 구성했습니다.

`Docker` `Go` `Linux`

<br>

### 🧱 크래프톤 정글 — CS 밑바닥부터 구현

> C로 직접 만들어본 시스템 소프트웨어

| 저장소 | 내용 |
| --- | --- |
| [pintos (VM)](https://github.com/minho-git/pintos_22.04_lab_docker_part2) | 가상 메모리, 페이지 폴트 처리, 스왑 |
| [pintos (Part 1)](https://github.com/minho-git/pintos_22.04_lab_docker_part1) | 스레드, 유저 프로그램, 시스템 콜 |
| [webproxy_lab](https://github.com/minho-git/webproxy_lab) | HTTP 프록시 서버 + 캐시, 동시성 처리 |
| [malloc_lab](https://github.com/minho-git/malloc_lab) | 동적 메모리 할당기 직접 구현 |
| [rbtree_lab](https://github.com/minho-git/rbtree_lab) | Red-Black Tree 구현 |

<br>

## 🧗 Problem Solving

<div align="center">

[![Solved.ac 프로필](http://mazassumnida.wtf/api/v2/generate_badge?boj=alsgh1552)](https://solved.ac/profile/alsgh1552)

</div>

<br>

## 📫 Contact

<div align="center">

[![GitHub](https://img.shields.io/badge/minho--git-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/minho-git)
[![Solved.ac](https://img.shields.io/badge/solved.ac-0093FF?style=for-the-badge&logo=leetcode&logoColor=white)](https://solved.ac/profile/alsgh1552)

</div>
