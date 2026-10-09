# Reply to the release-record run after STEP 0 (v2: lead's tickets are ours)

```
Answers to your STEP 0 questions. Continue the run with these.

Background: ZNW-178 to ZNW-200 were raised by my team lead while studying testing with
Claude AI. My lead has told me to handle them as OUR tickets: we may edit them, change their
status and retest them after fixes. Team rules still apply (New/Deferred: edit the description,
no comments; comments only on Reopened; never set "Fixed" — that is the developers' status).
Every Jira write still needs my approval per item.

1. ZNW-187, ZNW-190, ZNW-191: re-measure each once with the same method as 7 Oct
   (REPRODUCES / DOES NOT REPRODUCE + evidence). For each that DOES NOT REPRODUCE, draft:
   (a) a description edit adding "QA re-check <date>:" with the exact evidence, and
   (b) a proposed status change to "Reject".
   For any that REPRODUCES, keep it open and include it in the status document.
2. ZNW-186: phone-only; phone views are out of QA scope (desktop only since 7 Oct).
   Do not re-measure. Draft a description edit "Out of QA scope: phone resolution
   (desktop only since 7 Oct 2026)" and a proposed status change to "Reject".
3. ZNW-188 (/pricing -> Contact): confirmed BY DESIGN by my lead on 8 Oct. Draft a description
   edit recording that decision and a proposed status change to "Reject".
4. K4: do not raise a new ticket. ZNW-200 is New, so draft a DESCRIPTION EDIT to ZNW-200
   adding the other four strings, quoted exactly:
   "WHY ZETA IN UK", "Built for how UK works", "Statutory-ready for UK", "Talk to us in UK".
5. Links: F4 "relates to" ZNW-199; A2 "relates to" ZNW-184; C1 "relates to" ZNW-25 and ZNW-168;
   F3 "relates to" ZNW-99; D1 "relates to" ZNW-115; E1 "relates to" ZNW-94.
6. F1: use your full 6 Oct measurement (7 of 7 category links leave the FAQ page) plus one
   fresh re-measurement today.
7. Uncommitted files Bugs/phase1/forms.mjs, home.mjs, industries.mjs and site.mjs are NOT
   yours. Leave them untouched and keep them out of every commit (stage only your own files).
8. Before drafting each item, run a FRESH ZNW search again (new tickets may appear today).
   If a new duplicate appears, stop that item and tell me.
9. Also review the rest of ZNW-178..200 (the ones not listed above): for each, one line —
   key | title | your quick verdict from existing evidence (REPRODUCES / DOES NOT REPRODUCE /
   NOT CHECKED). Read only; no edits.

Then continue:
- STEP 1: re-measure and draft A2, D1, E1, C1, F1, F3, F4, K1, K2, K3 (K4 is the ZNW-200 edit).
- STEP 2: draft the description edits (ZNW-77, ZNW-165, ZNW-141, ZNW-177, ZNW-149, ZNW-155,
  ZNW-200, and the edits from answers 1–3).
- STEP 3: draft the business-confirmation Suggestion ticket.
- STEP 4: draft the QA release-status document, including ZNW-178..200 with their verdicts,
  and a "Retest after fix" list of every open ticket QA owns.
- STEP 5: STOP and show me everything: drafts, edits, proposed status changes, the
  Suggestion, the document and the answer-9 table.
  Create, save, change status or commit nothing until I reply with the exact items.
```
