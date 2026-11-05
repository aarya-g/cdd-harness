---
name: brand-creative-archetype
description: >
  Express BRAND's chosen archetype and positioning visually: palette, casting,
  composition, props, light, and the on / off codes every frame must hold.
  Reads positioning_brief.json and never picks the archetype. Use for
  "archetype visuals", "express the archetype", "visual identity from the
  brief", "casting brief", "what should the brand look like",
  `brand-creative-genai archetype`.
allowed-tools:
  - Read
  - Write
---

# Brand Creative Archetype — BRAND's Archetype, Made Visible

BRAND decides the archetype; this sub-skill decides what it looks like. Choosing or scoring one (Jung match, Aaker pillars, Holt myth, Olins vectors, semiotic square) is BRAND's work in `brand-strategy` (`../../../../../../ceo/strategy-director/brand/brand-strategy/SKILL.md`). To decode BRAND's choice, read `../../references/archetypes.md`.

**Reading rule:** research pack `../../sources/emotion-archetype-metaphor-2026-10/` (Carol Pearson's own pages 06a–07, lake `C-L2`; the book itself is not open) and platform pack `../../sources/platform-creative-2026-10/` (casting). The page wins over the lake.

**Input:** `positioning_brief.json` from BRAND: `archetype_hint`, positioning statement, POD, values, voice dimensions, distinctive assets, `buyer_psychology` (awareness stage, decision driver).
**No brief or no `archetype_hint`:** stop and ask BRAND to run `brand-strategy`, or take an archetype the operator states as BRAND's call. Never guess one from a loose brief.
**Process:** read the brief → look up the archetype row below → take BRAND's colours from the brief's distinctive assets; only if BRAND set none, propose a palette from `../../references/color-systems.md` §2 by category and price tier, marked for BRAND's sign-off → set casting, composition, props, light → write on-codes (every frame shows) and off-codes (no frame shows) from the POD, values, distinctive assets and the archetype's shadow → emit.

## Output — `archetype_lock.json`
```json
{
  "archetype": {"primary": "Caregiver", "secondary": "Everyman", "source": "positioning_brief.json archetype_hint"},
  "palette": {"source": "BRAND distinctive assets, else proposal for BRAND sign-off", "anchor": "Wellness — Soft (color-systems §2)", "primary_hex": ["#D4A5A5", "#9CAF88", "#F4F1ED"], "accent_hex": "#3F5E3F"},
  "casting": "real-looking women 30-50, unretouched skin, no fitness models",
  "composition": "eye level, close, documentary framing",
  "props": ["the real product", "mug", "linen"],
  "light": "soft warm daylight, 3200-3500 K",
  "distinctive_assets": ["from BRAND: colour, shape, mascot, sound"],
  "on_codes": ["calm morning", "touch", "real home"],
  "off_codes": ["clinic", "gym", "luxury marble"]
}
```

## Archetype → visual expression
CANON: operator heuristics. The props column is the original visual-anchor list; palette, casting and composition leans are operator defaults (UNVERIFIED). NOT IN SOURCE: no open source gives any archetype a colour, casting, composition or prop code (C-L2; Pearson's pages describe motives, gifts, shadows and subtypes only). Names (SRC 06b, 06c): Everyman = The Hero and the Outlaw's "Regular Guy/Gal" = Pearson's Realist (former Orphan); Outlaw = Revolutionary; Innocent = Idealist; Explorer is a Seeker subtype; Hero = Warrior is INF.

| Archetype | Props / visual anchors | Palette lean | Casting | Composition |
|---|---|---|---|---|
| Sage | books, scrolls, monochrome | ink, paper, monochrome | expert hands at work | centred, still, negative space |
| Hero | sweat, peak, summit | bold, high saturation | body mid-effort | low angle, diagonal, motion |
| Outlaw | leather, fire, road | B&W or red, crushed blacks | worn, defiant gaze | tilted frame, hard light |
| Magician | wand, mist, reveal | deep, glowing | hands mid-transformation | the reveal in one frame |
| Innocent | white, water, soft | white, pastel, high-key | natural skin, easy smile | high-key, airy, centred |
| Explorer | terrain, map, horizon | earth and sky | back to camera, facing out | wide, small figure, horizon |
| Ruler | crest, marble, throne | gold and black, navy | poised, tailored, still | symmetry, low angle |
| Creator | brick, sketch, hand-made | raw materials | hands making | overhead flat-lay, process sequence |
| Caregiver | infant, soft hand, white | soft warm, pastel | touch between two people | close, soft light |
| Everyman | family table, normal-sized rooms | natural, unstyled | real people, mixed ages | eye level, documentary, UGC look |
| Lover | silk, perfume, candlelight | warm, deep red | skin, closeness | tight crop, shallow DOF, low key |
| Jester | absurd flip, costume | saturated, clashing | expressive faces | off-centre, one surprise |

## Rules
- BRAND's colours, logo, distinctive assets and tagline win; this sub-skill expresses them and never invents one.
- Two archetypes at most. The primary sets props and composition; the secondary tints palette and casting.
- No more than 3 palette colours above 40% saturation in one frame (color-systems §3).
- Props match the price tier: Ruler codes (marble, crest, gold) on a $20 product read as a register mismatch.
- Cast the buyer in BRAND's brief, not the supplier's catalogue model. US/UK/CA/AU: Western colour readings dominate (color-systems §5).
- BRAND's distinctive assets appear in every frame so the code compounds across exposures (archetypes §1).
- Off-codes include the shadow. SRC [06a]: the book "warns against possession by the archetype and urges vigilance to avoid being drawn into its negative potentials"; each archetype page names its shadow [06c] (Ruler: "dominating others", "overly hierarchical"; Outlaw subtype: "Disobeys laws and harms others or just adopts a bad boy/bad girl image"). INF: a frame that shows the shadow (a Ruler sneering down at the buyer) is an off-code.
- Casting shows people. SRC: "Images with a visible human presence consistently outperform other assets" [platform 14]; Meta Stories: awareness objective → "focus your ad on people", sales objective → "focus on products" [platform 01c]. INF: Caregiver, Lover and Everyman frames lead with people; a sales-objective cut still ends on the product.

## Worked check — ECOM (illustrative)
BRAND: $38 ceramic pour-over set, US buyers 25-40, archetype hint Creator + Sage, POD "hand-thrown look at a factory price".
- Props: the real dripper, kettle, beans. Palette: Premium — Minimalist off-white with one clay accent. Casting: hands only.
- Composition: overhead flat-lay of the pour sequence (Creator) plus a still, centred hero (Sage).
- Off-codes: chain-café cups, chrome espresso machines. Fails if the palette comes from the supplier's white-background catalogue shot.

## Fails when
- CREATIVE picks or changes the archetype, or a palette overrides or adds to BRAND's colours (BRAND's call: send it back).
- Three or more archetypes show up in one frame: the frame reads incoherent.
- Codes contradict BRAND's POD or price tier, or off-codes appear in frame (audit symbolism 3.4).

## Cross-link
- Hands `archetype_lock.json` to `brand-creative-mood` (emotion matches archetype), `brand-creative-noun` (Person = casting, Object = props), `brand-creative-prompt`; `brand-creative-audit` checks it under brand fit and symbolism.
- Palettes and hex: `../../references/color-systems.md` · composition and light: `../../references/cinematography.md` §2-3.

## Verification
- [ ] Archetype copied from BRAND's brief (source named), 2 max
- [ ] Palette = BRAND's colours (or a color-systems §2 proposal marked for sign-off), ≤3 saturated colours per frame
- [ ] Casting matches BRAND's target buyer
- [ ] On-codes and off-codes listed and traced to POD, values or distinctive assets
- [ ] No brand example or framework claim invented
- [ ] Off-codes include the archetype's shadow (06c); archetype names mapped to BRAND's book name
