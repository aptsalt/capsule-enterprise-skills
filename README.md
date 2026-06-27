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

## Top-15 popular engineering catalog (seeded from community best practice)

In addition to the capsule-distilled skills above, `master` carries a catalog of the
**15 most popular real-world engineering skills**, seeded at `1.0.0` from community
best practice and admitted under capsules `CAP-P001..P015`. They follow the same RL
loop from here on. Each dev branch pins a unique, role-aligned set of 5.

**Backend / API** (pinned by **`dee`**)

| Skill | Version | Category | Saved/use | Seed capsule |
|-------|---------|----------|-----------|--------------|
| `skill/rest-api-design` | 1.0.0 | backend | 1744 | CAP-P001 |
| `skill/oauth2-jwt-auth` | 1.0.0 | backend | 1653 | CAP-P002 |
| `skill/idempotency-keys` | 1.0.0 | backend | 1660 | CAP-P003 |
| `skill/cursor-pagination` | 1.0.0 | backend | 1661 | CAP-P004 |
| `skill/redis-caching` | 1.0.0 | backend | 857 | CAP-P005 |

**Infra / DevOps** (pinned by **`ven`**)

| Skill | Version | Category | Saved/use | Seed capsule |
|-------|---------|----------|-----------|--------------|
| `skill/docker-containerization` | 1.0.0 | infra/devops | 1244 | CAP-P006 |
| `skill/kubernetes-orchestration` | 1.0.0 | infra/devops | 1741 | CAP-P007 |
| `skill/ci-cd-pipelines` | 1.0.0 | infra/devops | 1281 | CAP-P008 |
| `skill/structured-logging` | 1.0.0 | infra/devops | 825 | CAP-P009 |
| `skill/observability-tracing` | 1.0.0 | infra/devops | 1406 | CAP-P010 |

**Data / Quality** (pinned by **`saim`**)

| Skill | Version | Category | Saved/use | Seed capsule |
|-------|---------|----------|-----------|--------------|
| `skill/database-indexing` | 1.0.0 | data/quality | 2044 | CAP-P011 |
| `skill/input-validation` | 1.0.0 | data/quality | 859 | CAP-P012 |
| `skill/retry-with-backoff` | 1.0.0 | data/quality | 1196 | CAP-P013 |
| `skill/async-concurrency` | 1.0.0 | data/quality | 2163 | CAP-P014 |
| `skill/test-automation` | 1.0.0 | data/quality | 1754 | CAP-P015 |

The registry now indexes **27 skills** (12 capsule-distilled + 15 popular seeds).

## Pull a skill

```bash
capsule pull <skill-id>@<version>     # pin an exact, reproducible version
capsule pull <skill-id>               # latest published on master
```

A personal/local developer repo (see branch **`dee`**) pins specific — sometimes
intentionally older — versions in `my-project/capsule.lock`, and is told when
`master` has moved ahead of those pins.
