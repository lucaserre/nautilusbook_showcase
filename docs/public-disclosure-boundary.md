# Public Disclosure Boundary

NautilusBook is intended to become a commercial product. This public repository therefore documents engineering decisions without publishing the complete implementation.

## Public here

- high-level architecture;
- security controls and rationale;
- threat model;
- testing strategy;
- engineering lessons;
- technology stack;
- public-safe roadmap;
- AI-assistance disclosure;
- selected screenshots without personal data.

## Kept private

- product source code;
- complete prompts and model instructions;
- private database schema/migration details beyond what is necessary to explain architecture;
- `.env` files and secrets;
- JWT/HMAC/WAHA keys;
- WhatsApp sessions and QR information;
- database dumps and backups;
- user/phone/message data;
- infrastructure addresses and administrative credentials;
- private product roadmap and commercial strategy;
- historical repository versions that contained secrets during early development.

## Why this boundary exists

Security should not depend on source-code secrecy. However, that does not require publishing commercial intellectual property.

The goals are separate:

- **security:** controls should remain effective even when architecture is understood;
- **commercial exclusivity:** the private implementation and product differentiation do not need to be given away to demonstrate engineering competence.

This repository is therefore a case study, not an open-source distribution of NautilusBook.
