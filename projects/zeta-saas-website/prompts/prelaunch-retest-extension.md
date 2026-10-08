# Pre-launch retest (browser extension)

**Purpose:** After the QA build update, retest open visual/content tickets, then sweep all pages for new bugs.
**Used by:** Claude in the browser extension. Run one PART per message; paste results to the Qa-vi chat.

## Prompt

```
You are a senior QA tester. The website was just updated for QA before launch.
Report only what you SEE, with exact quotes and numbers. Confirm every finding on screen
(screenshot), not from page text alone.

<site>https://zetahrms-saas.com:8085/ERPSaasUI</site>

Setup: open a NEW tab. Desktop only. Record the viewport size at the start
(use 1291 x 775; for layout checks also 1280 x 650).
Inside the page body, use the keyboard (Tab, Space, Enter) instead of mouse clicks.
If a click seems to do nothing, try the keyboard once and report both.

Do ONE part per run. Report, then wait for "next".

PART 1 – Retest open tickets. For each, follow its steps and report
REPRODUCES / DOES NOT REPRODUCE / CANNOT TELL, with exact evidence:
- ZNW-166 home contact form: press Send with all fields empty; is Send pushed under the footer? (1291 x 775)
- ZNW-169 home tab title: does it say "Zeta Softwares"?
- ZNW-171 header: "What we Offer" capitalisation
- ZNW-172 Products page: after clicking a category card, can you get back to the top?
- ZNW-178 / ZNW-179 / ZNW-184 home hero labels around "Industry" (hover): quote all labels
- ZNW-180 Zenita speech bubble text on home: quote it
- ZNW-181 "Run Live In 30 Minutes" capitalisation
- ZNW-182 Send button label: home form vs Contact page form
- ZNW-183 "Asia Pacific" vs "APAC": list where each appears
- ZNW-185 "on-premise" vs "On-Premise" on home: list each occurrence
- NEW-A2 home hero, hover "Industry" at 1280 x 650: is "Construction" cut off at the right edge?
- NEW-D1 home footer at 1291 x 775: does the Zenita button cover the "Security" link?
- NEW-E1 home "Solution Finder" section at 1291 x 775: does the heading cover the left page menu?

PART 2 – Home page (all sections, top menu, left page menu, footer)
PART 3 – Products and the product pages
PART 4 – Industries, Software Development, Business Consultancy
PART 5 – Zenita, Partner, Support, FAQ, What's New, Privacy Policy, Security (/trust)
PART 6 – Contact page: all 4 tabs (Sales, Partner, General, Help Desk)
PART 7 – Free Consultation popup, country chooser (set it back to India afterwards), My Portal pages

For PARTS 2–7, on every page check:
1. Address, tab title, main heading (quote).
2. Read every line of text: spelling, grammar, company name, consistent wording.
3. Every link and button: where it goes.
4. Layout: overlaps, cut-off text, misalignment, extra blank space. Give viewport and
   pointer position. Give pixel sizes only if measured, else "approx., not measured".
5. Images: broken or missing.
6. Forms: submit empty, then invalid values ("gfdfg" in phone, "test@" in email),
   quote every message. Valid submissions allowed ONCE per form/tab with:
   Name "QA TEST - please ignore", Company "QA TEST", Email zeta.qa.hrms+saas@gmail.com,
   Phone a valid-length number, Message "QA TEST - <form> - <tab> - <time> - please ignore".
   Record form, tab, time and the exact success message.

Known open issues, do NOT report again: ZNW-165 (blank page on direct links/refresh of
2-part addresses), ZNW-155 (unknown address returns a normal page), ZNW-175/176/177/149
(security), ZNW-141 (no skip link), ZNW-167, ZNW-168, ZNW-170, ZNW-173, ZNW-186 (phone only),
missing footer on pages other than home/support/partner/contact (by design),
Zenita "Hi!" greeting animation in the header.

Rules: no sign-in with real accounts, no scanners or attack payloads, no rapid repeated
requests. No severity, no fixes, no cause guessing. Do not use "every/all/always" unless
you checked every case. CANNOT TELL when evidence is unclear.

Output per part:
1. Summary: X possible bugs, X passed, X CANNOT TELL (PART 1: X reproduce, X do not).
2. Table or blocks: Page | Steps | Saw (exact) | Viewport/pointer
3. Form submissions table (if any)
4. Passed: one line each
5. Not checked, and why
```

## Changelog
- 2026-10-08: first version (pre-launch, after QA build update)
