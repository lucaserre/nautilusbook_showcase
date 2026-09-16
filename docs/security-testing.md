# Security Testing Strategy

NautilusBook security validation combines automated tests, integration probes, manual runtime testing and operational checks.

## Current validation layers

### Unit and service tests

Automated tests cover areas such as:

- authentication-session lifecycle;
- refresh-token rotation/reuse behavior;
- webhook HMAC verification;
- WhatsApp allowlist/account linking;
- LID identity normalization;
- journal state transitions;
- multi-book plans;
- title resolution and partial-title recovery;
- image validation;
- HTTP security controls;
- queue/debounce behavior;
- Ollama request configuration.

At the milestone documented here, **76 automated tests** were passing.

### Real LLM probes

Synthetic unit tests cannot guarantee model behavior. Real Ollama probes are therefore executed against the local Qwen model.

Representative scenarios include:

- multiple book updates in one sentence;
- partial-title resolution;
- contextual references without repeating the title;
- deliberate ambiguity that must fail closed.

The latest validation completed **5/5 real probe scenarios**.

### Migration and integrity testing

For schema-changing releases, the process includes:

1. read-only preflight;
2. verified backup;
3. Alembic migration;
4. post-migration integrity script;
5. application test suite.

Examples of invariants checked after migration:

- a `want_to_read` item cannot contain real progress;
- completed readings must be represented consistently;
- reread numbering cannot collide;
- normalized email uniqueness is preserved;
- progress must not exceed a known edition page count.

### Operational validation

The deployment tooling includes checks for:

- backup manifest integrity;
- database dump readability;
- media archive structure;
- production configuration preflight;
- expected Alembic head;
- safe environment configuration.

## Planned AppSec test phase

The frontend milestone will be followed by a dedicated application-security pass.

Priority areas:

1. **Authorization / IDOR** — manipulate reading, note, image and account identifiers across two users.
2. **Authentication** — refresh races, session revocation, password-reset abuse and cookie handling.
3. **Input validation** — malformed JSON, boundary values and oversized requests.
4. **Upload security** — polyglots, corrupt images, decompression bombs and metadata cases.
5. **Webhook abuse** — replay, forged HMACs, burst traffic and duplicate delivery.
6. **LLM safety** — prompt injection, context poisoning and attempts to generate unauthorized plans.
7. **Rate limiting** — bypass attempts through header/IP handling.
8. **Deployment** — exposed ports, TLS configuration, container privileges and secret leakage.
9. **Dependency/image review** — package and container vulnerability scanning.
10. **Restore drill** — prove that a backup can restore the service into a clean environment.

## Testing philosophy

Passing tests does not mean the application is “secure”. Tests are evidence for specific assumptions.

Whenever production behavior contradicts an assumption, the preferred response is:

```text
observe → reproduce → add regression → fix deterministically → retest
```

This process is visible throughout the project’s engineering history.
