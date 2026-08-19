# 408-UI-3.12 — End-to-End Functional Regression

## Status
COMPLETE

## Goal
Prove that the completed UI-3 customer-facing redesign still behaves like the certified 408FARMERS product underneath it before production-design certification.

UI-3.12 is deliberately **regression-only**. It makes no customer-facing design, copy, form, Worker, attribution, routing, insurance, Local, Life, or CoverageFit behavior change.

## Product freeze
The exact UI-3.11.1 input was captured before 3.12 work.

- behavior-critical protected files: **73/73 unchanged**
- expanded customer-facing/runtime/static product surface: **160/160 unchanged**
- runtime JavaScript syntax: **41/41**

The expanded product freeze includes public/internal HTML surfaces, shared CSS/JS, Worker/routing files, Local catalog/schema, handoff manifest, and shipped image/icon assets.

## Dedicated end-to-end browser regression
A new `qa/test-408-ui-3.12-e2e.py` suite runs the real shipped page/runtime scripts in Playwright and deterministically mocks only the external/network response boundary.

It certifies **59/59** checks across:

- homepage identity and core destinations
- Home `/api/lead` submission
- Home Formspree fallback
- Home post-lead payoff
- explicit optional CoverageFit continuation
- Home prefill/consent/assessment handoff
- Home + Auto submission
- Buyer submission and referral parser
- Technology / Teachers / Engineers / Healthcare submission
- Life secure application transport
- Life schema + SSN last-four-only boundary
- Life completion event
- Local directory + Stevie's pilot merchant rendering
- merchant perk independence and redemption
- Local → insurance attribution decoration
- merchant join validation and proxy transport
- unknown/organic campaign fallback safety

The deterministic network layer is intentional for build-time regression. Live deployed-domain/external-service smoke testing remains part of UI-3.13 production certification.

## Full regression matrix
The current build reran the latest applicable certified suites rather than obsolete historical version/hash tests whose baselines predate intentional UI-3 changes.

- UI-3.11.1 source contract: **82/82**
- UI-3.11.1 campaign browser matching: **51/51**
- UI-3.11.1 accessibility delta: **56/56**
- Homepage UI-3.2.1: **93/93**
- Home UI-3.3: **108/108**
- Home + Auto UI-3.4: **99/99**
- Buyer UI-3.5: **115/115**
- Professional Programs UI-3.6: **452/452**
- Life UI-3.7: **23/23**
- Local UI-3.8: **155/155**
- Utility UI-3.9: **293/293**
- Mobile UI-3.10: **822/822**
- LOCAL-1.10 browser regression: **210/210**
- existing static regression: **296/296**
- Merchant Join Worker: **20/20**
- Local Attribution Worker: **29/29**
- Home hidden-required submit: **12/12**
- Home Advanced Mode routing: **16/16**
- Home deep-route assets: **12/12**
- Advanced Mode redirect-loop: **10/10**
- FLOW-2.4 explicit invitation runtime: **5/5**
- logo integration: **14/14**
- internal links/assets: **630 checked / 0 broken**

## Functional boundaries certified
### Home
Lead submission still hard-gates success; same-origin lead transport, Formspree fallback, progressive intake, campaign entry states, post-lead payoff, renter behavior, and explicit CoverageFit continuation remain intact.

### Home + Auto
The household review continues to submit through the existing transport, retains housing context and attribution, and preserves its existing post-lead/CoverageFit behavior.

### Buyer
Closing/referral context, partner parsing, online intake, submission, and downstream context remain intact.

### Professional Programs
Healthcare, Teachers, Technology, and Engineers retain profession-specific form contracts and submission behavior while campaign-specific entry presentation remains current-entry-only.

### Life
The campaign-aligned Life surface continues to use the secure application endpoint and schema. Regression explicitly verifies that only SSN last four is transported through the secure application initialization boundary.

### Local
The directory still resolves the active Stevie's pilot merchant, the perk remains independent from insurance, show-your-screen redemption still works, merchant application transport remains intact, and Local attribution still decorates optional insurance transitions.

### Campaign matching
Unknown or malformed campaign values fail to evergreen presentation. Persisted attribution does not take over later organic hero presentation.

## No obsolete-baseline false failures
UI-3.12 does not treat historical tests that assert old `VERSION` strings or pre-redesign HTML hashes as current product contracts. The regression matrix uses the newest applicable certified suite for each current surface plus the new cross-journey E2E suite and product-freeze hashes.

## Parallel Local status
LOCAL-1.10 remains technically certified with a production **NO-GO** for the planned three-merchant pilot until real Auto + Home merchants and the documented external closeout items are completed. UI-3.12 does not alter that boundary.

## Next sprint
**408-UI-3.13 — Production Design Certification**
