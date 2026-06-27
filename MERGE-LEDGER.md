# MERGE-LEDGER — multi-dev capsule resolutions

This ledger is the **append-only audit trail** for how capsules contributed by
multiple developers (`dee`, `ven`, `saim`, …) are reconciled into the single
canonical enterprise registry on `master`. Every entry records the relation
(dedup / additive / refinement / conflict), the evidence the pipeline used, and
the final decision.

**Relation → bump policy**

| Relation between capsules on the same skill | Bump |
|---|---|
| Near-identical signature (re-discovery) | **DEDUP** — no version; merge provenance |
| Adds a new, compatible facet | **minor** |
| Tightens/clarifies an existing facet | **patch** |
| Contradicts existing guidance (`do` vs `undo`) | **major (supersede)** or **reject** — escalate ties to human review |

Decisions are made by **measured reward** (A/B harness: token savings, pass-rate,
transfer lift) **+ recency**, not opinion. Contradictions always escalate to
human/agentic review before publish.

---

## ML-001 — DEDUP — ven ⨝ dee on `skill/command-verification`

- **Date:** 2026-06-27T09:05:00.000Z
- **Capsules:** `CAP-V001` (author **ven**) vs canonical `CAP-R007` behind `command-verification@1.0.0` (co-originated with **dee**, who pins 1.0.0)
- **Relation:** near-identical re-discovery
- **Signatures:** both `sig:cmd-verify::inspect-actual-state-over-inference`
- **Semantic-memory cosine:** **0.94** (≥ 0.90 dedup threshold)
- **Decision:** **DEDUP.** No new version forged. `CAP-V001` merged into the
  canonical capsule; provenance updated to credit **both ven and dee**.
- **Registry effect:** `command-verification` stays `1.0.0` for this finding
  (master head remains `2.0.0` for the later docs-verification rewrite).
  Contributors: `dee` (CAP-R007), `ven` (CAP-V001).
- **Backboard:** the two facts merged into one node with two provenance edges.
- **Source of record:** `ven` branch → `my-project/contributed-capsules/RESOLUTION.md`

```
skill/command-verification (canonical "inspect actual system state")
  ├── dee  — CAP-R007  (pinned 1.0.0 consumer + co-originator)
  └── ven  — CAP-V001  (independent re-discovery, deduped 2026-06-27)
```

---

## ML-002 — CONFLICT (do/undo) — saim vs `skill/api-rate-limiting`

- **Date:** 2026-06-27T10:05:00.000Z
- **Capsules:** `CAP-S001` (author **saim**) vs live finding `CAP-R003` behind `api-rate-limiting@1.0.0`
- **Relation:** **do/undo (contradictory)**
  - DO X (`1.0.0`): add client-side backoff + retry on 429s
  - UNDO X / DO Y (`CAP-S001`): remove client retries; **fail fast + honor `Retry-After`**, surface to caller
- **Gate:** CAP-S001 novelty **84** (≥ 80), transfer **58** — clears the gate
- **Agentic-CI A/B (new vs current), representative gateway tasks + regression check:**

  | Signal | current 1.0.0 | proposed 2.0.0 | Δ |
  |---|---|---|---|
  | Pass rate | 6/10 | **9/10** | +30pp |
  | Tokens/task (measured proxy) | 404 | **263** | −35% |
  | 429 amplification | retry storms | **none** | resolved |
  | Regression (other capsules) | — | **no regressions** | pass |

- **Tie-break:** measured reward improves on every axis **and** CAP-S001 is more
  recent (2026-06-27 > 2026-06-19) → both favor the new guidance.
- **Decision:** **SUPERSEDE → `api-rate-limiting@2.0.0` (major)**, status
  **`proposed`**, staged on `promotion/api-rate-limiting/` — **not** force-merged.
- **Escalation:** contradiction → **human review required** before publish
  (confirm no client depends on the old auto-retry contract). On reject, stays
  `1.0.0` and CAP-S001 is archived `rejected` with evidence retained.
- **Source of record:** `saim` branch → `my-project/contributed-capsules/RESOLUTION.md`
  and `promotion/api-rate-limiting/PROPOSED-2.0.0.SKILL.md`.

---

### Ledger invariants
1. **One canonical capsule per finding.** Dedup collapses re-discoveries; provenance keeps every author.
2. **No silent contradiction.** A `do/undo` can never be a minor/patch — it is supersede or reject, and it escalates.
3. **Reward gates publish.** A proposed version merges to `master` head only if the A/B harness shows improved reward and prior-capsule regressions pass.
4. **Append-only.** Entries are never edited in place; corrections are new entries.
