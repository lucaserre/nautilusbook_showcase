# Security Testing Strategy

Pelagium security validation combines automated tests, integration probes, manual runtime testing and operational gates.

## Current stable validation snapshot

At the v0.15.5 stable baseline:

- **234 backend tests** pass;
- frontend `structure-check` passes;
- TypeScript typecheck passes;
- production frontend build passes;
- **14 operational unittest cases** pass;
- pilot gate passes;
- production structure gate passes;
- Alembic current/head checks pass;
- critical auth/journal flows have been smoke-tested manually.

The v0.16 WhatsApp Cloud API branch adds additional provider/webhook tests while the official integration is still in progress.

## Coverage areas

Automated tests currently exercise areas including:

- authentication-session lifecycle;
- refresh rotation/reuse;
- password policy;
- password reset and verification tokens;
- authorization/ownership boundaries;
- horizontal IDOR cases;
- optimistic concurrency;
- malformed/boundary contracts;
- webhook HMAC/signature validation;
- WhatsApp allowlist/linking;
- message deduplication;
- journal state transitions;
- rereads;
- page-count/edition behavior;
- metadata editing isolation;
- journal decorations/templates/freeform state;
- XSS-preservation cases;
- library/statistics aggregation;
- image handling;
- HTTP security controls;
- queue/debounce behavior;
- observability and route topology.

## LLM probes

Synthetic tests do not prove model behavior. Real Ollama probes are used for conversational scenarios such as:

- multi-book operations;
- partial-title resolution;
- contextual references;
- deliberate ambiguity.

The LLM is not trusted to enforce authorization or persistence invariants.

## Migration/integrity validation

Schema-changing releases use:

1. preflight;
2. verified backup;
3. Alembic migration;
4. integrity checks;
5. automated suite;
6. smoke/manual gates when behavior changes.

## Operational validation

Operational tooling covers:

- backup manifest integrity;
- dump/archive verification;
- restore drill;
- offsite backup/revalidation;
- host preflight;
- external monitoring;
- production configuration safety;
- container exposure/hardening;
- expected Alembic state.

## Testing philosophy

Passing tests is evidence for specific assumptions, not proof that the product is “secure”.

The preferred loop is:

```text
observe → reproduce → regression test → deterministic fix → retest
```

This pattern has repeatedly driven the architecture of the project.
