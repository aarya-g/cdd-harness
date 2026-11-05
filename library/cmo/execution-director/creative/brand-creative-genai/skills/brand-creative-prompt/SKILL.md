---
name: brand-creative-prompt
description: >
  Assemble ready-to-paste image and video prompts from the mood, noun and
  metaphor locks, in each platform's own syntax: Midjourney v7, Flux Pro 1.1,
  SDXL, Sora 2, Runway Gen-4, Veo 3, Nano-Banana. Use for "Midjourney
  prompt", "Flux prompt", "Sora prompt", "Veo prompt", "Nano-Banana",
  "SDXL", "image gen prompt", "assemble prompt", "generate prompt",
  `brand-creative-genai prompt`.
allowed-tools:
  - Read
  - Write
  - Bash
---

# Brand Creative Prompt — Platform-Specific Assembly

Takes the locked mood, nouns and metaphor dials and emits ready-to-paste prompts for each platform the operator picks.

**Input:** `mood_lock.json` · `noun_matrix.json` · `metaphor_layers.json` · platform list · aspect per placement.
**Process:** map nouns and dials into the platform's shape → syntax from `../../references/prompt-vocabulary.md` → lens, light, texture, grade from `../../references/cinematography.md` → 3-5 variants per platform, each changing one dial (for A/B) → flags and params → `prompt_pack.md`, one section per platform.
**Script:** `python3 ../../scripts/generate_prompt.py --brief brief.json --platforms mj,flux,sora --aspect 4:5` (brief holds `mood_lock`, `noun_matrix`, `metaphor_layers`; `--all` for every platform; `--out` to save).

## Platform shapes (UNVERIFIED: Jan-2026 baseline)
Per-model syntax, flags and worked prompts: `../../references/prompt-vocabulary.md` §1-7. Which tool fits the job (cost, text rendering, motion): v2 `image`, `video` and `ad-creative/references/generative-tools.md`; v2 owns tool choice. Aspect per placement: `../../references/platform-creative.md` §3 (SRC).
Must-know: Midjourney has no official API per v2 `image`, so an agent can't run it · Flux, no negative prompt · SDXL, weighted parens + negatives · video prompts carry camera move, duration and sound (`mood_lock.sound_suggestion`).

## Dial → prompt words
- Hyper-real 8-10: lens, shallow DOF, rake light, visible pores / lint / dust motes, no beauty smoothing, film-stock grade, cinematic crop.
- Surreal 6-10: one canon move from metaphor-frameworks ("object floats one inch above the surface, no shadow").
- Symbolism 7-10: load each prop with its connotation (metaphor-frameworks §1, §7).
- Full recipe strings: bottom of prompt-vocabulary.md.

## ECOM rules (CANON)
- Product pixels are real: generate the scene, then composite the supplier-sample photo (Nano-Banana edit or manual). Never let a model redesign the product.
- "no logo, no text" by default; add on-image text in post, or pick the text-capable model v2 `image` names when packaging copy must render.
- Test 3-5 prompts on the cheapest platform that fits before paying for Sora or Veo.

## Worked prompts
Ice-cream luxury prompts for MJ, Flux, SDXL, Sora, Runway, Veo and Nano-Banana: prompt-vocabulary §1-7 and its bottom section.

## Cross-link
- Consumes JSONs from `mood`, `noun`, `metaphor`; hands `prompt_pack.md` to `brand-creative-audit` for scoring
- Tool choice and workflow recipes: v2 `image`, `video`, `ad-creative/references/generative-tools.md`

## Verification
- [ ] Each prompt uses that platform's flags and syntax, checked against current docs
- [ ] Aspect set per placement
- [ ] ≥3 variants per platform, different dial settings
- [ ] Negatives included where supported (SDXL, MJ)
- [ ] Sound cue on video platforms (Sora, Veo)
- [ ] Real product pixels; no invented platform feature
