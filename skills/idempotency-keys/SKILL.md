---
name: Idempotency Keys
id: skill/idempotency-keys
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
category: backend
popularity: "top-15"
description: Make unsafe POST/payment operations safe to retry by deduplicating on a client-supplied idempotency key.
tokensSavedPerUse: 1660
useCases: [ "Safe retries for POST/payments", "Client-supplied Idempotency-Key handling", "Storing and replaying first responses" ]
---

# Idempotency Keys  `skill/idempotency-keys@1.0.0`

Make unsafe POST/payment operations safe to retry by deduplicating on a client-supplied idempotency key.

## Canonical guidance

Let clients send an `Idempotency-Key` header (a UUID) on any non-idempotent request. Server-side, persist the key with the request fingerprint and the stored response. On a repeat: if a result exists, replay the original response byte-for-byte; if the request is still in flight, return 409/425 rather than double-processing. Scope keys to the operation and an actor, and expire them with a TTL (e.g. 24h). Reject a reused key whose request body differs from the original (422) so a key can never silently apply to a different payload. This turns at-least-once delivery and nervous client retries into exactly-once effects.

## Use cases

- Safe retries for POST/payments
- Client-supplied Idempotency-Key handling
- Storing and replaying first responses

## Provenance (current version)

Version `1.0.0` was **seeded from community best practice** as one of the *top-15*
popular real-world engineering skills, then admitted to the enterprise registry under
capsule **CAP-P003** (category `backend`). Future versions follow the normal RL loop —
distilled from real Claude Code sessions via local Ollama, durable memory in Backboard.

> **Seed finding:** Make unsafe POST/payment operations safe to retry by deduplicating on a client-supplied idempotency key.

Seed transfer score: **67/100** · novelty **83** · importance **94**.
Briefing persisted in **Backboard** (thread `a0b65e17-242c-a368-b1a1-294906668fc8`).

## Token savings

Each reuse of this skill saves **1660 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull idempotency-keys@1.0.0     # pin this exact version
capsule pull idempotency-keys                          # latest published
```
