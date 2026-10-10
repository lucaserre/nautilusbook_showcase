# Privacy & Data Lifecycle

Pelagium handles personal reading data and messaging identifiers. Privacy requirements are therefore part of the backend design rather than a future UI-only concern.

## Data categories

The application may process:

- account identity and authentication metadata;
- WhatsApp messaging identity and, when resolvable, phone number;
- book/edition metadata;
- reading progress, ratings and journal notes;
- uploaded personalized covers;
- short conversational context required to interpret journal commands;
- security/audit metadata needed for authentication and abuse prevention.

## Lifecycle principles

### Minimize

Only data required for product behavior, account security and operations should be retained.

### Separate identity concepts

Messaging identity and phone identity are modeled independently because they have different semantics and availability.

### User ownership

Reading data and personalized media are scoped to the owning account.

### Export

The backend includes an account export workflow so a user can retrieve structured application data associated with the account.

### Delete

Account deletion is designed to remove user-owned domain data and personalized media rather than merely deactivate login.

### Retain intentionally

Operational history such as inbox events, authentication audit records and expired tokens has configurable retention rather than unlimited growth.

## Backups

Backups create an additional data lifecycle obligation. A deletion from the live database does not instantly rewrite historical offline backups.

A production privacy policy should therefore document backup retention and the practical deletion window for historical copies.

## Public showcase boundary

This repository contains no real user data, messaging sessions, backups, phone numbers, tokens or production logs.
