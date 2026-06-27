---
name: Automation Maintenance
id: skill/automation-maintenance
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
tokensSavedPerUse: 1296
usedByAgents: [ "agent/factory-implementer" ]
useCases: [ "Killing stale Stop-hooks", "Reviewing scheduled automation conditions", "Preventing runaway scheduled jobs" ]
---

# Automation Maintenance  `skill/automation-maintenance@1.0.0`

Automated hooks can become stale and require manual intervention to resolve, highlighting the need for engineers to regularly review and update automation scrip

## Use cases

- Killing stale Stop-hooks
- Reviewing scheduled automation conditions
- Preventing runaway scheduled jobs

## Capsule provenance (current version)

The current version `1.0.0` was distilled from a **real Claude Code coding session**
and promoted by the RL gate from capsule **CAP-R002**
(session `003a671f`, project `Workspace`, model `claude-opus-4-8`,
distilled locally via Ollama `qwen2.5-coder:14b`).

> **Finding:** Automated hooks can become stale and require manual intervention to resolve, highlighting the need for engineers to regularly review and update automation scripts to prevent such issues.

Capsule transfer score: **29/100** · novelty **71** · importance **74**.
The distilled briefing is persisted in **Backboard** (thread `fd2a6898-9581-424f-88eb-87be27633f3a`).

## Token savings

Each reuse of this skill saves **1296 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull automation-maintenance@1.0.0        # pin this exact version
capsule pull automation-maintenance                              # latest published
```
