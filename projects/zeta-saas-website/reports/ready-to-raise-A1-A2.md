# Ready to raise (manually reproduced 2026-10-07)

Before raising: search ZNW for "Manufacture" and "Construction" (duplicates).
New tickets, so raise them as new (team rule: edits for New/Deferred, comments only on Reopened).
Attach the 1280 x 650 screenshot to A2.

## A1: DO NOT RAISE (duplicate of ZNW-178, New, raised 07 Oct 2026 4:46 PM)
Summary: Industry label in the home page hero reads "Manufacture"

STEPS TO REPRODUCE
1. Open https://zetahrms-saas.com:8085/ERPSaasUI/home
2. In the hero section, move the pointer over the orange "Industry" node
3. Read the sector labels around it

ACTUAL RESULT
The labels read "Health", "Education", "Construction" and "Manufacture".
The first three are sector names; "Manufacture" is a verb.

EXPECTED RESULT
The label uses the same word form as the other sector names.

## A2
Summary: "Construction" label in the home page hero is cut off at the right edge at 1280 x 650

STEPS TO REPRODUCE
1. Set the browser viewport to 1280 x 650
   (DevTools > device toolbar > Responsive > 1280 x 650)
2. Open https://zetahrms-saas.com:8085/ERPSaasUI/home
3. In the hero section, move the pointer over the orange "Industry" node
4. Look at the "Construction" label at the top right

ACTUAL RESULT
The label reads "Constructi". The rest of the word is cut off at the right edge of the
page. There is no horizontal scrollbar to reach it.
At a full-screen width (about 1920px) the full word is visible.

EXPECTED RESULT
The full label is visible inside the page at 1280 x 650.

## C1 (Low): STANDALONE, affects BOTH forms (home + /zetacontact). Link ZNW-25 (Closed) with "relates to"; do not touch it.
Summary: Phone number with letters shows the empty-field message on the home page and Contact page forms

STEPS TO REPRODUCE
1. Open https://zetahrms-saas.com:8085/ERPSaasUI/home and scroll to the contact form
2. Fill Name, Company Name, Company Email and the message field
3. Type gfdfg in Phone Number
4. Press Send

ACTUAL RESULT
The form is not submitted. Under Phone Number the message reads
"Please enter your phone number." and above Send it reads
"Please complete the required fields." The Phone Number field shows "gfdfg",
and every required field is filled.
The Contact page form (/zetacontact) accepts the same letters and shows the same
"Please enter your phone number." message.
For comparison, typing test@ in Company Email shows "Please enter a valid email address."

EXPECTED RESULT
The message states that the phone number entered is not valid.


## HOME-FORM: one ticket for fixes missing on the home page form
Before raising: open /zetacontact and confirm each behaviour there once (fixed state).
C5 dropped 2026-10-07: Country has aria-label "Country"; checkboxes are wrapped in <label> (name from label text).

Summary: The home page contact form tabs do not expose the selected state that the Contact page form tabs do

STEPS TO REPRODUCE
1. Open https://zetahrms-saas.com:8085/ERPSaasUI/zetacontact and check the behaviours below
2. Open https://zetahrms-saas.com:8085/ERPSaasUI/home and scroll to "Talk to a Zeta Specialist"
3. Check the same behaviours on the home page form

ACTUAL RESULT
On the home page form:
- The Sales / Partner / General tabs are plain buttons: DevTools Accessibility shows
  "No ARIA attributes", Role: button. The active tab is shown by colour only.
  On /zetacontact the same tabs have role="tab", aria-selected="true"/"false",
  aria-controls="contact-tabpanel", inside role="tablist" aria-label="Enquiry type".
  (Contact page fix: ZNW-161, Closed) [verified manually 2026-10-07, screenshots]
Measured at 1280 x 650.

EXPECTED RESULT
The home page form behaves the same as the Contact page form for each item above.

## D1 (manually checked 2026-10-07 at 1291 x 775)
Summary: The Zenita chat button covers the "Security" link in the home page footer at 1291 x 775

STEPS TO REPRODUCE
1. Set the browser viewport to 1291 x 775
2. Open https://zetahrms-saas.com:8085/ERPSaasUI/home
3. Scroll to the end of the page until the footer is shown
4. Look at the bottom-right links, beside "Privacy Policy"
5. Click the middle of the word "Security"

ACTUAL RESULT
The round Zenita chat button sits on top of the "Security" link and covers part of the word.
Clicking the covered part does not open the Security page; the click goes to the chat button.
The link opens /trust when reached with the keyboard (Tab, then Enter).

EXPECTED RESULT
The "Security" link is fully visible and can be clicked at 1291 x 775.

(Do not add a fix. Attach a screenshot showing the overlap.)
Related: ZNW-115 (Suggestion, Deferred) "Make the AI Chatbot Icon Moveable". Link it with Jira's "relates to" issue link; do not comment on it.

## E1 (manually found 2026-10-07 at 1291 x 775): Solution Finder heading overlaps the left page menu
Related (do not touch, Closed): ZNW-94 "Answering the Solution Finder slides the section 97px
left and the page menu prints on top of the heading" -> link with "relates to".
Difference: E1 happens on arrival, before any answer is chosen.

Summary: The Solution Finder heading overlaps the left page menu on the home page at 1291 x 775

STEPS TO REPRODUCE
1. Set the browser viewport to 1291 x 775
2. Open https://zetahrms-saas.com:8085/ERPSaasUI/home
3. In the left page menu, click "Solution Finder" (or scroll to that section)
4. Do not choose any answer. Look at the left page menu beside the heading

ACTUAL RESULT
The heading "Find your fit in under two minutes" sits on top of the left page menu.
The menu item "Solution Finder" shows as "Solution Fin" and the rest is covered by the
word "under". (Screenshot attached.)

EXPECTED RESULT
The heading and the left page menu do not overlap at 1291 x 775.

---
# Pre-launch retest 2026-10-08: confirmed by tester

## F1: FAQ category chips open the home page (NEW)
Summary: The category links on the FAQ page open the home page instead of the matching FAQ section

STEPS TO REPRODUCE
1. Open https://zetahrms-saas.com:8085/ERPSaasUI/faq
2. Click the category link "Partners" near the top of the page
3. Repeat with "Products", "Deployment" and "Security & compliance"

ACTUAL RESULT
Each click opens the home page (/ERPSaasUI/home). The FAQ page has a section for each
category (Products, Pricing & licensing, Deployment, Implementation & onboarding, Support,
Security & compliance, Partners), but the links do not move to them.

EXPECTED RESULT
Each category link moves to its section on the FAQ page.

## F2: DROPPED 2026-10-09 - India figures were read mid count-up; settled values match home (20+ / 2000+). Country count part still goes to ZNW-77 as an edit.
Summary: The India country page shows different company figures from the home page
Note: the country-count mismatch (banner "16 countries" vs 15 in the chooser) belongs to
ZNW-77 / ZNW-75 (Deferred): add it there as a DESCRIPTION EDIT, not a new ticket.

STEPS TO REPRODUCE
1. Open https://zetahrms-saas.com:8085/ERPSaasUI/home and read the four counters below the hero
2. Open https://zetahrms-saas.com:8085/ERPSaasUI/country/in and read its counters

ACTUAL RESULT
Home page: "2,000+ Companies", "20+ Countries", "25+ Years", "200,000+ Users".
India page: "1998 Established", "7+ Countries served", "656+ Customers worldwide",
"3K+ Core users", "66K+ ESS users".
The India page labels its figures as worldwide ("Customers worldwide").

EXPECTED RESULT
The same facts show the same figures on both pages.

## F3: "What we Offer" menu stays open on Escape and when focus moves away (NEW)
Summary: The "What we Offer" menu does not close with Escape or when the keyboard focus leaves it

STEPS TO REPRODUCE
1. Open https://zetahrms-saas.com:8085/ERPSaasUI/home
2. Press Tab until "What we Offer" is focused, then press Enter (the menu opens)
3. Press Escape
4. Reopen the menu, then press Tab until the focus moves past the menu items

ACTUAL RESULT
After step 3 the menu stays open. After step 4 the menu stays open while the focus is on
the next header item. Pressing Enter on "What we Offer" again closes it.

EXPECTED RESULT
The menu closes when Escape is pressed and when the focus leaves the menu.
Related (Closed, do not touch): ZNW-99, ZNW-91.

## F4: Bahrain is hidden in the country chooser until the list is scrolled (Low, NEW)
Summary: The country chooser shows 14 of 15 countries on open; Bahrain is reached only by scrolling inside the list

STEPS TO REPRODUCE
1. Open https://zetahrms-saas.com:8085/ERPSaasUI/home at 1291 x 775
2. Click "India" in the top bar to open the country chooser
3. Look at the MIDDLE EAST column

ACTUAL RESULT
The column ends at "Oman". "Bahrain" is not visible and there is no sign that the list
scrolls. Scrolling inside the list shows "Bahrain", and the group headings scroll out of view.

EXPECTED RESULT
All 15 countries are visible when the chooser opens, or the list shows that it can be scrolled.

---
# Country pages content check 2026-10-09 (all 15 pages checked)

## K1: Chips cut off on the Qatar and Bahrain country pages
STEPS: Header country chooser -> Qatar -> Done; read the four chips at the top left. Repeat for Bahrain. (1291 x 775)
ACTUAL: Qatar: currency chip shows "AR" (for "QAR") and the label "TATUTORY" (for "STATUTORY").
Bahrain: currency chip shows "3HD" (for "BHD") and the label "ANGUAGES" (for "LANGUAGES"); the "E" of "EN · AR" is partly cut.
The chips on the other 13 country pages render in full.
EXPECTED: The chip text is shown in full on every country page.

## K2: Qatar page spells "Labour Law" two ways
STEPS: Country chooser -> Qatar -> Done; read the hero pill and the compliance tile under "Statutory-ready for Qatar".
ACTUAL: The pill and the tile title read "Qatar Labor Law". The same tile's body reads "Leave, gratuity and contracts per Qatar Labour Law.", the hero line reads "...and Qatar Labour Law." and the card reads "Labour Law aligned".
EXPECTED: The page spells the law's name the same way everywhere.

## K3: Kenya page names the health scheme as "SHIF" and "NHIF"
STEPS: Country chooser -> Kenya -> Done; read the heading, the chips under the buttons and the compliance tile.
ACTUAL: Heading: "Kenya payroll & ERP — KRA PAYE, NSSF and SHIF ready." Chip and tile: "NSSF & NHIF".
The heading names three schemes; the STATUTORY chip reads "2 ready".
EXPECTED: The heading, chip and tile name the same scheme(s), and the count matches.

## K4: UK page drops "the" before "UK"
STEPS: Country chooser -> UK -> Done; read the section labels and headings down the page.
ACTUAL: "WHY ZETA IN UK", "Built for how UK works", "Statutory-ready for UK", "Talk to us in UK", "Ready to run UK on Zeta?"
EXPECTED: The wording reads grammatically for the UK, as it does for other countries (e.g. "Built for how Kenya works").

## Business confirmation list (do not raise yet)
Developer reply 2026-10-09: no offices in those countries, but local PARTNERS provide support -> "Local support: Yes" and UK "London office" are ACCEPTED (dropped). Compliance names: developers will verify updated versions (using Claude) (pending, do not raise).
- Possibly outdated scheme names: Kenya "NHIF", Oman "PASI", Sri Lanka "PAYE", Mauritius "NPF / NSF".
- Saudi card "GOSI + WPS" and Malaysia card "SOCSO & EIS": WPS / EIS are not in the statutory lists.
- "LOCAL SUPPORT: Yes" on 11 countries with no office pin (Qatar, Kuwait, Oman, Bahrain, Sri Lanka, Malaysia, Mauritius, Kenya, Uganda, Egypt, UK).
- UK hero: "From our London office..." - not in the office pins (UAE, Saudi Arabia, India) or the home "Offices UAE · India · Singapore".
- Egypt names no tax authority or scheme (others do).
Dropped: sentence case on cards vs Title Case on tiles (Egypt, UK) - consistent design pattern; "tap any product".
