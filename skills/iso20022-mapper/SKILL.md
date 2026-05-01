---
name: ISO 20022 Mapper
id: skill/iso20022-mapper
currentVersion: 1.2.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
tokensSavedPerUse: 2100
useCases: [ "pacs.008 outbound mapping", "camt inbound parsing", "Currency-correct decimal scaling" ]
---

# ISO 20022 Mapper  `skill/iso20022-mapper@1.2.0`

Bidirectional mapping between internal payment models and ISO 20022 pacs/camt messages with currency-correct decimal scaling.

## Use cases

- pacs.008 outbound mapping
- camt inbound parsing
- Currency-correct decimal scaling

## Capsule provenance (current version)

The current version `1.2.0` was promoted by the RL gate from capsule **CAP-1007**
(session `sess-6f29`, model `claude-sonnet-4-6`).

> **Finding:** A locally-pinned ISO 20022 XSD silently drifts out of date, so CI must validate against the network-published schema.

## Token savings

Each reuse of this skill saves **2100 tokens** versus re-deriving the pattern
from a cold session (measured in the A/B harness).

## Pull this skill

```bash
capsule pull iso20022-mapper@1.2.0        # pin this exact version
capsule pull iso20022-mapper             # latest published
```
