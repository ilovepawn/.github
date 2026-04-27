<div align="center">

<a href="https://github.com/ilovepawn">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:1f6feb,100:8957e5&height=220&section=header&text=ilovepawn&fontSize=80&fontColor=ffffff&animation=fadeIn&fontAlignY=38" alt="ilovepawn" />
</a>

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&pause=1000&color=58A6FF&center=true&vCenter=true&width=620&lines=A+microservice-based+chess+platform;Built+service+by+service" alt="tagline" />

<br/>

[![Python](https://img.shields.io/badge/Python-3.13-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-009688?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![RabbitMQ](https://img.shields.io/badge/RabbitMQ-FF6600?logo=rabbitmq&logoColor=white)](https://www.rabbitmq.com/)
[![MySQL](https://img.shields.io/badge/MySQL-8.4-4479A1?logo=mysql&logoColor=white)](https://www.mysql.com/)
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
    Platform[Main Platform]
    MQ[(RabbitMQ)]
    DT[deep-thought]
    S3[(MinIO / S3<br/>annotated PGNs)]
    TT[tactician]
    ZZ[zugzwang]
    Syzygy[(Syzygy<br/>Tablebases)]
    DB1[(MySQL)]
    DB2[(MySQL)]

    User <--> Platform
    Platform <-. AMQP .-> MQ
    MQ <-. AMQP .-> DT
    DT -- produces --> S3
    S3 -- nightly mining --> TT
    Platform -- HTTP --> TT
    Platform -- HTTP --> ZZ
    ZZ --> Syzygy
    TT --> DB1
    ZZ --> DB2
```

Annotated PGNs in the shared S3-compatible bucket act as the cross-service contract — `deep-thought` produces them, `tactician` consumes them.

---

## Services

<div align="center">

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

| Repo | Role | Stack |
|---|---|---|
| [**deep-thought**](https://github.com/ilovepawn/deep-thought) | Game analysis worker — RabbitMQ-driven Stockfish producing annotated PGNs | Python · RabbitMQ · Stockfish · MinIO |
| [**tactician**](https://github.com/ilovepawn/tactician) | Tactical puzzle service — daily Stockfish mining + HTTP API | Python · FastAPI · MySQL · Stockfish |
| [**zugzwang**](https://github.com/ilovepawn/zugzwang) | Endgame trainer — perfect-play opponent via Syzygy tablebases | Python · FastAPI · MySQL · Syzygy |

---

<div align="center">

<sub>Built by <a href="https://github.com/FickleBoBo">@FickleBoBo</a></sub>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:8957e5,100:1f6feb&height=100&section=footer" alt="" />

</div>
