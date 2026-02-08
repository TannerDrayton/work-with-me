---
name: wwm:list-phase-assumptions
description: Let me share my assumptions about a phase so you can correct them
argument-hint: "[phase]"
allowed-tools:
  - Read
  - Bash
  - Grep
  - Glob
---

<objective>
Let me analyze a phase and share my assumptions about technical approach, implementation order, scope boundaries, risk areas, and dependencies.

Purpose: Help you see what I'm thinking BEFORE we plan - so you can correct me early if my assumptions are wrong.
Output: Conversational output only (no file creation) - ends with "What do you think?" prompt
</objective>

<execution_context>
@~/.claude/work-with-me/workflows/list-phase-assumptions.md
</execution_context>

<context>
Phase number: $ARGUMENTS (required)

**Load project state first:**
@.planning/STATE.md

**Load roadmap:**
@.planning/ROADMAP.md
</context>

<process>
1. Validate phase number argument (error if missing or invalid)
2. Check if phase exists in roadmap
3. Follow list-phase-assumptions.md workflow:
   - Analyze roadmap description
   - Surface assumptions about: technical approach, implementation order, scope, risks, dependencies
   - Present assumptions clearly
   - Prompt "What do you think?"
4. Gather your feedback and offer next steps
</process>

<success_criteria>
- Phase validated against roadmap
- Assumptions surfaced across five areas
- You're prompted for feedback
- You know next steps (discuss context, plan phase, or correct my assumptions)
</success_criteria>
