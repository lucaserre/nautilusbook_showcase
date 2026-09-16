# GitHub Publication Checklist

Use this checklist before making `nautilusbook-showcase` public.

## 1. Use a separate repository

Do **not** change the private product repository to public.

Create a new repository such as:

```text
nautilusbook-showcase
```

Only push the contents of this showcase directory.

## 2. Do not import private Git history

Early product versions contained real development secrets. Even if those credentials were rotated, they should not enter the public repository history.

Create a fresh Git history for the showcase.

## 3. Inspect files locally

Before the first commit:

```bash
git init
git add .
git status
```

Expected content is documentation and screenshot assets only.

There should be no:

- `.env`;
- database dump;
- backup;
- WAHA session;
- phone number;
- private product source;
- generated logs;
- credential file.

## 4. Search for likely secrets

Examples:

```bash
git grep -n "SECRET_KEY"
git grep -n "WAHA_API_KEY"
git grep -n "POSTGRES_PASSWORD"
git grep -n "WHATSAPP_HOOK_HMAC_KEY"
```

In this documentation repository, these terms should normally be absent or mentioned only as generic concepts — never with real values.

Also search for your real phone number, personal e-mail if you do not want it public, server IPs and domain names.

## 5. First commit

Example:

```bash
git commit -m "Initial NautilusBook engineering showcase"
git branch -M main
```

## 6. GitHub settings

Recommended:

- create the repository **Private** first;
- inspect the rendered Markdown and Mermaid diagrams;
- enable GitHub secret scanning / push protection when available;
- enable Private Vulnerability Reporting if available;
- disable Wikis/Projects if you do not intend to maintain them;
- add repository topics such as `appsec`, `cybersecurity`, `fastapi`, `docker`, `postgresql`, `ollama`, `llm-security`, `threat-modeling`.

After review, switch only the showcase repository to **Public**.

## 7. Add screenshots last

Screenshots are a common source of accidental disclosure.

Before committing an image, inspect for:

- phone numbers;
- e-mail addresses;
- tokens/API keys;
- local usernames and filesystem paths;
- browser bookmarks;
- WhatsApp contact names/photos;
- IP addresses;
- private repository URLs.

Use synthetic demo accounts whenever possible.

## 8. Final review from a clean clone

After pushing privately:

```bash
git clone <private-showcase-url> review-copy
```

Open that clean clone as if you were an external recruiter. If everything visible is acceptable, make the repository public.
