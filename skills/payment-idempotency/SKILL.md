---
name: Payment Idempotency
id: skill/payment-idempotency
currentVersion: 2.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
tokensSavedPerUse: 900
useCases: [ "Safe retry of real-time payments", "Refund-endpoint idempotency", "Double-submit protection at the API boundary" ]
---

# Payment Idempotency  `skill/payment-idempotency@2.0.0`

Transaction-scoped idempotency keys with durable persistence and scheme-aligned TTLs for safe payment retries.

## Use cases

- Safe retry of real-time payments
- Refund-endpoint idempotency
- Double-submit protection at the API boundary

## Capsule provenance (current version)

The current version `2.0.0` was promoted by the RL gate from capsule **CAP-1006**
(session `sess-3a55`, model `claude-sonnet-4-6`).

> **Finding:** Hashing the whole request body for dedup conflates payment intent with transport noise and blocks legitimate repeat payments.

## Token savings

Each reuse of this skill saves **900 tokens** versus re-deriving the pattern
from a cold session (measured in the A/B harness).

## Pull this skill

```bash
capsule pull payment-idempotency@2.0.0        # pin this exact version
capsule pull payment-idempotency             # latest published
```
