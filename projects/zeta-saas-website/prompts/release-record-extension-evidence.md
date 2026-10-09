# Release record: add the extension retest evidence (SaaS Claude Code, same session)

**Run with:** Sonnet, High. Same release-record session. Paste AFTER release-record-continue.md (or together with it).
**Before pasting:** copy `retest-after-update-2026-10-09.md` and the afternoon `report.md` (save it as `docs/extension-gap-checks-2026-10-09.md`) into the SaaS repo `docs/`, and the screenshots into `docs/retest-2026-10-09/`.

```
Extra evidence: a browser-extension retest ran 9 Oct 07:06-08:27 UTC on build main-AJ2WBBZY.
Report: docs/retest-after-update-2026-10-09.md. Screenshots: docs/retest-2026-10-09/.
Use it like this:
1. ZNW-165: typed full loads of /ERPSaasUI/country/qa and /ERPSaasUI/login/partner both
   rendered (ZNW165-*.jpg). Confirm once yourself with a typed full load. If it renders, add
   a "QA re-check 9 Oct 2026" description edit (not reproduced on build main-AJ2WBBZY).
   No status change.
2. D1: add to ACTUAL RESULT: a real click on the centre of "Security" opened the Zenita chat
   and the address stayed /ERPSaasUI/home (D1-home-click-opens-zenita.jpg).
3. F3: Tab-away is now measured: focus moved to "Zenita" while the panel stayed visible
   (F3-panel-stays-open-focus-on-zenita.jpg). Add it to the F3 draft.
   The hidden-panel tab stops (F3-focus-inside-hidden-panel.jpg) belong to the separate
   Tab-invisible-links candidate.
4. ZNW-180: the extension never looked at the Zenita section. Your measurement stands.
5. K1: ignore the extension's K1 verdict - it measured the hero chip row ("WPS Ready",
   "Qatar Labor Law"), not the left tiles. Its screenshot ZNW165-typed-country-qa-renders.jpg
   shows the tile labels as "AR" and "ANGUAGES"; you may attach it to K1.
6. K4: use the 4 visible headings. The extension also found "Zeta in UK - ERP & HRMS software
   in UK"; include it only if it is visible on screen (leave it out if it is only in the
   hidden screen-reader nav).
7. New candidate N1: /ERPSaasUI/login/customer and /ERPSaasUI/login/partner have the tab title
   "Zeta Software" only, while other pages use "<page> | Zeta Software". Do a duplicate search
   and draft it as a candidate. I decide with my lead.
8. Do not commit the extension report or its screenshots, except screenshots you attach.
9. Afternoon extension gap checks (15:49-16:05 IST, docs/extension-gap-checks-2026-10-09.md):
   - ZNW-180 confirmed: the Zenita-section bubble reads "Hi, I'm Zenita! Click on me to know
     more!" - matches your measurement.
   - K1, letter by letter on the left tiles: Qatar "?AR" (QAR), "??ATUTORY", "?ANGUAGES";
     Bahrain "??NGUAGES", and the B of "BHD" is partly covered (can read as "3HD"). The other
     13 country pages read cleanly. Use this in the K1 ACTUAL RESULT.
   - K4: "Zeta in UK - ERP & HRMS software in UK" is only in the hidden screen-reader nav.
     Use the 4 visible headings only.
   - ZNW-165: typed /country/ae also renders (second confirmation).
10. Jira: the extension could not reach Jira. YOU do the fresh duplicate search (all
   statuses) for every draft and candidate, and list the tickets developers marked Fixed
   with a quick retest of each (read only), before the approval list.
Standing rules still apply: no NOTE section, no "Related:" line, no links, no status proposals.
STOP before any Jira write.
```
