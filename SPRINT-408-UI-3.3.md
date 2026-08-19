# 408-UI-3.3 — Home Conversion Experience

## Status
COMPLETE

## Goal
Bring `/home/` and every Worker-served Home deep entry into the clean, platform-oriented UI-3 visual language without changing the mature Home acquisition journey.

## Design direction
The Home experience now uses the same visual hierarchy established by UI-3.1 and the redesigned homepage:

- white-dominant composition with 408 navy, Farmers red, and restrained soft-blue surfaces
- compact universal navigation and footer inherited from UI-3.1
- controlled two-column conversion hero instead of the previous image-first campaign composition
- smaller, more deliberate typography and clearer hierarchy
- one contained guided-review shell with a clean conversion card
- red primary action and progress system
- restrained bordered cards instead of heavy shadows and oversized radii
- consistent form controls, option cards, payoff states, post-lead states, and CoverageFit invitation styling
- compact process and producer-credibility modules

## Home architecture
1. **Conversion hero**
   - existing campaign-aware eyebrow/title/lead/copy preserved
   - existing coverage-review anchor preserved
   - existing SMS alternative preserved
   - home photography becomes a contained supporting visual

2. **Guided review shell**
   - existing review explanation and benefit list retained
   - progressive Home journey remains inside the existing `#leadForm` conversion card
   - quick-question, recovery, payoff, lead-detail, and direct-contact states receive one visual language

3. **Post-lead progression**
   - existing lead receipt, post-lead engagement, personalized payoff, and optional CoverageFit invitation remain behaviorally unchanged
   - visual states converge on the new red/navy/white system

4. **Process explanation**
   - existing three-step sequence retained with compact platform cards

5. **Producer credibility**
   - existing Dylan/Virginia Tam/Farmers credentials retained in a cleaner soft-surface module

## Deep-entry behavior
No separate templates were created for campaign or QR Home routes. Existing Advanced Mode routing still maps `/home/qr/*`, `/home/campaign/*`, and other supported Home deep paths to the canonical `/home/` asset, so they automatically receive UI-3.3 while preserving campaign parsing and attribution.

## Added asset
- `shared/home-conversion-ui.css`

## Behavioral preservation
UI-3.3 intentionally does **not** change:

- `#leadForm` action, method, field names, hidden attribution fields, or consent
- Home progressive-intake JavaScript
- quick-question values or semantic fields
- address autocomplete
- campaign/flyer routing
- Formspree submission behavior
- renter branch
- post-lead engagement behavior
- optional CoverageFit invitation behavior
- CoverageFit zero-repeat handoff
- `_worker.js`
- UI-3.1 foundation runtime
- Local, Buyer, Life, or occupational product behavior

## Responsive behavior
- split conversion hero on desktop
- single-column content-first hero on phones
- guided review shell collapses to one column on tablet/mobile
- benefit cards adapt from compact three-column tablet presentation to one-column phone presentation
- form fields collapse safely to one column
- 16px mobile form controls remain enforced
- mobile actions remain at least 44px high
- short landscape screens receive a compact hero treatment
- reduced-motion and forced-color accommodations preserved

## Certification philosophy
UI-3.3 passes only if the Home page looks materially different while the Home form inventory, script inventory, Worker routing, campaign contracts, post-lead runtime, and CoverageFit handoff remain intact.

## Next sprint
**408-UI-3.4 — Home + Auto Conversion Experience**

Apply the same platform conversion language to `/auto-bundle/` while preserving bundle-specific context, form behavior, attribution, submission, and CoverageFit continuation.

## Certification results
- UI-3.3 source/behavior contract: **191/191**
- UI-3.3 browser rendering: **108/108** across 320px, 390px, 768px, and 1440px viewports
- Existing static regression: **296/296**
- Hidden-required submit hotfix: **12/12**
- Home Advanced Mode routing: **16/16**
- Home deep-route assets: **12/12**
- FLOW-2.4 explicit-invitation runtime: **5/5**
- Merchant Join Worker regression: **20/20**
- Local Attribution Worker regression: **29/29**
- Logo integration: **14/14**
- Homepage browser regression: **77/77**
- Local browser regression: **210/210**
- Shared JavaScript syntax: **37/37**
- Public internal links: **134 checked, 0 broken**
