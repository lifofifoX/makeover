# Normal Mode Proposal Guide

---

## STEP 1: Invoke Frontend-Design Plugin

Call the frontend-design plugin first for baseline design guidance.

---

## Craft Requirements

- Spacing from scale only: 4/8/12/16/24/32/48/64px
- No pure #000 or #FFF
- Accent color ≤10% of surface area
- Curly quotes and proper dashes
- HSL format for all colors

---

## Banned

**Themes:** Brutalist, Terminal/CLI, NASA mission control, Zine, Medical, Arcade

**Visual patterns:** Inter/Roboto/Open Sans, blue as accent, generic 3-col grid, opacity-only hovers, gradients everywhere, same border-radius on everything, shadow on every element

---

## STEP 2: Read Required Files

Read these files in order:
1. `tmp/makeover/capture/manifest.json` - pages, styling system
2. `tmp/makeover/capture/*.snapshot` - actual content for each page
3. `tmp/makeover/constraints.json` - your assigned DNA constraints
4. `DESIGN_SYSTEM.md` - DNA code definitions, spacing scale, color system
5. `tmp/makeover/capture/images.json` - app images to use in proposals
6. `tmp/makeover/capture/ui-elements.json` - app-specific UI elements to showcase
7. `tmp/makeover/capture/instructions.md` - app quirks/technical constraints (if exists)

---

## STEP 3: Verification Gate

**STOP. Output these statements before generating any HTML.**

```
VERIFICATION:
- Pages from manifest: [list them]
- Content I will use: [2-3 specific items per page from snapshots]
- Images I will use: [list 2-3 images from images.json to embed in Section 3]
- App-specific UI elements: [list elements from ui-elements.json to include in Section 4]
- My DNA code: H#-L#-G#-D#-C#-N#
- Constraints satisfied: [yes/no with explanation]
- References (2-3 specific): [list them]
- Palette name: [evocative name, not generic]
```

**If you cannot fill in all fields, read the capture files again.**

---

## STEP 4: Generate HTML

**Read TEMPLATE.md for the exact HTML structure.** Your proposal MUST have all 5 sections:

1. Theme Header (name, DNA code, references)
2. Color Palette (swatches with HSL values, palette name, story)
3. App Content (your redesign with real content from captures)
4. UI Elements (buttons, inputs, cards, alerts, modal, loading, empty)
5. Motion Showcase (if N3+, interactive demos)

**Missing any section = invalid proposal.**

Output: `tmp/makeover/themes/{name}.html`
