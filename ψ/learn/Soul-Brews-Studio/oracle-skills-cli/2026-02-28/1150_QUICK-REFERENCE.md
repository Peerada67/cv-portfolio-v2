# Quick Reference: oracle-skills-cli

## What it does
`oracle-skills-cli` is a cross-agent framework that installs a standardized set of "Oracle Skills" (like `/learn`, `/trace`, `/awaken`, `/project`) into 12+ different AI coding platforms including Gemini, Claude Code, Cursor, Windsurf, Aider, and OpenCode. These skills give agents long-term context retention, workspace standardization, and self-organization blueprints.

## Installation
**Automatic One-Command (Mac/Linux/WSL):**
```bash
curl -fsSL https://raw.githubusercontent.com/Soul-Brews-Studio/oracle-skills-cli/main/install.sh | bash
```

**Using Bun manually:**
```bash
~/.bun/bin/bunx --bun oracle-skills@github:Soul-Brews-Studio/oracle-skills-cli#main install -g -y
```

## Key Features
1. **Universal Skill Distribution**: Automatically detects active coding agents and installs the `.md` skill recipes in their respective hidden folders (e.g. `~/.gemini/antigravity/skills/`).
2. **Oracle Architecture Support**: Uses `ghq` structured repositories and a dedicated `ψ/` (Psi) workspace directory for persisting memory across isolated coding sessions.
3. **Core Workflow Commands**:
   - `/learn [url]`: Clones a repo and reads it in parallel, mapping its architecture.
   - `/trace [project]`: Searches git history and system memory to find context about previously built tools.
   - `/awaken`: Initializes and aligns a fresh AI agent to the local philosophy workspace.
   - `/rrr`: Standardized session wrap-up and retrospective memory caching.

## Usage Patterns
Once the skills are installed in the `.gemini/antigravity/skills` directory, any prompt explicitly calling out a command like `/learn https://github.com/foo/bar` will instruct the agent to load the `learn/SKILL.md` tool sequence and execute it iteratively.
