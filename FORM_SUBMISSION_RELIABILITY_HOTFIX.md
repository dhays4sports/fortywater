# 408FARMERS Form Submission Reliability Hotfix

- Starts from the user-provided current `fucker-main` source.
- All standard lead forms now have a direct Formspree HTML action fallback.
- Browser submission waits for confirmed lead delivery instead of racing away after 900 ms.
- Same-origin `/api/lead` relay is attempted first, then direct browser Formspree AJAX.
- Relay sends a canonical Referer for Formspree Restrict-to-Domain compatibility.
- If both AJAX transports fail, the next click performs a native HTML POST directly to Formspree.
- Optional CoverageFit/post-lead errors can no longer strand a lead after Formspree confirms it.
