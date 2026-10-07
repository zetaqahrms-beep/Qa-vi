# Prompt Library

Prompts for each project, saved here so they survive beyond any single chat.

## Projects

| Tag | Folder | What it is |
|---|---|---|
| `[SaaS]` | `zeta-saas-website/` | Zeta SaaS website |
| `[HRMS]` | `zeta-hrms-mobile/` | Zeta HRMS mobile app (Flutter) |
| `[Finance]` | `finance-ai/` | Finance AI: independent study, website + mobile app |

## How to use

1. Start chat messages with the project tag, e.g. `[HRMS] write a prompt for ...`.
2. Each folder has a `project-brief.md`. Keep it up to date; every prompt for that project builds on it.
3. When a prompt is final, save it as its own file in the project folder (e.g. `zeta-hrms-mobile/leave-summary.md`).
4. In a new chat, point Claude at `prompts/<project>/` to pick up where you left off.

## Prompt file template

Every saved prompt uses this layout:

```markdown
# <Prompt name>

**Purpose:** what this prompt does
**Used by:** person / backend code / app feature
**Model notes:** anything model-specific (optional)

## Prompt
<the prompt itself, with {{variables}} for inputs>

## Example input / output
<one or two real examples>

## Edge cases tested
- ...

## Changelog
- YYYY-MM-DD: first version
```
