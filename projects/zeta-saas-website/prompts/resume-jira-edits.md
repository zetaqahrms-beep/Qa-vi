# Resume: Jira description edits (after weekly limit)

**Purpose:** Finish the Jira description edits that were interrupted by the weekly usage limit on 2026-10-07.
**Used by:** Claude Code in the SaaS project repo.

## Prompt

```
Resume interrupted work. The last session hit its usage limit while saving Jira edits.

Team Jira rule: New and Deferred tickets are EDITED (description), never commented on.
Comments only on Reopened tickets. Never touch Closed tickets.

Step 0 – State check (read only):
Open ZNW-165 and ZNW-141. Tell me whether the 7 October re-check text was saved in each
description. Also run git status and report anything uncommitted.

Step 1 – If not saved, save these two as approved earlier:
- ZNW-165: add the four addresses (/country/ae, /login/customer, /login/partner,
  /products/crm: 0 characters, tab "Zeta Software") and the two console errors
  (module script served as text/html; stylesheet MIME on /login/partner). Viewport 1291x775.
- ZNW-141: add the five Tab stops from a fresh home page (Facebook, LinkedIn, X, Instagram,
  Threads) and "no skip-to-content link found". Keep the ticket's own ### style.

Step 2 – Redraft three, show them to me, and save nothing yet:
- ZNW-177: do NOT write "the same body". Quote the exact request body SEC-012 sends, then its
  response entry, using this form: "Request body sent by the guard test: <exact body>.
  Response errors[] entry: <exact text>."
- ZNW-149: in the existing Actual Result, change "with a reasonable policy" to "with a policy".
  Add the 7 October 'unsafe-inline' lines (script-src and style-src, quoted exactly).
- ZNW-155: put the path-form steps and the 7 October measurements FIRST. Move the old hash
  steps and the 30 September results below, under the label
  "Earlier measurement, 30 September 2026 (hash addresses, no longer served)".
  End with: "The blank render at /products/invented-thing is recorded in ZNW-165."

Rules: evidence only, no severity, no fixes, no cause guessing, never "still",
no "every/all" without proof. Do not delete the comments already posted on ZNW-149 and
ZNW-155 (waiting for my lead's decision).
```

## Changelog
- 2026-10-07: written after the weekly usage limit interrupted the Jira edits
