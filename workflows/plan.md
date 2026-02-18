---
name: plan
description: Write detailed, bite-sized implementation plans before touching code
---
# Plan Directive

## Overview
Write a comprehensive implementation plan assuming the engineer has zero context for the codebase and questionable taste. Document everything they need: which files to touch, exact code, exact commands, and how to verify each step. DRY. YAGNI. TDD. Frequent commits.

## Below are what agent MUST do:

### Plan Document Header
Every plan MUST start with this header:
```markdown
# [Feature Name] Implementation Plan

**Goal:** [One sentence describing what this builds]
**Architecture:** [2-3 sentences about approach]
**Tech Stack:** [Key technologies/libraries]
---
```

### Task Structure
Each task MUST follow this format:
```markdown
### Task N: [Component Name]

**Files:**
- Create: `exact/path/to/file.py`
- Modify: `exact/path/to/existing.py`
- Test: `tests/exact/path/to/test.py`

**Step 1: Write the failing test**
[exact test code]

**Step 2: Run test to verify it fails**
Run: `[exact command]`
Expected: FAIL with "[expected error message]"

**Step 3: Write minimal implementation**
[exact implementation code]

**Step 4: Run test to verify it passes**
Run: `[exact command]`
Expected: PASS

**Step 5: Commit**
`git commit -m "feat: [description]"`
```

### Rules
- **Exact file paths always** — no vague "add to the service file"
- **Complete code in plan** — not "add validation here"
- **Exact commands with expected output** — no ambiguity
- **Bite-sized steps** — each step is 2-5 minutes of work
- **TDD enforced** — every task starts with a failing test

### Save and Handoff
- Save plan to `docs/plans/YYYY-MM-DD-<feature-name>.md`
- Commit the plan document
- Announce: "Plan complete. Ready to execute via `/task`."
