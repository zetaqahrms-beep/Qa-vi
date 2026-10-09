# Country pages: content, consistency and grammar check (browser extension)

```
You are a senior QA tester and careful proofreader. Check the 15 country pages for
misleading content, inconsistencies and language mistakes. Report what you SEE, with exact
quotes, and confirm each finding on screen (screenshot or zoom).

<site>https://zetahrms-saas.com:8085/ERPSaasUI</site>
Desktop, about 1291 x 775. New tab. Reach each page through the header country chooser
(select the country, press Done). Never type the address.
WAIT about 10 seconds on each page before reading any number: the counters animate.

CONTROL CHECK at the start of each group: open the "What we Offer" menu from the keyboard.
If it does not open, STOP, report "INPUT FAILED", and report nothing from that group as a bug.

Run the 3 groups one after another without waiting. Post each group's report, then continue.
GROUP 1 – UAE, Saudi Arabia, Qatar, Kuwait, Oman, Bahrain
GROUP 2 – India, Sri Lanka, Malaysia, Mauritius, Singapore
GROUP 3 – Kenya, Uganda, Egypt, UK

On EVERY page, read every line from top to bottom (heading, chips, side cards, body text,
"Why Zeta in ..." band, feature cards, buttons, footer) and check:

1. SAME PAGE, SAME FACT: the heading, chips, cards and body name the same schemes, taxes and
   bodies in the same way. Example of a bug already found: Kenya heading says "SHIF", the chip
   and card say "NHIF".
   Also check that "STATUTORY N ready" matches the number of statutory items the page lists.
2. WRONG COUNTRY (copy-paste): any other country's name, currency, city, tax body or
   language on this page.
3. POSSIBLY OUTDATED OR WRONG: a tax, scheme or authority name that may be renamed, replaced
   or incorrect for that country. Report it as NEEDS BUSINESS CONFIRMATION with what is
   shown. Do not state the correct value as fact.
4. POSSIBLY MISLEADING CLAIMS: "Local support: Yes", "a local team in ...", office or city
   claims, language support, "ready" claims. Compare with the rest of the site (the country
   chooser shows "Zeta office" pins only for UAE, Saudi Arabia and India). Report as
   NEEDS BUSINESS CONFIRMATION.
5. LANGUAGE: spelling, grammar, missing or extra words, capitalisation, punctuation,
   apostrophes, and British vs American spelling (the site mostly uses British: "organise").
6. CUT-OFF TEXT: any text clipped by a shape or edge (example already found: Qatar chips show
   "AR" for "QAR" and "TATUTORY"). Check the chips on every page.

Already known, do NOT report again: identical worldwide figures on all country pages
(by design); Kenya "SHIF" vs "NHIF"; Qatar clipped chips (but DO report if other pages
have the same clipping); Egypt languages "EN" (with the business); ZNW-165 (direct address
or refresh shows a blank page).

Rules: no form submissions, no real accounts. No severity, no fixes, no cause guessing.
Do not use "every/all/always" unless you checked every case. CANNOT TELL when unclear.
At the end, set the country back to India and confirm the header reads "India".

Output per group:
1. Summary: X possible bugs, X NEEDS BUSINESS CONFIRMATION, X passed pages.
2. Table: Country | Where on the page | Saw exactly | Type (Same-page mismatch / Wrong country /
   Needs business confirmation / Language / Cut-off)
3. Pages with nothing found: one line each.
At the end: FINAL SUMMARY with all findings in one table.
```
