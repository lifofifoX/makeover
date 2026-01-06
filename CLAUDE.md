# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

Makeover is a Claude Code skill for redesigning existing applications with distinctive, production-grade visual themes. It auto-discovers app structure, generates theme proposals as HTML previews, and implements approved designs.

## Dependencies

This skill requires two external dependencies to function:

1. **frontend-design plugin** - Enforces high-quality, distinctive aesthetics. Install: `/plugins add claude-plugins-official/frontend-design`
2. **Playwright MCP** - Browses running apps and reference sites for visual research

## Commands

```
/makeover discover                     # Analyze app structure, detect pages
/makeover audit                        # Optional design health check
/makeover propose [count] [hints...]   # Generate theme proposals
/makeover propose [count] --wild       # Generate experimental themes
/makeover implement [names]            # Implement approved themes
```

## Workflow

1. **Discover** creates `tmp/makeover/profile.md` with detected pages, layouts, styling system, interactive patterns, components, and build commands
2. **Propose** spawns parallel agents that each create self-contained HTML previews at `tmp/makeover/themes/{name}.html`, plus an index at `tmp/makeover/themes/index.html`
3. **Implement** converts approved preview HTML into production code matching the detected styling system (Tailwind, CSS modules, styled-components, or vanilla CSS)

## File Structure

| File | Purpose |
|------|---------|
| `SKILL.md` | Entry point - commands and workflow overview |
| `DISCOVER.md` | App analysis methodology, detection strategies, profile template |
| `AUDIT.md` | Optional design audit methodology |
| `PROPOSE.md` | Proposal requirements, DNA system, banned patterns, agent prompts |
| `IMPLEMENT.md` | Implementation strategies, output formats by styling system |
| `LIBRARY.md` | Layout DNA tables, color palettes, archetypes, inspiration sources |
| `MOTION.md` | Motion DNA (N1-N9), scroll effects, interactions, animations |

## Layout DNA System

Every theme declares a DNA code specifying structural choices:

```
H[1-12]-L[1-12]-G[1-12]-D[1-12]-C[1-12]-N[1-9]

Example: H4-L5-G2-D8-C2-N4
- H4: Floating header
- L5: Magazine spread home
- G2: 3-column grid
- D8: Full bleed + drawer detail
- C2: Portrait cards
- N4: Parallax motion
```

DNA categories: Header (H), Home Layout (L), Grid (G), Detail Split (D), Card Style (C), Motion Intensity (N)

## Key Constraints

When generating proposals:
- Each proposal must cite 2-3 specific references from LIBRARY.md
- Multiple proposals must differ in at least 3 DNA positions
- No two proposals share the same header (H) or layout (L) code
- Banned patterns (overused): Inter font, blue accents, generic card grids, top-bar + logo left/links right

When implementing:
- Match the preview HTML exactly - copy CSS directly from proposal's `<style>` tags
- Preserve interactive patterns from profile (modal open/close mechanism, auth states)
- Output format must match detected styling system

## Semantic Presets

Quick-start presets that expand to DNA:

| Preset | Description |
|--------|-------------|
| `saas` | Clean dashboard, micro-interactions |
| `editorial` | Magazine layout, scroll reveals |
| `gallery` | Parallax hero, image zoom |
| `brutalist` | Aggressive hover, cursor effects |
| `terminal` | Blinking cursors, typing effects |
| `luxury` | Parallax depth, smooth reveals |
| `immersive` | Cinematic, scroll-driven |
| `chaotic` | Glitch effects, unpredictable |

Use: `/makeover propose 3 --preset editorial`
