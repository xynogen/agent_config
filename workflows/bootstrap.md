---
name: bootstrap
description: Generic project and tool scaffolding using documentation for best practices
---
# Bootstrap & Scaffolding Directive
## Below are what agent MUST do:
- **AUTO-RUN**: Proactively execute terminal commands and tool calls needed to fulfill this directive without waiting for confirmation unless explicit user input is required.
- **RESEARCH**: Use documentation to find authoritative setup steps for the target language/framework.
- **INIT**: Execute standard initialization commands (e.g., `npm init -y`, `cargo init`, `go mod init`).
- **STRUCTURE**: Create standard project layouts (src, tests, docs). Ensure architectural consistency.
- **DEPENDENCIES**: Install core libraries using project managers. Pin versions.
- **ENVIRONMENT**: Generate `.env.example` and ensure required local environment variables are documented.
- **TOOLING**: Initialize project-specific linting, formatting, and CI/CD configurations.
