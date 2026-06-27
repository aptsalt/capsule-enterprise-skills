---
name: Command Verification
id: skill/command-verification
currentVersion: 2.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
tokensSavedPerUse: 1920
usedByAgents: [ "agent/quality-reviewer" ]
useCases: [ "Verifying local command state", "Checking official docs before acting", "Inspecting system state vs inference" ]
---

# Command Verification  `skill/command-verification@2.0.0`

When working with local commands, always verify the actual current state by checking official documentation or authoritative sources instead of relying on infer

## Use cases

- Verifying local command state
- Checking official docs before acting
- Inspecting system state vs inference

## Capsule provenance (current version)

The current version `2.0.0` was distilled from a **real Claude Code coding session**
and promoted by the RL gate from capsule **CAP-R005**
(session `52cdf3c2`, project `Beacon`, model `claude-opus-4-8`,
distilled locally via Ollama `qwen2.5-coder:14b`).

> **Finding:** When working with local commands, always verify the actual current state by checking official documentation or authoritative sources instead of relying on inferred information.

Capsule transfer score: **55/100** · novelty **87** · importance **86**.
The distilled briefing is persisted in **Backboard** (thread `79169d2d-c0a9-4901-93a8-15acccdca031`).

## Token savings

Each reuse of this skill saves **1920 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull command-verification@2.0.0        # pin this exact version
capsule pull command-verification                              # latest published
```
