# PART 6 — Contact page, four tabs

**Tab:** 890709617. **Viewport:** 1291 × 775, DPR 1.14. **Page:** `/ERPSaasUI/zetacontact`, title `Contact | Zeta Software`.
**Form submissions made: none.** See below.
**State left behind:** none — nothing was typed into any field and nothing was submitted.

## Why there are no submissions

This session's synthetic input does not reach anything interactive on this page. Everything below was tried with the keyboard first and then once with the mouse, as the rules require.

| What I tried | Keyboard | Mouse | Evidence |
|---|---|---|---|
| Type into `Full name` | no | no | field focused (`document.activeElement` is the input), `disabled false`, `readOnly false`, `pointer-events auto`, rect 566,227 282 × 20 — a single real `q` keypress leaves `value` empty |
| Type into `Work email`, `Company`, `Phone`, `How can we help?` | no | — | all five typed strings left every `value` empty |
| Switch to the `Partner` tab | no | no | `aria-selected` stays `Sales:true Partner:false General:false Help Desk:false` after Enter on the focused tab and after a mouse click at its measured centre (784, 86) |
| Press `Send enquiry` with empty fields | no | — | button focused at (1064, 388), Enter produces no validation message and no change to the button label |

**I later proved this was my environment, not the page.** After PART 6 I went back to the home page `What we Offer` dropdown — a control that had worked reliably earlier in this same run (focus + Enter took `aria-expanded` from `false` to `true`, confirmed on screen). It now does nothing: `aria-expanded` stays `false`. The `Free Consultation` popup, which a mouse click at (1176, 68) opened earlier in this run, also stopped opening at the same coordinates. The tab reports `document.visibilityState: hidden`, which blocks real key events.

So the input channel for this session died partway through the run. Nothing on this page is implicated.

**Everything interactive on the Contact page is therefore NEEDS MANUAL CHECK**, and the four tab submissions did not happen.

## What I could measure without interacting

### Sales tab (the tab that is selected on load)

| Item | Value |
|---|---|
| Fields | 8 — `Your full name`, `you@company.com`, `Your company`, a select, `8–9 digit number`, two more selects, `Tell us about your business, team size and the modules you need…` |
| Submit label | `Send enquiry` |
| Labels | 10 |
| **Labels carrying a `for` attribute** | **0 of 10** |
| Required markers | 6: `Full name *`, `Work email *`, `Company *`, `Dialling code *`, `Phone *`, `How can we help? *` |
| Unmarked fields | 2 of the 8 (two of the selects) |

### Page level

- **52 anchors, every one has a real `href`.** Zero empty, zero `#`.
- Four tabs present and measured: `Sales` @640,86 · `Partner` @784,86 · `General` @927,86 · `Help Desk` @1071,86. `Sales` carries `aria-selected="true"`, the other three `false`.
- Section headings on the page: `Sales enquiries`, `Talk to sales`, `Existing customer?`, `Become a partner`, `Ask Zenita`.
- Page height 2103, no horizontal overflow.

## Possible bugs

| # | Page | Saw (exact) | Viewport |
|---|---|---|---|
| P6-1 | Contact | 10 form labels, none of them tied to a field | 1291 × 775 |

### P6-1
Counted on the Sales tab: **10** visible `label` elements, and **0** of them carry a `for` attribute. (This matches what an earlier run of mine recorded; I am listing it here because the Contact page is this part's subject.)

## NEEDS MANUAL CHECK

1. `Sales` tab — fill with the QA values and submit once; record the success message.
2. `Partner` tab — switch to it, fill, submit once; record the success message.
3. `General` tab — same.
4. `Help Desk` tab — same.
5. Press `Send enquiry` on an empty Sales form and record what validation appears.
6. Whether the two unmarked selects are in fact optional.
