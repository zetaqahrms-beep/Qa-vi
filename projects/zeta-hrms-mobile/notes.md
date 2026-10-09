# Notes & Decisions

Running log of decisions, ideas and context for this project, newest first.
Claude reads this at the start of a chat to pick up where we left off.

<!-- Format:
## YYYY-MM-DD
- Decision / idea / open question
-->

## 2026-10-09
- Phase 2 pre-step (9 Oct): Salary Certificate requester list = 11 rows (reader deduped two identical labels -> framework fault #5; phase-1 '10' was wrong). Approve Leave L1: reads 10,10,10,10 then slow scroll 15 then 10; bell 43, tile 10, portal 11 -> CANNOT TELL (possible app finding if inconsistent with fixed reader). Search box CANNOT TELL. Bell shows 10 queues incl. Pending Approve Salary Certificate 11 (menu showed 4). Approved: fix reader first, batches 9+1. Unattended 2-day prompt: prompts/unattended-2day-mobile.md (no approve/reject/cancel, only 10 marked records, no submissions otherwise, no Jira/email, report per part).
- Phase 2 STEP 1 plan (9 Oct): list = Salary Certificate (requester, Submitted tab; no balance, Purpose shows in row). Batches 1/9/1 -> 11/20/21, markers 'QA TEST pagination 01..11'. Clue: notification-counts.json (15 Sep) said Pending Approve Leave 31 vs tile/list 10 -> read-only pre-step first. No Approve Salary Certificate queue found for L1 (CANNOT TELL). Cleanup = delete before any approval (MAB-123). Approved with: pre-step stop-if-proof, framework logging in separate commit, no approving, cleanup only on my go.
- Developers: page size 10; test data creation allowed. Phase 1 lists stopped at EXACTLY 10 rows (Submit Leave, Salary Certificate, Approve Leave) -> possible page-1-only cap; Approve Leave matched app count. Phase 2 prompt: prompts/pagination-phase2.md (boundaries 10/11/20/21, plan + approval first).
- Pagination report done (docs/pagination-report-2026-10-09.md, commit bd7fa46 local). Verdict: no defect within available data; multi-page NOT TESTED (max 10 rows, no page size spec). Attendance Regularisation 0 rows + no empty message = CANNOT TELL -> manual check. Not tested: 8 Other Requests entries, search/filter/sort, L2/L3 queues, server-side paging. Ask lead: page size requirement, permission for bulk test data.
- Teaching cleanup DONE 9 Oct (repo commit b4f298f local; memory: coaching file deleted, no-lessons note added). b4f298f also swept in 3 older uncommitted edits to old-app-1.0.19-start.md -> split done: cd6a70e (one line). 3 user edits uncommitted for review (one [BRACKET] left; CROSS-APP row removed - deliberate?). Dry run found: coaching lives only in Claude memory files (coaching-after-technical-answers.md, user-junior-automation-tester.md, MEMORY.md) + one line in docs/prompts/old-app-1.0.19-start.md. Answers sent: delete coaching file + add no-lessons note; keep answer style + ask-dont-guess; drop teaching framing; cut the coaching sentence from the old-app prompt.
- Pagination run (interim): no pagination controls on 11 lists across 2 accounts; integrity clean (0 duplicates, 0 lost, stable order; 4/4 queues match app counts). Empty state: Resumption Request OK; Attendance Regularisation shows no rows and no message (candidate). Not done: 8 Other Requests lists, search/filter. Limitations: no page size spec, no permission to create multi-page data. Report prompt: prompts/pagination-report.md.

## 2026-10-07
- Brief filled in from intake session. This project is ZetaMobile: Appium + WebdriverIO test framework for the ESS Android app (`com.zeta.zeta_ess`), Jira MAB.
- Replaced the earlier pre-filled brief, which described the Flutter app's source conventions; the work here is black-box testing, not app development.
- Prompt priority: 1) project direction review. Second prompt still open (suggested: MAB bug report writer).
- Current task in progress: pagination testing.
- Project folder created.
