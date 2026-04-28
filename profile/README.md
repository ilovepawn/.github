<div align="center">

<a href="https://github.com/ilovepawn">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:1f6feb,100:8957e5&height=220&section=header&text=ilovepawn&fontSize=80&fontColor=ffffff&animation=fadeIn&fontAlignY=38" alt="ilovepawn" />
</a>

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&pause=1000&color=58A6FF&center=true&vCenter=true&width=620&lines=A+microservice-based+chess+platform;Built+service+by+service" alt="tagline" />

<br/>

<!-- Frontend -->
[![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Next.js](https://img.shields.io/badge/Next.js-16-000000?logo=nextdotjs&logoColor=white)](https://nextjs.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-v4-06B6D4?logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
[![Expo](https://img.shields.io/badge/Expo-Planned-000020?logo=expo&logoColor=white)](https://expo.dev/)

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

[한국어](README.ko.md) · **English**

</div>

---

## Architecture

```mermaid
flowchart LR
    User([User])
    FE[frontend<br/>Next.js · Expo]
    KC[(Keycloak<br/>PKCE)]
    ARB[arbiter<br/>Spring Boot]
    MQ[(RabbitMQ)]
    DT[deep-thought]
    S3[(MinIO / S3<br/>annotated PGNs)]
    TT[tactician]
    ZZ[zugzwang]
    Syzygy[(Syzygy<br/>Tablebases)]
    DB0[(MySQL<br/>+ Redis)]
    DB1[(MySQL)]
    DB2[(MySQL)]

    User <--> FE
    FE <-. OIDC .-> KC
    FE -- Bearer JWT --> ARB
    ARB -. validates .-> KC
    ARB <-. AMQP .-> MQ
    MQ <-. AMQP .-> DT
    DT -- produces --> S3
    S3 -- nightly mining --> TT
    ARB -- HTTP --> TT
    ARB -- HTTP --> ZZ
    ZZ --> Syzygy
    ARB --> DB0
    TT --> DB1
    ZZ --> DB2
```

`arbiter` is the user-facing API gateway and Keycloak OAuth2 resource server; `frontend` is the only client surface. Annotated PGNs in the shared S3-compatible bucket form the cross-service contract — `deep-thought` produces them, `tactician` consumes them.

---

## Services

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

| Repo | Layer | Role | Stack |
|---|---|---|---|
| [**frontend**](https://github.com/ilovepawn/frontend) | Client | pnpm monorepo — Next.js web today, Expo mobile planned. Talks to Keycloak directly and to Arbiter as Bearer JWT. | TypeScript · Next.js 16 · Tailwind v4 · shadcn/ui · Zustand · TanStack Query · chess.js · chessground · Stockfish (WASM) |
| [**arbiter**](https://github.com/ilovepawn/arbiter) | Gateway | API gateway and OAuth2 resource server. Aggregates platform state, brokers analysis jobs to `deep-thought`, proxies puzzle and endgame calls. | Java 21 · Spring Boot 3.5 · Keycloak · MySQL · Redis · RabbitMQ · Flyway · Prometheus · Grafana |
| [**deep-thought**](https://github.com/ilovepawn/deep-thought) | Worker | Game analysis worker — RabbitMQ-driven Stockfish producing annotated PGNs. | Python · RabbitMQ · Stockfish · MinIO |
| [**tactician**](https://github.com/ilovepawn/tactician) | Service | Tactical puzzle service — daily Stockfish mining + HTTP API. | Python · FastAPI · MySQL · Stockfish |
| [**zugzwang**](https://github.com/ilovepawn/zugzwang) | Service | Endgame trainer — perfect-play opponent via Syzygy tablebases. | Python · FastAPI · MySQL · Syzygy |

---

<div align="center">

<sub>Built by <a href="https://github.com/FickleBoBo">@FickleBoBo</a></sub>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:8957e5,100:1f6feb&height=100&section=footer" alt="" />

</div>
