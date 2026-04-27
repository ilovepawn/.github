<div align="center">

# ilovepawn

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&pause=1000&color=58A6FF&center=true&vCenter=true&width=620&lines=%EB%A7%88%EC%9D%B4%ED%81%AC%EB%A1%9C%EC%84%9C%EB%B9%84%EC%8A%A4+%EA%B8%B0%EB%B0%98+%EC%B2%B4%EC%8A%A4+%ED%94%8C%EB%9E%AB%ED%8F%BC;%EC%84%9C%EB%B9%84%EC%8A%A4+%EB%8B%A8%EC%9C%84%EB%A1%9C+%EB%A7%8C%EB%93%9C%EB%8A%94+%EC%A4%91" alt="tagline" />

<br/>

[![Python](https://img.shields.io/badge/Python-3.13-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-009688?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![RabbitMQ](https://img.shields.io/badge/RabbitMQ-FF6600?logo=rabbitmq&logoColor=white)](https://www.rabbitmq.com/)
[![MySQL](https://img.shields.io/badge/MySQL-8.4-4479A1?logo=mysql&logoColor=white)](https://www.mysql.com/)
[![MinIO](https://img.shields.io/badge/MinIO-S3--Compatible-C72E49?logo=minio&logoColor=white)](https://min.io/)
[![Stockfish](https://img.shields.io/badge/Stockfish-18-000000?logo=lichess&logoColor=white)](https://stockfishchess.org/)
[![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)](https://www.docker.com/)

**한국어** · [English](README.md)

</div>

---

## 아키텍처

```mermaid
flowchart LR
    User([사용자])
    Platform[메인 플랫폼]
    MQ[(RabbitMQ)]
    DT[deep-thought]
    S3[(MinIO / S3<br/>분석 PGN)]
    TT[tactician]
    ZZ[zugzwang]
    Syzygy[(Syzygy<br/>테이블베이스)]
    DB1[(MySQL)]
    DB2[(MySQL)]

    User <--> Platform
    Platform <-. AMQP .-> MQ
    MQ <-. AMQP .-> DT
    DT -- 생산 --> S3
    S3 -- 야간 채굴 --> TT
    Platform -- HTTP --> TT
    Platform -- HTTP --> ZZ
    ZZ --> Syzygy
    TT --> DB1
    ZZ --> DB2
```

S3 호환 버킷에 저장되는 분석 PGN이 서비스 간 계약 역할을 합니다 — `deep-thought`가 생산하고 `tactician`이 소비합니다.

---

## 서비스

| 레포 | 역할 | 스택 |
|---|---|---|
| [**deep-thought**](https://github.com/ilovepawn/deep-thought) | 게임 분석 워커 — RabbitMQ 기반 Stockfish로 분석 PGN 생성 | Python · RabbitMQ · Stockfish · MinIO |
| [**tactician**](https://github.com/ilovepawn/tactician) | 전술 퍼즐 서비스 — 매일 Stockfish 채굴 + HTTP API | Python · FastAPI · MySQL · Stockfish |
| [**zugzwang**](https://github.com/ilovepawn/zugzwang) | 엔드게임 트레이너 — Syzygy 테이블베이스 기반 완벽 대국 상대 | Python · FastAPI · MySQL · Syzygy |

---

<div align="center">
<sub>Built by <a href="https://github.com/FickleBoBo">@FickleBoBo</a></sub>
</div>
