# Changelog — skill/rest-api-design

RL audit trail. Every version is a capsule finding the gate promoted into the
enterprise registry. The 1.0.0 seed is canonical community best practice; later
versions are distilled from real Claude Code sessions via local Ollama. Newest
first. Versions follow semver (major/minor/patch).

## 1.0.1 — patch — 2026-06-27T17:01:55.030Z  [published]
- **Learned from:** CAP-DEE-01 (real session `12560ca4`, distilled via `ollama:qwen2.5-coder:14b (local)`)
- **Finding:** Implement rate limiting handling in your application to gracefully manage API errors due to server limitations.
- **Change:** Added rate-limit handling to the canonical guidance — server-side `429 + Retry-After` / `RateLimit-*` headers, and client-side honoring of `Retry-After` with jittered backoff instead of cascading errors. New use-case + frontmatter `description`/`useCases` updated.
- **Bump rule:** patch — refines existing REST guidance (classifier fit 0.80, session transfer 37/100 → below the minor threshold of 55).
- **Backboard:** thread `f094d4af-c5b7-40c6-bdac-b2b027e44f71` · message `6514d347-8e04-445f-95b6-983dc00171a3`
- **Tokens saved/use (proxy):** 444 · **Score delta (proxy):** +2

## 1.0.0 — major — 2026-06-27T12:00:00.000Z  [published]
- **Learned from:** CAP-P001 — seeded from community best practice (top-15 popular engineering skill, category `backend`)
- **Finding:** Design predictable, resource-oriented HTTP APIs with correct verbs, status codes, versioning, and consistent error envelopes.
- **Change:** Initial canonical guidance body, use-cases, and frontmatter for `skill/rest-api-design`.
- **Tokens saved/use:** 1744 · **Seed score:** transfer 66/novelty 71/importance 87
