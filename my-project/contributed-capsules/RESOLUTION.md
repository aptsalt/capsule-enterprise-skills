# RESOLUTION — CAP-V001 (DEDUP / semantic merge)

**Developer:** ven &lt;ven@localhost&gt;
**Submitted capsule:** `CAP-V001` → target `skill/command-verification`
**Resolved:** 2026-06-27T09:05:00.000Z
**Decision:** **DEDUP — merged into canonical capsule. No new version forged.**

---

## What happened

When ven submitted `CAP-V001`, the multi-dev pipeline did **not** immediately
forge a new skill version. First it computed the capsule's **semantic
signature** and compared it against every finding already in the registry +
Backboard's semantic memory.

| | ven's CAP-V001 | existing CAP-R007 (behind `command-verification@1.0.0`) |
|---|---|---|
| Signature | `sig:cmd-verify::inspect-actual-state-over-inference` | `sig:cmd-verify::inspect-actual-state-over-inference` |
| Finding | "verify by directly inspecting the actual system state before acting" | "verify assumptions by directly inspecting the system state rather than relying solely on inferred information" |
| Cosine (semantic memory) | — | **0.94** (≥ 0.90 dedup threshold) |

The two findings are **near-identical re-discoveries** of the same principle by
two different developers. Forging a second skill (or a redundant version bump)
would fragment the registry and double-count token savings.

## Resolution

1. **Merge into ONE canonical capsule.** `CAP-V001` is folded into the canonical
   finding already published as `skill/command-verification@1.0.0`.
2. **Provenance keeps both authors.** The canonical skill's contributor list is
   updated to credit **both** developers:
   - `dee` — original pin/consumer + co-originator of the system-state-inspection finding (via CAP-R007).
   - `ven` — independent re-discovery (CAP-V001), 2026-06-27.
3. **No version change.** `command-verification` stays at `1.0.0` for the
   canonical finding (master head remains `2.0.0` for the later docs-verification
   rewrite). The dedup is recorded, not promoted.
4. **Backboard semantic memory** merges the two facts into a single node with two
   provenance edges, so future recall returns one canonical answer, not two.

## Credit (canonical provenance after merge)

```
skill/command-verification  (canonical "inspect actual system state" finding)
  ├── dee  — CAP-R007 / pinned 1.0.0 consumer
  └── ven  — CAP-V001 / independent re-discovery (deduped 2026-06-27)
```

Recorded upstream in the enterprise **`MERGE-LEDGER.md`** on `master`
(entry **ML-001**).
