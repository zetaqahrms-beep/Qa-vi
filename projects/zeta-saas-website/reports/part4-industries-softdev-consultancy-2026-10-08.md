# PART 4 — Industries, Software Development, Business Consultancy

**Tab:** 890709617. **Viewport:** 1291 × 775, DPR 1.14.
**State left behind:** none. No forms on these three pages.

## Possible bugs

| # | Page | Saw (exact) | Viewport |
|---|---|---|---|
| P4-1 | Business Consultancy | Two different apostrophe characters in body text on one page | 1291 × 775 |

### P4-1 — mixed apostrophe characters
On `/ERPSaasUI/business-consultancy`, counted across the page text: **1** curved apostrophe, **2** straight ones.

- Curved, in the opening paragraph: > `Zeta’s consultants — often alongside a local partner — come to your organisation…`
- Straight, in the side card heading and its body: > `Let's talk it through` and > `Tell us what you're trying to build or improve.`

Both confirmed on screen by zoom, and both are visible in the same screenshot.

## Passed

### Industries — `/ERPSaasUI/industries`, title `Industries | Zeta Software`
- **33 anchors, every one has a real `href`.** Zero empty, zero `#`.
- The claim `Eight industry clouds, one platform.` matches **8** industry cards.
- 8 distinct destinations, one per card: `/for/education`, `/for/healthcare`, `/for/construction`, `/for/manufacturing`, `/for/retail`, `/for/real-estate`, `/for/airport-management`, `/for/field-service-management`.
- All 8 cards carry real content (measured text length 258–325 characters each, card size 336 × 427–475).
- No horizontal page overflow: `body.scrollWidth` 1276 against a 1291 viewport.
- Each card's call to action names its own sector — `Explore Education`, `Explore Healthcare`, `Explore Construction`, `Explore Manufacturing`, `Explore Wholesale & Retail`, `Explore Real Estate`, `Explore Airport Management`, `Explore Field Service Management`.

### Software Development — `/ERPSaasUI/software-development`, title `Software Development | Zeta Software`
- **21 anchors, 0 bad.** `body.scrollWidth` 1276, `scrollHeight` 1010 — no overflow.
- Six capability cards all render: `Web & Mobile Apps`, `APIs & Integrations`, `Cloud & DevOps`, `UI/UX & Design Systems`, `MVP & Product Engineering`, `QA, Security & Support`.
- Side card renders with `Email us sales@zetasoftwares.com` and `Talk to Sales →`.

### Business Consultancy — `/ERPSaasUI/business-consultancy`, title `Business Consultancy | Zeta Software`
- **21 anchors, 0 bad.** `body.scrollWidth` 1276, `scrollHeight` 1097 — no overflow.
- Five step cards all render: `On-site Discovery`, `Structure & Division Mapping`, `Process Analysis`, `Custom Software Build`, `Integration & Data`, `Rollout, Training & Support` (six in total).
- Side card identical in structure to the Software Development one.

## Checked and found NOT to be a defect

- **A blank card on the Industries page.** One screenshot showed a card with a green gradient header and a completely empty white body, and the `Airport Management` card missing beside it. Measuring found both cards present with 289 and 325 characters of text at 336 × 475. After waiting and nudging the scroll, both render in full on screen. It was the reveal animation caught mid-way.
- **`Explore Wholesale & Retail` wrapping to two lines** looked like it broke the row. The three links in that row share a bottom edge at **359** (`Explore Manufacturing` top 340 height 19, `Explore Wholesale & Retail` top 320 height 39, `Explore Real Estate` top 340 height 19) — they are bottom-aligned, so the row is intact.
- **Ticker items measuring up to 4,759 px wide** at absolute top 103 on the Industries page — the marquee strip under the header, same pattern as the Products page.

## Noted, not filed

The Industries page names its sectors `Healthcare`, `Manufacturing`, `Construction`, `Education` — matching the Products page and differing from the home hero hover labels. That difference is already covered by ZNW-178 / 179 / 184.
