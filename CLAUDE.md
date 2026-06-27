# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

The enterprise **skills registry** for the CAPSULE module (Content Engine program). It contains no application code — it is versioned Markdown skill bodies plus a JSON index, managed as the published head of an RL loop. There is **no build, lint, or test command**; "validation" means keeping the documents internally consistent (see Invariants).

## The RL loop (how content arrives here)

A real Claude Code session is distilled by a **local Ollama model (`qwen2.5-coder:14b`)** into a *capsule* (a compressed finding; durable memory lives in **Backboard**). The RL gate scores it; if it clears, the finding becomes a new **semver** version of a skill and is committed to `master`. See [README.md](README.md) for the full diagram.

Nothing in this repo runs that loop — the loop produces commits *to* this repo. Your job here is editing the published artifacts those commits write.

## Repository layout

- `skills/<skill-id>/SKILL.md` — frontmatter (id, currentVersion, tokensSavedPerUse, usedByAgents, useCases) + body + capsule provenance.
- `skills/<skill-id>/CHANGELOG.md` — full semver history, newest first, each entry citing the capsule it learned from. The RL audit trail.
- `registry.json` — machine index: skill id → currentVersion, useCases, derivedFromCapsule, tokensSavedPerUse. Must mirror the SKILL.md frontmatter.
- `promotion/<skill>/` — **staged candidates not yet on `master`** (`PROPOSED-<version>.SKILL.md` + `CI-<version>.md`). Clearing the gate proposes here; it does not publish.
- `MERGE-LEDGER.md` — append-only audit trail of multi-dev capsule reconciliations.
- `PROMOTION.md` — governance + agentic-CI spec; read before touching anything in `promotion/`.

## Branches

- `master` — latest **published** version of every skill ("capsule-maxxed" head). Only moves when a proposed version passes agentic CI + review.
- `dee` / `ven` / `saim` — per-developer repos that **pin** specific (sometimes intentionally older) versions and contribute capsules. The per-dev record of a reconciliation lives on the contributor's branch under `my-project/contributed-capsules/RESOLUTION.md`.

## Conventions that aren't obvious from a single file

- **Promotion, not direct push.** A new version is staged under `promotion/<skill>/` first. `master` head moves only after the A/B harness shows improved reward (tokens down / pass-rate up / transfer up) **and** no regressions. Do not bump a `currentVersion` on `master` for a candidate that is still `proposed` — `registry.json` carries a `proposedSupersede` block for that (see `api-rate-limiting`).
- **Bump policy is relation-driven** (see MERGE-LEDGER table): re-discovery → **DEDUP** (no new version, merge provenance, keep all authors); additive → **minor**; refinement → **patch**; contradictory `do`/`undo` → **major (supersede) or reject**, never a silent minor, and it **escalates to human review**.
- **Commit per version bump.** One commit per published version; the message names the capsule and finding (e.g. `feat(<skill>): v1.2.0 — learned from CAP-XXXX (...)`). That message *is* the audit trail.
- **MERGE-LEDGER is append-only.** Corrections are new entries, never in-place edits.

## Invariants to preserve on any edit

1. `registry.json` and each `skills/<id>/SKILL.md` frontmatter agree on `currentVersion`, `tokensSavedPerUse`, `useCases`, `usedByAgents`.
2. A version that appears in a `CHANGELOG.md` as `[published]` exists on `master`; `proposed` candidates live only under `promotion/`.
3. Every finding has one canonical capsule; provenance lists every contributing author.
