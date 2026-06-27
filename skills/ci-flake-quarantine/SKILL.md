---
name: CI Flake Quarantine
id: skill/ci-flake-quarantine
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
tokensSavedPerUse: 980
usedByAgents: [ "agent/quality-reviewer" ]
useCases: [ "Detecting and isolating flaky tests", "Avoiding blanket CI retries", "Keeping signal in the test suite" ]
---

# CI Flake Quarantine  `skill/ci-flake-quarantine@1.0.0`

When a test fails non-deterministically, quarantine it after N flaky runs instead of blanket-retrying the suite — blanket retries mask real regressions and inflate CI time.

## Use cases

- Detecting and isolating flaky tests
- Avoiding blanket CI retries
- Keeping signal in the test suite

## Capsule provenance (current version)

The current version `1.0.0` was distilled from a **real Claude Code coding session**
and promoted by the RL gate from capsule **CAP-V004**
(session `f0a6b13c`, project `Content Engine`, model `claude-opus-4-8`,
distilled locally via Ollama `qwen2.5-coder:14b`).

> **Finding:** When a test fails non-deterministically, quarantine it after N flaky runs instead of blanket-retrying the suite — blanket retries mask real regressions and inflate CI time.

Capsule transfer score: **58/100** · novelty **79** · importance **83**.
The distilled briefing is persisted in **Backboard** (thread `e21d7f4b-3c08-49a6-8f12-9b5e0d6a47c1`).

## Token savings

Each reuse of this skill saves **980 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull ci-flake-quarantine@1.0.0        # pin this exact version
capsule pull ci-flake-quarantine                              # latest published
```
