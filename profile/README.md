<div align="center">

# ilovepawn

**A microservice-based chess platform** — built service by service, each named after a piece of chess history.

[🇰🇷 한국어](README.ko.md) · 🇬🇧 English

</div>

---

## Services

| Repo | Role | Stack |
|---|---|---|
| [**deep-thought**](https://github.com/ilovepawn/deep-thought) | Game analysis worker — RabbitMQ-driven Stockfish producing annotated PGNs | Python · RabbitMQ · Stockfish · MinIO |
| [**tactician**](https://github.com/ilovepawn/tactician) | Tactical puzzle service — daily Stockfish mining + HTTP API | Python · FastAPI · MySQL · Stockfish |
| [**zugzwang**](https://github.com/ilovepawn/zugzwang) | Endgame trainer — perfect-play opponent via Syzygy tablebases | Python · FastAPI · MySQL · Syzygy |

## Architecture

Services communicate via RabbitMQ (async work) and HTTP (sync queries). Annotated PGNs in a shared S3-compatible bucket act as the cross-service contract — `deep-thought` produces them, `tactician` consumes them.

---

<div align="center">
<sub>Built by <a href="https://github.com/FickleBoBo">@FickleBoBo</a></sub>
</div>
