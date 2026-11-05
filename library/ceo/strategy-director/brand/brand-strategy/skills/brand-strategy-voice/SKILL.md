---
name: brand-strategy-voice
description: >
  Set brand voice: four NN/g tone sliders tuned to the buyer's decision
  style, messaging house (core message, pillars, proof), voice chart,
  vocabulary. Use for "brand voice", "tone of voice", "messaging
  architecture", "voice chart", "how should the brand sound",
  `/brand-strategy voice`.
allowed-tools:
  - Read
  - Write
---

# Brand Strategy Voice — How the Brand Sounds

Consistent enough to be recognised, tuned to how the target buyer wants to be spoken to.

**Input:** `buyer_psychology.json` · `positioning.json` · `purpose.json`.
**Process:** set the 4 tone sliders → messaging house → voice chart (do / don't) → vocabulary → emit.

## Output — `voice.json`
```json
{
  "tone_dimensions": {"formal_casual": 0, "serious_funny": 0, "respectful_irreverent": 0, "matter-of-fact_enthusiastic": 0},
  "tone_rationale": "why these settings, tied to decision-maker archetype",
  "messaging_architecture": {
    "core_message": "the one thing — derived from positioning POD",
    "pillars": [{"pillar": "...", "proof_points": ["..."]}]
  },
  "voice_chart": [{"principle": "...", "we_do": "...", "we_dont": "..."}],
  "vocabulary": {"use": ["..."], "avoid": ["..."]}
}
```

## Tone sliders (NN/g 4 dimensions; voice-frameworks §1)
Set each from -10 to +10: formal ↔ casual · serious ↔ funny · respectful ↔ irreverent · matter-of-fact ↔ enthusiastic. Voice stays fixed; tone may shift slightly by context.

## Tune to the buyer (voice-frameworks §2)
Set the voice tilt from the buyer's decision-maker archetype or driver in `buyer_psychology.json`, using the table in [voice-frameworks](../../references/voice-frameworks.md) §2 (its one home).

## Surface and teaching voice
- **DR vs institutional:** direct-response surfaces lead the material desire + proof; institutional surfaces carry emotional / aspirational desire (desire-mapping D5).
- **Teaching voice:** what the brand teaches to reframe how the buyer sees the problem and the cost of the status quo (sales-voices V3; its B2B→DTC scope notes bind).

## Messaging house (voice-frameworks §3)
Core message = one sentence from the positioning POD → 3-4 defensible pillars → concrete proof points under each (map to RTB). Everything ladders to a pillar; every pillar ladders to the core message.

## Voice chart and vocabulary (voice-frameworks §4–§5)
5-8 do / don't rows, e.g. plain over clever: "Ships in 2 days" not "Logistics excellence delivered"; confident, not loud: "It works." not "AMAZING!!! Best ever!!!". Vocabulary: **use** = words the brand owns and repeats; **avoid** = words that fight the positioning ("cheap" for premium, "luxury" for accessible).

## Cross-Link
- Consumes `buyer_psychology.json`, `positioning.json`, `purpose.json`
- Reference: `references/voice-frameworks.md`
- DR vs institutional voice: `../../references/desire-mapping.md` (D5) · teaching voice: `../../references/sales-voices.md` (V3)
- Hands `voice.json` to `book` and `positioning_brief.json`
- Long-form copy execution lives in `copywriting` + `marketing-execution-persuasion`

## Verification
- [ ] All 4 tone dimensions set with values; rationale ties to decision-maker archetype
- [ ] Messaging house has core message + 3-4 pillars + proof points; core message derives from the POD
- [ ] Voice chart has 5-8 do/don't rows
- [ ] Vocabulary use + avoid lists filled
