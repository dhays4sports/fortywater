# 408-UI-3.8 — Local Visual Convergence

## Status
COMPLETE

## Goal
Bring the real 408FARMERS Local directory, merchant detail/redemption, and merchant join experience into the restrained UI-3 platform language established by the approved Local reference mockup, without inventing unsupported Local functionality or changing any Local/insurance behavioral contract.

## Visual convergence delivered
- compact UI-3 platform introduction instead of an oversized campaign-style Local hero
- directory promoted immediately after the Local introduction
- pill category filters and compact directory status
- restrained merchant cards with smaller radii, lighter borders/shadows, and clearer current-perk hierarchy
- CSS-only merchant fallback artwork when no merchant-owned image/logo is available
- compact explanatory, compliance-boundary, and merchant-recruitment surfaces
- merchant detail redesigned around merchant identity first, perk second, and optional insurance bridge third
- redemption dialog redesigned as a clean show-your-screen credential
- merchant join page aligned with the reference form architecture and UI-3 field/card system
- phone, tablet, desktop, short-landscape, reduced-motion, and forced-colors handling

## Reference-mockup discipline
The approved mockup is treated as a visual reference, not a feature specification. UI-3.8 intentionally does **not** add:
- distance-to-merchant calculations
- browser geolocation requests
- star ratings or review counts
- map widgets
- merchant account/login requirements
- consumer accounts
- merchant imagery that is not already merchant-owned and present in the Local catalog
- new redemption mechanics

When a merchant has no image or logo in the catalog, Local uses a branded CSS fallback rather than fabricated merchant photography.

## Directory composition
`/local/` now leads with:
1. compact 408FARMERS Local introduction
2. active merchant directory and filters
3. how-it-works explanation
4. Local/insurance separation boundary
5. merchant join invitation

The directory data source, active/draft/fixture filtering, category filtering, attribution decoration, and error handling remain unchanged.

## Merchant detail / redemption
The dynamic `/local/{merchant}/` renderer remains unchanged. UI-3.8 only changes presentation around the existing generated markup:
- merchant identity + area + external links
- current merchant-owned perk
- `Use This Perk` show-your-screen redemption
- merchant terms and independent-offer language
- explicit Local/insurance separation
- optional Home / Home + Auto bridge after the merchant perk

No identity form is inserted before perk use.

## Merchant join
The `/local/join/` application contract is unchanged:
- same fields and required semantics
- same acknowledgements
- same honeypot
- same proxy endpoint
- same Formspree fallback
- same success destination
- no auto-publishing of merchants/offers

Only layout and styling converge with UI-3.

## Protected runtime files
UI-3.8 does not modify:
- `_worker.js`
- `shared/local-data-model.js`
- `shared/local-directory.js`
- `shared/local-merchant.js`
- `shared/local-attribution.js`
- `shared/local-join.js`
- `local/data/catalog.json`
- Local QR assets / pilot campaign manifests
- Home, Home + Auto, Buyer, Life, Professional Programs, CoverageFit, or other non-Local product routes

## Local operational status
LOCAL-1.10 remains technically certified with the existing production **NO-GO** for the planned three-merchant pilot until real Auto + Home merchants and the external closeout items are completed. UI-3.8 does not alter that status.

## Added asset
- `shared/local-visual-convergence.css`

## Next sprint
**408-UI-3.9 — Utility + Completion Surfaces**
