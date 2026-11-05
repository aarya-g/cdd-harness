---
name: brand-strategy-equity
description: >
  Model brand equity: Keller CBBE pyramid (current vs target), Aaker 4
  pillars scored 1-10, resonance mapped to buyer trust mechanisms, and
  the one lever for the biggest gap. Use for "brand equity", "CBBE",
  "Keller pyramid", "brand resonance", "Aaker equity",
  `/brand-strategy equity`.
allowed-tools:
  - Read
  - Write
  - Bash
---

# Brand Strategy Equity — The Value of the Brand Name

Equity = the premium and loyalty a buyer gives because of the name alone. Model current and target state.
**Sources:** pack `../../sources/brand-research-methods-2026-10/` (`_urls.md`; page 01 = Keller, MSI Report 01-107, 2001, with its Appendix of candidate measures; page 02 = Aaker, "What Is Brand Equity?", Prophet 2013; lake L1) via `../../references/equity-models.md`. Labels: SRC · INF · CANON. The page wins over the lake.

**Input:** `positioning.json` + `buyer_psychology.json`; optional metrics (awareness %, NPS, repeat rate).
**Process:** CBBE 6 blocks (current + target) → Aaker 4 pillars → resonance ↔ trust map → equity gap → emit.

## Output — `equity.json`
```json
{
  "cbbe_pyramid": {
    "salience": {"current": "...", "target": "..."},
    "performance": {"current": "...", "target": "..."},
    "imagery": {"current": "...", "target": "..."},
    "judgments": {"current": "...", "target": "..."},
    "feelings": {"current": "...", "target": "..."},
    "resonance": {"current": "...", "target": "..."}
  },
  "aaker_pillars": {
    "awareness": {"score_1_10": 0, "note": "..."},
    "perceived_quality": {"score_1_10": 0, "note": "..."},
    "associations": {"score_1_10": 0, "note": "..."},
    "loyalty": {"score_1_10": 0, "note": "..."}
  },
  "resonance_trust_map": "how resonance is built from buyer trust mechanisms",
  "equity_gap": "the biggest current-to-target gap and the lever to close it"
}
```

## Rules
- **CBBE** (Keller 2001; equity-models §1): salience → performance + imagery → judgments + feelings → resonance. Each level holds before the next; resonance is earned by building every level below, never bought. SRC 01 p12: equity "will only occur if the right brand-building blocks are in place". Sub-dimensions per block: equity-models §1 SRC detail (e.g. resonance = behavioral loyalty, attitudinal attachment, sense of community, active engagement, 01 p20).
- **Current state from evidence:** fill each block's "current" from the Keller Appendix items (01, printed p27–30) answered by buyers or reviews; with no respondents, say so and cap the block at INF.
- **Resonance ↔ trust** (equity-models §3, INF; block names SRC 01): resonance is where buyer trust mechanisms cash out. If Step 0 found buyers need third-party validation + risk reversal, the resonance plan shows how the brand delivers them. Map: social proof → judgments + resonance · third-party validation → judgments · risk reversal → judgments + feelings (security) · demo / trial → performance · founder transparency → feelings + judgments.
- **Aaker pillars** (Aaker 1991/1996; equity-models §2): score each 1-10 now (the scale is INF; SRC 02 names the "four dimensions—brand loyalty, brand awareness, brand associations, and perceived quality" but no scoring). CONFLICT (02): loyalty inside equity "was and is still controversial"; Keller puts loyalty at resonance, the outcome. Never count Aaker loyalty and Keller resonance as two gains. Awareness ← distinctive assets, consistent presence, ESOV · perceived quality ← proof, craft cues · associations ← owned vocabulary, consistent imagery · loyalty ← resonance, ritual, community, switching cost.
- **Equity gap** (equity-models §4, INF): the single biggest current-to-target gap and ONE lever. One focused lever beats a scattershot plan.

## Cross-Link
- Consumes `positioning.json`, `buyer_psychology.json`
- Reference: `references/equity-models.md`; distinctive assets and CEPs: `references/growth-science.md`
- Hands `equity.json` to `book` and the `positioning_brief.json` emit step

## Verification
- [ ] CBBE pyramid: all 6 blocks, current + target
- [ ] Aaker 4 pillars scored 1-10 with notes
- [ ] Resonance block maps to specific buyer trust mechanisms
- [ ] Equity gap identified with a single named lever
- [ ] No claim that resonance can skip the levels below it
- [ ] Each "current" cites a Keller Appendix item or buyer evidence, or is marked INF

