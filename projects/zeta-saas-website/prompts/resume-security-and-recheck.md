# Resume: security fixes + re-check follow-ups

**Purpose:** Restart the paused SaaS work in a fresh Claude Code session (previous session context was lost).
**Used by:** Claude Code in the SaaS project repo.

## Prompt

```
Resume paused work. The previous session's context is lost, so first check the real state.

Step 0 – State check (read only):
Run git status and git log -5. Tell me whether the SEC-001 and SEC-002 edits in
tests/site/security.spec.js are committed, uncommitted, or missing.

Step 1 – SEC-002 frame test (false positive: onload fires on blocked frames too).
Fix it with Playwright's frame API, not by reading the frame from the parent (a cross-origin
frame is unreadable from the parent whether it loaded or was blocked):
- find the iframe's frame object and record its URL (a frame blocked by the frame policy
  lands on chrome-error://chromewebdata/)
- check whether the heading "One Platform for Every Business Operation" is visible inside it
Framed = heading visible. Blocked = chrome-error URL and no heading.
Run it once, quote the frame URL and result. It should pass today (X-Frame-Options: SAMEORIGIN).

Step 2 – SEC-001 message: print the names of the headers actually missing (today expected:
content-security-policy only, ZNW-149).

Step 3 – Run the whole security spec once, quote every failure message exactly, commit locally.

Step 4 – Re-check follow-ups (draft only, create nothing):
- C3 ticket: one icon-only control on the home page has no text, aria-label, title or
  aria-labelledby. Add what it is and where it is on screen, with a screenshot. No screen-reader
  claims. Expected Result: "The control carries an accessible name."
- C9 ticket: POST /ERPSaasUIBackend/api/contact with body {not valid json returns 400 and
  errors[] contains the JSON parser's text (character, path, line, byte position).
  Re-measure with one request only.
- Comment for ZNW-165: the four addresses /country/ae, /login/customer, /login/partner,
  /products/crm render blank on direct visit; quote the console error about the module
  script served as text/html. Evidence only.
- Comment for ZNW-141: the first five Tab stops from a fresh home page; no skip link found.
House format: STEPS TO REPRODUCE / ACTUAL RESULT / EXPECTED RESULT, about 200 words,
no severity, no fixes, no cause guessing, no "every/all" without proof, never "still".
Search ZNW and data/jiraReported.mjs for duplicates first.

Step 5 – Stop and show me everything. Create nothing in Jira until I reply with exact items.
After approval: raise, add guard tests per this framework's convention, register in
data/jiraReported.mjs, run once, commit locally.

Do NOT raise C7 (/pricing redirect is configured on purpose; waiting on the developer).
```

## Changelog
- 2026-10-07: written after the Claude Code session context was lost
