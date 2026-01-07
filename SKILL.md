---
name: makeover
description: Redesign any existing app with distinctive, production-grade visual themes. Auto-discovers app structure, proposes themes, and implements approved designs.
---

# Makeover

Transform any existing application with distinctive, high-quality visual redesigns. Works with any tech stack by auto-detecting structure and adapting to existing styling systems.

## Dependencies

| Requirement | Purpose |
|-------------|---------|
| **frontend-design plugin** | Enforces distinctive, high-quality aesthetics. Without it, themes drift toward generic patterns. |
| **Playwright MCP** | Browses your running app and reference sites for visual research. Essential for understanding current design. |

Install:
- `/plugins add claude-plugins-official/frontend-design`
- `claude mcp add playwright npx @playwright/mcp@latest`

## Commands

```
/makeover propose [count] [inspiration...] # Generate theme proposals
/makeover propose [count] --wild          # Generate experimental proposals
/makeover implement [names]               # Implement approved themes
```

## Workflow Overview

### Propose (Primary Entry Point)

1. **Ask for app URL** — "Where is your app running?" (default: localhost:3000)
2. **Browse with Playwright** — visit running app, discover pages
3. **Ask user which pages** — use AskUserQuestion to confirm pages for proposal
4. **Capture real UI** — snapshot actual DOM structure, content, images from each page
5. **Detect styling system** — Tailwind, CSS modules, etc. (lightweight, inline)
6. **Generate proposals** — apply themes to REAL app content
7. **Report**: "Open tmp/makeover/themes/index.html to compare"

Proposals show exactly how themes look on your actual app, not mock content.

### Implement

1. **Read approved preview** at `tmp/makeover/themes/{name}.html`
2. **Extract embedded metadata** — styling system, patterns, build commands
3. **Copy CSS from proposal** — adapt to detected styling system
4. **Preserve interactive patterns** — modals, auth states work as before
5. **Run build and verify**

## File Structure

| File | Purpose | When to Read |
|------|---------|--------------|
| `SKILL.md` | This file — commands and overview | Always |
| `CRAFT.md` | Elite design principles, anti-AI patterns | **Before every proposal** |
| `PROPOSE.md` | Proposal requirements, agent prompts | Before proposing |
| `IMPLEMENT.md` | Implementation patterns, checklists | Before implementing |
| `LIBRARY.md` | DNA options, palettes, archetypes | During proposal ideation |
| `MOTION.md` | Scroll effects, animations, interactions | When designing motion |

## Semantic Presets

Quick-start presets that expand to DNA internally (now includes motion level):

| Preset | DNA | Description |
|--------|-----|-------------|
| `saas` | H1-L6-G3-D7-C1-N2 | Clean dashboard, micro-interactions, subtle polish |
| `editorial` | H4-L5-G2-D3-C2-N3 | Magazine layout, scroll reveals, elegant transitions |
| `gallery` | H8-L4-G1-D4-C1-N4 | Parallax hero, image zoom, cinematic feel |
| `brutalist` | H9-L9-G8-D6-C8-N6 | Aggressive hover, cursor effects, constant motion |
| `terminal` | H2-L6-G5-D7-C4-N5 | Blinking cursors, typing effects, ambient glow |
| `catalog` | H1-L1-G3-D1-C9-N2 | Subtle, archival, minimal animation |
| `luxury` | H8-L4-G1-D4-C1-N4 | Parallax depth, smooth reveals, specimen isolation |
| `immersive` | H8-L7-G7-D8-C5-N7 | Cinematic, scroll-driven, dramatic page transitions |
| `chaotic` | H9-L9-G8-D6-C11-N9 | Glitch effects, screen shake, unpredictable |

Use presets: `/makeover propose 3 --preset editorial`

Or combine with inspiration: `/makeover propose 2 --preset saas "stripe" "linear"`

## Inspiration Hints

### Text Hints

Pass **keywords** to guide theme generation:
- **Art styles**: anime, ukiyo-e, bauhaus, art deco, constructivist
- **Media**: album covers, movie posters, video games, manga, zines
- **Eras**: 80s, 90s, y2k, retro, vintage, futuristic
- **Moods**: dark, minimal, chaotic, elegant, playful, aggressive
- **Specific references**: "criterion collection", "studio ghibli", "4AD records"
- **Genres**: cyberpunk, vaporwave, noir, horror, fantasy

### Image References (Recommended)

Share **image files** before running the skill:
1. Include reference images in your message
2. Mention them: "use these screenshots as reference"
3. The skill analyzes: color palette, typography, layout patterns, texture

**What to share:**
- Screenshots of websites you like
- Album covers, movie posters, book covers
- Mood boards, design inspiration
- Your current app (for context)

## Output Structure

```
tmp/makeover/themes/
├── index.html          # Comparison page
├── {name}.html         # Individual previews (with embedded metadata)
└── ...
```

## Key Advantages

| Aspect | Traditional Theming | Makeover |
|--------|---------------------|----------|
| Content | Mock/placeholder data | Your actual app UI |
| Pages | Manual enumeration | Auto-detected via Playwright |
| Styling | Assumes specific system | Detects & adapts (Tailwind, CSS modules, etc.) |
| Framework | Framework-specific | Framework-agnostic |

## Quick Start

```bash
# Start your app, then propose themes
/makeover propose 3 "minimal" "dark"
# → Asks for app URL, browses with Playwright
# → Asks which pages to include
# → Generates proposals using your real UI

# Or go wild
/makeover propose 2 --wild "vaporwave"

# Open previews, pick favorites
open tmp/makeover/themes/index.html

# Implement approved theme
/makeover implement chosen-theme-name
```
