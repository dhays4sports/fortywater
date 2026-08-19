# 408-LOCAL-1.10 — Conversion + Compliance Certification

## Certification outcome

**Technical/source certification: PASS**  
**Production activation decision for the planned three-merchant MVP: NO-GO — external pilot closeout required**

408-LOCAL-1.10 has completed the full technical conversion/compliance certification pass against the uploaded 408-LOCAL-1.9 pilot-launch candidate. The implementation remains root-deployable and the currently activated Stevie's merchant can function as a one-merchant pilot, but this package does **not** falsely certify the roadmap's planned three-merchant MVP as operationally complete.

Two 408-LOCAL-1.9 pilot slots remain unfilled (Auto and Home), and the build environment cannot perform in-person merchant staff training, physical printed-device scans at each business, or the agency/Farmers advertising approval required before treating final live language/assets as carrier-approved.

## What was certified

### 1. Public routes and canonical routing
- `/local/` remains the canonical public directory.
- `/local/{merchant-slug}/` continues to route through the reusable merchant-detail shell.
- no-trailing-slash merchant URLs retain canonical normalization.
- Local reserved infrastructure routes remain protected from merchant-slug rewriting.
- `/local/join/` remains the independent merchant application flow.

### 2. Merchant lifecycle safety
The reusable data model was re-certified so that:
- only non-fixture `active` merchants are publicly discoverable;
- `draft`, `paused`, and `inactive` merchants remain hidden;
- fixture merchants remain non-public;
- unsupported/invalid lifecycle data fails closed.

### 3. Offer dates, terms, and redemption
The offer engine was re-certified across active, scheduled, expired, paused, draft, and inactive states.

A perk is redeemable only when:
- the merchant is active and non-fixture;
- the perk is active and non-fixture;
- any start date has arrived;
- any end date has not passed;
- the supported MVP redemption method is available.

Stevie's remains configured as an evergreen `show_screen` offer. No account, identity capture, insurance form, quote, policy purchase, or CoverageFit session is required to open or redeem it.

### 4. Insurance/perk separation
The public Local experience continues to state and enforce:
- no insurance purchase required;
- no insurance quote required;
- no insurance lead submission required;
- no CoverageFit assessment required;
- no change to insurance pricing, discounts, eligibility, underwriting, or coverage because of Local participation;
- merchant perks are merchant-provided and subject to merchant terms/availability;
- participation does not imply merchant endorsement/certification/recommendation by Farmers Insurance or 408FARMERS.

The optional insurance bridge remains **post-value**: the visitor first receives the merchant profile, current perk, terms, and redemption capability. The insurance CTA is separate and explicitly states that using or skipping the insurance review does not change the merchant perk.

### 5. Attribution and privacy boundary
408-LOCAL-1.6 attribution was re-certified without modification:
- bounded 30-day Local origin context;
- merchant/perk/surface/campaign/UTM token persistence;
- independently attributable merchant QR surfaces;
- five allowlisted Local events only;
- same-origin event collector;
- exact-key validation;
- no names, phone numbers, emails, street addresses, free-form URLs, insurance answers, quote data, or merchant-application PII in Local event telemetry;
- analytics failure remains non-blocking for perk use and insurance navigation.

### 6. Mobile, reflow, and accessibility
Automated browser checks were added for the public Local directory, Stevie's merchant page, redemption dialog, and merchant join page at phone, tablet, and desktop widths. Because the certification sandbox blocks browser network navigation, the browser suite renders the actual production HTML/CSS and Node-generated Local markup with Playwright `page.set_content`; deployed-domain navigation remains part of the external smoke-test checklist.

Certified behaviors include:
- no horizontal overflow at tested viewports;
- visible headings and key actions;
- mobile-sized form controls;
- 44px-or-larger primary touch targets where the Local system specifies them;
- keyboard-closeable redemption dialog;
- labelled close control;
- skip links and main landmarks;
- reduced-motion support retained in Local CSS;
- mobile form inputs remain 16px to avoid iOS zoom behavior.

### 7. QR routing
The three Stevie's pilot QR surfaces remain independently attributable:
- `merchant_table`
- `merchant_counter`
- `merchant_placard`

Automated QR decoding is preserved. Physical printed iOS/Android scanning remains an external launch task and is not falsely claimed by this source package.

### 8. California advertising/licensing preflight
The Local public pages already disclose:
- Virginia Tam Insurance Agency, Inc.;
- Dylan Haysbert;
- CA License #4528400;
- insurance context and agency contact information.

The Stevie's print placard now also carries `Virginia Tam Insurance Agency, Inc. · CA License #4528400` as a conservative print-advertising safeguard.

The compliance preflight reviewed California Department of Insurance public guidance on Insurance Code §1725.5 print-advertising license-number disclosure and the current internet-advertising disclosure framework associated with Insurance Code §1726. This source review is documented in `LOCAL1_10_COMPLIANCE_PREFLIGHT.md`.

**This is not a legal opinion and does not replace agency/Farmers advertising approval.**

## What is intentionally not certified as complete

The roadmap's three-merchant production MVP still requires:
1. a real Auto merchant;
2. a real Home merchant;
3. exact merchant-owned terms for those offers;
4. in-person merchant staff training/acknowledgment;
5. at least one physical printed scan check per merchant on real devices;
6. agency/Farmers review/approval of final live language, logos, placards, and campaign assets.

Until those items are recorded, **Generation 2 Local expansion remains blocked**.

## Regression protection
No changes were made to:
- Home, Home + Auto, Buyer, occupational, Life, or CoverageFit conversion logic;
- active insurance form fields or validation;
- Formspree/Worker submission contracts;
- Local attribution runtime;
- merchant directory/redemption runtime;
- merchant join runtime;
- Cloudflare routing behavior;
- insurance pricing, discount, eligibility, underwriting, or coverage logic.

The only public-asset compliance adjustment in 1.10 is the agency license disclosure added to the Stevie's Local print placard.

## Release interpretation
408-LOCAL-1.10 is a **completed certification sprint with a NO-GO activation finding for the full planned MVP**, not a fabricated three-merchant launch. The package is the authoritative certified source baseline for the current one-merchant pilot while external closeout remains open.

Once Auto + Home merchants are real and approved, rerun the included 1.10 certification harness and complete `LOCAL1_10_EXTERNAL_CLOSEOUT.md`. A GO result can then be issued without redesigning the Local architecture.
