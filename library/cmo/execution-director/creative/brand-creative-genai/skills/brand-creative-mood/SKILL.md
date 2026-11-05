---
name: brand-creative-mood
description: >
  Lock the emotion before any prompt: one primary plus two supporting
  emotions, aesthetic anchor, colour temperature, light, texture and sound,
  as mood_lock.json for the noun, metaphor, prompt and photoshoot steps. Use
  for "brand mood", "emotion lock", "what feeling", "moodboard", "mood board
  lock", "aesthetic anchor", "tone for creative", `brand-creative-genai mood`.
allowed-tools:
  - Read
  - Write
---

# Brand Creative Mood — Emotion + Aesthetic Lock

Step one of every creative run. Before a single noun is picked, the emotion is locked; a generic lock gives generic output.

**Reading rule:** research pack `../../sources/emotion-archetype-metaphor-2026-10/` (emotion models 01–02, colour 03–05, light and composition 08a–08b; lake `C-L1`) and platform pack `../../sources/platform-creative-2026-10/` (sound). The page wins over the lake. SRC lines below cite page files; everything else here is CANON.

**Input:** `positioning_brief.json` (desire, awareness stage) · `archetype_lock.json` · category, price tier, target market · competitor reference ("we feel like X, not Y") · optional operator-stated emotion.
**Process:** 1 primary + 2 supporting emotions (table 1) → aesthetic anchor by category and price tier (table 2) → colour temperature + Kelvin (`../../references/color-systems.md` §1; SRC [08a Nikon]: Sunny = 5000 K, "typical of mid-day sun"; the Kelvin setting can "skew the colors to reflect your choice of the scene's mood"; no source ties a Kelvin band to an emotion) → light quality (golden hour / overcast / studio rake / blue hour / harsh midday / candlelit) → texture register (clean / weathered / wet / dusty / metallic / organic / synthetic) → sound (silent / ambient / scored / SFX-heavy; feeds Sora and Veo; SRC: Reels ads "should not contain" licensed music, use original audio or the Meta Sound Collection [platform 03b]; "The majority of Stories with voice-over or music tend to drive better results" [01c]; design every cut to read with sound off too [01b]) → anti-keywords → emit.

## Output — `mood_lock.json`
```json
{
  "primary_emotion": "awe",
  "supporting_emotions": ["serenity", "longing"],
  "aesthetic_anchor": "heritage",
  "color_temperature": "warm",
  "color_temp_kelvin": 3200,
  "light_quality": "golden hour, soft rake",
  "texture_register": "weathered organic + brass",
  "sound_suggestion": "ambient, fire crackle, wood creak",
  "scroll_stop_target_ms": 500,
  "brand_keywords": ["legacy", "craft", "patina", "ritual"],
  "anti_keywords": ["modern", "slick", "minimal", "tech"]
}
```

## 1. Emotion picks (the 1 + 2 count is INF: [01]/[02] back basic emotions and blends, not a count; C-G1)
SRC [02 PyPlutchik, PLOS ONE 2021]: Plutchik's 8 basic emotions (joy, trust, fear, surprise, sadness, disgust, anger, anticipation), each in three degrees of intensity; adjacent petals combine into primary dyads (e.g. Optimism, Love), two apart into secondary dyads (Hope = anticipation + trust); "spatial opposition is a semantic opposition". SRC [01 Posner, Russell & Peterson 2005]: the circumplex places every affect on two dimensions, valence (pleasure–displeasure) and arousal; the authors say basic-emotion theories "no longer explain adequately the vast number of empirical observations" (CONFLICT with Plutchik's discrete petals; use Plutchik to name, the circumplex to check). INF: primary and both supporting emotions sit on the same side of valence, or the audit's "no competing emotion" check (1.4) fails. Awe, serenity, longing and pride are brand extensions; category leans are CANON (UNVERIFIED). Colour tilts: SRC only where `color-systems.md` §5b backs them (joy–yellow, orange, pink · sadness–gray, black · fear–black · anger and love–red · trust–blue in store, site and logo settings); the rest UNVERIFIED.

| Emotion | Brand categories that lean here | Colour tilt |
|---|---|---|
| Joy | youth, food, family, mass beauty | warm, saturated |
| Trust | wellness, finance, healthcare | cool blue, white |
| Fear (controlled) | security, insurance, anti-theft | dark, contrast |
| Surprise | tech launch, drops, novelty | high contrast |
| Sadness (aspirational) | luxury melancholy, fragrance | desaturated, blue-grey |
| Disgust (rejected) | almost never: anti-pattern | n/a |
| Anger (controlled) | activism, protest, edgy | red, raw |
| Anticipation | drops, pre-launch, food | warm, lifted |
| Awe | luxury, heritage, automotive | deep, dramatic |
| Serenity | wellness, sleep, hospitality | soft, low saturation |
| Longing | fragrance, travel, fashion | golden, atmospheric |
| Pride | sport, achievement, status | bold, high saturation |

## 2. Aesthetic anchor (price tiers UNVERIFIED; sound NOT IN SOURCE, C-G1)
| Anchor | Price tier | Colour bias | Texture | Sound |
|---|---|---|---|---|
| Luxury | $500+ | warm gold / cool silver | silk, leather, stone | silent or scored |
| Heritage | $200-2000 | warm sepia | wood, brass, leather, patina | crackle, creak |
| Premium | $100-500 | desaturated neutral | brushed metal, glass | ambient |
| Wellness | $30-300 | cool greens, off-white | linen, ceramic, water | flute, breath |
| Tech | $50-2000 | cool blue, anthracite | brushed titanium, glass | electronic pulse |
| Youth | $20-200 | saturated, bipolar | sweat, denim, plastic | hip-hop, club |
| Edgy | $30-500 | high-contrast B&W or red | rust, neon, raw concrete | distortion |
| Minimalist | varies | off-white, single accent | seamless, glass | silent |
| Maximalist | varies | jewel tones, layered | velvet, gold, fur, marble | orchestral |

## Block emotions that fight the category
Joy on luxury fragrance → longing or awe · anger on wellness → serenity · fear on food → anticipation or joy · serenity on an energy drink → pride or anticipation. If the brief implies a mismatch, flag it and confirm with the operator before going on.

## Context check (SRC, before emitting)
- Colour meaning follows context: red raises attraction in a mating setting and undermines performance in an achievement setting; blue raises trust appraisals of stores, sites and logos (colour-in-context theory) [03 Elliot 2015].
- Across 30 nations (US, UK included) colour–emotion patterns are shared (mean r = .88), pink most consistently, purple and yellow least [04 Jonauskaite 2020]. INF: don't let purple or yellow carry the primary emotion alone.
- Limits: [04] rated colour words, not colour patches; [03] flags underpowered samples, failed replications and colour rarely controlled at the spectral level. INF: a tilt for picking, never a predicted lift; the audit's emotion read decides.

## Cross-link
- Hands `mood_lock.json` to `brand-creative-noun`, `brand-creative-metaphor`, `brand-creative-prompt`, `brand-creative-photoshoot`
- Kelvin and palettes: `../../references/color-systems.md` · emotion-trigger theory: `marketing-psychology` (link it; the teaching stays there)

## Verification
- [ ] Primary emotion is one word from table 1; two supporting emotions named
- [ ] Anchor matches price tier, category and BRAND's archetype
- [ ] Kelvin estimate given
- [ ] ≥3 anti-keywords
- [ ] Every keyword traces to BRAND's brief or the operator
- [ ] Colour tilt traced to color-systems §5b (SRC) or marked UNVERIFIED; sound plan uses no licensed music on Reels
