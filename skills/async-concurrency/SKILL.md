---
name: Async Concurrency
id: skill/async-concurrency
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
category: data/quality
popularity: "top-15"
description: Run I/O concurrently with bounded parallelism, cancellation, and backpressure — without blocking the event loop.
tokensSavedPerUse: 2163
useCases: [ "Bounded concurrency / worker pools", "Cancellation and timeouts", "Avoiding event-loop blocking & races" ]
---

# Async Concurrency  `skill/async-concurrency@1.0.0`

Run I/O concurrently with bounded parallelism, cancellation, and backpressure — without blocking the event loop.

## Canonical guidance

Use async I/O to overlap waiting, but bound the concurrency — an unbounded fan-out exhausts file descriptors, connections, and memory. Gate parallel work behind a semaphore or worker pool sized to the downstream's capacity, and apply backpressure rather than buffering without limit. Always attach timeouts and propagate cancellation (AbortSignal / context / structured concurrency) so a slow dependency can't pin resources forever. Never block the event loop with CPU-bound or sync work — offload it to a thread/worker. Make shared-state mutations atomic to avoid races, and prefer awaiting a gathered set of tasks over fire-and-forget so errors surface.

## Use cases

- Bounded concurrency / worker pools
- Cancellation and timeouts
- Avoiding event-loop blocking & races

## Provenance (current version)

Version `1.0.0` was **seeded from community best practice** as one of the *top-15*
popular real-world engineering skills, then admitted to the enterprise registry under
capsule **CAP-P014** (category `data/quality`). Future versions follow the normal RL loop —
distilled from real Claude Code sessions via local Ollama, durable memory in Backboard.

> **Seed finding:** Run I/O concurrently with bounded parallelism, cancellation, and backpressure — without blocking the event loop.

Seed transfer score: **57/100** · novelty **82** · importance **78**.
Briefing persisted in **Backboard** (thread `5b42dcd1-a3eb-a212-a735-a716c96fac74`).

## Token savings

Each reuse of this skill saves **2163 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull async-concurrency@1.0.0     # pin this exact version
capsule pull async-concurrency                          # latest published
```
