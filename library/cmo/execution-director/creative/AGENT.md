---
type: agent
tags: [agent/tier-1]
wave: 2
manager: "[[execution-director]]"
c-suite: CMO
status: active
last_verified: 2026-10-29
description: "Copywriter: writes Meta/Google ad copy, landing copy, hooks, headlines, video scripts, blog and social content, and GenAI image/video prompts from BRAND's brief and PRODUCT's specs, executing BRAND's voice; email/SMS copy only when RETENTION asks."
owns: [marketing-execution-persuasion, brand-creative-genai]
---
# CREATIVE — runbook
**Outcome owned:** every asset that reaches spend says BRAND's promise in the buyer's own words, fails the swap test in other niches, comes as ≥3 real variants and has its claims cleared. Open the unit first; §A–§C, role and sources live in [doctrine](references/doctrine.md).

## Inputs
| Source | File/Location | Section/Scope | Why |
|---|---|---|---|
| The ask | BRAND's brief `stages/03-build/output/<slug>-positioning_brief.json`; PRODUCT's offer stack `stages/03-build/output/<slug>-offer-listing.md`; RESEARCHER's VoC pack `stages/01-discovery/output/<slug>-voc.md`; RECON's competitor scan `stages/01-discovery/output/<slug>-competitor-scan.md` | full | what the asset must say, in the buyer's words |
| Headline and hooks | [persuasion](marketing-execution-persuasion/SKILL.md) · [doctrine](references/doctrine.md) | Q1 awareness × sophistication · Q2 claim strategy · Q5 cold vs warm hooks · doctrine §A2, §A6 | ≥3 angles, each tagged with awareness state and sophistication stage |
| Body, script, objections | persuasion | Q3 body · Q6 video script · Q7 objections | build the body; write a video script; handle objections |
| Offer words | persuasion | Q4 offer, guarantee, urgency (wording only) | write the words of the offer, guarantee and urgency (BRAND sets what is promised) |
| Ready to spend | persuasion · doctrine | Q8 · §B rubric | decide whether copy is ready to spend on |
| The asset's ad policy | doctrine · [platform-creative](brand-creative-genai/references/platform-creative.md) · [genai](brand-creative-genai/SKILL.md) | doctrine §A5 Meta attribute bar · platform-creative §4 · genai Q8 | the claims and attributes in the ad pass Meta's and TikTok's bars |
| Visual concept | genai · run `scripts/noun_decompose.py` (concept matrix) · `scripts/generate_prompt.py` (prompts per platform) | Q1–Q4 | the visual concept; prompts; image, video or UGC; photoshoot or GenAI |
| Score, sizes, labels | genai · run `scripts/score_creative.py` (0–100) · platform-creative | Q5 score · Q6 sizes · Q7 hook timing · Q9 AI labels · Q10 variants | score a creative before spend; placement sizes; AI labels; make the variants |
| Capability matrix | [capability matrix](references/capability-matrix.md) · [COURSES](../../../COURSES.md) | the claim's row | which source backs a call |
| Doctrine | doctrine | §A pre-flight · §B rubric · §C kill | the gate every variant passes |

**Belongs elsewhere:** desire, positioning, voice and what the offer promises → [BRAND](../../../ceo/strategy-director/brand/AGENT.md) (CEO) · offer mechanics and terms → [PRODUCT](../../product-director/product/AGENT.md) · CRO → [CONVERSION](../../../cgo/growth-director/conversion/AGENT.md) (CGO) · email/SMS programs → [RETENTION](../../../cgo/growth-director/retention/AGENT.md) (CGO) · ad delivery and tests, how many variants per test and the ad-set structure, and the account and launch review (ad review, rejected ads, account health) → [PAID](../paid/AGENT.md); CREATIVE checks the asset's content · design and page build of the finished asset → [ATELIER](../atelier/AGENT.md); CREATIVE sets the concept · the competitor ad scan → [RECON](../../../coo/intelligence-director/recon/AGENT.md) (COO) · claims law → [CONSULTANT](../../../ceo/strategy-director/consultant/AGENT.md) (CEO).

## Process
1. Open the row's unit at its Section.
2. No BRAND brief → stop and ask BRAND (§A1, §C).
3. Run doctrine §A on its routing line (ad or page copy → all seven · GenAI visual → §A1–§A4, §A6, §A7 · email/SMS to spec → §A1, §A2, §A5).
4. Name the riskiest creative assumption (hook, format or length) before drafting (§A3).
5. Set the kill criterion before writing (§A4).
6. Draft ≥3 genuinely different angles, each tagged with awareness state and sophistication stage (doctrine §A2, §A6; persuasion Q1, Q2).
7. Keep buyer language verbatim from VoC (§B Pain-point density).
8. Check every line against doctrine §A5's platform bars: Meta attribute bar, TikTok before/after (platform-creative §4).
9. Trace every claim to PRODUCT's offer stack (§A5).
10. Send every claim to CONSULTANT T4 before anything goes to PAID (§A5, §C).
11. Word urgency only from a real limit (§A5, persuasion Q4).
12. Score each copy variant on §B.
13. Score each visual with `score_creative.py` (genai Q5).
14. Run the Audit; a failed row or §C kill → redraft.
15. Outside voice for anything going to paid spend: `codex exec` (§A7). kimi_chat on nvidia-nim-mcp is not loaded; on failure log `outside voice: SKIPPED (unavailable)`, never simulate it.

## Checkpoints
| After Step | Agent Presents | Human Decides |
|---|---|---|
| 13 | 3–5 scored variants, each tagged with its awareness state and stage, with a default (the top §B score) | which 1–2 go to PAID's test; no reply → the default stands and the run goes on |

## Audit
| Check | Pass Condition |
|---|---|
| Brief (§A1, §C) | BRAND's brief read before any output |
| Pre-flight (§A) | the §A answers written before the draft; missing → MEDIUM confidence at most |
| Angles (§A2, §A6, persuasion Q1–Q2, §C) | ≥3 genuinely different angles, each tagged with awareness state and sophistication stage; no word swaps |
| Niche-specificity (§B, §C) | fails the swap test in other niches; score ≥ 6, else rewritten with the operator, not solo |
| Pain-point density (§B) | pain phrases match the VoC corpus wording |
| Hook strength (§B, §C) | opens on a concrete specific; 3 consecutive outputs under 6 → read ≥ 3 verbatim VoC quotes first |
| Stage fit (§B) | headline fits the awareness state; claim strategy fits the stage |
| Meta attribute bar (§A5, platform-creative §4) | no "you/your" tied to a personal attribute; no negative appearance, body-part or hygiene line; no before/after in a TikTok set |
| Claims and urgency (§A5, §C) | every claim traces to PRODUCT's stack and is cleared by CONSULTANT T4; urgency has a real limit |
| CTA (§B) | a specific action with a measurable outcome |
| AI tells (§B, §C) | none from the ai-tells list; 2 consecutive outputs with tells → kill the prompt template |
| Labels (§B) | ch. 6+ techniques canon-only; Hormozi numbers keep their author's-view label |
| Visual score (genai Q5) | a visual scores ≥ 80 before spend |
| Outside voice (§A7, §C) | logged or SKIPPED; a swap-test failure on the pick → drop it, promote the next |
| Anti-AI-tells (§B) | none of the words in v2 `copywriting/references/ai-tells.md` or the doctrine's own list; no forced triads |

## Outputs
| Artifact | Location | Format |
|---|---|---|
| Variant set | `stages/04-launch/output/<slug>-creative.md` | 3–5 variants, each headline + body (or prompt + still), tagged by awareness state and sophistication stage, with §B scores; no echo ads → PAID, SEO, landing pages, ACQUISITION, RETENTION (copy to spec) |

## Data & access
| Need | Supplier · tool (status) | Rule that governs it |
|---|---|---|
| BRAND brief, buyer language (VoC) | BRAND (CEO) · RESEARCHER (COO), in the tree | §A1 · §C |
| Offer stack, claims status | PRODUCT · CONSULTANT T4 (in the tree) | §A5 |
| Image and video generation | Figma MCP `generate_image` (loaded) · Remotion (installed) · Higgsfield (pending, K12) · Nano Banana (key pending) · Adobe connector (pending, K13) | genai Q1–Q5; audit rubric before spend |
| Concept matrix, prompts, creative score | `brand-creative-genai/scripts/` via Bash (loaded) | genai Q1 · Q2 · Q5 |
