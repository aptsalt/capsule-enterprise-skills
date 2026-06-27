---
id: CAP-S001
author: saim <saim@localhost>
session: c3d8e1b7
project: API Gateway
model: claude-opus-4-8
createdAt: 2026-06-27T10:00:00.000Z
novelty: 84
importance: 88
transferScore: 58
semanticSignature: "sig:api-rate-limit::failfast-honor-retry-after::CONTRADICTS(backoff-retry)"
targetSkill: skill/api-rate-limiting
contradicts: "skill/api-rate-limiting@1.0.0 (CAP-R003)"
relation: do/undo
storedIn: Backboard
threadId: c3d8e1b7-77aa-4bd1-9c0e-2f5a9b3c4d61
---

# CAP-S001 — "Don't auto-retry shared upstreams; fail fast and honor Retry-After"

## Intent
A gateway endpoint fronting a shared third-party API kept collapsing under load.
The existing `api-rate-limiting@1.0.0` guidance had us add client-side
backoff + retry on 429s.

## Mental model
On a **shared** upstream, every client adding its own backoff+retry creates a
**thundering herd** the moment the window resets — the retries themselves are the
outage. The upstream already tells us exactly when to come back via the
`Retry-After` header. Re-deriving a backoff schedule both ignores that and
amplifies load.

## Finding (CONTRADICTS current guidance)
> Do **NOT** add client-side backoff/retry loops on shared-upstream 429s.
> **Fail fast**, read and **honor the upstream `Retry-After`**, and **surface it
> to the caller** (propagate 429 + Retry-After) instead of silently retrying.
> Centralize rate-limit accounting at the gateway, not per client.

## Conflict declaration
- **Existing (DO X):** `api-rate-limiting@1.0.0` — add backoff + retry on rate limits.
- **This (UNDO X / DO Y):** remove client retries; fail fast + honor Retry-After.
- **Relation:** `do/undo` (contradictory, not additive) → cannot be a patch/minor.

## Measured evidence (A/B harness, gateway tasks)
| Metric | current 1.0.0 (backoff+retry) | proposed (fail-fast + Retry-After) |
|---|---|---|
| Pass rate on representative tasks | 6/10 | **9/10** |
| Upstream 429 amplification | high (retry storms) | **none** |
| Tokens / task (measured proxy) | 404 | **263** |
| p99 added latency under load | high | **low** |

## Routing (proposed)
- **Target:** `skill/api-rate-limiting`
- **Proposes:** **major** supersede → `2.0.0`
- **Status:** `proposed` (gated; escalated to human review — see `RESOLUTION.md`)
