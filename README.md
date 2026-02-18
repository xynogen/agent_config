# agent_config

A portable, agent-agnostic configuration layer that enforces consistent behaviour across AI coding assistants. Drop it into any project or point your agent at it to get structured workflows, a strict operating specification, and slash-command-style directives out of the box.

## What's inside

| Path | Purpose |
|---|---|
| `SOP.md` | **System Operating Procedure** — the master system prompt. Defines core rules: no hallucination, no sudo, sequential thinking, response contract, task-mode system, and communication style. |
| `workflows/` | **16 slash-command workflows** — each is a self-contained `.md` directive the agent loads on demand. |

### Workflows

| Command | Description |
|---|---|
| `/brainstorm` | Design-before-code exploration |
| `/plan` | Bite-sized TDD implementation plans |
| `/task` | Multi-phase task orchestration |
| `/debug` | Root-cause analysis + self-annealing |
| `/test` | TDD red-green-refactor cycle |
| `/verify` | Evidence-based completion check |
| `/review` | Architectural code QA |
| `/finish` | Branch completion & cleanup |
| `/commit` | Conventional Commit management |
| `/bootstrap` | Project scaffolding from docs |
| `/audit` | Security, integrity & health scan |
| `/search` | Deep logic discovery |
| `/suggest` | Multi-dimensional optimisation |
| `/explain` | Technical deconstruction |
| `/ui` | UI/UX design guidance |
| `/tldr` | Tech-only summary |

---

## Integration

### Antigravity

Antigravity reads a `MEMORY[user_global]` block from its settings. Paste the contents of `SOP.md` there, then point the workflows directory at `.agent/workflows/` in your project.

```bash
# In your project root
mkdir -p .agent/workflows
cp /path/to/agent_config/workflows/*.md .agent/workflows/
```

Antigravity auto-discovers `.agent/workflows/*.md` files and exposes them as slash commands. The `SOP.md` content goes into **Settings → User Rules**.

---

### OpenCode

OpenCode supports a project-level `AGENTS.md` and a user-level `~/.config/opencode/AGENTS.md`.

```bash
# Project-level (one project)
cp /path/to/agent_config/SOP.md ./AGENTS.md

# User-level (all projects)
mkdir -p ~/.config/opencode
cp /path/to/agent_config/SOP.md ~/.config/opencode/AGENTS.md
```

For workflows, OpenCode reads any markdown files you reference in your prompt or place in a known docs directory. A simple convention is:

```bash
mkdir -p .agent/workflows
cp /path/to/agent_config/workflows/*.md .agent/workflows/
```

Then invoke a workflow by telling the agent: *"Follow the instructions in `.agent/workflows/plan.md`"* or use the slash-command name if your OpenCode version supports custom commands.

---

### Claude Code (Anthropic)

Claude Code reads `CLAUDE.md` at the project root and `~/.claude/CLAUDE.md` globally.

```bash
# Project-level
cp /path/to/agent_config/SOP.md ./CLAUDE.md

# Global (applies to every project)
mkdir -p ~/.claude
cp /path/to/agent_config/SOP.md ~/.claude/CLAUDE.md
```

Workflows can be stored anywhere and referenced inline. A clean convention:

```bash
mkdir -p .claude/workflows
cp /path/to/agent_config/workflows/*.md .claude/workflows/
```

Add this line to your `CLAUDE.md` so Claude knows where to look:

```markdown
## Workflows
Workflow directives live in `.claude/workflows/`. Load the relevant file when a slash command is invoked.
```

---

### Codex CLI (OpenAI)

Codex CLI reads `AGENTS.md` at the project root and `~/.codex/AGENTS.md` globally.

```bash
# Project-level
cp /path/to/agent_config/SOP.md ./AGENTS.md

# Global
mkdir -p ~/.codex
cp /path/to/agent_config/SOP.md ~/.codex/AGENTS.md
```

Codex also supports **skills** — structured directories under `~/.agents/skills/`. Each workflow can be a skill:

```bash
# Convert all workflows to Codex skills
for f in /path/to/agent_config/workflows/*.md; do
  name=$(basename "$f" .md)
  mkdir -p "$HOME/.agents/skills/$name"
  cp "$f" "$HOME/.agents/skills/$name/SKILL.md"
done
```

Each `SKILL.md` already contains the required `name` and `description` YAML frontmatter, so Codex will discover them automatically.

---

### Cursor / Windsurf / Aider / other agents

Most agents that support a custom system prompt or a project-level markdown context file follow the same pattern:

1. **System prompt** → paste `SOP.md` content into the agent's system prompt or rules field.
2. **Workflows** → copy `workflows/*.md` into a directory the agent can read (`.agent/workflows/`, `docs/`, etc.) and reference them in your prompt.

---

## Keeping it in sync

Clone this repo once and symlink the files instead of copying, so updates propagate automatically:

```bash
# Example: symlink for Claude Code (global)
mkdir -p ~/.claude
ln -sf /path/to/agent_config/SOP.md ~/.claude/CLAUDE.md

# Example: symlink workflows for Antigravity
mkdir -p /your/project/.agent
ln -sf /path/to/agent_config/workflows /your/project/.agent/workflows
```

---

## Customising

- **Add a workflow**: create a new `.md` file in `workflows/` with YAML frontmatter (`name`, `description`) and step-by-step instructions.
- **Modify the SOP**: edit `SOP.md` — changes apply everywhere the file is symlinked.
- **Override per-project**: create a local `AGENTS.md` / `CLAUDE.md` that extends or overrides the global one.
