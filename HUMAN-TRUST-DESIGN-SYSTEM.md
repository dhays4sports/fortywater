# HUMAN TRUST DESIGN SYSTEM

## Sprint
**408-UI-3.13.1A — Human Trust Foundation**

## Governing principle
**Modern system underneath. Human relationship on the surface.**

The completed UI-3 platform architecture remains authoritative. Human Trust is an opt-in editorial layer that makes 408FARMERS feel like a premium local insurance relationship supported by unusually good software — not software that happens to route a prospect to an agent.

## Scope
Human Trust may be consumed by the Homepage, Home, Home + Auto, Buyer, Professional Programs, Local, Contact/utility, and completion/post-submit surfaces.

**Life is excluded.** UI-3.7 already establishes the correct cinematic/human Life campaign environment and must not be restyled by this branch.

## Foundation rule
`shared/human-trust.css` is deliberately inert until a future sprint opts into an `ht-*` class. 3.13.1A loads the foundation on non-Life public surfaces but does not redesign their bodies. This gives the later B/C/D sprints one reusable vocabulary while preserving the UI-3.13 customer-facing baseline during foundation work.

## Human Trust Signature
Use `.ht-signature` to make Dylan visibly real without turning him into another feature card.

Preferred content hierarchy:
1. real Dylan headshot from `shared/images/dylan-headshot-*`
2. `Personally reviewed by Dylan Haysbert` or contextually equivalent copy
3. `Farmers Insurance Producer`
4. `Virginia Tam Insurance Agency, Inc.` when space/context benefits from agency identity
5. optional `Text Dylan` / `Call Dylan` actions

Rules:
- editorial signature, not testimonial or feature badge
- no AI-generated or substituted likeness of Dylan
- no claim that Dylan has personally reviewed information before submission
- do not repeat the signature multiple times within one short viewport
- direct contact actions must use the existing certified phone/SMS destinations

## Voice model
### Before submission
Warm, invitational, low-pressure.
- “Let’s see what’s worth reviewing.”
- “Tell me what changed.”
- “I’ll help you understand what may be worth a closer look.”

### During intake
Clear, neutral, concise. Keep instructions functional and avoid chatty copy around every field.

### After submission
First-person Dylan voice is preferred when technically accurate.
- “Thanks — I have your request.”
- “A few quick questions will help me understand what you’d like me to focus on.”
- “You’re not submitting another request.”

Avoid consumer-facing software words when ordinary language works: `workflow`, `request state`, `next-stage`, `processing`, `submission completed`, `context` (unless necessary to explain a specific rule).

## Photography contract
Photography is used for identity/trust, not decoration.

Intensity:
- Professional Programs: strongest
- Buyer: moderate lifestyle/homeownership context
- Homepage: restrained
- Home / Home + Auto: restrained
- Local: merchant/environment imagery when merchant-owned/approved assets exist
- Utility/completion: Dylan only when useful
- Life: unchanged

Rules:
- premium, natural, editorial, context-specific
- no fake customer/testimonial implication
- occupation images represent the profession, not a named insured or endorsement
- essential claims and CTA copy remain live HTML; never bake essential text into imagery
- responsive WebP where practical, explicit dimensions/aspect-ratio, lazy loading below the fold
- meaningful alt text only when the image conveys information; decorative imagery uses empty alt

The existing Professional Program campaign assets in `shared/assets/{healthcare,teachers,tech,engineers}.*` are approved source material for the next humanization sprint, subject to the same accessibility/performance checks.

## Professional Programs identity
Professional Programs may intentionally feel a little more exclusive/campaign-informed than core Home/Bundle.

Foundation:
- UI-3 navy / white remains primary
- Farmers red remains primary CTA/action
- warm gold is a **selective identity accent**, not a second CTA color
- campaign photography and a subtle editorial/hand-drawn rule may be used
- one clear profession identifier is preferred over stacked taxonomy labels

Gold rules:
- use `--ht-gold-700` / `--ht-gold-600`
- use for strong/large emphasis, small identity rules, and icons only
- do not use low-contrast gold for essential small body copy
- never replace required red action treatment

## Component Necessity Audit
Before retaining a pill, badge, border, tinted callout, or card, ask:
**Does this information need a container to be understood or acted on?**

If no, prefer:
- editorial spacing
- plain text hierarchy
- a short rule
- `.ht-human-note`
- `.ht-unboxed` only when an existing component is explicitly approved for de-chroming

Target for B/C/D: reduce nonessential visible containers by roughly 10–15% on the surfaces being humanized. This is not a global deletion target and must not reduce grouping, comprehension, consent visibility, error clarity, or touch ergonomics.

## Surface intensity
| Surface | Human Trust intensity | Direction |
|---|---:|---|
| Homepage | Moderate | bring Dylan/local service earlier; fewer abstract trust badges |
| Home | Restrained | small reassurance/signature; preserve conversion cleanliness |
| Home + Auto | Restrained | consultative household framing |
| Buyer | Moderate | lightly concierge-oriented closing support |
| Professional Programs | Strong | campaign-informed hero, professional photography, selective gold, Dylan signature |
| Local | Moderate | warmer neighborhood/editorial presentation; insurance bridge remains secondary |
| Completion/post-submit | Strong | first-person Dylan acknowledgement where accurate |
| Contact/utility | Moderate | obvious real-agent accessibility |
| Life | Excluded | UI-3.7 remains authoritative |

## Local compliance separation
Humanization must never make Local sound like an insurance reward or gated policyholder benefit. Preserve the existing rule:
**No insurance purchase or quote required.**

Merchant offers remain merchant-provided and independent of insurance quoting/purchasing.

## Accessibility inheritance
Human Trust inherits UI-3.11/3.13 requirements:
- one valid H1 per public page
- meaningful alt / empty alt as appropriate
- no essential text only inside images
- 320px reflow and 400% zoom resilience
- final UI-3 focus treatment remains authoritative
- reduced motion and forced colors remain respected
- live text contrast must remain AA-oriented
- mobile controls remain 44px+ and text inputs 16px+

## Behavior boundary
Human Trust is presentation/copy only. It does not change:
- form names or required fields
- Formspree or Cloudflare endpoints
- Workers or `_routes.json`
- Home / Bundle branching
- Buyer referral/closing logic
- occupational eligibility or discount determination
- Campaign Entry Registry or attribution schema
- Local redemption/join/insurance separation
- Life
- CoverageFit handoff
- SMS
- consent
- pricing/underwriting behavior

## Branch sequence
1. **3.13.1A — Human Trust Foundation** — COMPLETE
2. **3.13.1B — Professional Programs Humanization** — COMPLETE
3. **3.13.1C — Core Insurance Humanization** — COMPLETE
4. **3.13.1D — Relationship + Completion Humanization** — NEXT
5. **3.13.1E — Human Trust Regression + Production Certification**

After 3.13.1E, the customer-facing UI should freeze again so acquisition and actual conversion data — not continued aesthetic iteration — drive the next decisions.


## 3.13.1B applied Professional Programs contract
Professional Programs now consume the Human Trust foundation directly. The four occupation routes intentionally use the strongest Human Trust intensity outside Life:
- one profession-first hero identifier rather than stacked product taxonomy
- campaign-derived professional portraits cropped from existing approved campaign source art so essential copy remains live HTML
- warm gold only for identity/kicker/rule/step accents; Farmers red remains the primary action color
- editorial benefit lists instead of pill-heavy trust rows
- an early Dylan signature with existing Text/Call destinations
- a quiet eligibility/underwriting qualifier rather than a software-style context panel
- a simplified form introduction while preserving form controls and submission behavior
- reduced card chrome in the payoff, steps, and producer close

The Professional Programs treatment is the calibration reference for 3.13.1C. Core insurance surfaces should consume a more restrained version rather than copying the full occupation-photo/gold treatment.


## 3.13.1C applied Core Insurance contract
Homepage, Home, Home + Auto, and Buyer now consume a deliberately restrained Human Trust layer:
- Homepage replaces abstract hero trust chips with one compact Dylan identity cue while retaining the platform architecture and situation-first chooser.
- Home keeps its campaign-aware hero and certified form intact, but introduces Dylan beside the review explanation and reduces benefit-list chrome.
- Home + Auto is framed as a consultative household review, with a single early Dylan identity cue and less duplicated producer content inside the form card.
- Buyer adds a light concierge tone, early Dylan identity, and simpler editorial support around the existing closing workflow.
- Core insurance does **not** inherit the Professional Programs gold identity treatment. Farmers red/navy/white remains authoritative.
- The three core lead forms remain exactly preserved inside `#leadForm`; this sprint is presentation/copy only.

3.13.1D should now focus on the relationship **after** a prospect has submitted: first-person acknowledgements, focus questions, receipts, Contact/utility, and a warmer Local presentation while preserving Local/insurance separation.


## 3.13.1D applied Relationship + Completion contract
The Human Trust layer is now strongest after a prospect has already submitted and a relationship can be truthfully acknowledged:
- confirmed post-lead states may use `Thanks — I have your request.` with Dylan identity
- pending/unconfirmed states must remain operationally truthful and must not imply receipt
- post-submit focus questions remain functional controls, but surrounding status/summary chrome should be editorial rather than dashboard-like
- static receipts use first-person Dylan acknowledgement only because those pages represent a received-request fallback state
- Contact should make direct access to Dylan concrete instead of relying on abstract trust chips
- Local should feel neighborly and relationship-led while preserving the bright-line rule `No insurance purchase or quote required.`
- merchant applications can identify Dylan as the reviewer, but must never imply acceptance, referrals, sales, endorsement, or an insurance quid pro quo
- Professional gold remains confined to Professional Programs; relationship/completion surfaces use core navy/red/white
- Life remains excluded and authoritative under UI-3.7

## Final branch certification — 408-UI-3.13.1E
The Human Trust branch is complete and production-certified. The current presentation is now frozen.

- Professional Programs remain the strongest exclusive/human expression.
- Core insurance remains intentionally more restrained.
- Confirmed completion states may use first-person Dylan voice; pending/unconfirmed states must remain semantically truthful.
- Local remains independent of insurance purchase/quote requirements.
- Life remains outside this design layer.
- Future changes to these rules require an explicit maintenance/hotfix sprint or a new UI generation.

