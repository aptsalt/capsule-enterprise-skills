---
name: CI/CD Pipelines
id: skill/ci-cd-pipelines
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
category: infra/devops
popularity: "top-15"
description: Automate build, test, and deploy with fast, reproducible pipelines, quality gates, and safe progressive rollout.
tokensSavedPerUse: 1281
useCases: [ "Pipeline stage design", "Quality gates and caching", "Progressive/rollback-safe deploys" ]
---

# CI/CD Pipelines  `skill/ci-cd-pipelines@1.0.0`

Automate build, test, and deploy with fast, reproducible pipelines, quality gates, and safe progressive rollout.

## Canonical guidance

Structure the pipeline as fast-fail stages: lint -> unit -> build -> integration -> deploy, cheapest first so feedback is quick. Make builds reproducible — pin tool and dependency versions and cache dependency layers keyed on the lockfile. Enforce quality gates (tests, coverage, security/dependency scan, SBOM) as required checks before merge, not afterthoughts. Build the artifact once and promote the same immutable artifact through staging to prod; never rebuild per environment. Deploy progressively (blue-green or canary) behind a health check with an automatic rollback trigger, and keep secrets in the platform's secret store, injected at deploy time, never in the repo.

## Use cases

- Pipeline stage design
- Quality gates and caching
- Progressive/rollback-safe deploys

## Provenance (current version)

Version `1.0.0` was **seeded from community best practice** as one of the *top-15*
popular real-world engineering skills, then admitted to the enterprise registry under
capsule **CAP-P008** (category `infra/devops`). Future versions follow the normal RL loop —
distilled from real Claude Code sessions via local Ollama, durable memory in Backboard.

> **Seed finding:** Automate build, test, and deploy with fast, reproducible pipelines, quality gates, and safe progressive rollout.

Seed transfer score: **77/100** · novelty **74** · importance **64**.
Briefing persisted in **Backboard** (thread `89b6fd95-53e9-bdf9-4371-46349a834d94`).

## Token savings

Each reuse of this skill saves **1281 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull ci-cd-pipelines@1.0.0     # pin this exact version
capsule pull ci-cd-pipelines                          # latest published
```
