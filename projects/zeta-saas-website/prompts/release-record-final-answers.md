# Release record: final answers (paste into the release-record SaaS session)

**Run with:** Sonnet, High, same release-record session (needs its earlier measurements). Run AFTER the unattended retest has finished (one heavy session at a time).

```
Answers from my manual check at 1291x775, 9 Oct 2026, 12:22 IST (BEFORE the developers' update):
- E1: YES   F3: NOT CONFIRMED (my result was unclear; do not draft F3)   F4: YES
- K1 Qatar chips cut off: NOT CHECKED   K1 Bahrain chips cut off: NOT CHECKED (do not draft K1)
- The closing headline on a country page reads: "Ready to run Zeta?"
  (seen on /country/qa at 12:28 IST; the line under it: "Join 2,000+ businesses across
  20+ countries. Compliant, connected and supported locally.")
- ZNW-186: no status from QA. Reject and Deferred are developer statuses, not ours.
  Add only a "QA re-check 9 Oct 2026" description edit: out of QA scope (phone resolution;
  desktop only since 7 Oct 2026).
Draft only the items marked YES, with "manually confirmed by the tester, 9 Oct 2026"
as the evidence. List F3 and K1 as "pending" in the approval list.

NEW: the developers released an update after my manual check. The unattended retest report
docs/retest-after-update-2026-10-09.md has the post-update results. Read it first. Where it
differs from your earlier measurements or my manual results, use the retest result, say
which items changed, and do not draft anything the retest marks NOT REPRODUCED.
If the retest reproduces F3 or K1 with evidence, draft them too.

Corrections:
1. Country content changed today (Kenya SHIF only and "STATUTORY 3 ready", Oman SPF,
   Mauritius CSG/NSF).
   - K3: DROP. It no longer reproduces and was never raised.
   - STEP 3 Suggestion ticket: DO NOT RAISE. Put your measured list in the release-status
     document under "Compliance names: updated by developers on 9 Oct 2026; correctness
     not verified by QA".
2. List which country pages you visited. The chooser has 15 countries. Visit any you
   missed and read the closing headline and the STATUTORY chip (or take them from the
   retest report).
3. ZNW-77: count the chooser entries on screen today and use that number.
4. D1: keep "Clicking the covered part of the link does not open /trust" only if you
   actually clicked and stayed on the page. Otherwise remove the sentence.
5. K2: check the page again and say where each spelling appears (hero pill, tile title,
   tile body, hero line, card).
6. Ticket bodies contain ONLY STEPS TO REPRODUCE / ACTUAL RESULT / EXPECTED RESULT.
   No NOTE section and no "Related:" line in any body (remove them from every draft,
   e.g. "Related: ZNW-113 (closed) ..."). Never mention or link Closed tickets.
7. ZNW-200: add the four UK headings (K4), plus one line saying what the closing headline
   reads today and on which pages.
8. NO status proposals at all. Reject, Deferred and Fixed are developer statuses. For
   ZNW-180 (the reported bubble text is not shown; three different texts appear),
   ZNW-182 (the home page form was removed by design), ZNW-186, ZNW-188 and ZNW-190:
   only a "QA re-check 9 Oct 2026" description edit with the evidence.
9. ZNW-191: no status change. It stays open until the quiz buttons are checked.
10. Status document: note that site content changed during release day (and a new update
    was released in the afternoon), so every measurement has its date and time.

Then write the release-status document and bring the full approval list in one piece.
STOP before any Jira write.
```
