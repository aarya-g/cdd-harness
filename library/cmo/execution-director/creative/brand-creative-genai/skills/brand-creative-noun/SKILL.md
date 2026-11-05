---
name: brand-creative-noun
description: >
  Decompose the brand's look into the 5-slot noun matrix (Person, Place,
  Object, Animal, Activity), each slot chosen to reinforce the locked emotion
  and anchor, as noun_matrix.json for the prompt, photoshoot and metaphor
  steps. Use for "noun decomposition", "noun matrix", "Person Place Object
  Animal Activity", "aesthetic match", "P P O A A",
  `brand-creative-genai noun`.
allowed-tools:
  - Read
  - Write
---

# Brand Creative Noun — Person, Place, Object, Animal, Activity

Operator's core method (CANON): five noun slots can carry any brand emotion. Pick each slot to reinforce `mood_lock.json`.

**Reading rule:** platform pack `../../sources/platform-creative-2026-10/` (people, product in use) and research pack `../../sources/emotion-archetype-metaphor-2026-10/` (juxtaposition 13, composition 08b; lake `C-L2`); sourced lines collected in `../../references/noun-aesthetic-library.md` § Selection Rules. The page wins over the lake.

| Slot | Definition | Examples |
|---|---|---|
| Person | a human signal: clothing, body part, gesture, role | tuxedo cuff, weathered hand, linen-robed figure |
| Place | a location or set | minimal studio, oak cellar, brutalist atrium |
| Object | a prop or material | gold leaf, leather-bound book, brushed titanium |
| Animal | a creature carrying brand meaning | snow leopard, stag, white crane, orca |
| Activity | a core action | eating, pouring, sipping, tagging, jumping |

**Input:** `mood_lock.json` · `archetype_lock.json` (casting → Person, props → Object) · brand brief · optional operator overrides.
**Process:** match anchor + primary emotion to a row in `../../references/noun-aesthetic-library.md` → 5 candidates per slot → keep the strongest one (operator can swap) → engineer ≥2 tension pairs → register check → emit. Script: `python3 ../../scripts/noun_decompose.py --category <key> --auto` (`--list` for keys).

## Output — `noun_matrix.json`
```json
{
  "person": "silk-draped hand, no logo, dust-coated knuckles",
  "place": "white seamless studio, golden hour rake from camera left",
  "object": "gold leaf scoop, melted edge, cracked enamel",
  "animal": "snow leopard, half-lit, eyes closed",
  "activity": "slow eating, mid-bite, breath held",
  "tension_pairs": [
    "snow leopard + eating (predator stillness vs ritual)",
    "gold leaf + ice cream (mythic + mundane)"
  ],
  "register_match": ["luxury", "longing", "awe"]
}
```

## Decision rules
- **Reinforce, don't decorate.** If you can't say in one line why this noun beats the alternative, the slot is weak.
- **Tension comes from juxtaposition across slots.** Snow leopard + eating works as a quiet contradiction (apex predator in repose, a mundane act elevated). Engineer at least 2 tension pairs.
- **Register holds across all 5 slots.** A tuxedo-cuff Person in a freight-yard Place breaks the brand.
- **The animal is often the strongest symbol.** Lion, eagle and wolf signal generic brands. Pick rare-but-readable: snow leopard, white crane, stag, orca, hummingbird, manta ray, owl. (CANON; animal meanings are NOT IN SOURCE.)
- **Person and Activity carry the sale (SRC).** "Images with a visible human presence consistently outperform other assets … feature faces or people actively engaging with your product" [platform 14]; Shorts: "show talent using the product" [13a]; Meta Stories: awareness objective → "focus your ad on people", sales objective → "focus on products" [01c]. INF: a sales-objective frame keeps the Person but makes the Activity the product in use.
- **Build tension side by side first (SRC + INF).** Juxtaposed images drew the most elaboration and fused images were the hardest to understand [13, print ads, 185 students]; a break in a repeated pattern makes the focal point [08b]. INF: pair two slots in one frame before fusing two nouns into one object.
- **ECOM:** the Object slot is the real product (or its material) the customer receives; GenAI may stage it but never redesign it.

## Weak slot → swap
- Person too generic → a body-part close-up (hand, jaw, nape) or one garment detail (cuff, seam, lapel)
- Place too literal → negative space (empty studio, fog, void)
- Object too obvious → the material rather than the thing (the gold leaf, not the gold ring)
- Animal too common → rare-but-readable; check the Magritte / Dalí bestiary for surreal leverage
- Activity too static → a half-second slice (mid-bite, mid-pour, mid-step)

## Cross-link
- Consumes `mood_lock.json`; hands `noun_matrix.json` to `brand-creative-prompt`, `brand-creative-photoshoot`, `brand-creative-metaphor`
- 18 category matrices, sample rows and the operator's ice-cream example: `../../references/noun-aesthetic-library.md`

## Verification
- [ ] All 5 slots filled, no neutrals
- [ ] ≥2 tension pairs documented
- [ ] Register check passed (all slots in one anchor)
- [ ] Animal is rare-but-readable, not the first 5 of the category
- [ ] Each slot has a one-line "why"
- [ ] Person and Activity show a person using the real product unless BRAND's brief says otherwise
