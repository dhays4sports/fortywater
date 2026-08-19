# 408-FARMERS / CoverageFit Design System

Sprint 1.2 introduces `shared/design-system.css`, a reusable visual foundation shared by the homepage, campaign pages, and future CoverageFit integrations.

## Core tokens

- Colors: `--cf-color-*`
- Typography: `--cf-font-*`, `--cf-text-*`
- Spacing: `--cf-space-*`
- Radius: `--cf-radius-*`
- Shadows: `--cf-shadow-*`
- Motion: `--cf-transition-*`

## Reusable components

- `.cf-container`
- `.cf-eyebrow`, `.cf-heading`, `.cf-muted`
- `.cf-btn`, `.cf-btn--primary`, `.cf-btn--secondary`, `.cf-btn--wide`
- `.cf-card`, `.cf-card--flat`, `.cf-card--soft`
- `.cf-icon-tile`
- `.cf-chip`
- `.cf-panel-dark`
- `.cf-link-button`
- `.cf-grid-3`, `.cf-grid-4`
- `.cf-reveal`

## Implementation rule

New pages should use `cf-*` classes first. Page-specific CSS should only control unique layout or campaign-specific artwork. This keeps typography, controls, spacing, and interaction behavior consistent across the ecosystem.

## Sprint 1.3B visual polish

The optional `shared/visual-polish.css` layer refines gradients, surface depth, icon treatment, spacing, and responsive presentation without changing funnel behavior. Load it after `motion.css` on premium campaign pages.

## UI-3.8 — Local mode
408FARMERS Local consumes the same navy/red/white UI-3 foundation but uses a denser discovery-oriented composition:
- compact Local intro
- directory-first content order
- pill category filters
- restrained merchant cards and perk panels
- merchant value before optional insurance conversion
- CSS fallback artwork when merchant-owned imagery is not available
- no invented distance, rating, review, geolocation, or map UI
- merchant join forms use the shared UI-3 field/button/focus language

Local remains a public merchant-discovery program separate from insurance purchasing, quoting, pricing, eligibility, and underwriting.

## UI-3.10 — Mobile interaction layer
`shared/mobile-interaction.css` is the final consumer-side interaction layer after page-specific UI-3 styling.

Mobile rules:
- every public UI-3 page uses `viewport-fit=cover`
- platform header, mobile navigation, footer, and dialogs honor safe-area insets
- touch/coarse-pointer controls keep a 44px minimum target; primary conversion controls retain their previously certified 48–52px sizing
- text-entry controls render at 16px or larger on mobile to prevent iOS focus zoom
- focused fields and anchor destinations reserve sticky-header scroll margin and additional lower keyboard scroll margin
- Professional Programs and Local filter families scroll horizontally when labels would otherwise become too small
- phone CTA groups stack; disclosures, consent, warnings, and validation states are never covered by a fixed submit bar
- short-landscape layouts prioritize the current task by reducing oversized media/type and disabling counterproductive sticky sidecars
- dynamic viewport units are progressive enhancement only; standard viewport units remain the fallback

This layer is presentation/interaction-only. Product behavior remains owned by each existing route/runtime contract.

## UI-3.11 — Accessibility certification layer
`shared/accessibility-certification.css` and `shared/accessibility-certification.js` load after the UI-3/mobile presentation layers on every public consumer surface.

Accessibility rules:
- opaque dual-surface `:focus-visible` treatment is final and must not be overridden by page-specific UI
- form control boundaries use a 3:1-capable border against white; invalid state uses border thickness plus ARIA/native messaging, not color alone
- placeholder/instructional text remains readable against white
- links embedded inside prose/legal copy retain a non-color cue
- small campaign-red Life text on dark surfaces uses the lighter certified accent; red CTA backgrounds remain the darker campaign red to preserve white-text contrast
- reduced-motion and forced-colors preferences remain global user controls
- public viewport metadata must never disable zoom
- public pages preserve one focusable main landmark, one H1, valid labeling/ARIA references, and skip-to-main navigation

This layer is semantics/presentation only. Existing product runtimes, Workers, form contracts, attribution, Local, Life secure submission, and CoverageFit handoff behavior remain authoritative.

## UI-3.13.1A — Human Trust Foundation
`shared/human-trust.css` adds an opt-in human/editorial layer on top of the certified UI-3 platform. It is intentionally inert until a route uses an `ht-*` class.

Governing principle: **Modern system underneath. Human relationship on the surface.**

Key rules:
- Life is excluded; UI-3.7 remains authoritative there.
- Dylan appears as an editorial trust signature, not a feature card or testimonial.
- Human/context photography supports identity and trust; essential copy stays live HTML.
- Professional Programs may use a restrained warm-gold identity accent, but Farmers red remains the primary CTA color.
- Remove nonessential containers only when grouping/comprehension is not harmed.
- Post-submit surfaces may use first-person Dylan voice only when technically accurate.
- Local remains publicly accessible with **No insurance purchase or quote required.**

See `HUMAN-TRUST-DESIGN-SYSTEM.md` for the full production contract and `HUMAN-TRUST-COMPONENT-REGISTRY.json` for the machine-readable component/surface registry.

