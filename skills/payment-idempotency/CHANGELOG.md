# Changelog — skill/payment-idempotency

RL audit trail. Every version is a capsule finding the gate promoted into the
enterprise registry. Newest first. Versions follow semver (major/minor/patch).

## 2.0.0 — major — 2026-04-19T09:20:00Z  [published]
- **Learned from:** CAP-1006 (session `sess-3a55`, model `claude-sonnet-4-6`)
- **Finding:** Hashing the whole request body for dedup conflates payment intent with transport noise and blocks legitimate repeat payments.
- **Change:** Replaced request-hash dedup with a dedicated idempotency table.
- **Tokens saved/use:** 900 · **Score delta:** +11 · **Adopted by:** 3 agent(s)

