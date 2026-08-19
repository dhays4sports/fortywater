# 408-UI-3.10 — Mobile Interaction Pass

## Status
COMPLETE

## Goal
Make the unified 408FARMERS UI-3 platform dependable on phones, tablets, in-app browsers, landscape devices, short screens, and mobile keyboards without changing insurance, Local, Worker, attribution, Life secure-submission, or CoverageFit behavior.

## Mobile interaction layer
This sprint introduces `shared/mobile-interaction.css`, loaded after the existing UI-3 visual layers on every public consumer surface.

### Safe areas and viewport behavior
- all public UI-3 pages now opt into `viewport-fit=cover`
- universal header, mobile navigation, footer, and dialogs respect iPhone safe-area insets
- dynamic viewport (`dvh`) sizing is used when supported, with `vh` fallback
- anchor/focus scroll offsets account for the sticky header
- visual overflow is clipped at the page boundary without hiding vertical content

### Touch ergonomics
- primary interactive controls remain at least 44px tall on coarse-pointer/mobile devices
- form controls remain at least 16px on mobile to prevent iOS input zoom
- checkboxes/radios receive larger finger-sized controls
- touch actions use `touch-action: manipulation`
- phone CTA groups stack cleanly rather than compressing side-by-side

### Mobile navigation
- existing UI-3 menu behavior is preserved
- the menu now fits short/dynamic viewports, scrolls internally when needed, and respects safe-area insets
- navigation links remain finger-sized
- body scroll locking remains controlled by the existing UI-3.1 runtime

### Forms and mobile keyboards
- fields have sticky-header-aware `scroll-margin-top`
- text-entry fields reserve lower scroll margin so browser-native keyboard focus does not leave the active control trapped at the bottom edge
- textareas stay resizable and usable
- no sticky submit bar was introduced, so consent, disclosures, warnings, and validation messages cannot be covered by a mobile action layer

### Horizontal navigation families
- Professional Programs route switcher is horizontally scrollable on narrow devices instead of shrinking labels below usable size
- Local category filters use the same touch-scroll pattern

### Short landscape / in-app browser behavior
- oversized hero typography/media are reduced on short landscape screens
- sticky sidecars are disabled where a short viewport would make them counterproductive
- dialogs are constrained to the dynamic viewport and remain internally scrollable
- required disclosures and guardrails remain visible

## Behavior freeze
No changes were made to:
- `_worker.js`
- form field names, required semantics, actions, or success destinations
- Formspree / Cloudflare submission endpoints
- Home, Bundle, Buyer, Professional, Life, or Local runtime JavaScript
- QR/campaign routing
- Local merchant data, redemption, join, or attribution behavior
- Life secure application / producer queue contracts
- CoverageFit launch or zero-repeat handoff behavior
- insurance eligibility, pricing, underwriting, or discount logic

## Deliberate exclusion
`/life-ops/` remains an internal producer workspace and is not part of the consumer UI-3 mobile convergence program.

## Next sprint
**408-UI-3.11 — Accessibility Certification**
