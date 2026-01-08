# Normal Mode Proposal Guide

**Complete reference for normal mode proposal agents.** Everything you need is in this file.

---

## Checklist (Verify Before Submitting)

### Required Elements
- [ ] **DNA declared** — unique H#-L#-G#-D#-C#-N# combination
- [ ] **Color palette** with evocative name, 5-7 colors (no pure #000/#FFF), color story
- [ ] **2-3 specific references cited** — not categories, specific items
- [ ] **All captured pages shown** with REAL content
- [ ] **Styling system respected** — output matches detected system

### Elite Craft Verification
- [ ] **Spacing from scale only** — 4/8/12/16/24/32/48/64px
- [ ] **Typography polish** — curly quotes (" "), proper dashes (– —), letterspacing on caps
- [ ] **Color discipline** — no pure black/white, accent ≤10% of surface
- [ ] **Anti-AI check** — no generic gradients, same-radius-everywhere, shadow-on-everything
- [ ] **Removal pass** — nothing can be removed without losing function
- [ ] **Squint test** — hierarchy obvious when blurred

---

## Elite Design Principles

### 1. Restraint Over Decoration

Elite designers know when NOT to design. They remove rather than add.

**The Removal Test:**
- "What can I remove without losing function or clarity?"
- If nothing can be removed, you've achieved elegance
- Repeat until removal would cause harm

**Signs of Over-Design (Avoid):**
- Gradients where flat color would work
- Shadows on elements that don't need depth
- Borders around things that don't need containment
- Icons next to text that's already clear
- Multiple visual treatments competing for attention

### 2. Systematic Thinking

Every choice relates to every other choice:
- If you use 16px somewhere, there's a reason
- Every spacing value comes from a scale
- Every color has a defined role

### 3. Hierarchy Through Reduction

Don't add emphasis. Remove competing elements.

| Weak | Strong |
|------|--------|
| Make CTA button bigger | Reduce visual weight of surroundings |
| Add bold + color + size to headline | Let headline be the only large element |

**The Squint Test:** Blur your vision. Hierarchy should still be obvious.

---

## Spacing Scale

**Always use this scale. Never arbitrary values.**

```
4px  — micro (icon padding, tight gaps)
8px  — small (related element gaps)
12px — medium-small
16px — medium (comfortable breathing room)
24px — large (section gaps)
32px — x-large (major section breaks)
48px — 2x-large
64px — 3x-large (page-level divisions)
```

---

## Typography Craft

### Micro-Typography (What Separates Pros)

| Wrong | Right | Character |
|-------|-------|-----------|
| "quotes" | "quotes" | Curly quotes (U+201C, U+201D) |
| 'apostrophe' | 'apostrophe' | Curly apostrophe (U+2019) |
| 10-20 | 10–20 | En dash for ranges (U+2013) |
| word - word | word — word | Em dash for breaks (U+2014) |
| ... | … | Ellipsis character (U+2026) |

### Letterspacing by Size
- Headlines (24px+): Tighten slightly (-0.01em to -0.02em)
- Body text (14-18px): Default tracking (0)
- Small text (12px-): Loosen slightly (+0.01em to +0.02em)
- ALL CAPS: Always loosen (+0.05em to +0.1em)

### Line Height by Size
```
Small text (12-14px): 1.6-1.7
Body text (16-18px): 1.5-1.6
Subheadings (20-24px): 1.3-1.4
Headlines (32px+): 1.1-1.2
Display (48px+): 1.0-1.1
```

---

## Color Sophistication

### No Pure Black or White

`#000000` against `#FFFFFF` creates eye strain and halation.

**Instead:**
- Dark text: `#1a1a1a`, `#171717`, `#0d0d0d`
- Dark backgrounds: `#0a0a0a`, `#111111`
- Light backgrounds: `#FAFAFA`, `#F5F5F5`

### The 60-30-10 Rule
- 60%: Dominant (background, large surfaces)
- 30%: Secondary (cards, containers)
- 10%: Accent (CTAs, highlights)

### Neutral Temperature

All neutrals should share the same undertone:

| Temperature | Example | Feels Like |
|-------------|---------|------------|
| Warm gray | `#8B8680` | Cozy, organic |
| True gray | `#808080` | Neutral, digital |
| Cool gray | `#788084` | Technical, modern |
| Blue-gray | `#64748B` | Professional |

---

## Anti-AI Checklist

**Actively avoid these tells:**

### Visual Tells
| AI Pattern | Elite Alternative |
|------------|-------------------|
| Gradient backgrounds on everything | Flat colors, strategic gradient use |
| Identical border-radius on all elements | Varied radii based on element size |
| Shadows on every card | Shadows only where depth serves function |
| Saturated accent colors at full strength | Muted, sophisticated accent usage |
| Generic blob/wave decorations | No decoration, or highly specific |

### Structural Tells
| AI Pattern | Elite Alternative |
|------------|-------------------|
| Perfect symmetry everywhere | Intentional asymmetry with balance |
| Same spacing between all elements | Grouped spacing (related items closer) |
| Cards in perfect grids | Varied layouts, masonry, or asymmetric |
| Every section has same structure | Rhythm variation keeps interest |

---

## DNA System

Every theme declares: `H#-L#-G#-D#-C#-N#`

### Header Architecture (H1-H12)

| Code | Style | Description |
|------|-------|-------------|
| H1 | Top Bar | Full-width horizontal bar at top |
| H2 | Left Sidebar | Vertical nav on left, content right |
| H3 | Right Sidebar | Content left, vertical nav on right |
| H4 | Floating | Minimal floating element, semi-transparent |
| H5 | Split | Logo left edge, nav right edge |
| H6 | Bottom Bar | Navigation at bottom of viewport |
| H7 | Centered Stack | Centered logo above centered nav |
| H8 | Hidden/Hamburger | No visible nav until triggered |
| H9 | Diagonal/Angled | Rotated or angled header bar |
| H10 | Peripheral | Elements at extreme edges |
| H11 | Sticky Minimal | Collapses to micro-nav on scroll |
| H12 | Frame | Navigation forms border around viewport |

### Home Page Layout (L1-L12)

| Code | Style | Description |
|------|-------|-------------|
| L1 | Bio + Grid | Info section above, content grid below |
| L2 | Hero + List | Large featured section, vertical list |
| L3 | Sidebar + Content | Info in sidebar, main content center |
| L4 | Single Feature | One large item, minimal else |
| L5 | Magazine Spread | Editorial layout, asymmetric blocks |
| L6 | Dashboard Panels | Multiple stat/info panels |
| L7 | Vertical Scroll Story | Single column, narrative scroll |
| L8 | Bento Grid | Mixed-size boxes, varied content |
| L9 | Collage/Overlap | Overlapping elements, chaotic |
| L10 | Split Screen | Two equal vertical sections |
| L11 | Asymmetric Thirds | Golden ratio divisions |
| L12 | Floating Islands | Disconnected content blocks |

### Collection Grid (G1-G12)

| Code | Style | Description |
|------|-------|-------------|
| G1 | 2 Column | Two items per row |
| G2 | 3 Column | Three items per row |
| G3 | 4+ Column | Four or more per row |
| G4 | Single Column List | Vertical list, one per row |
| G5 | Table/Rows | Data table with columns |
| G6 | Masonry | Pinterest-style varied heights |
| G7 | Horizontal Scroll | Side-scrolling row |
| G8 | Scattered/Random | Non-grid placement |
| G9 | Featured + Grid | One large + smaller grid |
| G10 | Staggered | Offset columns, rhythm variation |
| G11 | Filmstrip | Continuous horizontal with peek |
| G12 | Cluster | Grouped by relationship |

### Detail Page Split (D1-D12)

| Code | Style | Description |
|------|-------|-------------|
| D1 | 50/50 Horizontal | Media left, info right |
| D2 | 50/50 Reversed | Info left, media right |
| D3 | Stacked Vertical | Media above, info below |
| D4 | Media Dominant (70/30) | Large media, narrow info |
| D5 | Info Dominant (30/70) | Narrow media, wide info |
| D6 | Overlay | Info overlays media |
| D7 | Tabbed Panels | Switchable info sections |
| D8 | Full Bleed + Drawer | Full media, slide-out info |
| D9 | Centered Theater | Centered media, info below |
| D10 | Diptych | Media and info as equal artwork |
| D11 | Immersive Scroll | Info reveals on scroll over media |
| D12 | Specimen | Clinical isolation, whitespace |

### Card Design (C1-C12)

| Code | Style | Description |
|------|-------|-------------|
| C1 | Square | 1:1 aspect ratio |
| C2 | Portrait | Tall cards (2:3, 3:4) |
| C3 | Landscape | Wide cards (16:9, 3:2) |
| C4 | Text Row | Minimal/no image, text only |
| C5 | Large Preview | Oversized image, tiny info |
| C6 | Thumbnail + Details | Small image, lots of text |
| C7 | Circular/Rounded | Non-rectangular shape |
| C8 | Polaroid/Framed | Image with border/frame |
| C9 | Index Card | Catalog/file card style |
| C10 | Bleed | Image extends beyond container |
| C11 | Layered | Stacked paper effect |
| C12 | Specimen Slide | Scientific presentation |

### Motion Intensity (N1-N9)

| Code | Style | Key Techniques |
|------|-------|----------------|
| N1 | Static | Hover color changes, focus states only |
| N2 | Subtle | Hover lifts, button feedback, smooth transitions |
| N3 | Responsive | Fade-ins, staggered reveals, intersection-based |
| N4 | Parallax | 2-3 parallax layers, scroll-linked opacity/scale |
| N5 | Kinetic | Floating elements, breathing, gradient animation |
| N6 | Interactive | Magnetic buttons, 3D tilt cards, custom cursor |
| N7 | Cinematic | Mask wipes, shared element morphs, orchestrated timing |
| N8 | Immersive | WebGL, shaders, particle systems |
| N9 | Chaotic | Glitch, screen shake, unpredictable triggers |

**If N3+, read MOTION.md for implementation techniques.**

---

## Color Palettes

### Monochromatic & Minimal

| Palette | Hex Reference | Mood |
|---------|---------------|------|
| **Ink & Paper** | `#0D0D0D`, `#FAFAFA`, `#E63946` | Classic, editorial |
| **Warm Graphite** | `#2D2D2D`, `#6B6B6B`, `#F5F5DC` | Sophisticated, quiet |
| **Cool Steel** | `#708090`, `#C0C0C0`, `#F8F8FF` | Technical, precise |
| **Parchment** | `#FFFEF0`, `#704214`, `#8B4513` | Archival, aged |
| **Obsidian** | `#0D0D0D`, `#1A1A1A`, `#333333` | Luxury, weight |
| **Bone China** | `#F9F6F2`, `#E8E4DE`, `#9C9890` | Refined, delicate |

### Contemporary Digital

| Palette | Hex Reference | Mood |
|---------|---------------|------|
| **Linear** | `#5E6AD2`, `#FFFFFF`, `#F2F2F2` | SaaS precision |
| **Stripe** | `#635BFF`, `#00D4FF`, `#7A73FF` | Fintech polish |
| **Notion** | `#FFFFFF`, `#37352F`, `#9B9B9B` | Productivity calm |
| **Vercel** | `#000000`, `#FFFFFF` | Maximum contrast |
| **Raycast** | `#1A1625`, `#7C3AED`, `#F9FAFB` | Power user |

### Luxury & High Fashion

| Palette | Hex Reference | Mood |
|---------|---------------|------|
| **Old Money** | `#1B1B3A`, `#722F37`, `#F5F5DC`, `#D4AF37` | Heritage |
| **Bottega** | `#9CAF88`, `#A0522D`, `#F5F5DC` | Quiet luxury |
| **The Row** | `#FFFFF0`, `#C19A6B`, `#000000` | Understated wealth |
| **Loro Piana** | `#C4A96A`, `#FAF8F5`, `#5C5C5C` | Fabric luxury |

### Natural & Organic

| Palette | Hex Reference | Mood |
|---------|---------------|------|
| **Forest Floor** | `#4A5D23`, `#5C4033`, `#8B7355`, `#C19A6B` | Woodland |
| **Coastal Dawn** | `#B8C4C8`, `#A0917B`, `#7FCDCD` | Pacific morning |
| **Desert Dusk** | `#D2B48C`, `#B7553E`, `#2F2F2F`, `#DAA520` | Southwestern |
| **Alpine Stone** | `#696969`, `#F5F5F5`, `#2E4A3E`, `#363636` | Mountain mineral |

### Nostalgic & Retro

| Palette | Hex Reference | Mood |
|---------|---------------|------|
| **Kodachrome** | `#E34234`, `#1E90FF`, `#FFD700` | Film nostalgia |
| **Diner Booth** | `#DC143C`, `#FFFDD0`, `#98FF98` | 50s Americana |
| **Faded Polaroid** | `#E6D5AC`, `#C4A77D`, `#8B7355` | 70s photography |

### Architectural

| Palette | Hex Reference | Mood |
|---------|---------------|------|
| **Bauhaus** | `#BE1E2D`, `#21409A`, `#F8E81C`, `#FFFFFF`, `#000000` | Modernism |
| **Art Deco Lobby** | `#000000`, `#D4AF37`, `#FFFDD0`, `#00A86B` | Chrysler building |
| **Mid-Century** | `#FFFFFF`, `#40E0D0`, `#FF6B35`, `#8B5A2B` | Desert modern |
| **Tadao Ando** | `#A0A0A0`, `#E8E8E8`, `#4A4A4A` | Meditative space |

### Pop Culture

| Palette | Hex Reference | Mood |
|---------|---------------|------|
| **Criterion** | `#000000`, `#FFFFFF`, `#CC0000` | Film, curated |
| **A24** | `#3D3D3D`, `#8B8B8B`, `#FF4500` | Arthouse |
| **Wong Kar-wai** | `#FF355E`, `#00CED1`, `#1A1A2E` | Hong Kong cinema |

---

## Typography Pairings

### Swiss International
| Role | Font | Weight |
|------|------|--------|
| Headlines | Helvetica Neue | Bold |
| Body | Helvetica Neue | Regular |

*Alternatives: Suisse Int'l, Akzidenz-Grotesk*

### Editorial Luxury
| Role | Font | Weight |
|------|------|--------|
| Headlines | Canela | Light |
| Subheads | Founders Grotesk | Medium |
| Body | Freight Text | Regular |

*Alternatives: GT Sectra, Tiempos, Domaine*

### Technical Precision
| Role | Font | Weight |
|------|------|--------|
| Headlines | GT America Mono | Bold |
| Body | GT America | Regular |
| Data | JetBrains Mono | Regular |

*Alternatives: IBM Plex Mono, Berkeley Mono*

### Contemporary Neutral
| Role | Font | Weight |
|------|------|--------|
| Headlines | Söhne | Bold |
| Body | Söhne | Regular |
| Accent | Söhne Mono | Regular |

*Alternatives: ABC Diatype, Graphik, Untitled Sans*

### Quiet Luxury
| Role | Font | Weight |
|------|------|--------|
| Headlines | Sabon | Regular |
| Subheads | Apercu | Medium |
| Body | Caslon | Regular |

*Alternatives: Garamond Premier, Lyon Text*

---

## UX Archetypes

| Archetype | DNA Example | Key Features |
|-----------|-------------|--------------|
| **Editorial** | H1-L5-G2-D3-C2-N3 | Masthead, columns, pull quotes |
| **Archive** | H1-L6-G5-D7-C4-N2 | Dense data, tables, filters |
| **Gallery** | H8-L4-G1-D4-C1-N4 | Whitespace, hidden chrome |
| **Catalog** | H1-L1-G3-D1-C9-N2 | Index cards, provenance |
| **SaaS Minimal** | H1-L1-G3-D1-C1-N2 | Clean, systematic |
| **Fintech Premium** | H4-L6-G5-D7-C4-N3 | Data viz, gradients, trust |
| **Luxury Retail** | H8-L4-G1-D4-C1-N4 | Specimen isolation, whitespace |

---

## Banned Patterns

### Overused Themes (Hard Ban)
- **Brutalist** — raw concrete, harsh typography
- **Terminal/Hacker** — green-on-black, monospace everything
- **Mission Control/NASA** — telemetry, countdown timers
- **Zine/Punk** — xerox textures, collage
- **Medical/Clinical** — clipboard aesthetic
- **Arcade/Casino** — neon lights, pixel fonts

### Overused Elements
- Inter, Roboto, Open Sans fonts
- Blue as primary accent
- Generic 3-column card grid with uniform sizing
- Top navigation bar with logo left, links right (H1 default)
- Cards with subtle rounded corners and drop shadows
- Hover states that only change opacity

**If you find yourself reaching for these, stop and pick something else.**

---

## Variance Requirements

When generating multiple proposals, ensure differentiation:

| Axis | Must Vary |
|------|-----------|
| Header | Every proposal different H-code |
| Layout | Every proposal different L-code |
| Color Temperature | At least 2 different (Warm/Cool/Neutral) |
| Density | At least 2 different (Minimal/Balanced/Dense) |
| Motion | Spread across range (Low N1-3/Mid N4-6/High N7-9) |

**DNA must differ by ≥3 positions between any two proposals.**

---

## Agent Prompt Template

```
You are creating a PREVIEW PROPOSAL for a theme using REAL APP CONTENT.

## Captured App Content

{PAGES_CONTENT}
<!-- Orchestrator passes actual DOM/content captured via Playwright -->

## Assignment

Theme: {NAME}
DNA: {H#-L#-G#-D#-C#-N#}
References: {cite 2-3 SPECIFIC items from this file — not categories}
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
5. Banned patterns — not using any banned themes/elements?

Return: theme name, DNA, palette name, references, file path
```

---

## Quality Signals

### Micro-Details
- Consistent icon stroke weights
- Proper typographic quotes ("" not "")
- En-dashes for ranges, em-dashes for breaks
- Focus states for accessibility
- Empty states with personality

### Polish Indicators
- Smooth 60fps animations
- Loading states that maintain layout
- Responsive images at correct density
- No layout shift on load

### Red Flags (Avoid)
- Lorem ipsum in production
- Layout shift on load
- Broken hover states
- Mixed icon styles
- Flash of unstyled content
