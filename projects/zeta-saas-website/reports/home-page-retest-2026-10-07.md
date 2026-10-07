# Home page retest — 7 October 2026

Site: `https://zetahrms-saas.com:8085/ERPSaasUI` · Area: home page, top menu and navigation, home contact form

**Browser window:** Microsoft Edge 154 (Chromium 154). Viewport **1291 × 775** CSS pixels. Device pixel ratio **1.14**, so the browser is at roughly **114% zoom, not 100%**. Every layout figure below is at that size and zoom.

Input method inside the page body: **keyboard** (focus, then Space / Enter / typing). No mouse fallback was needed.
Pointer parked at **x=30** for every reading unless a hover was the thing being tested.

---

# 1. Summary

**8 possible bugs · 21 checks passed · 3 CANNOT TELL**

---

# 2. Possible bugs

## A1 — Industry label reads "Manufacture"

**Page:** `/ERPSaasUI/home`
**Steps:** 1. Load the home page. 2. Hover the orange "Industry" node in the hero diagram at (1140, 330). 3. Five sector labels fade in.
**Saw:** The labels read "Health", "Education", "Construction", **"Manufacture"**, "Industry". The other four are sector nouns.
**Window / pointer:** 1291 × 775, DPR 1.14. Pointer on the Industry node at (1140, 330).
Confirmed on screen with a zoom screenshot, not from page text alone.

## A2 — "Construction" label runs past the right edge of the window and is cut off

**Page:** `/ERPSaasUI/home`
**Steps:** 1. Load the home page. 2. Hover the "Industry" node at (1140, 330). 3. Look at the "Construction" label, top right.
**Saw:** On screen it reads **"Constructio"** — the final "n" is missing. Measured: the label spans x = 1222 to **x = 1311**. Window inner width **1291**. It extends **20 px past the right edge**. `document.documentElement.scrollWidth` is 1291, so there is **no horizontal scrollbar** and the cut-off part cannot be reached. The element is `SPAN.hnet2-lbl`; an independent overflow scan at the end of the run returned the same right edge of 1311.
**Window / pointer:** 1291 × 775, DPR 1.14. Pointer on the Industry node at (1140, 330).

## C1 — Phone field holding "abc" shows the empty-field message

**Page:** `/ERPSaasUI/home`, contact form
**Steps:** 1. Scroll to the contact form. 2. Type `abc` into Phone Number. 3. Press Send.
**Saw:** The field still displays `abc` — the letters are kept, not stripped — and the message reads **"Please enter your phone number."** In the same submit the email field correctly switched to a format-specific message, "Please enter a valid email address."

## C2 — Success is shown only as a button label, for 4 seconds

**Page:** `/ERPSaasUI/home`, contact form
**Steps:** 1. Send a valid enquiry. 2. Watch the Send button.
**Saw:** Measured with a change-observer on the button:

```
+0.02 s   "Sending…"       blue  rgb(0, 85, 165)
+3.01 s   "Message sent"   green rgb(34, 197, 94)
+7.01 s   "Send"           still green
```

**"Message sent" is on screen for 4.0 seconds**, then the label reverts. There is **no banner and no other confirmation anywhere on the page** — a search for "thank you", "we'll be in touch", "within one business day" and "enquiry sent" returned **0 matches**. A visitor who looks away for four seconds gets no confirmation at all, and nothing says what happens next.

## C3 — Enquiry tabs carry no selected state for assistive technology

**Page:** `/ERPSaasUI/home`, contact form
**Steps:** 1. Read the Sales / Partner / General tabs.
**Saw:** `aria-selected` and `aria-pressed` are both absent on all three. The active tab is shown only visually, by an outline and colour.

## C4 — Two different reds are used for the validation messages

**Page:** `/ERPSaasUI/home`, contact form
**Steps:** 1. Submit the form empty. 2. Read the colour of each message.
**Saw:** "Please enter your name.", "Please enter your company name.", "Please enter your message." and "Please complete the required fields." are **`rgb(220, 38, 38)`**. "Please enter a valid email address." and "Please enter your phone number." are **`rgb(185, 28, 28)`**.

## C5 — No form label on the page is linked to its field

**Page:** `/ERPSaasUI/home`
**Steps:** 1. Inspect the ten form controls and ten labels.
**Saw:** **0 of 10 labels carry a `for` attribute**, and 5 of the 10 controls have no programmatic label of any kind. The four checkboxes additionally carry no `aria-required`.

## D1 — The Zenita launcher sits on top of the footer "Security" link

**Page:** `/ERPSaasUI/home`, footer
**Steps:** 1. Scroll to the very bottom. 2. Look at the bottom-right, beside "Privacy Policy".
**Saw:** Measured at the bottom of the page:

| Element | Left | Right | Top | Bottom |
|---|---|---|---|---|
| "Security" link | 1210 | 1254 | 746 | 762 |
| Zenita launcher (fixed, 60 × 60) | 1211 | 1271 | 695 | 755 |

They overlap by **42 px wide × 9 px tall**. A hit test at the centre of the "Security" link returns **a SPAN that is not the link** — the launcher is on top and takes the click. On screen the orb covers the middle of the word, which reads as "Secu…y". The link is still reachable by keyboard: focusing it and pressing Enter opened `/trust` correctly.
**Window / pointer:** 1291 × 775, DPR 1.14. Pointer parked at (30, 400); the launcher is fixed and does not follow the pointer.

## D2 — Mauritius is listed in the ASIA PACIFIC column

**Page:** `/ERPSaasUI/home`, country chooser
**Steps:** 1. Open the country chooser from the header. 2. Read the four columns.
**Saw:** Column headings sit at x = 184 (MIDDLE EAST), 417 (ASIA PACIFIC), 649 (AFRICA), 881 (EUROPE). **Mauritius sits at x = 458**, in the ASIA PACIFIC column, while a separate AFRICA column holds Kenya, Uganda and Egypt.
**Note:** this may be a deliberate sales-region grouping rather than a geographic one. Raising it as a question for the business, not as a clear fault.

---

# 3. Form submissions

Form: **Home contact form** ("Talk to a Zeta Specialist"). Values used each time — Name `QA TEST - please ignore`, Company `QA TEST`, Email `zeta.qa.hrms+saas@gmail.com`, Phone `501234567`, Message `QA TEST - Home contact form - <type> - <time> - please ignore`.

| Form | Enquiry type | Checkbox ticked | Time submitted | Success message |
|---|---|---|---|---|
| Home contact form | Sales | Learn more about the product | 15:39:02 | "Message sent" |
| Home contact form | Partner | Ask for a demo | 15:41:57 | "Message sent" |
| Home contact form | General | Fix an appointment | 15:43:00 | "Message sent" |
| Home contact form | Sales (timing run) | Learn more about the product | 16:00:40 | "Message sent" |

**The `+` in the email address was accepted** on all four. No fallback address was needed.

One note on the fourth: the message text I typed says `16:00` but I began typing it at 15:57 and submitted at 16:00:40. The time inside the message body is therefore approximate; the submitted time above is exact.

---

# 4. Passed

- Address, tab title and main heading all load: `https://zetahrms-saas.com:8085/ERPSaasUI/home`, "Best HRMS and ERP Software Dubai/India | Zeta Softwares", "One Platform for Every Business Operation". Exactly one `<h1>`.
- 65 images on the page. **0 broken, 0 missing an alt attribute.**
- Header links all go where they should: wordmark → `/home`, Home → `/home`, Zenita → `/zenita`, Partner → `/zetapartner`, Support → `/zetasupport`, Contact → `/zetacontact`, India flag → `/country/in`.
- "What we Offer" menu opens on hover; all four items correct — Products → `/products`, Software Development → `/software-development`, Business Consultancy → `/business-consultancy`, Industries → `/industries`.
- "Free Consultation" opens a dialog headed "Book a Free Consultation" and closes cleanly on Escape; the address stays `/home`.
- "My Portal" opens a menu; Customer → `/login/customer`, heading "Everything you run, in one secure workspace."
- **All 17 internal footer links activated by keyboard go to the right page:** Zeta Accounting → `/accounting`, Zeta ERP Enterprise → `/erp-enterprise`, Zeta Payroll → `/hr-payroll`, Zeta HRMS Enterprise → `/hrms-enterprise`, Zeta CRM → `/crm`, Software Development → `/software-development`, Business Consultancy → `/business-consultancy`, All Products → `/products`, Industries → `/industries`, Zenita AI → `/zenita`, Partners → `/zetapartner`, Support → `/zetasupport`, FAQ → `/faq`, Contact Us → `/zetacontact`, What's New → `/changelog`, Privacy Policy → `/privacy-policy`, Security → `/trust`.
- Empty submit raises six messages and no false success: "Please enter your name.", "Please enter your company name.", "Please enter your email address.", "Please enter your phone number.", "Please enter your message.", "Please complete the required fields."
- Six fields show a `*`: Name, Company Name, Company Email, Country, Phone Number, Tell us what we can do.
- **No checkbox is required.** Submitting with all four unticked produced no complaint about them.
- Country is marked `*` but raises no error, because it ships with a value selected. Correct.
- Invalid email `test@` is correctly refused with "Please enter a valid email address."
- The default-ticked checkbox can be unticked with the Space key, and each of the four can be set independently.
- Switching between Sales, Partner and General by keyboard works; the active tab changes on screen.
- After each send, every field clears on its own.
- **Footer spacing is correct.** At the very bottom the footer occupies y = 339 to 774 and there is **1 px** below it. No extra blank space. The reported fix holds at this window size.
- **No horizontal page scroll.** `document.documentElement.scrollWidth` 1291 equals the viewport width.
- The country chooser lists **15 countries**, and they match the footer region chips and the phone country list **exactly** — nothing in one list is missing from another.
- The country chooser closes with Done; the header still reads India and the stored setting is unchanged at `{"country":"in","lang":"en"}`.
- The counters below the hero read "0+" before they scroll into view and **"2,000+ / 20+ / 25+ / 200,000+"** once visible. A count-up on reveal, not a fault.

---

# 5. CANNOT TELL

**The spacing around "·" in the testimonial by-lines.** The page text reads "Louise Kenna· HR Manager, Honey Gourmet Grocer" with no space before the dot. In the DOM the role is its own `<SPAN>` beginning "· HR Manager…" with **`margin-left: 4px`**, so a 4 px gap exists when it renders. I could not photograph it: the by-line's parent panel measured **`opacity: 0`** on every attempt, so the quote card was faded out and the by-line never appeared on screen.

**Whether the page text wording in that by-line is a real spacing fault.** Follows from the above — the measurement says there is a gap, the screen could not be checked.

**Whether the Mauritius grouping is intended.** Measured as a fact; whether it is wrong is a business decision.

---

# 6. Not checked, and why

| Not checked | Why |
|---|---|
| The five social links in the top strip and six in the footer | Not activated, to avoid sending requests to other companies' servers. Checked by address only. |
| `mailto:sales@zetasoftwares.com` in the footer | Not activated — it would open a mail client. |
| My Portal → Partner | Listed as `/ERPSaasUI/login/partner`. Not reached before the run moved on. |
| The Solution Finder five-question flow | Not run. It is interactive and was outside the time available. |
| The testimonial carousel arrows and avatars | Not activated. |
| Behaviour at other window sizes or at 100% zoom | Everything here is at 1291 × 775 and DPR 1.14 only. |
| Colour contrast and screen-reader output | Not measured. |

---

# 7. One correction to my own reading

Two things I nearly reported were my error, not the site's:

- I read the page text as "ZETASOFTWARE" (one word) and was ready to call it a naming inconsistency. **On screen the wordmark reads "ZETA SOFTWARE"** and the footer line reads "© 2026 Zeta Software Pvt Ltd." Those agree. The page text had joined two styled parts.
- Reading a compressed screenshot, I thought Bahrain was missing from the country chooser. **The DOM shows it is there**, and all three country lists match exactly.

Both are the reason the brief's rule to confirm on screen — and to re-check against the DOM — is worth keeping.
