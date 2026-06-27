# CAPSULE — Enterprise Skills Registry (capsule-maxxed)

This repository is the **enterprise, capsule-maxxed skills registry** for the
*Content Engine* program on the 8090 Software Factory · CAPSULE module.

**Skills here are distilled from real coding sessions via local Ollama
(`qwen2.5-coder:14b`); the durable distilled memory lives in Backboard.**

`master` always holds the **latest published version of every enterprise skill** —
the "capsule-maxxed" head of the RL loop. Each skill folder is a self-describing,
versioned unit with an audit trail back to the capsule that produced it.

## The RL loop (how a skill version is born)

```
real Claude Code session  ──▶  Capsule Refinery (local Ollama qwen2.5-coder:14b)
                                               │
                                               ▼
                          capsule (compressed finding, stored in Backboard)
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

Every real coding session is compressed into a **capsule** by the local model. The RL
gate scores it (novelty / importance / transfer). If accepted, the **Skill Foundry**
promotes the capsule's `finding` into a new **semver** version of the target skill and
commits it here. The commit message names the capsule and finding — that is the RL
audit trail. Only the distilled briefings are persisted to Backboard.

## Layout

```
skills/<skill-id>/
  SKILL.md       frontmatter + description + capsule provenance + token savings
  CHANGELOG.md   full semver history, each entry citing the real capsule it learned from
registry.json    machine index: skill id -> current version, use-cases, tokensSavedPerUse
```

## Skills (latest on master)

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

## Pull a skill

```bash
capsule pull <skill-id>@<version>     # pin an exact, reproducible version
capsule pull <skill-id>               # latest published on master
```

A personal/local developer repo (see branch **`dee`**) pins specific — sometimes
intentionally older — versions in `my-project/capsule.lock`, and is told when
`master` has moved ahead of those pins.
