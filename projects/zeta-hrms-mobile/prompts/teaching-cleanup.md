# Teaching cleanup (ZetaMobile Claude Code)

Same prompt as the SaaS cleanup (done, commit 0618e1a in that repo), with mobile-specific protections.

```
Cleanup task: remove teaching instructions from this project.

Why: English coaching, prompt-writing tips and JavaScript lessons now happen in a
separate Claude account. Here I only want project work. Removing them saves tokens.

Step 1 – Find (dry run, change nothing):
Search all AI instruction files: CLAUDE.md (every level), .claude/ (settings, skills,
agents, commands), memory files, and any docs that give instructions to AI
(including starter prompts like docs/PROMPT-NEW-CHAT-MOBILE.md, if it exists).
List every place that asks you to:
- teach or correct my English
- give prompt-writing tips
- teach JavaScript or coding
- add a coaching / lesson section after answers
For each one, show: file, line number, exact text.

Step 2 – Ask:
If a line mixes teaching with a real project rule, or you are not sure, ask me.
Do not guess.

Step 3 – Remove only what I approve. Do NOT touch:
- prompts used for real work (test prompts, pagination prompts, report prompts)
- project rules: test accounts only, never push, never change HRMS admin configuration,
  never touch production, never print credentials, QA mailbox filter, no Jira unasked
- code conventions, evidence and CANNOT TELL rules
- the answer style: plain English, short sentences, chat summary first

Step 4 – Report the files changed and lines removed. Commit locally with the message
"Remove teaching instructions (moved to separate account)". Do not push.

From now on in this project: no English, prompt or coding lessons.
```
