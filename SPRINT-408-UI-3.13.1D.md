# 408-UI-3.13.1D — Relationship + Completion Humanization

## Status
COMPLETE — HUMAN TRUST / RELATIONSHIP + COMPLETION

## Input baseline
`408-UI-3.13.1C — Core Insurance Humanization`.

The UI-3.13 production design baseline, 408-INFRA-1.1 Pages Function boundary hotfix, Campaign Message-Match Convergence, Accessibility Certification, Professional Programs Humanization, and Core Insurance Humanization remain authoritative.

## Objective
Move the strongest Human Trust voice into the relationship **after a prospect has submitted** while warming Contact and Local without changing any insurance, campaign, merchant, attribution, or handoff behavior.

Governing principle: **The system should confirm state accurately; Dylan should own the relationship when the state supports it.**

Life / Life Ops remain excluded and untouched.

## Implemented

### Post-lead focus flow
- Reframed the confirmed state from software-style status copy to `Thanks — I have your request.`
- Added a compact Dylan portrait to the acknowledgement.
- Reframed the focus step as `A few quick questions will help me focus the review.`
- Added the explicit safeguard `You’re not submitting another request.`
- Preserved truthful pending / unconfirmed language so the interface never falsely claims Dylan has a request that has not been confirmed.
- Preserved every post-lead semantic field, radio option, progression rule, event name, payoff calculation, renter branch, and explicit-continuation contract.

### Optional CoverageFit invitation
- Kept the existing `Your request is complete.` and `Your information is already submitted` safeguards.
- Added restrained Dylan identity and first-person relationship copy.
- Reframed the optional branch as a choice between giving Dylan more organized context and simply having Dylan follow up.
- Preserved CoverageFit as educational and optional and retained every acceptance/defer/back telemetry contract.

### Static insurance receipts
- Humanized Home, Home + Auto, Buyer, Healthcare, Teachers, Technology, and Engineers fallback receipts.
- Added a compact Dylan signature and first-person acknowledgement where receipt state is already confirmed.
- Preserved fallback semantics, no-response-time guarantee language, underwriting/availability caveats, direct contact destinations, Local separation, and existing route attribution links.
- Preserved the Buyer receipt legacy H1 contract while adding the human acknowledgement beneath it.

### Contact
- Replaced abstract trust chips with an early, compact Dylan Human Trust Signature.
- Added `You’ll reach me directly.` and `No call-center handoff.` as concrete relationship cues.
- Preserved the existing SMS, phone, and email destinations and agency/license/carrier credentialing.

### 408FARMERS Local
- Warmed the directory opening with `Useful places. Local perks. South Bay businesses.`
- Removed the hero trust-chip row and replaced it with plain-language public-access / insurance-separation copy.
- Reframed merchant participation as a small relationship-led pilot and introduced Dylan as the person reviewing merchant applications.
- Humanized `/local/join/` and its completion state while preserving the merchant application form exactly.
- Kept Local's core rule intact: **No insurance purchase or quote required.**
- Preserved merchant data, directory, detail, redemption, attribution, insurance bridge, join Worker, offer responsibility, and no-endorsement / no-guarantee boundaries.

## Visual / component-density calibration
- Added `shared/relationship-human.css` as a presentation-only layer.
- De-chromed confirmation/status blocks into editorial identity rows.
- Reduced card treatment around summaries, optional next steps, and Local relationship copy while retaining functional grouping where it aids choice or accessibility.
- Farmers red remains the action/relationship accent; Professional Programs gold does not spread into these surfaces.

## Protected behavior
No change to:
- form names, controls, required fields, or consent
- Formspree endpoints
- `_worker.js`, `_routes.json`, or Cloudflare API behavior
- Home / Bundle branching
- Buyer referral and closing logic
- occupational eligibility or discount logic
- Campaign Entry Registry/runtime or attribution schema
- Local merchant model, redemption, attribution, or insurance separation
- Life / Life Ops
- CoverageFit launch/handoff contracts
- SMS/phone/email destinations
- pricing, eligibility, underwriting, or policy behavior

Eight protected forms are exact to the 3.13.1C input baseline.

## Accessibility / responsive requirements
- Human portraits include meaningful alt text.
- Confirmed, pending, and unconfirmed states remain semantically truthful.
- Focus, live-region, keyboard, reduced-motion, forced-colors, zoom, and mobile touch behavior remain inherited from UI-3.11/3.10.
- Relationship surfaces are browser-regression tested at 320px, 390px, 768px, 1024px, and 1440px as applicable.

## Certification
See:
- `UI3_13_1D_INPUT_BASELINE.json`
- `RELATIONSHIP_COMPLETION_HUMANIZATION_CONTRACT.json`
- `UI3_13_1D_QA.json`
- `UI3_13_1D_BROWSER_QA.json`
- `UI3_13_1D_RELEASE_CERTIFICATION.json`

## Next sprint
**408-UI-3.13.1E — Human Trust Regression + Production Certification**

That sprint should make no intentional customer-facing design changes. It should freeze A–D, run final cross-surface regression/certification, preserve Life and INFRA-1.1, and establish the final deployable Human Trust baseline.
