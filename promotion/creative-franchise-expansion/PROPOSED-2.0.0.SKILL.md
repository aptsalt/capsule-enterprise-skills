---
name: Creative Franchise Expansion
id: skill/creative-franchise-expansion
proposedVersion: 2.0.0
supersedes: 1.0.0
bump: major
status: proposed            # staged on promotion/creative-franchise-expansion — NOT on master head
scope: enterprise
adoptionPolicy: auto
optedIn: true
derivedFromCapsule: CAP-R001
ciTokensBefore: 392
ciTokensAfter: 478
ciDelta: 86
ciImproved: false
usedByAgents: [ "agent/factory-implementer" ]
---

# Creative Franchise Expansion  `skill/creative-franchise-expansion@2.0.0`  *(PROPOSED)*

> **THIS IS A STAGED PROPOSAL, NOT A PUBLISHED VERSION.** It lives on the
> `promotion/creative-franchise-expansion` path and lands on `master` head **only if** agentic CI
> passes and review signs off (per PROMOTION.md).

When expanding a creative franchise, it's crucial to maintain consistent continuity across all parts to avoid contradictions and ensure a cohesive narrative.

## What changed vs 1.0.0

- **1.0.0 (current):** When expanding a creative franchise, it's crucial to maintain consistent continuity across all parts to avoid contradictions and ensure a cohesive narrative.
- **2.0.0 (this, major):** Initial creation of skill for managing creative franchise expansion.

## Capsule provenance

Distilled from a **real Claude Code coding session**, capsule **CAP-R001**
(session `2535b3ad`, project `Content Engine`, model
`claude-opus-4-8`, distilled locally via Ollama `qwen2.5-coder:14b`).

> **Finding:** When expanding a creative franchise, it's crucial to maintain consistent continuity across all parts to avoid contradictions and ensure a cohesive narrative.

Capsule transfer score: **40/100** · novelty **75** · importance **78**.
The distilled briefing is persisted in **Backboard** (thread `d877861b-0ec9-4fe8-afe8-69ccbd74d775`).

## Agentic-CI gate

See `CI-2.0.0.md`. Measured proxy on the local model: tokens
392 → 478 (Δ +86).
New guidance did not reduce tokens (392→478, Δ+86) on this single-shot task; stays proposed pending broader CI.

## Promotion state

```
status:    proposed
staged-on: promotion/creative-franchise-expansion
gate:      REVIEW (transfer 40; novelty 75)
ci:        reward flat/worse — held proposed
on-merge:  master head -> skill/creative-franchise-expansion@2.0.0 (published); update registry.json + CHANGELOG.md
```
