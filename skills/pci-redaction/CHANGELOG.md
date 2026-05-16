# Changelog — skill/pci-redaction

RL audit trail. Every version is a capsule finding the gate promoted into the
enterprise registry. Newest first. Versions follow semver (major/minor/patch).

## 1.0.0 — major — 2026-05-16T10:05:00Z  [published]
- **Learned from:** CAP-1003 (session `sess-2b77`, model `claude-opus-4-8`)
- **Finding:** Redact PAN/CVV independently at every trust boundary — capsule writer, prompt egress, and tool-call args — using a Luhn check to avoid false positives on long IDs.
- **Change:** Initial PAN regex scrubber on prompt egress.
- **Tokens saved/use:** 600 · **Score delta:** +8 · **Adopted by:** 2 agent(s)

