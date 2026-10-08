# PART 3 — Products page

**Tab:** 890709617. **Viewport:** 1291 × 775, DPR 1.14. **Page:** `/ERPSaasUI/products`, title `Products | Zeta Software`.
**State left behind:** none. No form on this page.

## Possible bugs

| # | Page | Saw (exact) | Viewport |
|---|---|---|---|
| P3-1 | Products | `MODULES` / `CAPABILITIES` boxes sit at three different heights in one row | 1291 × 775 |
| P3-2 | Products | Single apps carry `Explore platform →` under a `ZETA PRODUCT` kicker | 1291 × 775 |

### P3-1 — count boxes misaligned within a row
Measured the top edge of every visible `MODULES` label. Cards are laid out three to a row at left 146 / 505 / 863.

| Row | left 146 | left 505 | left 863 | spread |
|---|---|---|---|---|
| Enterprise | 157 | 157 | — | 0 |
| Business Suite 1 | — | — | — | aligned |
| **Business Suite 2** (`Inventory`, `Procurement`, `Sales & Distribution`) | **420** | **443** | **468** | **48 px** |
| **Business Suite 3** (`Asset`, `Document Management`, `Support Portal`) | **754** | **779** | **754** | **25 px** |
| Business Suite 4 | 1065 | 1065 | — | 0 |
| Industry 1 | 1506 | 1506 | 1506 | 0 |
| Industry 2 | 1793 | 1793 | 1793 | 0 |
| Industry 3 | 2104 | 2104 | — | 0 |

Confirmed on screen: in the `Inventory` / `Procurement` / `Sales & Distribution` row the three count boxes step downwards left to right, while the `Explore platform →` links below them all sit level at the same height. The two affected rows are the ones where only some cards have a two-line title or a two-line description.

### P3-2 — `Explore platform` on cards labelled `ZETA PRODUCT`
Every product card's call to action reads:
> `Explore platform →`

The kicker above the title differs by card type:
- `ERP Enterprise` and `HRMS Enterprise` read `ENTERPRISE PLATFORM`.
- All 19 others — `Accounting`, `Payroll`, `CRM`, `Inventory`, `Procurement`, `Sales & Distribution`, `Asset`, `Document Management`, `Support Portal`, `E-commerce`, `Help Desk`, `Education`, `Healthcare`, `Construction`, `Manufacturing`, `Wholesale & Retail`, `Real Estate`, `Airport Management`, `Field Service Management` — read `ZETA PRODUCT`.

Confirmed on screen across four screenshots.

## NEEDS MANUAL CHECK

**The three category jump cards move the page 0 px.** Targets exist and are well below the fold:

| Card | Badge | Target | Target absolute top |
|---|---|---|---|
| `Enterprise` | `2 products` | `#group-enterprise` | 583 |
| `Business Suite` | `11 products` | `#group-suite` | 1052 |
| `Industry` | `8 products` | `#group-industry` | 2401 |

Attempts, all from a fresh load at `body.scrollTop` 0, each followed by an 8-poll settle check:
- `Enterprise` — mouse at the measured centre of its `span.phero-jump` (280, 498): `body.scrollTop` **0**.
- `Business Suite` — mouse at (638, 478): **0**.
- `Industry` — mouse at (996, 498): **0**.
- `Industry` — keyboard, card focused then Enter: **0**.
- (In PART 1, in the other tab, `Enterprise` by keyboard and by mouse also gave **0**.)

`document.documentElement.scrollTop` and `.gcanvas.scrollTop` also stayed at 0 throughout. Mouse and keyboard both tried, so per the rules this is a manual check, not a bug.

## Passed

- **38 anchors, every one has a real `href`.** Zero empty, zero `#`.
- **Badge counts match the cards.** `2 products` → 2 cards; `11 products` → 11 cards; `8 products` → 8 cards. Each badge appears twice (jump card and section header) with the same figure both times.
- **All three section anchors exist**: `group-enterprise`, `group-suite`, `group-industry`.
- **Product links are distinct and work.** 21 product destinations, no duplicates among them. Opened `CRM` from the keyboard: lands on `/ERPSaasUI/crm`, title `CRM — Products | Zeta Software`, `h1` `CRM`, and the page renders its own module list (`Leads & Contacts`, `Sales Pipeline`, `Engagement`, `Service`) — 4 modules, matching the `4 MODULES` on its card.
- **No horizontal page overflow.** `body.scrollWidth` 1276 against a 1291 viewport.
- Scrolling down and back up returns cleanly to the top (also covered in PART 1 under ZNW-172).

## Checked and found NOT to be a defect

- **Items measuring up to 6,485 px wide at absolute top 103.** This is the product ticker that runs under the header (`Accounting — Cloud accounting…`, `Payroll — Hire, pay and grow…`, and so on). It is a marquee, and the page itself does not overflow.

## Not reported — already open or by design

- No footer on this page — on the do-not-report list.
- **Supporting evidence for ZNW-178 / 179 / 184, not a new ticket:** this page names the same sectors `Healthcare`, `Manufacturing`, `Construction`, `Education`, while the home hero hover labels read `Health`, `Manufacture`, `Construction`, `Education`, `Industry`.
