# UI-3.13 Post-Deploy Smoke Runbook

Run this after the final UI-3.13 + INFRA-1.1 ZIP has actually been deployed to the 408FARMERS production project.

## 1. Confirm exact UI build is live
Open the page source for `/` and verify the UI-3.1 / UI-3.2.1 foundation markers are present and the production metadata from UI-3.13 is visible (canonical, robots, absolute Open Graph image). Verify `/robots.txt` and `/sitemap.xml` return 200.

## 2. Confirm the INFRA-1.1 invocation boundary is active
In Cloudflare Workers & Pages metrics / real-time Function logs:
- confirm ordinary static loads such as `/`, `/home/`, `/shared/*`, and invalid crawler path stacks do **not** invoke Pages Functions
- confirm `/api/*`, `/home/qr/*`, `/home/campaign/*`, `/neighbor/r/*`, `/local/*`, and the intentional no-trailing-slash redirect entries still invoke `_worker.js` as designed
- verify Function request volume trends toward genuine dynamic/API usage instead of the prior crawler-driven volume

This is an activation check; build-time QA already certifies `_routes.json` at **22/22**.

## 3. Browser smoke
Test current stable versions of:
- Safari on iPhone
- Safari on macOS
- Chrome on iPhone/Android or Chrome mobile emulation
- Chrome/Edge desktop
- Firefox desktop

For `/`, `/home/`, `/auto-bundle/`, `/buyer/`, `/life/`, one Professional Program, and `/local/`, verify no horizontal overflow, the mobile menu works, primary CTAs are reachable, and no visible content is clipped.

## 4. Read-only handoff smoke
Run:
`node qa/production-handoff-smoke.js`

Do not use submission mode unless you intentionally want clearly labeled synthetic leads created.

## 5. Lead submission canary
When agency operations are ready for a test lead, submit one clearly labeled canary through the production Home flow and confirm the expected producer delivery plus optional CoverageFit continuation. Do not use real customer PII for QA.

## 6. Life readiness
Follow `LIFE-PRODUCTION-CERTIFICATION.md`. Paid Life traffic should remain gated by the existing protected readiness/canary requirements.

## 7. Local
Do not interpret UI-3.13 as closing LOCAL-1.10. Complete `LOCAL1_10_EXTERNAL_CLOSEOUT.md` before calling the planned three-merchant pilot GO.

## Pass condition
Production is activated when the deployed pages render the UI-3.13 artifact correctly, the INFRA-1.1 Function boundary behaves as intended, critical routes return successfully, representative forms/handoffs work, and separately required Life/Local operational gates remain honored.
