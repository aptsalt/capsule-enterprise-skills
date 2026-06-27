---
name: API Security
id: skill/api-security
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
tokensSavedPerUse: 1896
usedByAgents: [ "agent/quality-reviewer" ]
useCases: [ "Valid auth-credential handling", "Avoiding repeated 401 errors", "API authentication hygiene" ]
---

# API Security  `skill/api-security@1.0.0`

Always ensure valid authentication credentials are used when interacting with APIs to avoid repeated errors.

## Use cases

- Valid auth-credential handling
- Avoiding repeated 401 errors
- API authentication hygiene

## Capsule provenance (current version)

The current version `1.0.0` was distilled from a **real Claude Code coding session**
and promoted by the RL gate from capsule **CAP-R006**
(session `b505be13`, project `ComfyUI`, model `claude-opus-4-8`,
distilled locally via Ollama `qwen2.5-coder:14b`).

> **Finding:** Always ensure valid authentication credentials are used when interacting with APIs to avoid repeated errors.

Capsule transfer score: **54/100** · novelty **81** · importance **70**.
The distilled briefing is persisted in **Backboard** (thread `9635bac3-b10c-4992-9f23-d02302d7a15a`).

## Token savings

Each reuse of this skill saves **1896 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull api-security@1.0.0        # pin this exact version
capsule pull api-security                              # latest published
```
