---
name: DB Migration Safety
id: skill/db-migration-safety
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
tokensSavedPerUse: 1740
usedByAgents: [ "agent/factory-implementer" ]
useCases: [ "Zero-downtime schema migrations", "Expand/backfill/contract rollout", "Avoiding read-after-drop errors" ]
---

# DB Migration Safety  `skill/db-migration-safety@1.0.0`

Run schema migrations as expand→backfill→contract: never drop or rename a column in the same deploy that stops writing it, or in-flight code will read a column that no longer exists.

## Use cases

- Zero-downtime schema migrations
- Expand/backfill/contract rollout
- Avoiding read-after-drop errors

## Capsule provenance (current version)

The current version `1.0.0` was distilled from a **real Claude Code coding session**
and promoted by the RL gate from capsule **CAP-V002**
(session `a1f29c4d`, project `Beacon`, model `claude-opus-4-8`,
distilled locally via Ollama `qwen2.5-coder:14b`).

> **Finding:** Run schema migrations as expand→backfill→contract: never drop or rename a column in the same deploy that stops writing it, or in-flight code will read a column that no longer exists.

Capsule transfer score: **63/100** · novelty **88** · importance **91**.
The distilled briefing is persisted in **Backboard** (thread `4c2b9e71-8a3f-4d6e-bb15-2f9c7d0a8e34`).

## Token savings

Each reuse of this skill saves **1740 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull db-migration-safety@1.0.0        # pin this exact version
capsule pull db-migration-safety                              # latest published
```
