# Screenshot Guide

Screenshots can make the showcase much stronger, but only if they are sanitized.

## Recommended screenshots

### 1. Docker stack

Show containers running, preferably with only generic service names visible.

Good signal:

- API;
- PostgreSQL;
- WAHA;
- Ollama;
- worker;
- maintenance process.

Avoid showing environment variables or mounted secret paths.

### 2. Swagger / API documentation

Use a synthetic local account and show a small portion of the API surface.

Good candidates:

- journal endpoints;
- authentication/session endpoints;
- account export/delete endpoint names.

Do not show tokens in the authorization dialog.

### 3. WhatsApp demo

Use a dedicated/synthetic contact if possible.

Example conversation:

```text
User: I started reading Dune.
User: I'm on page 120.
User: Update Dune to 130 and Foundation to 50.
NautilusBook: [sanitized successful response]
```

Blur/hide:

- phone numbers;
- profile photos;
- unrelated chats;
- timestamps if they reveal private context.

### 4. Architecture diagram

GitHub renders the Mermaid diagrams in this repository. A screenshot of the rendered architecture can also be used on LinkedIn.

### 5. Security/testing evidence

A terminal screenshot with:

```text
76 passed
```

and a sanitized:

```text
Result: 5/5 scenarios passed
```

is useful evidence without publishing private code.

## Suggested LinkedIn carousel order

1. NautilusBook title / one-line product concept;
2. architecture diagram;
3. WhatsApp demo;
4. security controls / threat model summary;
5. test result screenshot;
6. “What broke and what I learned” summary.
