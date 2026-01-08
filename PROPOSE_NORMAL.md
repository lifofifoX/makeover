# Normal Mode Proposal Guide

Read captured content from **tmp/makeover/capture/**. Read constraints from **tmp/makeover/constraints.json**.

---

## OUTPUT FORMAT

**Read TEMPLATE.md for the exact HTML structure.** Your proposal MUST have all 5 sections:

1. Theme Header (name, DNA code, references)
2. Color Palette (swatches with HSL values, palette name, story)
3. App Content (your redesign with real content from captures)
4. UI Elements (buttons, inputs, cards, alerts, modal, loading, empty)
5. Motion Showcase (if N3+, interactive demos)

**Missing any section = invalid proposal.**

**Before generating:** Invoke the frontend-design plugin.

---

## Checklist

### Required
- [ ] DNA declared: H#-L#-G#-D#-C#-N#
- [ ] 2-3 specific references cited
- [ ] All captured pages with REAL content
- [ ] Constraints from constraints.json satisfied

### Showcase Sections
- [ ] Section 1: Theme Header with name, DNA, references
- [ ] Section 2: Color Palette with 5-7 HSL swatches and story
- [ ] Section 3: App Content with all captured pages
- [ ] Section 4: UI Elements — standard + app-specific from capture
- [ ] Section 5: Motion Showcase (if N3+)

**App-specific elements:** Check capture files for elements unique to this app. If unsure, use `AskUserQuestion` before generating.

### Craft
- [ ] Spacing from scale: 4/8/12/16/24/32/48/64px only
- [ ] No pure #000/#FFF, accent ≤10%
- [ ] Curly quotes, proper dashes
- [ ] No AI patterns: generic gradients, same-radius-everywhere, shadow-on-everything

---

## DNA System

Declare: `H#-L#-G#-D#-C#-N#`

| Code | Category | Examples |
|------|----------|----------|
| H | Header | H1 Top bar, H2 Sidebar, H4 Floating, H8 Hidden |
| L | Layout | L1 Bio+Grid, L5 Magazine, L6 Dashboard |
| G | Grid | G1 2-col, G5 Table, G6 Masonry |
| D | Detail | D1 50/50, D4 Media dominant, D7 Tabbed |
| C | Card | C1 Square, C2 Portrait, C9 Index card |
| N | Motion | N1 Static, N3 Fade-ins, N6 Interactive |

**Full definitions in DESIGN_SYSTEM.md.** If N3+, also read MOTION.md.

---

## Color Palette

1. Use HSL format always
2. 5-7 colors + 8-10 gray shades
3. Evocative name ("Midnight Archive" not "Dark Blue")
4. One-sentence color story

**Banned:** Pure #000/#FFF, blue as accent, neon pink+cyan, gradients everywhere

---

## Banned Patterns

**Themes:** Brutalist, Terminal, NASA, Zine, Medical, Arcade

**Elements:** Inter/Roboto/Open Sans, blue accent, generic 3-col grid, opacity-only hovers
