---
name: ISO 20022 Mapper
id: skill/iso20022-mapper
currentVersion: 1.3.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
tokensSavedPerUse: 2400
useCases: [ "pacs.008 outbound mapping", "camt inbound parsing", "Currency-correct decimal scaling" ]
---

# ISO 20022 Mapper  `skill/iso20022-mapper@1.3.0`

Bidirectional mapping between internal payment models and ISO 20022 pacs/camt messages with currency-correct decimal scaling.

## Use cases

- pacs.008 outbound mapping
- camt inbound parsing
- Currency-correct decimal scaling

## Capsule provenance (current version)

The current version `1.3.0` was promoted by the RL gate from capsule **CAP-1002**
(session `sess-9c10`, model `claude-sonnet-4-6`).

> **Finding:** Currency fraction digits are a per-currency ISO 4217 property, so amount scaling must come from an exponent table rather than a hardcoded /100.

## Token savings

Each reuse of this skill saves **2400 tokens** versus re-deriving the pattern
from a cold session (measured in the A/B harness).

## Pull this skill

```bash
capsule pull iso20022-mapper@1.3.0        # pin this exact version
capsule pull iso20022-mapper             # latest published
```
