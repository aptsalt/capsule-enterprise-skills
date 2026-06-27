---
name: Cursor Pagination
id: skill/cursor-pagination
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
category: backend
popularity: "top-15"
description: Paginate large, mutating datasets with stable opaque cursors instead of OFFSET, avoiding drift and deep-page slowdown.
tokensSavedPerUse: 1661
useCases: [ "Stable pagination over mutating data", "Opaque cursor encoding", "Avoiding OFFSET deep-page cost" ]
---

# Cursor Pagination  `skill/cursor-pagination@1.0.0`

Paginate large, mutating datasets with stable opaque cursors instead of OFFSET, avoiding drift and deep-page slowdown.

## Canonical guidance

Prefer keyset/cursor pagination over `LIMIT/OFFSET`: OFFSET rescans skipped rows (slow at depth) and drifts when rows are inserted/deleted mid-scan. Order by a stable, unique tuple (e.g. `(created_at, id)`) and encode the last row's sort values into an opaque, base64 cursor the client echoes back. Query `WHERE (created_at,id) < (:c1,:c2) ORDER BY created_at DESC, id DESC LIMIT n+1`; the extra row tells you if a next page exists. Return `{items, nextCursor}` and treat the cursor as opaque so you can change the underlying key without breaking clients. Index the exact sort tuple so every page is an index range scan.

## Use cases

- Stable pagination over mutating data
- Opaque cursor encoding
- Avoiding OFFSET deep-page cost

## Provenance (current version)

Version `1.0.0` was **seeded from community best practice** as one of the *top-15*
popular real-world engineering skills, then admitted to the enterprise registry under
capsule **CAP-P004** (category `backend`). Future versions follow the normal RL loop —
distilled from real Claude Code sessions via local Ollama, durable memory in Backboard.

> **Seed finding:** Paginate large, mutating datasets with stable opaque cursors instead of OFFSET, avoiding drift and deep-page slowdown.

Seed transfer score: **59/100** · novelty **78** · importance **66**.
Briefing persisted in **Backboard** (thread `c12883ad-3f85-e44c-3139-8f76833c1255`).

## Token savings

Each reuse of this skill saves **1661 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull cursor-pagination@1.0.0     # pin this exact version
capsule pull cursor-pagination                          # latest published
```
