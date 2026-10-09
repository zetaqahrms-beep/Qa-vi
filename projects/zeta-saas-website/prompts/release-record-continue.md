# Release record: continue after the usage limit (SaaS Claude Code, same session)

**Run with:** Sonnet, High. SAME release-record session (its post-update measurements live only in that conversation).

```
Answers to your 4 decisions, plus standing rules. Continue from where you stopped.

STANDING RULES - save these to memory too:
- Ticket bodies contain ONLY: STEPS TO REPRODUCE / ACTUAL RESULT / EXPECTED RESULT.
  No NOTE section. No "Related:" line. No mention of other tickets in the body.
  Before showing me any draft, check every draft and remove such lines.
- No Jira "relates to" links at all for now.
- Never touch, link, comment on or reopen Closed tickets (ZNW-25, ZNW-94, ZNW-99, ZNW-113...).
- No status proposals. Fixed, Reject and Deferred are developer statuses. QA only adds a
  "QA re-check 9 Oct 2026" description edit with evidence.

THE RETEST REPORT: it does not exist (that run has not been done). Drop that instruction.
Your own post-update measurements replace it.

BUILD: my manual check at 12:22 IST = 06:52 UTC, so it was AFTER the 06:13 UTC deploy, on
the same build you measured (main-AJ2WBBZY). Label all evidence "build main-AJ2WBBZY".
Before writing anything, check the main JS hash once more. If it changed again, quickly
re-measure the items you draft and say so.

DECISIONS:
1. Closed tickets: no links and no "Related:" lines (rules above).
2. ZNW-180: your post-update measurement stands (the reported text IS shown at the Zenita
   section). No "not reproduced" edit for ZNW-180.
3. Yes, draft F3 and K1 now, from your post-update evidence:
   - F3: only what you measured - Escape does not close the "What we Offer" menu (opened by
     hover and by Enter). Leave out Tab-away (not measured).
   - K1: describe what is SEEN, not the cause: on the Qatar and Bahrain pages the first
     letter of the tile labels cannot be read ("QAR" reads as "OAR"/"AR", "STATUTORY" as
     "TATUTORY", "LANGUAGES" as "ANGUAGES"). Attach the screenshots.
   - The "Tab walks through four invisible menu links while the menu is closed" finding:
     draft it as a SEPARATE new ticket candidate, with no mention of any other ticket.
     I will decide with my lead whether it is raised.
4. Yes, a "QA re-check 9 Oct 2026" description edit on ZNW-166 (the home page has no form,
   no email input and no Send button; the form was removed by design).

ALSO:
5. Re-run C1 and F1 on the new build (quick), so every draft has post-update evidence.
6. QA re-check description edits (evidence only) for: ZNW-182, ZNW-186 (out of QA scope:
   phone resolution; desktop only since 7 Oct 2026), ZNW-188 (by design: /pricing goes to
   Contact, team lead 8 Oct 2026), ZNW-190 (not reproduced), ZNW-191 (not reproduced; all
   quiz steps and review arrows have names), ZNW-187 (reproduces, 1.245 s cold),
   ZNW-200 (UK headings K4 + "Ready to run Zeta?" on all 15 pages), ZNW-77 (15 in the
   chooser vs banner "16 countries"; "20+ countries" text).
7. SEC-012 / ZNW-177: fix the test so it sends the raw bytes {not valid json (e.g. a Buffer
   with content-type application/json), run it once, and use the REAL response in the
   ZNW-177 edit. Commit the test fix separately: "Fix SEC-012: send raw malformed body".
   Do not amend or rewrite older commits.
8. Delete your scratch scripts (tools/_post1..8.mjs, _echo.mjs, _sec12.mjs). Leave my four
   Bugs/phase1/*.mjs files untouched.
9. Drafts to bring: A2, D1, E1, F4, C1, F1, K1, K2, F3, the new Tab-invisible-links
   candidate. Drop K3 and the Suggestion ticket.
10. Write docs/qa-release-status-2026-10-09.md: "QA did not approve; released by business
    decision", build hash and deploy time, the 06:16 UTC outage, content changes during the
    day (compliance names, closing headline), the ZNW-178..200 verdict table, open bugs,
    "Retest after fix" list, and "Compliance names: updated by developers on 9 Oct 2026;
    correctness not verified by QA". Commit the document only.

Then bring everything in one piece: all drafts, all description edits, and the approval
list. STOP before any Jira write.
```
