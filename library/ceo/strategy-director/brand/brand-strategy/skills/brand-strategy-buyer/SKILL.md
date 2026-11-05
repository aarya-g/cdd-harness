---
name: brand-strategy-buyer
description: >
  Step 0, before any positioning: classify how buyers decide (objection,
  driver, awareness stage, trust mechanisms, decision-maker) from VoC and
  sales evidence into buyer_psychology.json. Use for "buyer psychology",
  "buyer behavior", "how buyers decide", "objection analysis",
  `/brand-strategy buyer`.
allowed-tools:
  - Read
  - Write
  - Bash
---

# Brand Strategy Buyer — Sales Psychology Grounding

The evidence base every other sub-skill consumes. No buyer evidence, no positioning.

**Input:** brand brief (category, price tier, market) + operator evidence: VoC scrape (reviews, forums, social), sales-call objection logs, or the Sales Voices NotebookLM notebook (id and re-query commands: `references/buyer-psychology.md` Source).
**Process:** read `references/buyer-psychology.md` → run `scripts/buyer_signal_extract.py` on any corpus export (code-bound counts, no LLM prose) → classify the 5 dimensions below → flag primary-research gaps → emit.

## Output — `buyer_psychology.json`
```json
{
  "dominant_objection_archetype": "price-vs-cost",
  "objection_evidence": ["count + sample phrases from corpus"],
  "primary_decision_driver": "loss-aversion",
  "driver_evidence": ["count + sample phrases"],
  "awareness_stage": "problem-aware",
  "trust_mechanisms_required": ["third-party validation", "risk reversal"],
  "decision_maker_archetype": "single-buyer-D2C",
  "buying_journey_stage_weights": {"recognition": 0.3, "evaluation": 0.4, "resolution": 0.2, "implementation": 0.1},
  "primary_research_gaps": ["day-in-life context", "spend-allocation specifics"],
  "evidence_confidence": "MEDIUM — text-only, no IDIs"
}
```
Weights in the example are placeholders, not benchmarks; stages follow the SPIN buying cycle (buyer-psychology §1).

## The 5 classification dimensions

**1. Dominant objection archetype** (Sales Voices notebook synthesis; depth: sales-voices V2)

| Archetype | Signal phrases | Brand implication |
|---|---|---|
| price-vs-cost | "too expensive", "can't justify", "cheaper elsewhere" | POD reframes the cost of not buying |
| external-approval | "need to ask my partner", "run it by my team" | arm the internal champion |
| transformation-skepticism | "does it actually work", "sounds too good" | trust mechanisms + proof are mandatory |
| timing | "not right now", "maybe next quarter" | create constructive tension |
| status-quo-inertia | "what we have is fine" | dramatize the cost of staying |

**2. Primary decision driver**

| Driver | What moves the buyer | Source |
|---|---|---|
| loss-aversion | fear of losing outweighs equal gain | Prospect Theory (Kahneman & Tversky; canonical addition) |
| status-gain | outcome that raises rank among peers | Hormozi "Who" step (sales-voices V1.12); Naval half canon-only, UNVERIFIED |
| trust-deficit | reducing perceived risk is the unlock | trust mechanisms / risk reversal (buyer-psychology §1) |
| peer-trend | what similar people are doing | Jones Theory: canon-only, UNVERIFIED |
| transformation | the dream-outcome leap itself | Hormozi Value Equation (sales-voices V1.1) |

**3. Awareness stage** (Schwartz): problem-unaware → problem-aware → solution-aware → product-aware → most-aware. Sets how much problem setup the brand does before it can sell.

**4. Trust mechanisms required:** social proof, testimonials, third-party validation, risk reversal / guarantee, founder transparency, demonstration / trial, certification. List the specific ones the evidence demands. "High-ticket and transformation-skeptic buyers need 3+ mechanisms" is UNVERIFIED (no basis in sales-voices.md): count from the corpus, don't assume.

**5. Decision-maker archetype**

| Archetype | Behaviour | Source |
|---|---|---|
| single-buyer-D2C | one person, fast, emotion-led | D2C default |
| Adapter / Innovator / Seeker | relationship-led / tech-forward, self-directed / seamless omnichannel | McKinsey, B2B (in inventory, SKIPPED by design as B2B-only) |
| consensus-group | multi-stakeholder B2B | Consensus-based buying / *Challenger Customer*: canon-only, UNVERIFIED |

## Hallucination guard
Evidence-backed: objection counts, desire / trust signal clusters, awareness stage inferred from phrasing, trust gaps from review themes.
Not allowed: a buyer's daily routine, an unobserved buying moment, spend allocation from text, demographics not in the data. These go in `primary_research_gaps` with "needs IDIs / diary studies / ethnography". Never fill a gap with a confident guess.

## Cross-Link
- Reference: `references/buyer-psychology.md`
- Desire evidence: `../../references/desire-mapping.md` (D1–D2) · offer/objection voice: `../../references/sales-voices.md` (V1–V2)
- Script: `scripts/buyer_signal_extract.py`
- Hands `buyer_psychology.json` to ALL downstream sub-skills
- Persuasion-execution frameworks live in `marketing-execution-persuasion` — link, don't re-teach

## Verification
- [ ] All 5 dimensions classified, each citing signal counts or sample phrases
- [ ] Trust mechanisms specific, not generic
- [ ] Primary-research gaps flagged; `evidence_confidence` stated (HIGH / MEDIUM / LOW)
- [ ] Canon-only / B2B-only sources labelled when used
- [ ] No fabricated buyer narrative
