---
name: Angular Upgrade
id: skill/angular-upgrade
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
tokensSavedPerUse: 1968
usedByAgents: [ "agent/factory-implementer" ]
useCases: [ "Angular 15->22 version upgrades", "Local bridge / WebSocket configuration", "Escaping template interpolation in demos" ]
---

# Angular Upgrade  `skill/angular-upgrade@1.0.0`

When upgrading Angular versions, ensure that local bridges and WebSocket servers are correctly configured to avoid connection issues.

## Use cases

- Angular 15->22 version upgrades
- Local bridge / WebSocket configuration
- Escaping template interpolation in demos

## Capsule provenance (current version)

The current version `1.0.0` was distilled from a **real Claude Code coding session**
and promoted by the RL gate from capsule **CAP-R004**
(session `85941354`, project `Workspace`, model `claude-opus-4-8`,
distilled locally via Ollama `qwen2.5-coder:14b`).

> **Finding:** When upgrading Angular versions, ensure that local bridges and WebSocket servers are correctly configured to avoid connection issues.

Capsule transfer score: **57/100** · novelty **97** · importance **94**.
The distilled briefing is persisted in **Backboard** (thread `fd2a6898-9581-424f-88eb-87be27633f3a`).

## Token savings

Each reuse of this skill saves **1968 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull angular-upgrade@1.0.0        # pin this exact version
capsule pull angular-upgrade                              # latest published
```
