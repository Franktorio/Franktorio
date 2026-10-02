<div align="center">

# Franktorio

### Python · Async APIs · Database services · Web applications

I build FastAPI backends, database layers, and React frontends, with a focus on authentication, application workflows, and shared service infrastructure.

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)

[Current systems](#current-systems) · [Stack](#stack) · [Public repositories](#public-repositories)

</div>

---

## Current systems

| Codebase | Architecture and scope |
| :--- | :--- |
| **Maciel Romo** | React + Vite frontend with a FastAPI API, async SQLAlchemy, and PostgreSQL. Public site and employee portal backed by workshop, catalog, inventory, purchasing, sales, finance, and reporting modules. |
| **Barras Armadas** | FastAPI + PostgreSQL + Redis backend with a React frontend. Domain APIs for class scheduling, reservations, memberships, workout definitions, exercise results, and member preferences. |
| **Database service** | Reusable backend foundation for authentication, authorization, database access, audit logging, monitoring, and transactional email. Shared implementations maintained across the application codebases. |

### Shared backend work

- **Sessions:** signed JWT cookies with stable session IDs, explicit renewal through `POST /me/refresh`, expiry validation, revocation, and permission-cache invalidation.
- **Email:** shared Brevo HTTP transport with asynchronous dispatch, validated responses, configurable sender identity, and application-specific templates.
- **Outbound HTTP:** destination validation, DNS pinning, TLS hostname verification, redirect rejection, request/response size limits, and connection/read timeouts.
- **Monitoring:** a versioned remote metrics contract and structured HTTP operation/failure logs.
- **Regression coverage:** GitHub Actions checks for session routes, token renewal, email transport, outbound HTTP protections, and monitoring behavior.

Domain logic, session lifetimes, and Redis implementations remain application-specific. These codebases are currently private.

## Stack

| Layer | Technologies |
| :--- | :--- |
| **API / runtime** | Python · FastAPI · Uvicorn · asyncio · REST |
| **Persistence** | PostgreSQL · SQLAlchemy 2 async · asyncpg · Alembic · SQLite |
| **Cache / access controls** | Redis · JWT cookies · role-based authorization · rate limiting |
| **Frontend** | React · Vite · Jinja2 |
| **Integrations** | Brevo HTTP API · Discord API |
| **Tooling / operations** | Git · GitHub Actions · unittest · logging · monitoring · database backups |

## Public repositories

### [Bulldog Simple Grader](https://github.com/Franktorio/bulldog-simple-grader)

A code-submission and automated evaluation system built with **FastAPI, Jinja2, and SQLite**.

- Linux namespace isolation using `unshare`, network restrictions, and CPU/memory limits.
- Assignment test suites, submission tracking, and separate instructor/student routes.
- Database initialization, backups, replicas, and recovery tooling.

<details>
<summary><strong>Earlier systems: data collection and Discord integration</strong></summary>

### [Franktorio Pressure Scanner](https://github.com/Franktorio/franktorio-pressure-scanner)

Data collection and analysis tooling for the Roblox game *Pressure*, with **200,000+ recorded room encounters**.

### [Franktorio & xSoul's Lab](https://github.com/Franktorio/franktorio-xsouls-lab)

Discord integration for querying collected data and supporting the scanner backend.

These projects are no longer maintained; their former web endpoints are offline.

</details>

## Exploring

Shared service boundaries, authentication edge cases, async database access, and regression testing across multiple applications. Also expanding my experience with AWS and Cloudflare.
  
