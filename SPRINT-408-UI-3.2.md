# 408-UI-3.2 — Homepage Platform Redesign

## Status
COMPLETE

## Goal
Transform `/` from a campaign-style landing page into the clean 408FARMERS platform hub established by UI-3.1, while preserving every existing destination, attribution contract, CoverageFit launcher, contact path, Local entry, professional-program route, and protected runtime dependency.

## Design direction
The homepage now follows the approved `/local` reference language:

- white-dominant page with restrained soft-blue/gray section separation
- compact UI-3.1 navy navigation and universal footer
- Farmers red reserved for primary action and small hierarchy cues
- controlled headline scale rather than oversized editorial typography
- clean bordered cards with smaller radii and lighter shadows
- denser, platform-like information architecture
- clear product families instead of one long campaign narrative

## Homepage architecture
The redesigned homepage is organized as:

1. **Platform hero**
   - South Bay household positioning
   - existing CoverageFit hero launcher preserved
   - existing “choose your path” behavior preserved
   - compact home visual and trust chips

2. **Primary platform routes**
   - Home
   - Home + Auto
   - Buying a Home
   - Life

3. **Additional needs**
   - Protection Score / current-coverage second opinion
   - Business
   - Rental Property

4. **Common review triggers**
   - premium increase
   - home purchase
   - approaching renewal
   - household/life change

5. **Professional Programs**
   - Healthcare
   - Education
   - Technology
   - Engineering

6. **CoverageFit method**
   - three-step review explanation
   - Protection Score experience link preserved

7. **408FARMERS Local**
   - Local directory entry
   - merchant pilot entry
   - explicit insurance-separation language

8. **Dylan / agency credibility**
   - producer identity and license
   - phone, SMS, and email actions
   - Virginia Tam Insurance Agency / Farmers Authorized Agency credential

## Added asset
- `shared/homepage-platform.css`

## Behavioral preservation
The sprint intentionally does **not** change:

- `_worker.js`
- `shared/ui-3-foundation.js`
- `shared/ui-3-foundation.css`
- `shared/homepage-optimization.js`
- `shared/config.js`
- `shared/campaign.js`
- `shared/coveragefit-launch.js`
- any Local merchant/perk/redemption/attribution runtime
- any Life secure-submission runtime
- Buyer/realtor context
- Home progressive intake
- Formspree/Worker submission contracts
- QR routing
- CoverageFit handoffs

Every tracked homepage destination that existed in the UI-3.1 baseline remains present with the same `data-track-*` contract and destination. The redesign adds a direct Home platform card without removing any legacy tracked destination.

## Responsive behavior
- four-column primary platform grid on wide desktop
- two-column grid through tablet widths
- single-column platform flow on phones
- split section headings collapse to one column
- Local and Dylan modules collapse cleanly
- no horizontal overflow at 320px
- primary actions remain at least 48px tall
- existing UI-3.1 mobile navigation remains authoritative

## Scope boundary
UI-3.2 redesigns **only the root homepage**. Product-specific conversion interfaces remain reserved for UI-3.3 through UI-3.7.

## Next sprint
**408-UI-3.3 — Home Conversion Experience**

Apply the shared platform language to `/home/` and Home deep-entry variants while preserving progressive intake, validation, campaign routing, submission, post-lead progression, and optional CoverageFit continuation.
