<div align="center">

<a href="https://github.com/ilovepawn">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:1f6feb,100:8957e5&height=220&section=header&text=ilovepawn&fontSize=80&fontColor=ffffff&animation=fadeIn&fontAlignY=38" alt="ilovepawn" />
</a>

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&pause=1000&color=58A6FF&center=true&vCenter=true&width=620&lines=%EB%A7%88%EC%9D%B4%ED%81%AC%EB%A1%9C%EC%84%9C%EB%B9%84%EC%8A%A4+%EA%B8%B0%EB%B0%98+%EC%B2%B4%EC%8A%A4+%ED%94%8C%EB%9E%AB%ED%8F%BC;%EC%84%9C%EB%B9%84%EC%8A%A4+%EB%8B%A8%EC%9C%84%EB%A1%9C+%EB%A7%8C%EB%93%9C%EB%8A%94+%EC%A4%91" alt="tagline" />

<br/>

<!-- Frontend -->
[![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Next.js](https://img.shields.io/badge/Next.js-16-000000?logo=nextdotjs&logoColor=white)](https://nextjs.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-v4-06B6D4?logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
[![Expo](https://img.shields.io/badge/Expo-%EC%98%88%EC%A0%95-000020?logo=expo&logoColor=white)](https://expo.dev/)

<!-- Backend -->
[![Java](https://img.shields.io/badge/Java-21-007396?logo=openjdk&logoColor=white)](https://openjdk.org/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.5-6DB33F?logo=springboot&logoColor=white)](https://spring.io/projects/spring-boot)
[![Python](https://img.shields.io/badge/Python-3.13-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-009688?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)

<!-- Infra -->
[![Keycloak](https://img.shields.io/badge/Keycloak-26-4D4D4D?logo=keycloak&logoColor=white)](https://www.keycloak.org/)
[![RabbitMQ](https://img.shields.io/badge/RabbitMQ-FF6600?logo=rabbitmq&logoColor=white)](https://www.rabbitmq.com/)
[![MySQL](https://img.shields.io/badge/MySQL-8.4-4479A1?logo=mysql&logoColor=white)](https://www.mysql.com/)
[![Redis](https://img.shields.io/badge/Redis-7-DC382D?logo=redis&logoColor=white)](https://redis.io/)
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
    FE[frontend<br/>Next.js · Expo]
    KC[(Keycloak<br/>PKCE)]
    ARB[arbiter<br/>Spring Boot]
    MQ[(RabbitMQ)]
    DT[deep-thought]
    S3[(MinIO / S3<br/>분석 PGN)]
    TT[tactician]
    ZZ[zugzwang]
    Syzygy[(Syzygy<br/>테이블베이스)]
    DB0[(MySQL<br/>+ Redis)]
    DB1[(MySQL)]
    DB2[(MySQL)]

    User <--> FE
    FE <-. OIDC .-> KC
    FE -- Bearer JWT --> ARB
    ARB -. 검증 .-> KC
    ARB <-. AMQP .-> MQ
    MQ <-. AMQP .-> DT
    DT -- 생산 --> S3
    S3 -- 야간 채굴 --> TT
    ARB -- HTTP --> TT
    ARB -- HTTP --> ZZ
    ZZ --> Syzygy
    ARB --> DB0
    TT --> DB1
    ZZ --> DB2
```

`arbiter`는 사용자 대면 API 게이트웨이이자 Keycloak OAuth2 리소스 서버이며, `frontend`가 유일한 클라이언트 표면입니다. S3 호환 버킷에 저장되는 분석 PGN이 서비스 간 계약 역할을 합니다 — `deep-thought`가 생산하고 `tactician`이 소비합니다.

---

## 서비스

<div align="center">

<a href="https://github.com/ilovepawn/frontend">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api/pin/?username=ilovepawn&repo=frontend&theme=tokyonight&show_owner=false" />
    <img src="https://github-readme-stats.vercel.app/api/pin/?username=ilovepawn&repo=frontend&show_owner=false" alt="frontend" />
  </picture>
</a>
<a href="https://github.com/ilovepawn/arbiter">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api/pin/?username=ilovepawn&repo=arbiter&theme=tokyonight&show_owner=false" />
    <img src="https://github-readme-stats.vercel.app/api/pin/?username=ilovepawn&repo=arbiter&show_owner=false" alt="arbiter" />
  </picture>
</a>
<a href="https://github.com/ilovepawn/deep-thought">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api/pin/?username=ilovepawn&repo=deep-thought&theme=tokyonight&show_owner=false" />
    <img src="https://github-readme-stats.vercel.app/api/pin/?username=ilovepawn&repo=deep-thought&show_owner=false" alt="deep-thought" />
  </picture>
</a>
<a href="https://github.com/ilovepawn/tactician">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api/pin/?username=ilovepawn&repo=tactician&theme=tokyonight&show_owner=false" />
    <img src="https://github-readme-stats.vercel.app/api/pin/?username=ilovepawn&repo=tactician&show_owner=false" alt="tactician" />
  </picture>
</a>
<a href="https://github.com/ilovepawn/zugzwang">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api/pin/?username=ilovepawn&repo=zugzwang&theme=tokyonight&show_owner=false" />
    <img src="https://github-readme-stats.vercel.app/api/pin/?username=ilovepawn&repo=zugzwang&show_owner=false" alt="zugzwang" />
  </picture>
</a>

</div>

<br/>

| 레포 | 계층 | 역할 | 스택 |
|---|---|---|---|
| [**frontend**](https://github.com/ilovepawn/frontend) | 클라이언트 | pnpm 모노레포 — 현재 Next.js 웹, Expo 모바일은 예정. Keycloak에 직접 인증, Arbiter에는 Bearer JWT 전달. | TypeScript · Next.js 16 · Tailwind v4 · shadcn/ui · Zustand · TanStack Query · chess.js · chessground · Stockfish (WASM) |
| [**arbiter**](https://github.com/ilovepawn/arbiter) | 게이트웨이 | API 게이트웨이 겸 OAuth2 리소스 서버. 플랫폼 상태를 집약하고, `deep-thought`로 분석 작업을 중개하며, 퍼즐·엔드게임 호출을 프록시. | Java 21 · Spring Boot 3.5 · Keycloak · MySQL · Redis · RabbitMQ · Flyway · Prometheus · Grafana |
| [**deep-thought**](https://github.com/ilovepawn/deep-thought) | 워커 | 게임 분석 워커 — RabbitMQ 기반 Stockfish로 분석 PGN 생성. | Python · RabbitMQ · Stockfish · MinIO |
| [**tactician**](https://github.com/ilovepawn/tactician) | 서비스 | 전술 퍼즐 서비스 — 매일 Stockfish 채굴 + HTTP API. | Python · FastAPI · MySQL · Stockfish |
| [**zugzwang**](https://github.com/ilovepawn/zugzwang) | 서비스 | 엔드게임 트레이너 — Syzygy 테이블베이스 기반 완벽 대국 상대. | Python · FastAPI · MySQL · Syzygy |

---

<div align="center">

<sub>Built by <a href="https://github.com/FickleBoBo">@FickleBoBo</a></sub>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:8957e5,100:1f6feb&height=100&section=footer" alt="" />

</div>
