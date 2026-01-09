# Wild Mode Proposal Guide

---

## STEP 1: Invoke Frontend-Design Plugin

Call the frontend-design plugin first for baseline design guidance.

---

## Structural Mutations (Choose One Primary)

| Type | What Changes |
|------|--------------|
| **Page** | Collapse all into one scroll, fragment into scattered artifacts, dissolve boundaries |
| **Navigation** | Nav becomes content, discovery-based, abolished entirely, environmental |
| **Hierarchy** | Invert (metadata becomes hero), flatten, dynamic on interaction |
| **Interaction** | Passive (time-based), friction (earn access), ambient (responds to presence) |

---

## Visual Techniques (Supplement Structure)

- Rotation 5-15 degrees, overlap, broken grid
- Asymmetric splits, scale extremes
- Mixed fonts, vertical text
- Color clash, texture overload

---

## Craft Basics

- Use HSL for all colors
- Avoid AI patterns: gradient backgrounds everywhere, same border-radius on everything, shadow on every element

---

## Banned

**Concepts:** Conspiracy board, evidence locker, fortune teller, arcade cabinet, specimen display, escape room, detective case files

**Visuals:** Neon pink + cyan together, Matrix green rain, horizontal CRT scanlines

---

## STEP 2: Read Required Files

Read these files in order:
1. `tmp/makeover/capture/manifest.json` - pages, styling system
2. `tmp/makeover/capture/*.snapshot` - actual content for each page
3. `tmp/makeover/constraints.json` - your assigned structural mutation

---

## STEP 3: Verification Gate

**STOP. Output these statements before generating any HTML.**

```
VERIFICATION:
- Pages from manifest: [list them]
- My structural mutation: [page/navigation/hierarchy/interaction]
- Mutation description: [one sentence explaining how structure changes]
- Decoration test: Could this be a normal theme with different colors? [must be NO]
- References (2-3 specific): [list them]
- Palette name: [evocative name]
```

**If "decoration test" is YES, you need a more radical structural mutation.**

---

## STEP 4: Generate HTML

**Read `tmp/makeover/capture/instructions.md` for technical constraints (if exists).**
**Read TEMPLATE.md for section requirements and HTML structure.**

Output: `tmp/makeover/themes/{name}.html`
