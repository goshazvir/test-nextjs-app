# Project Context

> Auto-loaded in every Claude Code session

---

## ⚠️ HOW TO USE PLUGIN SKILLS

**Plugin:** `claude-daemon` (9 skills for TypeScript/Next.js development)

**How skills work:**
1. Skills = Skill.md files in `~/.claude/plugins/marketplaces/claude-daemon-marketplace/skills/[skill-name]/Skill.md`
2. To activate: READ the Skill.md file and follow its instructions EXACTLY
3. NEVER use manual commands when a skill exists

### Quick Reference

| User Request | Skill Path |
|--------------|------------|
| "lint", "fix code" | `skills/lint-and-fix/Skill.md` |
| "check typescript", "ts health" | `skills/typescript-health-check/Skill.md` |
| "unused imports" | `skills/detect-unused-imports/Skill.md` |
| "show routes", "map structure" | `skills/route-map-nextjs/Skill.md` |
| "check cyrillic" | `skills/no-cyrillic-check/Skill.md` |
| "audit zustand" | `skills/zustand-store-audit/Skill.md` |
| "check api contracts" | `skills/api-contract-checker/Skill.md` |
| "test api", "smoke tests" | `skills/api-smoke/Skill.md` |
| "show prs" | `skills/gh-pr-digest/Skill.md` |

**Execution pattern:**
1. Read `~/.claude/plugins/marketplaces/claude-daemon-marketplace/skills/[skill-name]/Skill.md`
2. Output activation message (e.g., "🎯 [claude-daemon skill: lint-and-fix activated]")
3. Follow ALL instructions from Skill.md
4. Use ONLY allowed tools from Skill.md
5. Format output per Skill.md spec

---

## Skills Overview

**Code Quality:**
- `lint-and-fix` - ESLint autofix
- `typescript-health-check` - TS config & error analysis
- `detect-unused-imports` - Find dead code

**Next.js:**
- `route-map-nextjs` - Map App Router structure

**State:**
- `zustand-store-audit` - Store best practices check

**API:**
- `api-contract-checker` - Validate endpoint contracts
- `api-smoke` - Quick smoke tests (requires dev server :3000)

**GitHub:**
- `gh-pr-digest` - PR summaries (requires GITHUB_TOKEN)

**Quality:**
- `no-cyrillic-check` - Enforce English-only

---

## Installation

**Auto-install:** Enabled via `.claude/settings.json`

**Manual (fallback):**
```bash
claude plugin marketplace add GeoLabsAI/claude-daemon
claude plugin install claude-daemon@claude-daemon-marketplace
```

Repository: https://github.com/GeoLabsAI/claude-daemon
