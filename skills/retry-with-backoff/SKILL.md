---
name: Retry with Backoff
id: skill/retry-with-backoff
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
category: data/quality
popularity: "top-15"
description: Retry transient failures with exponential backoff, jitter, caps, and circuit breaking — only for idempotent calls.
tokensSavedPerUse: 1196
useCases: [ "Exponential backoff + jitter", "Retrying only idempotent ops", "Circuit breakers and retry budgets" ]
---

# Retry with Backoff  `skill/retry-with-backoff@1.0.0`

Retry transient failures with exponential backoff, jitter, caps, and circuit breaking — only for idempotent calls.

## Canonical guidance

Retry only transient, idempotent failures (timeouts, 429, 503, connection resets) — never retry a 4xx that will fail again, and never blindly retry a non-idempotent write (pair it with an idempotency key first). Use exponential backoff with full jitter (`sleep = random(0, base * 2^attempt)`) to avoid synchronized thundering-herd retries. Cap both the per-attempt delay and the total attempts/deadline. Honor `Retry-After` when the server sends it. Wrap the dependency in a circuit breaker that trips on sustained failure and sheds load while it recovers, and enforce a retry budget so retries can't amplify an outage into a self-inflicted DDoS.

## Use cases

- Exponential backoff + jitter
- Retrying only idempotent ops
- Circuit breakers and retry budgets

## Provenance (current version)

Version `1.0.0` was **seeded from community best practice** as one of the *top-15*
popular real-world engineering skills, then admitted to the enterprise registry under
capsule **CAP-P013** (category `data/quality`). Future versions follow the normal RL loop —
distilled from real Claude Code sessions via local Ollama, durable memory in Backboard.

> **Seed finding:** Retry transient failures with exponential backoff, jitter, caps, and circuit breaking — only for idempotent calls.

Seed transfer score: **89/100** · novelty **75** · importance **78**.
Briefing persisted in **Backboard** (thread `7a6bf66b-c0f4-e17b-9fa1-7566c7226146`).

## Token savings

Each reuse of this skill saves **1196 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull retry-with-backoff@1.0.0     # pin this exact version
capsule pull retry-with-backoff                          # latest published
```
