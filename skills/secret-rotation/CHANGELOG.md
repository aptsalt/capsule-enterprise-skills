# Changelog — skill/secret-rotation

RL audit trail. Every version is a capsule finding the gate promoted into the
enterprise registry, distilled from a real Claude Code session via local Ollama.
Newest first. Versions follow semver (major/minor/patch).

## 1.0.0 — major — 2026-06-27T13:38:51.204Z  [published]
- **Learned from:** CAP-V005 (session `3b9c2e08`, project `Beacon`, model `claude-opus-4-8`)
- **Finding:** Rotate secrets with overlapping dual-validity windows — provision and activate the new secret before revoking the old one — so in-flight requests don't fail with 401 mid-rotation.
- **Change:** New skill introduced for zero-downtime secret rotation via overlapping dual-validity windows.
- **Tokens saved/use:** 1404 · **Score delta:** +5 · **Adopted by:** 2 agent(s)
