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

Install: `/plugins add claude-plugins-official/frontend-design`

## Commands

```
/makeover discover                        # Analyze app structure, detect pages
/makeover audit                           # Optional: analyze current design
/makeover propose [count] [inspiration...] # Generate theme proposals
/makeover propose [count] --wild          # Generate experimental proposals
/makeover implement [names]               # Implement approved themes
```

## Workflow Overview

### Phase 0: Discover (Auto-runs on first use)

1. **Read DISCOVER.md** for detection strategies
2. **Scan codebase** — routes, pages, components, layouts
3. **Detect styling system** — Tailwind, CSS modules, styled-components, etc.
4. **Identify interactive patterns** — modals, dropdowns, auth states
5. **Generate app profile** at `tmp/makeover/profile.md`
6. **Report**: summary of detected pages, components, patterns

### Phase 1: Audit (Optional)

1. **Read AUDIT.md** for audit methodology
2. **Analyze current design** — colors, spacing, typography, consistency
3. **Generate audit report** at `tmp/makeover/audit.md`
4. **Report**: strengths, weaknesses, opportunities

### Phase 2: Propose

1. **Read PROPOSE.md** for proposal requirements
2. **Read LIBRARY.md** and select inspirations
3. **Review app profile** from discover phase
4. **Generate theme specs** with unique Layout DNA
5. **Spawn parallel proposal agents** — each creates `tmp/makeover/themes/{name}.html`
6. **Generate index** at `tmp/makeover/themes/index.html`
7. **Report**: "Open tmp/makeover/themes/index.html to compare"

### Phase 3: Implement

1. **Read IMPLEMENT.md** for technical requirements
2. **Read approved preview** at `tmp/makeover/themes/{name}.html`
3. **Determine implementation strategy** — drop-in or incremental
4. **Spawn implementation agents** with full context
5. **Run build and verify**

## File Structure

| File | Purpose | When to Read |
|------|---------|--------------|
| `SKILL.md` | This file — commands and overview | Always |
| `DISCOVER.md` | App analysis, page detection | Before first use |
| `AUDIT.md` | Design audit methodology | When using audit command |
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
tmp/makeover/
├── profile.md              # App analysis (from discover)
├── audit.md                # Design audit (optional)
└── themes/
    ├── index.html          # Comparison page
    ├── {name}.html         # Individual previews
    └── ...
```

Implemented themes go to your app's existing style directories, detected during discover phase.

## Key Advantages

| Aspect | Traditional Theming | Makeover |
|--------|---------------------|----------|
| Pages | Manual enumeration | Auto-detected from routes/files |
| Styling | Assumes specific system | Detects & adapts (Tailwind, CSS modules, etc.) |
| Patterns | Requires documentation | Discovered via code analysis |
| Output paths | Hardcoded | Detected from codebase |
| Framework | Framework-specific | Framework-agnostic |

## Quick Start

```bash
# First time: discover your app
/makeover discover

# Review the profile, then propose themes
/makeover propose 3 "minimal" "dark"

# Open previews, pick favorites
open tmp/makeover/themes/index.html

# Implement approved theme
/makeover implement chosen-theme-name
```
