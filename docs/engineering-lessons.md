# Engineering Lessons

Pelagium became substantially more interesting when real tests invalidated apparently reasonable assumptions.

## 1. A successful HTTP integration can still be configured twice

A duplicated WAHA webhook resulted in repeated deliveries and HTTP 401 retries.

**Lesson:** verify the full integration configuration, not only application code. Duplicate infrastructure configuration can look like a code bug.

**Control added:** one authoritative webhook configuration plus idempotent processing.

---

## 2. An identifier that looks numeric is not necessarily a phone number

WhatsApp delivered an opaque `@lid` identity. The first implementation stripped the suffix and stored the remaining digits as a phone number.

**Lesson:** identity semantics matter more than string shape.

**Control added:** separate messaging identity from phone identity and resolve phone information only when available.

---

## 3. Exactly-once delivery is the wrong assumption

Retries can deliver the same event multiple times.

**Lesson:** webhook correctness should be based on idempotency, not delivery guarantees.

**Control added:** persistent external message IDs and replay-safe processing.

---

## 4. A model can be “mostly correct” and still corrupt durable state

An early model extracted the right general action but omitted book titles or pages. Later, conversational context caused an explicit book update to be applied to the previously active title.

**Lesson:** semantic confidence is not enough when output becomes a database mutation.

**Controls added:** structured plans, deterministic field recovery, catalog resolution, explicit-title precedence and fail-closed ambiguity.

---

## 5. One user sentence can contain more than one transaction intent

A single-intent schema could not represent “update Book A to page 120 and Book B to page 50”.

**Lesson:** the data contract must represent the user’s actual language, not force language into an overly narrow model.

**Control added:** bounded multi-operation plans.

---

## 6. Debounce is not just `sleep()`

Messages sent in quick succession were still answered individually when the second message arrived while the first inference was already running.

**Lesson:** temporal grouping must account for work already in progress.

**Control added:** persistent inbox, deferred responses and a final pending-message check before sending.

---

## 7. Domain invariants need more than one enforcement point

Historical data contained a reading marked `want_to_read` despite having progress.

**Lesson:** old versions, alternate routes and migrations can bypass assumptions made in one service layer.

**Controls added:** service rules, API validation, database constraints and migration-time repair.

---

## 8. Configuration types can become protocol bugs

`OLLAMA_KEEP_ALIVE=-1` was read as a string and serialized as a JSON string, while the Ollama API expected a numeric `-1` or a duration string.

Result: every LLM request returned HTTP 400 even though the model itself was healthy.

**Lesson:** environment variables are strings; protocol payloads still require typed normalization.

**Control added:** configuration normalization plus a regression test.

---

## 9. Security hardening can create developer-experience side effects

Running the application container as a non-root user caused pytest cache permission warnings.

**Lesson:** security controls need operational feedback loops. A warning is not automatically a reason to weaken the control.

**Resolution:** move disposable test cache to a writable temporary path.

---

## 10. AI-assisted development still requires ownership

Several generated solutions looked reasonable but failed under actual integration testing.

**Lesson:** AI assistance increases implementation speed, not certainty.

The useful workflow has been to treat generated code as a hypothesis that must survive testing and review.
