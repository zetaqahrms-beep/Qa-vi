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

## C1 (Low): FOLD INTO the home-form ticket below (same fix as ZNW-25)
Summary: Phone number with letters shows the empty-field messages on the home contact form

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
For comparison, typing test@ in Company Email shows "Please enter a valid email address."

EXPECTED RESULT
The message states that the phone number entered is not valid.


## HOME-FORM: one ticket for fixes missing on the home page form
Before raising: open /zetacontact and confirm each behaviour there once (fixed state).
Check C5 with the DevTools Accessibility tab and list the exact fields with an empty Name.

Summary: The home page contact form does not have the fixes made to the Contact page form

STEPS TO REPRODUCE
1. Open https://zetahrms-saas.com:8085/ERPSaasUI/zetacontact and check the behaviours below
2. Open https://zetahrms-saas.com:8085/ERPSaasUI/home and scroll to "Talk to a Zeta Specialist"
3. Check the same behaviours on the home page form

ACTUAL RESULT
On the home page form:
- Phone Number accepts letters: "gfdfg" stays in the field, and the messages read
  "Please enter your phone number." and "Please complete the required fields."
  (Contact page fix: ZNW-25, Closed)
- The Sales / Partner / General tabs carry no aria-selected or aria-pressed; the active
  tab is shown by outline and colour only. (Contact page fix: ZNW-161, Closed)
- Validation messages use two reds: rgb(220, 38, 38) and rgb(185, 28, 28).
  (Related Contact page fix: ZNW-100, Closed)
- [Only if confirmed] Fields with an empty accessible name: <list>.
  (Contact page fix: ZNW-113, Closed)
Measured at 1280 x 650.

EXPECTED RESULT
The home page form behaves the same as the Contact page form for each item above.
