---
name: Payment Idempotency
id: skill/payment-idempotency
currentVersion: 2.1.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
tokensSavedPerUse: 1800
useCases: [ "Safe retry of real-time payments", "Refund-endpoint idempotency", "Double-submit protection at the API boundary" ]
---

# Payment Idempotency  `skill/payment-idempotency@2.1.0`

Transaction-scoped idempotency keys with durable persistence and scheme-aligned TTLs for safe payment retries.

## Use cases

- Safe retry of real-time payments
- Refund-endpoint idempotency
- Double-submit protection at the API boundary

## Capsule provenance (current version)

The current version `2.1.0` was promoted by the RL gate from capsule **CAP-1001**
(session `sess-4af2`, model `claude-opus-4-8`).

> **Finding:** Persist the idempotency key inside the same ledger transaction and scope it to (debtor, amount, currency) so retries are safe without ever blocking a legitimate repeat payment.

## Token savings

Each reuse of this skill saves **1800 tokens** versus re-deriving the pattern
from a cold session (measured in the A/B harness).

## Pull this skill

```bash
capsule pull payment-idempotency@2.1.0        # pin this exact version
capsule pull payment-idempotency             # latest published
```
