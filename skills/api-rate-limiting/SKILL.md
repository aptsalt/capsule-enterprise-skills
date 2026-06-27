---
name: API Rate Limiting
id: skill/api-rate-limiting
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
tokensSavedPerUse: 157
usedByAgents: [ "agent/factory-implementer" ]
useCases: [ "Handling third-party 429s", "Backoff on server-side throttling", "Resilient MCP/API integration" ]
---

# API Rate Limiting  `skill/api-rate-limiting@1.0.0`

When integrating third-party APIs, be prepared for unexpected rate limits that may not be directly related to your usage.

## Use cases

- Handling third-party 429s
- Backoff on server-side throttling
- Resilient MCP/API integration

## Capsule provenance (current version)

The current version `1.0.0` was distilled from a **real Claude Code coding session**
and promoted by the RL gate from capsule **CAP-R003**
(session `12560ca4`, project `Workspace`, model `claude-opus-4-8`,
distilled locally via Ollama `qwen2.5-coder:14b`).

> **Finding:** When integrating third-party APIs, be prepared for unexpected rate limits that may not be directly related to your usage.

Capsule transfer score: **37/100** · novelty **71** · importance **64**.
The distilled briefing is persisted in **Backboard** (thread `fd2a6898-9581-424f-88eb-87be27633f3a`).

## Token savings

Each reuse of this skill saves **157 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull api-rate-limiting@1.0.0        # pin this exact version
capsule pull api-rate-limiting                              # latest published
```
