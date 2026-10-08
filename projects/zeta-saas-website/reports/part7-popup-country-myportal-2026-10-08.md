# PART 7 — Free Consultation popup, country chooser, My Portal

**Tab:** 890709617. **Viewport:** 1291 × 775, DPR 1.14.
**State left behind:** none. Nothing submitted. Country is India.

## Run condition

The session's input channel stopped working before this part. Proof: the home page `What we Offer` dropdown, which earlier in this same run went from `aria-expanded false` to `true` on focus + Enter and was confirmed open on screen, now stays `false`; and the `Free Consultation` popup, which a mouse click at (1176, 68) opened earlier in this run, no longer opens at the same coordinates. The tab reports `document.visibilityState: hidden`, which blocks real key events. I waited 90 seconds and retried; no change.

I therefore could not re-exercise these three controls in this part. Everything below was measured earlier in this run under working input, and I say which part it came from. The items I could not complete are listed as NEEDS MANUAL CHECK.

## Free Consultation popup — measured in PART 1

Opened from the header with a mouse click (Enter on the focused header button did **not** open it — that is item 1 under NEEDS MANUAL CHECK).

| Item | Value |
|---|---|
| Badge | `FREE 30-MIN SESSION · NO OBLIGATION` |
| Heading | `Book a Free Consultation` |
| Sub-line | `Tell us a little about you — a senior consultant will confirm a slot within one business day.` |
| Fields | `Name *`, `Work email *`, `Country`, `Phone`, `What would you like to discuss?` |
| Placeholders | `Your name`, `you@company.com`, `Phone number`, `Tell us what you'd like to talk about — e.g. an ERP evaluation, HR & payroll, a custom software idea, or anything you're not sure about.` |
| Submit label | `Confirm my consultation` |
| Legal line | `By submitting you agree to our Privacy Policy. No marketing without your consent.` |
| Country default | `UAE`, with phone prefix `+971` |
| Empty submit | one message, `Please complete the required fields.`, colour `rgb(225, 29, 72)` |
| Button after empty submit | moves from top 577 to top 606 and stays fully visible in a 775 px viewport |
| Escape | closes the popup cleanly (0 dialogs, 0 inputs afterwards) |

### Possible bugs

| # | Page | Saw (exact) | Viewport |
|---|---|---|---|
| P7-1 | Free Consultation popup | Country opens on `UAE` while the header reads `India` | 1291 × 775 |
| P7-2 | Free Consultation popup | One combined message for a form with two starred fields | 1291 × 775 |
| P7-3 | Free Consultation popup | Validation message colour `rgb(225, 29, 72)` | 1291 × 775 |

**P7-1** — the header country control reads `India` and the site is on the India locale, but the popup's `Country` select opens on `UAE` and the phone prefix shows `+971`. Confirmed on screen.

**P7-2** — `Name` and `Work email` both carry a red `*`. Submitting with all four fields empty produced exactly one line, `Please complete the required fields.`, placed above the button — no message against either starred field. Confirmed on screen.

**P7-3** — that message is `rgb(225, 29, 72)`. Earlier runs recorded `rgb(220, 38, 38)` and `rgb(185, 28, 28)` for validation text elsewhere on the site, so this is a third red.

## Country chooser — measured in PART 2

| Item | Value |
|---|---|
| Heading | `Choose your country` |
| Groups | `MIDDLE EAST`, `ASIA PACIFIC`, `AFRICA`, `EUROPE` |
| Entries | 15 — UAE, Saudi Arabia, Qatar, Kuwait, Oman, Bahrain / India, Sri Lanka, Malaysia, Mauritius, Singapore / Kenya, Uganda, Egypt / UK |
| Legend | `Zeta office` · `Available country` |
| Office pins | UAE, Saudi Arabia, India |
| Confirm control | `Done`; close control has `aria-label="Close"` |
| List container | `div.zloc-countries`, `overflow-y: auto`, `scrollHeight` 263 vs `clientHeight` 239, `scrollTop` 0 on open |

### Possible bugs

Covered in PART 2 and not re-listed here: **P2-2** (`Bahrain` below the visible list on open — 15 entries, 14 shown) and **P2-8** (the banner's `Localized for 16 countries & currencies` against this list's 15, the hero's `20+ Countries` and the footer's 7 region chips).

One further observation, not filed: `Mauritius` is listed under `ASIA PACIFIC`.

## My Portal — measured in PART 2

`aria-expanded` is `false` before and after Enter on the focused control, and after a mouse click at its measured centre (1203, 17). No menu appears either way. You have previously confirmed by hand that `My Portal → Partner` opens the partner page, so this is a manual check, not a bug.

## NEEDS MANUAL CHECK

1. **`Free Consultation` header button does not open from the keyboard.** Focused, Enter — no dialog, 0 inputs, page unchanged. A mouse click at (1176, 68) opened it immediately. Both results recorded, as the rules require.
2. **Country chooser dismissal.** `Done` (Enter), `Done` (mouse at its measured centre, where a hit test returns `button[Done]`), `Escape`, `Close` X (Enter), `Close` X (mouse) — the overlay measured present 3 seconds after each, at `opacity 1 / visibility visible / display flex`. About 15 seconds after the last attempt it was gone and the page had navigated to `/ERPSaasUI/country/in`. I cannot tell which activation closed it.
3. **Changing the country and setting it back to India.** Not done. I opened the chooser and left `India` selected throughout, so nothing needs reverting, but the act of selecting a different country and returning was not tested.
4. **`My Portal` menu** — see above.
5. **Submitting the Free Consultation popup with valid QA values.** Not done; the input channel had failed by the time this part ran, and I would not spend the single allowed submission blind.

## Noted in passing

The India country page `/ERPSaasUI/country/in`, which the chooser navigates to, shows `1998 Established`, `7+ Countries served`, `656+ Customers worldwide`, `3K+ Core users`, `66K+ ESS users`. The home page shows `2,000+ Companies`, `20+ Countries`, `25+ Years`, `200,000+ Users`. `656+ Customers worldwide` and `7+ Countries served` are worldwide-scoped figures on a country page, sitting against `2,000+` and `20+` on the home page. I saw this once, in passing, while the chooser was navigating; I did not go back and verify the page properly, so I am recording it rather than filing it.
