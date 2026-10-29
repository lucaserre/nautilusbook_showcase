# Pelagium — Project Status & Roadmap

**Reference:** 28 October 2026. This document summarizes reported private-development milestones. It is not a live production status dashboard.

## Existing application

- React/TypeScript frontend for authentication, reading library, individual journal entries and progress, covers, statistics and personalized journal views.
- FastAPI/SQLAlchemy/PostgreSQL backend, authentication, per-user records, Alembic migrations and media storage.
- Optional conversational/WhatsApp infrastructure and production-oriented Compose/Caddy configuration.
- Security and operations tooling including verification gates and restore drills.

**None of the above means a public beta has been deployed.** In particular, documentation/legal readiness, real SMTP, VPS hardening, external backups and an end-to-end production gate remain separate requirements.

## Private local verification milestones

| Track | Result reported | Boundary |
|---|---|---|
| Local personal stack | Multiple isolated Windows/Docker installation and encrypted-recovery drills | Technical laboratory tooling; not an end-user installer |
| OFFLINE-3 | Journal functions, local search/media and persistence exercised with internet disconnected | On the original computer |
| OFFLINE-4a / 4b | Verifiable transfer kit, OCI identity attestation and four images imported on a second physical PC | Image transfer is not complete journal recovery |
| OFFLINE-4c1 / 4c2 / 4c3 | Preflight, M → R recovery and integrity/persistence checks reported successful | Locally on the source computer; full second-PC restore not yet approved |
| Desktop distribution | DESKTOP-1 feasibility assessment started | No Docker-free executable or installer built |

All quoted results are scoped to their own tests, tools and environments. Do not generalize them into a 100% security claim.

## Priority 1 — DESKTOP-1: feasibility and design

The target experience is **one ordinary Windows installer**. A reader must not have to install or operate Docker, Python, PostgreSQL or a terminal; use of the offline journal must not depend on a remote domain.

The candidate architecture retains the React interface and local business rules. A compact desktop shell (e.g. Tauri), a packaged local backend and an independently persistent journal/media directory are under evaluation. The database decision is **open**: validate SQLite compatibility before selecting SQLite or privately bundled PostgreSQL.

Acceptance requires safe local-only communication, automatic start/stop, no port conflict or unauthorized network exposure, offline WebView runtime support, backup/import/export flows, update/uninstall preservation and a fresh Windows installation test.

## Priority 2 — desktop implementation

1. **DESKTOP-2:** integrate shell, bundled backend and chosen database; clean local lifecycle.
2. **DESKTOP-3:** produce a Windows installer with fully local prerequisites and no post-install internet requirement.
3. **DESKTOP-4:** expose journal import/export, backups and recovery through a user interface, including a safe path from an existing accessible journal.
4. **DESKTOP-5:** test clean installation, offline use, upgrades, rollback, uninstall and restores on a second Windows PC without Docker.

These milestones are **planned**, not delivered.

## Parallel track — controlled online beta

The online edition is separate. Before external testers: approve legal versions, invitation-only registration, email verification through real SMTP, HTTPS/DNS, host hardening, production migrations, verified off-host backups, restore drills and horizontal authorization checks.

Optional AI/WhatsApp operation should be evaluated separately for hosting cost and security. The beta can prioritize the core web journal, but existing Compose service dependencies require review before disabling optional components.

## Release boundaries

- **No desktop installer, public distribution package, public VPS beta or service availability claim is authorized by this status page.**
- The public showcase does not contain the private code or recovery materials.
- Reported offline proofs are not substitutes for an independent second-PC end-to-end journal restore or a security assessment.
