# Project Status & Roadmap

## Current stage

Pelagium is preparing for a **closed private beta**.

The web product, authentication flows, journal experience, privacy workflows, operational tooling and production-oriented deployment profile are already implemented and have passed the current local validation gates.

The next milestone is no longer “build the frontend”. It is **real deployment + official WhatsApp integration + first external readers**.

## Stable baseline — v0.15.5

Validated before the official WhatsApp migration:

- React/TypeScript/Vite frontend;
- FastAPI/PostgreSQL backend;
- registration/login/email verification/password reset;
- rotating refresh tokens and revocable sessions;
- journal CRUD, rereads, progress, ratings and notes;
- editable title/author/page metadata;
- personalized journal appearance and decorations;
- cover upload/removal;
- library and statistics views;
- account export/deletion;
- privacy-request workflow;
- privacy-incident workflow;
- retention tooling;
- backup verification and restore drill;
- offsite backup/recovery automation;
- external monitoring;
- production host preflight;
- production deployment gate;
- **234 backend tests**;
- frontend structure/type/build gates;
- **14 operational tests**.

## v0.16 — official WhatsApp migration

In progress:

- provider abstraction;
- WAHA retained temporarily;
- Meta Cloud API sender;
- official webhook route;
- webhook challenge verification;
- HMAC-SHA256 signature validation;
- provider-specific production configuration;
- migration runbook.

Not yet claimed complete:

- real public callback validation;
- permanent Meta credentials;
- final production phone number;
- WAHA removal.

## Private beta sequence

1. refresh public showcase and recruitment copy;
2. buy/confirm domain;
3. recruit the first qualified readers;
4. provision VPS;
5. deploy production stack;
6. validate HTTPS, SMTP, backups and monitoring;
7. complete the real Meta webhook test;
8. onboard 5–10 readers;
9. expand gradually to 20–50 if activation/return signals justify it;
10. use real behavior to decide what to build next.

## AI direction

The current conversational path uses a local LLM. A future architecture milestone will reduce infrastructure pressure by making core journal actions deterministic-first and using AI only where natural-language interpretation or reading-companion behavior adds value.

## What is not claimed

Pelagium is not presented as:

- “100% secure”;
- ready for hundreds/thousands of users without operational evolution;
- proven commercially;
- running a completed official WhatsApp production integration.

The point of the project is to turn those assumptions into measurable operational evidence rather than marketing claims.
