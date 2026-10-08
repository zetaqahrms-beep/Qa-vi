# PART 5 — Zenita, Partner, Support, FAQ, What's New, Privacy Policy, Security

**Tab:** 890709617. **Viewport:** 1291 × 775, DPR 1.14.
**State left behind:** none. None of these pages carries a form.

## Possible bugs

| # | Page | Saw (exact) | Viewport |
|---|---|---|---|
| P5-1 | FAQ | Category links land on the home page | 1291 × 775 |
| P5-2 | Privacy Policy | `Last updated: November 14, 2021` | 1291 × 775 |
| P5-3 | Zenita | `Tap a tier — Zenita will explain it` on the desktop page | 1291 × 775 |
| P5-4 | Partner (footer) | Zenita launcher covers the `Security` link | 1291 × 775 |

### P5-1 — FAQ category links land on the home page
The seven category chips are anchors with in-page targets:

`Products` → `#products`, `Pricing & licensing` → `#pricing`, `Deployment` → `#deployment`, `Implementation & onboarding` → `#implementation`, `Support` → `#support`, `Security & compliance` → `#security`, `Partners` → `#partners`.

**All seven target sections exist on the FAQ page**, at absolute tops 590, 984, 1295, 1550, 1805, 2059 and 2314.

Four chips tested, each from a fresh load of `/ERPSaasUI/faq`:

| Chip | How | Result |
|---|---|---|
| `Security & compliance` | keyboard, focus + Enter | url becomes `/ERPSaasUI/home` |
| `Partners` | keyboard, focus + Enter | url becomes `/ERPSaasUI/home`, title becomes `Best HRMS and ERP Software Dub…` |
| `Products` | keyboard, focus + Enter | url becomes `/ERPSaasUI/home` |
| `Deployment` | mouse, at its measured centre (607, 500) | url becomes `/ERPSaasUI/home` |

Confirmed on screen: after activating a chip the browser shows the home page hero. I tested four of the seven and all four behaved this way; I have not tested the other three.

### P5-2 — Privacy Policy date
On `/ERPSaasUI/privacy-policy`, beside the contact address, the page reads:
> `Last updated: November 14, 2021`

Confirmed on screen by zoom. On the same site:
- Every footer reads `© 2026 Zeta Software Pvt Ltd. All rights reserved.`
- `/ERPSaasUI/changelog` lists under **v1.6, July 2026**: > `New Security & Trust page, Privacy Policy, and this Changelog.`

### P5-3 — `Tap a tier` on the desktop page
Above the three tier cards on `/ERPSaasUI/zenita`:
> `Tap a tier — Zenita will explain it`

Confirmed on screen. This is the same wording family as P2-7 on the home page (`Tap an option to continue`), so the two may belong together.

### P5-4 — Zenita launcher over the footer `Security` link, on the Partner page
Measured on `/ERPSaasUI/zetapartner` at the foot of the page:

| Element | left | right | top | bottom |
|---|---|---|---|---|
| `Security` link | 1201 | 1244 | 746 | 763 |
| `button.zbot-launcher` | 1211 | 1271 | 695 | 755 |

Overlap: x **1211 → 1244** (33 of the link's 43 px), y **746 → 755** (9 of its 17 px). Confirmed on screen. This is the same overlap as NEW-D1, which is written up against the home footer; it occurs on the Partner page as well.

## Passed

| Page | Title | Anchors | Bad hrefs | `body.scrollWidth` |
|---|---|---|---|---|
| `/ERPSaasUI/zenita` | `Zenita — AI Assistant \| Zeta Software` | 18 | 0 | 1291 |
| `/ERPSaasUI/zetapartner` | `Partners \| Zeta Software` | 51 | 0 | 1276 |
| `/ERPSaasUI/zetasupport` | `Support \| Zeta Software` | 61 | 0 | 1276 |
| `/ERPSaasUI/faq` | `FAQ \| Zeta Software` | 50 | 0 | — |
| `/ERPSaasUI/changelog` | `What's New \| Zeta Software` | 17 | 0 | 1276 |
| `/ERPSaasUI/privacy-policy` | `Privacy Policy \| Zeta Software` | 23 | 0 | 1276 |
| `/ERPSaasUI/trust` | `Security & Trust \| Zeta Software` | 18 | 0 | 1276 |

- No page among the seven overflows the 1291 px viewport.
- No page among the seven except FAQ uses an in-page `#` link at all.
- The Partner page carries **no form** — it ends with `Become a Partner →` and `Talk to our team`, then the footer. Nothing to submit.
- The Support page carries **no form** — `WhatsApp us`, `Contact us`, `Help Desk` are links out.
- Support page figures `20+ Countries supported` and `25+ Years in market` match the home hero's `20+` and `25+`.
- `What's New` lists v1.6 down to v1.2 with dates July 2026 back to May 2026; all entries render.
- `Security & Trust` renders with `h1` `Your data, protected by design`.

## Checked and found NOT to be a defect

- **`/ERPSaasUI/security` returns `Page not found`** (`h1` `This page can’t be found`). That address is my own guess, not a link on the site — the footer's `Security` link points to **`/ERPSaasUI/trust`**, which exists and renders correctly. The 404 page itself behaves properly, offering `Back to home`, `Browse products` and `Contact us`.
- **The leading bar before the footer headings** (`| PRODUCTS`, `| SOLUTIONS`, `| COMPANY`) is a styled element, not a character. The text nodes read exactly `Products`, `Solutions`, `Company`.
