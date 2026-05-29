---
name: SCA Challenge
id: skill/sca-challenge
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: manual
optedIn: true
tokensSavedPerUse: 3200
useCases: [ "Risk-driven step-up", "Single-use challenge tokens", "Audited SCA exemptions" ]
---

# SCA Challenge  `skill/sca-challenge@1.0.0`

Server-side Strong Customer Authentication: risk-driven step-up, single-use challenge tokens, and audited exemptions.

## Use cases

- Risk-driven step-up
- Single-use challenge tokens
- Audited SCA exemptions

## Capsule provenance (current version)

The current version `1.0.0` was promoted by the RL gate from capsule **CAP-1005**
(session `sess-1e08`, model `claude-opus-4-8`).

> **Finding:** Compute SCA step-up server-side from a risk score and treat the challenge token as a single-use capability bound to one payment intent.

## Token savings

Each reuse of this skill saves **3200 tokens** versus re-deriving the pattern
from a cold session (measured in the A/B harness).

## Pull this skill

```bash
capsule pull sca-challenge@1.0.0        # pin this exact version
capsule pull sca-challenge             # latest published
```
