# 408FARMERS Production Design Certification

## Certified build
**408-UI-3.13 + 408-INFRA-1.1 + 408-UI-3.2.1**

## Certification decision
**PASS — DEPLOYABLE-CERTIFIED**

The packaged artifact passes the final UI-3 production-design, metadata, asset, performance, browser-layout, link, JavaScript, behavior/config freeze, form-contract, infrastructure-boundary, and end-to-end regression matrix.

The unrelated **408-INFRA-1.1 Pages Function Invocation Boundary Hotfix** supplied after UI-3.12 is explicitly preserved in this artifact; `_routes.json` is included in the exact freeze and passes its focused **22/22** routing-boundary QA.

### Build-time results
- Production browser layout: **749/749**
- Metadata/indexing: **216/216**
- Asset/performance: **99/99**
- Runtime/form/config/product-delta freeze: **66/66**
- INFRA-1.1 function boundary: **22/22**
- Exact INFRA-1.1 hotfix preservation: **4/4**
- Runtime JavaScript syntax: **41/41**
- Internal links/assets: **640/640**
- End-to-end functional regression: **59/59**

All **27 suites** in `UI3_13_REGRESSION_MATRIX.json` are certified.

## What this certification means
The ZIP is the final deployable UI-3 design baseline and is ready to upload/deploy as the site root while preserving the packaged folder structure **and the INFRA-1.1 Cloudflare routing boundary**.

## What this certification does not claim
The build process does not itself deploy to Cloudflare. Therefore it does not claim that the production domain is already serving the new bytes, that the live Function-invocation rate has already fallen, or that a live external Formspree/CoverageFit/Life queue canary was submitted from this exact deployment.

After deployment, run `UI3_13_DEPLOYMENT_SMOKE_RUNBOOK.md`. A post-deploy failure should be treated as deployment/configuration remediation against this certified build, not as permission to silently change the UI baseline.

## Local program boundary
LOCAL-1.10 remains production NO-GO for the planned three-merchant pilot pending real Auto + Home merchants and the existing external closeout checklist.
