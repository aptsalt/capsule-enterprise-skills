# Meridian Bank — Enterprise Skills Registry (capsule-maxxed)

This repository is the **enterprise, capsule-maxxed skills registry** for the
*Payments Copilot* program on the 8090 Software Factory.

`master` always holds the **latest published version of every enterprise skill** —
the "capsule-maxxed" head of the RL loop. Each skill folder is a self-describing,
versioned unit with an audit trail back to the capsule that produced it.

## The RL loop (how a skill version is born)

```
coding session  ──▶  Capsule Refinery  ──▶  capsule (compressed learning, stored in Backboard)
                                               │
                                               ▼
                                         RL gate (novelty · importance · transfer)
                                               │  accepted
                                               ▼
                                       Skill Foundry forges a new SEMVER version
                                               │
                                               ▼
                                  committed to THIS repo's `master`  (one commit per version bump)
                                               │
                                               ▼
                       personal/local repos (branch `dee`) pull & PIN specific versions
                                               │
                                               ▼
                              "updates available" when master moves ahead of a pin
```

Every coding session is compressed into a **capsule**. The RL gate scores it
(novelty / importance / transfer). If accepted, the **Skill Foundry** promotes the
capsule's `finding` into a new **semver** version of the target skill and commits it
here. The commit message names the capsule and finding — that is the RL audit trail.

## Layout

```
skills/<skill-id>/
  SKILL.md       frontmatter + description + capsule provenance + token savings
  CHANGELOG.md   full semver history, each entry citing the capsule it learned from
registry.json    machine index: skill id -> current version, use-cases, tokensSavedPerUse
```

## Skills (latest on master)

| Skill | Version | Policy | Saved/use | From |
|-------|---------|--------|-----------|------|
| `skill/payment-idempotency`   | 2.1.0 | auto   | 1800 | CAP-1001 |
| `skill/iso20022-mapper`       | 1.3.0 | auto   | 2400 | CAP-1002 |
| `skill/pci-redaction`         | 1.2.0 | manual | 1500 | CAP-1003 |
| `skill/reconciliation-ledger` | 1.1.0 | auto   | 1100 | CAP-1004 |
| `skill/sca-challenge`         | 1.0.0 | manual | 3200 | CAP-1005 |

## Pull a skill

```bash
capsule pull <skill-id>@<version>     # pin an exact, reproducible version
capsule pull <skill-id>               # latest published on master
```

A personal/local developer repo (see branch **`dee`**) pins specific — sometimes
intentionally older — versions in `my-project/capsule.lock`, and is told when
`master` has moved ahead of those pins.
