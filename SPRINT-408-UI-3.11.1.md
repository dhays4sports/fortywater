# 408-UI-3.11.1 — Campaign Message-Match Convergence

## Status
COMPLETE

## Goal
Make major paid, physical, and referral campaign entry points feel intentionally connected to the certified 408FARMERS UI-3 platform without creating separate microsites or changing the underlying insurance journeys.

The rule is:

**Campaign-specific first impression → existing certified 408FARMERS journey.**

## Core architecture
This sprint introduces a presentation-only campaign layer:

- `shared/campaign-entry-registry.js` — bounded, approved campaign-entry resolver
- `shared/campaign-entry.js` — applies approved campaign copy to existing UI-3 hooks
- `shared/campaign-entry.css` — intentionally minimal presentation helper
- `CAMPAIGN_ENTRY_REGISTRY.json` — machine-readable registry snapshot
- `CAMPAIGN_MESSAGE_MATRIX.md` — human-readable ad → landing contract
- `CAMPAIGN_CREATIVE_REFRESH_SPEC.md` — future creative-system specification

## Presentation context vs. attribution context
Campaign presentation is selected only from **explicit current URL/path context**.

The campaign layer does not read `localStorage`, `sessionStorage`, cookies, or prior campaign memory. A later organic visit therefore returns to the normal evergreen route presentation.

Existing attribution may still persist downstream through the already-certified lead/Local/CoverageFit infrastructure. Presentation and attribution are deliberately separate concerns.

## Supported campaign families

### Stevie's coaster — Home/front
Recognizes the already-created coaster URL pattern:

`/home/?utm_source=stevies&utm_medium=coaster&utm_campaign=south_bay_homeowner&utm_content=home_front`

Matched first-screen message:

- **Own a Home in the South Bay?**
- Before your next renewal, see whether your coverage may deserve another look.
- **Start My Coverage Review**
- One local agent. No call-center barrage. No obligation. No pressure.

The visitor then continues through the unchanged UI-3.3 Home journey.

### Stevie's coaster — Home + Auto/back
Recognizes:

`/auto-bundle/?utm_source=stevies&utm_medium=coaster&utm_campaign=south_bay_homeowner&utm_content=bundle_back`

Matched first-screen message:

- **Own the Home. Drive the Cars.**
- Review them together.
- **Start My Home + Auto Review**

The underlying UI-3.4 form, housing branch, renter path, attribution, post-lead behavior, and CoverageFit handoff are unchanged.

### Professional Programs
Canonical future campaign IDs:

- `occupation_tech_meta_v1`
- `occupation_teacher_meta_v1`
- `occupation_engineer_meta_v1`
- `occupation_healthcare_meta_v1`

Matched hooks:

- Tech — **Work in Tech?**
- Teachers — **Are You a Teacher?**
- Engineers — **Are You an Engineer?**
- Healthcare — **Work in Healthcare?**

Campaign visitors receive `CHECK MY ELIGIBILITY`; organic visitors retain the existing UI-3.6 evergreen experience.

No profession-specific role choices, eligibility boundaries, form fields, submissions, or CoverageFit context were changed.

### Buyer / Realtor
Explicit partner/realtor current-entry context or the canonical `realtor_buyer_card` campaign activates:

- **Need Coverage for Your Closing?**
- Let’s organize the insurance side while your purchase keeps moving.
- **Start My Buyer Review**

Existing partner acknowledgement, partner IDs, closing urgency, buyer form, text-Dylan flow, and zero-repeat handoff remain canonical.

### Life
UI-3.7 remains the canonical Life campaign renderer. 3.11.1 does not flatten or replace it.

The registry formally recognizes the existing A/B/C/D creative states:

- `before_anything_changes`
- `20_minutes`
- `this_is_the_time`
- `financial_picture`

Life continues using the cinematic campaign visual mode and secure application runtime already certified in UI-3.7.

### Existing Home flyer family
Dynamic `/home/qr/<ZIP>/(rate|fit)/` and `/home/campaign/<ZIP>/(rate|fit)/` routes remain delegated to the existing `Farmers408FlyerCampaign` renderer. The new registry recognizes the family but does not compete with its ZIP-specific copy logic.

## Safe fallback
Unknown, malformed, stale, or route-incompatible campaign values render the normal evergreen page.

User-controlled query values are used only for normalized matching. They are never injected directly into visible copy or HTML.

## Behavior freeze
Compared against the exact UI-3.11 input:

- existing protected runtime/Worker/catalog files: **40/40 byte-identical**
- form contracts across public HTML: **28/28 preserved**
- non-target HTML surfaces: **22/22 byte-identical**

Only the eight campaign-facing route documents received approved presentation hooks/loaders:

- Home
- Home + Auto
- Buyer
- Tech
- Teachers
- Engineers
- Healthcare
- Life

No form field names, required semantics, endpoints, Worker APIs, underwriting logic, discount rules, partner attribution schema, Local merchant behavior, secure Life application, consent text, or CoverageFit contracts were changed.

## Accessibility delta
All eight campaign-facing routes were rechecked for:

- exactly one H1 and one main landmark
- unique IDs
- valid ARIA ID references
- labeled controls
- image alternative text
- no positive tabindex

Campaign-specific messages inherit the UI-3.11 contrast, focus, reduced-motion, forced-colors, mobile reflow, and zoom layers.

## QA
- UI-3.11.1 source contract: **82/82**
- campaign browser message-match: **51/51**
- accessibility delta: **56/56**
- protected runtime freeze: **40/40**
- form-contract freeze: **28/28**
- non-target HTML freeze: **22/22**
- runtime JavaScript syntax: **41/41**
- existing static regression: **296/296**
- homepage UI-3.2.1 browser regression: **93/93**
- Home UI-3.3 browser regression: **108/108**
- Home + Auto UI-3.4 browser regression: **99/99**
- Buyer UI-3.5 browser regression: **115/115**
- Professional Programs UI-3.6 browser regression: **452/452**
- Life UI-3.7 browser regression: **23/23**
- Local UI-3.8 browser regression: **155/155**
- Utility UI-3.9 browser regression: **293/293**
- Mobile UI-3.10 browser regression: **822/822**
- Home hidden-required submit regression: **12/12**
- Home Advanced Mode routing: **16/16**
- redirect-loop regression: **10/10**
- Merchant Join Worker: **20/20**
- Local Attribution Worker: **29/29**
- FLOW-2.4 explicit invitation runtime: **5/5**
- internal links/assets: **630 checked / 0 broken**

## Parallel Local status
LOCAL-1.10 remains technically certified with the planned three-merchant pilot production NO-GO pending real Auto + Home merchants and external closeout. This sprint does not alter that boundary.

## Design freeze
UI-3.11.1 is the final intentional customer-facing design/presentation change before final system regression.

## Next sprint
**408-UI-3.12 — End-to-End Functional Regression**
