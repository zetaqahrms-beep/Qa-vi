# Extension gap checks while Claude Code is at its limit (Claude in Chrome)

**Purpose:** use the browser extension until Claude Code resets (16:30 IST): fill the gaps the release record needs, duplicate-search every candidate, and retest Fixed tickets. Read only.
**Run with:** Sonnet (if the extension offers a choice). New tab. Desktop with the side panel open, window about 1291x775.
**After:** paste each part's report into the Qa-vi chat.

## Prompt

```
You are a senior QA tester. Read-only checks on the Zeta SaaS website and its Jira project.
Report only what you SEE, with exact quotes and numbers, and confirm every finding on screen
(zoom screenshot).

<site>https://zetahrms-saas.com:8085/ERPSaasUI</site>
<jira>The Jira tab already open in this browser, project ZNW</jira>

RULES
- At the start, record window.innerWidth x innerHeight and the time.
- JIRA IS READ ONLY: open, search and read tickets only. Never click Edit, Comment, Assign,
  Link, Create, Log work or any status/transition button, and never type into any Jira field
  except the search box. If a dialog opens by accident, press Cancel/Escape and report it.
- Website: never submit a form.
- Inside the website page body use the keyboard (Tab, Enter, Space, PageDown). Mouse clicks
  inside the home page can be swallowed. If a click seems to do nothing, try the keyboard
  once and report both.
- CONTROL CHECK at the start of each part and before any "does nothing" verdict: on the
  website, Tab to "What we Offer" and press Enter. If the menu does not open, wait 5 s and
  try once more. Still not: report "INPUT FAILED" and give no verdicts for that part.
- Country pages: click the country name in the top bar, click the country, click "Done".
  Never type a country address (except check 1.4).
- Wait 25 s on a page before reading any counter.
- Verdicts: REPRODUCES / NOT REPRODUCED / CHANGED / CANNOT TELL / NOT APPLICABLE.
  Never write "fixed". If you check a different element than the one named, the verdict is
  NOT APPLICABLE.
- Run the parts in order. Post each part's report, then continue to the next part without
  waiting. At 16:15 IST, post what you have and stop.

PART 1 - Gap checks (about 30 min)
1.1 ZNW-180: on /home, press PageDown slowly until the Zenita section (the section about the
    Zenita AI assistant) is in view. Wait 10 s. Quote the Zenita speech bubble text exactly.
    Does "Click on me to know more!" appear there? Screenshot.
1.2 K1 - the LEFT TILES, not the chip buttons: on each of the 15 country pages, the hero has
    4 stacked tiles at its left edge, labelled CURRENCY, STATUTORY, LOCAL SUPPORT and
    LANGUAGES, each with a value (e.g. "QAR", "2 ready", "Yes", "EN · AR"). Zoom on them.
    For each tile write the label and the value letter by letter as you SEE them, and mark
    any letter you cannot read. Do not write the text from memory.
1.3 K4: on the UK page, is the text "Zeta in UK — ERP & HRMS software in UK" visible on
    screen anywhere? If yes, where?
1.4 ZNW-165: type https://zetahrms-saas.com:8085/ERPSaasUI/country/ae into the address bar
    and press Enter. Does the page render or stay blank? Screenshot.
Report PART 1 as a table: check | verdict | what you saw | time.

PART 2 - Jira duplicate search (read only)
For each candidate below, search Jira project ZNW with 2-3 keywords (all statuses) and list
any ticket that describes the same problem.
- A2: "Construction" label cut off at the right edge of the home hero (1291x775)
- D1: Zenita chat button covers the footer "Security" link
- E1: Solution Finder heading covers the left page-menu item "Solution Finder"
- F1: FAQ category links open the home page
- F3: "What we Offer" menu does not close on Escape / stays open when focus leaves it
- T1: Tab moves into the hidden "What we Offer" menu items while the menu is closed
- F4: Bahrain hidden in the country chooser until the list is scrolled
- C1: Contact page phone field accepts letters with no message
- K1: Qatar / Bahrain hero tiles: first letters cannot be read
- K2: Qatar page "Labor Law" and "Labour Law"
- N1: sign-in pages tab title is only "Zeta Software" (also read ZNW-169)
Report: candidate | possible duplicate key | its status | same problem? YES / PARTLY / NO.

PART 3 - Retest tickets the developers marked Fixed (read only)
In Jira ZNW, list the tickets with status Fixed (and Resolved / Done / Ready for QA if those
exist). Skip Closed. For each: read its steps, retest on the site, give a verdict with
evidence. Report: key | title | verdict | evidence | time.

PART 4 - If time remains: these open tickets were not checked today. For each, read it in
Jira, retest, and give a verdict: ZNW-189, 192, 193, 194, 195, 196, 197, 198, 199, 175, 77,
141. If a check needs something the browser cannot show (e.g. response headers), write
CANNOT TELL and why.

FINAL: a short summary - what ran, counts per verdict, anything you could not do, and
confirm that nothing was changed in Jira.
```
