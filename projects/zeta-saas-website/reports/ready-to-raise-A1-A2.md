# Ready to raise (manually reproduced 2026-10-07)

Before raising: search ZNW for "Manufacture" and "Construction" (duplicates).
New tickets, so raise them as new (team rule: edits for New/Deferred, comments only on Reopened).
Attach the 1280 x 650 screenshot to A2.

## A1
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

## C1 (Low)
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
