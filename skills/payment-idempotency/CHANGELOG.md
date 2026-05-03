# Changelog — skill/payment-idempotency

RL audit trail. Every version is a capsule finding the gate promoted into the
enterprise registry. Newest first. Versions follow semver (major/minor/patch).

## 2.0.0 — major — 2026-04-19T09:20:00Z  [published]
- **Learned from:** CAP-1006 (session `sess-3a55`, model `claude-sonnet-4-6`)
- **Finding:** Hashing the whole request body for dedup conflates payment intent with transport noise and blocks legitimate repeat payments.
- **Change:** Replaced request-hash dedup with a dedicated idempotency table.
- **Tokens saved/use:** 900 · **Score delta:** +11 · **Adopted by:** 3 agent(s)

## 2.1.0 — minor — 2026-05-03T13:13:00Z  [published]
- **Learned from:** CAP-1001 (session `sess-4af2`, model `claude-opus-4-8`)
- **Finding:** Persist the idempotency key inside the same ledger transaction and scope it to (debtor, amount, currency) so retries are safe without ever blocking a legitimate repeat payment.
- **Change:** Scope keys to (debtor, amount, currency); persist within the ledger transaction; 24h TTL.
- **Tokens saved/use:** 1800 · **Score delta:** +16 · **Adopted by:** 5 agent(s)

