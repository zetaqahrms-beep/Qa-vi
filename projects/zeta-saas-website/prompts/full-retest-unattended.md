# Full retest after a site update (unattended, SaaS Claude Code + Playwright)

**Purpose:** re-check every open item and sweep all pages after a new build, with no stops.
**Run with:** Sonnet, High. Fresh session. Permission mode: Auto (so no prompts stop it). PC must not sleep.
**Resume line (if it stops at a usage limit):** "Continue the retest: read docs/qa-retest-2026-10-09-update.md and the prompt below, and carry on from the first part not marked DONE."

## Prompt

```
Full retest of the Zeta SaaS website after a new update (9 Oct 2026). I am away.
This run must NOT stop or ask me anything. Work through every part, then write the summary.

<site>https://zetahrms-saas.com:8085/ERPSaasUI</site>  Desktop only. Default viewport 1291x775.

UNATTENDED RULES
- Never ask a question and never wait for me. When something blocks you: retry once after
  5 seconds; then mark it BLOCKED (with the reason) and move to the next item.
- Time-box: about 5 minutes per item. If you go over, mark CANNOT TELL and move on.
- Site down: wait 1 minute, retry up to 3 times, record the outage times, continue.
- Save as you go: after EVERY part, append its results to docs/qa-retest-2026-10-09-update.md
  and mark the part "DONE". If the run stops, nothing is lost.
- Put scratch scripts in tmp/retest-2026-10-09/. Do not edit test files or other files. Leave the
  uncommitted files Bugs/phase1/forms.mjs, home.mjs, industries.mjs, site.mjs untouched.
  No git commits. No installs.
- Jira: READ only (to see what a ZNW ticket says). Never create, edit, comment or change status.
- Forms: test validation only. Never submit a form that would pass validation.
- Never print credentials.

MEASURING RULES (learned the hard way)
- Reach country pages through the header country chooser: click the country name in the top
  bar, click the country (a SPAN inside the open panel, not the footer REGIONS copy), click
  "Done". Check the URL is /country/<code>. Never type a country address (except ZNW-165).
- Wait 25 seconds on a page before reading any animated counter.
- Overlap: use document.elementFromPoint at the left edge, centre and right edge, AND take an
  element screenshot and look at it.
- Clipping: compare the text's Range rect with its nearest overflow-hidden ancestor on BOTH the
  left and right sides, AND look at an element screenshot. Never trust only scrollWidth.
- Menus: decide "open" by the panel being visible on screen (size > 0, in viewport, not hidden),
  not by the element existing. Before any keyboard verdict, prove Tab moves the focus.
- A verdict needs the right state: right viewport, section scrolled into view, counters settled.
  If you are not sure the state was right, the verdict is CANNOT TELL.
- Verdict words only: REPRODUCES / NOT SEEN / CHANGED (describe how) / NOT APPLICABLE /
  CANNOT TELL / BLOCKED. Never say "fixed". Never use "every", "all", "always", "unchanged"
  unless you checked every one. Never guess causes.

PART 0 - State
Record the time (UTC), the build identity if visible (version text, main JS file name/hash),
and git status (read only).
FIRST measurement, before anything else touches the backend: ZNW-187 cold start. Call
/ERPSaasUIBackend/health three times; record the time to first byte of each.

PART 1 - Open items (for each: verdict, evidence with numbers/quotes, time)
A2  Home hero sector labels: right edge of each label vs viewport, at 1291x775 AND 1280x650.
    Last result: "Construction" ended at 1311 (1291 wide); at 1280x650 also "Manufacture" 1281.
    Horizontal scrollbar present?
D1  Footer "Security" link (/trust) on /home and /zetapartner: what sits on top (left/centre/
    right)? Last result: the Zenita launcher (span.zbot-pulse). Then click its centre and
    record the URL you land on.
C1  Contact page, each tab: type gfdfg in Phone, leave the field. Is the value kept? Any message?
E1  1291x775, home: scroll the Solution Finder section into view (heading "Find your fit in
    under two minutes"). Is the left page-menu item "Solution Finder" covered by the heading?
    (Tester confirmed it on 9 Oct 12:22 before the update.)
F1  FAQ page: click each of the 7 category links (fresh load each time). Where does each land?
    Last result: all 7 went to /home#<fragment>.
F3  "What we Offer" by keyboard: Tab to it, Enter (opens?), Escape (closes?), reopen, Tab past
    the last item to the next header item (closes?).
F4  Country chooser: is Bahrain visible without scrolling the list? Is there any scroll sign?
K1  Qatar and Bahrain hero chips: any text cut off on either side? Last report: "AR" for QAR,
    "TATUTORY", "3HD" for BHD, "ANGUAGES". Screenshot each chip row.
K2  Qatar page: list every place "Labour Law" or "Labor Law" appears, with the exact text.
K4  UK page: "WHY ZETA IN UK", "Built for how UK works", "Statutory-ready for UK",
    "Talk to us in UK": still there? (missing "the")
HEAD On ALL 15 country pages: the closing headline text, and the line under it (last seen
    "Ready to run Zeta?" / "Join 2,000+ businesses across 20+ countries ..."), plus the
    STATUTORY chip number and the hero heading.
ZNW-77  Count the countries in the chooser on screen. Compare with the top banner
    ("Localized for 16 countries & currencies") and any other country count on the site.
ZNW-196 WhatsApp controls on country pages: is the icon the WhatsApp mark?
ZNW-165 Type /ERPSaasUI/country/ae directly: does the page render or stay blank?
ZNW-175 Does /ERPSaasUIBackend/swagger/index.html open?
ZNW-189 An unknown path (e.g. /ERPSaasUI/qa-no-such-page): HTTP status and what renders.
ZNW-190 Any request for /favicon.ico or console error about it on /home?
ZNW-191 Buttons with no accessible name on /home, INCLUDING the Solution Finder option cards
    ("Finance & operations", "People & payroll", ...) which are visible in the card on the right.
Text tickets, quote what you see: ZNW-178 ("Manufacture"), 179 ("Health"), 180 (Zenita bubble
    text; last seen 3 texts, not "Click on me to know more!"), 181 ("Run Live In 30 Minutes"),
    183 ("Asia Pacific" vs "APAC"), 184 ("Industry" shown as a sector), 185 ("on-premise"
    capitalisation), 194 (header social icons: YouTube present?).
Code checks (read only): 192 (count of visible text below 12px), 193 (Twitter bird or X logo),
    195 (brand logos vs outline icons), 197 (accessible names in lowercase), 198
    (backdrop-filter without -webkit- prefix), 199 (scrollbar styles WebKit-only).
Also read ZNW-141, ZNW-149, ZNW-155 and ZNW-177 in Jira and re-check what each describes.

PART 2 - Full-site sweep for new problems after the update
Visit every page reachable from the header, the "What we Offer" menu, the footer, and all 15
country pages. On each page record: HTTP status, page title, console errors, failed network
requests, broken images, links that land on the wrong page (e.g. back on /home), horizontal
overflow, clipped or overlapping text, anything covered by the Zenita launcher, and text or
figures that contradict another page. Forms (Contact tabs, Partner, Free Consultation popup,
sign-in page): mandatory markers and messages for empty / invalid email / invalid phone. Never
submit valid data.

PART 3 - Report (top of docs/qa-retest-2026-10-09-update.md)
1. Summary: time range, build identity, outages, how many items REPRODUCE / NOT SEEN /
   CHANGED / CANNOT TELL / BLOCKED.
2. Table of PART 1: item | verdict | evidence | time.
3. NEW problems from PART 2, each as STEPS TO REPRODUCE / ACTUAL RESULT / EXPECTED RESULT
   (about 200 words, evidence only, no severity, no fixes, no causes, never "still").
4. BLOCKED / CANNOT TELL list with the reason, so I can check by hand.
Do not draft Jira edits or status changes. I will review everything first.
```

## Changelog
- 2026-10-09: first version (after the release-day update)
