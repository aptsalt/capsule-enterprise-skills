# PROMOTION — how a capsule becomes a published skill version

This is the **governance + agentic-CI** spec for the multi-dev CAPSULE registry.
It documents how a capsule that clears the gate becomes a **proposed** version,
how the agentic pipeline **tests it before publish**, and how multi-dev
**dedup** and **conflict** are reconciled (recorded in `MERGE-LEDGER.md`).

> TL;DR: passing the gate **proposes** a version on a `promotion/<skill>` staging
> ref — it does **not** push to `master` head. Agentic CI (the A/B harness +
> regression check) decides whether the proposed version is **published**,
> **held**, or **rejected**. Contradictions escalate to human review.

---

## 1. Promotion, not direct push

A capsule clears the **RL gate** when `transferScore >= threshold` **OR**
`novelty >= 80`. Clearing the gate produces a **PROPOSED skill version**, staged
as:

```
promotion/<skill>/PROPOSED-<version>.SKILL.md      # the candidate skill body
promotion/<skill>/CI-<version>.md                  # the agentic-CI report
```

This is the equivalent of a **PR / staging ref** of the enterprise repo. No
developer (and no agent) force-pushes a new version onto `master`. The head of
`master` only moves when the proposed version **passes agentic CI** and review
merges it.

```
capsule (clears gate)
      │  propose
      ▼
promotion/<skill>/PROPOSED-x.y.z   ← staged candidate (this dir)
      │  agentic CI: A/B harness + regression check
      ├── reward improves  + review OK ──▶ merge → bump on master head (published)
      ├── reward improves, contradiction ─▶ HUMAN REVIEW required → merge or reject
      └── reward flat/worse ─────────────▶ held `proposed` or `rejected` (no publish)
```

## 2. Agentic CI — testing BEFORE the upgrade (CI-for-skills)

Before publishing a proposed version, the pipeline runs:

1. **A/B harness** — the **new** version vs the **current** published version on
   representative tasks for that skill, measuring **token savings**, **pass-rate**,
   and **transfer lift** (measured proxy on the local model, real token counts).
2. **Regression check** — replays prior capsules that touched the skill to ensure
   the new version does not break previously-learned behavior.

**Merge rule:** the version bump is published **only if measured reward improves**
(tokens down / pass-rate up / transfer up) **and** no regressions. Otherwise it
stays `proposed` or is `rejected`. This is CI for skills — a version upgrade must
*earn* its place with measured evidence, exactly like code passing tests.

## 3. Dedup (multi-dev, same finding)

Each capsule carries a **semantic signature**. On submission the pipeline matches
it against the registry + Backboard semantic memory. If cosine ≥ **0.90** to an
existing finding, it is a **re-discovery**: the capsules **merge into ONE
canonical capsule** and provenance keeps **all** authors. No redundant version is
forged. *(Live example: `ML-001`, ven ⨝ dee on `command-verification`.)*

## 4. Conflict (do/undo)

When capsule A says **do X** and capsule B says **undo X / do Y** against the same
skill, the pipeline flags a **do/undo conflict**:

- **Contradictory** → **major (supersede)** or **reject** — never a silent minor.
- **Additive** → **minor**. **Refinement** → **patch**.
- Resolved by **measured reward + recency**; **ties escalate to human review**.
- Every resolution is appended to `MERGE-LEDGER.md`.

*(Live example: `ML-002`, saim vs `api-rate-limiting` → supersede `2.0.0`,
escalated.)*

## 5. Worked examples in this repo

| Ref | Case | Skill | Outcome | Staged artifact |
|-----|------|-------|---------|-----------------|
| ML-001 | DEDUP (ven + dee) | `command-verification` | merge provenance, no new version | `promotion/command-verification/PROPOSED-canonical-merge.md` |
| ML-002 | CONFLICT (saim) | `api-rate-limiting` | supersede `2.0.0`, proposed, escalated | `promotion/api-rate-limiting/PROPOSED-2.0.0.SKILL.md` + `CI-2.0.0.md` |

See each developer branch's `my-project/contributed-capsules/RESOLUTION.md` for
the per-dev record, and `MERGE-LEDGER.md` for the canonical audit trail.
