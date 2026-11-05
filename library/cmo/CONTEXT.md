---
name: Chief Marketing Officer
tier: 3
receives-from: [Product Director, Execution Director]
domain: Marketing execution — product listing and offer, creative, paid media, search, design, marketing measurement
capacity: 2/4 managers
status: active
---
# CMO — where do I go
> Pass history (vertical closed 2026-10-14): [HANDOFF.md](HANDOFF.md) · open gaps: [GAPS.md](GAPS.md).

Turns CEO direction and BRAND's positioning into market-facing execution: the product as listed and offered, the creative, the media, search and the measurement that says what worked. Two managers: Product Director (PRODUCT, QUANT) and Execution Director (CREATIVE, PAID, SEO, ATELIER). For any deliverable, Read two files before answering: the row's runbook first (process, output format, kill rules), then the unit or § its Inputs table names (rules, numbers, sources).
**How to work here** (every task)
- **Speed:** route table first, then Read the row's runbook (`AGENT.md`) before any search; no row → list the folder, then Glob `**/AGENT.md` · `**/SKILL.md`.
- **Altitude:** name the outcome behind the ask; the runbook's Data & access table (or its Tools line) says what the job needs, which tool supplies it and the rule for using it; missing → ask the operator.
- **Depth:** Read the § each Inputs row names; a Grep hit only says where to Read, it is not a read (`Q#` index · SRC / INF / CANON / UNVERIFIED); run the unit's `scripts/`; `sources/` by path; an outside judge, never self-graded.
- **Range:** name the job as a verb; follow the row's links into other units and verticals; do the work, no personas.
- **Look-ups:** [COURSES](../COURSES.md) · [NOTEBOOKS](../NOTEBOOKS.md) · [OPERATORS](../OPERATORS.md)

| Task | Open |
|---|---|
| **PRODUCT:** pick the product for a chosen niche; build the offer stack, bundles, guarantee, continuity offers (RETENTION runs the flow); write the listing and the bridge file (RESEARCHER supplies the VoC); set the pre-order promise and terms; call READY / HOLD and the Go/Kill at a stage-gate (SAP runs the gate; supplier feasibility → SOURCING, COO) | runbook: [product](product-director/product/AGENT.md) · [money-models](product-director/product/references/money-models.md) · [bridge template](product-director/product/references/product-marketing-template.md) |
| **QUANT** | runbook: [quant](product-director/quant/AGENT.md) |
| Call a test, metric move or drift real or noise; size a test (N per arm, orders before calling); a pre-order or single-arm test; peeking; price test on profit; causal ROAS lift | [statistical-reasoning](product-director/quant/statistical-reasoning/SKILL.md) · [quant doctrine §A3 (single-arm payment check)](product-director/quant/references/doctrine.md) |
| Frame a data question: which task type (classify, cluster, associate), which method at small n, how many segments, what sells together, does it beat a do-nothing baseline | [mis-441 Q1–Q7](product-director/quant/mis-441-business-analytics-ml/SKILL.md) |
| Before building or trusting a model on our store data: worth it at our row count; label and grain; leakage (AUC too high); propensity, churn or LTV go/no-go; model card | [crisp-dm Q1–Q6](product-director/quant/crisp-dm-ml-bridge/SKILL.md) |
| Query orders and ad tables: funnel leak, cost per order by campaign, cohorts and repeat, top-N per group | [sql](product-director/quant/data-querying-sql/SKILL.md) |
| Clean and join exports in Python; what each week of spend bought; forecast orders (BFCM) | [python](product-director/quant/python-marketing-analytics/SKILL.md) |
| **CREATIVE** | runbook: [creative](execution-director/creative/AGENT.md) |
| Write the headline, hook, body, video script; write the words of the offer, guarantee and urgency (BRAND sets what is promised); check the ad's claims and attributes against Meta's bar (creative doctrine §A5); check copy is ready to spend on | [persuasion](execution-director/creative/marketing-execution-persuasion/SKILL.md) |
| Choose the visual concept (ATELIER owns the asset's design and page build), write image/video prompts, score creative before spend (run its `scripts/`) | [genai](execution-director/creative/brand-creative-genai/SKILL.md) |
| **PAID:** set a test's budget (N and significance from QUANT); structure Meta; set daily budget; kill, hold or scale an ad set; Google bidding, PMax; tracking; cross-channel mix (paid vs search, boosting organic posts); account and launch review (rejected ads, account health) | runbook: [paid](execution-director/paid/AGENT.md) · [paid-media](execution-director/paid/paid-media-playbooks/SKILL.md) |
| **SEO:** judge a link offer or link spam; decide which links are worth earning, HARO and digital PR included (the outreach → ACQUISITION); product-page SEO; read a traffic drop; AI Overviews; hreflang | runbook: [seo](execution-director/seo/AGENT.md) · [links](execution-director/seo/link-building-outreach/SKILL.md) |
| **ATELIER:** design the store or a page; the design and page build of a visual asset (CREATIVE sets the concept); checkout and trust; speed and accessibility | runbook: [atelier](execution-director/atelier/AGENT.md) · [store-design](execution-director/atelier/references/store-design.md) |
| **DIRECTORS** · the CMO brief | [product-director](product-director/CONTEXT.md) · [execution-director](execution-director/CONTEXT.md) · [marketing brief + clearance](references/marketing-brief.md) · [boundary + decisions](references/boundary-and-decisions.md) |

**Belongs elsewhere:** desire, positioning, voice, naming → [BRAND](../ceo/strategy-director/brand/AGENT.md) · unit economics, cash, cross-border cost → [ANALYST](../ceo/strategy-director/analyst/AGENT.md) · claims law → [CONSULTANT](../ceo/strategy-director/consultant/AGENT.md) · entry/exit, scale → [CEO](../ceo/CONTEXT.md) · non-search organic, community, outreach to creators and for links → [ACQUISITION](../cgo/growth-director/acquisition/AGENT.md) · competitor ad scans → [RECON](../coo/intelligence-director/recon/AGENT.md) · landing-page CRO → [CONVERSION](../cgo/growth-director/conversion/AGENT.md) · email/SMS programs → [RETENTION](../cgo/growth-director/retention/AGENT.md) · niche research, VoC → [RESEARCHER](../coo/intelligence-director/researcher/AGENT.md) · builds, pipelines, dashboards → [ANTIGRAVITY](../coo/analytics-director/antigravity/AGENT.md) · supply chain → [COO](../coo/supply-chain-director/CONTEXT.md).
- **Escalate → Aarya:** spend above the approved threshold · any SCALE beyond the approved budget or needing stock → CEO SCALE GATE (`../ceo/CONTEXT.md`; PAID SCALE is one of its six inputs) · a change to positioning (→ CEO/BRAND first) · conflict with CGO · launch-timing disputes · anything touching legal, claims or compliance (CONSULTANT and the cross-border reference first) · QUANT results that contradict a live campaign · any one-way door (stock, PO) → CEO memo.
