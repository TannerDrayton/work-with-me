---
name: wwm:discuss-phase
description: Clarify phase vision through conversation before planning
argument-hint: "<phase>"
allowed-tools:
  - Read
  - Write
  - Bash
  - Glob
  - Grep
  - AskUserQuestion
---

<objective>
Explore implementation decisions before planning — what gets decided here guides execution.

**Flow:**
1. Analyze the phase to identify gray areas (UI, UX, behavior, etc.)
2. User selects which areas to discuss
3. Explore each area until user is satisfied
4. Create CONTEXT.md capturing decisions to guide execution

**Output:** `{phase}-CONTEXT.md` — locked decisions, deferred ideas, and discretion areas
</objective>

<execution_context>
@~/.claude/work-with-me/workflows/discuss-phase.md
@~/.claude/work-with-me/templates/context.md
</execution_context>

<context>
Phase number: $ARGUMENTS (required)

**Load project state:**
@.planning/STATE.md

**Load roadmap:**
@.planning/ROADMAP.md
</context>

<process>
1. Validate phase number (error if missing or not in roadmap)
2. Check if CONTEXT.md exists (offer update/view/skip if yes)
3. **Analyze phase** — Identify domain and generate phase-specific gray areas
4. **Present gray areas** — Multi-select: which would you like to discuss? (NO skip option)
5. **Explore each area** — 4 questions per area, then check: "More questions about [area], or ready to move to the next?"
6. **Write CONTEXT.md** — Sections match areas discussed
7. Offer next steps (research or plan)

**CRITICAL: Scope guardrail**
- Phase boundary from ROADMAP.md is FIXED
- Discussion clarifies HOW to implement, not WHETHER to add more
- If user suggests new capabilities: "That sounds like its own phase — noting it as a deferred idea."
- Deferred ideas are captured, not lost — but not acted on now

**Domain-aware gray areas:**
Gray areas depend on what's being built. Analyze the phase goal:
- Something users SEE → layout, density, interactions, states
- Something users CALL → responses, errors, auth, versioning
- Something users RUN → output format, flags, modes, error handling
- Something users READ → structure, tone, depth, flow
- Something being ORGANIZED → criteria, grouping, naming, exceptions

Generate 3-4 **phase-specific** gray areas, not generic categories.

**Probing depth:**
- Ask 4 questions per area before checking in
- "More questions about [area], or move to next?"
- If more → ask 4 more, check again
- After all areas → "Ready to create the context document?"

**Claude handles (user doesn't decide):**
- Technical implementation details
- Architecture choices
- Performance concerns
- Scope expansion questions
</process>

<success_criteria>
- Gray areas identified through intelligent analysis
- User chose which areas to discuss
- Each selected area explored until user is satisfied
- Scope creep redirected to deferred ideas
- CONTEXT.md captures concrete decisions, not vague vision
- Next steps are clear
</success_criteria>
