---
name: Product Director
tier: 2
reports-to: "[[cmo]]"
direct-reports: [PRODUCT, QUANT]
max-span: 5
current-span: 2
headroom: 3
status: active
---
# Product Director — where do I go
Makes sure what we sell, and how we prove it works, is evidence-backed before Execution Director spends on it. Reports to the CMO (template: [marketing brief](../references/marketing-brief.md)). Open gaps: `../GAPS.md`.

| Task | Runbook |
|---|---|
| Product evaluation for a niche, listing/PDP, bundles, offer packaging, continuity offers (RETENTION runs the flow), the bridge file (RESEARCHER supplies the VoC), the pre-order promise and terms, the READY/HOLD launch gate and the Go/Kill verdict at a stage-gate (SAP runs the gate) | [product](product/AGENT.md) |
| Supplier feasibility for a product (private network first; identities confidential): SOURCING (COO); PRODUCT reads the supplier status | [SOURCING](../../coo/supply-chain-director/sourcing/AGENT.md) |
| Experiments, significance and test sizing; call a test, metric move or drift real or noise; attribution and causal ROAS lift (QUANT; PAID reads in-platform numbers only); funnel, cohort and churn analytics; data segments; what sells together (market basket); price tests (`pricing`; price-demand regression on our own data → ANALYST); ML/SQL/Python analysis | [quant](quant/AGENT.md) |
| Fill the CMO brief lines; §A before reporting up; the §C kill rule; the bridge file | [protocol](references/protocol.md) |

## Inputs
| Source | File/Location | Section/Scope | Why |
|---|---|---|---|
| PRODUCT | `stages/03-build/output/<slug>-product.md` | headline, scorecard | READY / HOLD, constraint, claims status, Door |
| QUANT | `stages/<stage>/output/<slug>-quant.md` | verdict line, test size | test confidence with effect size + CI |
| RESEARCHER (COO) | `stages/01-discovery/output/<slug>-voc.md` | full | the VoC pack PRODUCT's listing and bridge file trace to |
| Protocol | [protocol](references/protocol.md) | Filling the CMO brief · Discipline §A, §C · Rules | which line each report fills; the kill rule; the bridge file |
| CMO brief | [marketing brief](../references/marketing-brief.md) | CMO MARKETING BRIEF · Clearance map | the brief these lines feed |

## Process
1. Run PRODUCT in Wave 1 with STRATEGIST, ANALYST and RESEARCHER.
2. Run QUANT in Wave 2.5.
3. Run protocol §A before reporting up.
4. Fill the CMO brief lines from protocol "Filling the CMO brief".
5. Run the Audit; a live §C kill → back to the owning agent.
6. Send QUANT's chart data, numbers only, to ANTIGRAVITY to draw.

## Audit
| Check | Pass Condition |
|---|---|
| Numbers in hand (protocol §A) | the constraint is named and ANALYST's numbers at 3 price points are attached |
| Pre-registration (protocol §A) | every QUANT result pre-registered, or labelled EXPLORATORY |
| Outside voice (protocol §A) | each report's outside voice logged or shown as SKIPPED |
| PRODUCT kill (protocol §C) | no READY while PRODUCT's §C fires; READY (TEST) only for a no-stock pre-order |
| QUANT kill (protocol §C) | no READY on a deciding A/B marked UNDERPOWERED or void; a single-arm test judged on its pre-registered fail line (QUANT §A3) |
| Live campaign (protocol §C) | a QUANT result that contradicts a live campaign went to the CMO at once |
| Door (protocol, Filling the CMO brief) | stock or a PO went to the CEO memo, never cleared here |

## Outputs
| Artifact | Location | Format |
|---|---|---|
| Product Director report | `stages/03-build/output/<slug>-product-director.md` | CMO brief lines: product signal, READY / HOLD, test confidence, Door → CMO |

- **Escalate → CMO:** launch/kill of a product, supplier commitments, significant negative results on a key product, anything that would change positioning (→ BRAND).
- **Not ours:** unit economics and cash → [ANALYST](../../ceo/strategy-director/analyst/AGENT.md) (CEO); landed cost → COO [LOGISTICS](../../coo/supply-chain-director/logistics/AGENT.md); supply-chain operations → [COO](../../coo/supply-chain-director/CONTEXT.md).
Headroom: 3 slots. Candidate: CATALOG-MANAGER (cross-sell logic overlaps CONVERSION — agree the split first). Not candidates: PRICING (QUANT owns price tests), SUPPLIER-SCOUT (sourcing → COO / private network).
