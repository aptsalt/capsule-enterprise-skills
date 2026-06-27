# my-project (developer: ven) — consuming + contributing enterprise skills

This is a **personal / local** repo for developer **ven**. Like `dee`, it pulls
a few **enterprise** skills from the CAPSULE registry on `master` and pins them
in `capsule.lock`. Unlike a pure consumer, ven also **contributes** a capsule
back up the RL loop (see `contributed-capsules/`).

## How it consumes the registry

```bash
# pull and pin exact versions into capsule.lock
capsule pull command-verification@1.0.0   # same finding ven re-discovered locally
capsule pull api-security@1.0.0
capsule pull memory-management@1.0.0
```

Only **3 of 7** enterprise skills are used here — this service is an internal
ops/automation tool, so the franchise/Angular/rate-limit skills are not pulled.

## What ven contributed (DEDUP case)

While debugging a flaky local job, ven's session produced capsule **CAP-V001**:
*"stop guessing — inspect the actual system state instead of trusting inferred
status."* When ven submitted it, the pipeline computed its **semantic signature**
and found it **near-identical** to the finding already behind
`skill/command-verification@1.0.0` (CAP-R007) — the exact version **dee** is
pinned on.

Rather than forging a duplicate skill, Backboard's semantic memory **merged**
the two into ONE canonical capsule. Provenance keeps **both** authors: ven and
dee are now co-contributors to `skill/command-verification`. See
`contributed-capsules/RESOLUTION.md` and the enterprise `MERGE-LEDGER.md`.

## Why pin (and why a pin is intentionally old)

Pinning gives reproducible builds. `command-verification` is pinned at **1.0.0**
on purpose: ven's own finding *is* the 1.0.0 "inspect system state" guidance, so
ven stays on it rather than auto-adopting the `2.0.0` "check official docs"
rewrite (master head). `capsule status` reports the drift (see `STATUS.md`).
