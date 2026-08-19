# UI-3.13.1E Post-Deploy Smoke Runbook

Run this after the 408-UI-3.13.1E ROOT_DEPLOYABLE ZIP is deployed to the production 408FARMERS Cloudflare project.

## 1. Confirm final Human Trust build is live
Verify the deployed source includes the Human Trust assets and the expected 3.13.1D relationship presentation on representative routes.

Check:
- `/`
- `/home/`
- `/auto-bundle/`
- `/buyer/`
- one Professional Program
- `/contact/`
- `/local/`
- `/life/`

Life should remain in its cinematic campaign mode and should not inherit Human Trust branch styling.

## 2. Professional Programs smoke
On Healthcare, Teachers, Technology, and Engineers verify:
- profession-first headline
- occupation-specific photography
- restrained gold accent
- Dylan Human Trust Signature
- Check My Eligibility action
- role controls and submit flow still work
- campaign entry URLs still show the correct matched message

## 3. Core Insurance smoke
Verify Homepage, Home, Home + Auto, and Buyer retain the restrained Human Trust treatment with no extra form step or blocked CTA.

For Buyer, confirm realtor/partner context still survives when using a referral-origin entry.

## 4. Relationship / completion smoke
Submit one clearly labeled non-customer QA canary only when operations are ready.

Confirm a **confirmed** post-lead state can show:
- `Thanks — I have your request.`
- Dylan identity
- `You’re not submitting another request.`
- the existing focus questions
- optional CoverageFit continuation

Also verify unconfirmed/pending states do not falsely claim Dylan has received the request.

## 5. Contact smoke
Confirm Text Dylan, Call Dylan, and email actions use the intended destinations and that mobile handlers open normally.

## 6. Local smoke
Verify:
- Local remains public without login
- `No insurance purchase or quote required` remains visible
- Stevie's merchant/perk presentation works
- merchant join works
- insurance conversion remains secondary
- no synthetic Auto/Home merchants appear

LOCAL-1.10 remains NO-GO for the full planned three-merchant pilot until external closeout is complete.

## 7. INFRA-1.1 Cloudflare boundary
In Cloudflare metrics / Function logs confirm ordinary static requests do not invoke Pages Functions while intended dynamic/API/deep routes still do. `_routes.json` remains exactly preserved from the certified INFRA-1.1 baseline.

## 8. Browser/device smoke
Test current stable:
- Safari iPhone
- Safari macOS
- Chrome mobile
- Chrome/Edge desktop
- Firefox desktop

Verify no horizontal overflow, navigation works, photography does not obscure copy, focus indicators remain visible, and primary actions are reachable.

## 9. Life readiness
Follow `LIFE-PRODUCTION-CERTIFICATION.md` independently. Human Trust certification does not change Life readiness or secure-submission gates.

## Pass condition
Production activation is complete when the deployed bytes reflect 3.13.1E, representative acquisition and completion journeys function normally, Human Trust presentation appears only where intended, Life remains separate, INFRA-1.1 routing behaves correctly, and all separate Life/Local operational gates are honored.
