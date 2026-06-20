# Changelog — skill/sca-challenge

RL audit trail. Every version is a capsule finding the gate promoted into the
enterprise registry. Newest first. Versions follow semver (major/minor/patch).

## 1.1.0 — minor — 2026-06-20  [proposed · awaiting human adoption]
- **Learned from:** CAP-1008 (session `sess-8b14`, model `claude-opus-4-8`)
- **Finding:** A single WebAuthn passkey gesture can satisfy SCA inherence and possession together, but platform-specific attestation keeps an OTP fallback mandatory.
- **Change:** Proposed: WebAuthn passkey device-binding to replace SMS OTP. Not yet promoted to master — manual adoptionPolicy, awaiting compliance sign-off.
- **Tokens saved/use:** 2600 (projected) · **Score delta:** +9 · **Adopted by:** 0 agent(s)

## 1.0.0 — major — 2026-05-29T11:15:00Z  [published]
- **Learned from:** CAP-1005 (session `sess-1e08`, model `claude-opus-4-8`)
- **Finding:** Compute SCA step-up server-side from a risk score and treat the challenge token as a single-use capability bound to one payment intent.
- **Change:** Server-evaluated challenge state; single-use tokens bound to the payment intent.
- **Tokens saved/use:** 3200 · **Score delta:** +14 · **Adopted by:** 3 agent(s)

