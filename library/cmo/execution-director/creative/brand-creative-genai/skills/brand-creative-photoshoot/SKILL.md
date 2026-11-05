---
name: brand-creative-photoshoot
description: >
  Write a production brief for a real shoot, a UGC creator or a high-fidelity
  GenAI render run: the four pillars (mood, category, colour, copy), shot list
  from the noun matrix, call sheet, props, wardrobe, location, lighting and
  grade. Use for "photoshoot brief", "brand kit photoshoot", "shoot brief",
  "call sheet", "shot list", "campaign brief", "art direction brief",
  `brand-creative-genai photoshoot`.
allowed-tools:
  - Read
  - Write
---

# Brand Creative Photoshoot — Brand-Kit Brief

The operator's four-pillar input set: brand mood · target category · brand colour theme · copywriting. This sub-skill takes those four plus the noun matrix and emits a brief a photographer, a UGC creator or a GenAI render queue can run.

**Reading rule:** platform pack `../../sources/platform-creative-2026-10/` (lake `C7-scoring-shoot`: what a shoot must hand over) and research pack `../../sources/emotion-archetype-metaphor-2026-10/` (white balance 08a, composition 08b). Sourced hand-off table: `../../references/photoshoot-brief-template.md` §14. The page wins over the lake.

## Shoot or render? (CANON)
- Solo founder, little budget: the default is a phone or light-box shoot of the supplier sample for product pixels, with GenAI building scene, model and light around it. SRC: "Mobile shots tend to outperform studio shots for ad recall and intent, while studio shots tend to drive higher brand awareness" [platform 01c]; TikTok asks for "a DIY or not overly polished style" [09]. INF: phone footage for conversion ads, a studio day only for awareness or texture.
- Book a photographer only when texture or fit is the POD, or GenAI renders fail the audit's hyper-real layer.
- Supplier catalogue photos are a reference for the real finish, size and colour, never the hero: every other seller of the SKU uses them.
- Live exotic animals: most can't be shot live in most jurisdictions. Default to a GenAI render + composite and flag it in the brief.

**Input:** `mood_lock.json` · `noun_matrix.json` · brand identity from BRAND (name, tagline, palette hex, type) · constraints (budget tier, location, talent, sample in hand).
**Process:** confirm the 4 pillars → shot list, 1-3 setups per noun slot (5-15 setups; 3-5 for a quick run) → call sheet (date, location, talent, crew, gear, schedule) → wardrobe per Person → props per Object → location per Place → animal plan per Animal (live or composite) → choreography per Activity → lighting per shot → grade → copy pairing (which headline runs on which frame) → one `photoshoot_brief.md`.

## The four pillars
| Pillar | Fill |
|---|---|
| Mood | from `mood_lock`: primary + 2 supporting emotions, anchor, Kelvin, light, texture, anti-keywords |
| Category | industry, price tier, geo + demographic, competitor frame ("we feel like X, not Y"), buying occasion (gift / self / subscription / impulse) |
| Colour | BRAND's palette: primary 1-3 hex, secondary 2-4, 1 accent, grade direction (warm / cool / split / neutral shadows), material colour, where each colour sits (subject, prop, background) |
| Copy | tagline 3-6 words, hero headline 3-7 (`brand-creative-copy` owns it), sub-headline 10-25, CTA, voice register from BRAND, reading rhythm |

## Shot list
One row per setup: `# · slot · setup · lens · light · wardrobe / prop · activity beat · aspect`. Worked ice-cream rows, sample schedule and copy-pairing table: bottom of `../../references/photoshoot-brief-template.md`.

## Plans and notation
- **Lighting (K/F/B/P):** K key (size, position, intensity) · F fill (ratio 1:2, 1:4, 1:8) · B back or rim · P practicals. Example: K 4x6 softbox camera left 45°, F bounce camera right 1:4, B bare bulb behind subject high right, P one candle on the table.
- **Wardrobe per Person shot:** garment, material, palette match, styling (clean / weathered / wet / dusty), jewellery or explicit none, hair, makeup.
- **Animal (if live):** licensed handler + permit copy, welfare plan, stunt / safety plan with talent, CGI backup if welfare blocks the shoot.
- **Grade:** LUT reference (Kodak 250D, Fuji 400H, Arri Alexa LogC, custom), shadow and highlight tint, saturation (-20% to +30%), grain, vignette, 3 hero reference frames for the grader.
- **White balance (SRC [08a]):** write the Kelvin per setup; Sunny = 5000 K, "typical of mid-day sun"; mixed light → PRE white-card reading. **Framing (SRC [08b] + INF):** rule-of-thirds intersections, subjects looking into the frame; on 9:16 use the upper intersections, the lower third falls in Meta's bottom 35% UI band.
- **ECOM deliverables (SRC, template §14):** 9:16 vertical master (TikTok "at least 720P" [09]; Reels 1440 x 2560 [03b]); square ≥1080x1080 and vertical 1080x1920 for Instagram [01b]; vertical, square and landscape, "at least 3 images or videos in each aspect ratio" per Demand Gen ad group [17d]; key elements clear of the top 14%, bottom 35%, 6% sides [03b]; captions recommended, sound "strongly recommended", no licensed music in Reels [03b]; a creator's post runs as a Spark Ad only "with their authorization", via an authorization code whose duration you set [11]. Plus a 1:1 product macro for the Shopify PDP (CANON). Fixed 15 s masters, audio stems and `.srt` hand-offs: NOT IN SOURCE.

## Cross-link
- Consumes JSONs from `mood`, `noun`; full 16-section template, call sheet and risk table: `../../references/photoshoot-brief-template.md`
- Hands off to `brand-creative-copy` for headline-visual pairing; pairs with `brand-creative-prompt` for GenAI alternates

## Verification
- [ ] All 4 pillars filled
- [ ] Shot list has 5-15 setups, at least one per noun slot
- [ ] Call sheet has talent, crew, gear, schedule
- [ ] Lighting uses K/F/B/P notation; grade names a LUT or reference
- [ ] Animal plan filed (live or CGI composite)
- [ ] Copy pairing maps headlines to specific frames
- [ ] Product pixels real; no invented location, talent or permit
- [ ] Deliverables cover vertical, square and landscape with safe zones kept; Kelvin per setup; creator authorization asked for any Spark use


