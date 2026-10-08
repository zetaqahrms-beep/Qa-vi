# Friday 9 Oct, after 11:30: SaaS Claude Code prompt

```
Resume SaaS QA work. Previous sessions hit usage limits, so check the real state first.

Team Jira rules: New/Deferred tickets are EDITED (description), never commented on.
Comments only on Reopened. Never touch Closed tickets. Never write to Jira without my
approval for each item. House format: STEPS TO REPRODUCE / ACTUAL RESULT / EXPECTED RESULT,
about 200 words, evidence only: no severity, no fixes, no cause guessing, never "still",
no "every/all" without proof. State the viewport for layout items.

STEP 0 – State check (read only, report back):
- git status and git log -5 in this repo.
- In Jira ZNW, has anyone already raised these today? Search by keywords:
  "Construction" cut off, Zenita / Security link, Solution Finder heading, phone letters
  Contact, FAQ category, India country page figures, "What we Offer" Escape, Bahrain.
- Were the 7 Oct re-check texts saved in ZNW-165 and ZNW-141 descriptions?

STEP 1 – Pending description edits (draft, show me, save only after approval):
- ZNW-165 and ZNW-141: if the 7 Oct re-check text is missing, add it.
- ZNW-177: quote the exact request body SEC-012 sends and its response errors[] entry.
  Do NOT write "the same body".
- ZNW-149: change "with a reasonable policy" to "with a policy"; add the 'unsafe-inline'
  script-src and style-src lines quoted exactly.
- ZNW-155: put the path-form steps and 7 Oct measurements first; move the 30 Sep hash
  results below under "Earlier measurement, 30 September 2026 (hash addresses, no longer served)".
- ZNW-77: add that the top banner reads "Localized for 16 countries & currencies" while the
  country chooser lists 15 countries.

STEP 2 – New bugs (manually verified by me). Re-measure each once with Playwright at
1291x775 (A2 also at 1280x650), then draft in house format. Skip any already raised (STEP 0).
- A2: home hero, hover "Industry": the "Construction" label is cut off at the right edge
  ("Constructio"/"Constructi"), no horizontal scrollbar.
- D1: footer "Security" link is covered by the Zenita launcher on /home AND /zetapartner;
  clicking the covered part does not open /trust. Link "relates to" ZNW-115.
- E1: home Solution Finder section on arrival: the heading "Find your fit in under two
  minutes" covers the left menu item ("Solution Find"). Link "relates to" ZNW-94.
- C1 (Low): Contact page phone field accepts letters ("gfdfg") and shows
  "Please enter your phone number." Link "relates to" ZNW-25.
- F1: /faq category links (#products, #partners, ...) open /home instead of the FAQ section.
- F2: /country/in figures ("7+ Countries served", "656+ Customers worldwide", "3K+ Core users",
  "66K+ ESS users") differ from /home ("20+ Countries", "2,000+ Companies", "200,000+ Users").
- F3: "What we Offer" menu stays open after Escape and after Tab moves focus away.
- F4 (Low): country chooser shows 14 of 15 countries on open; Bahrain only after scrolling
  inside the list, with no sign the list scrolls.

Do NOT raise (decided by design / dropped): home contact form removed, /pricing redirect,
popup country default UAE, Products alignment, testimonial "MEA, MEA", name ellipsis,
"Tap" wording, validation colours, label "for" attributes.

STEP 3 – Stop. Show me STEP 0 results, all drafts and edits. Create or save nothing until
I reply with the exact items.

STEP 4 – After approval: raise/save only approved items, add a guard test for each new bug
following this framework's convention for open bugs, register them in data/jiraReported.mjs,
run the new tests once, quote the failure messages, commit locally.
```
