# 408-UI-3.13 — Production Design Certification

## Status
COMPLETE — DEPLOYABLE-CERTIFIED UI-3 BASELINE

## Input baseline
This certification was intentionally completed from **408-INFRA-1.1 — Pages Function Invocation Boundary Hotfix**, which itself is the UI-3.12 certified product plus an additive Cloudflare Pages `_routes.json` invocation boundary.

The unrelated infrastructure hotfix is preserved in this final UI artifact. No pre-existing INFRA-1.1 file was replaced or rolled back. `_routes.json`, `SPRINT-408-INFRA-1.1.md`, `INFRA1_1_RELEASE_CERTIFICATION.json`, and its focused QA remain present.

## Goal
Close the UI-3.x redesign program by certifying the packaged 408FARMERS artifact for production deployment: final visual edge cases, responsive image delivery, metadata, asset integrity, performance budgets, behavior/form/config freeze, and release packaging.

UI-3.13 is a production-polish/certification sprint. It does **not** change insurance eligibility, pricing, form field contracts, Worker APIs, attribution schemas, Local merchant logic, Life secure-submission logic, CoverageFit handoff behavior, or the INFRA-1.1 function-invocation boundary.

## Production polish applied
### Metadata and indexing
- Added/normalized canonical URLs, Open Graph URLs/images, Twitter cards, theme colors, and robots directives across indexable platform routes.
- Added explicit `noindex` boundaries to fallback/receipt surfaces that should not become search landing pages.
- Added root `robots.txt` and `sitemap.xml`.
- Preserved `/life-ops/` and `/neighbor/` indexing restrictions.

### Responsive image delivery
Three high-visibility pages previously relied on a larger JPG as the primary browser image. UI-3.13 keeps those JPGs as compatibility/social fallbacks but adds production WebP delivery:
- Homepage: existing `home-420.webp` / `home-653.webp`
- Buyer: new `buyer-home-420.webp` / `buyer-home-595.webp`
- Life: new `life-family-campaign-420.webp` / `life-family-campaign-705.webp`

The certified visual geometry is preserved by explicit `<picture>` wrapper rules in the existing page-specific UI-3 stylesheets.

### INFRA-1.1 preserved
- `_routes.json` remains byte-identical to the uploaded INFRA-1.1 hotfix input.
- Static pages/assets and crawler garbage remain outside Pages Function invocation.
- `/api/*` and the intentional dynamic/redirect routes remain Function-owned.
- No `_worker.js` change was introduced by UI-3.13.
- Focused function-boundary QA: **22/22**.

### No functional rewrite
Exact runtime/data/config hashes remain frozen for **47/47** contract files from the hotfix input, and all **9/9** shipped HTML form contracts remain structurally identical.

## Production browser certification
`qa/test-408-ui-3.13-browser.py` certifies the finished presentation at:
- 320×568
- 390×844
- 768×1024
- 1024×768
- 1440×900

It covers the homepage, Home, Home + Auto, Buyer, all Professional Programs, Life, Local, Local Join, Contact, Protection Score, Privacy, Terms, completion pages, 404, and the referral bridge.

Result: **749/749**.

The suite verifies no horizontal overflow, visible main/H1 content, UI-3 shell enhancement, readable base typography, mobile-menu/touch geometry, primary CTA geometry, receipt edge cases, and responsive picture-frame geometry.

## Production metadata certification
`qa/test-408-ui-3.13-metadata.py`

Result: **216/216**.

Certified:
- unique usable titles/descriptions
- exact HTTPS canonicals
- index/noindex boundaries
- Open Graph URL/image integrity
- Twitter card presence on customer-acquisition surfaces
- theme color and zoom-safe viewport metadata
- `robots.txt`
- `sitemap.xml`

## Asset + performance certification
`qa/test-408-ui-3.13-assets.py`

Result: **99/99**.

Certified:
- public HTML local asset references resolve
- shared CSS `url()` references resolve
- production WebP images decode
- mobile hero candidates remain at or below 125 KiB
- desktop hero candidates remain at or below 155 KiB
- existing occupational/bundle `performance-budgets.json` limits remain satisfied
- primary-route uncompressed CSS+JS source stays below 300 KiB per route
- key brand assets decode and stay inside explicit encoded-size ceilings

## Behavior + form + infrastructure freeze
`qa/test-408-ui-3.13-freeze.py`

Result: **66/66**.

- exact runtime/data/config freeze: **47/47**
- shipped HTML form contracts: **9/9**
- `_routes.json` from INFRA-1.1 is included in the exact freeze
- intentional UI-3.13 product delta remains restricted to metadata, receipt indexing, responsive-media surfaces, page-specific CSS, final `VERSION`, and new production metadata/image assets

## JavaScript + link integrity
- Runtime JavaScript syntax: **41/41**
- Internal links/assets: **640 checked / 0 broken**

## Current functional regression retained
UI-3.13 also retains the completed UI-3.12 end-to-end regression and latest applicable suites:
- UI-3.12 E2E: **59/59**
- INFRA-1.1 Function Boundary: **22/22**
- Exact INFRA-1.1 hotfix preservation: **4/4**
- Campaign matching: **51/51**
- Campaign accessibility delta: **56/56**
- Homepage: **93/93**
- Home: **108/108**
- Home + Auto: **99/99**
- Buyer: **115/115**
- Professional Programs: **452/452**
- Life: **23/23**
- Local: **155/155**
- Utility surfaces: **293/293**
- Mobile: **822/822**
- Existing static regression: **296/296**
- Merchant Join Worker: **20/20**
- Local Attribution Worker: **29/29**
- Home hidden-required submit: **12/12**
- Home deep-route assets: **12/12**
- Advanced Mode redirect-loop: **10/10**
- Logo integration: **14/14**

See `UI3_13_REGRESSION_MATRIX.json`.

## Cross-browser/deployment boundary
The build sandbox provides Chromium for rendered runtime certification; separate Safari and Firefox engines are not available here. A deployed-domain smoke on current Safari/Firefox/Chrome remains an **activation check** after this ZIP is actually deployed.

Likewise, artifact generation does not deploy the build, so it cannot certify that the production domain is already serving these exact bytes, that live third-party endpoints accepted a production submission, or that Cloudflare production Function-request volume has already fallen. Follow `UI3_13_DEPLOYMENT_SMOKE_RUNBOOK.md` immediately after deployment.

## Parallel Local status
The existing LOCAL-1.10 planned three-merchant pilot remains production **NO-GO** until the real Auto + Home merchants and documented external closeout items are completed. UI-3.13 does not alter that operational boundary.

## Program result
**408-UI-3.x is complete.**

`408-UI-3.13 + 408-INFRA-1.1 + 408-UI-3.2.1` is the certified deployable baseline. Future customer-facing design changes should begin a new UI generation or an explicitly scoped maintenance/hotfix sprint.
