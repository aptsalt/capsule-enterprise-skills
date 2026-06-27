# Agentic CI report — creative-franchise-expansion@2.0.0 (proposed)

**Pipeline:** A/B harness (new capsule guidance vs current published guidance)
**Model:** qwen2.5-coder:14b (Ollama, local) — measured token proxy (prompt_eval + eval)
**Candidate:** `2.0.0` from capsule `CAP-R001` (agent/factory-implementer)
**Run:** 2026-06-27T17:10:05.105Z
**Ollama available:** yes (real measurement)
**Verdict:** **HELD (reward flat/worse)**

## A/B — new (capsule finding injected) vs current (published guidance)

| Metric | current 1.0.0 | proposed 2.0.0 | Δ | better? |
|---|---|---|---|---|
| Tokens / task (prompt_eval + eval) | 392 | 478 | +86 | — |

**Representative task:** Write a short TypeScript function and explain the key correctness consideration for this task: "Creative Franchise Expansion" in a Content Engine codebase. Keep it under 20 lines.

**Current guidance:** When expanding a creative franchise, it's crucial to maintain consistent continuity across all parts to avoid contradictions and ensure a cohesive narrative.

**New guidance (capsule CAP-R001):** When expanding a creative franchise, it's crucial to maintain consistent continuity across all parts to avoid contradictions and ensure a cohesive narrative.

## Gate decision

New guidance did not reduce tokens (392→478, Δ+86) on this single-shot task; stays proposed pending broader CI.

> Per PROMOTION.md the version bump publishes onto `master` head **only if**
> measured reward improves **and** no regressions. Until then this candidate
> stays `proposed` on `promotion/creative-franchise-expansion`.
