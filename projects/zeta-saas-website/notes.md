# Notes & Decisions

Running log of decisions, ideas and context for this project, newest first.
Claude reads this at the start of a chat to pick up where we left off.

<!-- Format:
## YYYY-MM-DD
- Decision / idea / open question
-->

## Pending for Monday 2026-10-12
- Run `prompts/resume-security-and-recheck.md` in Claude Code (SEC-002 frame fix, SEC-001 missing-header names, C3 + C9 drafts, ZNW-165 + ZNW-141 comments).
- Ask developer whether /pricing -> /zetacontact redirect is intended (C7).
- Browser extension retest: home page Part C (forms) and Part D (layout, footer, testimonial '·' spacing, 24 footer links), then runs 2-7.

## 2026-10-07
- External report (UID/DEF) re-checked in Claude Code: C1 deep-link blank = ZNW-165; C2 mobile bubble, C5 favicon, C8 cold start NOT reproduced; C3 one unnamed icon button NEW; C4 skip link = same root as ZNW-141; C6 = ZNW-169; C7 /pricing redirect is configured on purpose (ask dev before raising); C9 verbose parser error NEW (was SEC-005). Lesson: external reports carried severity, fixes and cause guesses; 3 of 9 findings were false.
- Security test messages trimmed to observed facts only (commit d0eb821). SEC-002 framing test found to be a false positive (onload fires on blocked frames too); fix via Playwright frame API (frame URL chrome-error:// vs heading visible). Lesson: a test can be confidently wrong — when a test fails but its own output contradicts the failure, suspect the detection method.
- Full retest via browser extension, home page split into Parts A-D. Part A bugs: 'Manufacture' industry label (hover), 'Construction' label cut off 20px at 1291 viewport. Part B: hero buttons and side nav 'not working' were FALSE — manual clicks work; extension mouse clicks get swallowed inside .home-scroller. Lesson for bug-hunt prompt: inside the page body use keyboard (Tab + Enter); confirm click failures manually before reporting.
- Rule change: form submissions with marked test data now allowed (teams agreed to receive test emails). Sign-in still not allowed until confirmed. Full-site retest moved to the browser extension (Claude Code session limit).
- Security work done: guard tests SEC-010 (ZNW-175) and SEC-011 (ZNW-176) in tests/site/security.spec.js, commit 75f32e5 (local). Framework convention for open bugs: assert correct behaviour, ZNW key in failure message, test fails until fixed (no test.fail, no skip). ZNW-149 and ZNW-155 comments posted. SEC-005 untested.
- Raised ZNW-175 (Swagger public, SEC-002) and ZNW-176 (backend Server/X-Powered-By, SEC-004). SEC-003 added as comment on ZNW-149. SEC-006: comment on ZNW-155 with path-form measurements; /products/invented-thing blank render = ZNW-165. Guard tests planned in tests/site/security.spec.js.
- Lesson: every AI draft round added small overclaims ("every response", "unchanged", unobserved "Try it out"). Add an UNMEASURED rule to the bug-hunt prompt.
- Security checks (passive): SEC-001/002/003/004/006 confirmed; SEC-005 not tested. Plan: one ticket for CSP (001+003), separate tickets for 002 and 004 (backend only), 006 = duplicate of ZNW-155 (Deferred). SEC-005: read swagger.json for POST endpoints first, or reuse original evidence.
- Teaching instructions removed from the SaaS project (commit 0618e1a, local). Proven prompt findings moved to `docs/WHAT-WORKS-IN-EXTENSION-PROMPTS.md` in that repo.
- Proven finding (2026-09-01): for the browser-extension AI, prompts built on facts and quotes get better results than prompts asking for code. Apply this to every bug-hunt prompt.
- Brief filled in from intake session. Work here is black-box QA of the live site (Playwright + browser-extension AI bug hunts + Jira ZNW).
- Prompt priority: 1) bug-hunt prompt (`docs/PROMPT-*.md`) to cut measurement errors, 2) Jira bug report writer.
- Framework stays on the tester's machine for now (personal tool, run by hand).
- Project folder created.
