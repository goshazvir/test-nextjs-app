# Team Setup Guide

## Prerequisites

- Claude Pro subscription
- Claude Code installed
- Repository cloned

## Setup (2 Steps)

### 1. Clone Repository
```bash
git clone <repository-url>
cd test-nextjs-app
```

### 2. Trust Repository

When Claude Code prompts: **"Do you trust this repository?"** → Click **"Trust"**

**Done!** Plugin installs automatically.

## Verify (Optional)

```bash
claude plugin marketplace list
# Should show: claude-daemon-marketplace
```

## Usage

Just ask Claude naturally:
- "Check TypeScript health"
- "Lint and fix code"
- "Check for Cyrillic characters"

## Troubleshooting

**Plugin not installed?**
```bash
claude plugin marketplace add GeoLabsAI/claude-daemon
claude plugin install claude-daemon
```

**Skills not working?**
1. Did you trust the repository?
2. Restart Claude Code

## Update Plugin

```bash
cd ~/.claude/plugins/marketplaces/claude-daemon-marketplace
git pull
```

---

**Plugin:** https://github.com/GeoLabsAI/claude-daemon
