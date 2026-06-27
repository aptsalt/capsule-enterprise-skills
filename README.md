# CAPSULE — Enterprise Skills Registry

The **enterprise, capsule-maxxed skills registry** for the 8090 Software Factory · CAPSULE module.

> Skills here are distilled from **real coding sessions** via local Ollama (`qwen2.5-coder:14b`); the durable
> distilled memory lives in **Backboard**. `master` always holds the **latest published version of every
> enterprise skill** — the head of the RL loop. Each skill folder is a self-describing, versioned unit with
> an audit trail back to the capsule that produced it.

This is the published, public half of **CAPSULE** — the capture + feedback (RL) layer for the Software
Factory. The app that mints these skills lives at **[github.com/aptsalt/capsule](https://github.com/aptsalt/capsule)**.

---

## What it is

A git repo *is* the registry. The model is deliberately boring and auditable:

```
skills/<skill-id>/
  SKILL.md       frontmatter + description + capsule provenance + token savings
  CHANGELOG.md   full semver history, each entry citing the real capsule it learned from
registry.json    machine index: skill id → current version, use-cases, tokensSavedPerUse
promotion/       staged, proposed-but-not-yet-published versions (CI candidates)
MERGE-LEDGER.md  append-only multi-dev reconciliation record (dedup / conflict)
PROMOTION.md     the governance + agentic-CI spec
PURGE-LEDGER.md  append-only retirement record (active → deprecated → archived → purged)
```

One commit per version bump; the commit message names the capsule and finding — that is the RL audit trail.
Only distilled briefings are persisted to Backboard, never raw transcripts.

---

## The 28-skill catalog (13 real + 15 popular)

`master` carries **28 skills**: **13 capsule-distilled** (minted from real sessions) and **15 popular
engineering seeds** (admitted at `1.0.0` from community best practice under capsules `CAP-P001..P015`, and
following the same RL loop from there on).

### 13 capsule-distilled (minted from real sessions)

| Skill | Version | Policy | Saved/use | From capsule |
|-------|---------|--------|-----------|--------------|
| `skill/creative-franchise-expansion` | 1.0.0 | auto | 72 | CAP-R001 |
| `skill/automation-maintenance` | 1.0.0 | auto | 1296 | CAP-R002 |
| `skill/api-rate-limiting` | 1.0.0 | auto | 157 | CAP-R003 |
| `skill/angular-upgrade` | 1.0.0 | auto | 1968 | CAP-R004 |
| `skill/command-verification` | 2.0.0 | auto | 1920 | CAP-R005 |
| `skill/api-security` | 1.0.0 | auto | 1896 | CAP-R006 |
| `skill/memory-management` | 1.0.0 | auto | 1800 | CAP-R008 |
| `skill/db-migration-safety` | 1.0.0 | auto | 1740 | CAP-V002 |
| `skill/docker-build-caching` | 1.0.0 | auto | 612 | CAP-V003 |
| `skill/ci-flake-quarantine` | 1.0.0 | auto | 980 | CAP-V004 |
| `skill/secret-rotation` | 1.0.0 | auto | 1404 | CAP-V005 |
| `skill/websocket-reconnection` | 1.0.0 | auto | 828 | CAP-V006 |
| `skill/ui-modularity` | 1.0.0 | auto | — | **CAP-SESSION-1a6fcc9b** (self-capture) |

### 15 popular engineering seeds — grouped, each group pinned by one dev

**Backend / API** — pinned by **`dee`**

| Skill | Version | Saved/use | Seed capsule |
|-------|---------|-----------|--------------|
| `skill/rest-api-design` | 1.0.0 | 1744 | CAP-P001 |
| `skill/oauth2-jwt-auth` | 1.0.0 | 1653 | CAP-P002 |
| `skill/idempotency-keys` | 1.0.0 | 1660 | CAP-P003 |
| `skill/cursor-pagination` | 1.0.0 | 1661 | CAP-P004 |
| `skill/redis-caching` | 1.0.0 | 857 | CAP-P005 |

**Infra / DevOps** — pinned by **`ven`**

| Skill | Version | Saved/use | Seed capsule |
|-------|---------|-----------|--------------|
| `skill/docker-containerization` | 1.0.0 | 1244 | CAP-P006 |
| `skill/kubernetes-orchestration` | 1.0.0 | 1741 | CAP-P007 |
| `skill/ci-cd-pipelines` | 1.0.0 | 1281 | CAP-P008 |
| `skill/structured-logging` | 1.0.0 | 825 | CAP-P009 |
| `skill/observability-tracing` | 1.0.0 | 1406 | CAP-P010 |

**Data / Quality** — pinned by **`saim`**

| Skill | Version | Saved/use | Seed capsule |
|-------|---------|-----------|--------------|
| `skill/database-indexing` | 1.0.0 | 2044 | CAP-P011 |
| `skill/input-validation` | 1.0.0 | 859 | CAP-P012 |
| `skill/retry-with-backoff` | 1.0.0 | 1196 | CAP-P013 |
| `skill/async-concurrency` | 1.0.0 | 2163 | CAP-P014 |
| `skill/test-automation` | 1.0.0 | 1754 | CAP-P015 |

`registry.json` is the machine index of record; each SKILL.md frontmatter must agree with it on
`currentVersion`, `tokensSavedPerUse`, `useCases`, and `usedByAgents`.

---

## Branch model

- **`master`** = the **enterprise** head — all 28 skills, latest *published* version of each. It only moves
  when a proposed version passes agentic CI + review.
- **`dee` / `ven` / `saim`** = personal/local developer repos. Each **pins a unique, role-aligned set of 5**
  (Backend / Infra / Data above) in `my-project/capsule.lock` — sometimes intentionally *older* versions —
  and is told when `master` has moved ahead of a pin ("updates available"). Per-dev reconciliation records
  live on the contributor's branch under `my-project/contributed-capsules/RESOLUTION.md`.

A developer's local registry (CAPSULE app, branch `local-deepak`) accumulates the day's earned upgrades as
local commits, then promotes them upstream at end-of-day.

---

## Promotion (PR + agentic CI)

Clearing the RL gate (`transferScore ≥ threshold` **OR** `novelty ≥ 80`) **proposes** a version — it does
**not** push to `master` head. See [`PROMOTION.md`](PROMOTION.md).

```
capsule (clears gate)
      │ propose
      ▼
promotion/<skill>/PROPOSED-x.y.z.SKILL.md   ← staged candidate (+ CI-x.y.z.md report)
      │ agentic CI: multi-sample A/B harness + regression check
      ├── reward improves + review OK ──▶ merge → bump on master head (PUBLISHED)
      ├── reward improves, contradiction ─▶ HUMAN REVIEW required → merge or reject
      └── reward flat/worse ─────────────▶ held `proposed` or `rejected` (no publish)
```

- **Agentic CI** runs the **new** version vs the **current** published version on representative tasks,
  measuring token savings / pass-rate / transfer lift on the local model (real token counts), plus a
  **regression check** that replays prior capsules touching the skill. A bump publishes *only if measured
  reward improves and no regressions* — CI for skills. A still-`proposed` candidate never bumps
  `currentVersion` on `master`; `registry.json` carries a `proposedSupersede` block for that (see
  `api-rate-limiting`).
- **Multi-dev reconciliation** is recorded append-only in [`MERGE-LEDGER.md`](MERGE-LEDGER.md):
  - **`ML-001` — DEDUP** — `ven`'s `CAP-V001` re-discovered `dee`'s canonical `command-verification` finding
    (semantic cosine 0.94 ≥ 0.90). No new version forged; provenance updated to credit both authors.
  - **`ML-002` — CONFLICT (do/undo)** — `saim`'s `CAP-S001` contradicts `api-rate-limiting@1.0.0`
    (remove client retries → fail-fast + honor `Retry-After`). Cleared the gate, won the A/B on every axis,
    staged as a `2.0.0` supersede under `promotion/` — **escalated to human review**, never force-merged.

Bump policy is relation-driven: re-discovery → **DEDUP**; additive → **minor**; refinement → **patch**;
contradictory do/undo → **major (supersede) or reject** (never a silent minor, always escalates).

---

## Purge / retire

The opposite pole of promotion, so the registry never silts up with dead skills. Recorded append-only in
**`PURGE-LEDGER.md`** (mirrors the merge ledger), staged and reviewable — never a silent delete.

```
active  →  deprecated  →  archived  →  purged
```

The scanner flags candidates as **ABSORBED / SUPERSEDED / UNUSED / LOW_VALUE / ORPHANED**, computed from
measured token savings (`source: measured`), the merge ledger (`source: ledger`), and arithmetic over them
(`source: derived`). It is **dry-run by default**; `archive` MOVES `skills/<id>/ → archive/<id>/`
(recoverable) and even a hard purge is ledgered first. Backboard provenance is never touched. Driven from the
app by `scripts/purge-skills.ts`.

---

## Pull a skill

```bash
capsule pull skill/<id>@<ver>     # pin an exact, reproducible version
capsule pull skill/<id>           # latest published on master
```

A personal/local dev repo (see branch `dee`) pins specific — sometimes intentionally older — versions in
`my-project/capsule.lock`, and is told when `master` has moved ahead of those pins.

---

## The real proof

This registry has been moved by the live loop, not by hand:

- **`skill/ui-modularity@1.0.0`** was minted from CAPSULE's **own** build session — capsule
  `CAP-SESSION-1a6fcc9b` (session `1a6fcc9b`, project `relay`), distilled locally on `qwen2.5-coder:14b` —
  and **promoted into `master` (PR #4)**. The system captured itself.
- **`dee`** promoted real upgrades on top of the seeds: **`rest-api-design@1.0.1`** and
  **`oauth2-jwt-auth@1.0.1`**.

Each leaves a commit + changelog + ledger trail naming the originating capsule — the RL audit trail end to
end.

---

**App:** [github.com/aptsalt/capsule](https://github.com/aptsalt/capsule) — the Next.js app that captures,
distills, scores, and promotes into this registry.

---
Deepak Singh Kandari · [github.com/aptsalt](https://github.com/aptsalt)
