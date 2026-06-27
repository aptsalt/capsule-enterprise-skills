---
name: WebSocket Reconnection
id: skill/websocket-reconnection
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
tokensSavedPerUse: 828
usedByAgents: [ "agent/factory-implementer" ]
useCases: [ "Resilient WebSocket reconnection", "Jittered exponential backoff", "Resumable session tokens after drop" ]
---

# WebSocket Reconnection  `skill/websocket-reconnection@1.0.0`

On a dropped WebSocket, reconnect with jittered exponential backoff and a resumable session token — never tight-loop reconnect, which stampedes the server on mass disconnects.

## Use cases

- Resilient WebSocket reconnection
- Jittered exponential backoff
- Resumable session tokens after drop

## Capsule provenance (current version)

The current version `1.0.0` was distilled from a **real Claude Code coding session**
and promoted by the RL gate from capsule **CAP-V006**
(session `c5d81a37`, project `Beacon`, model `claude-opus-4-8`,
distilled locally via Ollama `qwen2.5-coder:14b`).

> **Finding:** On a dropped WebSocket, reconnect with jittered exponential backoff and a resumable session token — never tight-loop reconnect, which stampedes the server on mass disconnects.

Capsule transfer score: **55/100** · novelty **74** · importance **77**.
The distilled briefing is persisted in **Backboard** (thread `2f6b9c40-7d18-4e53-a0c9-3b5e8d17a946`).

## Token savings

Each reuse of this skill saves **828 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull websocket-reconnection@1.0.0        # pin this exact version
capsule pull websocket-reconnection                              # latest published
```
