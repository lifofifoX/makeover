# Normal Mode Proposal Guide

**Complete reference for normal mode proposal agents.**

For DNA codes and design scales, see **DESIGN_SYSTEM.md**. Read captured content from **tmp/makeover/capture/**.

---

## Checklist (Verify Before Submitting)

### Required Elements
- [ ] **DNA declared** — unique H#-L#-G#-D#-C#-N# combination
- [ ] **Color palette** with evocative name, 5-7 colors (no pure #000/#FFF), color story
- [ ] **2-3 specific references cited** — not categories, specific items
- [ ] **All captured pages shown** with REAL content
- [ ] **UI Elements section** — buttons, inputs, cards, alerts, modals, loading, empty states

### Craft Verification
- [ ] **Spacing from scale only** — 4/8/12/16/24/32/48/64px
- [ ] **Typography polish** — curly quotes (" "), proper dashes (– —), letterspacing on caps
- [ ] **Color discipline** — no pure #000/#FFF, accent ≤10% of surface
- [ ] **Anti-AI check** — no generic gradients, same-radius-everywhere, shadow-on-everything
- [ ] **Removal test** — nothing can be removed without losing function
- [ ] **Squint test** — hierarchy obvious when blurred

---

## Design Philosophy

- **Start with features** — design content first, shell emerges from it
- **Detail comes later** — grayscale first, color later
- **Restraint over decoration** — if it can be removed without harm, remove it
- **Emphasize by de-emphasizing** — make competitors quieter, not heroes louder

---

## DNA Quick Reference

Declare: `H#-L#-G#-D#-C#-N#`

| Code | Category | Range |
|------|----------|-------|
| H | Header | H1-H12 (Top bar, Sidebar, Floating, Hidden...) |
| L | Layout | L1-L12 (Bio+Grid, Hero+List, Dashboard...) |
| G | Grid | G1-G12 (2-col, Masonry, Horizontal scroll...) |
| D | Detail | D1-D12 (50/50, Overlay, Theater...) |
| C | Card | C1-C12 (Square, Portrait, Index card...) |
| N | Motion | N1-N9 (Static to Chaotic) |

**Full definitions in DESIGN_SYSTEM.md.** If N3+, also read MOTION.md.

---

## Color Palette Creation

**Create an original palette.** Do not use pre-defined palettes — design one that fits the app's content and your references.

### Requirements

1. **Use HSL** — define all colors in `hsl(H, S%, L%)` format (see DESIGN_SYSTEM.md)
2. **5-7 colors minimum** — primary, secondary, accent, plus 8-10 gray shades
3. **Evocative name** — "Midnight Archive", not "Dark Blue Theme"
4. **Color story** — one sentence explaining the palette's mood and origin

### Process

1. Start from your 2-3 references — what hues dominate?
2. Pick a base hue, build primary shades (100-900)
3. Choose accent by complementary, split-complementary, or analogous relationship
4. Build warm or cool grays that harmonize with primary
5. Test: 60% dominant, 30% secondary, 10% accent

### Banned Patterns

| Pattern | Why | Alternative |
|---------|-----|-------------|
| Pure `#000000` / `#FFFFFF` | Harsh, unrefined | `hsl(0,0%,10%)` / `hsl(0,0%,98%)` |
| Blue as primary accent | Default, overused | Any other hue |
| Neon pink + cyan | Cyberpunk cliché | Unexpected combinations |
| Gradient backgrounds everywhere | AI aesthetic | Flat colors, strategic gradients |
| Gray text on colored backgrounds | Muddy | Same-hue tints |
| Copying a famous brand's exact palette | Derivative | Extract principles, not colors |

---

## Typography Pairings

| Style | Headlines | Body | Alternatives |
|-------|-----------|------|--------------|
| **Swiss** | Helvetica Neue Bold | Helvetica Neue | Suisse Int'l, Akzidenz |
| **Editorial** | Canela Light | Freight Text | GT Sectra, Tiempos |
| **Technical** | GT America Mono Bold | GT America | IBM Plex, Berkeley Mono |
| **Contemporary** | Söhne Bold | Söhne | Graphik, Untitled Sans |
| **Quiet Luxury** | Sabon | Caslon | Garamond Premier, Lyon |

---

## Archetypes

| Archetype | DNA | Key Features |
|-----------|-----|--------------|
| Editorial | H1-L5-G2-D3-C2-N3 | Masthead, columns, pull quotes |
| Archive | H1-L6-G5-D7-C4-N2 | Dense data, tables, filters |
| Gallery | H8-L4-G1-D4-C1-N4 | Whitespace, hidden chrome |
| Catalog | H1-L1-G3-D1-C9-N2 | Index cards, provenance |
| SaaS | H1-L1-G3-D1-C1-N2 | Clean, systematic |
| Fintech | H4-L6-G5-D7-C4-N3 | Data viz, gradients |
| Luxury | H8-L4-G1-D4-C1-N4 | Specimen isolation |

---

## Banned Patterns

### Themes (Hard Ban)
Brutalist, Terminal/Hacker, NASA/Mission Control, Zine/Punk, Medical/Clinical, Arcade/Casino

### Elements
- Inter, Roboto, Open Sans fonts
- Blue as primary accent
- Generic 3-column card grid
- Top bar with logo left, links right (H1 default without variation)
- Cards with subtle rounded corners + drop shadows (default AI)
- Hover states that only change opacity

---

## Variance Requirements

When generating multiple proposals, each must differ by ≥3 DNA positions.

| Axis | Requirement |
|------|-------------|
| Header | Every proposal different H-code |
| Layout | Every proposal different L-code |
| Color Temperature | At least 2 different (warm/cool) |
| Motion | Spread across N1-3/N4-6/N7-9 |

**Read your assigned constraints from tmp/makeover/constraints.json before designing.**

---

## Pre-Submit Verification (REQUIRED)

Before writing the HTML file, state aloud:

1. **Content Check**: "I am using real content from capture: [list 3 specific text items]"
2. **DNA Check**: "My DNA is [code]. I chose H[#] because [reason], L[#] because [reason]"
3. **Palette Check**: "My palette [name] uses HSL: primary is hsl([H], [S]%, [L]%), accent is hsl(...). I created this palette from scratch based on [reference inspiration]"
4. **References Check**: "My 2-3 references are: [specific items, not categories]"
5. **Anti-AI Check**: "I avoided: [list 2 specific AI patterns I consciously rejected]"
6. **Constraint Check**: "My assigned constraints were [X]. I satisfied them by [Y]"

**If any check fails, revise before writing the file.**

---

## Agent Prompt Template

```
You are creating a PREVIEW PROPOSAL using REAL APP CONTENT.

## Read First
1. tmp/makeover/capture/manifest.json — pages, styling system
2. tmp/makeover/capture/{page}.snapshot — DOM captures
3. tmp/makeover/constraints.json — your assigned constraints
4. DESIGN_SYSTEM.md — if you need detailed scale definitions

## Assignment
Theme: {NAME}
DNA: {H#-L#-G#-D#-C#-N#}
References: {2-3 SPECIFIC items}
Palette: {name} with 5-7 colors
Styling: {Tailwind|CSS Modules|vanilla}

## Design Principles
1. Start with features, chrome emerges
2. Emphasize by de-emphasizing competitors
3. Spacing: only 4/8/12/16/24/32/48/64px
4. Color: USE HSL, create original palette, no pure black/white
5. Shadows: 5 levels, light from above
6. Restraint: remove anything non-essential

## Output
File: tmp/makeover/themes/{name}.html
- All CSS in <style>, fonts via Google CDN
- Invoke frontend-design plugin first

## Required Sections
1. Theme header (name, DNA, references)
2. Color palette with swatches
3. Each captured page with REAL content
4. UI Elements (buttons, inputs, cards, alerts, modals, loading, empty)
5. Motion showcase (if N3+)

## Metadata (Top of HTML)
<!--
MAKEOVER_METADATA
theme: {name}
dna: {H#-L#-G#-D#-C#-N#}
styling_system: {system}
pages: {list}
-->

## Pre-Submit Verification
Before writing, state aloud your Content, DNA, Palette, References, Anti-AI, and Constraint checks.

## Quality Gates
1. Squint test — hierarchy obvious?
2. Removal test — nothing removable?
3. Anti-AI check — no generic patterns?
4. Real content — no placeholders?
5. Spacing discipline — all from scale?

Return: theme name, DNA, palette, references, file path
```
