# 408-LOCAL-1.1 — Local Perks Foundation

## Outcome

408FARMERS now has a production-ready public foundation for **408FARMERS Local**, a South Bay merchant discovery and perks layer that remains deliberately separate from insurance quoting, purchase, eligibility, pricing, underwriting, and coverage decisions.

The canonical public route is:

`https://408farmers.com/local/`

## What this sprint adds

- A first-class `/local/` public route using the established 408FARMERS visual language.
- Clear consumer-facing positioning: **Good businesses. Useful local perks.**
- Public program principles:
  - no login required;
  - no insurance purchase required;
  - no insurance quote required;
  - merchant terms and availability apply;
  - Local participation does not affect insurance pricing, discounts, eligibility, coverage, or underwriting.
- A reusable Local page shell with:
  - Local-specific header and navigation;
  - launch-status panel;
  - three-step program explanation;
  - pilot category system for Eat & Drink, Home, and Auto;
  - explicit program-boundary section;
  - merchant pilot interest CTA;
  - insurance-services separation note;
  - agency/licensing footer.
- New `shared/local.css` scoped to `.local-page` and Local component classes.
- Cloudflare Pages Advanced Mode normalization for `/local` → `/local/`.
- Accessibility support through the existing site-wide accessibility layer, semantic landmarks, skip navigation, keyboard-reachable controls, 44px+ primary targets, responsive reflow, and reduced-motion handling.

## Deliberate exclusions

This sprint does **not** add merchant records, merchant offer cards, dynamic merchant routes, redemptions, merchant applications, attribution events, or insurance conversion modules. Those are sequenced into later Local sprints so the foundation does not pre-build unvalidated infrastructure.

Specifically deferred:

- `408-LOCAL-1.2` — Merchant Data Model
- `408-LOCAL-1.3` — Merchant Discovery Directory
- `408-LOCAL-1.4` — Merchant Perk Detail + Redemption
- `408-LOCAL-1.5` — Merchant Join Flow
- `408-LOCAL-1.6` — Local Attribution Engine
- `408-LOCAL-1.7` — Insurance Conversion Bridge
- `408-LOCAL-1.8` — 408FARMERS Site Integration
- `408-LOCAL-1.9` — Pilot Merchant Launch
- `408-LOCAL-1.10` — Conversion + Compliance Certification

## Architectural boundary

408FARMERS Local is a public community/merchant layer. It is not a policyholder-only reward program and is not an insurance discount program.

The intended long-term architecture remains:

`408FARMERS Local → merchant value / community discovery`

`408FARMERS acquisition flows → optional insurance conversion`

`CoverageFit → insurance assessment / consultation`

Local offers must remain usable without requiring an insurance quote, insurance purchase, insurance lead form, or CoverageFit assessment.

## Files added

- `local/index.html`
- `shared/local.css`
- `SPRINT-408-LOCAL-1.1.md`
- `408-LOCAL-ROADMAP.md`
- `LOCAL1_1_FOUNDATION_CONTRACT.json`
- `LOCAL1_1_RELEASE_CERTIFICATION.json`
- `qa/test-408-local-1.1.js`

## Files changed

- `_worker.js` — adds `/local` to canonical directory normalization.
- `VERSION` — advances the 408FARMERS source build to `408-LOCAL-1.1`.
- `CHANGELOG.md` — records the Local foundation release.
- `ROADMAP.md` — links the Local program roadmap.
- `README.txt` — documents the new Local route and sprint boundary.

## QA

Run:

```bash
node qa/test-408-local-1.1.js
python qa/test-static.py
python qa/check-links.py
node qa/test-advanced-mode-redirect-loop-hotfix.js
node qa/test-home-2.7-worker-routing.js
```

## Definition of done

`408-LOCAL-1.1` is complete when:

1. `/local/` renders independently and uses only local/static assets already shipped with 408FARMERS.
2. `/local` receives a single canonical 308 redirect to `/local/` through `_worker.js`.
3. The page makes the insurance/perk boundary explicit in multiple user-visible locations.
4. No Local flow requires a form, account, quote, policy, or insurance submission.
5. The pilot categories are visible without pretending that merchant offers are already live.
6. Local CSS is scoped and does not alter existing acquisition routes.
7. Existing static, link, and Advanced Mode routing checks continue to pass.
8. The detailed roadmap is included in the deployable archive for continuation in the next sprint.
