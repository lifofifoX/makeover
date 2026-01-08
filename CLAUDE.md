# CLAUDE.md

Project guidance for Claude Code.

## Overview

Makeover redesigns applications with distinctive, production-grade visual themes. It browses your running app, captures real UI, and generates theme proposals showing exactly how themes look on your actual content.

## Dependencies

1. **frontend-design plugin**: `/plugins add claude-plugins-official/frontend-design`
2. **Playwright MCP**: `claude mcp add playwright npx @playwright/mcp@latest`

## Commands

```
/makeover propose [count] [hints...]   # Browse app, generate proposals
/makeover propose [count] --wild       # Experimental themes (structural transformation)
/makeover implement [names]            # Implement approved theme
```

## File Structure

```
CLAUDE.md              # This file — routing and overview
SKILL.md               # User-facing skill definition
CAPTURE.md             # Playwright workflow (orchestrator only)
PROPOSE_NORMAL.md      # Complete normal mode guide (agents read this)
PROPOSE_WILD.md        # Complete wild mode guide (agents read this)
IMPLEMENT.md           # Implementation workflow
MOTION.md              # Motion catalog (if N3+ motion)
```

## Reading Order

| Role | Phase | Read |
|------|-------|------|
| Orchestrator | Capture | CAPTURE.md |
| Agent | Normal proposal | PROPOSE_NORMAL.md only |
| Agent | Wild proposal | PROPOSE_WILD.md only |
| Agent | If N3+ motion | + MOTION.md |
| Agent | Implementation | IMPLEMENT.md |

**Key principle:** Each proposal agent reads ONE file that contains everything needed.

## Workflow

### Orchestrator
1. Read CAPTURE.md
2. Ask for app URL (default: localhost:3000)
3. Browse with Playwright, discover pages
4. Ask user which pages to include (AskUserQuestion)
5. Capture real DOM/content from each page
6. Detect styling system
7. Spawn proposal agents in parallel, passing captured content

### Proposal Agents
1. Read PROPOSE_NORMAL.md OR PROPOSE_WILD.md (one file only)
2. Read MOTION.md if N3+ motion
3. Generate proposal HTML with real app content
4. Save to tmp/makeover/themes/{name}.html

### Post-Proposal (Orchestrator)
1. Generate index.html linking all proposals
2. Report: "Open tmp/makeover/themes/index.html to compare"

## Critical Constraints

### Normal Mode
- DNA required: `H#-L#-G#-D#-C#-N#`
- Spacing: only 4/8/12/16/24/32/48/64px
- No pure #000/#FFF
- One accent color, ≤10% of surface
- Pass squint test, removal test, anti-AI check

### Wild Mode
- **Structural transformation required** — visual wild alone is not enough
- DNA optional: use `DNA: FREEFORM` or declare custom structure
- Must transform at least one of: pages, navigation, hierarchy, interaction
- FORBIDDEN: same page structure with different skin

### Both Modes
- Real app content only (no placeholders)
- Real images from app (or realistic internet images)
- Cite 2-3 specific references
- Embed MAKEOVER_METADATA comment

## Banned Patterns

**Themes (never default to):** Brutalist, Terminal/Hacker, NASA/Mission Control, Zine/Punk, Medical/Clinical, Arcade/Casino

**Elements:** Inter font, blue accents, generic card grids, top-bar + logo left/links right
