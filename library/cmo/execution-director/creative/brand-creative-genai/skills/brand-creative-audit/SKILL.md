---
name: brand-creative-audit
description: >
  Score rendered creative on the 10x emotion rubric (0-100) before spend:
  emotion strike 30, surreal 20, symbolism 20, hyper-real 15, brand fit 15;
  returns band, verdict and iteration moves for the lowest layer. Use for
  "score creative", "audit creative", "rubric check", "10x audit",
  "creative review", "is this ad good enough", `brand-creative-genai audit`.
allowed-tools:
  - Read
  - Write
  - Bash
---

# Brand Creative Audit — 10x Emotion Rubric

The last gate before spend: it catches drift between brief and render and prescribes the fix. Operator rubric (CANON); weights, bands and the 0.5 s / 2 s read times are operator settings, NOT IN SOURCE.

**Reading rule:** platform pack `../../sources/platform-creative-2026-10/` (lake `C7-scoring-shoot`; checklist wording in `../../references/audit-rubric.md` § Platform pre-spend checklist) and research pack `../../sources/emotion-archetype-metaphor-2026-10/` (metaphor comprehension 12–13, colour 03–05). The page wins over the lake.

**Input:** `mood_lock.json` · `noun_matrix.json` · `metaphor_layers.json` · `copy_pack.json` · `archetype_lock.json` · the creative (image or video URL, description, or pasted result).
**Process:** score the 5 categories per creative → find the lowest layer → 1-3 specific iteration moves → apply the gate → emit.
**Script:** `python3 ../../scripts/score_creative.py --assessment assessment.json [--out scorecard.json]` (true / "warning" / false per check in; scorecard, band, verdict, moves out).

## Output — `audit_report.json`
```json
{
  "creatives": [
    {
      "id": "frame-1-mj-v7-variant-3",
      "scores": {"emotion_strike": 27, "surreal_layer": 16, "symbolism_layer": 19, "hyper_real_layer": 14, "brand_fit": 14, "total": 90},
      "band": "Iconic",
      "verdict": "SHIP — A/B as control",
      "iteration_suggestions": []
    }
  ],
  "iterations_required": 0,
  "avg_score": 87
}
```

## Checks (points)
Method, failure modes and calibration examples: `../../references/audit-rubric.md`.

| Category | Checks |
|---|---|
| Emotion strike 30 | primary emotion readable in <0.5 s 12 · supporting 1 in <2 s 6 · supporting 2 in <2 s 4 · no competing emotion 4 · `mood_lock` anti-keywords absent 4 |
| Surreal 20 | at least one surreal move 6 · canon reference identifiable 4 · inside the category cap 4 · brand-safe (aspirational, not absurd) 3 · scroll-stop "wait, what" beat 3 |
| Symbolism 20 | all 5 noun slots loaded 8 · Lakoff metaphor identifiable 4 · Barthes connotation right for the target market 4 · IS codes shown and IS NOT codes absent (`archetype_lock` on / off codes) 4 |
| Hyper-real 15 | lens readable 3 · lighting plan visible 3 · texture truth (pores, weave, dust, melt) 3 · film stock or grade identifiable 3 · no AI artifacts 3. Each artifact -2, floor 0 |
| Brand fit 15 | Aaker lift potential: awareness (distinctive code) 3 · perceived quality 3 · associations match BRAND's target 3 · loyalty cue (subscription, scarcity) 3 · Olins product / environment / communication / behaviour aligned 3 |

**Hard fails, whatever the score (CANON):** the product in frame differs from what ships (finish, size, colour, contents) → re-composite with the real product photo · a synthetic person shown as a real customer, or an invented quote → remove it.

## Platform gate (SRC, pass / fail, runs beside the score)
A fail is fixed before spend whatever the total. Full wording per page: audit-rubric.md § Platform pre-spend checklist.
- Every video: brand and key message in the first 3 s (Meta [01b]); hook in the first 6 s and proposition in the first 3 s (TikTok [09]); reads with sound off (subtitles for any dialogue [01b]); a CTA that says the action, also spoken (ABCD D [13a]).
- Every 9:16 frame: text, logo and product clear of the top 14%, bottom 35%, 6% sides; no licensed music, GIFs or face effects in Reels ads [03b].
- TikTok: sound or music, 9:16, ≥720p, captions at 5-10 words per second [09]; no fake play, close or CTA buttons [12b]; no "swipe up" or cursor [12c]. YouTube images: no fake buttons, no black bars or oversized logos [14].
- Vendor-reported lifts behind these lines (ABCDs "as much as" +30% short-term sales; human voice +12%, supers +3%, brand in first 5 s +4% conversions [14]) are reasons to check, never a forecast.

## Gate
- ≥90 Iconic: ship, A/B as control · 80-89 Strong: minor polish, then ship
- 70-79 Working: iterate the ONE lowest layer, re-audit · 60-69 Weak: iterate TWO layers, re-audit
- <60 Reject: restart from the mood lock
- Below 80 → updated prompt with the lowest-layer fix → re-run `brand-creative-prompt` (or `brand-creative-metaphor` when a dial changes) → re-audit. Max 3 loops, then operator review.

## Iteration move by lowest category
| Lowest | Move |
|---|---|
| Emotion strike | re-check the mood lock; replace one weak noun slot; push the primary emotion through light or the activity beat |
| Surreal | add a Magritte-style floating object or a scale inversion; surreal +2. If the test viewer couldn't state the metaphor, go the other way: structure down a step or a headline that names it (metaphor-frameworks §8: the hardest-to-read structure lost in both studies) |
| Symbolism | audit each noun for meaning; swap a generic prop for a loaded one (gold for brass, stag for deer) |
| Hyper-real | tighten the lens spec; add texture (pores, dust, weave); name the grade LUT |
| Brand fit | re-check `archetype_lock` codes against BRAND's brief; align product, environment, communication, behaviour |

AI-artifact list (fingers, faces, garbage text, eyes, edge bleed, repetition, symmetry, hair, shadow direction) and audit anti-pattern thresholds: audit-rubric.md "AI-Artifact Detection Pass" and its bottom section.

## Verification
- [ ] All 5 categories scored, total 0-100, band assigned
- [ ] AI artifacts checked; hard fails checked
- [ ] Iteration moves match the lowest layer; gate applied
- [ ] No score invented: every point traces to a check
- [ ] Platform gate run; every fail fixed before spend
