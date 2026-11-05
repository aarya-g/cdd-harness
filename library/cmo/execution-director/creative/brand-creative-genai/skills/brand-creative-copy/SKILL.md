---
name: brand-creative-copy
description: >
  Pair every headline with a specific visual moment from the noun matrix:
  3 hero headlines, 2 sub-headlines, BRAND's tagline and a CTA per frame,
  in BRAND's voice, so words and image carry the same metaphor. Use for
  "headline for visual", "tagline", "copy pairing", "headline visual
  resonance", "ad copy for image", `brand-creative-genai copy`.
allowed-tools:
  - Read
  - Write
---

# Brand Creative Copy — Headline-Visual Resonance

Copy that doesn't reinforce the visual is wasted space, so each headline is pinned to a noun-slot moment. Frameworks are applied here; their teaching lives with the owners: Schwartz awareness stages → `marketing-execution-persuasion` · Hormozi Value Equation → BRAND `../../../../../../ceo/strategy-director/brand/brand-strategy/references/sales-voices.md` V1.1 · DASH desire-first → BRAND `../../../../../../ceo/strategy-director/brand/brand-strategy/references/desire-mapping.md` D1–D6 · Cialdini → `marketing-psychology`. Voice and tagline are BRAND's (`voice_dimensions`, tagline in `positioning_brief.json`); this sub-skill uses them and never sets or invents one.

**Reading rule:** Schwartz canon `../../../marketing-execution-persuasion/knowledge/breakthrough-advertising-canon.md` §3, §5, §6 (ch. 1–5 only); platform pack `../../sources/platform-creative-2026-10/` (text pace, CTA); research pack `../../sources/emotion-archetype-metaphor-2026-10/` (page 13, verbal anchoring). Sourced lines collected in `../../references/copy-patterns.md` §6. The page wins over a lake.

**Input:** `mood_lock.json` · `noun_matrix.json` · `metaphor_layers.json` · BRAND's voice register, awareness stage and tagline (if BRAND has none, the field stays blank and the gap goes to BRAND).
**Process:** read the inputs → state BRAND's awareness stage → encode the dream outcome (Hormozi) in the headline → per frame: 3 hero headlines, 2 sub-headlines, BRAND's tagline (the same across frames), 1 CTA → resonance check → emit.

## Output — `copy_pack.json`
```json
{
  "tagline": "Luxury, slowly (from BRAND)",
  "frames": [
    {
      "frame_id": 1,
      "noun_slot": "person + activity",
      "moment": "silk-draped hand lifts gold-leaf scoop, mid-drip",
      "hero_headlines": ["Held, not consumed", "Two seconds before the drip", "Why hurry the gold"],
      "sub_headlines": ["Hand-laid gold leaf. Slow churn. Three farms, one season.", "The scoop you wait for, in the bowl you keep."],
      "cta": "Reserve the season"
    }
  ],
  "voice_register": "poetic-aspirational (from BRAND)",
  "awareness_stage": "problem-aware (from BRAND)",
  "framework_refs": ["Schwartz problem-aware", "Hormozi dream outcome", "DASH desire-first"]
}
```

## Resonance check: every headline must
1. Name or imply a noun slot ("Held" → the Person's hand, "Apex" → the Animal, "The bite" → the Activity)
2. Reinforce the primary emotion in `mood_lock`
3. Stay inside the surreal dial (controlled surreal at 4 → controlled copy)
4. Read in under 1.5 s: count beats, 3-7 words for a hero headline (CANON; TikTok's "5-10 words per second" text pace [platform 09] puts the ceiling at 7-15 words, INF)
5. Quote a real person only from a verified source; otherwise no attribution
6. Names the link on a hard frame: when `metaphor_layers` fuses or replaces objects, or surreal ≥ 5, the hero headline says what the image means. SRC [13]: advertisers now use "less verbal anchoring of rhetorical pictures", and fusion was the hardest structure to understand; the rule itself is INF
7. Says one thing: "Focus the message: Avoid doing too much in your ad" [platform 13a]; Schwartz: one summary trait per headline (canon §6)

Why pin copy to the image (SRC, canon §3, §5): the headline's job is to get the next sentence read, and "your prospect must identify with your headline before he can buy from it"; "metaphorize" and "symbolize" are two of Schwartz's ch. 4 headline techniques.

Reject any headline that could run under another brand's visual: copy that floats is dead copy.

## Tagline and CTA
- Tagline: BRAND's, as given, the same on all 5-15 frames. If it runs past 6 words or leans on an English-only idiom, flag it to BRAND; never rewrite or replace it.
- CTA matches category register and price: "Reserve" on a $20 brand or "Cop it" on a $5000 brand is a mismatch (CANON).
- CTA says the action and is voiced in video (SRC): "Say what you'd like viewers to do" · "Reinforce your onscreen CTA with voice-over" [platform 13a]; Stories: "Emphasize the action … such as 'Shop now'" [01c]; Demand Gen: "repeat the CTA … in the voiceover and overlaid graphics" [17d].
- Voice-register cadences, headline patterns by emotion and CTA shapes by category: `../../references/copy-patterns.md`.

## Fails when
- The headline could fit any brand (generic)
- The copy names the spec on a luxury frame (moves it from luxury to bargain)
- A tagline is invented, or BRAND's is rewritten
- A quote or testimonial is invented. Claims go through CONSULTANT before spend

## Cross-link
- Pairs with `brand-creative-photoshoot` for the copy-pairing table; hands `copy_pack.json` to `brand-creative-audit`
- "What is a Schwartz awareness stage?" → `marketing-execution-persuasion`

## Verification
- [ ] Tagline copied from BRAND (or blank and flagged), one across all frames
- [ ] Each frame has 3 hero headlines, each naming or implying a noun slot
- [ ] Voice register and awareness stage taken from BRAND, both stated
- [ ] CTA matches category register
- [ ] No invented quotes
- [ ] Hard frames (fusion, replacement, surreal ≥ 5) carry a headline that names the link; video CTA is also spoken


