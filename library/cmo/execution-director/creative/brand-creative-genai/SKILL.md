---
name: brand-creative-genai
description: >-
  CREATIVE turns BRAND's positioning into GenAI visuals: concept per awareness stage, image/video prompts (Midjourney, Flux, Sora, Veo), photoshoot vs GenAI, moodboards, storyboards, scoring creative before spend. Never sets positioning.
argument-hint: "mood | noun | prompt | photoshoot | metaphor | copy | archetype | audit | full <positioning-brief>"
allowed-tools: [Read, Write, Edit, Bash, Grep, Glob]
---

# Brand Creative GenAI — BRAND's Brief Into Pixels

`brand-strategy (BRAND) → positioning_brief.json → brand-creative-genai → prompt_pack / photoshoot_brief / copy_pack → PAID (ads) · PRODUCT (PDP)`

Input is BRAND's `positioning_brief.json`: desire, awareness stage, POD, archetype hint, voice, distinctive assets. If it is missing, stop and ask BRAND to run `brand-strategy`. CREATIVE never picks positioning, archetype or voice. The method here is CANON (operator method, no source). Every number is UNVERIFIED unless a reference § labels it. Ad-platform facts (Meta, TikTok, Google formats, specs, claims rules, AI labels) are SRC in `references/platform-creative.md` (official pages fetched 2026-10-11, refresh-by 2027-01-11; TikTok pages are archived copies). GenAI tool facts stay a January 2026 baseline, so re-check vendor docs before spend.

## Commands → sub-skills
`/brand-creative-genai <cmd> <brief>` loads `skills/brand-creative-<cmd>/SKILL.md`. No command = `mood`. `full` runs steps 1→8 in order, each consuming upstream JSON.

| Step | Cmd | Consumes | Produces |
|---|---|---|---|
| 1 | archetype | positioning_brief.json | `archetype_lock.json`: BRAND's archetype as palette, casting, composition, props |
| 2 | mood | brief + archetype_lock | `mood_lock.json`: 1 primary + 2 supporting emotions, light, texture, sound |
| 3 | noun | mood_lock | `noun_matrix.json`: Person, Place, Object, Animal, Activity |
| 4 | metaphor | mood + noun | `metaphor_layers.json`: surreal / symbolism / hyper-real dials 1-10 |
| 5 | prompt | mood + noun + metaphor | `prompt_pack.md`: 3-5 variants per platform |
| 6 | photoshoot | mood + noun + brand identity | `photoshoot_brief.md`: shot list, call sheet, props, light, grade |
| 7 | copy | mood + noun + metaphor + BRAND voice | `copy_pack.json`: headline-visual pairs, tagline, CTA |
| 8 | audit | all + rendered creative | `audit_report.json`: 0-100 score, band, iteration moves |

## Decision questions → test → fails when → where
| Question | Test (CANON) | Fails when | Where |
|---|---|---|---|
| Q1. Which visual concept for this awareness stage and desire? | Stages per BA §2. Unaware: identification (the buyer's state of mind or a metaphor), no product or price. Problem-aware: the problem first, then the product as the answer. Desire-aware: the wanted result, then the mechanism (demo, macro). Product / most-aware: the real product, proof, offer; surreal low | product or price opens an unaware frame; a problem-aware frame skips the problem | `marketing-execution-persuasion` BA §2 · mood, metaphor |
| Q2. How do I write a prompt the model renders correctly? | One platform's syntax per prompt. Name subject, scene, light, lens, texture, grade. Midjourney ≤5 comma clauses; Flux takes no negatives. 3-5 variants, one dial changed each | two platforms' syntax mixed; a flag not in current vendor docs; several dials changed at once | prompt · `references/prompt-vocabulary.md` §1-7 |
| Q3. Image, video or UGC? | Still first (4:5 feed, 1:1 PDP) to find the concept. Animate the winning still (image-to-video) before paying for text-to-video. UGC needs a real creator holding the real sample | video paid for before a still wins; "UGC" made from a render | which tool: v2 `video`, `ad-creative/references/generative-tools.md` · format per placement (Reels 9:16 video with audio, TikTok people and DIY, Spark for creator posts): `references/platform-creative.md` §1 |
| Q4. Photoshoot or GenAI? | Product pixels are the real product (supplier sample shot on a phone or light box). GenAI builds scene, model and light around it (Nano-Banana edit or composite). Book a shoot only when texture or fit is the POD | GenAI renders the product itself (finish, size, colour the buyer won't get) | photoshoot · `references/photoshoot-brief-template.md` |
| Q5. Is this creative good enough to spend on? | 10x rubric ≥80. Below 80, iterate the lowest layer; after 3 loops, the operator decides | ships under 80, or a 4th loop without the operator | audit · `references/audit-rubric.md` |
| Q6. Which size for which placement? | SRC: 4:5 Facebook Feed and Instagram Feed images · 9:16 Reels, Stories, Instagram Feed video, TikTok, Shorts · 1:1, 1.91:1, 4:5, 9:16 Demand Gen images · 16:9, 9:16, 1:1 YouTube. Meta 9:16 keeps 14% top, 35% bottom, 6% sides clear (bottom 40% with a disclaimer). 1:1 Shopify PDP stays CANON | one crop reused everywhere, so UI overlays cut the product or text | `references/platform-creative.md` §3 · prompt-vocabulary "Aspect Ratio Map" · template §14 |
| Q7. Which hook, first seconds, sound and length? | SRC: product or proposition inside 3 s (Meta, TikTok), brand inside 5 s (YouTube); captions plus a human voice. INF: a master ≤15 s, and ≥10 s if it may run on Demand Gen in-stream | the open is a question about the viewer's body; the video only works with sound on | `references/platform-creative.md` §2 |
| Q8. Does the copy or visual pass platform policy? | SRC: benefit framing only. Meta bars negative words or questions about appearance, body parts or hygiene and "you/your" + a personal attribute; TikTok bars exaggerated effects, time absolutes and before/after. CONSULTANT T4 clears | a "Do you smell…?" hook; a before/after in a set meant for TikTok | `references/platform-creative.md` §4 |
| Q9. Does a GenAI asset need a label? | SRC: Meta labels its own GenAI edits and C2PA-detected ones; TikTok needs the AIGC label for fully AI image, video or audio and AI people; Google labels where EU, India or New York rules apply | an AI person or voice-over shipped unlabelled on TikTok | `references/platform-creative.md` §5 |
| Q10. How many variants per test? | ≥3 genuinely different (`../references/doctrine.md` §C). SRC: TikTok 3-5 per ad group; Demand Gen 3 per aspect ratio; Search 2 RSAs per ad group, up to 15 headlines each. PAID sets the structure | word swaps counted as variants; one RSA per ad group | `references/platform-creative.md` §6 |

## Method — the 10x emotion stack
Operator thesis: people buy the brand, not the product; this stack engineers the brand feeling into pixels.
BRAND's archetype read → emotion lock (1 primary + 2 supporting) → noun decompose (5 slots) → aesthetic match (each noun reinforces the emotion) → surreal dial (Magritte / Dalí / Escher / Kusama) → symbolism dial (Lakoff metaphor, Barthes connotation) → hyper-real dial (lens, light, texture, grain) → platform prompt → audit, iterate below 80.

## Gates (operator rules)
- No prompt before the emotion is locked. All 5 noun slots reinforce it; no neutral slot.
- Dial caps: luxury surreal ≤6 · wellness surreal ≤5 · tech symbolism ≤7 · food / beauty hyper-real ≥8 · combined 8-27 of 30 (metaphor sub-skill; tech CONFLICT noted in audit-rubric §2.3).
- Every prompt's syntax is checked against prompt-vocabulary.md and current vendor docs.
- Artists only from the canonical list (metaphor-frameworks §4). No invented artist, platform feature, quote or brand example.
- Audit ≥80 before spend. Frameworks live with their owners: Schwartz stages and Hormozi offer wording in `marketing-execution-persuasion`; DASH desire mapping in BRAND `../../../../ceo/strategy-director/brand/brand-strategy/references/desire-mapping.md` D1–D6; the Value Equation in BRAND `../../../../ceo/strategy-director/brand/brand-strategy/references/sales-voices.md` V1.1. Apply them here; the teaching stays there.
- BRAND's colours, logo, distinctive assets and tagline win. Sub-skills express them and never invent one; a gap goes back to BRAND.

## Rubric — 10x emotion (0-100, operator rubric)
Emotion strike 30 (primary emotion readable in <0.5 s) · surreal 20 (breaks reality just enough to stop the scroll) · symbolism 20 (every prop, colour, animal carries brand meaning) · hyper-real 15 (lens, light, texture, grain believable; -2 per AI artifact) · brand fit 15 (lifts BRAND's target associations).
Bands: 90-100 Iconic (ship, A/B as control) · 80-89 Strong (polish, ship) · 70-79 Working (iterate the lowest layer, usually surreal or symbolism) · 60-69 Weak (iterate two layers) · <60 Reject (restart from the emotion lock).

## Worked check — ECOM, walking the decision table (illustrative; CANON, numbers UNVERIFIED)
$32 mulberry-silk pillowcase, China-sourced, sold on Meta and TikTok to US women 30-50. BRAND's brief: desire "wake up looking rested", problem-aware, archetype hint Lover + Caregiver, POD "real silk, not satin".
- Concept: problem-aware, so open on the problem (frizz and a sleep crease at the mirror), then the answer (smooth hair at the window); not the momme count. Mood: serenity primary, anticipation and trust supporting, warm 3200 K light.
- Prompt: Midjourney, 5 clauses; surreal 3 (silk pours off the pillow like water), symbolism 7, hyper-real 9; variants change one dial each (surreal 2 / 3 / 4). Wellness surreal cap ≤5 holds.
- Format: 4:5 still first; Runway animates the winning still for 9:16; no Sora spend until a still wins.
- Pixels: shoot the supplier sample on a phone; Nano-Banana builds bedroom and light around it.
- Gate: every variant ≥80 before PAID spends; a render with more sheen than the $32 product has is re-composited (refund risk). Sizes: 4:5 feed, 9:16 Reels, 1:1 PDP.

## Fails when
- The prompt comes before the emotion and BRAND's brief: generic output, no scroll-stop.
- CREATIVE invents positioning, archetype or voice that BRAND didn't set.
- The render shows a product the customer won't receive (finish, size, colour, contents): refunds and chargebacks.
- A synthetic person is shown as a real customer, or a quote is invented. Claims go through CONSULTANT before spend.
- All three dials sit at 10 (eye fatigue, reads chaotic), or the 5 nouns have no tension pair (flat, stock-like).

## References (`references/`, load on demand)
- `platform-creative.md`: Meta, TikTok and Google format, hooks and length, placement specs, claims and policy for hygiene copy, AI labels, test volume (official pages 2026-10-11) · `prompt-vocabulary.md`: per-model syntax, flags, worked prompts (tool choice → v2 `image`, `video`)
- `audit-rubric.md`: 24 check items, calibration examples, AI-artifact pass, sign-off gate · `metaphor-frameworks.md`: Lakoff, Barthes, McCracken, verified surrealism canon, surreal moves, symbol library
- `cinematography.md`: lens, light, composition, grade, film stock, texture, camera moves · `color-systems.md`: Kelvin × emotion, anchor palettes (hex), grade directions, cultural colour
- `noun-aesthetic-library.md`: 18 category matrices, category detection signals, the operator's ice-cream example · `photoshoot-brief-template.md`: 16-section brief, call sheet, deliverables, worked shot list · `copy-patterns.md`: voice registers, headline and CTA patterns
- `archetypes.md`: Aaker, Holt, Jung, Olins, Greimas, McCracken. These are BRAND's frameworks; read them only to decode BRAND's choice

## Scripts (run from this folder with python3)
- `scripts/noun_decompose.py --category <key> --auto | --interactive [--out matrix.json]`: fills the 5-slot matrix from its inline library; `--list` prints the 13 keys.
- `scripts/generate_prompt.py --brief brief.json --platforms mj,flux,sora --aspect 4:5 [--all] [--out prompts.json]`: brief holds `mood_lock`, `noun_matrix`, `metaphor_layers`; prints per-platform prompts (keys mj, flux, sdxl, sora, runway, veo, nano).
- `scripts/score_creative.py --assessment assessment.json [--out scorecard.json]`: per-check true / "warning" / false → 0-100 score, band, verdict, iteration moves.

## Scope
Owns: GenAI image and video prompts, photoshoot and render briefs, moodboards, storyboards, metaphor layering, headline-visual pairing, the 10x audit. Not here: desire, positioning, archetype choice, voice, naming, tagline, brand colours → BRAND `brand-strategy` · copy frameworks → `marketing-execution-persuasion`, `copywriting` · emotion-trigger theory → `marketing-psychology` · ad formats, fatigue, delivery → PAID `ads-creative` · store and asset design → ATELIER · UI colour → `ui-ux-pro-max` · logo and finished art → `canvas-design` · claims compliance → CONSULTANT · Adobe / Canva / Figma execution → operator.

## Verification (after every full run)
- [ ] `positioning_brief.json` read; nothing strategic invented
- [ ] Emotion lock: 1 primary + 2 supporting; 5 noun slots with ≥2 tension pairs
- [ ] Three dials stated 1-10, inside category caps
- [ ] ≥3 platform prompts, syntax checked, product pixels real
- [ ] Specs, claims and AI labels checked against `platform-creative.md` §3–§5
- [ ] Every variant audited ≥80; no invented artist, platform feature or quote
