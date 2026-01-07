# Proposal Phase

Everything needed to generate theme proposals. **Read this entire file before spawning proposal agents.**

---

## PROPOSAL CHECKLIST (VERIFY BEFORE SUBMITTING)

Every proposal MUST include:

- [ ] **Layout DNA declared** — unique combination not used by existing themes
- [ ] **Motion DNA declared** — N1-N9 motion intensity level (see MOTION.md)
- [ ] **Color palette** with:
  - [ ] Evocative name (e.g., "Midnight Cinema", "Sakura Dusk")
  - [ ] 5-7 colors with hex codes
  - [ ] Color roles defined (background, surface, text, accent, etc.)
  - [ ] Color story (2-3 sentences on why these work together)
  - [ ] Visual swatches in the preview
- [ ] **Motion design specified** with:
  - [ ] Scroll effects (parallax, reveals, sticky transforms)
  - [ ] Hover/interaction effects (buttons, cards, links)
  - [ ] Ambient motion (if N4+)
  - [ ] Page transitions (if N6+)
- [ ] **App-specific pages shown** — all pages from profile.md
- [ ] **Interactive patterns preserved** — modals, dropdowns work per profile
- [ ] **Styling system respected** — output matches detected system
- [ ] **2-3 specific references cited** from LIBRARY.md

---

## PREREQUISITES

Before proposing, ensure:

1. **Discovery completed** — `tmp/makeover/profile.md` exists
2. **Read profile** — understand pages, patterns, styling system
3. **Read audit** (if exists) — `tmp/makeover/audit.md`
4. **Read LIBRARY.md** — select specific inspirations
5. **Read MOTION.md** — understand motion options and techniques

---

## CREATIVE FORCING FUNCTIONS

### 1. Consult the Library

Read `LIBRARY.md` and **SELECT 2-3 SPECIFIC inspirations** — not categories, specific items:

| Bad | Good |
|-----|------|
| "inspired by anime" | "Cowboy Bebop end credits, Persona 5 menus" |
| "retro gaming vibe" | "PS1 save rooms, Final Fantasy VII menus" |
| "editorial layout" | "Apartamento magazine, Fantastic Man spreads" |

### 2. Declare Your References

Every proposal MUST state:
```
REFERENCES: [specific item 1], [specific item 2], [specific item 3]
```

Your design choices must **trace back** to these references.

### 3. Ensure High Variance Between Proposals

When generating multiple proposals:
- Each must differ in **at least 3 DNA positions** from every other
- No two proposals share the same header (H) or layout (L) code
- Vary color temperature (warm vs cool vs neutral)
- Vary density (minimal vs dense vs chaotic)

**Example for 3 proposals:**
```
Proposal A: H4-L5-G2-D8-C2 (floating, magazine, 2-col, full-bleed, portrait)
Proposal B: H1-L1-G6-D3-C1 (top bar, bio+grid, masonry, stacked, square)
Proposal C: H8-L7-G4-D6-C4 (hidden, scroll story, list, overlay, text row)
```

---

## BANNED PATTERNS (Overused — Avoid)

These patterns appear too frequently. **Do not use unless the concept demands it:**

### Overused Themes

These archetypes are generated too frequently across projects. **Avoid defaulting to these:**
- **Brutalist** — raw concrete, harsh typography
- **Terminal/Hacker** — green-on-black, monospace everything
- **Mission Control/NASA** — telemetry, countdown timers
- **Zine/Punk** — xerox textures, cut-out collage
- **Medical Records/Clinical** — clipboard aesthetic, diagnosis forms
- **Arcade/Casino** — neon lights, slot machine aesthetics, pixel fonts (especially in wild mode)

**Instead:** Explore the full LIBRARY.md — there are 50+ archetypes. Pick unexpected combinations. If your first instinct is one of the above, force yourself to choose something else.

### Layout
- Generic 3-column card grid with uniform sizing
- Standard 2-column detail page without justification
- Top navigation bar with logo left, links right (default H1)
- Plain text bio in a rectangle box

### Typography
- Inter, Roboto, Open Sans (too generic)
- System font stack without personality
- All-caps headers with letterspacing (overused minimal trope)

### Color
- Blue as primary accent
- White/light gray backgrounds with dark text (default, boring)
- "Clean minimal" grayscale without personality

### Components
- Cards with subtle rounded corners and drop shadows
- Buttons with slight border-radius and solid fill
- Hover states that only change opacity

**If you find yourself reaching for these, STOP and consult LIBRARY.md for alternatives.**

---

## ADAPTING TO APP PROFILE

### Reading the Profile

Before designing, extract from `tmp/makeover/profile.md`:

1. **Pages to design** — create sections for each detected page
2. **Styling system** — match output format (Tailwind classes, CSS vars, etc.)
3. **Interactive patterns** — preserve modal/dropdown behaviors
4. **Component library** — style existing components, don't invent new ones
5. **Layouts** — work within detected layout structure

### Mapping DNA to App

The DNA system is universal, but maps to your specific app:

| DNA Code | Generic Concept | Map to Profile |
|----------|-----------------|----------------|
| H1-H12 | Header architecture | Your detected layouts |
| L1-L12 | Home/landing layout | Your homepage |
| G1-G12 | Grid/list views | Your list pages |
| D1-D12 | Detail page split | Your detail pages |
| C1-C12 | Card design | Your card components |

### Respecting Detected Patterns

If profile says modal uses `data-state`:
```html
<!-- CORRECT: matches detected pattern -->
<div data-state="closed" class="modal">...</div>

<!-- WRONG: different pattern -->
<div class="modal hidden">...</div>
```

If profile says styling is Tailwind:
```html
<!-- CORRECT: Tailwind classes -->
<button class="bg-primary text-white px-4 py-2">...</button>

<!-- WRONG: inline styles or vanilla CSS classes -->
<button style="background: blue">...</button>
```

---

## Layout DNA System

Every theme picks ONE option from EACH category. See `LIBRARY.md` for full tables.

### DNA Format

```
DNA: H[1-12]-L[1-12]-G[1-12]-D[1-12]-C[1-12]

Example: H4-L5-G2-D1-C2
- H4: Floating header
- L5: Magazine spread home
- G2: 3-column grid
- D1: 50/50 detail split
- C2: Portrait cards
```

### Quick Reference

| Code | Category | Options |
|------|----------|---------|
| H1-H12 | Header Architecture | Top bar, sidebars, floating, split, bottom, hidden, diagonal, peripheral, sticky, frame |
| L1-L12 | Home Page Layout | Bio+grid, hero+list, sidebar, single feature, magazine, dashboard, scroll story, bento, collage, split, asymmetric, floating |
| G1-G12 | Collection Grid | 2-4+ columns, single list, table, masonry, horizontal scroll, scattered, featured+grid, staggered, filmstrip, cluster |
| D1-D12 | Detail Page Split | 50/50, reversed, stacked, media dominant, info dominant, overlay, tabbed, full bleed, theater, diptych, immersive, specimen |
| C1-C12 | Card Design | Square, portrait, landscape, text row, large preview, thumbnail+details, circular, polaroid, index card, bleed, layered, specimen |
| N1-N9 | Motion Intensity | Static, subtle, responsive, parallax, kinetic, interactive, cinematic, immersive, chaotic |

**Full tables with descriptions in LIBRARY.md and MOTION.md**

---

## Color Palette Requirements

Every theme MUST have a named palette with:

1. **Palette Name** — evocative, memorable
2. **5-7 Core Colors** — with hex codes and roles
3. **Color Story** — why these colors work together
4. **Visual Display** — swatches shown in the preview

### Color Roles (Required)

```css
--color-bg: #...;        /* Page background */
--color-surface: #...;   /* Cards, panels */
--color-primary: #...;   /* Main text */
--color-secondary: #...; /* Secondary text */
--color-muted: #...;     /* Faint text, labels */
--color-accent: #...;    /* Links, CTAs */
--color-border: #...;    /* Borders */
```

### Palette Display Template

```html
<section class="color-palette-display">
  <h2>Color Palette: [NAME]</h2>
  <div class="palette-swatches">
    <div class="swatch" style="background: #HEX;">
      <span class="color-name">Background</span>
      <span class="color-hex">#HEX</span>
    </div>
    <!-- Repeat for each color -->
  </div>
  <div class="palette-story">
    <p>[Why these colors work together]</p>
  </div>
</section>
```

---

## Wild Mode (--wild flag)

When `--wild` is used, generate AGGRESSIVELY EXPERIMENTAL themes.

### The Wild Mode Litmus Test

**Could someone mistake this for a "normal" theme?**
- If YES → not wild enough, push harder
- If NO → you're on the right track

**Would a client say "this is too weird"?**
- If NO → not wild enough
- If YES → perfect

### Wild Mode MANDATORY Requirements

#### 1. Unconventional Information Display
Transform how data is presented:
- **Dossier/file** — manila folder, paper clips, redacted sections
- **Interrogation transcript** — Q&A format, timestamps
- **Character sheet** — RPG stats, abilities, equipment
- **Wanted poster** — reward amount, distinguishing features
- **Medical record** — diagnosis, vital signs chart
- **Employee badge** — photo, clearance level, barcode

#### 2. Detail Pages (NEVER standard 2-column)
D1 is BANNED in wild mode. Use:
- D6: Info overlays image
- D8: Full bleed + sliding drawer
- D9: Theatrical spotlight presentation
- Or thematic: evidence bag, specimen jar, auction lot

#### 3. Navigation (NOT a nav bar)
Integrated into the theme's world:
- File tabs, TV channels, elevator buttons
- Radio dial, crime board pins, menu items
- Terminal commands, phone keypad

#### 4. Activity/List Pages (NOT tables)
Transform tabular data:
- Police blotter, flight board, medical chart
- Receipt roll, chat log, telegram
- Ship's log, betting slip, inventory log

### Wild Techniques

**Layout Chaos:**
- Rotated containers (5-15° angles, not subtle 1°)
- Overlapping elements (intentional layering)
- Broken grid (elements escape containers)
- Asymmetric splits (70/30, 80/20)

**Visual Disruption:**
- Glitch effects (RGB split, scan lines, noise)
- Maximalist overload (patterns on patterns)
- Color clash (intentionally "wrong" combinations)
- Scale extremes (72pt headlines, 8px labels)

**Typography Extremes:**
- Mixed fonts in single headlines
- Vertical text, rotated labels
- Distressed, corrupted text
- Ransom note cut-outs

### Wild Mode BANNED Effects

These effects are overused in wild mode. **Do not use:**
- **Horizontal scan line** — the animated line that scrolls from top to bottom (CRT scan effect)
- **Full-screen glitch on load** — overwhelming and predictable

---

## Visual Research for Inspiration

### Browsing Reference Sites (Playwright MCP)

When the user mentions inspiration sources (websites, brands, styles), use Playwright MCP to visit them:

```
"I want something like stripe.com and linear.app"
→ Navigate to stripe.com, take snapshots
→ Navigate to linear.app, take snapshots
→ Analyze: typography, spacing, color, layout patterns, motion
```

This provides:
- Actual rendered designs (not descriptions)
- Real typography choices and pairings
- Color relationships in context
- Layout patterns and whitespace usage
- Interaction patterns and hover states

**When to browse:**
- User mentions specific sites ("like Notion", "Vercel vibes")
- User provides URLs
- Vague inspiration ("minimal SaaS", "editorial magazine") - find canonical examples

**When NOT to use Playwright:**
- Do NOT screenshot the generated proposal HTML files — they are self-contained and the user opens them directly in their browser
- Do NOT browse unless the user explicitly asks or provides reference URLs
- Do NOT use Playwright just to "verify" proposals — trust the HTML output

### Analyzing Image References

When the user provides reference images:

### Step 1: Read Each Image

Use the Read tool to analyze each image.

### Step 2: Extract Design Elements

| Element | What to Look For |
|---------|------------------|
| Colors | Dominant hue, accents, contrast, saturation, temperature |
| Typography | Serif/sans/display, weight, case, spacing, era |
| Layout | Centered/asymmetric, grid/organic, dense/spacious |
| Texture | Grain/smooth, matte/glossy, layered/flat |
| Mood | Era, emotion, energy level, cultural context |

### Step 3: Synthesize

```
From analyzing 4 screenshots:
- Palette: muted earth tones (browns, sage, cream), low saturation
- Typography: elegant serifs, often italic, generous tracking
- Layout: centered, lots of negative space, minimal elements
- Texture: subtle grain, soft edges
- Mood: contemplative, timeless
```

### Step 4: Generate

Create themes that capture the essence while adding unique interpretations.

---

## Proposal Workflow

### 1. Read Prerequisites

```
Read: tmp/makeover/profile.md
Read: tmp/makeover/audit.md (if exists)
Read: LIBRARY.md
```

### 2. Determine Pages to Show

From profile, identify:
- Landing/home page
- List/collection pages
- Detail pages
- Settings/profile pages
- Any special pages

### 3. Parallel Execution

Spawn all proposal agents in a SINGLE message:

```
Task(subagent_type="general-purpose", description="Propose {name} theme", prompt="...")
Task(subagent_type="general-purpose", description="Propose {name} theme", prompt="...")
```

### 4. Generate Index

After proposals complete, create `tmp/makeover/themes/index.html` with links to all.

---

## Proposal Agent Prompt Template

```
You are creating a PREVIEW PROPOSAL for a theme, not implementing it.

## CRITICAL: Read First

1. Read tmp/makeover/profile.md — understand the app
2. Read tmp/makeover/audit.md (if exists) — understand current issues
3. Read LIBRARY.md — select inspirations

## App Context

[INSERT PROFILE SUMMARY]

Pages to design: [list from profile]
Styling system: [from profile]
Interactive patterns: [from profile]

## Your Selected References

You MUST cite 2-3 specific references from LIBRARY.md:
REFERENCES: [item 1], [item 2], [item 3]

## Layout DNA

This theme's DNA: {DNA_CODE}
- Header: {H_DESCRIPTION}
- Home Layout: {L_DESCRIPTION}
- Grid: {G_DESCRIPTION}
- Detail Split: {D_DESCRIPTION}
- Card Style: {C_DESCRIPTION}
- Motion: {N_DESCRIPTION}

## Motion Design

Motion Level: {N_CODE} ({N_NAME})

### Scroll Effects
{SCROLL_EFFECTS}
- Parallax layers (if N4+): {describe layers}
- Scroll-triggered reveals: {describe what animates in}
- Sticky transforms: {any sticky with progression}

### Hover & Interactions
- Buttons: {hover effect}
- Cards: {hover effect}
- Links: {underline animation}
- Images: {zoom/filter effect}

### Ambient Motion (if N4+)
{AMBIENT_EFFECTS}
- Floating elements: {if any}
- Background animation: {gradient shift, particles, grain}
- Cursor effects: {if N6+}

### Page Transitions (if N6+)
{PAGE_TRANSITIONS}

### JS Enhancements (note for implementation)
{LIST_JS_LIBRARIES_NEEDED}

## Color Palette

Palette Name: {PALETTE_NAME}
Colors:
- Background: {HEX} - {ROLE}
- Surface: {HEX} - {ROLE}
- Primary Text: {HEX} - {ROLE}
- Accent: {HEX} - {ROLE}
- [Additional colors...]

Color Story: {WHY_THESE_COLORS}

## Use frontend-design Plugin

Invoke: Skill tool: skill="frontend-design", args="Create {AESTHETIC} theme preview"

## Output: Single HTML File

Create: tmp/makeover/themes/{name}.html

Requirements:
- ALL CSS inline in <style> tag
- Google Fonts via CDN only
- NO external dependencies
- NO build step

## Required Sections

### 0. THEME HEADER
- Theme name in display type
- Layout DNA code
- References cited
- Brief description

### 1. COLOR PALETTE DISPLAY
- Named palette with swatches
- Hex codes visible
- Color story

### 2. EACH PAGE FROM PROFILE
For each page in profile.md, create a section showing:
- Page layout
- Key components
- Interactive states
- Responsive behavior (show mobile)

### 3. COMPONENTS
- Buttons (all variants)
- Cards (all variants)
- Forms (inputs, selects)
- Modals (if in profile)
- Navigation states

### 4. MOTION SHOWCASE
Demonstrate the key motion effects:
- A scroll-triggered section with working parallax or reveals
- Hover states on all interactive elements
- Any ambient animations running
- Loading/entrance animations

### 5. LAYOUT WIREFRAME
Box diagram showing DNA structure.

## Realistic Content

**Use actual images, not placeholders.** Sources:
- Screenshots from the user's running app (captured during discovery)
- Relevant images from the web (Unsplash, product photos, etc.)
- Images from the app's existing assets

Content should match the app type:
- For e-commerce: real product photos, prices, cart
- For dashboard: realistic metrics, charts, data
- For portfolio: actual project images, case studies
- For social: realistic posts, profile photos, interactions

**Never use:** gray boxes, "placeholder" text, or generic colored rectangles for images.

## DO NOT

- Create multiple files
- Use framework-specific templates yet
- Reference external CSS/JS (except fonts)
- Implement real functionality
- Use different colors than specified
- Use different layout than DNA specifies

## Output Summary

Return:
- Theme name
- Layout DNA code
- Color palette name
- References cited
- File path
- Aesthetic description
```

### Wild Mode Additions

When `--wild` flag is used, add to the prompt:

```
## WILD MODE ACTIVE

### MANDATORY — ALL OF THESE:

1. **Data Presentation** — Theatrical, NOT plain text:
   - Dossier, character sheet, wanted poster, medical record

2. **Detail Page** — D1 is BANNED:
   - D6, D8, D9, or thematic (evidence bag, specimen jar)

3. **Navigation** — NOT a nav bar:
   - File tabs, TV channels, terminal commands

4. **List Pages** — NOT tables:
   - Police blotter, flight board, chat log

### WILD TECHNIQUES — USE SEVERAL:
- Rotated sections (5-15° angles)
- Overlapping, layered elements
- 72pt headlines, 8px labels
- Mixed fonts in headlines
- Textures, stains, wear marks

The goal: someone sees this and says "what the hell?" — then discovers it actually works.
```

---

## Preview Index Template

After all proposals complete, generate:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Makeover Proposals</title>
  <style>
    * { box-sizing: border-box; }
    body {
      font-family: system-ui, -apple-system, sans-serif;
      padding: 3rem 2rem;
      max-width: 1400px;
      margin: 0 auto;
      background: #fafafa;
      color: #1a1a1a;
    }
    h1 {
      font-size: 2rem;
      font-weight: 600;
      margin: 0 0 0.5rem;
    }
    .subtitle {
      color: #666;
      margin: 0 0 2.5rem;
    }
    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(340px, 1fr));
      gap: 1.5rem;
    }
    .card {
      display: block;
      background: #fff;
      border: 1px solid #e5e5e5;
      border-radius: 12px;
      overflow: hidden;
      text-decoration: none;
      color: inherit;
      transition: transform 0.2s ease, box-shadow 0.2s ease;
    }
    .card:hover {
      transform: translateY(-4px);
      box-shadow: 0 12px 24px rgba(0,0,0,0.1);
    }
    .card-preview {
      aspect-ratio: 16/10;
      background: #f0f0f0;
    }
    .card-preview img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
    .card-body {
      padding: 1.25rem;
    }
    .card-title {
      font-size: 1.125rem;
      font-weight: 600;
      margin: 0 0 0.5rem;
    }
    .card-dna {
      font-family: ui-monospace, monospace;
      font-size: 0.75rem;
      color: #888;
      margin: 0 0 0.75rem;
    }
    .card-desc {
      font-size: 0.875rem;
      color: #555;
      margin: 0;
      line-height: 1.5;
    }
  </style>
</head>
<body>
  <h1>Makeover Proposals</h1>
  <p class="subtitle">Generated: [timestamp] · Click any card to view full preview</p>
  <div class="grid">
    <!-- Repeat for each proposal — entire card is clickable -->
    <a href="[name].html" class="card">
      <div class="card-preview">
        <img src="[screenshot or representative image from proposal]" alt="[Theme Name] preview">
      </div>
      <div class="card-body">
        <h2 class="card-title">[Theme Name]</h2>
        <p class="card-dna">DNA: [code]</p>
        <p class="card-desc">[Brief description]</p>
      </div>
    </a>
  </div>
</body>
</html>
```
