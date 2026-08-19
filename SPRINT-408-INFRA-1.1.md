# 408-INFRA-1.1 — Pages Function Invocation Boundary Hotfix

## Incident
Cloudflare production metrics showed approximately 84.6k successful Worker/Pages Function requests and 84.5k subrequests in 24 hours while Web Analytics recorded only 9 page views. Real-time logs showed an automated crawler requesting malformed stacked URLs such as `/contact/healthcare/teachers/shared/tech/...` at roughly one request per second.

The deployed project uses Cloudflare Pages Advanced Mode (`_worker.js`). Without `_routes.json`, every incoming request invokes the Worker, including static pages, assets, 404s, and crawler garbage. The Worker then forwards normal requests to `env.ASSETS.fetch()`, explaining the near 1:1 Worker-request/subrequest ratio.

## Hotfix
Add `_routes.json` at the deployment root. It invokes `_worker.js` only for routes that genuinely need server-side logic:

- `/api/*`
- canonical no-trailing-slash entry points whose redirects are owned by `_worker.js`
- `/home/Wowindex.html` legacy redirect
- `/home/qr/*`
- `/home/campaign/*`
- `/neighbor/r/*`
- `/local/*` dynamic Local routing

Everything else—including `/`, canonical static pages, `/shared/*` assets, and malformed crawler path stacks—is served by Cloudflare Pages' static asset layer without invoking Functions.

## Behavior freeze
No pre-existing application file is changed. `_worker.js`, all HTML, JavaScript, CSS, API handlers, Home campaign behavior, Neighbor referral behavior, Local merchant behavior, forms, attribution, and UI-3.12 remain byte-for-byte identical to the certified baseline. This hotfix adds only `_routes.json`, this sprint record, and focused QA/certification artifacts.

## Expected production effect
The crawler may continue requesting malformed URLs, but those requests should stop appearing in Pages Function real-time logs and stop consuming the Workers Free daily Function-request quota. Function traffic should collapse toward genuine API and intentional dynamic-route usage.

## Post-deploy verification
1. Deploy this root directly to `408farmers-v2`.
2. Open `Workers & Pages → 408farmers-v2 → Metrics` and Real-time Function logs.
3. Confirm malformed stacked URLs no longer appear as Function invocations.
4. Confirm normal static page loads do not materially increase Function request counts.
5. Verify one Home QR route, one Neighbor referral route, one Local merchant route, and the existing lead/API path still behave normally.
