---
name: OAuth2 / JWT Auth
id: skill/oauth2-jwt-auth
currentVersion: 1.0.1
scope: enterprise
adoptionPolicy: auto
optedIn: true
category: backend
popularity: "top-15"
description: Implement standards-compliant OAuth2 flows and JWT validation (short-lived access, rotated refresh, verified signatures) AND fail fast on bad credentials — pre-flight validation + terminal 401 handling instead of retry storms.
tokensSavedPerUse: 1653
useCases: [ "Authorization Code + PKCE flows", "Validating JWT signature/claims", "Access/refresh token rotation", "Pre-flight credential validation to avoid 401 storms" ]
---

# OAuth2 / JWT Auth  `skill/oauth2-jwt-auth@1.0.1`

Implement standards-compliant OAuth2 flows and JWT validation: short-lived access tokens, rotated refresh tokens, and verified signatures.

## Canonical guidance

Use the Authorization Code flow with PKCE for user-facing clients and Client Credentials for service-to-service; never ship the implicit flow or password grant. Keep access tokens short-lived (5-15 min) and rotate refresh tokens on every use, revoking the whole family on reuse detection. On every request validate the JWT fully: verify the signature against the IdP's JWKS (cache keys, honor `kid`), then check `iss`, `aud`, `exp`, `nbf`, and `scope`/roles — a token that merely decodes is not a token that is valid. Treat tokens as bearer secrets: TLS only, never in URLs or logs. Prefer asymmetric (RS256/ES256) so resource servers verify without the signing key.

**Validate credentials at the boundary, fail fast, don't hammer.** Before making authenticated outbound requests, verify the credential actually exists and is well-formed (present, non-expired, correct issuer/scope) rather than discovering it is wrong mid-flight. When an upstream returns `401 Invalid authentication credentials`, treat it as a **terminal auth failure** for that credential — surface a clear error and stop, instead of blindly retrying and producing a storm of repeated 401s. Refresh-then-retry exactly once on a genuinely *expired* token; for an *invalid* one, re-authenticate rather than loop. Distilled from a real session where unvalidated API credentials caused cascading repeated `401 Invalid authentication credentials` errors.

## Use cases

- Authorization Code + PKCE flows
- Validating JWT signature/claims
- Access/refresh token rotation
- Pre-flight credential validation + fail-fast 401 handling (avoid retry storms)

## Provenance

The `1.0.0` seed was **seeded from community best practice** as one of the *top-15*
popular real-world engineering skills, then admitted to the enterprise registry under
capsule **CAP-P002** (category `backend`; seed transfer **80**/novelty **64**/importance **72**,
Backboard thread `0b6f49a7-96fd-6d52-46b0-62d7fac43be8`). Later versions follow the normal
RL loop — distilled from real Claude Code sessions via local Ollama, durable memory in Backboard.

### Latest version `1.0.1` — learned from a real session

Version `1.0.1` was distilled from a **real Claude Code session** (`b505be13`) via local
Ollama (`qwen2.5-coder:14b`) and promoted as capsule **CAP-DEE-01**. The capsule briefing
is persisted in **Backboard** (thread `90466bf8-4b15-4065-a1ee-1b2d4bee9e57`).

> **Finding (CAP-DEE-01):** Always validate API credentials before making requests to avoid repeated `401 Invalid authentication credentials` errors.

Classifier fit to this skill: **0.90** · session transfer score **54/100** (local-model proxy).

## Token savings

Each reuse of this skill saves **1653 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull oauth2-jwt-auth@1.0.1     # pin this exact version
capsule pull oauth2-jwt-auth                          # latest published
```
