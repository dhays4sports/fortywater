# 408-LOCAL-1.6 — Local Attribution Engine

## Outcome

408FARMERS Local now has a privacy-safe attribution layer that can answer the questions the pilot actually needs to answer without turning merchant perks into gated lead generation.

The engine preserves a bounded Local first-touch origin, carries merchant/perk/surface/campaign context through Local navigation, emits the minimum five Local events, and can carry that same origin into a later voluntary 408FARMERS insurance request without asking the visitor to type the merchant or source again.

The Local offer remains independent. Analytics failure does not block directory browsing, merchant pages, perk viewing, show-your-screen redemption, merchant application, or insurance navigation.

## What this sprint adds

### 1. Privacy-safe Local origin context

New shared runtime:

`/shared/local-attribution.js`

Canonical context:

- `source=local`
- `partner_id`
- `perk_id`
- `merchant_slug`
- `surface`
- `campaign`
- `variant`
- `utm_source`
- `utm_medium`
- `utm_campaign`
- `utm_content`
- `utm_term`

The runtime accepts campaign-safe tokens only. Free-form values containing spaces, email-style values, URLs, query strings, addresses, or similar arbitrary text are rejected instead of being persisted or emitted.

No name, email, phone, business-application contact data, property address, insurance answers, offer-redemption details, or policy data is part of the Local analytics contract.

### 2. Bounded first-touch persistence

The browser stores only the normalized non-PII Local origin in:

`408farmers_local_attribution_v1`

Retention is bounded to 30 days.

This enables a visitor to:

1. discover 408FARMERS through a Local merchant or physical surface;
2. leave Local;
3. later reach a 408FARMERS insurance form;
4. retain the truthful Local merchant/surface origin without re-entering it.

An explicit new attribution query on the later insurance page takes precedence over the stored Local origin, preventing a prior Local touch from overwriting a new named campaign.

### 3. Merchant and physical-surface propagation

Directory merchant links now carry structured merchant identifiers into canonical:

`/local/{merchant-slug}/`

routes.

The engine is prepared for tokenized surfaces such as:

- `merchant_counter`
- `merchant_window`
- `coaster_table`
- `receipt_insert`
- `realtor_material`
- `new_homeowner_material`

The system does not require a hardcoded surface allowlist in order to support future physical placements, but all accepted values must remain campaign-safe tokens.

### 4. Minimum Local event contract

The exact consumer event set added in this sprint is:

- `local_view`
- `merchant_view`
- `perk_open`
- `perk_redeem_intent`
- `insurance_cta_click`

Events are emitted to both:

- `window.dataLayer`
- the `408farmers:local-event` custom DOM event

and are sent non-blockingly to:

`POST /api/local/event`

The event transport never gates UX.

### 5. Merchant-view attribution

The directory renders merchant links with machine-readable:

- partner/merchant ID;
- merchant slug;
- currently active perk ID when available.

The merchant page then:

- confirms the active public merchant from the validated 1.2 catalog;
- attaches that merchant to Local origin if no earlier merchant origin exists;
- emits `merchant_view`;
- emits `perk_open` when a current active perk exists;
- emits `perk_redeem_intent` when the visitor taps `Use This Perk`.

The show-your-screen redemption payload itself is not sent to analytics.

### 6. Insurance CTA measurement without adding the 1.7 bridge

Existing insurance links on Local directory/merchant pages are explicitly marked as Local insurance CTAs.

Clicking one:

- emits `insurance_cta_click`;
- records only the bounded destination token (`insurance_root`, `home`, `auto_bundle`, or `life`);
- decorates the same-origin destination with Local context.

This sprint does **not** add the dedicated post-perk homeowner/home+auto conversion module. That remains 408-LOCAL-1.7.

### 7. Durable same-origin event collector

New Worker endpoint:

`POST /api/local/event`

The endpoint:

- accepts JSON only;
- requires same-origin browser delivery;
- requires `X-Local-Event-Version: 1`;
- enforces a small body limit;
- exact-key validates the payload;
- allows only the five certified Local event names;
- validates UUID event/session identifiers;
- accepts only campaign-safe context tokens;
- accepts only Local routes;
- does not read or store IP address, user agent, contact identity, property address, insurance answers, or merchant-application contact data.

When a D1 binding exists, events are stored in a dedicated `local_attribution_events` table.

Preferred binding:

`LOCAL_ANALYTICS_DB`

Deployment-compatible fallback:

`LIFE_QUEUE_DB`

If neither binding is available or persistence fails, the endpoint returns a non-blocking accepted response with `persisted:false`. Public Local behavior continues normally, and the `dataLayer` / DOM-event instrumentation remains available.

### 8. Existing lead-form attribution compatibility

The shared 408FARMERS lead controller now accepts these Local query fields:

- `source`
- `partner_id`
- `perk_id`
- `merchant_slug`
- `surface`
- `campaign`
- `variant`
- existing campaign ID/variant fields;
- standard UTMs.

Missing hidden fields are created only when attribution is actually present.

If no explicit attribution exists on the later insurance page, a still-valid Local context can populate those hidden fields from the bounded Local storage record.

This means the Formspree lead itself can retain Local origin without a second lead form.

### 9. CoverageFit sender continuity

The shared CoverageFit launcher now recognizes Local attribution fields as pass-through context.

When the truthful acquisition source is Local:

`source=local`

is preserved into the CoverageFit transition instead of being replaced by the generic sender source.

The launcher can also recover a valid stored Local origin when the visitor reaches an insurance form without Local query parameters, while explicit current campaign parameters still win.

No CoverageFit assessment questions, scoring, recommendation logic, or consultation behavior changed in this sprint.

## Analytics privacy boundary

Allowed Local analytics values are identifiers and campaign tokens only.

Explicitly excluded:

- consumer name;
- email;
- phone;
- residential/property address;
- insurance answers;
- policy/carrier/premium data;
- merchant application contact information;
- proposed merchant application notes;
- exact perk redemption details;
- free-form browser URL/query payloads;
- IP address;
- user agent.

## Files added

- `shared/local-attribution.js`
- `SPRINT-408-LOCAL-1.6.md`
- `LOCAL1_6_ATTRIBUTION_CONTRACT.json`
- `qa/test-408-local-1.6.js`
- `qa/test-408-local-1.6-worker.mjs`
- `LOCAL1_6_QA.json`
- `LOCAL1_6_WORKER_QA.json`
- `LOCAL1_6_RELEASE_CERTIFICATION.json`

## Files intentionally changed

- `local/index.html` — loads the Local attribution runtime, advances the Local build marker, and marks existing insurance links for privacy-safe CTA attribution.
- `local/detail/index.html` — loads the attribution runtime, advances the detail build marker, and marks insurance links.
- `shared/local-directory.js` — gives generated merchant links bounded merchant/perk identifiers and decorates them with Local context.
- `shared/local-merchant.js` — attaches confirmed merchant context and emits merchant/perk/redemption-intent events.
- `shared/script.js` — carries Local context into later 408FARMERS lead submissions, including bounded storage recovery when no new attribution query exists.
- `shared/coveragefit-launch.js` — passes Local origin through the existing zero-repeat sender path.
- `_worker.js` — adds `/api/local/event` and optional D1 persistence.
- `408-LOCAL-ROADMAP.md`, `ROADMAP.md`, `CHANGELOG.md`, `README.txt`, `VERSION` — sprint progression and continuation.

## Preserved

- `local/data/catalog.json` unchanged;
- `local/data/catalog.schema.json` unchanged;
- no real merchant activation;
- no live merchant perk activation;
- merchant join flow remains 408-LOCAL-1.5 and does not feed merchant contact data into consumer analytics;
- no consumer login/account;
- no quote or policy purchase gate on Local;
- no redemption identity capture;
- no automatic CoverageFit launch from Local;
- no new Local insurance conversion module yet;
- no insurance pricing, discount, eligibility, underwriting, or coverage behavior changed;
- no CoverageFit assessment/scoring changes.

## Next sprint

**408-LOCAL-1.7 — Insurance Conversion Bridge**

Add the first explicit optional insurance pathway only after merchant value has been delivered, using the certified 1.6 attribution engine. The intended first module is a restrained South Bay homeowner / Home + Auto review invitation on the merchant detail experience. It must not gate or condition the merchant perk, must not create a duplicate lead, and must not automatically launch CoverageFit.
