# Project Status & Roadmap

## Current stage

NautilusBook currently has a mature backend foundation and is moving into frontend development.

The backend is suitable for continued integration work and controlled testing. It is **not presented as a fully production-ready public SaaS** yet.

## Completed backend capabilities

- account registration/authentication;
- revocable sessions and rotating refresh tokens;
- journal CRUD and domain invariants;
- rereads;
- optional ISBN/edition metadata;
- notes, ratings and progress;
- personalized cover upload;
- WhatsApp account linking;
- WhatsApp queue/worker processing;
- multi-book natural-language operations;
- partial-title/catalog resolution;
- local LLM integration;
- backup/verification tooling;
- account export/deletion;
- retention maintenance;
- production-oriented container hardening.

## Next product milestone — frontend v1

Planned first frontend scope:

1. registration and login;
2. journal dashboard;
3. reading status/progress controls;
4. book details and notes;
5. reread history;
6. cover management;
7. WhatsApp linking/status;
8. account/security settings;
9. export/delete workflows.

## Security milestone after the frontend

The frontend will make several classes of authorization and browser-security testing meaningful for the first time.

Planned AppSec phase:

- horizontal IDOR testing;
- cookie/session behavior;
- CSRF review based on final browser architecture;
- CSP design;
- XSS testing;
- upload attack corpus;
- rate-limit bypass;
- LLM prompt-injection/abuse testing;
- dependency and container scanning;
- real staging deployment review.

## Before public beta

- successful restore drill in a clean environment;
- production host/firewall validation;
- HTTPS + DNS;
- real SMTP delivery;
- off-host backups;
- monitoring/alerting;
- vulnerability scanning;
- documented incident/secret-rotation process;
- final privacy and terms documentation.
