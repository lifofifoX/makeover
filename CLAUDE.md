# CLAUDE.md

Project guidance for Claude Code.

## Overview

Makeover is a skill for redesigning applications with distinctive, production-grade visual themes. It browses your running app, captures real UI, and generates theme proposals showing exactly how themes look on your actual content.

## Dependencies

1. **frontend-design plugin**: `/plugins add claude-plugins-official/frontend-design`
2. **Playwright MCP**: `claude mcp add playwright npx @playwright/mcp@latest`

## Commands

```
/makeover propose [count] [hints...]   # Browse app, generate proposals
/makeover propose [count] --wild       # Experimental themes
/makeover implement [names]            # Implement approved theme
```

## Workflow

1. Ask for app URL (default: localhost:3000)
2. Browse with Playwright, discover pages
3. Ask user which pages to include (AskUserQuestion)
4. Capture real DOM/content from each page
5. Detect styling system inline
6. Generate proposals using actual app content

## File Reading Order

| Phase | Always Read | Conditional |
|-------|-------------|-------------|
| Propose (normal) | CRAFT.md, PROPOSE.md, LIBRARY.md | MOTION.md (if N3+ motion) |
| Propose (--wild) | WILD_CRAFT.md, PROPOSE.md, LIBRARY.md § Wild Concepts | MOTION.md (if N3+ motion) |
| Implement | IMPLEMENT.md, proposal HTML | — |

**Context Note:** CRAFT.md is the single source for design rules. PROPOSE.md references but does not duplicate.

## Key Files

- `SKILL.md` — Full workflow, presets, inspiration hints
- `CRAFT.md` — Elite design principles (normal proposals)
- `WILD_CRAFT.md` — **Permission-first wild philosophy** (--wild proposals)
- `LIBRARY.md` — DNA tables, 130+ color palettes, typography, inspiration sources
- `MOTION.md` — N1-N9 motion levels, effect catalog

## Critical Constraints

**DNA System**: Every theme declares `H#-L#-G#-D#-C#-N#` (see LIBRARY.md for options)

**Elite Design (CRAFT.md)**:
- Spacing: only 4/8/12/16/24/32/48/64px
- No pure #000/#FFF (use #0a0a0a, #FAFAFA)
- Typography: curly quotes (" "), proper dashes (– —), letterspacing on caps
- One accent color, ≤10% of surface
- Anti-AI: no uniform shadows, same radii everywhere, decorative bloat

**Banned Patterns**: Inter font, blue accents, generic card grids, top-bar + logo left/links right

**Banned Themes (Tier 1 — never default to)**: Brutalist, Terminal/Hacker, NASA/Mission Control, Zine/Punk, Medical/Clinical, Arcade/Casino. See PROPOSE.md for full tiered list.

**Proposals Must**:
- Cite 2-3 specific references from LIBRARY.md
- Use REAL app content (no placeholders, no emoji substitutes)
- Use REAL images from app (or realistic images from internet if app has none)
- Embed MAKEOVER_METADATA comment for implementation
- Differ by ≥3 DNA positions if multiple
- Pass squint test (hierarchy obvious when blurred)
- Pass removal test (nothing unnecessary)

**Implementation Must**:
- Extract metadata from proposal HTML
- Copy CSS directly from proposal's `<style>` tags
- Match preview exactly
