# Normal Mode Proposal Guide

Read captured content from **tmp/makeover/capture/**. Read constraints from **tmp/makeover/constraints.json**.

---

## STOP — Complete This Checklist Before Generating Code

**You must verify ALL items below. If any item is unclear, re-read the relevant section.**

### Required Elements (All Must Be Present)
- [ ] **DNA declared** — unique H#-L#-G#-D#-C#-N# code (see DNA section below)
- [ ] **2-3 specific references cited** — actual items (albums, sites, films), not categories
- [ ] **All captured pages shown** — use REAL content from tmp/makeover/capture/*.snapshot

### Visible Showcase Sections (MANDATORY)

Proposals are **showcase documents**. You MUST include these visible HTML sections:

- [ ] **Color Palette section** — visible swatches with HSL values, evocative name, color story paragraph
- [ ] **UI Elements section** — Buttons (primary, secondary, ghost, destructive, disabled), Inputs (text, select, checkbox, radio, toggle + focus/error), Cards (with hover), Alerts (success, error, warning, info), Modal, Loading, Empty State, + any app-specific elements from capture
- [ ] **Motion showcase section** — if N3+, demonstrate animations/transitions

### Craft Checks (All Must Pass)
- [ ] **Spacing from scale only** — 4/8/12/16/24/32/48/64px, nothing else
- [ ] **Typography polish** — curly quotes (" "), proper dashes (– —), letterspacing on caps
- [ ] **Color discipline** — no pure #000/#FFF, accent ≤10% of surface
- [ ] **Anti-AI check** — no generic gradients, same-radius-everywhere, shadow-on-everything
- [ ] **Removal test** — nothing can be removed without losing function
- [ ] **Squint test** — hierarchy obvious when blurred

### Pre-Submit Verification (State Aloud Before Writing HTML)

1. **Content**: "I am using real content from capture: [list 3 specific items]"
2. **DNA**: "My DNA is [code]. I chose H[#] because [reason], L[#] because [reason]"
3. **Palette**: "My palette [name] uses HSL: primary hsl([H],[S]%,[L]%), accent hsl(...). Created from [reference inspiration]"
4. **References**: "My 2-3 references are: [specific items]"
5. **Anti-AI**: "I avoided: [list 2 specific AI patterns I rejected]"
6. **Constraints**: "My assigned constraints were [X]. I satisfied them by [Y]"

**STOP — Verify Visible Sections Before Writing:**

7. **Palette Section**: "My HTML will include a visible Color Palette section with swatches showing HSL values"
8. **UI Elements Section**: "My HTML will include a visible UI Elements section with: Buttons (primary/secondary/ghost/destructive/disabled), Inputs (text/select/checkbox/radio/toggle + focus/error), Cards, Alerts (success/error/warning/info), Modal, Loading, Empty State"
9. **Metadata Format**: "My HTML comment will use MAKEOVER_METADATA format with theme, dna, styling_system, pages fields"

**If any check fails, revise before writing the file.**

---

## Output Requirements

**File:** `tmp/makeover/themes/{name}.html`

**Metadata comment at top of HTML (EXACT FORMAT REQUIRED):**
```html
<!--
MAKEOVER_METADATA
theme: {name}
dna: {H#-L#-G#-D#-C#-N#}
styling_system: {Tailwind|CSS Modules|vanilla}
pages: {comma-separated list}
palette: {palette name}
references: {comma-separated list}
-->
```

**Required visible sections in HTML (ALL MANDATORY):**

| Section | Contents | Notes |
|---------|----------|-------|
| **1. Theme Header** | Name, DNA code, references | Visible at top of page |
| **2. Color Palette** | Swatches with HSL values, palette name, color story | Must be a visible section with actual color boxes |
| **3. App Content** | Each captured page with REAL content | Use content from capture files |
| **4. UI Elements** | Buttons (primary/secondary/ghost/destructive/disabled), Inputs (text/select/checkbox/radio/toggle + focus/error), Cards, Alerts (4 types), Modal, Loading, Empty State | Dedicated section with all variants |
| **5. Motion Showcase** | Animations, transitions, hover effects (if N3+) | Demonstrate interactivity |

**CRITICAL:** Proposals are **showcase documents** that demonstrate a design system. They are NOT raw theme implementations. Each section above must be a visible, labeled section in the HTML that a reviewer can scroll to and evaluate.

**HTML STRUCTURE TEMPLATE (Follow This Exactly):**

```html
<!--
MAKEOVER_METADATA
theme: {name}
dna: H#-L#-G#-D#-C#-N#
styling_system: vanilla
pages: home, collection, detail
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
    <p class="dna">DNA: {H#-L#-G#-D#-C#-N#}</p>
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
    <!-- The actual redesigned app pages go here -->
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
    <!-- Card component matching C-code + hover state -->

    <h3>Alerts</h3>
    <!-- success, error, warning, info variants -->

    <h3>Modal</h3>
    <!-- modal with header, body, actions, overlay -->

    <h3>Loading</h3>
    <!-- spinner or skeleton -->

    <h3>Empty State</h3>
    <!-- icon + message + action -->
  </section>

  <!-- SECTION 5: Motion Showcase (REQUIRED if N3+) -->
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

## DNA System

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

### Archetypes

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

## Color Palette Creation

**Create an original palette.** Do not use pre-defined palettes.

### Requirements

1. **Use HSL** — `hsl(H, S%, L%)` format always
2. **5-7 colors minimum** — primary, secondary, accent, plus 8-10 gray shades
3. **Evocative name** — "Midnight Archive", not "Dark Blue Theme"
4. **Color story** — one sentence explaining mood and origin

### Process

1. Start from your 2-3 references — what hues dominate?
2. Pick base hue, build primary shades (100-900)
3. Choose accent by complementary, split-complementary, or analogous relationship
4. Build warm or cool grays that harmonize with primary
5. Test: 60% dominant, 30% secondary, 10% accent

### Banned Color Patterns

| Pattern | Why | Alternative |
|---------|-----|-------------|
| Pure `#000000` / `#FFFFFF` | Harsh, unrefined | `hsl(0,0%,10%)` / `hsl(0,0%,98%)` |
| Blue as primary accent | Default, overused | Any other hue |
| Neon pink + cyan | Cyberpunk cliché | Unexpected combinations |
| Gradient backgrounds everywhere | AI aesthetic | Flat colors, strategic gradients |
| Gray text on colored backgrounds | Muddy | Same-hue tints |

---

## Typography Pairings

| Style | Headlines | Body |
|-------|-----------|------|
| **Swiss** | Helvetica Neue Bold | Helvetica Neue |
| **Editorial** | Canela Light | Freight Text |
| **Technical** | GT America Mono Bold | GT America |
| **Contemporary** | Söhne Bold | Söhne |
| **Quiet Luxury** | Sabon | Caslon |

---

## Variance Requirements

When generating multiple proposals, each must differ by ≥3 DNA positions.

| Axis | Requirement |
|------|-------------|
| Header | Every proposal different H-code |
| Layout | Every proposal different L-code |
| Color Temperature | At least 2 different (warm/cool) |
| Motion | Spread across N1-3/N4-6/N7-9 |

**Read your assigned constraints from tmp/makeover/constraints.json.**

---

## Design Philosophy

- **Start with features** — design content first, shell emerges from it
- **Detail comes later** — grayscale first, color later
- **Restraint over decoration** — if it can be removed without harm, remove it
- **Emphasize by de-emphasizing** — make competitors quieter, not heroes louder

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
