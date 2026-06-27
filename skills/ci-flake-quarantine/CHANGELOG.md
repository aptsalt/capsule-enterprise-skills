# Changelog — skill/ci-flake-quarantine

RL audit trail. Every version is a capsule finding the gate promoted into the
enterprise registry, distilled from a real Claude Code session via local Ollama.
Newest first. Versions follow semver (major/minor/patch).

## 1.0.0 — major — 2026-06-27T12:05:19.730Z  [published]
- **Learned from:** CAP-V004 (session `f0a6b13c`, project `Content Engine`, model `claude-opus-4-8`)
- **Finding:** When a test fails non-deterministically, quarantine it after N flaky runs instead of blanket-retrying the suite — blanket retries mask real regressions and inflate CI time.
- **Change:** New skill introduced for quarantining flaky tests instead of masking them with blanket retries.
- **Tokens saved/use:** 980 · **Score delta:** +5 · **Adopted by:** 2 agent(s)
