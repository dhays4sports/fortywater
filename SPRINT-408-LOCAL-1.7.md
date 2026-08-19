# 408-LOCAL-1.7 — Insurance Conversion Bridge

## Outcome

408FARMERS Local now has its first explicit insurance conversion bridge, but the bridge appears only after Local merchant value has already been delivered. On an active merchant-perk page, visitors first receive the merchant profile, current perk, merchant terms, frictionless show-your-screen action, and the explicit Local/insurance separation statement. Only after that does a distinct optional homeowner module invite them into an existing 408FARMERS insurance journey.

The merchant offer remains completely independent. A visitor can view and redeem the perk without clicking, submitting, or interacting with insurance at all. The merchant-detail header now keeps its prominent action inside Local (Browse Local), so the first dedicated insurance conversion module appears only after the merchant value and separation boundary.

## What this sprint adds

### 1. Post-value homeowner module

The merchant detail renderer now adds a dedicated `data-local-insurance-bridge` section after the merchant-perk and program-boundary content.

Headline:

`Own a home in the South Bay?`

The module clearly identifies itself as an optional insurance review and states that it is separate from the Local perk.

### 2. Two existing insurance journeys

The bridge provides:

- `Review home + auto` → `/auto-bundle/`
- `Review my home only` → `/home/`

No new insurance intake is created inside Local. The visitor enters the already-certified 408FARMERS acquisition journey.

### 3. Merchant value remains first

The merchant-detail header's prominent right-side action stays inside Local (`Browse Local`) rather than jumping directly into an insurance flow before the merchant value is shown.

The bridge is rendered after:

1. merchant identity and description;
2. merchant links/directions;
3. current Local perk;
4. `Use This Perk` redemption action when supported;
5. merchant-specific terms;
6. independent-offer language;
7. explicit Local/insurance program boundary.

The dedicated bridge is not rendered when the public merchant has no active perk. This prevents an offer-less merchant page from being repurposed as an insurance acquisition page.

### 4. Existing 1.6 attribution is reused

Both bridge links use the existing `data-local-insurance-cta` contract and destination tokens. The 1.6 attribution runtime decorates the links with the current Local merchant/perk/surface/campaign context and emits the existing `insurance_cta_click` event.

No new analytics event type or PII collection is introduced in 1.7.

### 5. No duplicate lead capture

There is no form in the Local bridge. A later insurance submission occurs only through the existing 408FARMERS insurance form. The 1.6 continuity layer preserves Local origin into that lead and into the existing CoverageFit sender path when the visitor voluntarily continues there.

### 6. No automatic CoverageFit launch

Local never starts CoverageFit. The bridge only navigates into an existing 408FARMERS insurance route. CoverageFit can occur later only according to the existing insurance journey and its explicit invitation/continuation rules.

## Compliance and product boundary

The bridge explicitly states:

- the merchant perk is already available;
- using or skipping the insurance review does not change the merchant offer;
- no insurance quote or policy purchase is required to use the Local perk;
- the merchant offer remains subject to merchant terms and availability.

No insurance discount, premium concession, eligibility preference, underwriting benefit, or coverage benefit is attached to Local participation or perk redemption.

## Files added

- `SPRINT-408-LOCAL-1.7.md`
- `LOCAL1_7_BRIDGE_CONTRACT.json`
- `qa/test-408-local-1.7.js`
- `LOCAL1_7_QA.json`
- `LOCAL1_7_RELEASE_CERTIFICATION.json`

## Files intentionally changed

- `shared/local-merchant.js` — renders the dedicated post-value insurance bridge.
- `shared/local.css` — responsive bridge presentation.
- `local/index.html` — advances the Local release marker only.
- `local/detail/index.html` — advances the Local release marker while keeping the prominent header action inside Local so the dedicated insurance invitation remains post-value.
- `408-LOCAL-ROADMAP.md`, `ROADMAP.md`, `CHANGELOG.md`, `README.txt`, `VERSION` — sprint progression and continuation.

## Preserved

- Local catalog and schema unchanged;
- no real merchant activation;
- no live perk activation;
- merchant join flow unchanged;
- Local attribution runtime remains 408-LOCAL-1.6 and its privacy/event contract is unchanged;
- Worker routes and event API unchanged;
- existing 408FARMERS insurance forms unchanged;
- CoverageFit launcher and zero-repeat sender unchanged;
- no automatic CoverageFit launch from Local;
- no duplicate Local insurance lead capture;
- no insurance discount, pricing, eligibility, underwriting, or coverage rule changed.

## Next sprint

**408-LOCAL-1.8 — 408FARMERS Site Integration**

Make Local discoverable from the broader 408FARMERS site without weakening the existing insurance conversion funnels.
