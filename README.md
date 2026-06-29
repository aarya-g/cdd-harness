# cdd-harness

An operator who knows commercial due diligence, amplified. A Claude Code harness that runs the $0 educated-guess desk-screen a consultant would run *before* committing weeks of research, plus an interactive atlas of the decision framework behind it.

> Scope, honestly: this is the **desk layer**, not a full CDD engagement. Real commercial due diligence takes weeks because most of it is primary research (data rooms, management interviews, customer surveys) — no model one-shots that. This harness owns the fast kill-screen that decides what is *worth* researching. The intelligence is in the operator's command; the harness amplifies it.

## What this is

I reverse-engineered how commercial due-diligence and strategy consultants actually decide, then turned it into a system I can run solo. The result has two parts:

1. **The decision atlas** (`index.html`) — an interactive, citation-audited map of 108 consulting operators (frameworks from McKinsey, Porter, Kano, Van Westendorp, and others), each sorted by where a consultant reaches for it and whether it survives at small scale. Filterable by phase, domain, and verdict; deep-linkable per operator.
2. **The harness** — the Claude Code agent setup that operationalises the atlas: I own the requirements, the logic, and the quality gates; the agents execute against them.

## The framework

Every screen runs on a 6-phase spine:

`Diagnose` (is the problem real, acute, funded?) → `Size` (big enough to live on, small enough to own?) → `Price` (what will the acute buyer pay?) → `Position` (what one slot do we own?) → `Capture` (reach the buyer at zero ad spend?) → `Measure` (stay honest about what worked?)

Each operator gets one of five verdicts: **KEEP** (transfers as-is), **ADAPT** (keep the reasoning, drop the apparatus), **SWITCH** (discarded now, flips to leverage on a named trigger), **DISCARD** (sample- or spend-bound, no honest substitute), **FLAG** (proprietary or unverified, reconstruct the principle but never the hidden mechanics).

## How I build

I specify what gets built, how it should work, and what counts as done. The agents write the code against that spec, and I review and validate every output. Database design, data pipelines, agent orchestration, and the decision logic are mine; the execution is AI-augmented. This repo is the public, sanitized slice of a larger private system.

## Honesty boundaries

The atlas was citation-audited (40 of 46 source claims verified against primaries, zero fabricated). Operators that rest on proprietary or unverified mechanics are tagged FLAG and withhold the mechanics by design. No client, sourcing, financial, or private business data appears anywhere in this repo.

## Self-audit

This harness is graded by an independent third-party tool ([Dallionking/claude-harness-audit](https://github.com/Dallionking/claude-harness-audit), MIT), not self-scored.

<!-- AUDIT-REPORT: filled after the local audit run passes (plan step 4) -->

## Live atlas

<!-- ATLAS-URL: added after public deploy (plan step 6) -->
