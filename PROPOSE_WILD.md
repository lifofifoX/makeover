# Wild Mode Proposal Guide

Read captured content from **tmp/makeover/capture/**. DNA is optional — use `DNA: FREEFORM` for structural experimentation.

---

## STOP — Complete This Checklist Before Generating Code

**Wild mode requires STRUCTURAL transformation, not just visual styling.**

### Litmus Tests (All Must Pass)

| Test | Question | Required Answer |
|------|----------|-----------------|
| **Decoration Test** | Could someone implement this as a normal theme with different colors? | **NO** |
| **Structure Test** | Does this challenge how the app fundamentally works? | **YES** |
| **Skeleton Test** | Strip away all visual styling. Is the UX still wild? | **YES** |

**If any test would fail, push harder on structural transformation before continuing.**

### Structural Requirements (MANDATORY)
- [ ] **At least ONE structural mutation applied** — page, navigation, hierarchy, or interaction (see Mutations section)
- [ ] **NOT the same page structure** as original app
- [ ] **NOT the same navigation model** (even if reskinned)
- [ ] **NOT the same user journey** with wild visuals

### Standard Requirements (Same as Normal Mode)
- [ ] **NOT an overused concept** — no conspiracy board, evidence locker, fortune teller, arcade cabinet, specimen, escape room
- [ ] **2-3 specific references cited** — actual items, not categories
- [ ] **All captured content shown** — can be restructured, but must be present

### Visible Showcase Sections (MANDATORY — Same as Normal Mode)

Wild proposals are **showcase documents**, not just theme implementations. You MUST include these visible HTML sections:

- [ ] **Color Palette section** — visible swatches with HSL values, evocative name, color story paragraph
- [ ] **UI Elements section** — Buttons (primary, secondary, ghost, destructive, disabled), Inputs (text, select, checkbox, radio, toggle + focus/error), Cards (with hover), Alerts (success, error, warning, info), Modal, Loading, Empty State, + any app-specific elements from capture
- [ ] **Motion showcase section** — if any animations/transitions exist, demonstrate them

### Craft (Still Applies)
- [ ] **Typography correctness** — curly quotes (" "), proper dashes (– —)
- [ ] **Functional interactivity** — clickable things work
- [ ] **Core content accessible** — users can eventually find everything

### Pre-Submit Verification (State Aloud Before Writing HTML)

1. **Structural**: "My structural mutation is [X]. Original app had [structure], my version has [different structure]"
2. **Decoration Test**: "This could NOT be implemented as a normal theme because [specific structural reason]"
3. **Content**: "I am using real content from capture: [list 3 specific items]"
4. **Palette**: "My palette [name] uses HSL: [list primary colors]. Color story: [one sentence]"
5. **References**: "My 2-3 references are: [specific items]"
6. **Banned**: "I verified this is NOT a conspiracy board, evidence locker, fortune teller, arcade cabinet, specimen display, or escape room"

**STOP — Verify Visible Sections Before Writing:**

7. **Palette Section**: "My HTML will include a visible Color Palette section with swatches showing HSL values"
8. **UI Elements Section**: "My HTML will include a visible UI Elements section with: Buttons (primary/secondary/ghost/destructive/disabled), Inputs (text/select/checkbox/radio/toggle + focus/error), Cards, Alerts (success/error/warning/info), Modal, Loading, Empty State"
9. **Metadata Format**: "My HTML comment will use MAKEOVER_METADATA format with theme, structure, styling_system, pages, wild_mode fields"

**If any check fails, revise before writing the file.**

---

## Output Requirements

**File:** `tmp/makeover/themes/{name}.html`

**Metadata comment at top of HTML (EXACT FORMAT REQUIRED):**
```html
<!--
MAKEOVER_METADATA
theme: {name}
structure: {mutation description}
styling_system: {Tailwind|CSS Modules|vanilla}
pages: {comma-separated list}
wild_mode: true
palette: {palette name}
references: {comma-separated list}
-->
```

**Required visible sections in HTML (ALL MANDATORY):**

| Section | Contents | Notes |
|---------|----------|-------|
| **1. Theme Header** | Name, wild concept, structure mutation, references | Visible at top of page |
| **2. Color Palette** | Swatches with HSL values, palette name, color story | Must be a visible section with actual color boxes |
| **3. App Content** | All captured pages, restructured per wild concept | Use real content from capture files |
| **4. UI Elements** | Buttons (primary/secondary/ghost/destructive/disabled), Inputs (text/select/checkbox/radio/toggle + focus/error), Cards, Alerts (4 types), Modal, Loading, Empty State | Dedicated section with all variants |
| **5. Motion Showcase** | Any animations, transitions, hover effects | Demonstrate interactivity |

**CRITICAL:** Wild proposals are **showcase documents** that demonstrate a wild design system. They are NOT raw theme implementations. Each section above must be a visible, labeled section in the HTML that a reviewer can scroll to and evaluate.

**HTML STRUCTURE TEMPLATE (Follow This Exactly):**

```html
<!--
MAKEOVER_METADATA
theme: {name}
structure: {mutation}
styling_system: vanilla
pages: home, collection, detail
wild_mode: true
palette: {palette-name}
references: {ref1}, {ref2}
-->
<!DOCTYPE html>
<html>
<head>...</head>
<body>
  <!-- SECTION 1: Theme Header (REQUIRED) -->
  <header class="theme-header">
    <h1>{Theme Name}</h1>
    <p class="concept">{Wild concept description}</p>
    <p class="structure">{Structural mutation description}</p>
    <p class="references">Inspired by: {specific references}</p>
  </header>

  <!-- SECTION 2: Color Palette (REQUIRED) -->
  <section class="color-palette">
    <h2>Color Palette: {Palette Name}</h2>
    <p class="color-story">{One sentence explaining mood/origin}</p>
    <div class="swatches">
      <div class="swatch" style="background: hsl(...)"><span>Primary</span><code>hsl(...)</code></div>
      <div class="swatch" style="background: hsl(...)"><span>Secondary</span><code>hsl(...)</code></div>
      <!-- 5-7 colors with HSL values displayed -->
    </div>
  </section>

  <!-- SECTION 3: App Content (REQUIRED) -->
  <section class="app-content">
    <h2>App Preview</h2>
    <!-- The actual redesigned app goes here -->
  </section>

  <!-- SECTION 4: UI Elements (REQUIRED) -->
  <section class="ui-elements">
    <h2>UI Elements</h2>
    <h3>Buttons</h3>
    <button class="primary">Primary</button>
    <button class="secondary">Secondary</button>
    <button class="ghost">Ghost</button>
    <button class="destructive">Destructive</button>
    <button disabled>Disabled</button>

    <h3>Inputs</h3>
    <!-- text, select, checkbox, radio, toggle + focus/error states -->

    <h3>Cards</h3>
    <!-- Card component with hover state -->

    <h3>Alerts</h3>
    <!-- success, error, warning, info variants -->

    <h3>Modal</h3>
    <!-- modal with header, body, actions, overlay -->

    <h3>Loading</h3>
    <!-- spinner or skeleton -->

    <h3>Empty State</h3>
    <!-- icon + message + action -->
  </section>

  <!-- SECTION 5: Motion Showcase (REQUIRED if animations exist) -->
  <section class="motion-showcase">
    <h2>Motion & Interactions</h2>
    <!-- Interactive demos of hover, transitions, animations -->
  </section>
</body>
</html>
```

**Without ALL 5 sections visible and labeled, the proposal is INVALID.**

**Before generating HTML:** Invoke the frontend-design plugin.

---

## Structural Mutations (Choose At Least One)

### Page Mutations

| Mutation | What It Does | Example |
|----------|--------------|---------|
| **Collapse** | All pages become one continuous experience | Profile + Activity + Settings = one infinite scroll |
| **Fragment** | Single logical "page" scattered as artifacts | User profile as scattered documents on a canvas |
| **Dissolve** | No pages exist, content is spatial | Everything floats in explorable 2D space |
| **Invert** | Metadata becomes content, content recedes | Timestamps and tags are hero, actual data is ambient |
| **Archaeology** | Layers reveal history | Scroll to "dig" through time layers |

### Navigation Mutations

| Mutation | What It Does | Example |
|----------|--------------|---------|
| **As Content** | Clicking nav reveals content in-place | "About" expands into about content, no page change |
| **Discovery** | Users must find paths | Content hidden until discovered through exploration |
| **Abolished** | No explicit nav exists | Users scroll/swipe through continuous experience |
| **Temporal** | Structure changes over time | New sections appear based on session duration |
| **Environmental** | Navigate by moving through space | Scroll direction changes what content appears |

### Hierarchy Mutations

| Mutation | What It Does | Example |
|----------|--------------|---------|
| **Inversion** | Secondary info becomes primary | Dates and metadata are huge, content is small |
| **Flat** | Everything at same visual weight | No emphasis, user decides importance |
| **Dynamic** | Importance shifts with interaction | Hovered items grow, others shrink |
| **Relationship** | Connections matter more than items | Lines between items are the feature |

### Interaction Mutations

| Mutation | What It Does | Example |
|----------|--------------|---------|
| **Passive** | Content appears without action | Information surfaces based on time, not clicks |
| **Friction** | Deliberately difficult | Users must "earn" access through engagement |
| **Ambient** | Responds to presence | Hover time, scroll speed affect display |
| **Accumulative** | Builds over session | More content appears the longer you stay |

---

## Visual Wild Techniques (Supplement, Not Substitute)

These ADD to structural transformation but don't REPLACE it.

### Layout Disruption
- **Rotation**: 5-15° angles (not subtle 1-2°)
- **Overlap**: Elements intentionally competing for space
- **Broken grid**: Elements escape their containers
- **Asymmetric splits**: 70/30, 80/20, not balanced
- **Vertical/diagonal text**: Labels, headers, navigation

### Visual Aggression
- **Glitch effects**: RGB split, scan lines, noise, corruption
- **Scale extremes**: 72pt headlines next to 8pt labels
- **Color clash**: Intentionally "wrong" combinations
- **Texture overload**: Multiple overlapping textures
- **Harsh transitions**: No smooth gradients — hard cuts

### Typography Extremes
- **Mixed fonts**: Different typefaces in single headlines
- **Distressed text**: Worn, corrupted, fragmenting
- **Ransom note**: Cut-out letters, mixed sizes/styles
- **Vertical orientation**: Rotated labels, sideways navigation

---

## Rules You SHOULD Break

| Normal Rule | Wild Freedom |
|-------------|--------------|
| No pure #000/#FFF | Harsh contrast creates tension |
| Spacing scale only | Irregular gaps signal intention |
| Hierarchy must squint-test | Obscured hierarchy forces engagement |
| One accent, ≤10% | Clashing colors create energy |
| Subtle hover states | Aggressive feedback is memorable |
| Consistent radii | Mixed radii create unpredictability |

### Structural Rules to Break (MANDATORY)

| Normal Rule | Wild Transformation |
|-------------|---------------------|
| Pages follow app structure | Collapsed, fragmented, dissolved |
| Navigation in header/sidebar | Anywhere, nowhere, or IS content |
| Content displayed directly | Hidden, revealed, discovered |
| Linear user journey | Non-linear, exploratory, surprising |

---

## Color Palette Creation

**Create an original palette that serves your structural concept.**

### Requirements

1. **Use HSL** — even when breaking rules, HSL makes relationships clear
2. **5-7 colors** — can be high contrast, clashing, or unconventional
3. **Evocative name** — match your structural concept
4. **Color story** — explain the intentional discomfort or energy

### Wild Freedoms

In wild mode, you MAY:
- Use pure `#000000` / `#FFFFFF` for harsh contrast
- Use clashing colors intentionally
- Break the 60-30-10 rule
- Oversaturate or desaturate extremely

But you MUST:
- Do it intentionally, not by accident
- Explain why in your color story
- Ensure it serves the structural concept

### Banned Patterns (Still Apply)

| Pattern | Why | Alternative |
|---------|-----|-------------|
| Neon pink + cyan | Cyberpunk cliché | Other unexpected clashes |
| Matrix green on black | 1999 | Different "digital" approaches |
| Generic glitch colors | Lazy | Concept-specific palette |

---

## Typography Pairings

### Brutalist Expression
| Role | Font |
|------|------|
| Headlines | Druk Wide Heavy |
| Body | Suisse Int'l Regular |

### Terminal
| Role | Font |
|------|------|
| All | Berkeley Mono |

### Mixed Chaos
Intentionally mismatched:
- Headlines: Mix serif + sans in same line
- Ransom note: Different fonts per word
- Vertical: Rotated labels

---

## Banned Patterns

### Structural Anti-Patterns
| Banned | Why | Alternative |
|--------|-----|-------------|
| Same pages, different skin | Not structural wild | Collapse, fragment, dissolve |
| Navigation reskinned as tabs/dials | Still conventional | Navigation as content, or abolished |
| List restyled as cards | Still a list | Spatial, temporal, discovery model |
| "Wild looking" same journey | Just decoration | Transform the journey itself |

### Visual Anti-Patterns
| Banned | Why | Alternative |
|--------|-----|-------------|
| Horizontal CRT scan line | Cliché | Vertical interference, diagonal static |
| Full-screen glitch on load | Predictable | Localized glitch on interaction |
| Neon pink + cyan | Cyberpunk cliché | Unexpected color clash |
| Matrix falling code | 1999 | Static corruption, data viz |

### Overused Concepts (Do Not Use)
- Conspiracy Board — red string, polaroids
- Evidence Locker — police evidence bags
- Fortune Teller — tarot, crystal ball
- Arcade Cabinet — pixel fonts, insert coin
- Specimen Display — museum labels
- Escape Room — puzzles, locks, clues

---

## The Wild Standard

**"Would David Carson think this is bold enough?"**
**"Would this confuse someone expecting a normal app?"**

Wild design that works:
- **Commits** to structural transformation, not just visual
- **Challenges** fundamental UX assumptions
- Is **disorienting** in an intentional way
- **Couldn't exist** as a "normal theme with wild styling"
