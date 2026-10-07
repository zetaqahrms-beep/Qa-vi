# Qa-vi: Prompt Engineering Workspace

This repo is a prompt engineering workspace for several projects. All project data lives in `projects/`.

## Projects

| Tag | Folder | What it is |
|---|---|---|
| `[SaaS]` | `projects/zeta-saas-website/` | Zeta SaaS marketing website (Angular); black-box QA with Playwright + AI bug hunts, Jira ZNW |
| `[HRMS]` | `projects/zeta-hrms-mobile/` | ZetaMobile: Appium + WebdriverIO test framework for the ESS Android app (Flutter), Jira MAB |
| `[Finance]` | `projects/finance-ai/` | Finance AI: independent study, website + mobile app |

## How to work in this repo

- The user tags messages with a project tag. Before writing a prompt for a project, read its `project-brief.md` and `notes.md`.
- Never mix details between projects.
- When writing a prompt, explain the reasoning behind each part (role, context, input tags, rules, output format, examples).
- When the user says "save it", write the prompt to `projects/<project>/prompts/<name>.md` using the template in `projects/README.md`, add a line to that project's `notes.md`, then commit and push.
- Keep `project-brief.md` updated when the user shares new project details.

## Who this is for

- The user is the only reader of the output. This workspace is for planning prompts and tracking where each project is heading.
- The user does prompt engineering from a separate Claude account; the actual projects are worked on elsewhere.
- Default response format: a short chat summary first, then details only if needed.
