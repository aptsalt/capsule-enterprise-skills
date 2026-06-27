---
name: Test Automation
id: skill/test-automation
currentVersion: 1.0.0
scope: enterprise
adoptionPolicy: auto
optedIn: true
category: data/quality
popularity: "top-15"
description: Build a fast, reliable automated test suite shaped as a pyramid: many unit, fewer integration, few deterministic E2E.
tokensSavedPerUse: 1754
useCases: [ "Test pyramid and coverage strategy", "Deterministic, isolated tests", "CI gating and flake elimination" ]
---

# Test Automation  `skill/test-automation@1.0.0`

Build a fast, reliable automated test suite shaped as a pyramid: many unit, fewer integration, few deterministic E2E.

## Canonical guidance

Shape the suite as a pyramid: a broad base of fast, isolated unit tests, a thinner layer of integration tests for real boundaries (DB, queue, HTTP), and a few high-value end-to-end tests for critical user journeys. Keep tests deterministic and independent — control time, randomness, and network (fakes/containers), and never depend on test ordering or shared mutable state, so they can run in parallel. Follow Arrange-Act-Assert and assert on behavior, not implementation, so refactors don't break green tests. Gate merges on the suite in CI, treat any flaky test as a bug to quarantine and fix immediately, and track coverage of critical paths rather than chasing a vanity percent.

## Use cases

- Test pyramid and coverage strategy
- Deterministic, isolated tests
- CI gating and flake elimination

## Provenance (current version)

Version `1.0.0` was **seeded from community best practice** as one of the *top-15*
popular real-world engineering skills, then admitted to the enterprise registry under
capsule **CAP-P015** (category `data/quality`). Future versions follow the normal RL loop —
distilled from real Claude Code sessions via local Ollama, durable memory in Backboard.

> **Seed finding:** Build a fast, reliable automated test suite shaped as a pyramid: many unit, fewer integration, few deterministic E2E.

Seed transfer score: **51/100** · novelty **90** · importance **63**.
Briefing persisted in **Backboard** (thread `41840224-9cda-8703-a1df-a81b4e3e1a51`).

## Token savings

Each reuse of this skill saves **1754 tokens** versus re-deriving the pattern
from a cold session (measured proxy on the local model in the A/B harness).

## Pull this skill

```bash
capsule pull test-automation@1.0.0     # pin this exact version
capsule pull test-automation                          # latest published
```
