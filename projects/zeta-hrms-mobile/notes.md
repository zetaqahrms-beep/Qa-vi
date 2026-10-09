# Notes & Decisions

Running log of decisions, ideas and context for this project, newest first.
Claude reads this at the start of a chat to pick up where we left off.

<!-- Format:
## YYYY-MM-DD
- Decision / idea / open question
-->

## 2026-10-09
- Pagination report done (docs/pagination-report-2026-10-09.md, commit bd7fa46 local). Verdict: no defect within available data; multi-page NOT TESTED (max 10 rows, no page size spec). Attendance Regularisation 0 rows + no empty message = CANNOT TELL -> manual check. Not tested: 8 Other Requests entries, search/filter/sort, L2/L3 queues, server-side paging. Ask lead: page size requirement, permission for bulk test data.
- Mobile Claude still gives English/prompt/JS coaching -> teaching cleanup not yet run in the mobile project.
- Pagination run (interim): no pagination controls on 11 lists across 2 accounts; integrity clean (0 duplicates, 0 lost, stable order; 4/4 queues match app counts). Empty state: Resumption Request OK; Attendance Regularisation shows no rows and no message (candidate). Not done: 8 Other Requests lists, search/filter. Limitations: no page size spec, no permission to create multi-page data. Report prompt: prompts/pagination-report.md.

## 2026-10-07
- Brief filled in from intake session. This project is ZetaMobile: Appium + WebdriverIO test framework for the ESS Android app (`com.zeta.zeta_ess`), Jira MAB.
- Replaced the earlier pre-filled brief, which described the Flutter app's source conventions; the work here is black-box testing, not app development.
- Prompt priority: 1) project direction review. Second prompt still open (suggested: MAB bug report writer).
- Current task in progress: pagination testing.
- Project folder created.
