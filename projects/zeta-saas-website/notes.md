# Notes & Decisions

Running log of decisions, ideas and context for this project, newest first.
Claude reads this at the start of a chat to pick up where we left off.

<!-- Format:
## YYYY-MM-DD
- Decision / idea / open question
-->

## 2026-10-07
- Teaching instructions removed from the SaaS project (commit 0618e1a, local). Proven prompt findings moved to `docs/WHAT-WORKS-IN-EXTENSION-PROMPTS.md` in that repo.
- Proven finding (2026-09-01): for the browser-extension AI, prompts built on facts and quotes get better results than prompts asking for code. Apply this to every bug-hunt prompt.
- Brief filled in from intake session. Work here is black-box QA of the live site (Playwright + browser-extension AI bug hunts + Jira ZNW).
- Prompt priority: 1) bug-hunt prompt (`docs/PROMPT-*.md`) to cut measurement errors, 2) Jira bug report writer.
- Framework stays on the tester's machine for now (personal tool, run by hand).
- Project folder created.
