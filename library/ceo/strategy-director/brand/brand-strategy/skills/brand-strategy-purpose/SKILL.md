---
name: brand-strategy-purpose
description: >
  Define brand purpose, mission, vision and values (Golden Circle, Brand
  Key or onion), tied to a real buyer driver, not a feel-good line. Use
  for "brand purpose", "mission vision values", "Golden Circle", "why
  statement", "brand key", "brand onion", `/brand-strategy purpose`.
allowed-tools:
  - Read
  - Write
---

# Brand Strategy Purpose — Why the Brand Exists

Purpose answers "why would a buyer care that this brand exists", so it must connect to a real buyer driver.
**Sources:** pack `../../sources/brand-research-methods-2026-10/` (`_urls.md`; page 04 = Sinek TED transcript, 05 = simonsinek.com Golden Circle, 06 = Brand Key (Umbrex, secondary), 12–13 = JTBD; lake L2) via `../../references/purpose-frameworks.md`. Labels: SRC · INF · CANON · NOT IN SOURCE.

**Input:** `buyer_psychology.json` + brand brief, founder story (if any).
**Process:** purpose ladder → Golden Circle → Brand Key or onion → buyer-driver link → emit.

## Output — `purpose.json`
```json
{
  "purpose": "the change the brand exists to make (1 sentence)",
  "mission": "what the brand does day-to-day to pursue the purpose",
  "vision": "the future state if the brand succeeds",
  "values": ["3-6 values, each a behavioral commitment not an adjective"],
  "golden_circle": {"why": "...", "how": "...", "what": "..."},
  "brand_key": {"root_strength": "...", "competitive_environment": "...", "target": "...", "insight": "...", "benefits": ["..."], "values_and_personality": "...", "reason_to_believe": "...", "discriminator": "...", "essence": "the brand in 2-3 words"},
  "buyer_driver_link": "which buyer driver this purpose answers"
}
```

## Rules
- **Ladder tests** (purpose-frameworks §1; INF, the pack defines no purpose / mission / vision ladder): purpose = would anyone outside the company care? · mission = active, current-tense · vision = a destination, not a slogan · values = behaviours, not adjectives.
- **Values rule:** "integrity" means nothing; "we name our suppliers publicly" can be checked. Every value is a verifiable behavioural commitment.
- **Golden Circle** (Sinek; purpose-frameworks §2): communicate Why → How → What. The Why is discovered (founding story, the change wanted), not invented (INF). SRC 05: "Your WHY is your purpose, cause, or belief" and not making money ("that's a result"); HOWs are "the actions we take when we are at our natural best and are living out our WHY". SRC 04: "People don't buy what you do; they buy why you do it." Sinek's limbic-brain explanation is his claim (UNVERIFIED); use the order, not the neuroscience.
- **Brand Key or onion** (purpose-frameworks §3–§4): operator's choice; both end at a 2-3 word essence (INF). SRC 06 (secondary): nine components culminating in the essence, built outside-in from frame and target; 2–3 functional + 2–3 emotional benefits, 3–5 RTBs; CONFLICT on length: essence "often 3–6 words". Onion: NOT IN SOURCE (CANON).

## Buyer-driver binding (purpose-frameworks §5)
Bind the purpose to the buyer driver from Step 0, using the table in [purpose-frameworks](../../references/purpose-frameworks.md) §5 (its one home).

A purpose disconnected from buyer drivers is decoration. State `buyer_driver_link` explicitly. The binding table is INF; SRC support: jobs carry "functional, social, and emotional forces" (12); "purpose branding" builds a brand around one job (13).

## Fails when
Generic purpose ("to delight customers") · adjective values · a Golden Circle that starts at What · purpose written for the founder's ego, not the buyer's world.

## Cross-Link
- Consumes `buyer_psychology.json`
- Reference: `references/purpose-frameworks.md`
- Hands `purpose.json` to `positioning`, `voice`, `book`

## Verification
- [ ] Purpose ladder: all 4 rungs filled and distinct
- [ ] Every value is a behavioural commitment, not an adjective
- [ ] Golden Circle starts at Why; Brand Key / onion completed to essence
- [ ] `buyer_driver_link` names the driver the purpose answers

