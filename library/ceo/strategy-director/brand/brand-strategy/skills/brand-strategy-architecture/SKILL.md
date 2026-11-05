---
name: brand-strategy-architecture
description: >
  Choose brand architecture for a multi-product or multi-brand portfolio
  (branded house, sub-brands, endorsed, house of brands) and migration;
  skip for one product. Use for "brand architecture", "brand portfolio",
  "sub-brand", "endorsed brand", "house of brands",
  `/brand-strategy architecture`.
allowed-tools:
  - Read
  - Write
  - Bash
---

# Brand Strategy Architecture — Portfolio Structure

How a company's brands relate. Errors compound for years, so settle it before the next product launches.
**Skip rule:** one product and no expansion plan → skip this sub-skill.
**Sources:** pack `../../sources/brand-research-methods-2026-10/` (`_urls.md`; page 03 = the brand relationship spectrum, page 08 = a branded-house governance policy; lake L1, gaps G1) via `../../references/brand-architecture.md`. Labels: SRC (page + section) · INF (house rule) · CANON (book, not fetched). The page wins over the lake.

**Input:** brand brief + portfolio inventory (products, brands, sub-brands) · `positioning.json` per brand if available · expansion plans.
**Process:** inventory → decision tree → `scripts/architecture_recommend.py` → migration plan if the structure is broken → emit.

## Output — `architecture.json`
```json
{
  "current_structure": "describe current state",
  "recommended_type": "endorsed",
  "rationale": "...",
  "naming_convention": "how products should be named under this type",
  "endorsement_strength": "strong | linked | token | n/a",
  "migration_plan": ["ordered steps if structure is changing"],
  "risk_notes": ["..."]
}
```

## Decision tree (INF house rule on the four SRC strategies; brand-architecture §1–§2, encoded in the script)
```
Same buyer, same decision driver?
├── YES → can one brand credibly cover all?  YES → BRANDED HOUSE · NO (needs a stretch) → SUB-BRANDS
└── NO  → do products benefit from parent trust?  YES → ENDORSED · NO (or risk isolation needed) → HOUSE OF BRANDS
```
**SRC 03:** "four basic strategies which feed into nine sub-strategies": house of brands (not connected · shadow endorser) · endorsed brands (token endorsement · linked name · strong endorsement) · sub-brands (co-driver · master brand as driver) · branded house (different identity · same identity). The page gives no use-when test: the YES/NO questions above are ours.

## Rules
- **Cost / risk** (brand-architecture §5, INF): branded house is cheapest but one scandal hits everything; house of brands is most expensive (every brand built from zero) but risk-isolated; endorsed is the middle ground, most common for growing portfolios.
- **Endorsement strength** (brand-architecture §3; definitions SRC 03, use-when INF): strong (endorser is part of the name and identity: Courtyard by Marriott) · linked name (a shared name element: McMuffin via "Mc") · token (a small parent mark: Universal Pictures, A Sony Company). Shadow endorser is a house-of-brands sub-strategy (Toyota → Lexus), not an endorsement strength.
- **Migration** (brand-architecture §4, INF; NOT IN SOURCE beyond SRC 03: strategies combine, and "too many, too few or the entirely wrong" ones "prove highly ineffective"): sequence over quarters, never big-bang; order moves to minimise equity loss; never strand a high-equity brand without a bridge; tell existing customers.
- **Governance** (SRC 08 §4.9–§4.10): in a branded house, a new sub-brand needs a business case and approval before launch; hand that rule to `book`.

## Cross-Link
- Reference: `references/brand-architecture.md`
- Script: `scripts/architecture_recommend.py`
- Hands `architecture.json` to `book` and `naming`

## Verification
- [ ] Portfolio inventoried
- [ ] Type chosen via the decision tree, rationale stated
- [ ] Naming convention specified for the chosen type
- [ ] If endorsed, endorsement strength set
- [ ] Migration ordered to minimise equity loss (if structure changing); risk notes documented

