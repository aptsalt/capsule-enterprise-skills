---
name: Docker Build Caching
id: skill/docker-build-caching
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
tokensSavedPerUse: 612
usedByAgents: [ "agent/factory-implementer" ]
useCases: [ "Fast incremental Docker builds", "Layer ordering for cache hits", "Separating deps from source copy" ]
---

# Docker Build Caching  `skill/docker-build-caching@1.0.0`

Order Dockerfile layers from least to most volatile and copy dependency manifests (lockfiles) before source, so a code change doesn't bust the dependency-install cache layer.

## Use cases

- Fast incremental Docker builds
- Layer ordering for cache hits
- Separating deps from source copy

## Capsule provenance (current version)

The current version `1.0.0` was distilled from a **real Claude Code coding session**
and promoted by the RL gate from capsule **CAP-V003**
(session `7d3e0b92`, project `Foundry`, model `claude-opus-4-8`,
distilled locally via Ollama `qwen2.5-coder:14b`).

> **Finding:** Order Dockerfile layers from least to most volatile and copy dependency manifests before source, so a code change doesn't bust the dependency-install cache layer.

Capsule transfer score: **49/100** · novelty **66** · importance **72**.
The distilled briefing is persisted in **Backboard** (thread `b8e14a07-5c2d-4f91-9a3e-6d0b7c81f25a`).

## Token savings

Each reuse of this skill saves **612 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull docker-build-caching@1.0.0        # pin this exact version
capsule pull docker-build-caching                              # latest published
```
