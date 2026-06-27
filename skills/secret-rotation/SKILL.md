---
name: Secret Rotation
id: skill/secret-rotation
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
tokensSavedPerUse: 1404
usedByAgents: [ "agent/quality-reviewer" ]
useCases: [ "Zero-downtime secret/key rotation", "Dual-validity overlap windows", "Avoiding 401s during rotation" ]
---

# Secret Rotation  `skill/secret-rotation@1.0.0`

Rotate secrets with overlapping dual-validity windows — provision and activate the new secret before revoking the old one — so in-flight requests don't fail with 401 mid-rotation.

## Use cases

- Zero-downtime secret/key rotation
- Dual-validity overlap windows
- Avoiding 401s during rotation

## Capsule provenance (current version)

The current version `1.0.0` was distilled from a **real Claude Code coding session**
and promoted by the RL gate from capsule **CAP-V005**
(session `3b9c2e08`, project `Beacon`, model `claude-opus-4-8`,
distilled locally via Ollama `qwen2.5-coder:14b`).

> **Finding:** Rotate secrets with overlapping dual-validity windows — provision and activate the new secret before revoking the old one — so in-flight requests don't fail with 401 mid-rotation.

Capsule transfer score: **61/100** · novelty **84** · importance **89**.
The distilled briefing is persisted in **Backboard** (thread `9a7e3d51-6b04-4c28-bf73-1e8d2a09c64f`).

## Token savings

Each reuse of this skill saves **1404 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull secret-rotation@1.0.0        # pin this exact version
capsule pull secret-rotation                              # latest published
```
