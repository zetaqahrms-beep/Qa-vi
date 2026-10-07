# Qa-vi: Prompt Engineering Workspace

This repo is a prompt engineering workspace for several projects. All project data lives in `projects/`.

## Projects

| Tag | Folder | What it is |
|---|---|---|
| `[SaaS]` | `projects/zeta-saas-website/` | Zeta SaaS website |
| `[HRMS]` | `projects/zeta-hrms-mobile/` | Zeta HRMS mobile app (Flutter) |
| `[Finance]` | `projects/finance-ai/` | Finance AI: independent study, website + mobile app |

## How to work in this repo

- The user tags messages with a project tag. Before writing a prompt for a project, read its `project-brief.md` and `notes.md`.
- Never mix details between projects.
- When writing a prompt, explain the reasoning behind each part (role, context, input tags, rules, output format, examples).
- When the user says "save it", write the prompt to `projects/<project>/prompts/<name>.md` using the template in `projects/README.md`, add a line to that project's `notes.md`, then commit and push.
- Keep `project-brief.md` updated when the user shares new project details.
