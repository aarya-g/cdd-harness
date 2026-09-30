# cdd-harness

Commercial due diligence (CDD) answers one question: will this drive sales? Market sizing, competitor maps, pricing work and customer evidence all feed that answer. This repo is how I run that first screen on my own, before anyone commits weeks to research. It also includes an interactive atlas of the framework behind it.

The screen works on more than acquisitions. I use it on new businesses and niches, marketing strategies, paid-media plans and ad angles. If the question is "will this make money, and is the claim honest?", it goes through the same steps.

McKinsey calls this layer **outside-in** diligence: forming a commercial view from public evidence before anyone opens a data room ([their article on doing it with gen AI](https://www.mckinsey.com/capabilities/transformation/our-insights/from-potential-to-performance-using-gen-ai-to-conduct-outside-in-diligence)). Their research also finds that in many industries a point of revenue growth is worth more than a point of margin. That is why the screen starts with sales.

> Scope: this is the desk layer, not a full CDD. A real engagement takes weeks because most of it is primary research: data rooms, management interviews and customer surveys. This harness does the fast first cut that decides what is worth researching.

## How I run a screen

I split the work between me and the AI on purpose.

**I do the framing myself, before any AI is involved.** I start with the decision the screen feeds and what would change my mind. Then I build an issue tree of the key drivers, write a testable hypothesis for each branch, and pick the two or three drivers that decide the answer. Framing, choosing what to leave out and knowing what a good market looks like need domain judgement, so I keep them.

**Then the agents build on that frame.** I hand over the issue tree, the hypotheses, the buyer definition and the output format. The agents do what they are faster at: reading public evidence widely, drafting the market structure, pulling pricing signals and testing a hypothesis from angles I missed. We go back and forth; I don't take one answer and stop.

**Then I review and loop.** I check each output three ways: is it accurate and sourced, did it reason its way there, and is the back-and-forth still improving the answer. Anything that fails gets re-briefed and re-run.

**Nothing ships on the model's word.** I check every claim that reaches a verdict against its source, and my name goes on the result.

I also sort each task into one of three modes. Mechanical steps that are easy to check are automated. Judgement-heavy work is augmented, with me in the loop. Work that has earned trust runs as an agent on its own, but behind a hard gate: an agent can propose, flag and prepare, and the verdict and anything a customer sees wait for my approval.

One distinction matters a lot. A summary of what I have read is the **evidence shelf**. The **frame** starts from the decision and pulls evidence question by question. Mixing the two up turns analysis into an inventory of facts.

## The framework

Every screen runs through six phases:

`Diagnose` (is the problem real, urgent and funded?) → `Size` (big enough to live on, small enough to own?) → `Price` (what will the urgent buyer pay?) → `Position` (which one slot do we own?) → `Capture` (can we reach the buyer with no ad spend?) → `Measure` (how do we stay honest about what worked?)

Each method (I call them operators) gets one of five verdicts:
- **KEEP**: works as it is.
- **ADAPT**: keep the reasoning, drop the heavy process.
- **SWITCH**: skip it for now, and use it once a named trigger happens.
- **DISCARD**: needs a sample size or budget we don't have, with no honest substitute.
- **FLAG**: proprietary or unverified. I use the principle and never guess the hidden parts.

The decision atlas (`index.html`) maps 109 operators onto those six phases. 108 come from the consulting literature (McKinsey, Porter, Kano, Van Westendorp and others). For each one it records where a consultant uses it and whether it still works at small scale. The last one is my own. You can filter by phase, domain and verdict, and link to any operator.

**№109, the brand-efficiency delta, is the one I came up with in the field.** Score how it feels to do a job the old way and your way, from 1 to 10. A street cab might be a 3 and an Uber a 7 or 8. Brand strength is the gap between the two, not either score. My working hypothesis, which is testable and not proven, is that at a gap of about 4 or more, three things happen:
- people don't switch back, because the old way now feels like a loss;
- customers forgive a slip in performance, though not a betrayal;
- people talk about it unprompted, because telling others makes them look good.

I call that last one a **UBP, a unique brag-worthy proposition**. It is a sharper signal than NPS: people brag without being asked, while a recommendation has to be requested.

## Who runs the screen

Every operator in the atlas has one owning specialist agent, so nothing is owned by everyone. The setup mirrors how a diligence team is staffed:
- a **STRATEGIST** owns market entry and positioning;
- a **QUANT** owns pricing and modelling;
- an **ANALYST** owns scorecards and cause-and-effect reads;
- a **RESEARCHER** owns jobs-to-be-done and customer voice;
- a **CONVERSION** specialist owns sales methods;
- **SEO** and **ACQUISITION** own reaching buyers without ads;
- **PAID** owns media buying, mostly to rule spend out until a trigger says otherwise.

There are nineteen specialists in all, reporting through directors to a C-suite layer. The layers keep a verdict readable. The specialist gives the full detail, a director restates it as scope and risk in plain language, and the C-suite line says what it means for the business. It is the same answer, pitched for an engineer and for a founder.

## After the screen

The screen is the base layer. Everything after it takes its targets from the verdict, which is why automating it is worth doing:
- **Marketing campaigns and analytics**: automated end to end, with agents doing the first checks. Nothing spends or publishes without my approval.
- **Customer data**: segmented against what the business is trying to do now, not a fixed list.
- **Buyer personas**: kept up to date as new buyer evidence comes in.
- **Customer service**: run by agents, holding to the promise the screen validated.

Automating before the verdict means automating guesses.

The loop closes in the Measure phase, where the brand-efficiency delta (№109) becomes the metric to track. You see it in where sales come from: unprompted mentions, referral share, organic and direct share, and a price premium that holds. Those tell you whether the brand is growing and whether the original verdict was right. When survey scores and buying behaviour disagree, trust the behaviour.

## Under the hood

The engineering has one job: know where the AI is strong and where it is weak, and push both in the right direction. In practice that means:
- **Retrieval:** every screen starts from past research, not from scratch.
- **Checks on every write:**
  - every number needs a source;
  - every document says whether it is a sourced fact, an interpretation or a synthesis;
  - dead links and generic filler get flagged.
- **A nightly self-review:** the system proposes changes to its own memory. A separate check catches deleted facts and reversed meanings, like a dropped "never" or a flipped direction. The part that proposes a change never approves it.
- **Tests first:** I wrote good and bad test cases before each checker, and they stay in the suite so old bugs can't come back.

I decide what gets built, how it should work and what counts as done. The agents write the code to that spec, and I review every output. This repo is the public, cleaned-up part of a larger private system. The tools are described by role, because their job is to keep the work grounded in evidence.

## Honesty boundaries

I audited the atlas citations: 40 of 46 source claims checked against the original sources, none made up. Operators that rest on proprietary or unverified methods are tagged FLAG and leave those parts out. There is no client, supplier, financial or private business data in this repo. The agents run tasks and write drafts. The frames, the verdicts and anything that ships are my judgement and my responsibility.

My working method draws on Anthropic's AI Fluency framework (Rick Dakan, Joseph Feller and Anthropic, CC BY-NC-SA 4.0).

## Audit it yourself

You can grade this harness with an independent tool instead of taking my word for it: [Dallionking/claude-harness-audit](https://github.com/Dallionking/claude-harness-audit) (MIT, runs locally). Install it and run `/harness-audit` to get a findings and benchmark report.

## Live atlas

The interactive decision atlas is at **https://cdd-atlas.vercel.app**. Filter the 109 operators by phase, domain and verdict, or link straight to one.
