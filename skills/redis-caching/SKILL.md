---
name: Redis Caching
id: skill/redis-caching
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
category: backend
popularity: "top-15"
description: Add a Redis cache layer correctly: cache-aside reads, sane TTLs, explicit invalidation, and stampede protection.
tokensSavedPerUse: 857
useCases: [ "Cache-aside read/write patterns", "TTL and key-namespacing strategy", "Stampede and stale-data protection" ]
---

# Redis Caching  `skill/redis-caching@1.0.0`

Add a Redis cache layer correctly: cache-aside reads, sane TTLs, explicit invalidation, and stampede protection.

## Canonical guidance

Default to cache-aside: read from Redis, on miss load from the source, then set with a TTL. Namespace keys (`user:{id}:profile`) and version them so a schema change can mass-invalidate. Always set a TTL — an unbounded cache is a memory leak and a correctness bug. Invalidate (delete) on write rather than trying to update the cache in place, and accept eventual consistency for read-heavy data. Protect against stampedes with a short lock or request-coalescing on miss, and add jitter to TTLs so keys don't all expire together. For hot counters use atomic ops (INCR) and never read-modify-write across a round trip.

## Use cases

- Cache-aside read/write patterns
- TTL and key-namespacing strategy
- Stampede and stale-data protection

## Provenance (current version)

Version `1.0.0` was **seeded from community best practice** as one of the *top-15*
popular real-world engineering skills, then admitted to the enterprise registry under
capsule **CAP-P005** (category `backend`). Future versions follow the normal RL loop —
distilled from real Claude Code sessions via local Ollama, durable memory in Backboard.

> **Seed finding:** Add a Redis cache layer correctly: cache-aside reads, sane TTLs, explicit invalidation, and stampede protection.

Seed transfer score: **64/100** · novelty **94** · importance **72**.
Briefing persisted in **Backboard** (thread `a4d9aa58-af39-d198-36a7-e1f1c8be8707`).

## Token savings

Each reuse of this skill saves **857 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull redis-caching@1.0.0     # pin this exact version
capsule pull redis-caching                          # latest published
```
