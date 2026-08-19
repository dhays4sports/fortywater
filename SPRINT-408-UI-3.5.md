# 408-UI-3.5 — Buyer Experience Redesign

## Status
COMPLETE

## Goal
Align `/buyer/` and realtor-origin buyer journeys with the UI-3 platform while preserving closing urgency, partner/referral context, attribution, submission, post-lead progression, and the zero-repeat CoverageFit handoff.

## Design direction
The buyer experience now uses the same restrained platform system established by UI-3.1 through UI-3.4:

- white-dominant composition with 408 navy, Farmers red, and restrained soft-blue support surfaces
- compact universal navigation and footer inherited from UI-3.1
- controlled split hero with contained home imagery rather than campaign-scale typography
- closing-first message hierarchy centered on the buyer's purchase timeline
- visible realtor-referral acknowledgement when a validated partner name is present
- one concise guided two-step buyer intake card
- Farmers-red primary conversion actions and focus states
- lighter borders, smaller radii, and reduced shadow weight
- compact local producer / agency credibility module
- buyer-specific fallback receipt aligned to the shared platform language

## Buyer architecture
1. **Closing-first hero**
   - retains the `Buying a Home?` identity required by the stable buyer contract
   - elevates `Coverage that keeps up with your closing.` as the new conversion lead
   - retains both text-first and online-start entry choices
   - keeps partner referral acknowledgement bounded and conditional
   - keeps property address, closing date, and contact context visually explicit

2. **Guided new-home review**
   - existing `#leadForm` remains the only online buyer intake
   - existing property-address, closing-date, occupancy, contact, and consent fields are unchanged
   - the two-step Property → Contact progression remains controlled by the existing buyer runtime
   - closing urgency continues to be derived by the existing controller

3. **CoverageFit continuation**
   - no duplicate buyer assessment was introduced
   - existing post-submit behavior and optional CoverageFit continuation remain intact
   - buyer/realtor attribution is carried through the existing zero-repeat handoff

4. **Producer credibility**
   - Dylan / Virginia Tam / Farmers credentials remain intact in a cleaner platform module
   - no new response-time, savings, underwriting, or eligibility promise was introduced

5. **Fallback receipt**
   - `/buyer/thank-you.html` consumes the new buyer visual layer
   - fallback messaging, contact links, and post-submit Local separation remain unchanged

## Added asset
- `shared/buyer-experience-ui.css`

## Behavioral preservation
UI-3.5 intentionally does **not** change:

- `shared/buyer-flow.js`
- `shared/buyer-referral.js`
- form action or method
- form field names / required semantics
- source / campaign / partner / referral / UTM fields
- closing urgency derivation
- closing-date minimum logic
- partner-name display safety (`textContent`)
- text-first SMS context
- address autocomplete runtime
- Formspree submission behavior
- post-lead engagement
- optional CoverageFit invitation
- CoverageFit sender/handoff contract
- `_worker.js`
- Home, Home + Auto, Local, Life, or professional-program behavior

## Responsive behavior
- two-column hero on desktop
- stacked content-first hero on tablet and phone
- one-column form fields on narrow screens
- 16px mobile form controls prevent iOS input zoom
- primary, secondary, and navigation targets remain touch-friendly
- short-landscape support included
- reduced-motion and forced-color accommodations included

## Conversion principle
The redesign treats the buyer as someone solving a closing problem first, not shopping an abstract insurance product. Realtor context remains visible when present, the intake stays short, and all insurance options remain downstream of the existing guided review and underwriting process.

## Next sprint
**408-UI-3.6 — Professional Programs Convergence**

Unify Healthcare, Teachers, Technology, and Engineers as one professional-program family while retaining occupation-specific messaging and context.
