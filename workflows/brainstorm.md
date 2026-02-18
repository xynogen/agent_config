---
name: brainstorm
description: Design exploration and spec refinement before any implementation begins
---
# Brainstorm Directive

## Hard Gate
```
DO NOT write any code, scaffold any project, or take any implementation action
until you have presented a design and the user has approved it.
```
This applies to EVERY request, regardless of perceived simplicity.

## Below are what agent MUST do:

### Step 1: Explore Context
- Check existing files, docs, and recent git commits.
- Understand what already exists before proposing anything new.

### Step 2: Ask Clarifying Questions
- Ask ONE question at a time. Do not overwhelm with multiple questions.
- Prefer multiple-choice when possible.
- Focus on: purpose, constraints, success criteria, and edge cases.
- Continue until you understand the full scope.

### Step 3: Propose 2-3 Approaches
- Present distinct approaches with trade-offs.
- Lead with your recommended option and explain WHY.
- Apply YAGNI ruthlessly — remove unnecessary features from all proposals.

### Step 4: Present Design for Approval
- Present the design in sections scaled to complexity.
- Cover: architecture, components, data flow, error handling, testing strategy.
- Ask for approval after each section. Revise if needed.

### Step 5: Write Design Doc
- Save the validated design to `docs/plans/YYYY-MM-DD-<topic>-design.md`.
- Commit the design document to git.

### Step 6: Transition to Implementation
- Invoke the `/plan` workflow to create a detailed implementation plan.
- Do NOT start coding directly. `/plan` is the next step.

## Key Principles
- **One question at a time** — Don't overwhelm with multiple questions
- **YAGNI ruthlessly** — Remove unnecessary features from all designs
- **Explore alternatives** — Always propose 2-3 approaches before settling
- **Incremental validation** — Present design, get approval before moving on
