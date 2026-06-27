---
name: Database Indexing
id: skill/database-indexing
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
category: data/quality
popularity: "top-15"
description: Design indexes that match query predicates and sort order, covering hot paths while controlling write cost.
tokensSavedPerUse: 2044
useCases: [ "Composite index column ordering", "Covering indexes and selectivity", "Reading EXPLAIN plans" ]
---

# Database Indexing  `skill/database-indexing@1.0.0`

Design indexes that match query predicates and sort order, covering hot paths while controlling write cost.

## Canonical guidance

Index to serve your actual queries: build composite indexes with the most selective equality columns first, then the range/sort column last, matching the WHERE + ORDER BY shape so the planner does an index range scan, not a full scan or filesort. Add covering indexes (INCLUDE the selected columns) to satisfy hot read paths from the index alone. Remember every index taxes writes and storage — drop unused/duplicate indexes. Keep predicates sargable (no functions wrapping the indexed column). Always confirm with EXPLAIN/ANALYZE on production-like data and watch for the gap between estimated and actual rows, which signals stale statistics.

## Use cases

- Composite index column ordering
- Covering indexes and selectivity
- Reading EXPLAIN plans

## Provenance (current version)

Version `1.0.0` was **seeded from community best practice** as one of the *top-15*
popular real-world engineering skills, then admitted to the enterprise registry under
capsule **CAP-P011** (category `data/quality`). Future versions follow the normal RL loop —
distilled from real Claude Code sessions via local Ollama, durable memory in Backboard.

> **Seed finding:** Design indexes that match query predicates and sort order, covering hot paths while controlling write cost.

Seed transfer score: **67/100** · novelty **70** · importance **77**.
Briefing persisted in **Backboard** (thread `46726a7e-77b4-dc7a-39ac-574760317400`).

## Token savings

Each reuse of this skill saves **2044 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull database-indexing@1.0.0     # pin this exact version
capsule pull database-indexing                          # latest published
```
