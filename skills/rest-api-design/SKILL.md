---
name: REST API Design
id: skill/rest-api-design
currentVersion: 1.0.1
scope: enterprise
adoptionPolicy: auto
optedIn: true
category: backend
popularity: "top-15"
description: Design predictable, resource-oriented HTTP APIs with correct verbs, status codes, versioning, consistent error envelopes, and graceful rate-limit handling.
tokensSavedPerUse: 1744
useCases: [ "Modeling resources and routes", "Choosing correct HTTP verbs/status codes", "Versioning and error-envelope conventions", "Handling 429 / rate limits gracefully" ]
---

# REST API Design  `skill/rest-api-design@1.0.1`

Design predictable, resource-oriented HTTP APIs with correct verbs, status codes, versioning, and consistent error envelopes.

## Canonical guidance

Model the API around nouns (resources), not verbs: `/orders/{id}/items`, never `/getOrderItems`. Use HTTP verbs for intent — GET (safe, idempotent), POST (create), PUT (full replace, idempotent), PATCH (partial), DELETE (idempotent). Return accurate status codes: 200/201/204 success, 400 validation, 401 unauthenticated, 403 unauthorized, 404 missing, 409 conflict, 422 semantic, 429 throttled, 5xx server. Version at the edge (`/v1`) and never break a published contract — add, don't mutate. Always return a consistent error envelope (`{error:{code,message,details,traceId}}`) so clients can branch on a stable `code`. Paginate collections, never return unbounded lists, and document with OpenAPI as the source of truth.

**Rate limits are part of the contract, on both sides.** As a server, return `429 Too Many Requests` with a `Retry-After` header rather than failing opaquely, and surface remaining quota (`RateLimit-*` headers) so clients can self-pace. As a *client* of an upstream API, treat `429`/5xx as expected back-pressure — not a crash — by honoring `Retry-After`, backing off with jitter, and degrading gracefully instead of hammering a limited server. Distilled from a real session where unhandled provider rate limits surfaced as cascading API errors.

## Use cases

- Modeling resources and routes
- Choosing correct HTTP verbs/status codes
- Versioning and error-envelope conventions
- Handling 429 / rate limits gracefully (server-side headers + client-side backoff)

## Provenance

The `1.0.0` seed was **seeded from community best practice** as one of the *top-15*
popular real-world engineering skills, then admitted to the enterprise registry under
capsule **CAP-P001** (category `backend`). Later versions follow the normal RL loop —
distilled from real Claude Code sessions via local Ollama, durable memory in Backboard.

### Latest version `1.0.1` — learned from a real session

Version `1.0.1` was distilled from a **real Claude Code session** (`12560ca4`) via local
Ollama (`qwen2.5-coder:14b`) and promoted as capsule **CAP-DEE-01**. The capsule briefing
is persisted in **Backboard** (thread `f094d4af-c5b7-40c6-bdac-b2b027e44f71`).

> **Finding (CAP-DEE-01):** Implement rate limiting handling in your application to gracefully manage API errors due to server limitations.

Classifier fit to this skill: **0.80** · session transfer score **37/100** (local-model proxy).

## Token savings

Each reuse of this skill saves **1744 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull rest-api-design@1.0.1     # pin this exact version
capsule pull rest-api-design                          # latest published
```
