---
name: brand-strategy-book
description: >
  Compile all upstream brand-strategy outputs into the brand book with a
  governance section, and emit positioning_brief.json for CREATIVE. Use
  for "brand book", "brand guidelines", "brand bible", "brand
  governance", "compile brand strategy", `/brand-strategy book`.
allowed-tools:
  - Read
  - Write
---

# Brand Strategy Book — The Governance Document

Compiles upstream outputs into the reference everyone uses. Invents nothing.
**Sources:** pack `../../sources/brand-research-methods-2026-10/` (`_urls.md`; page 07 = University of Melbourne Branding Policy, page 08 = University of Bath Brand Compliance policy; lake L2) via `../../references/brand-book-template.md` §9. Institutional policies, not DTC books: they back the governance mechanics only. The 10 sections are INF (house structure).

**Input:** `buyer_psychology.json` · `brand_audit.json` · `positioning.json` · `purpose.json` · `equity.json` · `architecture.json` (if multi-brand) · `voice.json` · `naming.json` (if run).
**Output:** `brand_book.md` (10 sections) + `positioning_brief.json`.

## Brand book — 10 sections (`references/brand-book-template.md`)
1. Brand at a glance (essence, one-line positioning, archetype hint; one page) · 2. Buyer foundation (leads on purpose: every later section is justified by it) · 3. Purpose · 4. Positioning · 5. Equity model · 6. Architecture (omit if single-product) · 7. Verbal identity · 8. Naming + distinctive assets (omit if already named) · 9. Governance · 10. Handoff.

## Handoff — `positioning_brief.json`
Connects `brand-strategy` to `brand-creative-genai` (owned by CREATIVE); its `brand-creative-archetype` sub-skill ingests it directly. Every field comes from an upstream JSON.
```json
{
  "brand_name": "...",
  "category": "...",
  "target_segment": "...",
  "jtbd": "...",
  "buyer_psychology": {
    "dominant_objection_archetype": "...",
    "primary_decision_driver": "...",
    "awareness_stage": "...",
    "trust_mechanisms_required": ["..."],
    "decision_maker_archetype": "...",
    "primary_research_gaps": ["..."]
  },
  "positioning_statement": "...",
  "points_of_difference": ["..."],
  "points_of_parity": ["..."],
  "brand_purpose": "...",
  "values": ["..."],
  "cbbe_target_resonance": "...",
  "voice_dimensions": {"formal_casual": 0, "serious_funny": 0, "respectful_irreverent": 0, "matter-of-fact_enthusiastic": 0},
  "distinctive_assets": ["color", "logo", "sonic", "character", "tagline"],
  "archetype_hint": "optional Jung archetype if strategy implies one"
}
```

## Governance — fixed vs flexible
| Fixed (sign-off required) | Flexible (team discretion) |
|---|---|
| Positioning statement | Campaign concepts |
| Purpose + values | Seasonal creative |
| Core message | Channel-specific copy |
| Distinctive assets (colour, logo) | Photography selection |
| Brand architecture | Promotional offers |

Also state who approves changes and the review cadence (e.g. annual brand-health audit). A brand book without governance gets ignored within a year (INF).
**SRC backing:** fixed end: "Official brand assets, including logos and visual identity elements, must not be altered or recreated" (08 §4.7); flexible end: routine activity "in accordance with approved ... brand guidelines" needs no steering-group approval (08 §4.12). One owner reviews and updates the guidelines, approves variances and third-party use, and acts on breaches (07 §4.4); a new sub-brand or identity needs approval and a business case first (08 §4.9–§4.10); keep an approvals register and an exceptions register (07 §5.8; 08 §2.5). Cadence CONFLICT: about 2 years (07: approved 2023-06-06, review 2025-06-30) vs 3 years (08: 2026-09-21 → 2029-09-21); "annual" is ours (INF). Solo store: the operator is the approver (INF).

## Missing inputs
Optional input missing (e.g. `naming.json` for an already-named brand) → mark the section "not in scope this run", never fabricate. Required input missing (`buyer_psychology.json`, `positioning.json`) → stop and flag; the book can't be built without the foundation.

## Cross-Link
- Consumes ALL upstream sub-skill JSONs
- Reference: `references/brand-book-template.md`
- Emits `positioning_brief.json` → `brand-creative-genai`

## Verification
- [ ] All available upstream JSONs compiled; 10 sections present or flagged out of scope, not faked
- [ ] Governance states fixed vs flexible, approver and cadence
- [ ] `positioning_brief.json` emitted and schema-complete
- [ ] Required inputs (buyer, positioning) present, else stopped + flagged

