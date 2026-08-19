# 408-UI-3.2.1 — Homepage Conversion Identity Alignment

## Status
COMPLETE

## Purpose
Preserve the UI-3.2 platform redesign while restoring the strongest conversion identity from the original 408FARMERS homepage. This sprint is intentionally narrow and is built on top of the 408-UI-3.3 package; the Home Conversion Experience remains intact.

## Changes
- Restored the primary homepage identity: **Insurance That Fits.**
- Restored the positioning line: **Start with a Coverage Review. Not a quote.**
- Reframed the primary chooser around **What brought you here today?** instead of insurance-product taxonomy.
- Added six situation-first paths:
  - buying a home
  - reviewing current coverage / second opinion / renewal change
  - shopping home + auto / bundle options
  - protecting a business
  - reviewing a rental property
  - protecting family / life responsibilities
- Preserved the four Home / Home + Auto / Buyer / Life product routes as a visually secondary browsing layer.
- Elevated CoverageFit into the hero identity, primary chooser bridge, and an earlier full explanation section.
- Preserved the existing **something changed** review psychology and reasons section.
- Retained UI-3.1/3.2 navigation, cards, Local integration, footer, spacing, typography, and visual polish.

## Behavior freeze
No Worker, form, submission, attribution, CoverageFit launch, Local runtime, Buyer, Life, or Home conversion contracts were changed. All pre-existing homepage href destinations and tracked anchor contracts remain available.

## New files
- `shared/homepage-conversion-identity.css`
- `UI3_2_1_HOMEPAGE_IDENTITY_CONTRACT.json`
- `UI3_2_1_QA.json`
- `UI3_2_1_BROWSER_QA.json`
- `UI3_2_1_RELEASE_CERTIFICATION.json`
- `qa/test-408-ui-3.2.1.py`
- `qa/test-408-ui-3.2.1-browser.py`

## Next sprint
**408-UI-3.4 — Home + Auto Conversion Experience**
