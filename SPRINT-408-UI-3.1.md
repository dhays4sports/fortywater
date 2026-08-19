# 408-UI-3.1 — Unified Visual Foundation

## Status
COMPLETE

## Goal
Establish one reusable 408FARMERS visual language across the current public platform without changing any protected acquisition, submission, attribution, Local, Life, or CoverageFit behavior.

## Visual direction
The foundation is based on the restrained `/local` reference direction approved in the UI planning conversation:

- 408 navy as the authority/navigation color
- Farmers red as the primary action color
- white as the dominant content surface
- subtle blue-gray page/support surfaces
- smaller radii, lighter borders, and materially lighter shadows
- compact platform navigation rather than oversized marketing headers
- consistent form controls and status treatments
- one universal footer and one shared page-shell vocabulary

## Added assets
- `shared/ui-3-foundation.css`
- `shared/ui-3-foundation.js`
- `shared/assets/408-farmers-nav-logo.png`
- `UI3_1_FOUNDATION_CONTRACT.json`
- `qa/test-408-ui-3.1.py`
- `408-UI-ROADMAP.md`

## Public-page integration
The UI-3.1 foundation is loaded last on every public HTML surface, including the root, Home, Home + Auto, Buyer, Life, Local, Local Join, merchant detail shell, professional-program pages, Contact, Score, Neighbor, thank-you surfaces, Privacy, and Terms.

Internal QA fixtures and `life-ops/` are intentionally excluded from the consumer visual foundation.

## Universal header
The new runtime enhancement converts the existing page header into a common compact navy navigation shell:

- Home
- Home + Auto
- Buyers
- Local
- Life
- Contact
- preserved Call Dylan action
- responsive menu with Escape/resize close behavior
- page-aware active state with Farmers-red underline

The existing header remains the no-JavaScript fallback. The enhancement does not change any insurance form or flow code.

## Universal footer
Existing public footers are progressively enhanced into one shared footer containing:

- core consumer journeys
- professional programs
- Local
- Protection Score
- phone, SMS, email, and contact-options routes
- agency/license disclosure
- Privacy and Terms

Existing source footers remain available as the no-JavaScript fallback.

## Design tokens
UI-3.1 establishes canonical tokens for:

- color
- spacing
- typography
- borders
- radii
- shadows
- focus treatment
- success/warning/error state colors

A compatibility bridge maps legacy `--gold` and CoverageFit-green primary tokens to Farmers red **on 408FARMERS pages only**, allowing later UI-3.x sprints to migrate component-by-component without breaking the mature runtime.

## Shared components
The foundation provides or normalizes:

- primary buttons
- secondary buttons
- text inputs
- selects
- textareas
- checkboxes/radios
- card surfaces
- chips
- dividers
- alerts/status messages
- page/container shells
- compact navigation
- universal footer

## Protected behavior
This sprint intentionally does **not** change:

- form field names
- required-field semantics
- submission endpoints
- `_worker.js`
- campaign routing
- QR routes
- Local merchant/perk data
- Local attribution implementation
- Local redemption implementation
- Buyer/realtor context
- Life secure submission
- CoverageFit handoff contracts
- post-submission progression

The certification test compares every modified public HTML file with the LOCAL-1.10 baseline after removing only the UI-3.1 stylesheet/meta/script hooks. The normalized documents must be byte-identical.

## Responsive behavior
- 64px desktop header
- 60px mobile header
- mobile menu at <= 860px
- 44px menu target
- 16px mobile form typography to prevent iOS input zoom
- minimum 48–50px form controls
- reduced-motion support
- visible focus treatment

## Scope boundary
UI-3.1 is the **foundation**, not the full page-by-page redesign. Hero composition, content architecture, product-specific hierarchy, and deeper route-level visual convergence are intentionally reserved for UI-3.2 through UI-3.9.

## Next sprint
**408-UI-3.2 — Homepage Platform Redesign**

Use the new foundation to transform `/` into the clean 408FARMERS ecosystem hub while preserving all current destinations and attribution contracts.
