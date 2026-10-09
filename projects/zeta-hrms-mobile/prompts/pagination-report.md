# Pagination run: final report prompt (ZetaMobile Claude Code)

```
Write the pagination test report for this run. Do not run new tests unless a number in the
report cannot be backed by a run you already did; if so, mark it CANNOT TELL instead.

Save it as docs/pagination-report-<today's date>.md and commit locally. Do not push.
Then show me the chat summary first.

Rules:
- Evidence before verdicts. Every number must come from a run in this session; name the run.
- Say CANNOT TELL where a run proves nothing. No "fixed", "passed" or "missing" without evidence.
- Keep APP DEFECTS and FRAMEWORK FIXES strictly separate. The four reader problems
  (scroll gesture, pre-scrolled list, stale empty message, reading before the screen opened)
  are framework fixes, not app findings.
- Never print credentials. Name accounts by role (e.g. "approver account", "requester account").
- No severity, no fix suggestions for the app, no cause guessing.
- Do not raise anything in Jira. Bugs go to me in chat first; I confirm by hand.

Report sections:
1. Summary (5 lines max): what was tested, the verdict, the biggest limitation.
   Verdict wording: "No pagination defect found within the data available" plus
   "Behaviour with more rows than one screen/page: NOT TESTED" if that is the case.
2. Scope: app version, device/emulator, accounts by role, date.
3. Mechanism: what kind of list loading the app uses (pagination controls, load more,
   infinite scroll, or none) with the evidence per list.
4. Lists covered: table
   List | Menu path | Account role | Rows seen | Mechanism | Duplicates | Rows lost between
   visits | Order changed | Matches app's own count | Empty state
5. Empty states: which lists show "No records found", which show nothing; exact text.
6. App findings: only defects shown on screen with evidence. For each:
   STEPS TO REPRODUCE / ACTUAL RESULT / EXPECTED RESULT, plus a MAB duplicate search result
   (read only). Include Attendance Regularisation (no rows and no message) only if re-confirmed.
7. Framework fixes made during the run: problem, how it showed, fix, commit hash.
8. Not tested and why: the eight "Other Requests" lists that would not open, search/filter,
   anything else skipped.
9. Limitations: no documented page size; no permission to create test data for a
   multi-page case.
10. Open questions for my lead (numbered, one line each).
11. Recommended next steps (max 5).
```
