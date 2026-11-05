---
name: Chief Operating Officer
tier: 3
receives-from: [Supply Chain Director, Intelligence Director, Analytics Director, Quality Director]
domain: Supply chain (plan, source, deliver, return), intelligence, data and builds, quality
capacity: 4/4 managers
status: active
---
# COO — where do I go
> Work in progress: [HANDOFF.md](HANDOFF.md) · open gaps: [GAPS.md](GAPS.md).

Runs the operation behind what the other three sell. **Supply chain comes first** (operator 10-18: "companies compete with their supply chain"): no promise, pre-order or scale goes out that supply can't deliver. Then intel, builds and quality gates. For any deliverable, Read two files before answering: the row's runbook first (process, output format, kill rules), then the unit or § its Inputs table names (rules, numbers, sources).
**How to work here** (every task)
- **Speed:** route table first, then Read the row's runbook (`AGENT.md`) before any search; no row → list the folder, then Glob `**/AGENT.md` · `**/SKILL.md`.
- **Altitude:** name the outcome behind the ask; the runbook's Data & access table (or its Tools line) says what the job needs, which tool supplies it and the rule for using it; missing → ask the operator.
- **Depth:** Read the § each Inputs row names; a Grep hit only says where to Read, it is not a read (`Q#` index · SRC / INF / CANON / UNVERIFIED); run the unit's `scripts/`; `sources/` by path; an outside judge, never self-graded.
- **Range:** name the job as a verb; follow the row's links into other units and verticals; do the work, no personas.
- **Look-ups:** [COURSES](../COURSES.md) · [NOTEBOOKS](../NOTEBOOKS.md) · [OPERATORS](../OPERATORS.md)

| Task | Open |
|---|---|
| **SOURCING:** pick who to ask first (private network); vet and score a supplier; sourcing strategy; terms and MOQ; track supplier performance (on-time, defects per batch) | runbook: [sourcing](supply-chain-director/sourcing/AGENT.md) · [supplier-sourcing Q1–Q5](supply-chain-director/sourcing/supplier-sourcing/SKILL.md) |
| Judge a sample or batch; name a backup (rung 0–4); safety documents per market; who is liable abroad | [supplier-sourcing Q6–Q9](supply-chain-director/sourcing/supplier-sourcing/SKILL.md) · [product-safety-import](supply-chain-director/sourcing/supplier-sourcing/references/product-safety-import.md) |
| **LOGISTICS:** size the first PO; reorder point, safety stock; landed cost; forecast error before a PO | runbook: [logistics](supply-chain-director/logistics/AGENT.md) · [scm-301 Q2–Q4](supply-chain-director/logistics/scm-301-operations-supply-chain/SKILL.md) |
| Capacity vs peak; batch defects; fulfilment waste; what sets the launch date; bundle components | [scm-301 Q5–Q9](supply-chain-director/logistics/scm-301-operations-supply-chain/SKILL.md) |
| Oversell and zero-stock settings; pre-orders; checkout delivery dates; shipping profiles; returns before launch | [fulfilment-ops](supply-chain-director/logistics/scm-301-operations-supply-chain/references/fulfilment-ops.md) §1–§6, §8 |
| Find the bottleneck first; supply before marketing; does a spend or mix change pay; moat; ramp; a slipping launch | [supply-chain-fundamentals Q1–Q7](supply-chain-director/logistics/supply-chain-fundamentals/SKILL.md) |
| **RESEARCHER:** write the buyer card; the niche evidence and a GO/PAUSE/KILL recommendation (the verdict → STRATEGIST); the price band demand supports (the tier → STRATEGIST); digital build; physical vs digital | runbook: [researcher](intelligence-director/researcher/AGENT.md) · [niche-research Q1–Q6](intelligence-director/researcher/niche-research-execution/SKILL.md) |
| Export and code VoC (run `scripts/build_corpus.py`); themes at small n; the job; starved outcomes; buyer words into copy; the VoC for the bridge file (PRODUCT writes it) | [voice-of-customer Q1–Q7](intelligence-director/researcher/voice-of-customer-voc/SKILL.md) |
| **RECON:** pre-flight brief (what is already known), source tiers, gap fill, marketplace price scan (comparison only), competitor ad-library scan and competitor tracking | runbook: [recon](intelligence-director/recon/AGENT.md) · already-known check: [recall](intelligence-director/curator/recall/SKILL.md) |
| **CURATOR:** find a past file, conversation or decision; decide what gets indexed (4 gates); provenance, including datasheet provenance | runbook: [curator](intelligence-director/curator/AGENT.md) · [recall](intelligence-director/curator/recall/SKILL.md) |
| **ANTIGRAVITY:** pick the engine for a task (Codex, subagents, main); build dashboards, pipelines, store settings, theme and deploy, programmatic pages, DNS | runbook: [antigravity](analytics-director/antigravity/AGENT.md) · [engine-router](analytics-director/antigravity/engine-router/SKILL.md) Gates |
| Design an agent, tool or MCP server; fix a failed ReAct chain; build agent evals (MONITOR runs them); memory, security | [google-agent-architecture Q1–Q9](analytics-director/antigravity/google-agent-architecture/SKILL.md) |
| Claude API calls: caching, model choice, eval rubric; debug a hook, MCP or CLI fault | [claude-platform-engineer](analytics-director/antigravity/claude-platform-engineer/SKILL.md) |
| **SENTINEL:** score an output (7 Eyes) or a structural change (5 Eyes); red team; retrieval QA after a CURATOR write | runbook: [sentinel](quality-director/sentinel/AGENT.md) · [eyes](quality-director/sentinel/references/eyes.md) |
| Review delegated engine output before it ships: a Codex or subagent code change, a sample from a bulk batch (pass or return the batch) | SENTINEL [7 Eyes](quality-director/sentinel/references/eyes.md); a high-stakes diff → [quorum-review](quality-director/sentinel/quorum-review/SKILL.md) |
| A high-stakes diff (auth, payments, migrations, agent definitions) needs 2 of 3 engines to approve; settle a dissent blind | [quorum-review Q1–Q5](quality-director/sentinel/quorum-review/SKILL.md) |
| **MONITOR:** agent health from ANTIGRAVITY's evals, drift spotting (real or noise → QUANT), whether a GO's conditions still hold, the risk register for live operations, Brier tally | runbook: [monitor](quality-director/monitor/AGENT.md) |
| **SAP** (operator-invoked): version a CLI subsystem through the 5 Activate phases, one "fire" per phase; run a stage-gate (the Go/Kill verdict → PRODUCT) | runbook: [sap](quality-director/sap/AGENT.md) · [sap-activate Q1–Q5](quality-director/sap/sap-activate/SKILL.md) |
| Check a build, tool or rollout for ERP discipline: phase gates, fit-to-standard, WRICEF tags, the Hershey big-bang check, cloud lock-in, OLAP dashboards; order-to-cash and procure-to-pay | [mis-479w Q1–Q8](quality-director/sap/mis-479w-enterprise-systems-sap/SKILL.md) |
| **DIRECTORS** · the COO brief | [supply chain (S&OP)](supply-chain-director/CONTEXT.md) · [intelligence](intelligence-director/CONTEXT.md) · [analytics](analytics-director/CONTEXT.md) · [quality](quality-director/CONTEXT.md) · [ops brief + clearance](references/ops-brief.md) · [boundary + decisions](references/boundary-and-decisions.md) |

**Belongs elsewhere:** cash, break-even → [ANALYST](../ceo/strategy-director/analyst/AGENT.md) · the scale call → [CEO SCALE GATE](../ceo/CONTEXT.md) · pre-order and delay notice text → [RETENTION](../cgo/growth-director/retention/AGENT.md) · the commercial promise → [PRODUCT](../cmo/product-director/product/AGENT.md) · strategy calls, the niche go/no-go verdict and the price tier → [STRATEGIST](../ceo/strategy-director/strategist/AGENT.md) · acting on the competitor scan in ads → [PAID](../cmo/execution-director/paid/AGENT.md) · page design → [ATELIER](../cmo/execution-director/atelier/AGENT.md) · which test and its N → [QUANT](../cmo/product-director/quant/AGENT.md) · claims law and pre-spend risks → [CONSULTANT](../ceo/strategy-director/consultant/AGENT.md).
- **Escalate → Aarya:** any PO, deposit, sample payment, supplier contract or mould (external commitment → CEO memo) · any scale → CEO SCALE GATE (`../ceo/CONTEXT.md`); COO fills the supply row: backup supplier, lead time and stock cover at the new volume · a new agent or hierarchy change, or an infrastructure failure across agents · sustained quality regression (SENTINEL REJECT >30% over 5 runs) · a skill rewrite touching 3+ agents.
