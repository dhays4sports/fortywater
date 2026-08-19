# Home form submission root-cause hotfix

## Root cause
The enhanced Home form kept `review_context` as a required select while `home-lead-progressive.css` unconditionally hid its label whenever the progressive form was active. The browser therefore rejected the final submit before any `/api/lead` or Formspree request was attempted. Because the invalid required control was `display:none`, Chromium reported `An invalid form control with name=review_context is not focusable`, making the button appear to do nothing.

## Fix
- The enhanced Home form now hides the review-context control only when its `hidden` attribute is actually set.
- Form-first Home flow explicitly reveals the review-context field and keeps it required.
- Renter/degraded branches remove the requirement whenever the review-context field is hidden.
- The submit handler now displays a visible validation message for any invalid form state.
- Home page asset query strings were advanced to force browsers to load the corrected CSS and JavaScript.

## Verified behavior
A real headless Chromium reproduction of the pre-fix package showed no network request and the hidden invalid `review_context` control. The patched package shows the field, becomes valid after a selection, and reaches `/api/lead` on final submit.
