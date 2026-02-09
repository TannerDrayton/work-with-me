---
name: wwm:map-codebase
description: Analyze codebase and create structured documentation
argument-hint: "[optional: specific area to map, e.g., 'api' or 'auth']"
allowed-tools:
  - Read
  - Bash
  - Glob
  - Grep
  - Write
  - Task
---

<objective>
Analyze existing codebase using specialized mapper agents to create structured documentation.

Each mapper agent explores a focus area and **writes documents directly** to `.planning/codebase/`. Orchestrator coordinates agents and collects confirmations.

Output: .planning/codebase/ folder with 7 structured documents for planning reference.
</objective>

<execution_context>
@~/.claude/work-with-me/workflows/map-codebase.md
</execution_context>

<context>
Focus area: $ARGUMENTS (optional — agents focus on that specific subsystem if provided)

**Load project state if exists:**
Check for .planning/STATE.md — loads context if project is initialized.

**This command can run:**
- Before /wwm:new-project (brownfield codebases) — understand existing code first
- After /wwm:new-project (greenfield codebases) — updates as code evolves
- Anytime to refresh codebase understanding
</context>

<when_to_use>
**Use map-codebase when:**
- Starting with existing code (brownfield) — need to understand it first
- Code has changed significantly — time to refresh
- New to the codebase — get oriented quickly
- Planning major refactoring — understand current state first
- STATE.md references seem outdated

**Skip map-codebase when:**
- Starting from scratch (greenfield) — nothing to map
- Very small codebase (<5 files) — just read it directly
</when_to_use>

<process>
1. Check if .planning/codebase/ already exists (offer refresh or skip)
2. Create .planning/codebase/ directory structure
3. Spawn 4 parallel wwm-codebase-mapper agents:
   - Agent 1: tech focus → writes STACK.md, INTEGRATIONS.md
   - Agent 2: arch focus → writes ARCHITECTURE.md, STRUCTURE.md
   - Agent 3: quality focus → writes CONVENTIONS.md, TESTING.md
   - Agent 4: concerns focus → writes CONCERNS.md
4. Wait for agents to complete, collect confirmations (NOT document contents)
5. Verify all 7 documents exist with line counts
6. Commit codebase map
7. Suggest next steps (typically: /wwm:new-project or /wwm:plan-phase)
</process>

<success_criteria>
- [ ] .planning/codebase/ directory created
- [ ] All 7 codebase documents written by mapper agents
- [ ] Documents follow template structure
- [ ] Parallel agents completed without errors
- [ ] Next steps suggested
</success_criteria>
