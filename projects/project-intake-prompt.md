# Project Intake Prompt

**Purpose:** Collect everything needed to fill in a project's `project-brief.md`.
**Used by:** You, once per project. Paste it into a chat (Claude Code opened on the project's codebase works best).
**Output:** A completed brief in the same format as `projects/<project>/project-brief.md`.

## How to use

1. Open a chat. If the project has code, open Claude Code **on that project's repo** so it can read the code itself.
2. Replace `{{PROJECT_NAME}}` and `{{ONE_LINE_DESCRIPTION}}` below, then paste the whole prompt.
3. Answer its questions. Short answers are fine; "don't know yet" is fine.
4. Copy the final brief back into this chat and say **"save it"**.

## Prompt

```
You are a senior product analyst and prompt engineer. Your job is to build a complete
project brief that will be used as context for every AI prompt written for this project.
A good brief means future prompts produce accurate, on-brand, correctly formatted output
without the user re-explaining the project each time.

<project>
Name: {{PROJECT_NAME}}
Description: {{ONE_LINE_DESCRIPTION}}
</project>

Follow these steps in order:

STEP 1: Investigate before asking.
If you have access to this project's files or codebase, explore them first: README,
package/dependency files (pubspec.yaml, package.json, requirements.txt, etc.), folder
structure, config, routes/screens, API clients, localization files and any docs.
Fill in everything you can find yourself. Do not ask me things the code already answers.
If you have no file access, skip to Step 2.

STEP 2: Interview me for the gaps.
Ask only about what you could not find. Ask at most 4 questions per message, grouped by
topic, and wait for my answers before continuing. Prefer multiple-choice or short-answer
questions. If an answer is vague, ask one follow-up; if I say "don't know yet", record it
as an open question and move on.

STEP 3: Output the brief.
When every section is filled or marked as an open question, output the brief in exactly
the format below, inside one markdown code block, with nothing after it.

Rules:
- Facts you found in files: state them plainly. Facts you inferred: add "(inferred, confirm)".
- Never invent details. Unknown = "TODO: <the specific question>".
- Never include secrets, API keys, passwords, server URLs with credentials, or real
  personal/employee/financial data. Describe data by its shape, not its values
  (e.g. "employee record: id, name, department, leave balance").
- Keep each bullet to one or two lines.

<brief_format>
# Project Brief: {{PROJECT_NAME}}

## Overview
- **What it is:**
- **Problem it solves:**
- **Current status:** (idea / in development / live; what exists today)

## Users
- **Who uses it:** (roles)
- **Their goals:**
- **Regions & languages:**

## Where AI is used
- **AI tasks:** (e.g. writing code, test cases, UI copy, in-app AI features, chatbots, analysis)
- **Who consumes AI output:** (a person reads it / app code parses it)
- **Most urgent prompt to build first:**

## Voice & style
- **Tone:**
- **Words / claims to avoid:**

## Technical
- **Platforms:** (web / iOS / Android / backend)
- **Tech stack:** (languages, frameworks, state management, database, hosting)
- **Code conventions:** (patterns, folder structure, naming, error handling)
- **APIs & integrations:**
- **Key data entities:** (name: main fields)

## Output formats
- **Formats needed:** (JSON schema, markdown, HTML, code, plain text)

## Rules & constraints
- **Must always:**
- **Must never:**
- **Compliance / privacy:** (personal data, financial advice disclaimers, etc.)

## Open questions
- (everything still marked TODO, as a list)
</brief_format>

Start with Step 1 now.
```

## Why it's built this way

| Part | Why |
|---|---|
| Role + purpose paragraph | Tells the model *why* the brief matters, so it aims for completeness and accuracy, not a quick summary. |
| `<project>` tags | Keeps your inputs separate from the instructions. |
| "Investigate before asking" | Reads the code first so you don't type out things like your tech stack. |
| Max 4 questions per message | Avoids a wall of 30 questions; keeps the interview easy to answer. |
| "(inferred, confirm)" + TODO rules | Stops the model from guessing and makes guesses visible to you. |
| No secrets / no real data rule | HRMS and finance projects hold sensitive data; the brief only needs its shape. |
| Exact `<brief_format>` | Output drops straight into `project-brief.md` with no reformatting. |
| "Start with Step 1 now" | Makes the model begin working instead of replying "Sure, ready when you are!" |

## Changelog
- 2026-10-07: first version
