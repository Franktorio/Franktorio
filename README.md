<div align="center">

# Franktorio

### Python · TypeScript · Application architecture · Database systems

I build applications from the data model through the API and frontend: business management systems, gym platforms, automated grading, and data collection tools.

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)

[Current systems](#current-systems) · [Architecture](#architecture-and-infrastructure) · [Public repositories](#public-repositories)

</div>

---

## Current systems

### Maciel Romo

A consolidated **business operations platform** with a bilingual public website, storefront, and permission-scoped employee portal.

| Domain | Application scope |
| :--- | :--- |
| **Retail operations** | Multi-store inventory, product variants, replenishment, purchasing, point-of-sale workflows, and store-level employee assignments. |
| **Production / workshop** | Orders and backlog, artwork status, work assignments, production progress, materials, losses, shipping, and receipt of goods by stores. |
| **Finance** | Sales and purchase records, expenses and salaries, daily cash closes, store balances, capital transactions, profit reporting, and company-level dashboards. |
| **Commerce** | Product publishing, customer accounts, checkout, order administration, payment handling, shipping quotations, and customer inquiries. |
| **Web development operations** | Application records, employee assignments, billing, support tickets, and remote service monitoring. |
| **Administration** | Employee access, granular permissions, internal notifications, and audit history. |

**React + TypeScript + Vite** frontend, **FastAPI** API, and **PostgreSQL** persistence through async **SQLAlchemy**. Public pages and the employee portal share a frontend build, with separate session and access boundaries.

### Barras Armadas

A **gym management and training platform** connecting public enrollment with member, coach, and administrator interfaces.

| Domain | Application scope |
| :--- | :--- |
| **Member lifecycle** | Enrollment, account activation, membership management, reactivation, profiles, and preferences. |
| **Scheduling / attendance** | Class definitions, recurring schedule presets, capacity and role restrictions, reservations, and reservation history. |
| **Training data** | Exercise and workout catalogs, ordered workout tasks, benchmark definitions, recorded results, personal records, and leaderboards. |
| **Staff operations** | Coach interfaces, member administration, product tabs, schedule management, and operational metrics. |

**React + TypeScript + Vite** frontend backed by **FastAPI, PostgreSQL, and Redis**, with domain APIs and role-scoped interfaces.

### Database service

An extensible **application backend foundation** used by the systems above. Product modules build on a common system layer for identity, access control, persistence, and operations.

- **Identity and access:** user and role management, tiered API keys, password hashing, browser sessions, and server-side revocation.
- **Request controls:** Redis-backed rate limiting, permission caching, IP blocking, and write-path cache invalidation.
- **Persistence:** async database sessions, ORM models, dedicated CRUD modules, migrations, and audit records.
- **Operations:** scheduled PostgreSQL backups with retention, health checks, configurable recovery, session cleanup, rotating logs, and supervised background tasks with restart backoff.
- **Integration services:** transactional email, outbound HTTP validation, and a versioned monitoring interface.
- **Deployment tooling:** environment validation, typed service configuration, database/cache provisioning scripts, and backup restore utilities.

The three codebases share infrastructure conventions while retaining application-specific data models, workflows, permissions, and Redis behavior. Their repositories are currently private.

## Architecture and infrastructure

| Layer | Approach / technologies |
| :--- | :--- |
| **Frontend** | React · TypeScript · Vite · routed public and authenticated interfaces · Jinja2 in the grading application |
| **API** | Python · FastAPI · Uvicorn · asyncio · validated request models · REST endpoints |
| **Data** | PostgreSQL · SQLAlchemy 2 async · asyncpg · Alembic · SQLite |
| **Application boundaries** | Domain routers and CRUD modules · explicit database sessions · role and assignment scopes |
| **Infrastructure** | Redis caching and Lua operations · background task supervision · backups and recovery |
| **Integrations** | Discord API · Brevo · Stripe · shipping quotation services |
| **Verification / operations** | GitHub Actions · automated regression tests · audit logs · metrics · Nginx and systemd deployment configuration |

## Public repositories

### [Bulldog Simple Grader](https://github.com/Franktorio/bulldog-simple-grader)

An **assignment, code-submission, and automated evaluation system** built with FastAPI, Jinja2, and SQLite.

Instructors define assignments and test suites; students submit files through a web interface. The evaluation pipeline runs submissions in Linux namespaces using `unshare`, with network isolation and CPU/memory limits, then records results for instructor review.

Includes dedicated student/instructor authentication, submission and completion tracking, database initialization, rotating logs, backups, replicas, and recovery tooling.

<details>
<summary><strong>Data collection and Discord systems</strong></summary>

### [Franktorio Pressure Scanner](https://github.com/Franktorio/franktorio-pressure-scanner)

Collection and analysis tooling for the Roblox game *Pressure*, with **200,000+ recorded room encounters**.

### [Franktorio & xSoul's Lab](https://github.com/Franktorio/franktorio-xsouls-lab)

A Discord bot for querying collected data and supporting the scanner backend.

These projects are no longer maintained; their former web endpoints are offline.

</details>

## Exploring

Application architecture, data consistency, async service design, and infrastructure that can be reused across codebases. Also expanding my experience with AWS and Cloudflare.
  
