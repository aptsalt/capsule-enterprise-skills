---
name: Docker Containerization
id: skill/docker-containerization
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
category: infra/devops
popularity: "top-15"
description: Build small, secure, reproducible container images with multi-stage builds, pinned bases, and non-root runtime.
tokensSavedPerUse: 1244
useCases: [ "Multi-stage build optimization", "Minimal non-root runtime images", "Layer caching and .dockerignore hygiene" ]
---

# Docker Containerization  `skill/docker-containerization@1.0.0`

Build small, secure, reproducible container images with multi-stage builds, pinned bases, and non-root runtime.

## Canonical guidance

Use multi-stage builds: compile/install in a fat builder stage, then COPY only the artifact into a minimal runtime (distroless or `-slim`). Pin base images by digest, run as a non-root USER, and never bake secrets into layers — they persist in history. Order Dockerfile steps from least- to most-frequently-changing and copy dependency manifests before source so layer caching survives code edits. Add a tight `.dockerignore` to keep build context small. Declare an explicit `EXPOSE`, a `HEALTHCHECK`, and a non-shell exec-form `ENTRYPOINT` so signals propagate and the orchestrator can reap the container cleanly.

## Use cases

- Multi-stage build optimization
- Minimal non-root runtime images
- Layer caching and .dockerignore hygiene

## Provenance (current version)

Version `1.0.0` was **seeded from community best practice** as one of the *top-15*
popular real-world engineering skills, then admitted to the enterprise registry under
capsule **CAP-P006** (category `infra/devops`). Future versions follow the normal RL loop —
distilled from real Claude Code sessions via local Ollama, durable memory in Backboard.

> **Seed finding:** Build small, secure, reproducible container images with multi-stage builds, pinned bases, and non-root runtime.

Seed transfer score: **86/100** · novelty **91** · importance **93**.
Briefing persisted in **Backboard** (thread `c30bbe3c-4e4c-f1d0-7418-6d918ad4ba7d`).

## Token savings

Each reuse of this skill saves **1244 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull docker-containerization@1.0.0     # pin this exact version
capsule pull docker-containerization                          # latest published
```
