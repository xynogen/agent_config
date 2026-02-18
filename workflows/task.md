---
name: task
description: Task Orchestration and Ambiguity Resolution
---
# Task Orchestration Directive

## Below are what agent MUST do:
- **AUTO-RUN**: Proactively execute terminal commands and tool calls needed to fulfill this directive without waiting for confirmation unless explicit user input is required.
- **CONTEXT**: Synthesize intent from recent history. Link "orders" to the last proposed `/plan` or `/suggest`.
- **RESOLVE**: Identify and fill "Human Ambiguities" (e.g., 'fix that' → define 'that' via `/audit` or `/search` context).
- **IMPACT**: Calculate implications of the task. Identify affected documentation, tests, and downstream dependencies. Flag potential breaking changes.
- **PRE-FLIGHT**: Audit the current system state. Confirm paths, versions, and permissions. Map dependency chains that could be broken.

## Phased Execution
Order tasks logically:
1. **Backup** — Snapshot state if destructive changes are planned.
2. **Execution** — Implement changes in bite-sized steps (2-5 minutes each).
3. **Configuration** — Apply config changes after code changes are verified.
4. **Validation** — Run `/test` and `/verify` to confirm correctness.

**CAUTION**: Run one chunk at a time. Verify the outcome of Step N before starting Step N+1.

## Bite-Sized Task Structure
Each task step MUST be atomic and verifiable:
```
Step N: [Action]
- Files: [exact paths]
- Command: [exact command to run]
- Expected: [what success looks like]
```

## Batch Execution Pattern
For multi-task plans, execute in batches of 3 tasks:
1. Execute batch → verify each step → report what was done
2. Say: "Ready for feedback." and wait
3. Apply feedback if any → execute next batch → repeat

## Stop-When-Blocked Rule
If a blocker is hit mid-batch (missing dependency, failing test, unclear instruction):
- **STOP immediately** — do not guess or work around it
- Report the blocker with exact context
- Ask for clarification before continuing

## Report
Provide the Final Answer using the Response Contract, detailing exactly what was performed.
