---
name: mece-frameworks
description: >-
  Build an issue tree, or check a list, segmentation or taxonomy for overlaps and gaps: revenue/ROAS/retention-drop trees, audience segments, categories, grouping reasons into three, SENTINEL Eye 2 domain checks. Triggers: is this MECE, issue tree.
version: 1.1.0
author: Aarya Godghate
created: 2026-03-11
risk: safe
source: custom
---

# MECE Frameworks — build and validate

Canon-only (method). The MECE definition lives in `mbb-strategic-frameworks`. Sourced practice: `references/mckinsey-way-mece-frameworks.md` (the one home of M02, M03, M15; M16 lives in `minto-pyramid-principle`; the master `mbb-strategic-frameworks/references/mckinsey-way.md` indexes them). Where this file and that reference disagree, the reference wins.

## Q index
| Question | Open |
|---|---|
| Q1. Build an issue tree for a question (one split dimension, 2–5 siblings) | § Build |
| Q2. Is this list, segmentation, taxonomy or tree MECE? | § Validation gate |
| Q3. Merge or re-split a branch? A branch under 5% merges into its nearest sibling; "Other" over 20% re-splits one level higher | § Validation gate (split/combine thresholds) |
| Q4. Which McKinsey rules apply (MECE, issue tree, 3–5, three)? | § Sourced rules · [entries](references/mckinsey-way-mece-frameworks.md) |
| Q5. Check a hierarchy change for overlaps (SENTINEL Eye 2) | § Routing and gates |

## Sourced rules (The McKinsey Way)
- **M02 MECE:** top-line issues must be ME and CE. "Other Issues" is allowed at lower levels only, never on the top line.
- **M03 Issue tree:** IH or top-line problem → actionable recommendations → sub-issues → the analyses that prove or disprove each. A leaf that isn't actionable or testable fails ("pray for good weather").
- **M15 Three-to-five:** 2–5 top-line items, 3 best (FV). Outliers go to sub-issues.
- **M16 Three:** don't force three when there are fewer than 2 or more than 5 real items; forcing it creates overlaps or gaps.

## Build (6 steps, max 3 refine loops)
1. **Governing question in one sentence** ("What are the drivers of declining ROAS?", not "how's marketing?"). If you can't write it, don't decompose yet.
2. **Pick ONE split dimension.** The 12 patterns: segment · channel · funnel stage · geography · product · function · time · revenue driver · cost structure · risk type · process step · decision type. "Why is X happening?" → revenue driver or process step. "Where do we invest?" → channel or geography. Details and nesting matrix: `references/decomposition-patterns.md`.
3. **2–5 siblings (3 best)**, plain-language names, each analysable on its own.
4. **Same-dimension test:** finish the sentence "these differ by ___" with one word. If you can't, push the off-axis items down a level.
5. **Validate** (gate below).
6. **Refine until PASS.** After 3 failed loops, re-scope the governing question; don't keep patching.

Worked check (ECOM): "Revenue decline → Meta, Checkout, Returning customers, Google" fails step 4 (channel, stage, segment mixed). Rebuild: level 1 by channel (Meta · Google · SEO · Email), level 2 by funnel stage under each. Different dimensions on different levels are fine; never on the same level.

## Validation gate
**Phase 1 — Exclusivity (each sibling pair)**
- E1 can one item sit in both? · E2 if one is removed, are its contents homeless? (if not, one subsumes the other) · E3 same dimension? · E4 any "and" relationship? · E5 can you state the boundary rule in one sentence?
- Fix: write the one-sentence boundary rule, move the item to its level, or split the category.

**Phase 2 — Exhaustiveness (the sibling set)**
- X1 name 3 real cases; does each map to exactly one branch? · X2 "Other" >20% of cases? · X3 walk each boundary; is the space between claimed? · X4 inversion: name what is NOT covered.
- Fix: add or broaden a branch. "Other" >20% means re-decompose one level higher.

**Phase 3 — Structure (whole tree)**
- S1 same dimension under each parent · S2 no branch >2 levels deeper than the shallowest · S3 every leaf is a testable hypothesis, measurable segment or action.
- Also: a single-child node gets merged or split into 2+. Depth 4 typical, 5 max; deeper means the question is too broad, so split it into several trees.

**Split/combine thresholds:** a branch <5% → merge with its nearest neighbour; "Other" >20% → re-split one level higher; vague leaf ("misc") → decompose until actionable. A category >20% of cases → split into 2–3 applies to taxonomies of cases (tags, reasons, segments), not to the 2–5 top-line branches of an issue tree (M15), where some branch always tops 20%. (Source: `references/validation-diagnostic-questions.md` "When to split vs combine".)

```
MECE VALIDATION REPORT
Structure: … | Governing question: … | Nodes: N | Depth: D
Phase 1 Exclusivity:    PASS/FAIL  [pair + E# per overlap]
Phase 2 Exhaustiveness: PASS/FAIL  [X# + fix per gap]
Phase 3 Structure:      PASS/FAIL/WARN  [S# + fix]
Verdict: VALID / NEEDS REVISION  [fixes in priority order]
```

## Fails when
- Solving during structuring: finish the tree, then analyse.
- Branch order read as priority: MECE is about coverage. Prioritise after the tree passes.
- No governing question, or a tree that doesn't answer it.
- The deepest branch shows your bias. Balance depth before you trust the tree.
- Don't use it for yes/no calls, ordered sequences (use process mapping) or number-crunching (`quantitative-analytical-toolkit`).

## Routing and gates
- **Token routing:** Claude drafts trees, rebuilds and parallel alternative trees; with nvidia-nim-mcp loaded, they go to kimi_chat or kimi_swarm. Choosing the pattern and running the validation stay with Claude. Prompt templates: `references/auto-mece-integration.md` §Kimi protocol.
- **SENTINEL Eye 2 (structural mode):** run Phases 1–2 on the change. Look for two agents claiming one domain, an agent with no manager, or a domain with no agent. A FAIL blocks delivery until fixed.
- **Templates and storage:** PageIndex tree → per-level validation → validated trees stored in Qdrant (`source: mece-templates`), retrieved at min_similarity 0.70 (without vector-search-mcp: `references/ecom-issue-trees.md`). Architecture: `references/auto-mece-integration.md`.

## References
- `references/decomposition-patterns.md`: the 12 patterns with ECOM examples, the nesting matrix and the agent → default-pattern map.
- `references/ecom-issue-trees.md`: six worked ECOM trees (ROAS, expansion, CPA, portfolio, retention, $10K budget).
- `references/validation-diagnostic-questions.md`: per-pattern diagnostics and the common-mistakes table.
- `references/auto-mece-integration.md`: PageIndex + Qdrant pipeline and the Kimi protocol (resolves hypothesis-training cold zone C-01).
- Related: `mbb-strategic-frameworks` (definition), `hypothesis-training`, `big4-operational-frameworks` (TOM layers as implicit MECE).
