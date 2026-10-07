# Manual verification: home page retest findings (2026-10-07)

Site: https://zetahrms-saas.com:8085/ERPSaasUI/home

## Setup (do once): desktop only
1. Open Edge on your desktop as normal, with the Claude side panel OPEN.
   (That is the window size the AI used: 1291 x 775. No phone or device mode needed.)
2. Open the home page in a new tab.
Note: A2 and D1 depend on the window width. If you test with the side panel closed (wider
window) and they do not appear, open the side panel and check again. Record the width you used.

---

## A1: Industry label reads "Manufacture"
STEPS TO REPRODUCE
1. Open the home page.
2. In the top section (hero), move the mouse over the orange "Industry" circle.
3. Read the five labels that appear.

ACTUAL RESULT
The labels read: Health, Education, Construction, Manufacture, Industry.

EXPECTED RESULT
All labels use the same word form as the other sector names.

Result: [ ] Reproduced  [ ] Not reproduced

---

## A2: "Construction" label is cut off at the right edge
STEPS TO REPRODUCE
1. Use the desktop window from Setup (side panel open).
2. Open the home page.
3. Move the mouse over the orange "Industry" circle in the hero.
4. Look at the "Construction" label at the top right.

ACTUAL RESULT
The label shows "Constructio"; the last letter is cut off at the right edge.
There is no horizontal scrollbar to reach it.

EXPECTED RESULT
The full label is visible inside the window.

Result: [ ] Reproduced  [ ] Not reproduced

---

## C1: Phone field with letters shows the "empty field" message
STEPS TO REPRODUCE
1. Open the home page and scroll to the contact form ("Talk to a Zeta Specialist").
2. Type abc in Phone Number.
3. Leave the other fields empty and press Send.
4. Read the message under Phone Number.

ACTUAL RESULT
The field shows "abc". The message reads "Please enter your phone number."
(For comparison: typing "test@" in email shows "Please enter a valid email address.")

EXPECTED RESULT
The message tells the user the phone value is not valid, not that the field is empty.

Result: [ ] Reproduced  [ ] Not reproduced

---

## C3: Enquiry tabs have no "selected" state for screen readers
STEPS TO REPRODUCE
1. Scroll to the contact form.
2. Right-click the active "Sales" tab and choose Inspect.
3. In DevTools, look at the element's attributes.
4. Click "Partner" and inspect it again.

ACTUAL RESULT
Neither tab has aria-selected or aria-pressed. The active tab is shown only by its outline and colour.

EXPECTED RESULT
The active tab is announced as selected to assistive technology.

Result: [ ] Reproduced  [ ] Not reproduced

---

## C4: Two different reds for validation messages
STEPS TO REPRODUCE
1. Scroll to the contact form. Type test@ in Company Email; leave the rest empty.
2. Press Send.
3. Right-click "Please enter your name." and choose Inspect. In DevTools open Computed and find "color".
4. Do the same for "Please enter a valid email address."

ACTUAL RESULT
"Please enter your name." is rgb(220, 38, 38).
"Please enter a valid email address." is rgb(185, 28, 28).

EXPECTED RESULT
All validation messages in the form use the same colour.

Result: [ ] Reproduced  [ ] Not reproduced

---

## C5: Form fields without an accessible name (check carefully)
STEPS TO REPRODUCE
1. Scroll to the contact form.
2. Right-click the Name field and choose Inspect.
3. In DevTools, open the "Accessibility" tab (next to Styles). Read "Name" under Computed Properties.
4. Repeat for every field and checkbox (10 controls).

ACTUAL RESULT (from the automated run, to confirm)
Some controls show an empty Name.

EXPECTED RESULT
Every control has a Name that matches its visible label.

Note: use the Accessibility tab, not just the HTML. A name can come from aria-label, a
placeholder or a wrapping label. Report the exact fields with an empty Name.

Result: [ ] Reproduced (fields: ________)  [ ] Not reproduced

---

## D1: Zenita chat button covers the footer "Security" link
STEPS TO REPRODUCE
1. Use the desktop window from Setup (side panel open).
2. Open the home page and scroll to the very bottom.
3. Look at the bottom-right, beside "Privacy Policy".
4. Click the middle of the word "Security".

ACTUAL RESULT
The round Zenita button covers part of "Security". Clicking the covered part does not open the Security page.

EXPECTED RESULT
The "Security" link is fully visible and can be clicked.

Result: [ ] Reproduced  [ ] Not reproduced

---

## Extra check: testimonials visible?
STEPS
1. Open the home page and scroll to the testimonials section.
2. Wait 10 seconds.

CHECK
Can you see the quote text and the person's name and role (e.g. "Louise Kenna · HR Manager")?
- Yes: no bug. Also check there is a space before and after the "·".
- No (empty or invisible card): this is a bug. Take a screenshot.

Result: [ ] Visible  [ ] Not visible
