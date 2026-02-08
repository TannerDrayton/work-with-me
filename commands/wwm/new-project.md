---
name: wwm:new-project
description: Let's set up a new project together with thoughtful planning
argument-hint: "[--auto]"
allowed-tools:
  - Read
  - Bash
  - Write
  - Task
  - AskUserQuestion
---
<context>
**Flags:**
- `--auto` — Automatic mode. After config questions, runs research → requirements → roadmap without further interaction. Expects idea document via @ reference.
</context>

<objective>
Let's initialize a new project together through: questioning → research (optional) → requirements → roadmap.

**We'll create:**
- `.planning/PROJECT.md` — our project context
- `.planning/config.json` — your workflow preferences
- `.planning/research/` — domain research (optional)
- `.planning/REQUIREMENTS.md` — scoped requirements
- `.planning/ROADMAP.md` — phase structure
- `.planning/STATE.md` — project memory

**After this command:** Run `/wwm:plan-phase 1` to start working together.
</objective>

<execution_context>
@~/.claude/work-with-me/workflows/new-project.md
@~/.claude/work-with-me/references/questioning.md
@~/.claude/work-with-me/references/ui-brand.md
@~/.claude/work-with-me/templates/project.md
@~/.claude/work-with-me/templates/requirements.md
</execution_context>

<process>
Execute the new-project workflow from @~/.claude/work-with-me/workflows/new-project.md end-to-end.
Preserve all workflow gates (validation, approvals, commits, routing).
</process>
