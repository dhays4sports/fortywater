# 408-UI-3.13.1B — Professional Programs Humanization

## Status
COMPLETE — HUMAN TRUST / PROFESSIONAL PROGRAMS

## Input baseline
`408-UI-3.13.1A — Human Trust Foundation`.

The certified UI-3.13 architecture, 408-INFRA-1.1 Pages Function boundary hotfix, Campaign Message-Match Convergence, Life campaign mode, and Human Trust Foundation remain authoritative.

## Objective
Use Healthcare, Teachers, Technology, and Engineers as the strongest calibration point for the Human Trust branch: preserve the modern UI-3 platform while bringing back the original occupational campaigns’ **exclusive yet human** quality.

Governing principle: **Profession and person first. System second.**

Life is excluded and remains untouched.

## Implemented
- Added `shared/professional-programs-human.css` as a scoped override layer for the four occupational routes only.
- Added a `408-UI-3.13.1B` route/body marker to the four Professional Program pages.
- Rebuilt each hero around one occupation identifier and the proven campaign hooks:
  - Healthcare — **Work in Healthcare?**
  - Teachers — **Are You a Teacher?**
  - Technology — **Work in Tech?**
  - Engineers — **Are You an Engineer?**
- Added occupation-specific professional portrait crops derived from the existing approved campaign artwork. Essential copy remains live HTML and is not embedded in the images.
- Added restrained warm-gold identity rules/kickers/check accents while keeping Farmers red as the only primary conversion color.
- Replaced pill-heavy hero reassurance with a plain editorial benefit list.
- Added a pre-submit Human Trust Signature: `Your review is handled by Dylan Haysbert`, with the existing certified phone/SMS destinations.
- Added an explicit `Check My Eligibility` hero action that scrolls to the existing form; no new form or endpoint was created.
- Replaced the large software-style role-context callout with a quiet eligibility/underwriting qualifier.
- Simplified form intro copy and visible submit wording while preserving all controls, required semantics, Formspree action, attribution fields, consent, and CoverageFit behavior.
- Removed the duplicative pre-submit `Meet Dylan` block inside the form card; the full agency credential close remains later on the page.
- Reduced component density in the payoff, steps, and agency close using editorial rules/spacing instead of additional cards.

## Campaign continuity
UI-3.11.1 Campaign Entry Registry and runtime are unchanged. Explicit campaign traffic still controls the approved campaign eyebrow/title/lead/form copy for the current entry only. Organic traffic receives the new Human Trust defaults. Unknown campaign values continue to fail to evergreen copy.

## Protected behavior
No change to:
- occupational role/select options
- form field names or required semantics
- Formspree endpoints
- `_worker.js` or `_routes.json`
- Campaign Entry Registry/runtime or attribution schema
- professional discount determination
- consent language
- CoverageFit invitation/handoff
- Local
- Home / Bundle / Buyer
- Life / Life Ops
- SMS/phone destinations
- pricing or underwriting logic

## Accessibility and performance
- Profession portraits have meaningful alt text and no essential text embedded in them.
- Human Trust typography and CTA remain live HTML.
- Gold used for text is the AA-oriented dark gold token; brighter gold is decorative only.
- Farmers red remains a white-text primary action with adequate contrast.
- 320px mobile, tablet, 1024px, and 1440px layouts are explicitly regression-tested for overflow and touch targets.
- Mobile text inputs remain 16px+ and primary controls remain 44px+.
- Reduced-motion and forced-colors handling are included.
- New professional WebP crops are each below 100 KB.

## Certification
See `UI3_13_1B_QA.json`, `UI3_13_1B_BROWSER_QA.json`, and `UI3_13_1B_RELEASE_CERTIFICATION.json`.

## Next sprint
**408-UI-3.13.1C — Core Insurance Humanization**

That sprint should apply a deliberately more restrained Human Trust treatment to Homepage, Home, Home + Auto, and Buyer. It should not copy the full occupational photography/gold treatment.
