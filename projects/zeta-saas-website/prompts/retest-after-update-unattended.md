# Full retest after the website update (unattended, SaaS Claude Code)

**Purpose:** retest every page and every open item after the developers' update, with no stops.
**Used by:** tester, in a FRESH SaaS Claude Code session, then walks away.
**Run with:** Sonnet, High. Fresh session. Permission mode Auto. PC must not sleep.

## Prompt

```
UNATTENDED FULL RETEST after the developers' new update of the Zeta SaaS website.
I am away. Do NOT stop, do NOT ask me anything, do NOT wait for approval. Work through all
parts in order. When something blocks you, write BLOCKED + the reason in the report and
move on. Put every question for me in the report section "Questions for the tester".

<site>https://zetahrms-saas.com:8085/ERPSaasUI</site>
Viewports: 1291x775 (main) and 1280x650 (second). Desktop only (phone is out of scope).

HARD RULES (no exceptions):
- Jira: READ ONLY. No edits, comments, status changes, links or new tickets.
- Never retest Closed tickets.
- Forms: check validation only. Never fill every required field with valid data and submit.
- Never type a two-level address (e.g. /country/qa) except for the ZNW-165 check. Reach
  country pages through the header country chooser: click the country name in the top bar,
  click the country (a SPAN inside the open panel, not the footer REGIONS list), click "Done".
- Wait 25 seconds on a page before reading any animated counter.
- Leave the uncommitted files Bugs/phase1/forms.mjs, home.mjs, industries.mjs and site.mjs
  untouched. Do not edit existing tests. Put scratch scripts outside the repo.
- Site down: wait 60 s and retry, up to 3 times. Still down: note the time, skip to the next
  part, and come back at the end.
- One item may take at most about 10 minutes. After that: CANNOT TELL, move on.
- Never push. Never print credentials.

EVIDENCE RULES:
- Every verdict has a measured value or a screenshot, plus the time (UTC).
- Verdicts: REPRODUCES / NOT REPRODUCED / CHANGED (describe) / CANNOT TELL / BLOCKED /
  NOT APPLICABLE. Never write "fixed"; developers decide that.
- No overclaim words (every, all, always, unchanged) unless you counted them; give the count.
- Do not guess causes. Do not suggest fixes. If you substitute a different element for the
  one named, the verdict is NOT APPLICABLE.
- Text clipping: take an element screenshot, open the image and read the letters you SEE.
  Code checks miss left-side clipping.

REPORT: docs/retest-after-update-2026-10-09.md. Write each part into the file as soon as it
is done (so nothing is lost if the run stops). Screenshots in docs/retest-2026-10-09/.
At the end, commit ONLY the report file locally: "Retest after update 2026-10-09".

PART 0 - Health (5 min): record the time; home page loads; /ERPSaasUIBackend/health status
and time; note anything that looks different since 9 Oct morning.

PART 1 - Existing test suite: run the project's Playwright tests as they are. Report
passed / failed / names of failures with the first error line. Do not change any test.

PART 2 - Tickets developers marked Fixed (or Resolved, Done, Ready for QA): search Jira
project ZNW, read only. Retest each one from its own steps. Most important part.

PART 3 - Our verified findings, not raised yet (measured 9 Oct, 1291x775 unless stated):
A2 Home hero: sector label "Construction" ends past the right edge (r=1311 in 1291);
   at 1280x650 "Construction" (1306) and "Manufacture" (1281); no horizontal scrollbar.
D1 Footer "Security" link (/ERPSaasUI/trust) covered by the Zenita launcher
   (span.zbot-pulse) on /home and /zetapartner. Also try a real click: does /trust open?
C1 Contact page, Sales tab: Phone accepts "gfdfg"; no message after leaving the field.
E1 Home, Solution Finder section scrolled into view: the left-menu item "Solution Finder"
   is covered by the heading "Find your fit in under two minutes". Screenshot.
   Also check at 1920x1080 (expected fine there).
F1 FAQ category links (#products #pricing #deployment #implementation #support #security
   #partners) land on /home#<fragment> instead of the FAQ section. Click each one.
F3 Keyboard: Tab to "What we Offer", Enter. (a) Does the menu open? (b) Escape: does it
   close? (c) Reopen, Tab past the last item to "Zenita": does it close?
F4 Country chooser: Middle East column ends at "Oman"; "Bahrain" only after scrolling
   inside the list. Screenshot on open.
K1 Qatar and Bahrain pages: hero chips cut off ("AR" for QAR, "TATUTORY", "3HD" for BHD,
   "ANGUAGES"). Element screenshots of the chip row on all 15 country pages.
K2 Qatar page: "Qatar Labor Law" and "Qatar Labour Law" both used. Say where each appears.
K4 UK page without "the": "WHY ZETA IN UK", "Built for how UK works",
   "Statutory-ready for UK", "Talk to us in UK".
HL Closing headline on country pages read "Ready to run Zeta?". Record the exact text on
   each of the 15 pages.

PART 4 - Open tickets (New, Reopened, In Progress), Jira read only: for each one, follow
its steps and give a verdict. Include ZNW-178..200 (ZNW-191: include the Solution Finder
quiz buttons; start the quiz first). Also: ZNW-165 (type /ERPSaasUI/country/ae directly:
blank?), ZNW-175 (/ERPSaasUIBackend/swagger/index.html reachable?), ZNW-176 (backend
Server / X-Powered-By headers), ZNW-77 (top banner country number vs countries in the
chooser vs "20+ countries" text; count the chooser on screen).

PART 5 - Full page sweep for new problems (both viewports). Pages: home, products,
industries, software development, consultancy, Zenita, partner, support, FAQ, what's new,
privacy, security/trust, contact (every tab), the consultation popup, My Portal menu,
sign-in page (validation and required markers only), all 15 country pages, and an unknown
address (404). On each page check:
- loads; console errors; failed network requests (4xx/5xx)
- internal links and images (request each internal link once; list failures)
- horizontal overflow; text cut off; elements overlapping (incl. the Zenita launcher)
- keyboard: header and footer reachable with Tab; visible focus
- spelling and grammar in visible text; same fact shown differently on two pages
- country pages: compliance names, STATUTORY chip count vs items listed (record, do not
  judge correctness of law names)
New problems: confirm twice before listing. Duplicate check: search Jira (read only) for
each one and note any matching ticket key.

FINAL REPORT (top of the file):
1. Summary: start/end time, parts done, counts per verdict.
2. Fixed-ticket retest table (PART 2) and suite result (PART 1).
3. Table for PART 3 and PART 4: item | verdict | evidence | time.
4. New findings: Summary, STEPS TO REPRODUCE, ACTUAL RESULT, EXPECTED RESULT (about 200
   words, evidence only, no severity, no fixes, no causes), plus a possible duplicate key.
5. What changed since 9 Oct morning (content, layout, behaviour).
6. Not done / BLOCKED / CANNOT TELL, with reasons.
7. Questions for the tester.
Then commit the report only. Do not stop before the final report is written.
```

## Changelog
- 2026-10-09: first version (after the developers' update on release day)
