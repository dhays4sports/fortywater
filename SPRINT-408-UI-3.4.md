# 408-UI-3.4 — Home + Auto Conversion Experience

## Status
COMPLETE

## Goal
Bring `/auto-bundle/` into the UI-3 platform conversion language while preserving the mature Home + Auto / renters branching, attribution, submission, post-lead progression, and CoverageFit handoff behavior.

## Design direction
The bundle experience now uses the same system established by UI-3.1, the reconciled homepage, and UI-3.3 Home:

- white-dominant composition with 408 navy, Farmers red, and restrained soft-blue surfaces
- compact universal navigation and footer inherited from UI-3.1
- controlled split hero with contained bundle imagery
- clearer Home + Auto positioning without promising a discount
- one centered guided-review card that supports both homeowners and renters
- Farmers-red primary submission action and focus treatment
- lighter borders, smaller radii, and reduced shadow weight
- compact three-step explanation and producer credibility module

## Bundle architecture
1. **Conversion hero**
   - `Home + auto coverage review` positioning
   - `Review Home + Auto Together.` primary headline
   - renter support remains explicit in the supporting copy
   - trust chips communicate one household review, no obligation, and homeowner/renter eligibility
   - existing bundle visual asset is retained as a contained supporting image

2. **Guided bundle review**
   - existing `#leadForm` remains the conversion surface
   - existing first/last name, phone, email, property address, and housing-context fields are unchanged
   - homeowners still continue toward the Home CoverageFit assessment
   - renters still branch directly to Dylan through the existing renter destination
   - full Dylan bio inside the form card is visually suppressed because the dedicated producer section remains below

3. **Coverage explanation**
   - current housing-first branch logic is explained without creating a new decision tree
   - no savings or discount result is promised before quoting/underwriting

4. **Producer credibility**
   - Dylan/Virginia Tam/Farmers credentials remain intact in a cleaner soft-blue module

## Added asset
- `shared/auto-bundle-conversion-ui.css`

## Behavioral preservation
UI-3.4 intentionally does **not** change:

- `#leadForm` action or method
- form field names or required-field semantics
- hidden source/campaign/UTM fields
- consent language
- address autocomplete runtime
- `housing_context` branch field
- renter destination
- Formspree submission behavior
- post-lead engagement
- optional CoverageFit invitation
- CoverageFit handoff contract
- `_worker.js`
- UI-3.1 foundation runtime
- UI-3.3 Home experience
- Local, Buyer, Life, or professional-program behavior

## Responsive behavior
- two-column hero on desktop with the guided review immediately below
- content-first stacked hero on tablet/mobile
- form fields collapse to one column on small screens
- 16px mobile form controls prevent iOS input zoom
- direct-contact targets remain at least 44px high
- short-landscape support included
- reduced-motion and forced-color accommodations included

## Conversion principle
This sprint does not manufacture a bundle-discount promise. It frames Home + Auto as one household review, retains renter relevance, and leaves discount availability to the existing quote/underwriting process.

## Next sprint
**408-UI-3.5 — Buyer Experience Redesign**

Align `/buyer/` and realtor-origin journeys with the platform while preserving closing urgency, referral context, attribution, and zero-repeat handoff.
