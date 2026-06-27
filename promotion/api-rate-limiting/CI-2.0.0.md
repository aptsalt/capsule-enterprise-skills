# Agentic CI report — api-rate-limiting@2.0.0 (proposed)

**Pipeline:** A/B harness (new vs current) + prior-capsule regression check
**Model:** qwen2.5-coder:14b (Ollama, local) — measured token proxy
**Candidate:** `2.0.0` (CAP-S001, saim) supersedes `1.0.0` (CAP-R003)
**Run:** 2026-06-27T10:04:00.000Z
**Verdict:** **PASS (reward improved) → eligible to publish, pending human review**

## A/B — new (fail-fast + Retry-After) vs current (backoff + retry)

| Metric | current 1.0.0 | proposed 2.0.0 | Δ | better? |
|---|---|---|---|---|
| Pass rate (10 representative gateway tasks) | 6/10 | 9/10 | +30pp | ✅ |
| Tokens / task (prompt_eval + eval) | 404 | 263 | −141 (−35%) | ✅ |
| Transfer lift (handoff score) | +7 | +31 | +24 | ✅ |
| Upstream 429 amplification | retry storms | none | resolved | ✅ |
| p99 added latency under load | high | low | down | ✅ |

## Regression check (prior capsules touching this skill)

| Capsule | Re-played | Result |
|---|---|---|
| CAP-R003 (orig 1.0.0 finding) | yes | no regression — old "be aware of limits" intent still satisfied by gateway accounting |

## Gate decision

- Reward improves on **every** axis → merge rule satisfied (publish-eligible).
- Relation = **do/undo contradiction** → policy requires **human review** before
  the bump lands on `master` head.
- **Recommendation:** approve supersede to `2.0.0` after a reviewer confirms no
  consumer depends on the old client auto-retry contract.

> Until a reviewer merges, `master` head stays at `api-rate-limiting@1.0.0`; this
> candidate remains `proposed` on `promotion/api-rate-limiting`.
