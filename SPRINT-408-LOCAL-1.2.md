# 408-LOCAL-1.2 — Merchant Data Model

## Outcome

408FARMERS Local now has a reusable, validated merchant/perk source-of-truth contract without activating a public merchant directory or any live merchant offer.

This sprint turns the Local foundation into a data-driven system that later sprints can render, attribute, and eventually migrate to Cloudflare-backed storage without changing consumer merchant URLs.

## What this sprint adds

### 1. Versioned Local catalog

Canonical source:

`local/data/catalog.json`

The catalog has two normalized collections:

- `merchants[]`
- `perks[]`

Perks reference merchants through stable `merchant_id` values rather than nesting merchant profile data into each offer.

### 2. Merchant model

Required merchant fields:

- `merchant_id`
- `name`
- `slug`
- `category`
- `neighborhood`
- `city`
- `address_display`
- `description_short`
- `description_long`
- `website_url`
- `instagram_url`
- `image`
- `logo`
- `status`
- `featured`
- `sort_order`

The current pilot categories remain:

- `eat-drink`
- `home`
- `auto`

Merchant lifecycle statuses are:

- `draft`
- `active`
- `paused`
- `inactive`

### 3. Perk model

Required perk fields:

- `perk_id`
- `merchant_id`
- `headline`
- `summary`
- `terms`
- `start_at`
- `end_at`
- `evergreen`
- `status`
- `redemption_method`
- `independent_offer_text`

Supported initial redemption methods:

- `show_screen`
- `merchant_code`
- `merchant_instruction`

### 4. Active-offer resolver

`shared/local-data-model.js` now determines whether a perk is actually renderable.

An offer cannot resolve active when it is:

- draft;
- paused;
- inactive;
- scheduled for the future;
- expired.

Public discovery also requires the parent merchant to be active.

### 5. Insurance/perk independence enforcement

Every perk must carry the sentence:

> No insurance purchase or quote required.

The model rejects common copy patterns that imply a participating merchant is recommended, preferred, approved, certified, vetted, or endorsed by Farmers Insurance or 408FARMERS.

This is a product/data guardrail, not a substitute for Farmers/agency advertising review before public activation.

### 6. Stable merchant routes

Each merchant receives a canonical slug contract:

`/local/{merchant-slug}/`

The durable internal key remains `merchant_id`; display-name changes do not require an ID change. The model is intentionally compatible with a later static → Cloudflare KV/D1 migration without changing this consumer URL contract.

### 7. Three non-public fixtures

The catalog includes one fixture for each pilot category:

- Eat & Drink
- Home
- Auto

All fixtures are explicitly marked `fixture:true` and `status:draft`. Their perks are also draft. They are not rendered on `/local/` and do not represent real participating businesses or real offers.

The QA harness joins and renders all three through the same schema/view-model/renderer pipeline, proving that future merchant cards do not require duplicated merchant markup or merchant-specific code.

## Deliberate exclusions

This sprint does **not** add:

- a public merchant directory;
- public merchant cards;
- live merchant detail pages;
- real merchants or offers;
- consumer redemption;
- merchant application intake;
- Local analytics/attribution events;
- insurance conversion CTAs;
- global 408FARMERS Local navigation integration beyond the existing `/local/` foundation.

Those remain sequenced in later sprints.

## Files added

- `local/data/catalog.json`
- `local/data/catalog.schema.json`
- `local/data/README.md`
- `shared/local-data-model.js`
- `LOCAL1_2_DATA_CONTRACT.json`
- `LOCAL1_2_QA.json`
- `LOCAL1_2_RELEASE_CERTIFICATION.json`
- `SPRINT-408-LOCAL-1.2.md`
- `qa/test-408-local-1.2.js`

## Existing runtime boundary

The existing `/local/` HTML, Local CSS, Cloudflare Worker, insurance acquisition HTML/JavaScript, and CoverageFit behavior are unchanged from 408-LOCAL-1.1.

This is intentional: 1.2 creates the model before 1.3 turns it into a public directory.

## QA

Run:

```bash
node qa/test-408-local-1.2.js
node qa/test-408-local-1.1.js
node qa/test-b1.2d.js
python3 qa/test-static.py
python3 qa/check-links.py
node qa/test-advanced-mode-redirect-loop-hotfix.js
node qa/test-home-2.7-worker-routing.js
```

## Next sprint

**408-LOCAL-1.3 — Merchant Discovery Directory**

Consume the validated 1.2 model on `/local/` to create the real active-merchant discovery experience, including category filtering, active/paused/expired handling, featured state, image/logo fallbacks, neighborhood labels, useful empty states, and mobile category controls where warranted.
