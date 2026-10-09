# Projects

Project data and prompts, saved here so they survive beyond any single chat.

## Folder layout

```
projects/<project>/
├── project-brief.md   what the project is, users, tone, stack, rules
├── notes.md           running log of decisions and ideas (newest first)
├── prompts/           finished prompts, one file each
└── examples/          sample inputs/outputs used to test prompts
```

## Projects

| Tag | Folder | What it is |
|---|---|---|
| `[SaaS]` | `zeta-saas-website/` | Zeta SaaS website |
| `[HRMS]` | `zeta-hrms-mobile/` | Zeta HRMS mobile app (Flutter) |
| `[Finance]` | `finance-ai/` | Finance AI: independent study, website + mobile app |

## How to use

1. Start chat messages with the project tag, e.g. `[HRMS] write a prompt for ...`.
2. Each folder has a `project-brief.md`. Keep it up to date; every prompt for that project builds on it.
3. When a prompt is final, save it in the project's `prompts/` folder (e.g. `zeta-hrms-mobile/prompts/leave-summary.md`).
4. Record decisions and ideas in `notes.md`.
5. In a new chat, Claude reads `CLAUDE.md` automatically and finds `projects/<project>/` to pick up where you left off.

## Prompt file template

Every saved prompt uses this layout:

```markdown
# <Prompt name>

**Purpose:** what this prompt does
**Used by:** person / backend code / app feature
**Run with:** model + effort (see CLAUDE.md "Model choice"), fresh session yes/no

## Prompt
<the prompt itself, with {{variables}} for inputs>

## Example input / output
<one or two real examples>

## Edge cases tested
- ...

## Changelog
- YYYY-MM-DD: first version
```
