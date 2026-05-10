# Changelog — skill/iso20022-mapper

RL audit trail. Every version is a capsule finding the gate promoted into the
enterprise registry. Newest first. Versions follow semver (major/minor/patch).

## 1.2.0 — minor — 2026-05-01T11:42:00Z  [published]
- **Learned from:** CAP-1007 (session `sess-6f29`, model `claude-sonnet-4-6`)
- **Finding:** A locally-pinned ISO 20022 XSD silently drifts out of date, so CI must validate against the network-published schema.
- **Change:** Pin mapper to the network-published XSD in CI; EUR/USD coverage.
- **Tokens saved/use:** 2100 · **Score delta:** +9 · **Adopted by:** 2 agent(s)

## 1.3.0 — minor — 2026-05-10T15:08:00Z  [published]
- **Learned from:** CAP-1002 (session `sess-9c10`, model `claude-sonnet-4-6`)
- **Finding:** Currency fraction digits are a per-currency ISO 4217 property, so amount scaling must come from an exponent table rather than a hardcoded /100.
- **Change:** ISO 4217 exponent table for per-currency fraction digits; JPY/BHD support.
- **Tokens saved/use:** 2400 · **Score delta:** +13 · **Adopted by:** 4 agent(s)

