# PART 1 — Retest of 13 open tickets

**Date:** 8 October 2026
**Site:** `https://zetahrms-saas.com:8085/ERPSaasUI`
**Browser:** Edge 154, new tab (id 890709625), desktop only
**Viewport:** 1291 × 775 CSS px, devicePixelRatio 1.14 (≈114% zoom) — same zoom as every prior run
**Interaction:** keyboard inside the page body; mouse used only where the keyboard did nothing, and both results reported
**State left behind:** none. No form submitted. Header country chooser untouched (India). Popup closed.

---

## Result table

| # | Ticket | Verdict |
|---|---|---|
| 1 | ZNW-169 | REPRODUCES |
| 2 | ZNW-171 | REPRODUCES |
| 3 | ZNW-181 | REPRODUCES |
| 4 | ZNW-183 | REPRODUCES |
| 5 | ZNW-185 | REPRODUCES |
| 6 | ZNW-178 | REPRODUCES |
| 7 | ZNW-179 | REPRODUCES |
| 8 | ZNW-184 | REPRODUCES |
| 9 | ZNW-180 | REPRODUCES |
| 10 | ZNW-166 | DOES NOT REPRODUCE |
| 11 | ZNW-172 | DOES NOT REPRODUCE |
| 12 | ZNW-182 | REPRODUCES |
| 13 | NEW-A2 | CANNOT TELL at 1280 × 650 — see entry |
| 14 | NEW-D1 | REPRODUCES |
| 15 | NEW-E1 | REPRODUCES |

(13 tickets; ZNW-178 / 179 / 184 share one screen and one screenshot.)

---

## 1. ZNW-169 — REPRODUCES

**Where:** `/ERPSaasUI/home`, browser tab title.

**What is shown:** the tab title reads

> `Best HRMS and ERP Software Dubai/India | Zeta Softwares`

The trailing company name is **"Zeta Softwares"**. The header wordmark on the same page reads **"ZETA SOFTWARE"**, and the Contact page title reads `Contact | Zeta Software`.

---

## 2. ZNW-171 — REPRODUCES

**Where:** `/ERPSaasUI/home`, main top navigation bar.

**What is shown:** the menu item reads

> `What we Offer`

One occurrence on the page. Confirmed on screen by zoom, not from page text alone. The sibling items on the same bar are `Home`, `Zenita`, `Partner`, `Support`, `Contact`.

---

## 3. ZNW-181 — REPRODUCES

**Where:** `/ERPSaasUI/home`.

**What is shown:**

> `Run Live In 30 Minutes`

The word `In` carries a capital I.

---

## 4. ZNW-183 — REPRODUCES

**Where:** `/ERPSaasUI/home`.

**What is shown:** two different forms of the same region name on one page.

`Asia Pacific` — 2 occurrences:

1. > `…Middle East, Africa & Asia Pacific — with regional compliance…`
2. > `Cloud · 99.9% On-Premise | Middle East, Africa & Asia Pacific | Purpose-built for your markets — ZATCA, WPS, GOSI…`

`APAC` — 1 occurrence, in the footer:

3. > `All-in-one ERP & HRMS for growing businesses across GCC, India & APAC — Finance, HR, Inventory, CRM and Production.`

---

## 5. ZNW-185 — REPRODUCES

**Where:** `/ERPSaasUI/home`.

**What is shown:** two different capitalisations of the same term on one page.

Lowercase `on-premise` — 2 occurrences:

1. Hero sub-line: > `Cloud (SaaS) or on-premise (HRMS, ERP).` — confirmed on screen by zoom
2. > `…or a full on-premise deployment on your own infrastructure.`

Title case `On-Premise` — 2 occurrences:

3. Card heading: > `SaaS & On-Premise`
4. Chip: > `Cloud · 99.9% On-Premise`

---

## 6–8. ZNW-178, ZNW-179, ZNW-184 — REPRODUCES

**Where:** `/ERPSaasUI/home`, hero graphic. Hover the **Industry** node at (1140, 325).

**What is shown:** five labels appear around the node. Confirmed on screen by zoom. They read, exactly:

> `Health`
> `Education`
> `Construction`
> `Manufacture`
> `Industry`

One screenshot covers all three tickets.

---

## 9. ZNW-180 — REPRODUCES

**Where:** `/ERPSaasUI/home`, Zenita speech bubble beside the orb at bottom right.

**What is shown:** three different bubble texts appeared across one visit, each confirmed on screen. Quoted exactly:

1. At the top of the page, on load:
   > `Welcome to Zeta! One platform for your whole business. Ask me anything. 👋`
2. While scrolled to roughly the customer-logo band:
   > `Built for your region, designed for growth. Curious why teams pick Zeta?`
3. At the "Let's build what's next for your business." contact section:
   > `Ready to talk to a human too? I can point you to the right people.`

In reading 2 the bubble sat on top of the customer logo row and overlapped the `KLM AXIVA FINVEST` logo.

The bubble did not appear at the top of the page during roughly 13 seconds of waiting on one earlier load — only the orb was visible. I could not establish what makes it appear, so I am not stating a rule about when it shows.

---

## 10. ZNW-166 — DOES NOT REPRODUCE

**Ticket asks:** home contact form — press Send with all fields empty; is Send pushed under the footer? (1291 × 775)

**First, a correction to the premise.** The home page has **no contact form of its own**. Scrolled from top (scrollTop 0) to the footer (scrollTop 5287 of a 5960 scrollHeight), the count of visible `input` and `textarea` elements on `/ERPSaasUI/home` was **0** at every position. The home contact section offers two buttons only:

> `Contact Us →`   and   `Email Sales`

`Contact Us` is an `<a href="/ERPSaasUI/zetacontact">` and navigates away to the Contact page.

The only form reachable from the home page is the **"Book a Free Consultation"** popup, opened from the header button. I tested that.

**Steps**

1. Load `/ERPSaasUI/home` at 1291 × 775, scrollTop 0.
2. Open the header **Free Consultation** popup.
3. Leave every field empty. Focus the button and press Enter.

**What is shown**

- Button label before: `Confirm my consultation`, rect left 422, top **577**, right 870, bottom **622**.
- After Enter, one message appears above the button:
  > `Please complete the required fields.`
  colour `rgb(225, 29, 72)`, at top 549.
- Button after: left 422, top **606**, right 870, bottom **651**. It moved **down 29 px**.
- Viewport height is **775**. Button bottom **651 < 775** — the button stays **fully visible**, and the line `By submitting you agree to our Privacy Policy. No marketing without your consent.` is still visible below it. Confirmed on screen.
- This is a centred modal dialog; no page footer is involved at all.

**Verdict: DOES NOT REPRODUCE** at 1291 × 775. Nothing was pushed under anything.

**Two things I did see while doing it** (not this ticket, listed under Observations below): the popup did not open from the keyboard, and only one combined message appears for the whole form — no per-field messages.

---

## 11. ZNW-172 — DOES NOT REPRODUCE

**Ticket asks:** Products page — after clicking a category card, can you get back to the top?

**Steps and readings** on `/ERPSaasUI/products`, pointer parked at x=30 for every measurement:

1. Fresh load. `document.body.scrollTop` **0**, `div.gcanvas` scrollTop **0**, `h1` "Products" at top **130**.
2. **Enterprise** card — focused the card and pressed Enter. After settle (8 consecutive identical polls): body **0**, gcanvas **0**. Nothing moved. The card took a visible focus ring.
3. Same card — clicked `Jump to section ↓` with the mouse at (197, 501), inside the measured span (133→427, 481→514). After settle: body **0**, gcanvas **0**. Nothing moved.
4. **Industry** card — clicked `Jump to section ↓` with the mouse at (996, 498). Its target `#group-industry` sits at absolute top **2401**, so a jump would have to move the page. After settle: body **0**, gcanvas **0**. Nothing moved.
5. Scrolled down with the real wheel, 10 ticks: body **1000**, gcanvas **0**, h1 at top **-870**.
6. Scrolled up with the real wheel, 15 ticks: body **0**, gcanvas **0**, h1 `Products` back at top **130**. Confirmed on screen.

**Verdict: DOES NOT REPRODUCE.** You can get back to the top. `div.gcanvas` scrollTop stayed at 0 for the whole run and its computed `overflow` now reads **`clip`**, so the scroll trap behind DEF-009 does not occur on this page.

The reason the ticket's situation never arises is that **clicking a category card does not move the page at all** — 0 of 3 cards, keyboard and mouse. That is listed under Observations.

---

## 12. ZNW-182 — REPRODUCES

**Ticket asks:** Send button label — home form vs Contact page form.

**What is shown:** the two labels differ.

| Form | Button label |
|---|---|
| Home — "Book a Free Consultation" popup (the only form reachable from the home page) | `Confirm my consultation` |
| Contact page `/ERPSaasUI/zetacontact`, **Sales** tab | `Send enquiry` |

Both confirmed on screen. The Contact page carries four tabs: `Sales`, `Partner`, `General`, `Help Desk`.

---

## 13. NEW-A2 — CANNOT TELL at 1280 × 650

**Ticket asks:** home hero, hover "Industry" at **1280 × 650** — is "Construction" cut off at the right edge?

**Why CANNOT TELL:** I could not reach that viewport. `resize_window` to 1280 × 650 returned `Successfully resized window containing tab 890709625 to 1280x650 pixels`, and the page then reported `inner:1291x775 outer:1685x906`. The viewport did not change. This is the sixth time this session the call has reported success without changing anything. Browser zoom was left alone, as instructed.

**What I can report, at 1291 × 775:** the label **is** cut off.

- Measured: `Construction` text left **1232**, right **1301** — **10 px past** the 1291 px viewport edge.
- On screen it reads **`Constructio`**, with the pill outline running off the edge. Confirmed by zoom.
- `documentElement.scrollWidth` **1291** = `clientWidth` **1291**, and `body.scrollWidth` **1291** — **no horizontal scrollbar appears**, so the cut-off part cannot be scrolled into view.
- The labels orbit the node. A second reading of the same label gave left 1222, right **1311** — **20 px past** the edge. The overflow amount varies with the animation; it was past the edge in both readings.

Since 1280 is narrower than 1291 I would not expect this to improve at the ticket's size, but I did not see it at 1280 × 650 and am not reporting it as seen.

---

## 14. NEW-D1 — REPRODUCES

**Where:** `/ERPSaasUI/home`, footer bottom bar, scrollTop 5287. Viewport 1291 × 775, zoom ≈114%.

**What is shown:** the Zenita launcher sits on top of the `Security` link.

| Element | left | right | top | bottom |
|---|---|---|---|---|
| `Security` link text | 1210 | 1254 | 748 | 761 |
| `button.zbot-launcher` (inside `div.zbot-root`) | 1211 | 1271 | 695 | 755 |

- Horizontal overlap **1211 → 1254** = **43 px of the link's 44 px width**.
- Vertical overlap **748 → 755** = **7 px of its 13 px height**.
- Hit test at five points along the link, at its vertical middle (y 754): the leftmost point returns the `<a>`; the other **four return `span.zbot-pulse`**.
- Confirmed on screen by zoom: the word `Security` is overlaid by the orb and its glow ring.

For contrast, the neighbouring `Privacy Policy` link (1118 → 1190) returns its own `<a>` at all five points.

---

## 15. NEW-E1 — REPRODUCES

**Where:** `/ERPSaasUI/home`, Solution Finder section, `.home-scroller` scrollTop 2021. Viewport 1291 × 775, zoom ≈114%.

**What is shown:** the section heading overlaps the left page menu.

- Heading `Find your fit in under two minutes`, second line spans left **102** → right **476**, vertically **339 → 389**.
- Left-menu item `Solution Finder` text spans left **32** → right **121**, vertically **355 → 387**.
- The last **19 px** of the menu item sit under the heading's second line.
- On screen the menu item reads **`Solution Find`** — the final letters are covered by the `u` of `under`. Confirmed by zoom at two magnifications.

The item is still operable: a hit test at (117, 371) returns the menu's own `<button>`, so this is a readability problem, not a dead control. The other four menu items in that band (`Why Zeta` 32→89, `Customers` 32→97, `Zenita` 32→69) end to the left of the heading and are not covered.

---

## Observations picked up while retesting

Not tickets, not counted above. Listed so they are not lost.

1. **Free Consultation popup does not open from the keyboard.** With the header `Free Consultation` button focused, Enter did nothing — no dialog, 0 visible inputs, page unchanged. A single mouse click at (1176, 68) opened it immediately. Both results as required by the rule.

2. **Products page jump controls are inert.** All three `Jump to section ↓` controls (`span.phero-jump` inside a `<button>` card) moved the page 0 px, by keyboard and by mouse, measured after settle. Section anchors `#group-enterprise` (abs top 583) and `#group-industry` (abs top 2401) exist in the page; I found no id matching the **Business Suite** card.

3. **Country default differs between the header and the popup.** The header chooser shows `India`. The Free Consultation popup opens with Country `UAE` and the phone prefix `+971`.

4. **A third validation red.** The popup's message `Please complete the required fields.` is `rgb(225, 29, 72)`. Earlier runs recorded `rgb(220, 38, 38)` and `rgb(185, 28, 28)` elsewhere on the site.

5. **One message for the whole popup form.** Submitting with all four fields empty produced a single combined line, not a message per field. `Name` and `Work email` both carry a red `*`.

6. **`.home-scroller` settles slowly.** After activating the left-menu `Contact` item, scrollTop still read 2021 six seconds later and 4716 once it had finished. Readings taken before an 8-poll settle check are not trustworthy on this page.
