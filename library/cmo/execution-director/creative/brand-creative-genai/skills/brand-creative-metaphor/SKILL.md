---
name: brand-creative-metaphor
description: >
  Set the three metaphor dials (surreal, symbolism, hyper-real, 1-10 each)
  that turn a literal product shot into a scroll-stopping ad, inside the
  category caps, as metaphor_layers.json for the prompt step. Use for
  "surreal ad", "symbolic ad", "metaphor ad", "10x emotion", "dial surreal",
  "metaphorical advertising", "metaphor stack", `brand-creative-genai metaphor`.
allowed-tools:
  - Read
  - Write
---

# Brand Creative Metaphor — Surreal × Symbolism × Hyper-Real

Operator thesis: creative should feel 10x surreal, 10x symbolic and 10x hyper-real. This sub-skill turns that into three dials per creative. The method is CANON; default dials and caps are operator settings (UNVERIFIED).

**Reading rule:** research pack `../../sources/emotion-archetype-metaphor-2026-10/` (visual metaphor 12–13, deep metaphors and ZMET 09–11, lake `C-L2`); measured effects in `../../references/metaphor-frameworks.md` §8. The page wins over the lake.

**Why a dial at all (SRC [12], 43 adults, lab, print ads):** metaphor ads beat the same ads without one on attitude to the ad (4.5 vs 3.4) and purchase intention (4.0 vs 3.7); positive reactions rise with complexity "which ends where complexity outweighs comprehension". The dial positions and caps below are not sourced.

## The three dials
| Dial | 1 = | 10 = | Draw from |
|---|---|---|---|
| Surreal | photo-real product shot | gravity reverses, animals appear that shouldn't, objects float | canon artists only: Magritte (safest: one floating object on a still scene), Dalí (6-9), Escher (tech, architecture), Kusama (fashion). `../../references/metaphor-frameworks.md` §4, §6 |
| Symbolism | props decorate | every object, colour, animal, gesture is loaded | Lakoff conceptual metaphor ("luxury is slowness"), Barthes denotation vs connotation (gold leaf denotes gold, connotes myth), McCracken meaning transfer, Zaltman deep metaphors (SRC [11]: transformation, balance, journey, connection, container; "two or three" are relevant to any topic). §1-3, §7, §8 |
| Hyper-real | generic stock photo | every pore, dust mote, fibre, melt visible | lens (anamorphic 85mm, 100mm macro, 50mm), f/1.4-2.8, light (hard rake / soft wrap / single source / window), film stock (Kodak 250D warm, 500T cool, Fuji 400H pastel, Cinestill 800T neon leak), texture, grain, grade. `../../references/cinematography.md` |

The symbolism metaphor comes from BRAND's positioning (POD, desire), not from the prompt. The IS / IS NOT visual codes come from `archetype_lock.json` (on / off codes).

**Input:** `mood_lock.json` · `noun_matrix.json` · `archetype_lock.json` · operator dial overrides (or category defaults).
**Process:** category defaults (table) → operator override → one text snippet per layer for the prompt → check caps and combined sum → emit.

## Output — `metaphor_layers.json`
```json
{
  "surreal_dial": 4,
  "surreal_snippet": "snow leopard's gaze is closed in serene repose, gold drip falls in slow motion against gravity for a single beat",
  "surreal_canon_refs": ["Magritte stillness", "Kusama dot rhythm muted"],
  "symbolism_dial": 9,
  "symbolism_snippet": "gold leaf = myth and ritual, snow leopard = apex rarity, slow eating = ritual luxury",
  "symbolism_frameworks": ["Lakoff: luxury is slowness", "Barthes: gold connotes myth", "McCracken: rarity transferred from leopard to product"],
  "hyper_real_dial": 9,
  "hyper_real_snippet": "anamorphic 85mm at f/1.4, Kodak 250D, soft golden hour rake, skin pores, fabric weave, drip surface tension, dust motes in beam",
  "register_check": "PASS — luxury aspirational with controlled surreal"
}
```

## Category default dials
| Category | Surreal | Symbolism | Hyper-real |
|---|---|---|---|
| Luxury | 4-6 | 8-10 | 8-10 |
| Heritage | 2-4 | 9-10 | 9-10 |
| Premium | 3-5 | 7-9 | 9-10 |
| Wellness | 3-5 | 7-9 | 6-8 |
| Tech | 5-7 | 5-7 | 8-10 |
| Youth | 6-8 | 5-7 | 5-7 |
| Edgy | 7-9 | 6-8 | 7-9 |
| Minimalist | 2-4 | 6-8 | 8-10 |
| Maximalist | 7-9 | 8-10 | 6-8 |
| Fragrance | 6-8 | 9-10 | 7-9 |
| Automotive luxury | 4-6 | 8-10 | 9-10 |
| Food premium | 3-5 | 7-9 | 9-10 |

## Combo rules
- All three at 10 = eye fatigue: cap the combined dials at 27/30.
- Surreal <3 with symbolism <5 = generic stock: combined minimum 8/30.
- Hard caps: luxury surreal 6 (above reads absurd) · tech symbolism 7 (above reads esoteric) · wellness surreal 5 (above reads psychedelic). Tech CONFLICT: see `../../references/audit-rubric.md` §2.3.
- ECOM product-aware and most-aware ads: keep surreal low so the real product reads.
- **Comprehension cap (SRC [12], [13]):** the hardest-to-read structure lost in both studies (replacement in [12]; fusion, "more difficult to comprehend than either juxtaposition or replacement", in [13], 185 students). CONFLICT: fusion was the most liked in [12] and the least liked in [13]. INF: if a test viewer can't say the metaphor in one sentence, drop the surreal dial 2 or move from fusion to side-by-side juxtaposition, or hand `brand-creative-copy` a headline that names the link.
- Never cite Zaltman's "95 percent of purchase decision making takes place in the subconscious mind" as data: it is a Q&A assertion [09].

## Moves and symbols
Brand-safe surreal moves, ranked by risk (floating object, reflection mismatch, scale inversion, gravity reverse, colour migration, time slice, animal in human space, empty inhabited, material swap, repetition rhythm and more): metaphor-frameworks §6. Cross-culture symbol library with connotations and use-for categories: §7 and the bottom of that file.

## Cross-link
- Consumes `mood_lock.json`, `noun_matrix.json`; hands `metaphor_layers.json` to `brand-creative-prompt`
- Canon artists are verified historical figures: never extend the list with fictional or unverified names

## Verification
- [ ] All 3 dials set 1-10; combined sum within 8-27 and category caps
- [ ] Surreal snippet references a canon artist
- [ ] Symbolism snippet names a framework (Lakoff / Barthes / McCracken / a Zaltman deep metaphor) and traces to BRAND's positioning
- [ ] Comprehension check: one test viewer states the metaphor in one sentence, or the dial steps down
- [ ] Hyper-real snippet specifies lens + light + texture + grade
- [ ] Register check confirms category fit
