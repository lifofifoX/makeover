# Proposal Phase

Everything needed to generate theme proposals. **Read this entire file before spawning proposal agents.**

---

## PROPOSAL CHECKLIST (VERIFY BEFORE SUBMITTING)

Every proposal MUST include:

### Required Elements
- [ ] **Layout DNA declared** — unique combination not used by existing themes
- [ ] **Motion DNA declared** — N1-N9 motion intensity level (see MOTION.md)
- [ ] **Color palette** with:
  - [ ] Evocative name (e.g., "Midnight Cinema", "Sakura Dusk")
  - [ ] 5-7 colors with hex codes (NO pure #000 or #FFF)
  - [ ] Color roles defined (background, surface, text, accent, etc.)
  - [ ] All neutrals share same temperature undertone
  - [ ] Color story (2-3 sentences on why these work together)
  - [ ] Visual swatches in the preview
- [ ] **Motion design specified** with:
  - [ ] Scroll effects (parallax, reveals, sticky transforms)
  - [ ] Hover/interaction effects (buttons, cards, links)
  - [ ] Ambient motion (if N4+)
  - [ ] Page transitions (if N6+)
- [ ] **App-specific pages shown** — all pages captured via Playwright
- [ ] **Interactive patterns preserved** — modals, dropdowns work as detected
- [ ] **Styling system respected** — output matches detected system
- [ ] **2-3 specific references cited** from LIBRARY.md

### Elite Craft Verification (CRAFT.md)
- [ ] **Spacing from scale only** — 4/8/12/16/24/32/48/64px, no arbitrary values
- [ ] **Typography polish** — curly quotes, proper dashes, letterspacing on caps
- [ ] **Color discipline** — no pure black/white, accent used ≤10% of surface
- [ ] **Anti-AI checkpoint passed** — no generic gradients, same-radius-everywhere, shadow-on-everything
- [ ] **Removal pass done** — nothing decorative that doesn't serve function
- [ ] **Squint test passed** — hierarchy obvious when blurred

---

## PREREQUISITES

Before proposing, ensure:

1. **App is running** — user provides URL (default: localhost:3000)
2. **Read CRAFT.md** — internalize elite design principles
3. **Read LIBRARY.md** — select specific inspirations
4. **Read MOTION.md** — understand motion options and techniques

---

## CAPTURING REAL APP UI (Playwright MCP)

Proposals show **your actual app**, not mock content. Use Playwright to capture real UI.

### Step 1: Ask for App URL

```
"Where is your app running?"
Default: http://localhost:3000
```

### Step 2: Browse and Discover Pages

Navigate to the app URL. Explore by:
- Clicking navigation links
- Checking common routes (/dashboard, /settings, /profile, /[id])
- Looking at the DOM for route information

Capture each distinct page:
- Take a snapshot (accessibility tree)
- Note the URL/route
- Note the page purpose

### Step 3: Ask User Which Pages

Use AskUserQuestion to confirm:

```
"I found these pages in your app:
- / (Home/Landing)
- /dashboard (Main dashboard)
- /settings (User settings)
- /profile/[id] (User profiles)

Which pages should appear in the theme proposals?"
```

Options: Let user select multiple, or suggest "All of these (Recommended)"

### Step 4: Capture DOM Structure

For each selected page, extract:
- **Actual content** — real text, headings, labels
- **Real images** — actual image URLs from the page
- **Component structure** — buttons, cards, forms, modals
- **Current classes** — detect Tailwind, CSS modules, etc.

Store this as context for proposal agents.

### Step 5: Detect Styling System (Inline)

Quick detection from DOM/files:
- Tailwind: class names like `bg-blue-500`, `px-4`
- CSS Modules: class names like `styles_button__abc123`
- Styled-components: `sc-` prefixed classes
- Vanilla CSS: standard class names, inline styles

Note the system for proposal metadata.

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

**Variance Enforcement Matrix (MANDATORY):**

Before finalizing proposals, verify differentiation across these axes:

| Axis | Must Vary | Options |
|------|-----------|---------|
| **Header** | Every proposal different H-code | H1-H12 |
| **Layout** | Every proposal different L-code | L1-L12 |
| **Color Temperature** | At least 2 different temps | Warm / Cool / Neutral |
| **Density** | At least 2 different levels | Minimal / Balanced / Dense |
| **Motion** | Spread across range | Low (N1-3) / Mid (N4-6) / High (N7-9) |
| **Era** | Mix eras | Contemporary / Retro / Timeless |
| **Energy** | Mix energies | Calm / Dynamic / Intense |

**For 3 proposals, target this distribution:**
```
Proposal A: Warm temp, Minimal density, Low motion, Contemporary, Calm
Proposal B: Cool temp, Balanced density, Mid motion, Retro influence, Dynamic
Proposal C: Neutral temp, Dense, High motion, Timeless, Intense
```

**DNA Example for 3 proposals:**
```
Proposal A: H4-L5-G2-D8-C2-N3 (floating, magazine, 2-col, full-bleed, portrait, responsive)
Proposal B: H1-L1-G6-D3-C1-N5 (top bar, bio+grid, masonry, stacked, square, kinetic)
Proposal C: H8-L7-G4-D6-C4-N7 (hidden, scroll story, list, overlay, text row, cinematic)
```

**Automatic Rejection Triggers:**
- Two proposals with same H or L code
- Two proposals from same overused tier
- Two proposals with same color temperature
- Three proposals all using N2-N3 motion (too safe)

---

## BANNED PATTERNS (Overused — Avoid)

These patterns appear too frequently. **Do not use unless the concept demands it:**

### Overused Themes (BANNED as Defaults)

These archetypes are generated too frequently. **Do NOT use unless explicitly requested:**

**Tier 1 — Severely Overused (Hard Ban):**
- **Brutalist** — raw concrete, harsh typography, exposed structure
- **Terminal/Hacker** — green-on-black, monospace everything, blinking cursors
- **Mission Control/NASA** — telemetry, countdown timers, trajectory displays
- **Zine/Punk** — xerox textures, cut-out collage, ransom note aesthetic
- **Medical Records/Clinical** — clipboard aesthetic, diagnosis forms, vitals
- **Arcade/Casino** — neon lights, slot machines, pixel fonts

**Tier 2 — Frequently Overused (Avoid):**
- **Cyberpunk Neon** — hot pink/cyan on black, rain, Japanese text
- **Vaporwave** — pink/purple gradients, Roman busts, 80s geometry
- **Film Noir** — high contrast B&W, venetian blinds, fedoras
- **Retro Computing** — Win95/DOS nostalgia, pixel fonts, old icons
- **Dark Mode SaaS** — purple gradients, glass cards, Linear clone
- **Luxury Minimal** — black + gold + serif, fashion editorial clone
- **Spotify Dark** — green accent, card grids, rounded everything

**Tier 3 — Becoming Overused (Use Sparingly):**
- **Japanese Minimal** — lots of whitespace, subtle typography, muji-like
- **Editorial Magazine** — big serif headlines, multi-column, pull quotes
- **Bauhaus Primary** — red/blue/yellow blocks, geometric, Mondrian-ish
- **Gradient Mesh SaaS** — Stripe-style color blobs, purple-blue
- **Glassmorphism** — frosted glass, blur, translucent cards

**Variance Rule:** If multiple proposals, maximum ONE from Tier 2-3 across all proposals. Never two from same tier.

**Instead:** LIBRARY.md has 50+ palettes and 30+ archetypes. Pick unexpected combinations:
- Hospitality + Technical (hotel keycard meets server logs)
- Luxury + Brutalist (Bottega meets concrete)
- Retro + Contemporary (Kodachrome palette with Linear layout)
- Geographic + Functional (Marrakech colors on dashboard UI)

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

## ELITE DESIGN REQUIREMENTS

**All requirements from CRAFT.md are mandatory.** Key rules (see CRAFT.md for details):

| Requirement | Rule |
|-------------|------|
| **Spacing** | Only 4/8/12/16/24/32/48/64px — no arbitrary values |
| **Typography** | Curly quotes (" "), proper dashes (– —), letterspacing on caps |
| **Color** | No pure #000/#FFF, one accent ≤10% surface, consistent neutral temperature |
| **Anti-AI** | No: uniform shadows, same radii everywhere, gradients on everything, decorative blobs |
| **Squint Test** | Hierarchy obvious when blurred |
| **Removal Pass** | If it can be removed without losing function, remove it |

---

## ADAPTING TO CAPTURED APP

### Using Captured Content

From the Playwright capture:

1. **Pages to design** — create sections for each captured page
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

If app uses `data-state` for modals:
```html
<!-- CORRECT: matches detected pattern -->
<div data-state="closed" class="modal">...</div>

<!-- WRONG: different pattern -->
<div class="modal hidden">...</div>
```

If app uses Tailwind:
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

### 1. Get App URL and Browse

```
1. Ask user: "Where is your app running?" (default: localhost:3000)
2. Navigate with Playwright MCP
3. Explore pages via navigation
4. Take snapshots of each page
```

### 2. Confirm Pages with User

Use AskUserQuestion:
- List discovered pages
- Let user select which to include
- "All pages (Recommended)" as first option

### 3. Capture Page Content

For each selected page:
- Extract DOM structure
- Capture real text/content
- Note image URLs
- Detect styling system

### 4. Read Design References

```
Read: CRAFT.md (mandatory)
Read: LIBRARY.md (select 2-3 specific references)
Read: MOTION.md (for motion techniques)
```

### 5. Parallel Execution

Spawn all proposal agents in a SINGLE message, passing captured page content:

```
Task(subagent_type="general-purpose", description="Propose {name} theme", prompt="...")
Task(subagent_type="general-purpose", description="Propose {name} theme", prompt="...")
```

### 6. Generate Index

After proposals complete, create `tmp/makeover/themes/index.html` with links to all.

---

## Proposal Agent Prompt Template

```
You are creating a PREVIEW PROPOSAL for a theme using REAL APP CONTENT.

## Files to Read

**Mandatory:** CRAFT.md (design rules), LIBRARY.md § Palettes/Typography (pick 1 each)
**If N3+:** MOTION.md (scroll/animation techniques)
**If --wild:** WILD_CRAFT.md instead of CRAFT.md

## Captured App Content

{PAGES_CONTENT}
<!-- Orchestrator passes actual DOM/content captured via Playwright -->

## Assignment

Theme: {NAME}
DNA: {H#-L#-G#-D#-C#-N#}
References: {cite 2-3 SPECIFIC items from LIBRARY.md — not categories}
Palette: {name} with 5-7 colors (no pure #000/#FFF)
Styling System: {detected: Tailwind/CSS Modules/vanilla}

## Output

File: tmp/makeover/themes/{name}.html
- All CSS in <style>, fonts via Google CDN only
- Invoke frontend-design plugin first

## Required Sections
1. Theme header (name, DNA, references)
2. Color palette with swatches and story
3. Each captured page with REAL content
4. Components (buttons, cards, forms, modals)
5. Motion showcase (if N3+)

## Content Rules (CRITICAL)
- ACTUAL text from captured pages — no "Lorem ipsum"
- ACTUAL image URLs from app — no emoji, no placeholder.com
- If no images in app: realistic internet images fitting context
- ACTUAL navigation structure

## Embed Metadata (Top of HTML)

<!--
MAKEOVER_METADATA
theme: {name}
dna: {H#-L#-G#-D#-C#-N#}
styling_system: {Tailwind|CSS Modules|vanilla}
pages: {comma-separated list}
-->

## Quality Gates (All Must Pass)
1. Squint test — hierarchy obvious when blurred?
2. Removal pass — nothing can be removed?
3. Anti-AI check — no generic shadows/gradients/radii?
4. Real content — no placeholders, no emoji substitutes?
5. Banned themes — not in Tier 1, max 1 from Tier 2-3?

Return: theme name, DNA, palette name, references, file path
```

### Wild Mode Addition

Add when `--wild` flag used:

```
## WILD MODE

MANDATORY:
- Data as theater (dossier, wanted poster, medical chart)
- Detail pages: D1 banned, use D6/D8/D9 or thematic
- Navigation: NOT a nav bar (file tabs, channels, terminal)
- Lists: NOT tables (police blotter, flight board, chat log)

TECHNIQUES: Rotated sections (5-15°), overlapping layers, scale extremes (72pt/8px), mixed fonts, textures.

Read CRAFT.md "Wild Mode" section for intentional rule-breaking.
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
      position: relative;
      overflow: hidden;
    }
    .card-preview iframe {
      width: 200%;
      height: 200%;
      transform: scale(0.5);
      transform-origin: top left;
      border: none;
      pointer-events: none; /* Allows clicks to pass through to card link */
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
        <iframe src="[name].html" title="[Theme Name] preview" loading="lazy"></iframe>
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
