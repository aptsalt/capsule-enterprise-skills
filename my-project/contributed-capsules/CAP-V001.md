---
id: CAP-V001
author: ven <ven@localhost>
session: a91f7c20
project: Ops Automation
model: claude-opus-4-8
createdAt: 2026-06-27T09:00:00.000Z
novelty: 31
importance: 62
transferScore: 44
semanticSignature: "sig:cmd-verify::inspect-actual-state-over-inference"
targetSkill: skill/command-verification
storedIn: Backboard
threadId: a91f7c20-1d44-4e2e-9f6b-0b2f5c7a1e90
---

# CAP-V001 — "Stop guessing, read the actual state"

## Intent
A scheduled local job kept reporting `idle` while clearly still running. I was
about to act on the *reported* status.

## Mental model
Don't trust inferred/cached status for a long-running local process — go read
the **actual** system state (process table, lock file, log tail) before
deciding anything.

## Finding
> When working with local commands, stop relying on inferred or reported status
> and verify by **directly inspecting the actual system state** (process list,
> lock files, live logs) before acting.

## Why this matters
Acting on inferred state caused a double-trigger of the job. Inspecting the real
state first would have prevented it outright.

## Routing (proposed)
- **Target:** `skill/command-verification`
- **Proposes:** (none — see resolution)
- **Semantic signature:** `sig:cmd-verify::inspect-actual-state-over-inference`

> NOTE: On submission the pipeline matched this signature against the canonical
> finding behind `command-verification@1.0.0` (CAP-R007). Outcome: **DEDUP**, not
> a new version. See `RESOLUTION.md`.
