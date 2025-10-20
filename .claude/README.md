# Claude Code Configuration

## Plugin Setup

This project uses `claude-daemon` plugin with auto-install via `settings.json`:

```json
{
  "extraKnownMarketplaces": {
    "claude-daemon-marketplace": {
      "source": {
        "source": "github",
        "repo": "GeoLabsAI/claude-daemon"
      }
    }
  }
}
```

**New team members:** See [SETUP.md](SETUP.md) for quick start guide.

## Skills (9 total)

**Code Quality**
- `lint-and-fix` - ESLint autofix
- `typescript-health-check` - TS compilation check
- `detect-unused-imports` - Find unused imports

**Next.js**
- `route-map-nextjs` - Map all routes

**State**
- `zustand-store-audit` - Store audit

**API**
- `api-contract-checker` - Verify contracts
- `api-smoke` - Smoke tests

**GitHub**
- `gh-pr-digest` - PR summaries

**Guards**
- `no-cyrillic-check` - English-only

## Usage

Ask Claude naturally - skills activate automatically.

## Files

- `settings.json` - Marketplace config (committed)
- `settings.local.json` - Local permissions (gitignored)
- `SETUP.md` - Team setup guide
- `README.md` - This file

**Source:** https://github.com/GeoLabsAI/claude-daemon
