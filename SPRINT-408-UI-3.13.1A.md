# 408-UI-3.13.1A — Human Trust Foundation

## Status
COMPLETE — FOUNDATION / BEHAVIOR-FROZEN

## Input baseline
`408-UI-3.13 + 408-INFRA-1.1 + 408-UI-3.2.1` from the uploaded `farmerton-main(2).zip`.

The unrelated 408-INFRA-1.1 Pages Function Invocation Boundary Hotfix remains protected and byte-identical.

## Objective
Establish one reusable human/editorial trust vocabulary before modifying individual journeys. The foundation is intentionally narrower than a redesign: it creates the components, voice rules, photography contract, Professional Programs accent policy, and protected behavior boundary required by the B/C/D humanization sprints.

Governing principle: **Modern system underneath. Human relationship on the surface.**

Life is explicitly excluded.

## Implemented
- Added `shared/human-trust.css` with opt-in `ht-*` primitives.
- Added reusable Human Trust Signature, editorial note/copy, photo frame, Professional Programs accent/rule, Local cue, personal receipt, and explicit unboxed helper primitives.
- Added `HUMAN-TRUST-DESIGN-SYSTEM.md`.
- Added machine-readable `HUMAN-TRUST-COMPONENT-REGISTRY.json`.
- Loaded the inert foundation stylesheet on all 25 non-Life public HTML surfaces.
- Added a build marker to the same 25 surfaces.
- Did **not** add `ht-*` classes to current page bodies, so this sprint does not redesign any customer-facing body.
- Preserved all Life/Life Ops files byte-for-byte.
- Preserved the 408-INFRA-1.1 hotfix files byte-for-byte.
- Preserved all non-Life public HTML `<body>` content byte-for-byte; only `<head>` foundation references were added.

## Why foundation first
The Human Trust branch is a subtle calibration, not a new redesign generation. By making 3.13.1A visually inert, Professional Programs can establish the intended “exclusive yet human” balance in 3.13.1B before that treatment propagates more cautiously into core conversion journeys.

## Protected behavior
No change to forms, required semantics, Workers, `_routes.json`, Formspree, attribution, Campaign Entry Registry, Home/Bundle branching, Buyer referral logic, occupational eligibility, Local, Life, CoverageFit handoff, SMS, consent, pricing, or underwriting behavior.

## Next sprint
**408-UI-3.13.1B — Professional Programs Humanization**
