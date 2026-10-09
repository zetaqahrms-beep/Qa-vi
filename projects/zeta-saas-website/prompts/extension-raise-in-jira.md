# Raise the verified bugs and edits in Jira (Claude in Chrome)

**Purpose:** duplicate-search, then create the verified tickets and add the "QA re-check" description edits, one at a time with the tester's approval. Screenshots are attached by hand (visual bugs only).
**Run with:** Sonnet. Jira must be open INSIDE the extension's tab group (or paste the URL in <jira>).
**Before pasting:** replace PASTE-JIRA-URL. Do the C1 manual check (Contact > Sales > Phone: type gfdfg, leave the field). If C1 is not confirmed, delete the C1 block.

## Prompt

```
You are a QA tester raising verified bugs in Jira project ZNW for me. You type into my Jira,
so work slowly and only with my approval.

<jira>PASTE-JIRA-URL</jira>
If the line above still says PASTE-JIRA-URL, stop and ask me for the address.

RULES
- One item at a time. Before EVERY Jira write, show me exactly what you will write and wait
  for my reply "approve <item>". No reply, no write.
- Copy the texts below exactly. Do not add a NOTE section, a "Related:" line, links to other
  tickets, a severity, a fix, a cause, or the word "still".
- Never change a ticket's status. Never comment. Never touch Closed tickets.
- Before editing an existing ticket, read its status. New or Deferred: append the text at the
  END of the description, keep the existing text unchanged. Any other status (Reopened,
  Fixed, Closed, In Progress...): do not edit; tell me.
- Do not upload files. After each create or edit, give me the ticket key and wait while I
  attach the screenshot myself.
- If anything unexpected opens (a dialog, a workflow screen), press Cancel and tell me.

STEP 1 - Duplicate search (read only, all statuses). For each NEW ticket below, search with
2-3 keywords and list any ticket that describes the same problem:
item | possible duplicate key | its status | same problem? YES / PARTLY / NO.
Then STOP and wait for my list of items to raise.

STEP 2 - Create the new tickets I approve (Issue type: Bug). Use the Priority I give in the
approval; if I give none, ask.

=== A2 ===
Summary: Home hero: the "Construction" label runs past the right edge of the window at 1291 x 775
STEPS TO REPRODUCE
1. Set the browser window to 1291 x 775
2. Open https://zetahrms-saas.com:8085/ERPSaasUI/home
3. Look at the sector names around "Industry" on the right side of the hero
4. Try to scroll the page sideways
5. Repeat at 1280 x 650
ACTUAL RESULT
At 1291 x 775 the label "Construction" ends up to 20 pixels past the right edge of the
window, so its last letters are not visible. At 1280 x 650 two labels end past the edge:
"Construction" and "Manufacture". The page has no horizontal scrollbar, so the hidden part
cannot be reached. (Screenshot attached.)
EXPECTED RESULT
Every sector label is fully visible at 1291 x 775 and at 1280 x 650.

=== D1 ===
Summary: The Zenita chat button covers the footer "Security" link at 1291 x 775
STEPS TO REPRODUCE
1. Set the browser window to 1291 x 775
2. Open https://zetahrms-saas.com:8085/ERPSaasUI/home
3. Scroll to the footer
4. Click the "Security" link
5. Repeat steps 3-4 on https://zetahrms-saas.com:8085/ERPSaasUI/zetapartner
ACTUAL RESULT
The Zenita chat button sits on top of the "Security" link. Clicking the link opens the Zenita
chat instead; the address stays /ERPSaasUI/home and the Security & Trust page does not open.
On the Partner page the button covers most of the link. (Screenshot attached.)
EXPECTED RESULT
The "Security" link is fully visible and opens the Security & Trust page.

=== E1 ===
Summary: The Solution Finder heading covers the left page-menu item "Solution Finder" at 1291 x 775
STEPS TO REPRODUCE
1. Set the browser window to 1291 x 775
2. Open https://zetahrms-saas.com:8085/ERPSaasUI/home
3. In the left page menu, click "Solution Finder" (or scroll to that section)
4. Look at the left page menu beside the heading
ACTUAL RESULT
The heading "Find your fit in under two minutes" overlaps the left page menu. The menu item
"Solution Finder" shows as "Solution Fin" and the rest is covered by the word "under".
(Screenshot attached.)
EXPECTED RESULT
The heading and the left page menu do not overlap at 1291 x 775.

=== F1 ===
Summary: The category links on the FAQ page open the home page instead of the matching FAQ section
STEPS TO REPRODUCE
1. Open https://zetahrms-saas.com:8085/ERPSaasUI/faq
2. Click the category link "Products" near the top of the page
3. Go back to the FAQ page and repeat with the other six category links
ACTUAL RESULT
Each of the seven links (Products, Pricing & licensing, Deployment, Implementation &
onboarding, Support, Security & compliance, Partners) opens the home page
(/ERPSaasUI/home#products and so on) at the top of the page. The FAQ page has a section for
each of these categories, but the links do not move to them.
EXPECTED RESULT
Each category link moves to its section on the FAQ page.

=== F3 ===
Summary: The "What we Offer" menu does not close with Escape or when keyboard focus leaves it
STEPS TO REPRODUCE
1. Open https://zetahrms-saas.com:8085/ERPSaasUI/home
2. Press Tab until "What we Offer" is focused, then press Enter (the menu opens)
3. Press Escape
4. Press Tab five times, past the last menu item "Industries", until "Zenita" in the header
   is focused
ACTUAL RESULT
After step 3 the menu stays open (Escape pressed twice). After step 4 the focus is on
"Zenita", but the menu is still open over the page. Escape also does not close the menu when
it is opened by moving the mouse over "What we Offer". (Screenshot attached.)
EXPECTED RESULT
The menu closes when Escape is pressed and when the focus leaves the menu.

=== F4 ===  (Priority: Low)
Summary: The country chooser hides Bahrain until the list is scrolled
STEPS TO REPRODUCE
1. Set the browser window to 1291 x 775
2. Open https://zetahrms-saas.com:8085/ERPSaasUI/home
3. Click "India" in the top bar to open the country chooser
4. Look at the MIDDLE EAST column
ACTUAL RESULT
The column ends at "Oman". "Bahrain" is below the visible part of the list and nothing shows
that the list can be scrolled. Scrolling inside the list shows "Bahrain". 14 of the 15
countries are visible when the chooser opens. (Screenshot attached.)
EXPECTED RESULT
All 15 countries are visible when the chooser opens, or the list shows that it can be scrolled.

=== K1 ===
Summary: Qatar and Bahrain pages: the first letters of the hero tiles cannot be read
STEPS TO REPRODUCE
1. Set the browser window to 1291 x 775
2. Click the country name in the top bar, choose Qatar, click Done
3. Read the four tiles at the left edge of the hero (Currency, Statutory, Local support,
   Languages)
4. Repeat for Bahrain
ACTUAL RESULT
The white zig-zag shape at the left edge of the hero covers the start of the tile text.
Qatar: the currency "QAR" reads as "AR", the label "STATUTORY" as "ATUTORY" and "LANGUAGES"
as "ANGUAGES". Bahrain: "LANGUAGES" reads as "NGUAGES", and the "B" of "BHD" is partly
covered, so it reads like "3HD". The tiles on the other 13 country pages read in full.
(Screenshots attached.)
EXPECTED RESULT
The tile text is shown in full on every country page.

=== K2 ===
Summary: The Qatar page spells the law's name both "Labor" and "Labour"
STEPS TO REPRODUCE
1. Click the country name in the top bar, choose Qatar, click Done
2. Read the chips in the hero and the section "Statutory-ready for Qatar"
ACTUAL RESULT
"Qatar Labor Law" appears in the hero chip and in the title of a card under
"Statutory-ready for Qatar". The same card's text reads "Leave, gratuity and contracts per
Qatar Labour Law." "Labour" is also used in the hero text and in the card "Labour Law
aligned". The page uses "Labor" twice and "Labour" four times.
EXPECTED RESULT
The page uses one spelling of the law's name throughout.

=== C1 ===  (Priority: Low)  [only if I confirmed it by hand]
Summary: The Contact page accepts letters in the Phone field and shows no message
STEPS TO REPRODUCE
1. Open https://zetahrms-saas.com:8085/ERPSaasUI/zetacontact and stay on the Sales tab
2. Type gfdfg in the Phone field
3. Click another field
ACTUAL RESULT
The Phone field keeps "gfdfg". No message appears on the page.
EXPECTED RESULT
The Phone field does not accept letters, or a message is shown at the field.

STEP 3 - Description edits on existing tickets (append at the end; status rules above).
Start each with a blank line, then the text exactly:

ZNW-165:  QA re-check 9 Oct 2026 (build main-AJ2WBBZY): not reproduced. Typed full loads of
  /ERPSaasUI/country/ae, /ERPSaasUI/country/qa and /ERPSaasUI/login/partner all showed the
  page (15:57-16:19 IST). No blank page.
ZNW-200:  QA re-check 9 Oct 2026 (build main-AJ2WBBZY): the closing headline on all 15 country
  pages now reads "Ready to run Zeta?" (no country name). On the UK page these four headings
  use "UK" without "the": "Why Zeta in UK", "Built for how UK works", "Statutory-ready for UK",
  "Talk to us in UK".
ZNW-77:   QA re-check 9 Oct 2026 (build main-AJ2WBBZY): the country chooser lists 15 countries;
  the top banner reads "Localized for 16 countries & currencies".
ZNW-166 and ZNW-182 (same text):  QA re-check 9 Oct 2026 (build main-AJ2WBBZY): not applicable.
  The home page no longer has a contact form (no form and no input fields); it shows
  "Contact Us" and "Email Sales" links instead. The form was removed by design (team lead,
  8 Oct 2026).
ZNW-186:  QA re-check 9 Oct 2026: out of QA scope. This is phone resolution; QA tests desktop
  only since 7 Oct 2026.
ZNW-188:  QA re-check 9 Oct 2026: by design (team lead, 8 Oct 2026). /pricing opens the
  Contact page on purpose.
ZNW-190:  QA re-check 9 Oct 2026 (build main-AJ2WBBZY): not reproduced. Loading
  /ERPSaasUI/home made no request for /favicon.ico and showed no console error. The page
  uses assets/favicon.ico, which loads (HTTP 200).
ZNW-191:  QA re-check 9 Oct 2026 (build main-AJ2WBBZY): not reproduced. On /ERPSaasUI/home
  every button has an accessible name, including each Solution Finder quiz step and the
  review arrows ("Previous reviews", "Next reviews").
ZNW-187:  QA re-check 9 Oct 2026: reproduces. The first call to /ERPSaasUIBackend/health
  after a long idle time took 1.245 s; the next two calls took 0.048 s and 0.079 s.

FINAL: list every ticket created (key + summary) and every ticket edited, and confirm that no
status was changed and no comment was added.
```

## Screenshots to attach by hand (visual bugs only, 1 each, cropped)
| Ticket | File |
|---|---|
| A2 | A2-construction-clip-1291.png |
| D1 | D1-home-click-opens-zenita.jpg |
| E1 | E1-solution-finder-overlap-1291.png (or the tester's 12:22 screenshot, cropped) |
| F3 | F3-escape-does-not-close.png |
| F4 | F4-middle-east-ends-at-oman.png |
| K1 | tester's Qatar tiles + Bahrain tiles screenshots |
No screenshots for F1, K2, C1 and the description edits (text is enough).

## Held back (not in this prompt)
- T1 (Tab enters hidden menu items) and N1 (sign-in tab titles): wait for the lead's decision.
- ZNW-177 (SEC-012 body), ZNW-141/149/155: need Claude Code (test fix, earlier drafts).

## Changelog
- 2026-10-09: first version (final texts assembled from the post-update runs)
