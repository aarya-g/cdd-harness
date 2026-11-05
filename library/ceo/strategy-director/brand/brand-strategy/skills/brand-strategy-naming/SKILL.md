---
name: brand-strategy-naming
description: >
  Generate, score and screen brand names, and lock distinctive brand
  assets (colour, logo, tagline, sonic). Runs for a new brand, sub-brand
  or rebrand only. Use for "brand naming", "name ideas", "brand name",
  "naming options", "distinctive assets", `/brand-strategy naming`.
allowed-tools:
  - Read
  - Write
---

# Brand Strategy Naming — Name + Distinctive Assets

A name is hard to change later: evaluate it properly before locking. Runs only for a new brand, sub-brand or rebrand.

**Input:** `positioning.json` · `architecture.json` (naming convention, if multi-brand) · `purpose.json` (essence, tone).
**Process:** generate across naming types → shortlist → score → flag screening → lock distinctive assets → emit.

## Output — `naming.json`
```json
{
  "name_candidates": [{"name": "...", "type": "suggestive", "score": 0, "notes": "..."}],
  "recommended_name": "...",
  "recommendation_rationale": "...",
  "screening_required": ["trademark class search", "domain availability", "social handle check"],
  "distinctive_assets": {
    "color": "the ownable color / palette",
    "logo_direction": "wordmark / symbol / combination",
    "character": "mascot or spokes-character if any",
    "sonic": "audio signature if any",
    "tagline": "the locked tagline",
    "other": ["packaging shape, typeface, etc."]
  }
}
```

## Method (naming-frameworks §1–§3; canon-only, the reference cites no source)
1. Mine positioning, purpose, essence and the buyer's decision driver for root concepts. Name from desire: desire-mapping D1.4, D6.5.
2. Generate 20-40 raw candidates across types: descriptive (clear, hard to trademark or stretch) · suggestive (often the sweet spot) · abstract / invented (most ownable, costs more to fill with meaning) · founder · acronym (weak for a new brand) · metaphor · compound.
3. Cut to 8-12: drop the unpronounceable, generic, awkward or negative-association.
4. Score 1-5 each: distinctive · meaningful · memorable · pronounceable · spellable · stretchable · available · tone-fit. High meaning but failed pronounceability or availability = not usable.
5. Recommend the top 1-2 with explicit rationale.

Offer or bundle names (not the brand name) use Hormozi's MAGIC formula: sales-voices V1.11.

## Screening (naming-frameworks §4)
This step FLAGS screening; it never performs legal clearance or calls a name "available". List: trademark search in relevant classes and jurisdictions · `.com` + market TLDs · social handles · negative-meaning / mispronunciation check across target-market languages · existing-brand confusion in the category. Always recommend professional trademark clearance before final lock.

## Distinctive brand assets (Ehrenberg-Bass; growth-science §1, naming-frameworks §5)
Lock the non-name cues that let a buyer recognise the brand: colour (one ownable colour or palette, typically the strongest single asset; mandatory) · logo · character (optional, high recall) · sonic (optional) · tagline · typeface / packaging / layout device. Assets build by consistency over time; changing one resets the clock. Scope-fence: keep distinctive assets and availability, reject mass-penetration doctrine (BRAND doctrine, `../../../references/doctrine.md`). Asset choice is BRAND; visual execution is CREATIVE.

## Cross-Link
- Consumes `positioning.json`, `architecture.json`, `purpose.json`
- References: `references/naming-frameworks.md`, `references/growth-science.md`
- Name from desire: `../../references/desire-mapping.md` (D1.4, D6.5) · offer/bundle name: `../../references/sales-voices.md` (V1.11)
- Hands `naming.json` to `book`
- Visual execution of assets (logo render, etc.) is `canvas-design` / `brand-creative-genai`

## Verification
- [ ] Candidates generated across multiple naming types
- [ ] Shortlist scored on the full evaluation matrix
- [ ] Recommended name has explicit rationale
- [ ] Screening needs flagged, incl. negative-meaning check; no "available" claim made
- [ ] Distinctive assets locked (colour mandatory, others as fit)
