# Raise in Jira - final combined prompt (SaaS Claude Code)

**Purpose:** one self-contained prompt: final texts N1-N9 + 14 edits (with the tester's changes) + approval. Supersedes claude-code-raise-in-jira.md.
**Run with:** Sonnet, High. Fresh session in the SaaS project (works in the old session too).

## Prompt

```
You are a QA tester raising verified bugs in Jira project ZNW (Zeta SaaS website) with your
Jira tool. Every ticket text below is FINAL and was verified on build main-AJ2WBBZY on
9 Oct 2026. Do not re-measure the site. Copy the texts exactly.
This message is my approval, with the changes already applied. Do these in order.

RULES
- Ticket bodies contain ONLY: STEPS TO REPRODUCE / ACTUAL RESULT / EXPECTED RESULT.
  No NOTE section, no "Related:" line, no links to other tickets, no severity, no fix,
  no cause, never "still". Check every text before writing it.
- No status changes. No comments. No Jira "relates to" links. Never touch Closed tickets.
- Edits are APPEND ONLY: read the ticket's status first. New or Deferred: add the text at the
  end of ACTUAL RESULT (before EXPECTED RESULT if the ticket has one, otherwise at the end),
  keep every existing word unchanged. Any other status: do not edit; tell me.
- Do not remove anyone else's NOTE or "Related:" lines.
- Never print credentials. Do not push.

STEP 1 - Checks (read only).
a. Check the main JS file name on /ERPSaasUI/home. If it is no longer main-AJ2WBBZY, STOP
   and tell me.
b. Fresh duplicate search: ZNW tickets created or updated today, all statuses, against
   N1-N9 below. If any describes the same problem, STOP and show me before raising
   anything. Otherwise continue without waiting.

STEP 2 - Raise N1-N9 (Issue type: Bug, Priority as given, Module if the field exists).

=== N1 === Priority: Medium. Module: Home
Summary: Home hero: the "Construction" sector label extends past the right edge of the window
STEPS TO REPRODUCE
1. Open the home page at a viewport of 1291x775
2. Look at the sector labels in the hero, to the right of the heading
3. Read the label furthest to the right
4. Try to scroll the page sideways
5. Repeat at a viewport of 1280x650
ACTUAL RESULT
At 1291x775 the label "Construction" starts at x=1222 and ends at x=1311. The window is 1291
wide, so 20 pixels of the label are outside it.
At 1280x650 two labels end outside the window: "Construction" at x=1306 and "Manufacture" at
x=1281, against a window 1280 wide.
The page cannot be scrolled sideways: document.body.scrollWidth equals
document.body.clientWidth at both sizes.
At 1291x775 the other nine labels end inside the window. At 1280x650 the other eight do.
Observed on zetahrms-saas.com:8085, build main-AJ2WBBZY, 9 October 2026.
EXPECTED RESULT
Every sector label is fully inside the window at both viewports.

=== N2 === Priority: Medium. Module: Footer
Summary: The footer "Security" link sits under the Zenita launcher, and clicking it does not open the Trust page
STEPS TO REPRODUCE
1. Open the home page at a viewport of 1291x775
2. Scroll to the foot of the page
3. Find the "Security" link in the footer
4. Click the middle of the link
5. Read the address bar
6. Repeat on the Partner page
ACTUAL RESULT
The "Security" link points to /ERPSaasUI/trust and is drawn at left 1210, top 746, right 1254,
bottom 763.
Asking the browser which element is at the left edge, the middle and the right edge of the
link returns "span.zbot-pulse" at all three points on the home page. On the Partner page it
returns "div.zbot-root" at the left edge and "span.zbot-pulse" at the middle and the right
edge.
A mouse click at the middle of the link (1232, 755 on the home page; 1232, 754 on the Partner
page) left the address on /ERPSaasUI/home and on /ERPSaasUI/zetapartner. The Trust page did
not open.
Observed on zetahrms-saas.com:8085, build main-AJ2WBBZY, 9 October 2026, at a viewport of
1291x775.
EXPECTED RESULT
Clicking the "Security" link opens the Trust page.

=== N3 === Priority: Medium. Module: Home
Summary: Solution Finder: the left menu item and the section heading overlap
STEPS TO REPRODUCE
1. Open the home page at a viewport of 1291x775
2. Click "Solution Finder" in the menu on the left of the page
3. Wait until the page stops moving
4. Look at the menu item and at the heading "Find your fit in under two minutes"
ACTUAL RESULT
The page stops with the Solution Finder section in view.
The text of the "Solution Finder" menu item spans x=32 to x=121 and y=362 to y=378. The
heading (h2) spans x=102 to x=528 and y=292 to y=382. The two overlap by 19 pixels
horizontally, and the menu text lies inside the heading's vertical range.
Asking the browser what sits at the left, the middle and the right of the menu item returns
the menu button itself at all three points.
Manually confirmed by the tester, 9 October 2026: the menu item reads "Solution Find" beside
the heading.
Observed on zetahrms-saas.com:8085, build main-AJ2WBBZY, 9 October 2026, at a viewport of
1291x775.
EXPECTED RESULT
The menu item text and the heading do not overlap.

=== N4 === Priority: Low. Module: Header
Summary: The country chooser shows 14 of its 15 countries when opened; Bahrain is only reachable by scrolling inside the list
STEPS TO REPRODUCE
1. Open the home page at a viewport of 1291x775
2. Click the country name in the top bar
3. Count the countries fully visible in the panel
4. Look for Bahrain
5. Scroll inside the country list
ACTUAL RESULT
The panel lists 15 countries. Fourteen are fully visible when it opens. Bahrain is not: its
row starts at y=677, below the list area, which is 218 pixels high and holds 265 pixels of
content (scrollTop 0).
Bahrain appears after scrolling inside the list.
Manually confirmed by the tester, 9 October 2026: nothing on screen shows that the list
scrolls.
Observed on zetahrms-saas.com:8085, build main-AJ2WBBZY, 9 October 2026, at a viewport of
1291x775.
EXPECTED RESULT
All countries in the list can be seen when the panel opens.

=== N5 === Priority: Low. Module: Contact
Summary: The Contact form accepts letters in the Phone field and shows no message
STEPS TO REPRODUCE
1. Click Contact in the header and stay on the Sales tab
2. Click into the Phone field
3. Type gfdfg
4. Click into another field so Phone loses focus
5. Look for a message on the page
6. Type 1 in the Phone field instead, click into another field, and look again
ACTUAL RESULT
With gfdfg, the field keeps the value. No message appears anywhere on the page: a search of
the page text for sentences beginning "Please" returns nothing.
With 1, the message "Please enter a valid phone number." appears.
Observed on zetahrms-saas.com:8085, build main-AJ2WBBZY, 9 October 2026, at a viewport of
1291x775.
EXPECTED RESULT
A value containing letters is refused, with a message shown for the Phone field.

=== N6 === Priority: Medium. Module: FAQ
Summary: None of the seven FAQ category links reaches its section; all seven open the home page
STEPS TO REPRODUCE
1. Open the FAQ page
2. Click the first category link
3. Read the address bar
4. Return to the FAQ page and repeat for each of the other six links
ACTUAL RESULT
All seven links leave the FAQ page and land on the home page:
  #products       -> /ERPSaasUI/home#products
  #pricing        -> /ERPSaasUI/home#pricing
  #deployment     -> /ERPSaasUI/home#deployment
  #implementation -> /ERPSaasUI/home#implementation
  #support        -> /ERPSaasUI/home#support
  #security       -> /ERPSaasUI/home#security
  #partners       -> /ERPSaasUI/home#partners
Each link was clicked once, from a freshly loaded FAQ page.
Observed on zetahrms-saas.com:8085, build main-AJ2WBBZY, 9 October 2026, at a viewport of
1291x775.
EXPECTED RESULT
Each category link moves to its section on the FAQ page, and the address stays on the FAQ
page.

=== N7 === Priority: Medium. Module: Country pages
Summary: Qatar and Bahrain pages: the first letters of the hero tiles cannot be read
STEPS TO REPRODUCE
1. Open the home page at a viewport of 1291x775
2. Click the country name in the top bar, choose Qatar, and click Done
3. Look at the four tiles at the left of the page: Currency, Statutory, Local support,
   Languages
4. Read the first letters of each label and value
5. Repeat with Bahrain
ACTUAL RESULT
On the Qatar page the start of three tile texts cannot be read: "QAR" reads as "AR",
"STATUTORY" as "ATUTORY" and "LANGUAGES" as "ANGUAGES".
On the Bahrain page "BHD" reads as "3HD" and "LANGUAGES" as "NGUAGES".
A white zig-zag shape is drawn at the left edge of the tile column on both pages. The tiles
on the other 13 country pages read in full.
Screenshots attached.
Observed on zetahrms-saas.com:8085, build main-AJ2WBBZY, 9 October 2026, at a viewport of
1291x775.
EXPECTED RESULT
Every tile label and value can be read in full.

=== N8 === Priority: Low. Module: Country pages
Summary: The Qatar page spells the same law "Labor" in two places and "Labour" in four
STEPS TO REPRODUCE
1. Open the home page at a viewport of 1291x775
2. Click the country name in the top bar, choose Qatar, and click Done
3. Read every mention of the law, from the top of the page to the compliance cards
ACTUAL RESULT
Six mentions, in page order:
  Hero paragraph:        "...aligned to the Wage Protection System and Qatar Labour Law."
  Hero pill:             "Qatar Labor Law"
  Tile title:            "Labour Law aligned"
  Tile text:             "Leave, end-of-service gratuity and contracts follow Qatar Labour Law."
  Compliance card title: "Qatar Labor Law"
  Compliance card text:  "Leave, gratuity and contracts per Qatar Labour Law."
Two use "Labor" and four use "Labour".
Observed on zetahrms-saas.com:8085, build main-AJ2WBBZY, 9 October 2026, at a viewport of
1291x775.
EXPECTED RESULT
One spelling is used for the law throughout the page.

=== N9 === Priority: Medium. Module: Header
Summary: The "What we Offer" menu does not close with Escape or when keyboard focus leaves it
STEPS TO REPRODUCE
1. Open the home page at a viewport of 1291x775
2. Move the mouse pointer onto "What we Offer" in the header so that the menu opens
3. Press Escape and look at the menu
4. Reload the page, press Tab until "What we Offer" is focused (11 presses from a fresh
   load), and press Enter so that the menu opens
5. Press Escape and look at the menu
6. Reload the page, open the menu with Tab and Enter as in step 4, then press Tab five
   times, past "Industries", until "Zenita" is focused
ACTUAL RESULT
After the pointer opens the menu, Escape leaves it open: the button reports aria-expanded
"true" and the "Industries" item receives the pointer.
After Enter opens the menu from the keyboard, Escape leaves it open in the same way.
After step 6 the focus is on "Zenita" and the menu is still open.
Moving the pointer away closes the menu in the first case. Pressing Enter a second time
closes it in the second case.
Observed on zetahrms-saas.com:8085, build main-AJ2WBBZY, 9 October 2026, at a viewport of
1291x775.
EXPECTED RESULT
The "What we Offer" menu closes when Escape is pressed and when the keyboard focus leaves it.

N10 (Tab through hidden menu links) stays HELD - do not raise it.

STEP 3 - Description edits (append only, status rules above). Add each text exactly.

Edit 1 - ZNW-77:
QA re-check 9 October 2026, build main-AJ2WBBZY, viewport 1291x775: the country chooser lists
15 countries (07:57 UTC). The top banner, which rotates, reads "Localized for 16 countries &
currencies" (07:55 UTC). The 15 country pages read "Join 2,000+ businesses across 20+
countries." (07:58 to 08:07 UTC).

Edit 2 - ZNW-141:
QA re-check 9 October 2026, build main-AJ2WBBZY, 11:05 UTC, viewport 1291x775. On a fresh
home page, with nothing clicked, Tab was pressed five times. The focused element after each
press: link "Zeta on Facebook", "Zeta on LinkedIn", "Zeta on X", "Zeta on Instagram", "Zeta
on Threads". No link with the text "Skip to content" or "Skip to main content" and no link to
#main or #content was found in the page.

Edit 3 - ZNW-149 (do not change the existing text):
QA re-check 9 October 2026, build main-AJ2WBBZY, 11:16 UTC, /ERPSaasUI/home: the report-only
policy includes script-src 'self' 'unsafe-inline' https://cdn.jsdelivr.net and style-src
'self' 'unsafe-inline' https://fonts.googleapis.com. No enforcing Content-Security-Policy
header is sent.

Edit 4 - ZNW-155 (no rewrite):
QA re-check 9 October 2026, build main-AJ2WBBZY, 11:09 UTC: /this-page-does-not-exist,
/products/invented-thing and /zz-not-a-page-123 each show the heading "This page can't be
found" and the tab title "Page not found | Zeta Software"; the typed address stays in the
address bar. Each answers HTTP 200.

Edit 5 - ZNW-165:
QA re-check 9 October 2026, build main-AJ2WBBZY, 11:06 UTC, viewport 1291x775. 29 addresses
were opened directly, one load each: the 15 country pages (/country/ae to /country/uk), the 8
industry pages (/for/education to /for/field-service-management), /login/customer,
/login/partner, and /products/, /crm/, /trust/ and /zetacontact/ with a trailing slash. All 29
rendered page content, between 546 and 5,611 characters of text. F5 on /country/qa reloaded
the page (2,961 characters before, 2,957 after). The browser console reported no error on
/country/ae, /login/customer, /login/partner or /products/crm.

Edit 6 - ZNW-166:
QA re-check 9 October 2026, build main-AJ2WBBZY, 08:07 UTC, viewport 1291x775. After
scrolling the whole home page, the page has 0 form elements, 0 email inputs, 0 text areas and
no button whose label starts with "Send". The form was removed by design (decision recorded
9 October 2026).

Edit 7 - ZNW-177:
Request body sent by the guard test: {not valid json (15 bytes, sent as raw bytes with
Content-Type: application/json). Response errors[] entry: 'n' is an invalid start of a
property name. Expected a '"'. Path: $ | LineNumber: 0 | BytePositionInLine: 1. The response
status was 400 and the message was "Please check the form and try again." Measured 9 October
2026, 11:02 UTC, build main-AJ2WBBZY.

Edit 8 - ZNW-182:
QA re-check 9 October 2026, build main-AJ2WBBZY, 08:07 UTC, viewport 1291x775. After
scrolling the whole home page, the page has 0 form elements, 0 email inputs, 0 text areas and
no button whose label starts with "Send". The text "Talk to a Zeta Specialist" is not in the
page. The form was removed by design (decision recorded 9 October 2026).

Edit 9 - ZNW-186:
QA re-check 9 October 2026: out of QA scope: phone resolution (desktop only since 7 October
2026).

Edit 10 - ZNW-187:
QA re-check 9 October 2026, 06:12 UTC: after about 45 hours with no request from QA,
/ERPSaasUIBackend/health answered the first call in 1.245 s. The next two calls answered in
0.048 s and 0.079 s.

Edit 11 - ZNW-188:
QA re-check 9 October 2026: confirmed by design by the team lead on 8 October 2026. The route
table redirects /pricing to the Contact page intentionally.

Edit 12 - ZNW-190:
QA re-check 9 October 2026, build main-AJ2WBBZY, 11:13 UTC, viewport 1291x775: loading
/ERPSaasUI/home produced no request for /favicon.ico and no console error. The page declares
<link rel="icon" type="image/x-icon" href="assets/favicon.ico">, and that file answers 200
with Content-Type image/x-icon and Content-Length 8264. A direct request for /favicon.ico at
the site root answers 404 Not Found (06:12 UTC).

Edit 13 - ZNW-191:
QA re-check 9 October 2026, build main-AJ2WBBZY, viewport 1291x775. On the home page after
scrolling the whole page, 26 buttons were present and all 26 carry an accessible name. The
review arrows carry aria-label "Previous reviews" and "Next reviews". The reviewer buttons are
named "LK", "NI", "NF" (from their text) and "Anil Kumar" (from the image alt). The Solution
Finder quiz was answered step by step: at each of its six steps every button carries a name
from its text, and the last step offers "Free consultation" and "Start over".

Edit 14 - ZNW-200:
QA re-check 9 October 2026, build main-AJ2WBBZY, 07:58 to 08:07 UTC, viewport 1291x775. On
each of the 15 country pages the closing headline reads "Ready to run Zeta?", with "Join
2,000+ businesses across 20+ countries. Compliant, connected and supported locally." beneath
it.
On the UK page four more headings are written without "the" before "UK": "WHY ZETA IN UK",
"Built for how UK works", "Statutory-ready for UK", "Talk to us in UK".

STEP 4 - Screenshots (one per visual bug). Use the first file that exists:
N1: test-results/ or docs/retest-2026-10-09/A2-construction-clip-1291.png
N2: docs/retest-2026-10-09/D1-home-click-opens-zenita.jpg
N3: test-results/post-e1-arrival.png or docs/retest-2026-10-09/E1-solution-finder-overlap-1291.png
N4: test-results/post-chooser-open.png or docs/retest-2026-10-09/F4-middle-east-ends-at-oman.png
N9: docs/retest-2026-10-09/F3-escape-does-not-close.png
N7: I attach my own screenshots by hand.
If your Jira tool cannot attach files, or a file is missing, list it and I will add it by
hand. No screenshots for N5, N6, N8 or the edits.

STEP 5 - No guard tests now. FINAL report: every key created (with its N number and
summary), every ticket edited, every edit skipped and why, attachments done or still to add.
Confirm that no status was changed and no comment was added. Do not push.
```

## Changelog
- 2026-10-09: first version (combines the final texts and the tester's approval with changes)
