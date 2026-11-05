---
name: supplier-sourcing
description: >-
  Any supplier decision: private network before marketplaces, is the supplier real and capable, scorecard, Kraljic, MOQ and terms, sample and batch quality, backup supplier, safety documents before import to US/UK/CA/AU. Triggers: supplier, MOQ, GCC.
---

# Supplier sourcing: decision layer (SOURCING, COO pass 2026-10-18)

Each question: what to decide, what evidence it needs, where the sourced detail lives. This unit points rather than copies:
- course method → `../../logistics/scm-301-operations-supply-chain/` (Q1, Q3, Q6; whole course: `../../../../COURSES.md`);
- pipeline steps → `../backup/.vault/sops/supplier-sourcing.md` and `../backup/.vault/sops/supplier-operations.md`;
- safety documents → `references/product-safety-import.md` (PSI).

**Rules:**
- Supplier identities are confidential: Supplier A/B only.
- Labels: SRC (sourced) · INF (inference or ECOM application) · CANON (textbook, not in our sources, UNVERIFIED).

## Q1. Who do we ask first?
- **Rule:** private network first (operator policy). Marketplaces (1688, AliExpress, Alibaba) are a price and spec comparison only: RECON scans, SOP Stage 1.
- **Regulated categories** (supplements, cosmetics, anything with a licence or registration): RFQ the private network AND a destination-country private-label maker, then compare documents and lead time, not only price. The operator decides (canary C4, INF).
- **Fails when:** a marketplace listing becomes the supplier by default because it answered first.

## Q2. Is this supplier real and capable?
- **Test:**
  - SOP Stage 2 checklist (business licence, factory or trading company, samples, references, communication).
  - Each cell records its evidence kind: document · sample · video · order history · claim.
- **Fails when:** "factory" claims aren't checked against a video or a third-party audit (INF); or a trading company's lead time is read as a factory's.

## Q3. How do they score?
- **Test:** SOP Stage 3 scorecard (quality · speed · reliability · price). Use LOGISTICS' landed cost (scm-301 Q3 five legs, with ANALYST's XB rates), never unit price alone.
- **Fails when:** weights are tuned after seeing the scores; price is compared ex-works against a competitor's delivered quote.

## Q4. Which sourcing strategy for this SKU?
- **Test:** scm-301 Q1 quadrant (SRC [L223–226]):
  - Routine → simplify;
  - Leverage → exploit buying power;
  - Bottleneck → secure supply;
  - Critical → partnership.
- **ECOM rule (INF):** a hero SKU with a factory-owned mould is Critical. Get mould-transfer terms and qualify a second factory before scaling ads.
- **Fails when:** quadrants are set once and never revisited after a tariff, mould or supplier change.

## Q5. What terms do we ask for?
- **Test:** SOP Stage 4 (BATNA, target terms, sequence).
  - MOQ against LOGISTICS' EOQ (scm-301 Q2): MOQ sets order size, not the reorder point.
  - Price anchoring → atlas №69 (QUANT).
- **Fails when:** a low MOQ is bought with a higher unit price that ANALYST's break-even can't carry.

## Q6. Is the sample or batch good enough?
- **Test:**
  - Written spec with a defect list.
  - scm-301 Q6 DMAIC loop (SRC); DPMO compares batches over time, never as an acceptance line.
  - Pre-shipment inspection before the balance payment (INF).
- **Gap:** acceptance sampling (AQL plan) is not in our sources. CANON, UNVERIFIED; logged in GAPS.
- **Fails when:** the first sample is approved and production is never checked against it.

## Q7. Do we need a backup supplier now?
- **Status ladder** (one scale, canary C5): 0 none · 1 identified · 2 documents verified · 3 sampling · 4 qualified (sample passed + documents + first batch).
- **Where to look:** Q1 (who we ask first) applies to the backup too.
- **Rule:** a scale needs rung 4 (CEO SCALE GATE). Critical and Bottleneck SKUs need rung 3 at all times, and rung 4 if requalification time > stock cover.
- **Warm bench:** supplier-operations SOP Stage 3 (bench slots ready to activate).
- **Test:** requalification time (sample + documents + first batch) vs stock cover from LOGISTICS. If requalification is longer than cover, the backup must be sampling now (INF).
- **Fails when:** the "backup" uses the same factory under another trading company.

## Q8. Which safety documents must the supplier provide before import?
- **Step 0, classify the category first** (canary C1): food or dietary supplement · cosmetic · drug or device · natural health product · children's product · general consumer product. PSI covers only children's and general consumer products. Any other category → NOT IN SOURCE → CONSULTANT plus its own official regulatory pack before any RFQ that names documents.
- **Test, per market** (PSI §1–§4, §7):
  - **US:** first, does a CPSC rule cover it? If not, "a GCC is likely not required" (SRC). If yes, a GCC (children's: CPC with an accepted lab) and an e-filed certificate. Mail parcels e-file from 22 Oct 2026, with no de minimis exemption.
  - **GB:** GPSR safety duty, plus producer name/address and batch on the product. UKCA/CE sector products need a technical file kept ~10 years.
  - **Canada:** CCPSA prohibitions, s.13 records kept 6 years in Canada, s.14 incident reports.
  - **Australia:** mandatory standards and bans only for high-risk products; block banned products online; serious-injury report within 2 days.
- Map each target market to its documents before the RFQ, and put them in the RFQ. A product with no clear category → CONSULTANT.
- **Fails when:** a supplier's generic "CE" or test report is accepted without checking that it covers this product and this market's rule.

## Q9. Who is legally responsible when the supplier is abroad?
- **Test:** PSI §5.
  - **US:** for direct-to-consumer parcels "the foreign firm may meet the definition of an importer" (SRC), so our store may have to certify and e-file.
  - **GB and Canada:** the importer is defined as established in the country, and Canada doesn't recognise a "non-resident importer"; the non-resident store's role is NOT IN SOURCE → CONSULTANT before launch.
  - **Australia:** anyone "in the business of supplying".
- **Fails when:** the store assumes the overseas supplier carries the legal duty.

## Not this skill
Stock, reorder, delivery promise, returns → `../../logistics/` · duty and VAT → ANALYST XB · claims law → CONSULTANT · copy → CREATIVE.
