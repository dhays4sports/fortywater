# 408FARMERS Local — Detailed Product & Sprint Roadmap

**Roadmap owner:** 408FARMERS

**Current Local build:** `408-LOCAL-1.10-CERTIFIED-NO-GO`

**Core rule:** 408FARMERS Local is a public merchant/community layer. A merchant perk must never require an insurance quote, policy purchase, insurance lead submission, or CoverageFit assessment to view or redeem it.

---

## Product architecture

### 408FARMERS Local
Purpose: local discovery, merchant value, physical distribution, community recognition, and relationship building.

### 408FARMERS insurance acquisition
Purpose: optional home, auto, life, business and other insurance-intent conversion.

### CoverageFit
Purpose: insurance assessment, consultation, Protection Score/report and producer workflow.

Local can introduce a visitor to insurance later, but it must not gate or condition a public merchant benefit on insurance activity.

---

# Generation 1 — Local MVP

## 408-LOCAL-1.1 — Local Perks Foundation — COMPLETE

Build the canonical `/local/` route, Local brand shell, category architecture, public program explanation, merchant-interest surface, responsive/accessibility behavior and explicit insurance/perk separation.

**Done in this archive.**

---

## 408-LOCAL-1.2 — Merchant Data Model — COMPLETE

### Goal
Create a reusable source-of-truth structure so merchants and offers are data-driven rather than hardcoded into pages.

### Merchant fields
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

### Perk fields
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

### Rules
- inactive/expired offers cannot render as active;
- no merchant data may imply Farmers endorsement of merchant quality;
- every perk carries independent-offer language;
- data model must be safe to move later into a Cloudflare-backed store without changing consumer URLs.

### Done when
Three fixture merchants can be rendered from the same schema without duplicating page markup.

**Completed in 408-LOCAL-1.2.** The archive now includes a versioned normalized catalog, JSON Schema, storage-neutral runtime helper, lifecycle/date resolver, no-endorsement guardrails, independent-offer language enforcement, stable merchant URL construction, and three non-public fixture merchants covering Eat & Drink, Home, and Auto. The public directory remains intentionally deferred to 1.3.

---

## 408-LOCAL-1.3 — Merchant Discovery Directory — COMPLETE

### Goal
Turn `/local/` from a program foundation into a real discovery directory.

### Build
- active merchant grid;
- category filtering;
- merchant image/logo handling;
- neighborhood labels;
- featured merchant state;
- active/expired/paused handling;
- useful empty states;
- mobile horizontal category controls if warranted by testing;
- no login.

### Pilot categories
1. Eat & Drink
2. Home
3. Auto

### Done when
A visitor can understand what is available and choose a merchant in two taps or fewer from `/local/`.

**Completed in 408-LOCAL-1.3.** `/local/` now consumes the canonical Local catalog, filters active non-fixture merchants across All / Eat & Drink / Home / Auto, supports featured state and image/logo fallbacks, and clearly distinguishes active perks from unavailable scheduled/expired/paused/draft offers. Merchant details can be inspected inline without a login. Because real merchant activation is intentionally reserved for the pilot launch, the production catalog still shows the certified pilot empty state until approved businesses are loaded.

---

## 408-LOCAL-1.4 — Merchant Perk Detail + Redemption — COMPLETE

### Goal
Create canonical merchant pages and a frictionless first redemption model.

### Route
`/local/{merchant-slug}/`

### Page content
- merchant name;
- image/logo;
- category + neighborhood;
- short merchant description;
- current Local perk;
- merchant-specific terms;
- “Use This Perk” action;
- show-your-screen redemption state;
- merchant site/directions link if available;
- no consumer account;
- no insurance lead form before redemption.

### MVP redemption
Tap `Use This Perk` → reveal a clear screen the customer can show the participating merchant.

### Done when
The full discovery → offer → redemption path works without collecting personal information.

**Completed in 408-LOCAL-1.4.** Canonical `/local/{merchant-slug}/` routes now resolve through one reusable detail shell, active non-fixture merchants render their full business profile and current perk, and `Use This Perk` opens a show-your-screen redemption state containing the current offer and merchant terms. Unavailable perks never expose redemption, no consumer identity or insurance lead is collected, and the production fixtures remain draft/non-public until the pilot launch.

---

## 408-LOCAL-1.5 — Merchant Join Flow — COMPLETE

### Goal
Make merchant acquisition repeatable.

### Route
`/local/join/`

### Intake
- business name;
- contact name;
- email;
- phone;
- category;
- location;
- website/social;
- proposed perk;
- basic terms/acknowledgment;
- optional notes.

### Positioning
- free pilot participation unless business rules change later;
- merchant chooses its offer;
- merchant remains responsible for offer terms;
- Local participation is not conditioned on buying commercial insurance;
- no promise of insurance referrals or lead volume.

### Done when
A merchant can submit an application without Dylan reconstructing the information manually from texts/emails.

**Completed in 408-LOCAL-1.5.** `/local/join/` now provides a branded, mobile-accessible merchant application with the full pilot intake, required authorization and insurance-separation acknowledgments, privacy-safe source/UTM context, a dedicated same-origin `/api/local/merchant-application` relay, direct Formspree fallback, and a branded receipt page. The public `/local/` business CTA now enters this flow instead of relying on a manual email. Applications do not publish merchants automatically, do not create an insurance obligation, and do not promise referrals, lead volume, sales, or directory acceptance.

---

## 408-LOCAL-1.6 — Local Attribution Engine — COMPLETE

### Goal
Measure the Local network and preserve origin when a visitor later chooses insurance.

### Context fields
- `source=local`
- `partner_id`
- `perk_id`
- `merchant_slug`
- `surface`
- `campaign`
- `variant`
- standard UTMs when present.

### Minimum privacy-safe events
- `local_view`
- `merchant_view`
- `perk_open`
- `perk_redeem_intent`
- `insurance_cta_click`

Do not put customer identity, offer redemption details, addresses or insurance answers in public analytics payloads.

### Physical surfaces
Prepared for tokenized surfaces including:
- merchant counter QR;
- window QR;
- coaster/table QR;
- receipt insert;
- realtor/new-homeowner materials.

### Done when
A later insurance lead can truthfully retain the originating Local merchant and surface without requiring the user to re-enter it.

**Completed in 408-LOCAL-1.6.** The build now includes a bounded 30-day, non-PII Local first-touch context; merchant/perk/surface-aware URL propagation; the five minimum Local events; `dataLayer` + `408farmers:local-event` instrumentation; a same-origin `/api/local/event` collector with optional D1 persistence through `LOCAL_ANALYTICS_DB` (falling back to the existing `LIFE_QUEUE_DB` binding when present); and Local-origin recovery inside the shared insurance form and CoverageFit sender paths when a visitor reaches insurance later without Local query parameters. Explicit new campaign parameters still take precedence over stored Local origin. Merchant redemption remains fully usable when analytics transport is unavailable.

---

## 408-LOCAL-1.7 — Insurance Conversion Bridge — COMPLETE

### Goal
Add optional insurance pathways after merchant value has been delivered.

### Rule
Merchant value first. Insurance CTA second.

### Candidate module
“Own a home in the South Bay?” → optional Home or Home + Auto Coverage Review.

### Requirements
- no insurance CTA can gate the perk;
- Local context carries into 408FARMERS attribution;
- no duplicate lead capture;
- no automatic CoverageFit launch;
- existing 408FARMERS/CoverageFit zero-repeat rules remain intact.

### Done when
A Local visitor can voluntarily enter the existing insurance journey and the final lead retains the Local merchant origin.

**Completed in 408-LOCAL-1.7.** Active merchant-perk pages now render a dedicated optional homeowner insurance module only after the merchant profile, current perk, merchant terms, redemption action, and explicit Local/insurance boundary. The module offers existing Home and Home + Auto review routes, is decorated by the certified 1.6 Local attribution engine, and emits the existing `insurance_cta_click` event without adding a second lead form. The merchant perk remains fully accessible without engaging the module, no CoverageFit experience launches from Local, no perk condition is tied to insurance activity, and merchant pages with no active perk do not render the bridge.

---

## 408-LOCAL-1.8 — 408FARMERS Site Integration — COMPLETE

### Goal
Make Local discoverable from the broader 408FARMERS site without weakening insurance conversion funnels.

### Candidate placements
- primary/global navigation: `Local`;
- homepage lower-page module;
- footer;
- post-submission value module;
- selected realtor/homebuyer completion surfaces.

### Do not
- replace the primary homeowner CTA;
- place perk distractions inside active form steps;
- insert Local content inside CoverageFit assessment/consultation flows.

### Done when
Local feels native to 408FARMERS but core insurance pages remain insurance-first.

**Completed in 408-LOCAL-1.8.** The root 408FARMERS experience now exposes Local through the desktop/global navigation, a deliberately lower-page community module, and the homepage footer. Property-oriented fallback request receipts and the selected homebuyer completion receipt add a post-submission Local value module only after the existing insurance receipt content. Active insurance forms, the buyer intake, Life, CoverageFit, merchant data/redemption, Local attribution runtime, and the Cloudflare Worker remain unchanged. Site-entry links carry token-safe Local surface/campaign context into the existing 1.6 attribution engine, while public perks remain independent of insurance activity.

---

## 408-LOCAL-1.9 — Pilot Merchant Launch

### Goal
Launch with three real businesses and real merchant-owned offers.

### Recommended pilot composition
1. Stevie's — Eat & Drink
2. One Auto merchant
3. One Home merchant

### Launch tasks
- validate merchant identity/contact;
- approve exact offer and terms;
- load merchant records;
- activate offers;
- generate merchant/surface-specific QR codes;
- verify physical scans on iOS/Android;
- train merchant staff on MVP redemption;
- provide a simple merchant placard/card.

### Done when
All three merchants can be discovered, their perks can be used without insurance activity, and traffic is independently attributable.

**Pilot launch state in 408-LOCAL-1.9:** Stevie's Bar & Grill is activated as the first real Eat & Drink merchant with a live show-your-screen perk and independently attributable table/counter/placard QR campaigns. The Auto and Home pilot slots remain intentionally unfilled pending user recruitment and exact merchant-owned terms. The sprint therefore remains operationally open rather than inventing merchant participation.

---

## 408-LOCAL-1.10 — Conversion + Compliance Certification — COMPLETE (NO-GO FINDING)

### Goal
Certify the Local MVP before expansion.

### Certification matrix
- public route and canonical routing;
- merchant active/inactive logic;
- offer dates/terms;
- no quote/purchase gate;
- no policyholder-only gate unless separately approved;
- mobile/reflow/accessibility;
- QR routing;
- attribution persistence;
- privacy-safe telemetry;
- insurance bridge separation;
- existing 408FARMERS regression suite;
- agency/Farmers advertising/compliance review of final live language and assets.

### Done when
The three-merchant pilot can run in production and be measured end-to-end without changing the economics or eligibility of insurance.

### Certification result in this archive
The technical/source certification matrix passes, but the full planned three-merchant MVP remains **NO-GO for production activation** because only Stevie's is active, Auto/Home merchant recruitment is still open, physical merchant/device checks are external, and agency/Farmers advertising approval cannot be performed by the build environment. See `LOCAL1_10_RELEASE_CERTIFICATION.json`, `LOCAL1_10_COMPLIANCE_PREFLIGHT.md`, and `LOCAL1_10_EXTERNAL_CLOSEOUT.md`.

Generation 2 Local expansion remains blocked until the external checklist is closed and a GO decision is recorded.

---

# Generation 2 — Network Expansion

Build only if the Generation 1 pilot produces meaningful merchant and consumer usage.

## 408-LOCAL-2.1 — Merchant QR Distribution System
Standardize counter cards, window cards, coaster/table placements and surface-level attribution.

## 408-LOCAL-2.2 — Redemption Intelligence
Add privacy-conscious redemption timestamps/tokens, basic abuse protection and optional merchant confirmation without requiring consumer accounts.

## 408-LOCAL-2.3 — Local Analytics Command Center
Internal merchant-level reporting for visits, perk opens, redemption intent, insurance CTA clicks, insurance starts/submissions/quotes/policies when attributable.

## 408-LOCAL-2.4 — Merchant Operations Console
Internal merchant status, contact, offer state, dates, notes, QR campaign and quick activate/pause/replace controls.

## 408-LOCAL-2.5 — Merchant Offer Lifecycle
Evergreen, seasonal, replacement and expiring offers without changing the merchant URL or QR identity.

## 408-LOCAL-2.6 — Merchant Acquisition System
Upgrade `/local/join/` with examples, FAQ, application qualification, onboarding status and reusable merchant launch kit.

---

# Generation 3 — Homeowner Ecosystem

Build only after Local itself is useful independent of insurance.

## 408-LOCAL-3.1 — New Homeowner Local Guide
A dedicated South Bay move-in resource for locksmiths, plumbers, HVAC, movers, cleaners, restaurants and similar categories.

## 408-LOCAL-3.2 — Realtor Local Handoff
Give referred homebuyers useful post-closing Local resources after the insurance/closing task is handled.

## 408-LOCAL-3.3 — Post-Submission Local Payoff
After an insurance lead is already submitted, offer Local as immediate value while Dylan reviews the insurance request.

## 408-LOCAL-3.4 — Customer Relationship Layer
Optional periodic Local updates that provide a non-insurance reason to re-engage with 408FARMERS.

---

# Generation 4 — Merchant → Commercial Relationship Flywheel

This is an internal relationship layer, not a condition of Local participation.

## 408-LOCAL-4.1 — Merchant Relationship CRM
Track merchant contact, business type, locations, relationship strength and potential commercial lines while keeping Local participation separate from insurance opportunity status.

## 408-LOCAL-4.2 — Commercial Opportunity Signals
Record legitimate relationship moments such as a merchant asking an insurance question, mentioning renewal, adding vehicles/employees/locations, or requesting a review.

## 408-LOCAL-4.3 — Local-to-Business Handoff
When a merchant voluntarily wants commercial help, route them into the existing/future 408FARMERS Business intake while retaining merchant relationship context.

---

# Product principles that remain frozen across all Local sprints

1. **No insurance discount masquerading as a merchant perk.**
2. **No insurance quote or purchase required to access a public perk.**
3. **No merchant compensation tied to insurance placement unless separately reviewed and approved.**
4. **Merchant terms are visible and owned by the merchant.**
5. **Local is publicly useful even if a visitor never becomes an insurance lead.**
6. **CoverageFit remains an insurance-only assessment/consultation environment.**
7. **Do not add accounts, loyalty points, POS integrations or complex coupon infrastructure before the pilot proves the need.**
8. **Attribution should be measurable but privacy-safe.**
9. **Physical merchant distribution is a first-class channel, not an afterthought.**
10. **Every expansion sprint must preserve existing 408FARMERS insurance conversion behavior unless the sprint explicitly owns that integration.**

---

# Immediate continuation point

The Local technical certification sprint is complete with a **NO-GO production finding** for the planned three-merchant MVP. Close the external items in `LOCAL1_10_EXTERNAL_CLOSEOUT.md`: add real Auto + Home merchants, validate exact merchant-owned terms, complete merchant staff/physical QR checks, and obtain the applicable agency/Farmers advertising approval.

**Do not start 408-LOCAL-2.x until a 1.10 GO closeout is recorded.** A separate visual-only `408-UI-3.x` redesign may proceed if it preserves the certified Local/insurance behavior contracts.
