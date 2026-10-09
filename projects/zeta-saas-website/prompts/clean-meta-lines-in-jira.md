# Remove process/meta lines from our Jira text (SaaS Claude Code)

**Run with:** Sonnet, High. Fresh session.

```
Clean-up task in Jira project ZNW. Our ticket texts contain lines the developers do not need.
Remove them. Only touch text that QA wrote; never change anyone else's text.

SCOPE
- New tickets ZNW-201 to ZNW-209: the whole description is ours.
- Edited tickets ZNW-77, 141, 149, 155, 165, 166, 177, 182, 186, 187, 188, 190, 191, 200:
  ONLY the paragraph we appended on 9 Oct 2026 (it starts "QA re-check 9 October 2026" or
  "Request body sent by the guard test"). Every other word in those tickets stays.

REMOVE ALWAYS
- "Manually confirmed by the tester ..." - drop the prefix. If the rest is a useful
  observation, keep it as a plain sentence (e.g. "Nothing on screen shows that the list
  scrolls.").
- "Observed on zetahrms-saas.com:8085, build ..., 9 October 2026, at a viewport of ..." lines.
  The viewport is already in step 1; Jira already shows the date.
- Measurement times and dates inside sentences: "(07:57 UTC)", "11:05 UTC", "Measured
  9 October 2026, 11:02 UTC, build main-AJ2WBBZY", "(decision recorded 9 October 2026)",
  "on 8 October 2026".
- Build names (main-AJ2WBBZY) in ticket text.
- How QA worked: "Each link was clicked once, from a freshly loaded FAQ page." and similar.
- In the appended re-check paragraphs keep ONE short label at the start: "QA re-check
  9 Oct 2026:" (it marks which text is new). Remove "build ..., viewport ..., <time>" after it.

SHOW ME, DO NOT DECIDE
- Technical measurement wording (pixel coordinates, element names like "span.zbot-pulse",
  "document.body.scrollWidth", "aria-expanded"). Propose a plain-English version next to it;
  I decide per ticket.

RULES
- Bodies keep ONLY STEPS TO REPRODUCE / ACTUAL RESULT / EXPECTED RESULT. No NOTE, no
  "Related:", never "still".
- No status changes, no comments, no links. Never touch Closed tickets.
- Never print credentials. Do not push.

STEP 1 - Read every ticket in scope. For each, show: ticket | line now -> line after (or
"remove"). List the "SHOW ME" items separately. Then STOP and wait for my approval.
STEP 2 - Apply only what I approve. Report every ticket changed.
STEP 3 - Update your memory: replace any rule about labelling ticket text with build/date
with this one: "Ticket text has no process or meta lines - no 'manually confirmed', no
'observed on', no build, date or time (except one 'QA re-check <date>:' label on an edit to
an existing ticket)."
```
