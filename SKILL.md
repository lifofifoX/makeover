---
name: makeover
description: Redesign any app with distinctive, production-grade visual themes using real app content.
---

# Makeover

Transform any existing application with distinctive, high-quality visual redesigns.

## Setup

```bash
# Required - enforces distinctive, high-quality aesthetics
/plugins add claude-plugins-official/frontend-design

# Required - browses your running app
claude mcp add playwright npx @playwright/mcp@latest
```

## Commands

```
/makeover propose [count] [inspiration...]  # Generate theme proposals
/makeover propose [count] --wild            # Experimental structural proposals
/makeover implement [names]                 # Implement approved themes
```

## Presets

Expand to DNA codes (H-L-G-D-C-N):

| Preset | DNA | Description |
|--------|-----|-------------|
| `saas` | H1-L6-G3-D7-C1-N2 | Clean dashboard, micro-interactions |
| `editorial` | H4-L5-G2-D3-C2-N3 | Magazine layout, scroll reveals |
| `gallery` | H8-L4-G1-D4-C1-N4 | Parallax hero, image zoom |
| `dashboard` | H2-L6-G5-D7-C4-N2 | Dense data, panels, filters |
| `portfolio` | H4-L4-G1-D4-C1-N4 | Parallax, specimen isolation |
| `catalog` | H1-L1-G3-D1-C9-N2 | Archival, minimal animation |
| `luxury` | H8-L4-G1-D4-C1-N4 | Smooth reveals, specimen isolation |
| `immersive` | H8-L7-G7-D8-C5-N7 | Cinematic, scroll-driven |
| `chaotic` | H9-L9-G8-D6-C11-N9 | Glitch effects, unpredictable |

Usage: `/makeover propose 3 --preset editorial` or `/makeover propose 2 saas "stripe"`

## Inspiration Hints

### Text Keywords
- **Art styles**: bauhaus, art deco, constructivist, ukiyo-e
- **Media**: album covers, movie posters, manga, zines
- **Eras**: 80s, 90s, y2k, retro, futuristic
- **Moods**: dark, minimal, elegant, playful, aggressive
- **Specific**: "criterion collection", "studio ghibli", "4AD records"

### Image References (Recommended)
Share images before running the skill:
1. Include reference images in your message
2. Mention: "use these as reference"
3. The skill extracts: palette, typography, layout patterns, texture

## Normal vs Wild Mode

| Aspect | Normal | Wild |
|--------|--------|------|
| Goal | Polished, production-ready | Structural transformation |
| DNA | Required | Optional (`DNA: FREEFORM`) |
| Pages | Preserve app structure | Collapse, fragment, dissolve |
| Navigation | Reimagined within conventions | Can be abolished, hidden, or IS the content |
| Rules | Systematic spacing, no pure #000/#FFF | Break visual rules with purpose |

**Wild mode fails if:** You could implement it as a normal theme with different colors.

## Output

```
tmp/makeover/themes/
├── index.html      # Comparison page
└── {name}.html     # Individual previews with embedded metadata
```

Open `tmp/makeover/themes/index.html` to compare all proposals side-by-side.
