---
name: search
description: Deep Logic Discovery and Project Context Mapping
---
# Deep Context Search Directive
## Below are what agent MUST do:
- **AUTO-RUN**: Proactively execute terminal commands and tool calls needed to fulfill this directive without waiting for confirmation unless explicit user input is required.
- **SCAN**: Use `grep` for content and `glob` for structure. Group by intent (Logic, Config, Test).
- **TRACE**: Identify how data flows through the matches. Note all call sites and dependencies.
- **IDENTIFY**: Highlight inconsistencies, anti-patterns, or deviations from the project standard.
- **MAP**: Provide a technical map of the implementation across the repository.
- **REPORT**: Concise technical summary of findings with direct file references.
