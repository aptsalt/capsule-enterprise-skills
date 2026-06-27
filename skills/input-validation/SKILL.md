---
name: Input Validation
id: skill/input-validation
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
category: data/quality
popularity: "top-15"
description: Validate and normalize all external input at the boundary with allowlist schemas, rejecting before it reaches logic.
tokensSavedPerUse: 859
useCases: [ "Schema validation at the boundary", "Allowlist over denylist rules", "Parse-don't-validate normalization" ]
---

# Input Validation  `skill/input-validation@1.0.0`

Validate and normalize all external input at the boundary with allowlist schemas, rejecting before it reaches logic.

## Canonical guidance

Validate every external input at the trust boundary before it touches business logic, and treat all client input as hostile. Prefer parse-don't-validate: convert raw input into a typed, constrained model (e.g. a Zod/Pydantic schema) so downstream code receives only well-formed data. Use allowlists (what is permitted) over denylists (what is blocked) — enumerate valid enums, ranges, lengths, and formats. Normalize/canonicalize (trim, Unicode NFC, case) before comparing to avoid bypass. Fail closed with a precise 4xx and field-level errors, and keep validation separate from authorization. Never rely on client-side validation as a security control.

## Use cases

- Schema validation at the boundary
- Allowlist over denylist rules
- Parse-don't-validate normalization

## Provenance (current version)

Version `1.0.0` was **seeded from community best practice** as one of the *top-15*
popular real-world engineering skills, then admitted to the enterprise registry under
capsule **CAP-P012** (category `data/quality`). Future versions follow the normal RL loop —
distilled from real Claude Code sessions via local Ollama, durable memory in Backboard.

> **Seed finding:** Validate and normalize all external input at the boundary with allowlist schemas, rejecting before it reaches logic.

Seed transfer score: **86/100** · novelty **91** · importance **68**.
Briefing persisted in **Backboard** (thread `1a63c642-eb63-ce94-24dd-6a9f2f2f45e2`).

## Token savings

Each reuse of this skill saves **859 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull input-validation@1.0.0     # pin this exact version
capsule pull input-validation                          # latest published
```
