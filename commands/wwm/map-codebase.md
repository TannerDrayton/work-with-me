---
name: wwm:map-codebase
description: Let's understand your codebase together by creating structured documentation
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
Let's analyze your existing codebase together using specialized mapper agents to create structured documentation.

Each mapper agent explores a focus area and **writes documents directly** to `.planning/codebase/`. I'll coordinate them and keep our conversation focused, while they do the deep analysis work.

Output: .planning/codebase/ folder with 7 structured documents that help us understand your codebase together.
</objective>

<execution_context>
@~/.claude/work-with-me/workflows/map-codebase.md
</execution_context>

<context>
Focus area: $ARGUMENTS (optional - if you provide one, I'll tell the agents to focus on that specific subsystem)

**Load project state if exists:**
I'll check for .planning/STATE.md - loads context if we've already initialized the project

**This command can run:**
- Before /wwm:new-project (brownfield codebases) - let's understand existing code first
- After /wwm:new-project (greenfield codebases) - updates as our code evolves
- Anytime to refresh our understanding of the codebase
</context>

<when_to_use>
**Let's use map-codebase when:**
- Starting with existing code (brownfield) - we need to understand it first
- Code has changed significantly - time to refresh our understanding
- You're new to this codebase - I'll help you get oriented
- Planning major refactoring - let's understand current state first
- Our STATE.md references seem outdated

**We can skip map-codebase when:**
- Starting from scratch (greenfield) - nothing to map yet
- Very small codebase (<5 files) - we can just read it together
</when_to_use>

<process>
1. Check if .planning/codebase/ already exists (I'll offer to refresh or skip)
2. Create .planning/codebase/ directory structure
3. Spawn 4 parallel wwm-codebase-mapper agents:
   - Agent 1: tech focus → writes STACK.md, INTEGRATIONS.md
   - Agent 2: arch focus → writes ARCHITECTURE.md, STRUCTURE.md
   - Agent 3: quality focus → writes CONVENTIONS.md, TESTING.md
   - Agent 4: concerns focus → writes CONCERNS.md
4. Wait for agents to complete, collect confirmations (NOT document contents)
5. Verify all 7 documents exist with line counts
6. Commit codebase map
7. I'll suggest next steps (typically: /wwm:new-project or /wwm:plan-phase)
</process>

<success_criteria>
- [ ] .planning/codebase/ directory created
- [ ] All 7 codebase documents written by mapper agents
- [ ] Documents follow template structure
- [ ] Parallel agents completed without errors
- [ ] You know what we should do next
</success_criteria>
