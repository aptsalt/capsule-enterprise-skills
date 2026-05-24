---
name: Reconciliation Ledger
id: skill/reconciliation-ledger
currentVersion: 1.1.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
tokensSavedPerUse: 1100
useCases: [ "camt.053 reconciliation", "Partial-settlement matching", "Composite-key ledger sync" ]
---

# Reconciliation Ledger  `skill/reconciliation-ledger@1.1.0`

camt.053 reconciliation with composite key matching and partial-settlement handling.

## Use cases

- camt.053 reconciliation
- Partial-settlement matching
- Composite-key ledger sync

## Capsule provenance (current version)

The current version `1.1.0` was promoted by the RL gate from capsule **CAP-1004**
(session `sess-7d31`, model `claude-sonnet-4-6`).

> **Finding:** Reconcile camt.053 on a composite (EndToEndId, amount) key with a value-date fallback, because the network re-issues references on partial settlement.

## Token savings

Each reuse of this skill saves **1100 tokens** versus re-deriving the pattern
from a cold session (measured in the A/B harness).

## Pull this skill

```bash
capsule pull reconciliation-ledger@1.1.0        # pin this exact version
capsule pull reconciliation-ledger             # latest published
```
