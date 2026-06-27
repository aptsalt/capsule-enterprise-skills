---
name: Observability & Tracing
id: skill/observability-tracing
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
category: infra/devops
popularity: "top-15"
description: Instrument services with OpenTelemetry traces, metrics, and context propagation to debug distributed latency.
tokensSavedPerUse: 1406
useCases: [ "Distributed trace instrumentation", "RED/USE metrics and SLOs", "Context propagation across services" ]
---

# Observability & Tracing  `skill/observability-tracing@1.0.0`

Instrument services with OpenTelemetry traces, metrics, and context propagation to debug distributed latency.

## Canonical guidance

Treat the three signals together: traces (where time goes), metrics (aggregate health), logs (detail), correlated by a shared trace id. Adopt OpenTelemetry so instrumentation is vendor-neutral. Create spans around I/O and service boundaries, propagate `traceparent` across every hop (HTTP/gRPC/queue), and tag spans with low-cardinality attributes — never PII or unbounded ids. Track RED for services (Rate, Errors, Duration) and USE for resources, and define SLOs/alerts on those rather than on raw CPU. Sample smartly (tail-based on errors/slow traces) to keep fidelity where it matters without paying to store every span.

## Use cases

- Distributed trace instrumentation
- RED/USE metrics and SLOs
- Context propagation across services

## Provenance (current version)

Version `1.0.0` was **seeded from community best practice** as one of the *top-15*
popular real-world engineering skills, then admitted to the enterprise registry under
capsule **CAP-P010** (category `infra/devops`). Future versions follow the normal RL loop —
distilled from real Claude Code sessions via local Ollama, durable memory in Backboard.

> **Seed finding:** Instrument services with OpenTelemetry traces, metrics, and context propagation to debug distributed latency.

Seed transfer score: **84/100** · novelty **84** · importance **89**.
Briefing persisted in **Backboard** (thread `6734f4e5-025e-c7ef-7248-f859735569e7`).

## Token savings

Each reuse of this skill saves **1406 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull observability-tracing@1.0.0     # pin this exact version
capsule pull observability-tracing                          # latest published
```
