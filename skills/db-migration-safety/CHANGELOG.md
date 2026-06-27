# Changelog — skill/db-migration-safety

RL audit trail. Every version is a capsule finding the gate promoted into the
enterprise registry, distilled from a real Claude Code session via local Ollama.
Newest first. Versions follow semver (major/minor/patch).

## 1.0.0 — major — 2026-06-27T09:12:44.118Z  [published]
- **Learned from:** CAP-V002 (session `a1f29c4d`, project `Beacon`, model `claude-opus-4-8`)
- **Finding:** Run schema migrations as expand→backfill→contract: never drop or rename a column in the same deploy that stops writing it, or in-flight code will read a column that no longer exists.
- **Change:** New skill introduced for safe, zero-downtime schema migrations via the expand/backfill/contract pattern.
- **Tokens saved/use:** 1740 · **Score delta:** +6 · **Adopted by:** 2 agent(s)
