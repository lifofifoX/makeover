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
3. `./DESIGN_SYSTEM.md` - DNA code definitions, spacing scale, color system

---

## STEP 3: Verification Gate

**STOP. Output these statements before generating any HTML.**

```
VERIFICATION:
- Pages from manifest: [list them]
- My DNA code: H#-L#-G#-D#-C#-N#
- Constraints satisfied: [yes/no with explanation]
- References (2-3 specific): [list them]
- Palette name: [evocative name, not generic]
```

**If you cannot fill in all fields, read the capture files again.**

---

## STEP 4: Generate HTML

**Read TEMPLATE.md for section requirements and HTML structure.**

Output: `tmp/makeover/themes/{name}.html`
