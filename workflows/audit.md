---
name: audit
description: Security audit, integrity check, and health scan
---
# Audit Directive
## Below are what agent MUST do:
- **AUTO-RUN**: Proactively execute terminal commands and tool calls needed to fulfill this directive without waiting for confirmation unless explicit user input is required.
- **SECRETS**: Scan for exposed credentials, API keys, or sensitive data patterns.
- **INTEGRITY**: Verify imports, symlinks, and references are valid and functional.
- **BLOAT**: Identify duplicate code, unused dependencies, or redundant files.
- **HEALTH**: Check for outdated packages, deprecated APIs, or security vulnerabilities.
- **REPORT**: Provide actionable findings with severity levels and remediation steps.