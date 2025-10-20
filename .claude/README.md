# Claude Code Configuration

This directory contains Claude Code configuration for this project.

## Plugin Setup

This project uses the **claude-daemon** plugin for TypeScript/Next.js development automation.

### Auto-Installation (Recommended)

**Good news!** The plugin should install automatically when you:

1. Open this project in Claude Code
2. Trust the workspace when prompted
3. Accept the plugin installation prompt

The `.claude/settings.json` file in this project tells Claude Code to automatically:
- Add the `claude-daemon-marketplace` from GitHub
- Install and enable the `claude-daemon` plugin

**No manual installation needed!** Just restart Claude Code after trusting the workspace.

### Manual Setup (If Auto-Install Doesn't Work)

If you're setting up for the first time or auto-install didn't work:

```bash
# 1. Add the marketplace
claude plugin marketplace add GeoLabsAI/claude-daemon

# 2. Install the plugin
claude plugin install claude-daemon@claude-daemon-marketplace

# 3. Restart Claude Code to activate skills
```

### Verification

Check that everything is installed correctly:

```bash
# List configured marketplaces
claude plugin marketplace list
# Should show: claude-daemon-marketplace

# Check project settings
cat .claude/settings.json
# Should show enabledPlugins with claude-daemon
```

### Do I Need to Reinstall Each Session?

**NO!** Common misconceptions:

❌ **Wrong**: "I need to install the plugin every time I start Claude Code"
✅ **Correct**: Plugin is installed once globally and persists forever

❌ **Wrong**: "The plugin is stored in my project"
✅ **Correct**: Plugin is stored globally in `~/.claude/plugins/`, project just enables it

❌ **Wrong**: "Each project needs its own copy"
✅ **Correct**: All projects share the same global plugin installation

### What is a "Session"?

A **session** in Claude Code is:
- Each time you run the `claude` command in terminal
- When you exit (type `exit` or Ctrl+D) and run `claude` again = **new session**
- When you use `--resume` or `--continue` = same conversation, but still loads fresh environment

**Important**: Plugins load **every session** but DON'T need to be **installed** every session!

### What Happens Between Sessions

```
First Time Ever (Installation):
1. Open project → Trust workspace
2. Claude detects settings.json → Prompts to install plugin
3. Accept → Plugin downloads to ~/.claude/plugins/
4. Plugin installed globally ✅

Every Session After (Including "exit" + "claude"):
1. Run 'claude' command → New session starts
2. Claude loads plugins from ~/.claude/plugins/
3. Claude reads .claude/settings.json → Enables configured plugins
4. Skills work immediately ✅ (plugin was already installed)
```

**Example**:
```bash
$ claude                    # Session 1 starts, plugin loads
> exit                      # Session 1 ends

$ claude                    # Session 2 starts, plugin loads again
                           # NO installation needed - already installed!
```

### Troubleshooting

**Skills not working?**
- Make sure you installed the plugin (not just the marketplace)
- Restart Claude Code after installation
- Check that `.claude/settings.json` has `"claude-daemon@claude-daemon-marketplace": true`

**Plugin not found?**
```bash
# Re-install the plugin
claude plugin uninstall claude-daemon
claude plugin install claude-daemon@claude-daemon-marketplace
```

**Think you're reinstalling every session?**
- Check if plugin is actually installed: `claude plugin marketplace list`
- If it's installed, you don't need to reinstall
- The feeling of "reinstalling" might be Claude just re-enabling the plugin for the project

## How Skills Work

Skills are **automatically activated** by Claude based on your natural language requests. You don't need to invoke them manually.

### Available Skills (9 total)

#### Code Quality
- **lint-and-fix**: "Check code quality", "lint my code", "fix linting errors"
- **typescript-health-check**: "Check TypeScript", "validate types", "TS health"
- **detect-unused-imports**: "Find unused imports", "clean up imports"

#### Next.js
- **route-map-nextjs**: "Show routes", "map app structure", "list endpoints"

#### State Management
- **zustand-store-audit**: "Audit stores", "check Zustand", "validate stores"

#### API
- **api-contract-checker**: "Check API contracts", "validate endpoints"
- **api-smoke**: "Test API", "smoke test endpoints" (requires dev server on :3000)

#### GitHub
- **gh-pr-digest**: "Show PRs", "PR digest", "list pull requests" (requires GITHUB_TOKEN)

#### Quality Guards
- **no-cyrillic-check**: "Check for Cyrillic", "enforce English only"

### Usage Examples

Just ask Claude in natural language:

```
You: "Check TypeScript health"
Claude: [Automatically uses typescript-health-check skill]

You: "Lint my code"
Claude: [Automatically uses lint-and-fix skill]

You: "Show me all routes"
Claude: [Automatically uses route-map-nextjs skill]
```

## Configuration Files

### settings.json
Project-level plugin configuration. This file is committed to Git so all team members use the same setup.

### settings.local.json (optional)
Local overrides for personal preferences. This file is in `.gitignore` and won't be committed.

## Plugin Location

The plugin code is installed globally at:
```
~/.claude/plugins/marketplaces/claude-daemon-marketplace/
```

But it's activated per-project through `.claude/settings.json`.

## Hooks

The plugin provides pre-commit hooks that automatically:
- Run ESLint with autofix
- Check TypeScript compilation
- Detect Cyrillic characters
- Stage fixes automatically

Hook configuration: `~/.claude/plugins/marketplaces/claude-daemon-marketplace/hooks/onPreCommit.yaml`

## Templates

Available templates:
- **commit-message.md**: Conventional commits format guide
- **pr-description.md**: Pull request template with checklists

Templates location: `~/.claude/plugins/marketplaces/claude-daemon-marketplace/templates/`

## Updating the Plugin

To get the latest version:

```bash
# 1. Uninstall current version
claude plugin uninstall claude-daemon

# 2. Remove marketplace (clears cache)
claude plugin marketplace remove claude-daemon-marketplace

# 3. Re-add marketplace
claude plugin marketplace add GeoLabsAI/claude-daemon

# 4. Reinstall plugin
claude plugin install claude-daemon@claude-daemon-marketplace

# 5. Restart Claude Code
```

## Support

- Plugin Repository: https://github.com/GeoLabsAI/claude-daemon
- Issues: https://github.com/GeoLabsAI/claude-daemon/issues
- Claude Code Docs: https://docs.claude.com/en/docs/claude-code
