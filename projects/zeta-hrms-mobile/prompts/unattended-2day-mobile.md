# Unattended run while the tester is away (ZetaMobile Claude Code)

**Run with:** Sonnet, Medium (stretches the Pro limit). SAME session as pagination phase 2 (it needs the pre-step context).
**Limits:** the run stops when the Pro usage limit is hit; progress is saved per part. Resume line: "Continue the unattended run: read docs/unattended-run-2026-10-09.md and carry on from the first part not marked DONE."

```
I am away for about 2 days. The PC, emulator and Appium stay on. Work through the parts
below in order WITHOUT asking me anything. When something blocks you, write BLOCKED + the
reason in the report and move to the next item.

ANSWERS TO YOUR TWO DECISIONS
1. Yes: fix the reader first (count by row id, keep scrolling past a stall, load-boundary
   logging), then re-read Approve Leave three times. Framework commits separate from the
   report.
2. Yes: batches 9 + 1 (markers "QA TEST pagination 01".."10") -> totals 20 and 21.
   Measure the existing 10->11 boundary before creating anything.

UNATTENDED RULES
- Test accounts only (requester, approver L1/L2/L3). Never a real person's account. Never
  change HRMS admin configuration. Never touch production. Never print credentials (name
  accounts by role).
- NEVER approve, reject, cancel, withdraw or delete anything. Create ONLY the 10 pagination
  records above. No other submissions: test forms by filling and checking validation, then
  go back without submitting.
- No Jira at all. No email reading. Commit locally, never push. Leave
  docs/prompts/old-app-1.0.19-start.md untouched. Do not clean up the pagination records.
- Evidence before verdicts; CANNOT TELL when a run proves nothing. Keep APP findings and
  FRAMEWORK faults in separate sections. A possible app bug must reproduce twice, with a
  screenshot in docs/evidence/ (never only in test-results/), before it goes in the report.
- Recovery: if Appium or the app session dies, restart the session once and relaunch the
  app. If the emulator itself is gone, write BLOCKED and stop the run with the report saved.
- Time-box each item to about 20 minutes; then CANNOT TELL and move on.
- Save the report docs/unattended-run-2026-10-09.md after EVERY part and mark the part DONE.
  Commit the report after each part ("Unattended run: part N").

PART 1 - Finish pagination phase 2 (as approved above). Requester Salary Certificate:
boundaries 10/11 (existing), 20, 21. For each: rows by row id, duplicates, lost rows, order,
re-open twice, pull to refresh, when new rows load. Batch 2 is the "create, return, re-read"
check. Approve Leave: three fixed-reader reads; if the counts differ between reads, record
each read with screenshots (possible app finding: list content changes between visits).
Approver side: baseline of the Approvals menu and the bell (all queues, to the end) before
batch 1, and again after each batch - read only. Append "Phase 2" to
docs/pagination-report-2026-10-09.md.

PART 2 - Open queues never checked: every approval queue the bell lists that the Approvals
menu did not show (e.g. Approve Salary Certificate Request). Can each be opened? Does its
row count match the bell and (if visible) the tile? Read only. Also the 8 "Other Requests"
entries that did not open in phase 1: try each once more, record what opens.

PART 3 - Bug hunt, read only, module by module, as requester and as approver L1:
home/dashboard, leave (balances, history, filters), HR requests (each type: open the form,
check required markers and messages for empty / invalid input, then back WITHOUT submitting),
attendance (history, regularisation screen incl. its empty state), approvals (each queue,
detail screens), notifications (counts vs lists), profile, settings, logout/login.
Check on every screen: crashes or freezes, blank screens, endless loaders, wrong or
inconsistent counts, text cut off or overlapping, wrong dates/times, back-button behaviour,
pull to refresh, empty states, error messages, English spelling. English only (Arabic is out
of scope).

PART 4 - Final report (top of docs/unattended-run-2026-10-09.md):
1. Summary: start/end time, parts done, counts per verdict.
2. APP findings: each as STEPS TO REPRODUCE / ACTUAL RESULT / EXPECTED RESULT, roles not
   usernames, screenshot path. Mark each "candidate - tester to confirm by hand".
3. FRAMEWORK faults found and fixed (commit ids).
4. Records created (count, type, markers) and their current state. Clean-up NOT done.
5. BLOCKED / CANNOT TELL list with reasons, for me to check by hand.
Then stop.
```
