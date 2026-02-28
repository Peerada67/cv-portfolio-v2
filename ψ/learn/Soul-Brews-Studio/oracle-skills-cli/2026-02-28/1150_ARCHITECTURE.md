# Architecture Overview: oracle-skills-cli

## Directory Structure
The repository is structured to manage and distribute generalized skills for various AI agents (Claude Code, OpenCode, Cursor, and more).

```
oracle-skills-cli/
├── install.sh          # Universal installation script that proxies the CLI
├── src/
│   └── skills/         # The core content: a collection of skill folders
│       ├── _template/  # Template for creating new skills
│       ├── awaken/     # Skill to orchestrate Oracle birth/awakening
│       ├── learn/      # Deep dive codebase learning skill
│       ├── trace/      # Context tracing skill
│       ├── rrr/        # Retrospective logging skill
│       └── ...         # ~20+ other structured skills
└── README.md           # Extensive documentation on supported agents and usage
```

## Entry Points
1. **`install.sh`**: A shell script meant to be piped to `bash` via `curl`. It handles the installation of dependencies like `bun`, `ghq`, and configures the default agent environment.
2. **NPM Executable**: The repository can be called via `bunx --bun oracle-skills@github:Soul-Brews-Studio/oracle-skills-cli#main` to install skills directly.

## Core Abstractions
- **Skill Pattern**: Every skill is defined as a directory containing a `SKILL.md` file with a standardized YAML frontmatter describing its name and purpose. It acts as a modular extension of system prompts.
- **Oracle Philosophy**: Prioritizes the AI acting as an "external brain" mapping memory to files iteratively instead of being a generic stateless worker.
- **Universal Installer**: Maps the same collection of skills to over 12+ different AI agent environments by identifying directories like `~/.claude/skills/`, `~/.gemini/antigravity/skills/`, etc.

## Dependencies
- **Bun**: Used as the primary fast execution engine for the CLI utility layer.
- **ghq**: Used extensively in skills like `/learn` and `/trace` for managing local clones of external git repositories uniformly inside a `ψ/` (psi) workspace.
