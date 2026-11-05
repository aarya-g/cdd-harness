---
name: brand-strategy-positioning
description: >
  Write the positioning statement (For X who Y, brand is the Z that POD
  because RTB), POP/POD/POC and a perceptual map; PODs answer the
  decision driver, POCs real objections. Use for "positioning statement",
  "POD", "POP POD POC", "swap test", "perceptual map",
  `/brand-strategy positioning`.
allowed-tools:
  - Read
  - Write
  - Bash
---

# Brand Strategy Positioning — The Statement

The single sentence the whole brand is built to prove.

**Input:** `buyer_psychology.json` · `brand_audit.json` (target segment) · purpose ladder (pipeline run) · competitor set.
**Process:** draft the 5-slot statement → POP / POD / POC → perceptual map → validate with `scripts/positioning_statement.py` → emit.

## Output — `positioning.json`
```json
{
  "positioning_statement": "For [target] who [need], [brand] is the [frame of reference] that [point of difference], because [reason to believe].",
  "slots": {"target": "...", "need": "...", "frame_of_reference": "...", "point_of_difference": "...", "reason_to_believe": "..."},
  "points_of_parity": ["table-stakes the brand must match"],
  "points_of_difference": ["what only this brand offers"],
  "points_of_contention": ["where the brand deliberately picks a fight"],
  "perceptual_map": {"x_axis": "...", "y_axis": "...", "brand_position": "...", "competitor_positions": {}}
}
```

## Slot rules (Kotler / Keller; positioning-frameworks §1)
| Slot | Rule |
|---|---|
| Target | the segment from `brand_audit.json`, never "everyone" |
| Need | the buyer's motivating problem from `buyer_psychology.json` |
| Frame of reference | the category the buyer files the brand in (wrong frame = wrong comparison set) |
| Point of difference | what only this brand credibly offers; MUST answer `primary_decision_driver` |
| Reason to believe | a proof, not an adjective; maps to `trust_mechanisms_required` |

## POP / POD / POC rules (Keller; positioning-frameworks §2)
- **POP** = category table stakes. If a claimed difference is table stakes, it's a POP; POP and POD never overlap.
- **POD** = desirable (answers the decision driver), deliverable (provable), differentiating (not shared). A difference nobody decides on is wasted.
- **POC** = an honest stance built from a real objection archetype ("too expensive" → "we won't race to the bottom; here's why cheap costs more"). Honest, never spin. Guarantees and urgency behind it are firm, never false (sales-voices V1.7, V1.8, V1.10).
- **Swap test:** could the statement or any POD run for a named competitor? If yes, it isn't distinctive (canon-only test, no reference).

## Perceptual map
Axes are buyer-decision dimensions from `buyer_psychology.json`, not reflex price / quality. The brand should hold a defensible, uncontested position; an empty quadrant is only an opportunity if buyers value it (positioning-frameworks §4).

## Validation — `positioning_statement.py`
Checks: 5 slots filled · target specific (not "everyone" / "anyone") · POD present and non-generic · RTB concrete · POP and POD lists don't overlap.

## Cross-Link
- Consumes `buyer_psychology.json`, `brand_audit.json`, purpose ladder
- Reference: `references/positioning-frameworks.md`
- Desire evidence: `../../references/desire-mapping.md` (D1–D4) · offer, guarantee and objection→POC voice: `../../references/sales-voices.md` (V1–V2)
- Script: `scripts/positioning_statement.py`
- Hands `positioning.json` to `equity`, `voice`, `naming`, `book`
- Awareness-stage copy execution lives in `marketing-execution-persuasion`

## Verification
- [ ] All 5 Kotler slots filled
- [ ] Every POD answers the buyer's primary decision driver; swap test passed
- [ ] Every POC traces to a real objection archetype, honest not spin
- [ ] POP and POD do not overlap
- [ ] Perceptual map axes are buyer-decision axes, not reflex price/quality
- [ ] `positioning_statement.py` validation passes
