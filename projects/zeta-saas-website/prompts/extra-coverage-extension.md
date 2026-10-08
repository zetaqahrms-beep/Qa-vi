# Extra coverage run (browser extension), 2026-10-08

Covers areas NOT tested in the pre-launch retest: sign-in pages, country pages,
product detail pages, industry detail pages, Zenita chat.

```
You are a senior QA tester. Test only the parts below. Report what you SEE, with exact
quotes and numbers, and confirm each finding on screen (screenshot).

<site>https://zetahrms-saas.com:8085/ERPSaasUI</site>
Desktop only, about 1291 x 775. Record the viewport at the start. New tab.
Inside the page body use the keyboard (Tab, Space, Enter); if that fails, try the mouse once.

CONTROL CHECK at the start of EVERY part: open the "What we Offer" menu from the keyboard.
If it does not open, your input has stopped working: STOP, report "INPUT FAILED", and do not
report anything from that part as a bug.

Run PART A to PART E one after another without waiting. Post each part's report, then continue.

PART A – Sign-in pages (dummy, not connected yet): /login/customer and /login/partner
Reach them from the header "My Portal" menu (not by typing the address).
Use made-up values only, never saved or real accounts.
Check: mandatory markers (*) on each field; message for empty submit; invalid email format
("test@"); spaces only; a very long value (200 characters); password field hides the text;
"Forgot password" or similar links and where they go; tab title and heading.
Do NOT report "login does not work" — the page is not connected yet.

PART B – Country pages: open the header country chooser and select each country in turn
(UAE, Saudi Arabia, Qatar, Kuwait, Oman, Bahrain, India, Sri Lanka, Malaysia, Mauritius,
Singapore, Kenya, Uganda, Egypt, UK). For each: tab title, main heading, dialling code shown,
phone numbers and address shown, every figure (customers, countries, users, years), and
whether text mentions the right country. At the end set the country back to India.
Report figures as a table: Country | each figure exactly as shown.

PART C – Product detail pages: from /products open each of the 21 products.
For each: tab title, heading, module count vs the "N MODULES" on its card, links/buttons
and where they go, spelling, broken images.

PART D – Industry detail pages: from /industries open each of the 8 "Explore ..." links.
Same checks as PART C.

PART E – Zenita chat (the round button bottom right): ask these 5 questions, one at a time,
and quote each answer exactly:
1. "What products does Zeta offer?"
2. "Do you have offices in India?"
3. "How much does HRMS cost?"
4. "What is the weather today?"
5. "Can I talk to sales?"
Report: answer text, whether it stays on Zeta topics, any wrong or made-up facts
(compare with what the site pages say), and any link it gives and where it goes.

Known issues, do NOT report: ZNW-165 (blank page when a 2-part address is typed or refreshed),
ZNW-155, ZNW-175/176/177/149, ZNW-141, ZNW-167, ZNW-168, ZNW-170, ZNW-173, ZNW-178/179/184,
ZNW-169, ZNW-171, ZNW-181, ZNW-183, ZNW-185, ZNW-75/77/78 (country counts), ZNW-156 (Zenita
keyword answers), Zenita launcher over the footer "Security" link, the "Hi!" header animation,
missing footer except on home/support/partner/contact.
By design, do NOT report: home page has no contact form; /pricing opens Contact; the
Free Consultation popup defaults to UAE.

Rules: no real accounts, no scanners, no attack payloads, no rapid repeated requests, no form
submissions in this run. No severity, no fixes, no cause guessing. Do not use "every/all/always"
unless you checked every case. CANNOT TELL when unclear. NEEDS MANUAL CHECK when a click fails
with both keyboard and mouse. If an element no longer exists, report NOT APPLICABLE.

Output per part: Summary (possible bugs / passed / CANNOT TELL / NEEDS MANUAL CHECK),
possible bugs (Page | Steps | Saw exactly), passed (one line each), not checked and why.
At the end: FINAL SUMMARY with all possible bugs in one table.
```
