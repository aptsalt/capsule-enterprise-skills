---
name: PCI Redaction
id: skill/pci-redaction
currentVersion: 1.2.0
scope: enterprise
adoptionPolicy: manual
optedIn: true
tokensSavedPerUse: 1500
useCases: [ "PAN/CVV scrubbing on prompt egress", "Capsule-writer redaction", "Tool-call argument scrubbing" ]
---

# PCI Redaction  `skill/pci-redaction@1.2.0`

Luhn-validated PAN/CVV scrubbing applied to prompts, tool arguments, and capsules before they leave the trust boundary.

## Use cases

- PAN/CVV scrubbing on prompt egress
- Capsule-writer redaction
- Tool-call argument scrubbing

## Capsule provenance (current version)

The current version `1.2.0` was promoted by the RL gate from capsule **CAP-1003**
(session `sess-2b77`, model `claude-opus-4-8`).

> **Finding:** Redact PAN/CVV independently at every trust boundary — capsule writer, prompt egress, and tool-call args — using a Luhn check to avoid false positives on long IDs.

## Token savings

Each reuse of this skill saves **1500 tokens** versus re-deriving the pattern
from a cold session (measured in the A/B harness).

## Pull this skill

```bash
capsule pull pci-redaction@1.2.0        # pin this exact version
capsule pull pci-redaction             # latest published
```
