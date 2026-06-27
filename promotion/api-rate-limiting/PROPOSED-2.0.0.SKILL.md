---
name: API Rate Limiting
id: skill/api-rate-limiting
proposedVersion: 2.0.0
supersedes: 1.0.0
bump: major
relation: do/undo (supersede)
status: proposed            # staged on promotion/api-rate-limiting — NOT on master head
scope: enterprise
adoptionPolicy: auto
optedIn: true
tokensSavedPerUse: 141      # measured A/B proxy: 404 -> 263
derivedFromCapsule: CAP-S001
contributedBy: saim <saim@localhost>
escalation: human-review-required (contradicts published guidance)
usedByAgents: [ "agent/factory-implementer" ]
useCases: [ "Shared-upstream 429 handling", "Honoring Retry-After at the gateway", "Avoiding client retry storms" ]
---

# API Rate Limiting  `skill/api-rate-limiting@2.0.0`  *(PROPOSED — supersede)*

> **THIS IS A STAGED PROPOSAL, NOT A PUBLISHED VERSION.** It lives on the
> `promotion/api-rate-limiting` ref and supersedes `1.0.0` **only if** agentic CI
> passes **and** human review signs off (it contradicts published guidance).

On shared third-party upstreams, do **NOT** add client-side backoff/retry loops
on 429s — they amplify the thundering herd. **Fail fast, honor the upstream
`Retry-After`, and surface it to the caller.** Centralize rate-limit accounting
at the gateway, not per client.

## What changed vs 1.0.0 (do/undo)

- **1.0.0 (superseded):** "be prepared for unexpected rate limits" → add
  client-side **backoff + retry** on 429s.
- **2.0.0 (this):** **remove** client retries on shared upstreams; **fail fast +
  honor `Retry-After`**; propagate 429 to the caller.

This is a **contradiction** of 1.0.0, so it is a **major supersede** — not a
minor/patch.

## Capsule provenance

Distilled from a **real Claude Code coding session**, capsule **CAP-S001**
(session `c3d8e1b7`, project `API Gateway`, model `claude-opus-4-8`, contributed
by **saim**, distilled locally via Ollama `qwen2.5-coder:14b`).

> **Finding:** Do not add client-side backoff/retry on shared-upstream 429s; fail
> fast, honor `Retry-After`, and surface it to the caller.

Capsule transfer score: **58/100** · novelty **84** · importance **88**.

## Agentic-CI gate (must pass before publish)

See `CI-2.0.0.md`. Summary: pass-rate 6/10 → **9/10**, tokens/task 404 → **263**
(−35%), 429 amplification **resolved**, **no regressions**. Reward improves on
every axis → **eligible to publish**, pending human review (contradiction).

## Promotion state

```
status:    proposed
staged-on: promotion/api-rate-limiting
gate:      PASS (novelty 84 >= 80; CI reward improved)
blocker:   human review (do/undo contradiction) — confirm no client relies on auto-retry
on-merge:  master head -> api-rate-limiting@2.0.0 (published); update registry.json + CHANGELOG.md
on-reject: stays 1.0.0; CAP-S001 archived `rejected`, evidence retained in Backboard
```
