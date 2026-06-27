---
name: Command Verification
id: skill/command-verification
proposedVersion: 1.0.0        # NO new version — canonical provenance merge only
relation: dedup
status: merged-provenance      # dedup recorded; no version bump
scope: enterprise
derivedFromCapsule: CAP-R007
mergedCapsule: CAP-V001
contributedBy: [ "dee", "ven" ]
---

# Command Verification — DEDUP / canonical provenance merge  *(no version bump)*

> This staged artifact records a **dedup**, not a version upgrade. `CAP-V001`
> (ven) was found to be a **re-discovery** of the canonical finding already
> published as `command-verification@1.0.0` (CAP-R007, co-originated by dee).
> The pipeline **merged provenance** — it did **not** forge a new version.

## Canonical finding (unchanged)

> When working with local commands, verify by **directly inspecting the actual
> system state** rather than relying on inferred/reported information.

## Why dedup (not a new version)

| | ven CAP-V001 | canonical CAP-R007 |
|---|---|---|
| Signature | `sig:cmd-verify::inspect-actual-state-over-inference` | `sig:cmd-verify::inspect-actual-state-over-inference` |
| Semantic cosine | — | **0.94** (≥ 0.90 dedup threshold) |

Forging a second version would fragment the registry and double-count token
savings. Instead, Backboard's semantic memory merges the two facts into one node.

## Canonical provenance after merge

```
skill/command-verification@1.0.0  ("inspect actual system state")
  ├── dee  — CAP-R007  (co-originator + pinned consumer)
  └── ven  — CAP-V001  (independent re-discovery, deduped 2026-06-27)
```

## Promotion state

```
status:   merged-provenance (dedup)
version:  unchanged — 1.0.0 (canonical finding); master head remains 2.0.0
ledger:   MERGE-LEDGER.md -> ML-001
publish:  none — provenance/credit update only
```
