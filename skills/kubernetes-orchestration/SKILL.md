---
name: Kubernetes Orchestration
id: skill/kubernetes-orchestration
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
category: infra/devops
popularity: "top-15"
description: Run workloads on Kubernetes with correct resource requests/limits, probes, and rollout strategy for self-healing deploys.
tokensSavedPerUse: 1741
useCases: [ "Deployment manifests and rollouts", "Resource requests/limits + probes", "Config/secret and scaling strategy" ]
---

# Kubernetes Orchestration  `skill/kubernetes-orchestration@1.0.0`

Run workloads on Kubernetes with correct resource requests/limits, probes, and rollout strategy for self-healing deploys.

## Canonical guidance

Declare every workload as a Deployment (stateless) or StatefulSet (stateful) with explicit resource `requests` and `limits` — requests drive scheduling and the autoscaler, limits prevent noisy-neighbor blast radius. Always define `readinessProbe` (gate traffic) and `livenessProbe` (restart on hang) plus a `startupProbe` for slow boots. Use RollingUpdate with `maxUnavailable`/`maxSurge` and a PodDisruptionBudget so deploys and node drains stay zero-downtime. Externalize config to ConfigMaps/Secrets (never image-baked), set least-privilege ServiceAccounts, and front Pods with a Service. Scale with HPA on real signals (CPU/RPS/custom metrics), not guesswork.

## Use cases

- Deployment manifests and rollouts
- Resource requests/limits + probes
- Config/secret and scaling strategy

## Provenance (current version)

Version `1.0.0` was **seeded from community best practice** as one of the *top-15*
popular real-world engineering skills, then admitted to the enterprise registry under
capsule **CAP-P007** (category `infra/devops`). Future versions follow the normal RL loop —
distilled from real Claude Code sessions via local Ollama, durable memory in Backboard.

> **Seed finding:** Run workloads on Kubernetes with correct resource requests/limits, probes, and rollout strategy for self-healing deploys.

Seed transfer score: **64/100** · novelty **73** · importance **67**.
Briefing persisted in **Backboard** (thread `0b690df6-c315-df93-0eb4-dcf6ed31f0f8`).

## Token savings

Each reuse of this skill saves **1741 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull kubernetes-orchestration@1.0.0     # pin this exact version
capsule pull kubernetes-orchestration                          # latest published
```
