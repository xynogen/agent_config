---
name: debug
description: Root-Cause Analysis and self-annealing procedure for error resolution
---
# Debug & Anneal Directive

## The Iron Law
```
NO FIXES WITHOUT ROOT CAUSE INVESTIGATION FIRST
```
If Phase 1 is not complete, you CANNOT propose fixes.

## Below are what agent MUST do:

### Phase 1: Root Cause Investigation
- **READ**: Read error messages and stack traces completely. Note line numbers, file paths, error codes.
- **REPRODUCE**: Reproduce the error consistently. If not reproducible → gather more data, do NOT guess.
- **CHANGES**: Check recent changes (git diff, recent commits, new dependencies, config changes).
- **EVIDENCE**: In multi-component systems, add diagnostic logging at each boundary BEFORE proposing fixes. Run once to gather evidence, THEN analyze.
- **TRACE**: Trace data flow backward through the call stack to find the original trigger. Fix at source, not symptom.

### Phase 2: Pattern Analysis
- **EXAMPLES**: Find working examples of similar code in the codebase.
- **COMPARE**: Compare working vs broken. List every difference, however small.
- **DEPENDENCIES**: Understand what config, environment, or assumptions the code relies on.

### Phase 3: Hypothesis and Testing
- **HYPOTHESIZE**: State clearly: "I think X is the root cause because Y." Write it down.
- **TEST MINIMALLY**: Make the SMALLEST possible change to test the hypothesis. One variable at a time.
- **VERIFY**: Did it work? Yes → Phase 4. No → form a NEW hypothesis. Do NOT stack fixes.

### Phase 4: Implementation
- **TEST FIRST**: Create a failing test reproducing the bug BEFORE writing the fix.
- **FIX**: Implement a single, targeted fix addressing the root cause. No "while I'm here" changes.
- **VERIFY**: Confirm test passes and no regressions via `/test`.
- **ANNEAL**: If the error was due to missing rules, update the appropriate Directive.

## Escalation Rule
- If 3+ fixes have failed: **STOP**. Question the architecture. Discuss with the user before attempting more fixes. This is a wrong architecture, not a wrong hypothesis.

## Red Flags — STOP and Return to Phase 1
- "Quick fix for now, investigate later"
- "Just try changing X and see if it works"
- "It's probably X, let me fix that"
- "I don't fully understand but this might work"
- "One more fix attempt" (when already tried 2+)
- Each fix reveals a new problem in a different place
