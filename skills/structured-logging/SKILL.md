---
name: Structured Logging
id: skill/structured-logging
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
category: infra/devops
popularity: "top-15"
description: Emit machine-parseable JSON logs with consistent fields, levels, and a correlation id — never bare strings.
tokensSavedPerUse: 825
useCases: [ "JSON log schema and levels", "Correlation/trace id propagation", "Redacting secrets/PII in logs" ]
---

# Structured Logging  `skill/structured-logging@1.0.0`

Emit machine-parseable JSON logs with consistent fields, levels, and a correlation id — never bare strings.

## Canonical guidance

Log structured JSON, not interpolated strings: one event per line with stable fields (`timestamp`, `level`, `message`, `service`, `traceId`, plus event-specific keys). Use levels deliberately — ERROR for actionable failures, WARN for recoverable anomalies, INFO for state transitions, DEBUG off in prod. Propagate a correlation/trace id from the inbound request through every downstream call so one user action is greppable end-to-end. Never log secrets, tokens, or PII — redact at the logger boundary. Write to stdout and let the platform ship/aggregate; the app should not own log rotation or destinations.

## Use cases

- JSON log schema and levels
- Correlation/trace id propagation
- Redacting secrets/PII in logs

## Provenance (current version)

Version `1.0.0` was **seeded from community best practice** as one of the *top-15*
popular real-world engineering skills, then admitted to the enterprise registry under
capsule **CAP-P009** (category `infra/devops`). Future versions follow the normal RL loop —
distilled from real Claude Code sessions via local Ollama, durable memory in Backboard.

> **Seed finding:** Emit machine-parseable JSON logs with consistent fields, levels, and a correlation id — never bare strings.

Seed transfer score: **50/100** · novelty **86** · importance **67**.
Briefing persisted in **Backboard** (thread `2cf429c4-3151-604d-50d3-c76c043f4080`).

## Token savings

Each reuse of this skill saves **825 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull structured-logging@1.0.0     # pin this exact version
capsule pull structured-logging                          # latest published
```
