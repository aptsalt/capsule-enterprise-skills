---
name: REST API Design
id: skill/rest-api-design
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
category: backend
popularity: "top-15"
description: Design predictable, resource-oriented HTTP APIs with correct verbs, status codes, versioning, and consistent error envelopes.
tokensSavedPerUse: 1744
useCases: [ "Modeling resources and routes", "Choosing correct HTTP verbs/status codes", "Versioning and error-envelope conventions" ]
---

# REST API Design  `skill/rest-api-design@1.0.0`

Design predictable, resource-oriented HTTP APIs with correct verbs, status codes, versioning, and consistent error envelopes.

## Canonical guidance

Model the API around nouns (resources), not verbs: `/orders/{id}/items`, never `/getOrderItems`. Use HTTP verbs for intent — GET (safe, idempotent), POST (create), PUT (full replace, idempotent), PATCH (partial), DELETE (idempotent). Return accurate status codes: 200/201/204 success, 400 validation, 401 unauthenticated, 403 unauthorized, 404 missing, 409 conflict, 422 semantic, 429 throttled, 5xx server. Version at the edge (`/v1`) and never break a published contract — add, don't mutate. Always return a consistent error envelope (`{error:{code,message,details,traceId}}`) so clients can branch on a stable `code`. Paginate collections, never return unbounded lists, and document with OpenAPI as the source of truth.

## Use cases

- Modeling resources and routes
- Choosing correct HTTP verbs/status codes
- Versioning and error-envelope conventions

## Provenance (current version)

Version `1.0.0` was **seeded from community best practice** as one of the *top-15*
popular real-world engineering skills, then admitted to the enterprise registry under
capsule **CAP-P001** (category `backend`). Future versions follow the normal RL loop —
distilled from real Claude Code sessions via local Ollama, durable memory in Backboard.

> **Seed finding:** Design predictable, resource-oriented HTTP APIs with correct verbs, status codes, versioning, and consistent error envelopes.

Seed transfer score: **66/100** · novelty **71** · importance **87**.
Briefing persisted in **Backboard** (thread `a6c7056c-91e0-ba3e-1092-c926f654b9f5`).

## Token savings

Each reuse of this skill saves **1744 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull rest-api-design@1.0.0     # pin this exact version
capsule pull rest-api-design                          # latest published
```
