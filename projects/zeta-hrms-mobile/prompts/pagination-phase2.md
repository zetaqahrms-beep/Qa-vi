# Pagination phase 2: page size 10, test data allowed (ZetaMobile Claude Code)

```
Pagination phase 2. New facts from the developers (9 Oct 2026):
- Page size is 10.
- We may create test records on the TEST accounts to fill lists beyond one page.

Important: several lists showed EXACTLY 10 rows in phase 1 (Submit Leave, Salary Certificate,
Approve Leave). With a page size of 10, a list that stops at 10 could be page 1 only.
Approve Leave matched the app's own count; the others show no count, so for them it is
CANNOT TELL whether more records exist.

Rules: test accounts only; never change HRMS admin configuration; never touch production;
never print credentials (name accounts by role); evidence before verdicts; CANNOT TELL when a
run proves nothing; keep app findings and framework fixes separate; bugs go to me in chat
first, no Jira writes; commit locally, never push. Do not add any coaching or lessons.

STEP 1 – Plan only, create nothing:
a. For Submit Leave and Salary Certificate: is there any way to see the true record count
   (web portal, an API response the app already makes, a count elsewhere in the app)?
   Read only. Report what you find.
b. Pick ONE requester list where creating records is simplest and has no balance limit
   (e.g. a request type that does not consume leave). Explain why.
c. Propose exactly how many records to create to test the boundaries: 11, then 20, then 21.
   Each record clearly marked (e.g. reason/remarks "QA TEST pagination <n>").
d. Say which approver(s) will receive notifications or approval items, and propose a
   clean-up plan (withdraw/cancel) for after the test.
STOP after STEP 1 and wait for my approval.

STEP 2 – After approval, create records in batches and test at each boundary
(10, 11, 20, 21 rows):
- Open the list fresh. Scroll to the end. Count rows. Record when new rows load
  (after row 10? after row 20?).
- Integrity: no duplicates at the boundary (row 10/11, 20/21), nothing lost, order stable
  (state the order: newest first or oldest first).
- Re-open the list twice; same rows each time.
- Pull to refresh at the top: list still complete.
- Create one more record while the list is open/after returning: does it appear in the
  right place, and does the total stay correct?
- Approver side: if the records create approval items, check the approver queue the same
  way at 10/11 and 20/21, and that the queue count matches.
- Note loading indicators, "No more records", or blank rows at the bottom.

STEP 3 – Report (append to docs/pagination-report-2026-10-09.md as "Phase 2", commit locally):
summary verdict per boundary (PASS / FAIL / CANNOT TELL), evidence table, app findings with
STEPS / ACTUAL / EXPECTED, records created (count, type, marker), and the clean-up status.
Do not clean up until I approve.
Commit ONLY docs/pagination-report-2026-10-09.md. Leave every other changed file
(e.g. docs/prompts/old-app-1.0.19-start.md) uncommitted and untouched.
```
