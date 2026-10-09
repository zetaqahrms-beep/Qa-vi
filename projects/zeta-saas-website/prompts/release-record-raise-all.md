# Release record: raise all verified bugs + QA status document (SaaS Claude Code)

Use this INSTEAD of friday-after-reset.md (it includes everything from it, updated).

```
The website is being released WITHOUT QA approval. Every verified, open problem must be
recorded in Jira today, and a QA release-status document must be saved, so the record
shows what QA found before release.

Team Jira rules: New/Deferred tickets are EDITED (description), never commented on.
Comments only on Reopened. Never touch Closed tickets. House format: STEPS TO REPRODUCE /
ACTUAL RESULT / EXPECTED RESULT, about 200 words, evidence only: no severity, no fixes, no cause
guessing, never "still", no "every/all" without proof, do not name the correct value unless a
requirement defines it. State the viewport (1291x775) for layout items.

STEP 0 – State check (read only): git status / git log -5. Search ZNW (including Closed,
Deferred, Rejected) for each item below and report NEW / DUPLICATE OF <key> / RELATED TO <key>.

STEP 1 – Re-measure each NEW bug once (Playwright, 1291x775; A2 also 1280x650) and draft it.
Bugs verified by the tester:
- A2  Home hero, hover "Industry": "Construction" label cut off at the right edge, no scrollbar.
- D1  Footer "Security" link covered by the Zenita launcher on /home and /zetapartner; clicking
      the covered part does not open /trust. Link "relates to" ZNW-115.
- E1  Home Solution Finder on arrival: heading covers the left menu item ("Solution Find").
      Link "relates to" ZNW-94.
- C1  Contact page phone accepts letters ("gfdfg"); message "Please enter your phone number."
      Low. Link "relates to" ZNW-25.
- F1  /faq category links (#products, #partners, ...) open /home instead of the FAQ section.
- F3  "What we Offer" menu stays open after Escape and after Tab moves focus away.
- F4  Country chooser shows 14 of 15 countries on open; Bahrain only after scrolling inside
      the list, with no sign it scrolls. Low.
- K1  Country pages, chips cut off: Qatar shows "AR" (QAR) and "TATUTORY"; Bahrain shows
      "3HD" (BHD) and "ANGUAGES". One ticket, both pages.
- K2  Qatar page: "Qatar Labor Law" (pill, tile title) vs "Qatar Labour Law" (tile body,
      hero, card).
- K3  Kenya page: heading "…KRA PAYE, NSSF and SHIF ready." vs chip and tile "NSSF & NHIF";
      heading names three schemes, chip reads "STATUTORY 2 ready".
- K4  UK page: "WHY ZETA IN UK", "Built for how UK works", "Statutory-ready for UK",
      "Talk to us in UK", "Ready to run UK on Zeta?" (no "the" before "UK").

STEP 2 – Description edits (draft):
- ZNW-77: add that the banner reads "Localized for 16 countries & currencies" while the
  chooser lists 15.
- ZNW-165, ZNW-141: add the 7 Oct re-check text if missing.
- ZNW-177: quote the exact request body SEC-012 sends and its errors[] entry (never "same body").
- ZNW-149: "with a reasonable policy" -> "with a policy"; add the 'unsafe-inline' lines.
- ZNW-155: path-form steps and 7 Oct measurements first; 30 Sep hash results below, labelled.

STEP 3 – One "Suggestion" ticket for business confirmation (do not call these bugs):
Summary: "Country pages: compliance scheme names and statutory lists need business confirmation"
List exactly what is shown: Kenya "NHIF", Oman "PASI", Sri Lanka "PAYE", Mauritius "NPF / NSF";
Saudi card "GOSI + WPS" (WPS not in its statutory list); Malaysia card "SOCSO & EIS" (EIS not in
its statutory list); Egypt names no tax authority or scheme. Note: developers said on
9 Oct 2026 they will check the current names.

STEP 4 – Save docs/qa-release-status-<today>.md:
- Release date, build/URL, and "QA did not approve this release; released by business decision."
- Table of every open ZNW ticket QA raised or edited for this release: key | title | type |
  status (include the new ones after approval).
- Known risks section: ZNW-165 (blank pages on direct links/refresh), ZNW-175 (public API docs),
  ZNW-176, ZNW-177, ZNW-149, ZNW-141.
- Decisions recorded: home contact form removed (by design), /pricing -> Contact (by design),
  popup default UAE (not a bug), partners count as local support (developers, 9 Oct).
- Not tested / limitations.

STEP 5 – STOP. Show me STEP 0 results, all drafts, edits, the Suggestion and the document.
Create, save or commit nothing until I reply with the exact items.

STEP 6 – After approval: raise/save only approved items, fill the real keys into the
document, add guard tests for new bugs per this framework's convention, register them in
data/jiraReported.mjs, run the new tests once, quote the failures, commit locally.
```
