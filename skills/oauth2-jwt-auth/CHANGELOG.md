# Changelog — skill/oauth2-jwt-auth

RL audit trail. Every version is a capsule finding the gate promoted into the
enterprise registry. The 1.0.0 seed is canonical community best practice; later
versions are distilled from real Claude Code sessions via local Ollama. Newest
first. Versions follow semver (major/minor/patch).

## 1.0.1 — patch — 2026-06-27T17:25:08.517Z  [published]
- **Learned from:** CAP-DEE-01 (real session `b505be13`, distilled via `ollama:qwen2.5-coder:14b (local)`)
- **Finding:** Always validate API credentials before making requests to avoid repeated `401 Invalid authentication credentials` errors.
- **Change:** Added fail-fast credential handling to the canonical guidance — pre-flight validation that a credential is present/well-formed before authenticated outbound calls, and treating an upstream `401 Invalid authentication credentials` as a terminal auth failure (re-authenticate, don't loop) instead of producing repeated-401 storms. New use-case + frontmatter `description`/`useCases` updated.
- **Bump rule:** patch — refines existing OAuth2/JWT guidance (classifier fit 0.90, session transfer 54/100 → below the minor threshold of 55).
- **Backboard:** thread `90466bf8-4b15-4065-a1ee-1b2d4bee9e57` · message `f201af0e-ede3-4dab-8fad-9a53ebe4a5ff`
- **Tokens saved/use (proxy):** 648 · **Score delta (proxy):** +2

## 1.0.0 — major — 2026-06-27T12:00:00.000Z  [published]
- **Learned from:** CAP-P002 — seeded from community best practice (top-15 popular engineering skill, category `backend`)
- **Finding:** Implement standards-compliant OAuth2 flows and JWT validation: short-lived access tokens, rotated refresh tokens, and verified signatures.
- **Change:** Initial canonical guidance body, use-cases, and frontmatter for `skill/oauth2-jwt-auth`.
- **Tokens saved/use:** 1653 · **Seed score:** transfer 80/novelty 64/importance 72
