# 408-LOCAL-1.4 — Merchant Perk Detail + Redemption

## Outcome

408FARMERS Local now has a reusable canonical merchant-detail and MVP redemption experience at:

`/local/{merchant-slug}/`

The detail route consumes the same validated 408-LOCAL-1.2 catalog used by the discovery directory. No merchant page is hardcoded, and no personal information, account, insurance quote, or insurance lead submission is required to view or use an active merchant perk.

No real merchant or live offer is activated in this sprint. The three existing fixture merchants remain `draft`, `fixture:true`, and non-public. The new runtime is production-ready for approved merchants when 408-LOCAL-1.9 loads real pilot records.

## What this sprint adds

### 1. Canonical merchant routing

Cloudflare Pages Advanced Mode now recognizes one-segment Local merchant URLs:

`/local/{slug}/`

No-trailing-slash merchant paths are normalized with a 308 redirect. A single reusable `/local/detail/` asset renders the public merchant page while the browser remains on the canonical merchant URL.

Reserved Local infrastructure routes (`data`, `detail`, and the future `join` route) are excluded from merchant-slug routing.

### 2. Reusable merchant detail runtime

New runtime:

`shared/local-merchant.js`

The runtime:

- validates and loads the canonical Local catalog;
- resolves only active, non-fixture merchants;
- derives the merchant slug from the public URL;
- renders merchant name, category, neighborhood, descriptions, image/logo, address/area, website, Instagram, and directions when available;
- updates page title, description, canonical metadata, and social metadata client-side;
- fails closed when a merchant is draft, paused, inactive, fixture-only, missing, or the catalog is unavailable.

### 3. Directory → merchant handoff

Active directory cards now include a canonical merchant-page action:

- `View Local perk` when a current active perk exists;
- `View business` when the merchant is active but the offer is unavailable.

The directory still does not redeem inline. The full perk, terms, and redemption state live on the canonical merchant page.

### 4. Current perk detail

When the merchant has an active, in-window perk, the page renders:

- current perk headline;
- summary;
- merchant-specific terms;
- independent-offer language;
- `Use This Perk` action;
- explicit reassurance that no account or insurance form is required.

Scheduled, expired, paused, draft, and inactive perks cannot expose the redemption action.

### 5. Frictionless MVP redemption

For an active perk:

`Use This Perk` → show-your-screen redemption dialog.

The redemption screen includes:

- 408FARMERS Local Perk identity;
- participating merchant name;
- exact currently published perk headline and summary;
- merchant terms;
- clear `Ready to show` state;
- independent-offer / no-insurance-purchase language;
- close controls with focus returned to the initiating button.

This is intentionally not a coupon wallet, account system, POS integration, one-time token, or redemption database. Those capabilities remain deferred to Generation 2 after real pilot use exists.

### 6. Merchant / insurance separation

The 1.1–1.3 boundary remains frozen:

- no insurance purchase required;
- no insurance quote required;
- no CoverageFit assessment required;
- no insurance lead form before or during redemption;
- no consumer identity capture;
- no change to insurance pricing, discounts, eligibility, underwriting, or coverage;
- no Farmers/408FARMERS endorsement or certification claim about merchant quality.

The merchant controls fulfillment, offer availability, and its terms.

## Production state

Because the production catalog still contains only three draft fixtures:

- `/local/` remains the intentional pilot empty state;
- fixture slugs cannot resolve into public detail view models;
- no real business name or live perk claim is published;
- the merchant-detail/redemption framework is ready for approved pilot data later.

## Files added

- `local/detail/index.html`
- `shared/local-merchant.js`
- `SPRINT-408-LOCAL-1.4.md`
- `LOCAL1_4_REDEMPTION_CONTRACT.json`
- `qa/test-408-local-1.4.js`
- `LOCAL1_4_QA.json`
- `LOCAL1_4_RELEASE_CERTIFICATION.json`

## Files intentionally changed

- `local/index.html` — advances build marker/copy for merchant detail availability.
- `shared/local-directory.js` — adds canonical merchant-page links.
- `shared/local.css` — adds merchant detail and redemption UI.
- `_worker.js` — adds safe canonical `/local/{slug}/` routing.
- `408-LOCAL-ROADMAP.md` / `ROADMAP.md` / `CHANGELOG.md` / `VERSION` — sprint progression.

## Preserved

- `local/data/catalog.json` unchanged;
- `local/data/catalog.schema.json` unchanged;
- `shared/local-data-model.js` unchanged;
- no real merchant activation;
- no insurance acquisition HTML/JS changes;
- no CoverageFit changes;
- no Local account/login system;
- no merchant application form yet.

## Next sprint

**408-LOCAL-1.5 — Merchant Join Flow**

Build `/local/join/` so a South Bay merchant can submit the business/contact/offer information needed for pilot review without Dylan reconstructing applications manually.
