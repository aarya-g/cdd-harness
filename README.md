# cdd-harness

**Commercial due diligence exists to answer one question: will this drive sales?** Everything else in a CDD — market sizing, competitive mapping, pricing analysis, customer evidence — is machinery in service of that verdict. This repo is how I run that screen solo: the way a diligence team would run it *before* committing weeks of research, plus an interactive atlas of the decision framework behind it.

The screen doesn't care what you point it at. An M&A target, a new business or niche entry, a marketing strategy, a paid-media plan, an ad-copy angle — if the underlying question is *"will this generate revenue, and is the claim honest?"*, it goes through the same spine and comes out with the same verdict discipline.

This is the layer McKinsey's diligence practice calls **outside-in**: forming the commercial view from public evidence before anyone opens a data room ([their gen-AI diligence work](https://www.mckinsey.com/capabilities/transformation/our-insights/from-potential-to-performance-using-gen-ai-to-conduct-outside-in-diligence) names exactly this screen). Their value-creation research holds that in many industries a point of revenue growth is worth more than a point of margin. Sales first is not a simplification of CDD; it *is* CDD.

> Scope, honestly: this is the **desk layer**, not a full CDD engagement. Real commercial due diligence takes weeks because most of it is primary research (data rooms, management interviews, customer surveys) — no model one-shots that. This harness owns the fast kill-screen that decides what is *worth* researching.

## How I actually run a screen

The method matters more than the tooling, so it goes first. Every screen is a division of labor between me and the machine, and the split is deliberate.

**The consulting work is mine, and it happens before any AI is involved.** Problem awareness first: what decision is this screen actually feeding, and what would change my mind? Then the structure — a MECE issue tree of key drivers, falsifiable hypotheses per branch, and an 80/20 cut so the screen attacks the two or three drivers that decide the verdict instead of boiling the ocean. AI cannot own this part. Framing the problem, choosing what *not* to analyze, and knowing what "good" looks like in a market read are domain-expertise work — delegate them and you get confident nonsense with a bibliography.

**Then I describe, and let the AI build on the frame — augmentation.** The issue tree, the hypotheses, the buyer definition, the output format and the register all get communicated up front; the agents then do what they're genuinely better at — sweeping public evidence at breadth, drafting market structure, pulling pricing signals, stress-testing a hypothesis from angles I didn't think to try. Thinking partners, iterating — not an oracle answering once.

**Then discernment, and the loop.** Every output gets judged three ways: the product (is it accurate, relevant, sourced), the process (did it *reason* its way there, or land somewhere plausible by luck), and the collaboration itself (is the back-and-forth still sharpening the answer). What fails gets re-described and re-run. The screen converges by loop, not by one-shot.

**Diligence closes it.** Nothing ships on the model's word. Every claim that survives to a verdict is verified against its source, and I vouch for what goes out — my name on the screen, not the AI's.

Around that loop sits one standing question: **what's automated, what's augmented, what's agentic.** Mechanical, verifiable steps get automated. Judgment-adjacent work is augmented. And work that has earned trust runs agentic — configured once, running 24/7 on my behalf — but always behind a hard gate: an agent can propose, flag, and prepare; the commercial verdict and anything customer-facing waits for my approval.

One distinction does most of the remaining work: a knowledge synthesis (what was read, how strongly sources corroborate) is the **evidence shelf** — supply-side. The **frame** is demand-side: it stands on the actual decision, states the problem, and pulls evidence per question. Confusing the map of what you know with the structure of the problem is how analysis drifts into inventory.

## The framework

Every screen runs on a 6-phase spine:

`Diagnose` (is the problem real, acute, funded?) → `Size` (big enough to live on, small enough to own?) → `Price` (what will the acute buyer pay?) → `Position` (what one slot do we own?) → `Capture` (reach the buyer at zero ad spend?) → `Measure` (stay honest about what worked?)

Each operator gets one of five verdicts: **KEEP** (transfers as-is), **ADAPT** (keep the reasoning, drop the apparatus), **SWITCH** (discarded now, flips to leverage on a named trigger), **DISCARD** (sample- or spend-bound, no honest substitute), **FLAG** (proprietary or unverified, reconstruct the principle but never the hidden mechanics).

The decision atlas (`index.html`) maps 108 consulting operators (frameworks from McKinsey, Porter, Kano, Van Westendorp, and others) onto that spine — each owned by where a consultant reaches for it and whether it survives at small scale. Filterable by phase, domain, and verdict; deep-linkable per operator.

## Who runs the screen — the agent bench

Every operator in the atlas has exactly one owning specialist agent — an owner-map, not a
free-for-all. The bench mirrors how a diligence team actually staffs: a **STRATEGIST** owns
market-entry and positioning operators, a **QUANT** owns pricing and modeling, an **ANALYST**
owns scorecards and causal reads, a **RESEARCHER** owns jobs-to-be-done and voice-of-customer,
a **CONVERSION** specialist owns the sales-methodology operators, **SEO/ACQUISITION** own
zero-spend capture, and **PAID** owns the media-buying operators (mostly to rule spend *out*
until a named trigger flips it). Nineteen specialists in all, reporting through directors to a
C-suite tier.

The tiering isn't decoration — it's how a verdict stays readable. A non-trivial screen rolls up
a reporting vertical: the specialist leads with full mechanism, a director reframes it as scope
and risk in plain language, and the C-suite line states what it means for the business — the
same answer, legible to an engineer and to a founder, with the register shifting per tier.

## After the screen: what the verdict unlocks

The screen isn't the end product — it's the base layer. Every operation downstream inherits its targets from the CDD verdict, which is what makes automating them meaningful instead of merely busy:

- **Marketing campaigns and analytics** — automated end-to-end, with agents doing the first-pass verification, but hard-gated: nothing spends or publishes without my approval.
- **Customer data** — augmented: segmented against the *current* operation's goals and challenges, not a static taxonomy.
- **Buyer personas** — living documents that keep evolving as buyer evidence accumulates, instead of a slide frozen at launch.
- **Customer service** — agentic, defending the exact promise the screen validated.

Automate before the verdict and you're automating guesses. The screen earns the right to run the rest 24/7.

## Under the hood

The engineering exists for one purpose: **know the AI's strengths and limitations, then lower the limitations and raise the strengths** — so the augmentation stays honest and the agentic layer can be trusted with more over time. In practice that means retrieval that grounds every screen in prior intel rather than cold starts; write-time gates that machine-check what consultants are actually paid for (every quantified claim carries a citation signal, every document declares whether it's source-fact, interpretation, or synthesis, dead links and portable filler get flagged); and a self-improvement loop that proposes changes to the system's own memory nightly — with a guard that catches not just deleted facts but meaning-inversions (a dropped "never", a swapped direction), because the proposer is never allowed to judge its own proposal. Every gate was built exam-first: known-good and known-bad fixtures written before the checker, and the fixtures stay in the suite as regression contracts.

I specify what gets built, how it should work, and what counts as done; the agents write the code against that spec, and I review and validate every output. This repo is the public, sanitized slice of a larger private system — the tools are described by role because the point of the tool layer is grounding, not autonomy. The harness is exactly as good as the operator commanding it.

## Honesty boundaries

The atlas was citation-audited (40 of 46 source claims verified against primaries, zero fabricated). Operators that rest on proprietary or unverified mechanics are tagged FLAG and withhold the mechanics by design. No client, sourcing, financial, or private business data appears anywhere in this repo. AI's role in this work is stated plainly: agents execute and draft; the frames, verdicts, and everything shipped carry my judgment and my accountability.

Working method shaped in part by Anthropic's AI Fluency framework (Rick Dakan, Joseph Feller & Anthropic, CC BY-NC-SA 4.0).

## Auditable, not self-scored

This harness is built to be graded by an independent tool rather than self-attested. Audit it yourself: [Dallionking/claude-harness-audit](https://github.com/Dallionking/claude-harness-audit) (MIT, local-only) — install it and run `/harness-audit` against a harness to get a findings + benchmark report.

## Live atlas

Explore the interactive decision atlas: **https://cdd-atlas.vercel.app** — filter 108 operators by phase, domain, and verdict; deep-link any operator.
