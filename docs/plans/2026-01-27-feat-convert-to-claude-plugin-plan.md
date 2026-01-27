---
title: Convert Makeover Skill to Claude Plugin
type: feat
date: 2026-01-27
---

# Convert Makeover Skill to Claude Plugin

## Overview

Convert the makeover skill from a local skill installation to a distributable Claude Code plugin. Users install via `/plugins add lifo/makeover`, with auto-updates on invocation.

## Problem Statement

Currently users must manually clone the repo to `~/.claude/skills/makeover`. No update mechanism exists - users must `git pull` manually. This creates friction for adoption and version drift across users.

## Proposed Solution

Restructure repo to follow Claude Code plugin conventions:
- Add `.claude-plugin/plugin.json` manifest
- Keep skill files in `skills/makeover/` directory
- Publish as GitHub-based marketplace
- Document frontend-design dependency (kept separate per user preference)

## Technical Approach

### Directory Structure Change

**Current:**
```
makeover/
├── SKILL.md
├── README.md
├── DESIGN_SYSTEM.md
├── DNA_CODES.md
├── MOTION.md
├── ORCHESTRATE.md
├── IMPLEMENT.md
├── PROPOSE_NORMAL.md
├── PROPOSE_WILD.md
├── TEMPLATE.md
├── lib/
│   └── browser.md
├── orchestrate/
│   ├── reference.md
│   ├── capture.md
│   └── ui-elements.md
└── templates/
    ├── proposal.html
    └── index.html
```

**Target:**
```
makeover/
├── .claude-plugin/
│   └── plugin.json          # NEW: Plugin manifest
├── skills/
│   └── makeover/            # MOVED: All skill files here
│       ├── SKILL.md
│       ├── DESIGN_SYSTEM.md
│       ├── DNA_CODES.md
│       ├── MOTION.md
│       ├── ORCHESTRATE.md
│       ├── IMPLEMENT.md
│       ├── PROPOSE_NORMAL.md
│       ├── PROPOSE_WILD.md
│       ├── TEMPLATE.md
│       ├── lib/
│       ├── orchestrate/
│       └── templates/
├── README.md                # UPDATE: New installation instructions
├── LICENSE                  # NEW: MIT or similar
└── CHANGELOG.md             # NEW: Version history
```

### plugin.json

```json
{
  "name": "makeover",
  "version": "1.0.0",
  "description": "Redesign any app with distinctive, production-grade visual themes using real UI content",
  "author": {
    "name": "lifo",
    "url": "https://github.com/lifo"
  },
  "repository": "https://github.com/lifo/makeover",
  "license": "MIT",
  "keywords": ["design", "frontend", "themes", "ui", "redesign"]
}
```

### Dependency Handling

No formal plugin dependency system exists. Handle via:

1. **Pre-flight check in ORCHESTRATE.md** - Before spawning proposal agents, check if frontend-design plugin responds
2. **Clear error message** - "Required: frontend-design plugin. Install: `/plugins add claude-plugins-official/frontend-design`"
3. **Browser automation detection** - lib/browser.md already handles this with fallback chain

### Auto-Update Mechanism

GitHub-based plugins auto-update per marketplace settings. User controls via:
- `/plugin` → Marketplaces tab → Toggle auto-update
- Default: disabled for third-party marketplaces
- Updates apply on next Claude Code session

### Path Resolution

Plugin files cached at `~/.claude/plugins/cache/lifo/makeover/[version]/`

All relative paths in skill files resolve relative to skill root. Current paths like `./DESIGN_SYSTEM.md` will resolve correctly because:
- Skill files move to `skills/makeover/`
- References stay relative to that directory
- `tmp/makeover/` stays in user's project CWD (not affected)

## Acceptance Criteria

- [ ] `.claude-plugin/plugin.json` exists with required fields
- [ ] All skill files under `skills/makeover/`
- [ ] `/plugins add lifo/makeover` installs successfully
- [ ] `/makeover propose 3` works after installation
- [ ] Missing frontend-design shows clear error message
- [ ] README documents new installation method
- [ ] CHANGELOG tracks version 1.0.0

## Implementation Phases

### Phase 1: Restructure

- [x] Create `.claude-plugin/plugin.json`
- [x] Create `skills/makeover/` directory
- [x] Move all .md files to `skills/makeover/`
- [x] Move `lib/`, `orchestrate/`, `templates/` to `skills/makeover/`
- [x] Update any hardcoded paths in skill files
- [x] Add LICENSE file (MIT)
- [x] Create CHANGELOG.md

### Phase 2: Dependency Checks

- [x] Add pre-flight check in ORCHESTRATE.md for frontend-design
- [x] Verify lib/browser.md fallback chain works from plugin context
- [ ] Test with missing dependencies - confirm clear error messages

### Phase 3: Documentation

- [x] Update README.md with plugin installation
- [x] Add migration section for existing local skill users
- [x] Document dependency installation commands
- [x] Add troubleshooting section

### Phase 4: Testing

- [ ] Install plugin via `/plugins add lifo/makeover`
- [ ] Run `/makeover propose 3` on test app
- [ ] Run `/makeover implement {name}`
- [ ] Verify `tmp/makeover/` creates in project CWD
- [ ] Test auto-update by pushing change and re-invoking

## Migration Path

For users with existing `~/.claude/skills/makeover`:

1. Install plugin: `/plugins add lifo/makeover`
2. Remove local skill: `rm -rf ~/.claude/skills/makeover`
3. Existing `tmp/makeover/` data in projects remains compatible

## Risks

| Risk | Mitigation |
|------|------------|
| Path resolution breaks | Test all relative paths after restructure |
| Users have both local + plugin | Document migration, plugin takes precedence |
| frontend-design version mismatch | Pin to known-working version in docs |
| Breaking changes in updates | Use semantic versioning, document in CHANGELOG |

## Success Metrics

- Users can install with single command
- No manual `git pull` needed for updates
- Clear error messages for missing dependencies
- Zero breaking changes for existing users

## References

### Internal
- Current skill: `SKILL.md`, `ORCHESTRATE.md`
- Browser detection: `lib/browser.md`
- Recent refactor: commit `c7d6cb6` (flexible browser support)

### External
- [Claude Code Plugins Reference](https://code.claude.com/docs/en/plugins-reference)
- [Plugin Manifest Schema](https://code.claude.com/docs/en/plugins)
- [Skills Documentation](https://code.claude.com/docs/en/skills)

## Open Questions

1. **GitHub username** - Plan assumes `lifo`. Confirm or provide actual username for repo URL.
2. **License choice** - Plan assumes MIT. Confirm or specify preferred license.
3. **Marketplace strategy** - Single-plugin marketplace (`lifo/makeover`) or multi-plugin (`lifo/plugins` with makeover inside)?
