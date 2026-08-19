# 408-UI-3.13.1C — Core Insurance Humanization

## Status
COMPLETE — HUMAN TRUST / CORE INSURANCE

## Input baseline
`408-UI-3.13.1B — Professional Programs Humanization`.

The UI-3.13 production baseline, 408-INFRA-1.1 Function boundary hotfix, Campaign Message-Match Convergence, Accessibility Certification, and Professional Programs Humanization remain authoritative.

## Objective
Apply a deliberately restrained Human Trust layer to the Homepage, Home, Home + Auto, and Buyer experiences so the platform feels more like a premium way to work with a real local producer and less like an insurance software product.

Governing principle: **Modern system underneath. Human relationship on the surface.**

Professional Programs remain the stronger campaign/editorial calibration reference. Life remains excluded and untouched.

## Implemented

### Homepage
- Replaced the abstract hero trust-chip row with a compact Dylan Human Trust Signature.
- Shifted the hero support copy into a first-person local-producer voice without changing the existing Coverage Review CTA or situation-first routing.
- Kept the 408FARMERS platform structure, product routes, Local, professional programs, and lower full Dylan credibility section intact.
- Softened the CoverageFit explanation so it reads as a tool that helps organize the conversation rather than a software layer speaking to the user.

### Home
- Preserved the campaign-aware Home hero from UI-3.11.1 and the full UI-3.3 lead/intake architecture.
- Humanized the editorial review proposition to `Let’s see what’s worth reviewing.`
- Added a restrained early Dylan signature beside the review explanation, not inside the form.
- Reduced benefit-list chrome while retaining grouping, scanability, and accessibility.
- Left the form, engagement steps, payoff, post-lead states, and downstream agent section functionally untouched.

### Home + Auto
- Reframed the organic hero around reviewing the household together with Dylan.
- Replaced pill-heavy hero trust cues with a compact Dylan signature and simple Homeowners/Renters reassurance.
- Rewrote the pre-form explanation in plain language while preserving renter/homeowner routing.
- Removed the redundant long-form `Meet Dylan` block from inside the conversion card; the existing direct-contact choice and lower producer credential section remain.
- Humanized the supporting section to `Let’s look at the household together.`

### Buyer
- Added a light concierge tone around the existing closing-first experience.
- Added an early Dylan signature while preserving the existing Text Dylan and Start Online actions.
- Reframed the visual card as `A few details to start` instead of software-like closing-context taxonomy.
- Humanized the intake heading to `Let’s keep the insurance side moving.`
- De-chromed the three supporting promises without changing the Buyer form, referral acknowledgement, or closing logic.

## Human Trust calibration
- No Professional Programs gold was introduced into core insurance pages.
- No new lifestyle photography was added solely for decoration.
- Existing Home/Bundle/Buyer photography remains context-first; Dylan imagery is used selectively for trust.
- No customer-facing page claims Dylan has already reviewed information before submission.
- Core pages use less Human Trust intensity than the occupational pages.

## Protected behavior
No change to:
- form names, controls, required fields, or consent
- Formspree endpoints
- `_worker.js`, `_routes.json`, or Cloudflare API behavior
- Home / Bundle branching
- Buyer referral and closing urgency
- Campaign Entry Registry/runtime or attribution schema
- Professional Program pages/logic
- Life / Life Ops
- Local
- CoverageFit launch/invitation/handoff
- SMS/phone destinations
- pricing, eligibility, or underwriting behavior

The three core lead forms are HTML-identical inside `<form id="leadForm">` to the 3.13.1B input baseline.

## Accessibility / responsive requirements
- Existing UI-3.11 focus, contrast, reduced-motion, forced-colors, zoom, and semantic behavior remains authoritative.
- Human Trust portraits include meaningful alt text.
- Essential copy remains live HTML.
- 320px, 390px, tablet, 1024px, and 1440px layouts are regression-tested for overflow.
- Mobile controls retain the certified touch/input sizing.

## Certification
See:
- `UI3_13_1C_QA.json`
- `UI3_13_1C_BROWSER_QA.json`
- `UI3_13_1C_RELEASE_CERTIFICATION.json`

## Next sprint
**408-UI-3.13.1D — Relationship + Completion Humanization**

That sprint should move the strongest Human Trust voice into post-submit, receipt, follow-up, Local, Contact, and utility surfaces. It should not reopen the core pre-submit architecture certified here.
