---
name: python-marketing-analytics
description: >-
  QUANT answers store questions in Python from Shopify, Meta, Google Ads or GA4 exports: cleaning and joins, blended CPA, cohorts, test readouts, order/BFCM forecasts, segments, repeat-purchase models. Pipelines to ANTIGRAVITY; scraping to RECON.
---

# Python marketing analytics: store questions answered from exports

QUANT's Python layer for a small DTC store: hundreds to low thousands of orders, not 100K rows. Each question gives **the method, a worked ECOM check, what makes it fail, and the code** in `references/` (§ below).

## Reading rule
1. **Sources:** QUANT pack `../data-querying-sql/sources/data-measurement-2026-10/` (`_urls.md`: Shopify order export `pages/14`, PAID's Meta/Google attribution pages, SCM 421 data-cleaning and forecasting originals, SCM 301 forecasting; cross-checks `lakes/A1-L1`, `A1-L3`). A rule a page states is SRC (the page wins over the notebook). Methods and library calls stay CANON (standard pandas, statsmodels, scikit-learn, Prophet: no library docs in the pack). Library behaviour marked "checked" was run against pandas 3.0, statsmodels 0.15 and the Prophet 1.5.0 source on 2026-10-11.
2. **Worked checks:** [data-querying-sql](../data-querying-sql/SKILL.md) reading rule 2 applies here too (its one home).
3. **Export columns:** Shopify order export SRC `pages/14-shopify-exporting-orders.md` § Order export CSV structure; Meta and Google Ads export columns are UNVERIFIED (no page; `lakes/A1-G1-gap.md` (1)). Print `df.columns.tolist()` first and rename to the names the references use.
4. **Fails-when lines are INF** unless they quote checked library behaviour.

**Operator context:** India-based solo founder · Shopify DTC into US/UK/CA/AU · Meta primary, Google secondary · GA4 · China suppliers (ship time shows up as fulfilment days).

**Files:** `references/pandas-data-prep.md` (§1 setup and delegating a build · §2 read · §3 inspect · §4 filter · §5 clean · §6 aggregate and join · §7 new columns · §8 habits · §9 troubleshooting · §10 cheat sheet) · `references/cohort-segmentation.md` (§1 repeat cohorts · §2 RFM inputs · §3 k-means · fails-when list) · `references/models-tests-forecasts.md` (§1 z-test · §2 repeat propensity · §3 orders vs spend · §4 Prophet · §5 decomposition · §6 versioning).

## Owned elsewhere (pointers, not copies)
- Charts and dashboards → ANTIGRAVITY `../../../../coo/analytics-director/antigravity/AGENT.md`: numbers stay in QUANT, visuals go to ANTIGRAVITY.
- Production pipelines, schedulers, emailed reports → ANTIGRAVITY (same file).
- API pulls: HubSpot, Google Ads, Google Sheets → ANTIGRAVITY (same file).
- Web scraping and competitor monitoring → RECON `../../../../coo/intelligence-director/recon/AGENT.md`.
- Unit economics, ROAS as profit, LTV:CAC, cohort P&L, RFM segment actions → ANALYST `../../../../ceo/strategy-director/analyst/quantitative-analytical-toolkit/SKILL.md` §2, §12, §13.
- Significance, power, sample size → `../statistical-reasoning/SKILL.md` · ML process and leakage → `../crisp-dm-ml-bridge/SKILL.md` · algorithm choice → `../mis-441-business-analytics-ml/SKILL.md` · the same questions in SQL → `../data-querying-sql/SKILL.md`.

---

## Decision layer

### Q1. Are the Shopify and ad exports clean enough to trust?
**Method (CANON).** Inspect before computing: rows vs unique order names, dtypes, nulls, `value_counts()` on status, currency and country. Then one row per order for order-level sums, paid and partially refunded only, refunds netted, timestamps in the store timezone, one reporting currency. Flag outlier campaign-days with IQR; don't drop them silently.
**Worked ECOM check (illustrative).** 1,000 order names: 38 voided or pending and 22 fully refunded leave 940 that count as revenue. The order export's `Currency` is the store's base currency at the time of the order (SRC `pages/14`), so totals share one currency; more than one value in `value_counts()` on `Currency` means the base currency changed: convert before summing.
**Fails when.** `df['col'].fillna(x, inplace=True)` changes nothing on pandas 3 (Copy-on-Write; checked) · the ad account and the store sit in different timezones, so late-evening orders land on the next day's spend · line-item rows are counted as orders: the export repeats an order once per extra line item with order fields blank (SRC `pages/14`), so count unique `Name` · `Discount Code` is read as all discounts (it excludes automatic ones: SRC `pages/14`) · test orders are left in.
**Code:** `pandas-data-prep.md` §2–§5.

### Q2. What did each day or week of spend buy across Meta and Google?
**Method (CANON).** Aggregate each source to the same grain (date, or date × platform) *before* joining; left-join spend to orders. Blended CPA = spend ÷ Shopify orders; blended ROAS = net revenue ÷ spend (formulas owned by ANALYST §2, §15).
**Worked ECOM check (illustrative).** Week spend $4,500. Meta claims 120 purchases and Google 70: 190 claimed against 150 Shopify orders, an over-claim of 40 (27%). Blended CPA = $4,500 ÷ 150 = $30.00, not the $23.68 the platform sum implies.
**Fails when.** Row-level spend joined to row-level orders fans out and inflates both sums · platform purchases are added across platforms as if exclusive · platforms with different attribution windows are compared raw: Meta counts 1- or 7-day click and 1-day view (SRC PAID `platform-help-2026-10/pages/06-meta-attribution-settings.md`), Google defaults to data-driven (`…/21-google-data-driven-attribution.md`).
**Profitable or not:** ANALYST (break-even ROAS). **Code:** `pandas-data-prep.md` §6.

### Q3. Which first-order channel and cohort really drive repeat orders?
**Method (CANON).** Cohort = month of first order. Label each customer's first channel from a post-purchase survey or the UTM captured at first order: the export's `Source` is "the order's source -- for example, web, draft order, POS", the sales channel, not the ad channel (SRC `pages/14`). Count second orders within 30 and 90 days of *each customer's own* first order, and keep only customers old enough for the window.
**Worked ECOM check (illustrative).** Meta: 400 first-time buyers, 48 reorder within 90 days (12%). Google: 150 buyers, 27 reorder (18%). Google buyers look 1.5× more loyal, but z = −1.83, p = 0.068 (checked): not established at 95%, and 27 repeaters is below QUANT's 100-per-arm minimum. Don't move budget on it yet.
**Fails when.** Cohorts are compared at different ages (the young one is censored) · email as the customer key splits guest checkouts · last click on the first order is read as "what found the buyer".
**Then:** cohort LTV and LTV:CAC → ANALYST §12. **Code:** `cohort-segmentation.md` §1.

### Q4. Is this price or creative test result real?
**Method (CANON).** Two-proportion z-test on orders ÷ visitors per arm (`proportions_ztest`). Report the effect size and confidence interval, not just p. For a price test, compare revenue per visitor as well as CVR. Power, SRM, peeking and Bayesian reads → `statistical-reasoning`.
**Worked ECOM check.** Control 200/5,000 (4.0%), variant 250/5,000 (5.0%) → z = −2.41, p = 0.016 (checked): significant at 95%, both arms ≥100 conversions. Price test: +10% price with −8% CVR gives revenue per visitor 1.10 × 0.92 = 1.012, so +1.2%: the "losing" CVR wins on revenue. Margin per visitor is ANALYST's call.
**Fails when.** The snippet prints "variant is better" for any p < 0.05; the test is two-sided, so read the sign of z · the test stops at the first p < 0.05 after daily peeks · Meta serves each ad to a different audience, so an ad-level split is not randomised by visitor.
**Code:** `models-tests-forecasts.md` §1.

### Q5. How many orders next month, and over BFCM?
**Method (CANON).** Start with a naive baseline (same weekday, last 4 weeks). Then fit Prophet with weekly seasonality and BFCM as a custom holiday that includes future dates, or run a weekly decomposition. Treat the orders-on-spend regression as a planning slope, not a causal effect.
**Worked ECOM check (illustrative).** With 8 months of history, Prophet switches yearly seasonality off below 730 days (checked), and no BFCM lift can be learned until one BFCM is in the data. The Q4 number is then a scenario band from ANALYST's sensitivity cases, not a fitted forecast.
**SRC:** an automatic forecast must pick the model, estimate its parameters and give **prediction intervals**, not one number (SCM 421 `LectureClass_Python-III-FillRate_and_Forecast.md` Slide 16; ETS Slide 19); score it on MFE (bias), MAD, MAPE and the tracking signal (SCM 301 `Chapter-9-Forecasting.md` Slides 59–66).
**Fails when.** `seasonal_decompose` gets fewer than two full cycles (24 months at period 12; checked) · stockouts from China lead times record lost demand as low demand · planned spend sits outside the range the model has seen.
**Code:** `models-tests-forecasts.md` §3–§5.

### Q6. Which customers behave alike, and who will buy again?
**Method (CANON).** Build the RFM inputs table (scoring and actions: ANALYST §13); run k-means on standardised features for unsupervised segments; fit a repeat-purchase classifier on features known at the first order, with a chronological split and a fully observed label window. Leakage, calibration and model-card gates → `crisp-dm-ml-bridge`.
**Worked ECOM check (illustrative).** 900 customers, 92% with one order: F quintiles split identical values arbitrarily, so use a repeat yes/no flag. At an 8% repeat base rate, a model that says "no" to everyone is 92% accurate and useless; read ROC-AUC and the top-decile repeat rate against the 8% base.
**Fails when.** Fewer than ~100 repeaters (INF threshold: the forest memorises) · random split on time-ordered customers · random-forest probabilities used as calibrated · clusters named before their profile is read.
**Code:** `cohort-segmentation.md` §2–§3 · `models-tests-forecasts.md` §2, §6.

---

## Delegating a build
Script, model and scraper builds can go to ANTIGRAVITY in the MISSION / INPUT / OUTPUT / VALIDATE / LIBS format (`pandas-data-prep.md` §1). Interpretation and the significance call stay with QUANT.


