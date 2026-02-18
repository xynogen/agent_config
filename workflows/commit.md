---
name: commit
description: Guidelines for splitting, editing, and maintaining commits in Conventional Commit style
---
# Conventional Commit Management Directive
## Below are what agent MUST do:
- **AUTO-RUN**: Proactively execute terminal commands and tool calls needed to fulfill this directive without waiting for confirmation unless explicit user input is required.
- **PROTECT**: NO commits without explicit permission. NO secrets, binaries, or unrelated changes.
- **FORMAT**: Use `feat`, `fix`, `chore`, or `refactor`. Scope MUST be clear. Message MUST be concise and descriptive.
- **SPLIT**: Separate changes by path/module and functionality into self-contained commits.
- **VALIDATE**: Ensure all tests/lints pass before finalizing. Review for clarity and correctness.
- **MAINTAIN**: Reorganize, squash, or amend commits to preserve integrity. WIP commits MUST be removed.
- **NON-GOAL**: DO NOT assume intent or alter unrelated history.

## Artifact Definition
- **Artifact**: any file, commit message, or metadata created to fulfill a commit-related directive.
