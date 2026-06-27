# Changelog — skill/docker-build-caching

RL audit trail. Every version is a capsule finding the gate promoted into the
enterprise registry, distilled from a real Claude Code session via local Ollama.
Newest first. Versions follow semver (major/minor/patch).

## 1.0.0 — major — 2026-06-27T10:47:03.552Z  [published]
- **Learned from:** CAP-V003 (session `7d3e0b92`, project `Foundry`, model `claude-opus-4-8`)
- **Finding:** Order Dockerfile layers from least to most volatile and copy dependency manifests before source, so a code change doesn't bust the dependency-install cache layer.
- **Change:** New skill introduced for Dockerfile layer ordering that maximizes build-cache reuse.
- **Tokens saved/use:** 612 · **Score delta:** +4 · **Adopted by:** 2 agent(s)
