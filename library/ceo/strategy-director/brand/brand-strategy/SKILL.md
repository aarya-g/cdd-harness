---
name: brand-strategy
description: >-
  Set brand positioning before creative: the desire answered, POP/POD/POC statement and swap test, offer framing, CBBE equity, architecture, voice, naming, audit or rebrand, brand book. Triggers: brand strategy, positioning, brand voice, STP.
argument-hint: "buyer | audit | positioning | purpose | equity | architecture | voice | naming | book | full <brand-brief>"
allowed-tools:
  - Read
  - Write
  - Edit
  - Bash
  - Grep
  - Glob
---

# Brand Strategy — Positioning Before Creative

`buyer evidence → brand-strategy → positioning_brief.json → brand-creative-genai (owned by CREATIVE) → ads / blog / email`

Positioning is reverse-engineered from how buyers decide, never top-down from MBA theory. Every claim traces to buyer evidence; if a sub-skill can't trace its output, it is generating theory: flag and stop.

## Commands → sub-skills
`/brand-strategy <cmd> <brand>` loads `skills/brand-strategy-<cmd>/SKILL.md`. No command = `buyer`. `full` runs steps 0→8 in order, each consuming upstream output.

| Step | Cmd | Consumes | Produces |
|---|---|---|---|
| 0 | buyer | brief + VoC / sales corpus | `buyer_psychology.json` |
| 1 | audit | buyer | STP segments, health 0-100, rebrand verdict |
| 2 | purpose | buyer | purpose ladder, Golden Circle, Brand Key |
| 3 | positioning | buyer + audit + purpose | Kotler statement, POP/POD/POC, perceptual map |
| 4 | equity | positioning | CBBE target, Aaker pillars, equity gap |
| 5 | architecture | brief (skip if single-product) | Aaker type, migration |
| 6 | voice | buyer + positioning | NN/g tone, messaging house, voice chart |
| 7 | naming | positioning (new brand / sub-brand / rebrand only) | names, distinctive assets |
| 8 | book | all | brand book + `positioning_brief.json` |

## Decision questions → test → reference
| Question | Test | Reference |
|---|---|---|
| Q1. Which desire does the product answer? | Mass Material Desire *identified* from US/UK/CA/AU buyer evidence; emotional/aspirational *concluded* from it, never invented | desire-mapping D1–D2, D6 |
| Q2. Desire or benefit wording? | Desire is the market's word, benefit the product's; map features → benefits → desires | desire-mapping D3–D4 |
| Q3. What does the buyer decide on? | `primary_decision_driver` + `dominant_objection_archetype` from code-bound signal counts | buyer sub-skill · buyer-psychology §1–§2 |
| Q4. Is the POD distinctive? | Swap test: could it run for a named competitor? Yes = not distinctive (canon-only, in no reference) | positioning-frameworks §2 |
| Q5. Is the offer framed on value? | Value Equation: work time delay, effort and likelihood, not louder dream-outcome claims | sales-voices V1.1–V1.6 |
| Q6. Is each POC honest, the offer firm? | POC traces to a counted objection; guarantees and urgency real | sales-voices V1.7, V1.8, V1.10, V2 |
| Q7. Which voice on this surface? | DR leads material desire + proof; institutional carries emotional/aspirational; teach, don't pitch | desire-mapping D5 · sales-voices V3 |
| Q8. Is the number real? | Every number labelled SRC / INF / CANON with its reference § | the reference's label key |

**Reading rule (desire-mapping and sales-voices):** INF lines are inference, not source text. Each "B2B→DTC scope note" binds: don't apply a B2B finding past it. Transfer test (sales-voices V2.9): a no-salesperson, low-ticket DTC store sits on Rackham's small-sale side, so CTAs, guarantees and urgency may be firm but never false (real dates, real batches, payable guarantees).

## Binding rules
- `buyer_psychology.json` exists before any positioning. Buyer analysis is code-bound aggregation (`scripts/buyer_signal_extract.py`), not LLM narrative.
- PODs answer `primary_decision_driver`; POCs trace to real `objection_archetypes`; POPs are category table stakes; POP and POD don't overlap.
- Positioning statement fills all 5 slots: For [target] / who [need] / [brand] is the [frame] / that [POD] / because [RTB].
- `voice_dimensions` tuned to `decision_maker_archetype`; CBBE resonance maps to `trust_mechanisms_required`.
- Text evidence supports brand-stack, desire, objection, awareness stage and trust mechanism only. Day-in-life, media diet and spend allocation → `primary_research_gaps`, never invented.
- Every framework cites a verified source from the references; no invented author, book or study.
- Architecture is skipped for a single-product brand and never skipped for a multi-brand portfolio (errors compound for years).
- Persuasion copy lives in `marketing-execution-persuasion` (CREATIVE): link, don't re-teach Schwartz or Hormozi copy frameworks.

## Fails when
- Positioning is written before the buyer step: output is MBA theory, untraceable to buyers.
- A POD answers nothing buyers decide on, or a POC hides a real objection (honest parity beats pretended superiority).
- A buyer narrative is built from a text scrape, or urgency and scarcity are false.

## Health score (audit, `scripts/brand_audit_score.py`)
Operator rubric, 0-100: buyer grounding 25 · positioning clarity 25 (statement complete, POD distinct, POC honest) · equity strength 20 (CBBE level reached) · distinctiveness 15 (Ehrenberg-Bass assets owned vs category) · coherence 15 (Olins 4-vector: product / environment / communication / behaviour).
Bands: 90-100 Locked (hand to creative) · 75-89 Strong (tighten, then hand off) · 60-74 Working (iterate the weak pillar) · 40-59 Weak (rework from buyer step) · <40 Reset (restart from buyer evidence).

## References (`references/`, load on demand)
- `desire-mapping.md`: TSOR Product-Desire Mapping by decision (D1–D6, flags C/U). Which desire, which material desire to lead with, desire-vs-benefit wording, DR vs institutional voice per surface.
- `sales-voices.md`: Hormozi offers, SPIN, Challenger, closing, Sapp, with DTC scope notes and flags. Offer and value framing, objections → honest POCs, urgency and guarantees, what the brand teaches.
- `buyer-psychology.md`: summary layer of the buyer-decision frameworks with brand translation; canon-only items marked.
- `positioning-frameworks.md` (Kotler statement, POP/POD/POC, Trout & Ries, perceptual map) · `equity-models.md` (Keller CBBE, Aaker 4 pillars) · `brand-architecture.md` (Aaker spectrum, decision tree, migration) · `growth-science.md` (Ehrenberg-Bass, distinctive assets, CEPs, Binet & Field 60/40, ESOV) · `purpose-frameworks.md` (purpose ladder, Golden Circle, Brand Key, onion) · `voice-frameworks.md` (NN/g 4 dimensions, messaging house, voice chart) · `naming-frameworks.md` (types, method, matrix, screening) · `segmentation.md` (STP, JTBD, ICP) · `brand-book-template.md` (10 sections).

## Scripts
`scripts/buyer_signal_extract.py` (corpus export → signal counts) · `positioning_statement.py` (slots JSON → statement + validation) · `brand_audit_score.py` (assessment → scorecard) · `architecture_recommend.py` (portfolio → Aaker type).

## Handoff — `positioning_brief.json`
Emitted by `full` / `book`; ingested by `brand-creative-genai`'s `brand-creative-archetype` sub-skill. Carries a `buyer_psychology` block (objection archetype, decision driver, awareness stage, trust mechanisms, decision-maker archetype, research gaps), positioning statement, POP/POD, purpose, values, CBBE resonance target, voice dimensions, distinctive assets, optional archetype hint. Schema: `skills/brand-strategy-book/SKILL.md`.

## Scope
Owns positioning, equity, architecture, buyer grounding, purpose, voice, naming, brand book, strategy health. Not here (cross-link): awareness-stage copy → `marketing-execution-persuasion` · Cialdini / consumer psychology → `marketing-psychology` · Porter / market mapping → `competitive-landscape` · visual creative → `brand-creative-genai` · channel plans → `seo-plan`, `ads-plan`, `email-plan`, `blog-strategy` · logo / finished art → `canvas-design` · pricing → QUANT `pricing` (strategic pricing stance: STRATEGIST via mbb-strategic-frameworks).

## Verification (after every full run)
- [ ] `buyer_psychology.json` produced first; research gaps flagged, not fabricated
- [ ] Every POD traces to the decision driver, every POC to a real objection archetype
- [ ] Positioning statement has all 5 slots; swap test passed
- [ ] CBBE resonance maps to trust mechanisms; voice tuned to decision-maker archetype
- [ ] Every number labelled; no invented framework, author or study
- [ ] `positioning_brief.json` emitted and schema-complete
