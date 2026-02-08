---
name: wwm:discuss-phase
description: Work together to clarify your vision for a phase through conversation before we plan
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
Let's explore implementation decisions together - what we decide here guides our work ahead.

**How it works:**
1. I'll analyze the phase to identify gray areas (UI, UX, behavior, etc.)
2. You select which areas you'd like to discuss
3. We'll explore each area together until you're satisfied
4. I'll create a CONTEXT.md that captures our decisions to guide the work ahead

**Output:** `{phase}-CONTEXT.md` — clear decisions that help us work together without needing to re-discuss
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
5. **Explore each area together** — 4 questions per area, then I'll check: "More questions about [area], or ready to move to the next?"
6. **Write CONTEXT.md** — Sections match areas we discussed
7. Offer next steps (research or plan together)

**CRITICAL: Scope guardrail**
- Phase boundary from ROADMAP.md is FIXED
- Our discussion clarifies HOW to implement, not WHETHER to add more
- If you suggest new capabilities: "That sounds like its own phase - let me note it so we can plan for it later."
- I'll capture deferred ideas — we won't lose them, but we won't act on them now

**Domain-aware gray areas:**
Gray areas depend on what's being built. I'll analyze the phase goal:
- Something users SEE → layout, density, interactions, states
- Something users CALL → responses, errors, auth, versioning
- Something users RUN → output format, flags, modes, error handling
- Something users READ → structure, tone, depth, flow
- Something being ORGANIZED → criteria, grouping, naming, exceptions

I'll generate 3-4 **phase-specific** gray areas, not generic categories.

**Probing depth:**
- I'll ask 4 questions per area before checking in
- "More questions about [area], or move to next?"
- If more → I'll ask 4 more, check again
- After all areas → "Ready to create our context document?"

**What I'll handle (you don't need to decide):**
- Technical implementation details
- Architecture choices
- Performance concerns
- Scope expansion questions
</process>

<success_criteria>
- Gray areas identified through intelligent analysis
- You chose which areas to discuss
- Each selected area explored until you're satisfied
- Scope creep redirected to deferred ideas
- CONTEXT.md captures our decisions, not vague vision
- You know what's next in our collaboration
</success_criteria>
