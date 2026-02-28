# Code Snippets: oracle-skills-cli

## 1. Universal Installation Script (`install.sh`)
This script checks for prerequisites and maps the installation.

```bash
#!/bin/bash
# Oracle Skills Installer - One command to install everything

# 0. Check & install Claude Code
if ! command -v claude &> /dev/null; then
  curl -fsSL https://claude.ai/install.sh | bash
fi

# 1. Check & install bun
if ! command -v bun &> /dev/null; then
  curl -fsSL https://bun.sh/install | bash
  export PATH="$HOME/.bun/bin:$PATH"
fi

# Fetching latest stable version...
LATEST_TAG=$(curl -s https://api.github.com/repos/Soul-Brews-Studio/oracle-skills-cli/releases/latest | grep '"tag_name"' | cut -d'"' -f4)

~/.bun/bin/bunx --bun \
  oracle-skills@github:Soul-Brews-Studio/oracle-skills-cli#$LATEST_TAG \
  install -g -y
```

## 2. Setting Up Agent Permissions (Example)
The repository extensively uses local config injection (`.claude/settings.local.json`) to give agents expanded bash capabilities.

```json
{
  "permissions": {
    "allow": [
      "Bash(gh:*)", "Bash(ghq:*)", "Bash(git:*)",
      "Bash(bun:*)", "Bash(bunx:*)", "Bash(mkdir:*)",
      "Bash(rg:*)", "Bash(date:*)", "Bash(curl:*)",
      "Bash(*ψ/*)", "Bash(*psi/*)",
      "Skill(learn)", "Skill(trace)", "Skill(awaken)",
      "Skill(rrr)", "Skill(recap)", "Skill(project)"
    ]
  }
}
```

## 3. Skill Metadata Format (`src/skills/awaken/SKILL.md`)
All skills adhere to this markdown format.

```markdown
---
name: awaken
description: Guided Oracle birth and awakening ritual (~15 min). Use when creating a new Oracle in a fresh repo. Orchestrates /learn and /trace for philosophy discovery.
---
# /awaken
...
```
