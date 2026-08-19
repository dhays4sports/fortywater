# 408-UI-3.6 — Professional Programs Convergence

## Status
COMPLETE

## Goal
Unify Healthcare, Teachers, Technology, and Engineers as one recognizable 408FARMERS Professional Programs family while preserving each route's occupation-specific eligibility language, professional-role options, attribution, submission behavior, and CoverageFit context.

## Design direction
The four occupational routes now consume one shared professional-program visual layer:

- UI-3 navy / Farmers red / white hierarchy
- shared **408FARMERS Professional Programs** family bar
- one compact four-program switcher with a route-specific active state
- shared two-column professional-review hero architecture
- consistent conditional-discount framing without an automated eligibility conclusion
- one guided eligibility-review card system
- unified field, consent, reassurance, submit, direct-contact, and producer-context treatments
- shared professional-review explanation panel
- shared three-step CoverageFit progression
- shared Dylan / Virginia Tam / Farmers credibility close
- responsive phone, tablet, desktop, short-landscape, reduced-motion, and forced-color support

## Route identities retained

### Healthcare
- `Work in Healthcare?`
- healthcare role remains the profession field
- `healthcare_eligibility_form`
- `occupation_healthcare`

### Teachers
- `Work in Education?`
- school / education role remains the profession field
- `teachers_eligibility_form`
- `occupation_education`

### Technology
- `Work in Tech?`
- tech role remains the profession field
- `tech_eligibility_form`
- `occupation_tech`

### Engineers
- `Are You an Engineer?`
- engineering field remains the profession field
- `engineers_eligibility_form`
- `occupation_engineer`

## Eligibility / compliance boundary
The new family UI intentionally reinforces the existing rule:

> A professional role may be useful review context, but it is not an automatic eligibility decision.

The existing conditional discount language remains authoritative. Dylan still verifies availability during quoting and underwriting. CoverageFit remains educational and does not make the discount / underwriting decision.

## Added asset
- `shared/professional-programs-ui.css`

## Behavioral preservation
UI-3.6 intentionally does **not** change:

- the four `#leadForm` markup blocks
- Formspree form actions or methods
- field names / required semantics
- profession-specific `occupation_segment` choices
- source / campaign / UTM values
- `review_context`
- address autocomplete
- consent language
- professional discount eligibility wording
- direct Text Dylan / Call Dylan destinations
- post-lead engagement
- optional CoverageFit invitation
- CoverageFit sender / zero-repeat handoff contract
- `_worker.js`
- Home, Home + Auto, Buyer, Life, or Local behavior
- professional fallback thank-you pages (reserved for UI-3.9 utility/completion convergence)

## Conversion principle
The program family should feel like one organized platform, not four microsites. The profession earns contextual relevance; it does not become a promise of savings or automatic eligibility. The route remains a short professional-discount + broader coverage review that carries the selected role into the existing CoverageFit continuation.

## Next sprint
**408-UI-3.7 — Life Campaign + Platform Convergence**

Align Life with the UI-3 platform while preserving secure submission, campaign attribution, and producer-queue behavior.
