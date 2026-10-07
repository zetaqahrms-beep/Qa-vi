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
