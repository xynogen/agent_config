---
name: review
description: Architectural Review and Quality Assurance
---
# Review Directive

## Below are what agent MUST do:

### Pre-Review Checklist (Before Requesting Review)
- **SELF-REVIEW**: Read every changed line. Would you be embarrassed to show this?
- **TESTS**: All tests pass. New behavior has tests. No skipped tests without explanation.
- **SCOPE**: Changes are limited to what was planned. No unrelated modifications.
- **DOCS**: Public interfaces are documented. README updated if behavior changed.
- **CLEAN**: No debug logs, commented-out code, or TODO left behind.

### Review Phases
- **PHASES**: Verify logic follows proper ordering and dependencies.
- **IDEMPOTENCY**: Ensure scripts and commands are safely repeatable without side effects.
- **CONSISTENCY**: Check adherence to project naming, structure, and style conventions.
- **INTEGRITY**: Verify imports, links, and cross-module dependencies are intact.
- **SECURITY**: No hardcoded secrets, credentials, or unsafe inputs.
- **YAGNI**: If a feature or endpoint is unused, flag it for removal — don't "implement it properly."

### Receiving Review Feedback
- **NO PERFORMATIVE AGREEMENT**: Never say "Great point!", "You're absolutely right!", or "Thanks for catching that!" Just fix it or push back. Actions speak.
- **UNDERSTAND FIRST**: Before implementing anything, restate the requirement in your own words. If any item is unclear, stop and ask — do not implement the ones you understand while deferring the unclear ones.
- **VERIFY BEFORE IMPLEMENTING**: Check if the suggestion is technically correct for *this* codebase. Does it break existing functionality? Does it conflict with prior architectural decisions?
- **YAGNI CHECK**: If a reviewer suggests adding a feature, grep the codebase first. If nothing calls it, push back: "This isn't used anywhere — remove it (YAGNI)?"
- **PUSH BACK WHEN WRONG**: Use technical reasoning, not defensiveness. Reference working tests or code. Involve the user if it's architectural.
- **IMPLEMENTATION ORDER**: Fix blocking issues first (crashes, security), then simple fixes (typos), then complex refactors. Test each fix individually.

### Acknowledging Correct Feedback
```
✅ "Fixed. [Brief description of what changed]"
✅ "Good catch — [specific issue]. Fixed in [location]."
✅ [Just fix it and show the diff]

❌ "You're absolutely right!"
❌ "Great point!"
❌ "Thanks for catching that!"
```

### Verdict
- **VERDICT**: Provide a clear **Pass / Pass with Suggestions / Fail** report with technical rationale.
- **FAIL** means: critical logic errors, missing tests, security issues, or broken contracts.
- **Pass with Suggestions** means: works correctly but has improvement opportunities.
