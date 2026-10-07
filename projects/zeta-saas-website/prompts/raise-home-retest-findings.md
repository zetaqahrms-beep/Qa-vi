# Raise home page retest findings (2026-10-07)

**Purpose:** Turn the browser-extension home page retest report into Jira tickets, safely.
**Used by:** Claude Code in the SaaS project repo. Attach or paste `reports/home-page-retest-2026-10-07.md` with it.

## Prompt

```
Attached is the home page retest report from 7 October 2026 (browser extension, viewport
1291x775, DPR 1.14). Process these findings: A1, A2, C1, C3, C4, C5, D1.
Skip C2 and D2 (questions for my lead, not bugs).

Step 1 – Re-measure each with Playwright at 1291x775 (one page load each). For C5, do NOT
rely on a DOM query for labels: resolve accessible names with Playwright's role/name lookup,
because names can come from aria-label, alt, placeholder or wrapping labels. Verdict per item:
CONFIRMED / NOT REPRODUCED / CANNOT TELL, with exact evidence.

Step 2 – Duplicate search: data/jiraReported.mjs and ZNW, including closed and deferred.
Check C5 and C3 against ZNW-113. Result per item: NEW / DUPLICATE OF <key> / SAME ROOT CAUSE AS <key>.

Step 3 – Draft NEW items in house format (STEPS TO REPRODUCE / ACTUAL RESULT / EXPECTED RESULT,
about 200 words). No severity, no fixes, no cause guessing, no opinions about users, never
"still", no "every/all" without proof, do not name the correct value unless a requirement
defines it. State viewport and pointer position for layout items.
Team rule: if an item matches a New or Deferred ticket, draft a DESCRIPTION EDIT, not a comment.

Step 4 – Stop and show me everything. Create nothing until I name the exact items.
After approval: raise, add guard tests per this framework's convention, register in
data/jiraReported.mjs, run once, commit locally.
```

## Changelog
- 2026-10-07: first version
