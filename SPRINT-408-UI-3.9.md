# 408-UI-3.9 — Utility + Completion Surfaces

## Status
COMPLETE

## Goal
Bring low-frequency but trust-critical 408FARMERS utility and completion surfaces into the UI-3 platform language without changing insurance, Local, Worker, attribution, or CoverageFit behavior.

## Surfaces converged
- Home fallback receipt
- Home + Auto fallback receipt
- Buyer fallback receipt
- Healthcare, Teachers, Technology, and Engineers fallback receipts
- Life secure-application receipt, preserving Life campaign mode
- Local merchant-join application receipt
- Contact Dylan page
- Privacy notice
- Website terms
- Neighbor / referral handoff bridge into CoverageFit
- shared error, recovery, and empty-state treatments
- static `404.html` fallback

## Completion hierarchy
Receipts now use a consistent structure: clear receipt state, concise explanation, direct contact actions, next-step guidance when present, and optional Local value only after the insurance receipt. The Local/insurance separation language and existing attribution links are unchanged.

## Legal and contact surfaces
Privacy and Terms retain their existing substantive text and are presented as restrained document surfaces. Contact remains a direct text/call/email choice with the same telephone number, email address, SMS body, Dylan identity, agency identity, and carrier credential.

## Redirect / bridge surface
The existing `/neighbor/` referral bridge keeps its CoverageFit green analytical identity inside the UI-3 platform shell. No redirect destination, referral token, privacy statement, or bridge runtime changed.

## Error and empty states
The shared UI foundation now gives existing error, recovery, and empty states a consistent border/radius/background language. A static 404 page provides a branded fallback without changing Worker routing.

## Behavior freeze
No changes were made to:
- `_worker.js`
- form field names or required semantics
- Formspree / Cloudflare endpoints
- Local data, redemption, join or attribution runtimes
- Life secure-submission or producer-queue runtime
- QR/campaign routing
- CoverageFit launch or handoff logic
- insurance quote, underwriting, pricing, discount, or eligibility behavior

The only HTML repair beyond presentation is valid markup for five legacy `What happens next` receipt blocks; user-facing copy and order are unchanged.

## Deliberate exclusions
- `/life-ops/` remains an internal protected producer workspace and is not converted into a consumer utility surface.
- Product experiences such as Protection Score remain owned by their product-specific UI rather than this utility sprint.

## Next sprint
**408-UI-3.10 — Mobile Interaction Pass**
