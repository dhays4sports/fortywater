# 408-LOCAL-1.5 — Merchant Join Flow

## Outcome

408FARMERS Local now has a repeatable merchant-acquisition workflow at:

`/local/join/`

A South Bay business can submit the information needed for pilot review without Dylan reconstructing business/contact/offer details from text messages or email threads. The application remains explicitly separate from insurance purchase, quoting, renewal, coverage, underwriting, and commercial insurance placement.

No application automatically activates a merchant or offer in the 1.2 catalog. Real merchant publication remains owned by 408-LOCAL-1.9.

## What this sprint adds

### 1. Canonical merchant join route

New public route:

`/local/join/`

The route uses the established 408FARMERS Local visual system and is linked directly from the `/local/` “For South Bay businesses” module. `/local/join` normalizes to the canonical trailing-slash route in Cloudflare Advanced Mode.

### 2. Structured pilot intake

The application collects:

- business name;
- contact name;
- email;
- phone;
- pilot category;
- business location;
- optional website/social profile;
- proposed Local perk;
- optional notes;
- authorization acknowledgment;
- insurance-separation / no-guarantee acknowledgment.

The form does not ask for insurance carrier, renewal date, premium, policy details, commercial coverage, or an insurance quote request.

### 3. Merchant-facing program boundaries

The page makes the operating model explicit before submission:

- no cost to apply;
- pilot participation is free if accepted under the current model;
- merchant proposes and remains responsible for its offer and terms;
- applying does not guarantee acceptance or publication;
- Local participation is not conditioned on buying or quoting insurance;
- no promise of referrals, lead volume, sales, or insurance business;
- Local inclusion does not state or imply Farmers/408FARMERS endorsement or certification of merchant quality.

### 4. Dedicated secure delivery route

New endpoint:

`POST /api/local/merchant-application`

The Cloudflare Worker:

- accepts same-origin HTML form submissions only;
- caps body size;
- rejects the honeypot field;
- allowlists/sanitizes expected merchant-application fields;
- validates required contact/category/acknowledgment data;
- does not log request fields or PII;
- relays the normalized application to Formspree;
- supports a future dedicated `LOCAL_MERCHANT_FORMSPREE_ENDPOINT` environment variable;
- otherwise preserves the existing `FORMSPREE_ENDPOINT` / production default.

This creates operational separation from the consumer form contract without requiring a new external service before the pilot proves demand.

### 5. Resilient browser submission

`shared/local-join.js` progressively enhances the HTML form:

- standard browser validation remains available even if JavaScript fails;
- landing page and standard UTM fields are populated without adding consumer Local analytics;
- successful same-origin relay redirects to the branded receipt page;
- server-side delivery failures can fall back to the form’s direct Formspree action;
- invalid 4xx responses stay on-page for correction rather than bypassing validation;
- submit state is announced through an accessible live region.

### 6. Branded receipt

New page:

`/local/join/thank-you.html`

It confirms receipt while reiterating that nothing publishes automatically, no insurance obligation was created, and directory placement is not guaranteed.

## Privacy and scope boundary

This sprint captures the business contact information necessary to review a merchant application because the merchant explicitly submits it for that purpose.

It does **not** implement 408-LOCAL-1.6 consumer attribution events. Merchant application contact data must never be copied into public analytics payloads.

## Files added

- `local/join/index.html`
- `local/join/thank-you.html`
- `shared/local-join.js`
- `SPRINT-408-LOCAL-1.5.md`
- `LOCAL1_5_JOIN_CONTRACT.json`
- `qa/test-408-local-1.5.js`
- `qa/test-408-local-1.5-worker.mjs`
- `LOCAL1_5_QA.json`
- `LOCAL1_5_WORKER_QA.json`
- `LOCAL1_5_RELEASE_CERTIFICATION.json`

## Files intentionally changed

- `local/index.html` — advances Local build marker and routes merchant interest to `/local/join/`.
- `shared/local.css` — adds scoped join-form and receipt styles.
- `_worker.js` — adds canonical join routing and the dedicated merchant-application relay.
- `408-LOCAL-ROADMAP.md` / `ROADMAP.md` / `CHANGELOG.md` / `VERSION` — sprint progression.

## Preserved

- `local/data/catalog.json` unchanged;
- `local/data/catalog.schema.json` unchanged;
- `shared/local-data-model.js` unchanged;
- `shared/local-directory.js` unchanged;
- `shared/local-merchant.js` unchanged;
- no real merchant activation;
- no Local offer automatically created from a submitted application;
- no consumer account/login system;
- no insurance acquisition HTML/JS changes;
- no CoverageFit changes;
- no insurance CTA added to merchant perk redemption;
- no promise of merchant leads/referrals or sales.

## Next sprint

**408-LOCAL-1.6 — Local Attribution Engine**

Measure Local discovery and preserve merchant/surface origin when a visitor later voluntarily chooses an insurance pathway, using privacy-safe non-PII events and without gating merchant value.
