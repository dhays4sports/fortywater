# 408-LOCAL-1.3 — Merchant Discovery Directory

## Outcome

`/local/` is now a real data-driven discovery surface instead of a program-only foundation page.

The directory consumes the canonical 408-LOCAL-1.2 merchant/perk catalog, automatically excludes fixtures and non-active merchants, exposes category filters for the three pilot categories, supports featured merchant presentation, and handles active/scheduled/paused/expired offer states without misrepresenting an unavailable perk as active.

No real pilot merchant is activated in this sprint. The existing three fixture merchants remain draft/non-public. The production directory therefore ships with an intentional pilot empty state until 408-LOCAL-1.9 loads approved real merchant records.

## What this sprint adds

### 1. Live directory runtime

New runtime:

`shared/local-directory.js`

The directory loads:

`/local/data/catalog.json`

through the validated 408-LOCAL-1.2 `LocalDataModel` helper. Invalid or unavailable catalog data fails closed with a directory-only recovery message; existing insurance routes are not affected.

### 2. Public directory section

`/local/` now contains:

- an active merchant grid;
- All / Eat & Drink / Home / Auto category controls;
- an accessible live merchant/perk count;
- merchant neighborhood metadata;
- featured state;
- merchant image/logo handling with a branded fallback when no asset exists;
- a no-active-perk state for active merchants whose offer is paused, scheduled, expired or otherwise unavailable;
- useful global and category empty states;
- no consumer login or lead form.

### 3. Merchant discovery card

A merchant can be understood from one card. The reusable card renderer supports:

- merchant name;
- category;
- neighborhood;
- short description;
- current active perk when one exists;
- explicit `No active offer right now` treatment when one does not;
- expandable business details;
- merchant website / Instagram when supplied;
- independent-offer language on active perk details.

The expandable disclosure lets a visitor choose and inspect a merchant without creating the full merchant-detail/redemption route that belongs to 408-LOCAL-1.4.

### 4. Featured state

Active `featured:true` merchants sort before ordinary active merchants, then continue to honor the existing `sort_order` contract.

Featured is a Local presentation state only. It must not be described as a Farmers endorsement, recommendation, certification or quality judgment.

### 5. Lifecycle handling

Public discovery rules now operate as follows:

- `merchant.status=active` → merchant may appear;
- `draft`, `paused`, `inactive` merchant → hidden;
- `fixture:true` merchant → always hidden;
- active merchant + active in-window perk → current perk displayed;
- active merchant + draft/paused/inactive/scheduled/expired perk → merchant may remain discoverable, but the offer is clearly unavailable and is never rendered as current.

This keeps merchant discovery independent from perk lifecycle changes.

### 6. Mobile category controls

The filter row becomes horizontally scrollable on narrow screens rather than compressing touch targets. Buttons retain at least a 44-pixel interaction height and native keyboard/button behavior.

### 7. Fail-closed public behavior

If the Local catalog cannot load or validate, `/local/` shows a bounded directory-only unavailable state. No fixture data is revealed, no stale offer is guessed, and no insurance flow is modified.

## Explicitly not included

This sprint does **not** add:

- real participating merchants;
- a merchant redemption screen;
- `/local/{merchant-slug}/` detail pages;
- Local analytics or attribution;
- insurance CTAs inside merchant cards;
- merchant application intake;
- consumer accounts;
- POS integrations;
- customer identity collection.

Those remain assigned to later roadmap sprints.

## Production state at release

The production catalog still contains only the three 408-LOCAL-1.2 draft fixtures. Because public discovery excludes draft and fixture records, a production visitor sees a deliberate `directory ready for the pilot` empty state until approved real merchants are loaded later.

The same public runtime has been certified against an in-memory active merchant matrix covering all three categories, featured sorting, active/no-active-perk states, filters, asset fallbacks, and fixture/lifecycle exclusion.

## Frozen boundaries

- Public perks are not conditioned on an insurance quote or purchase.
- Local does not alter insurance pricing, eligibility, underwriting, discounts or coverage.
- Public merchant presentation must not imply Farmers/408FARMERS endorsement.
- No fixture may render publicly.
- No merchant detail/redemption route is activated before 408-LOCAL-1.4.
- Existing 408FARMERS acquisition funnels and CoverageFit remain unchanged.

## Next sprint

**408-LOCAL-1.4 — Merchant Perk Detail + Redemption**

Build canonical `/local/{merchant-slug}/` pages and the frictionless show-your-screen redemption experience without collecting consumer identity or requiring insurance activity.
