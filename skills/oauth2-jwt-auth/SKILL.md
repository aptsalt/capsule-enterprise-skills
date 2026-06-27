---
name: OAuth2 / JWT Auth
id: skill/oauth2-jwt-auth
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
category: backend
popularity: "top-15"
description: Implement standards-compliant OAuth2 flows and JWT validation: short-lived access tokens, rotated refresh tokens, and verified signatures.
tokensSavedPerUse: 1653
useCases: [ "Authorization Code + PKCE flows", "Validating JWT signature/claims", "Access/refresh token rotation" ]
---

# OAuth2 / JWT Auth  `skill/oauth2-jwt-auth@1.0.0`

Implement standards-compliant OAuth2 flows and JWT validation: short-lived access tokens, rotated refresh tokens, and verified signatures.

## Canonical guidance

Use the Authorization Code flow with PKCE for user-facing clients and Client Credentials for service-to-service; never ship the implicit flow or password grant. Keep access tokens short-lived (5-15 min) and rotate refresh tokens on every use, revoking the whole family on reuse detection. On every request validate the JWT fully: verify the signature against the IdP's JWKS (cache keys, honor `kid`), then check `iss`, `aud`, `exp`, `nbf`, and `scope`/roles — a token that merely decodes is not a token that is valid. Treat tokens as bearer secrets: TLS only, never in URLs or logs. Prefer asymmetric (RS256/ES256) so resource servers verify without the signing key.

## Use cases

- Authorization Code + PKCE flows
- Validating JWT signature/claims
- Access/refresh token rotation

## Provenance (current version)

Version `1.0.0` was **seeded from community best practice** as one of the *top-15*
popular real-world engineering skills, then admitted to the enterprise registry under
capsule **CAP-P002** (category `backend`). Future versions follow the normal RL loop —
distilled from real Claude Code sessions via local Ollama, durable memory in Backboard.

> **Seed finding:** Implement standards-compliant OAuth2 flows and JWT validation: short-lived access tokens, rotated refresh tokens, and verified signatures.

Seed transfer score: **80/100** · novelty **64** · importance **72**.
Briefing persisted in **Backboard** (thread `0b6f49a7-96fd-6d52-46b0-62d7fac43be8`).

## Token savings

Each reuse of this skill saves **1653 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull oauth2-jwt-auth@1.0.0     # pin this exact version
capsule pull oauth2-jwt-auth                          # latest published
```
