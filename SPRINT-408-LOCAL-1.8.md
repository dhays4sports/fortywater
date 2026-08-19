# 408-LOCAL-1.8 — 408FARMERS Site Integration

## Outcome

408FARMERS Local is now discoverable from the broader 408FARMERS site without inserting merchant-perk distractions into active insurance forms or CoverageFit. The integration is intentionally strongest on broad discovery and completed-request surfaces: the homepage navigation, a lower-page Local module, the homepage footer, property-review fallback receipts, and the completed homebuyer receipt.

The primary homeowner/insurance conversion architecture remains unchanged. Local is an optional secondary destination and public merchant perks remain independent of insurance quote, purchase, pricing, eligibility, underwriting, coverage, or lead submission.

## What this sprint adds

### 1. Homepage/global discovery

The root 408FARMERS navigation now includes a `Local` link alongside existing site navigation. The link does not replace or visually outrank the header call action or homepage Coverage Review CTA.

### 2. Lower-page 408FARMERS Local module

A dedicated lower-page module appears after the professional-program section and before the Dylan/agency contact section. It introduces:

- 408FARMERS Local as a separate community layer;
- the three pilot categories: Eat & Drink, Home, and Auto;
- a single primary `Explore 408FARMERS Local` action;
- a secondary merchant-pilot join link;
- explicit `No insurance purchase or quote required` language.

The module is deliberately below all primary insurance intent selection and CoverageFit explanation content.

### 3. Homepage footer integration

The homepage footer now contains a dedicated Local column with:

- `Explore Local`;
- `For businesses`.

The footer expands responsively from four columns to two and then one without changing the insurance-review link hierarchy.

### 4. Post-submission value modules

Local is offered only after request receipt on the property-oriented fallback receipt pages:

- Home;
- Home + Auto;
- Healthcare;
- Teachers;
- Technology;
- Engineers.

The module appears after the existing request receipt/next-steps content. It contains no lead form, no quote CTA, no policy-purchase condition, and no automatic CoverageFit launch.

### 5. Selected homebuyer completion integration

`/buyer/thank-you.html` receives a homebuyer-specific Local module after the buyer request receipt. The active buyer intake page is unchanged. This gives the realtor/homebuyer ecosystem a useful post-request community destination without introducing Local into the closing-intent form itself.

### 6. Site-entry attribution surfaces

Internal entry links use token-safe Local attribution context so the existing 408-LOCAL-1.6 engine can distinguish discovery surfaces such as:

- `global_nav`;
- `homepage_local_module`;
- `homepage_footer`;
- `post_submit_home`;
- `post_submit_auto_bundle`;
- occupational post-submit surfaces;
- `buyer_completion`.

No new analytics event names, identity fields, or PII transport are added.

## Files added

- `shared/local-site-integration.css`
- `SPRINT-408-LOCAL-1.8.md`
- `LOCAL1_8_SITE_INTEGRATION_CONTRACT.json`
- `qa/test-408-local-1.8.js`
- `LOCAL1_8_QA.json`
- `LOCAL1_8_MARKUP_QA.json`
- `LOCAL1_8_RELEASE_CERTIFICATION.json`

## Files intentionally changed

- `index.html` — root navigation, lower-page Local module, footer Local column, isolated integration stylesheet.
- `home/thank-you.html`
- `auto-bundle/thank-you.html`
- `healthcare/thank-you.html`
- `teachers/thank-you.html`
- `tech/thank-you.html`
- `engineers/thank-you.html` — post-submission Local value module only.
- `buyer/thank-you.html` — selected homebuyer completion Local value module only.
- `local/index.html`, `local/detail/index.html` — current Local release marker only.
- `408-LOCAL-ROADMAP.md`, `ROADMAP.md`, `CHANGELOG.md`, `README.txt`, `VERSION` — sprint progression and continuation.

## Explicitly not changed

- active Home, Home + Auto, Buyer, occupational, Life, landlord, business, or contact intake UX;
- any insurance form field, consent, validation, Formspree transport, or lead submission behavior;
- CoverageFit launch logic, assessment, consultation, Protection Score, or report behavior;
- Local merchant catalog, schema, lifecycle rules, join application, redemption runtime, or attribution runtime;
- Cloudflare Worker routes;
- public merchant/perk activation state;
- insurance pricing, discounts, eligibility, underwriting, coverage, or policy economics.

## Next sprint

**408-LOCAL-1.9 — Pilot Merchant Launch**

Validate and load the first three real participating businesses and merchant-owned offers, generate merchant/surface QR campaigns, verify physical scans and redemption, and train pilot merchant staff without changing the frozen Local/insurance boundary.
