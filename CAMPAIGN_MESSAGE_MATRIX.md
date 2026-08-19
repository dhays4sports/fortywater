# 408FARMERS Campaign Message Matrix

Build: **408-UI-3.11.1**

The first screen may adapt only when the current URL/path contains an approved campaign signal. Stored attribution may continue downstream for analytics and lead context, but it does not control presentation on a later organic visit.

| Campaign / creative | Ad hook | Matched landing hook | Route | Visual mode |
|---|---|---|---|---|
| Stevie's coaster — front | Own a Home in the South Bay? | Own a Home in the South Bay? | `/home/` | UI-3 Home |
| Stevie's coaster — back | Own the Home. Drive the Cars. Review Them Together. | Own the Home. Drive the Cars. | `/auto-bundle/` | UI-3 Bundle |
| Tech eligibility | Work in Tech? | Work in Tech? | `/tech/` | UI-3 Professional |
| Teacher eligibility | Are You a Teacher? | Are You a Teacher? | `/teachers/` | UI-3 Professional |
| Engineer eligibility | Are You an Engineer? | Are You an Engineer? | `/engineers/` | UI-3 Professional |
| Healthcare eligibility | Work in Healthcare? | Work in Healthcare? | `/healthcare/` | UI-3 Professional |
| Realtor / buyer card | Have a buyer who needs home coverage? | Need Coverage for Your Closing? | `/buyer/` | UI-3 Buyer |
| Life A | Before Anything Changes. | Before Anything Changes. | `/life/` | Life Campaign Mode |
| Life B | 20:00 | 20:00. | `/life/` | Life Campaign Mode |
| Life C | This Is the Time. | This Is the Time. | `/life/` | Life Campaign Mode |
| Life D | Health / financial picture | Your health is part of your financial picture. | `/life/` | Life Campaign Mode |
| Home flyer A/B | ZIP-specific rate / fit hook | Existing ZIP-specific matched copy | `/home/qr/<ZIP>/<variant>/` | UI-3 Home |

## Canonical future occupational URLs

These are the canonical IDs for refreshed advertising. Existing explicit aliases remain accepted by the runtime, but new creative should use the canonical `campaign_id`.

- Technology: `/tech/?campaign_id=occupation_tech_meta_v1&utm_source=meta&utm_medium=paid_social&utm_campaign=professional_eligibility&utm_content=tech_v1`
- Teachers: `/teachers/?campaign_id=occupation_teacher_meta_v1&utm_source=meta&utm_medium=paid_social&utm_campaign=professional_eligibility&utm_content=teacher_v1`
- Engineers: `/engineers/?campaign_id=occupation_engineer_meta_v1&utm_source=meta&utm_medium=paid_social&utm_campaign=professional_eligibility&utm_content=engineer_v1`
- Healthcare: `/healthcare/?campaign_id=occupation_healthcare_meta_v1&utm_source=meta&utm_medium=paid_social&utm_campaign=professional_eligibility&utm_content=healthcare_v1`

## Existing coaster URLs

- Home/front: `/home/?utm_source=stevies&utm_medium=coaster&utm_campaign=south_bay_homeowner&utm_content=home_front`
- Home + Auto/back: `/auto-bundle/?utm_source=stevies&utm_medium=coaster&utm_campaign=south_bay_homeowner&utm_content=bundle_back`

## Safe fallback

Unknown, malformed, missing, or route-incompatible campaign values render the normal evergreen page. Query values are never inserted directly into visible campaign copy.
