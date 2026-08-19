# 408-UI-3.7 — Life Campaign + Platform Convergence

## Status
COMPLETE

## Goal
Preserve the distinctive cinematic identity of the Farmers Life paid-social campaign while integrating `/life/` into the unified 408FARMERS UI-3 platform shell. The Life route remains the deliberate visual exception: campaign continuity first, platform consistency underneath.

## Design direction
The LIFE experience now uses a dedicated **408FARMERS Life Mode**:

- UI-3 compact navigation and universal footer remain the platform anchors
- black / deep-navy campaign canvas
- oversized white campaign typography
- Farmers red urgency / action accents
- Farmers Life blue as a restrained supporting accent
- warm family photography derived from the approved campaign creative
- campaign-matched hero messages for the existing A/B/C/D creative variants
- the existing 20-minute application expectation and potential same-day decision qualifier remain visible
- the intake becomes a high-readability white working surface inside the cinematic dark environment
- supporting "why now" content is simplified into a campaign-style editorial section instead of generic SaaS cards
- Dylan / agency credibility remains visible inside the dark Life environment

## Campaign message matching retained
The existing `shared/life-campaign.js` attribution and routing contract remains intact. Only visible creative copy was tightened to match the campaign more directly:

- **A — Before Anything Changes**
  - `Before anything changes.`
  - `Life changes. Health changes. Eligibility can too.`
  - `Life insurance is something you want to take care of before you need it.`
- **B — 20 Minutes**
  - `20:00`
  - application-time framing
  - potential same-day decision qualifier for eligible applicants
- **C — This Is the Time**
  - `This is the time.`
  - `Not after a diagnosis. Not after a health change. While life is normal.`
- **D — Financial Picture**
  - existing financial-picture variant remains supported

Variant resolution, creative codes, UTM/campaign keys, first-party conversion measurement, and memory-only attribution behavior are unchanged.

## Application UX principle
The campaign earns attention; the application must earn completion. Once the visitor starts, visual drama recedes and the existing secure intake is presented as a clear white task surface with:

- unchanged six-step secure flow
- unchanged field names and required semantics
- unchanged dedicated application-start endpoint
- unchanged SSN-last-4 boundary
- unchanged application acknowledgement
- unchanged privacy language
- unchanged producer queue delivery

## Added assets
- `shared/life-campaign-platform.css`
- `shared/assets/life-family-campaign.jpg`

The family image is a crop of the previously approved campaign visual supplied in the project conversation. It is used as campaign continuity artwork, not as a new claim or functional surface.

## Behavioral preservation
UI-3.7 intentionally does **not** change:

- `_worker.js`
- `/api/life/application-init`
- `/api/life/conversion`
- producer queue / encryption / audit behavior
- LIFE conversion event names or schema
- attribution key allowlist
- campaign variant keys / creative codes
- browser-storage privacy boundary
- `shared/life-conversion.js`
- `shared/life-intake.js`
- `shared/life-secure-submit.js`
- secure application form markup / field inventory
- policy / underwriting qualification language
- `life/thank-you.html` (reserved for UI-3.9 completion-surface convergence)
- any non-Life public route

## Compliance / message boundary
The page continues to qualify all time and underwriting language:

- application time may vary
- same-day decision is potential and only for eligible applicants
- coverage remains subject to underwriting, policy terms, acceptance, availability, and required premium
- no coverage is represented as in force by completing the site flow

## Next sprint
**408-UI-3.8 — Local Visual Convergence**
