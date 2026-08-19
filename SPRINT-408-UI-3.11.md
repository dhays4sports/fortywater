# 408-UI-3.11 — Accessibility Certification

## Status
COMPLETE

## Goal
Certify the public 408FARMERS UI-3 consumer experience against the project’s WCAG 2.2 AA-oriented accessibility contract while preserving all insurance, Local, Worker, attribution, Life secure-submission, and CoverageFit behavior.

This is a product/source certification, not a legal representation or third-party WCAG conformance attestation.

## Scope
27 public consumer surfaces are covered. `/life-ops/` remains an internal producer workspace outside the consumer UI-3 convergence program.

## Certification layer
This sprint adds two final accessibility assets, loaded after the existing UI-3/mobile presentation layers:

- `shared/accessibility-certification.css`
- `shared/accessibility-certification.js`

Every public consumer page also carries the `408farmers-accessibility-build=408-UI-3.11` build marker.

## Keyboard + focus
- retained the existing skip-to-main pattern on every public surface
- certified exactly one focusable main landmark per page
- added a final opaque high-contrast focus indicator that remains visible on light, dark, and image-backed surfaces
- preserved keyboard operation of links, buttons, forms, disclosure controls, and native dialogs
- added focus return to the mobile navigation trigger when Escape closes the menu while focus is inside it
- certified no positive `tabindex` usage

## Semantic hierarchy
- certified `lang="en"`, page titles, one main landmark, and one H1 per public page
- certified no static heading-level jumps
- certified unique IDs and valid `aria-labelledby`, `aria-describedby`, and `aria-controls` references
- certified accessible names for links/buttons/summary controls
- certified alternative text presence for all images
- certified accessible dialog names where dialogs exist

## Forms, labels + errors
- certified every non-hidden input/select/textarea has an accessible label
- preserved all native `required`, pattern, type, and form-submission behavior
- added semantic reflection of native invalid controls through `aria-invalid` without suppressing browser validation
- invalid fields now have a non-color-only border treatment in addition to existing error/status messaging
- status/live regions are made atomic so updates are announced as complete messages
- form control borders were strengthened to meet non-text contrast expectations
- placeholder text was raised to a readable AA-safe contrast level

## Contrast
The certification layer explicitly corrects the highest-risk UI-3 pairs:
- control boundaries against white
- placeholder text against white
- final focus indicator against light and dark surfaces
- small red campaign text on the dark Life canvas
- secondary action boundaries

Core UI-3 navy/red/white, muted text, footer, success/warning/error, and Life dark-mode pairs were computationally checked against the applicable project thresholds.

## Reduced motion + forced colors
- global reduced-motion preference disables non-essential animation/transition behavior and smooth scrolling
- reveal content remains visible with reduced motion
- forced-colors mode receives explicit focus, field-boundary, invalid-state, and primary-action treatment

## Zoom + reflow
- no public viewport disables user zoom
- every public page retains `viewport-fit=cover`
- text-size adjustment remains enabled
- sticky-header scroll offsets are preserved for focused/anchored content
- long legal/contact/status text can wrap
- narrow-screen reflow extends through the 320–360px CSS viewport range used by 400% desktop zoom scenarios

## Behavior freeze
No existing runtime JavaScript was changed. The sprint adds one accessibility-only runtime file and one accessibility-only stylesheet.

Exact-hash preservation was certified for the existing runtime/Worker/catalog set, including:
- `_worker.js`
- Home / Bundle / Buyer runtimes
- campaign and attribution runtimes
- Life intake, secure-submit, conversion, and producer-queue runtimes
- Local catalog/data-model/directory/detail/join/attribution runtimes
- CoverageFit invitation/launch sender behavior

Form actions, methods, field names, types, required semantics, values, autocomplete/pattern boundaries, and submit controls were also compared against the UI-3.10 input and preserved.

## QA
- UI-3.11 accessibility contract: **597/597**
- per-page structural/semantic checks: certified across **27/27** public consumer surfaces
- protected runtime freeze: **39/39**
- form-contract freeze: **27/27**
- explicit contrast pairs: **10/10**
- runtime JavaScript syntax: **38/38**
- Home hidden-required submit regression: **12/12**
- Home Advanced Mode routing: **16/16**
- Home deep-route assets: **12/12**
- Advanced Mode redirect-loop regression: **10/10**
- internal links/assets: **598 checked / 0 broken**

## Deliberate exclusion
`/life-ops/` remains outside the consumer UI-3 accessibility certification scope. It continues to preserve its existing internal producer behavior and prior accessibility layer.

## Parallel Local status
LOCAL-1.10 remains technically certified with a production NO-GO for the planned three-merchant pilot until real Auto + Home merchants and the documented external closeout items are completed. UI-3.11 does not change that operational status.

## Next sprint
**408-UI-3.12 — End-to-End Functional Regression**
