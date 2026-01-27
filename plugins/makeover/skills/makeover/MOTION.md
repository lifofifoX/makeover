# Motion & Immersive Effects

Dynamic, scroll-driven, and interactive design elements. **Reference when designing proposals with motion.**

---

## Motion DNA (N Codes)

| Code | Style | Description | Key Techniques |
|------|-------|-------------|----------------|
| `N1` | **Static** | Essential only | Hover color, focus states |
| `N2` | **Subtle** | Micro-interactions | Hover lifts, button feedback, smooth transitions |
| `N3` | **Responsive** | Scroll-triggered | Fade-ins, staggered reveals, intersection-based |
| `N4` | **Parallax** | Layered depth | 2-3 parallax layers, scroll-linked opacity/scale |
| `N5` | **Kinetic** | Constant motion | Floating elements, breathing, gradient animation |
| `N6` | **Interactive** | Cursor-responsive | Magnetic buttons, tilt cards, custom cursor |
| `N7` | **Cinematic** | Dramatic reveals | Mask wipes, shared element morphs, orchestrated timing |
| `N8` | **Immersive** | Environmental | WebGL, shaders, particle systems |
| `N9` | **Chaotic** | Disruption | Screen shake, glitch, random triggers |

---

## Effect Catalog

### Scroll Effects

| Effect | Description | CSS Technique |
|--------|-------------|---------------|
| **Parallax layers** | Elements move at different scroll speeds | `animation-timeline: scroll()` with varying translateY |
| **Scroll-linked transform** | Element scales/rotates/fades based on scroll position | `animation-timeline: scroll()`, `animation-range` |
| **Sticky progression** | Element sticks, transforms while pinned | `position: sticky` + scroll-driven animation |
| **Horizontal scroll** | Vertical scroll moves content horizontally | Flex track with `translateX` on scroll |
| **Scroll snap** | Full-page sections with snap points | `scroll-snap-type: y mandatory` |

### Entrance Animations

| Effect | Description |
|--------|-------------|
| **Fade up** | Opacity 0→1, translateY 30px→0 |
| **Fade scale** | Opacity 0→1, scale 0.9→1 |
| **Fade blur** | Opacity 0→1, blur 10px→0 |
| **Clip reveal** | `clip-path` from inset/circle to full |
| **Staggered** | Children animate with incremental delays |
| **Split text** | Words/characters animate individually |

### Hover & Interaction

| Effect | Description |
|--------|-------------|
| **Magnetic button** | Element pulls toward cursor (requires JS) |
| **3D tilt card** | Card rotates toward cursor position (requires JS) |
| **Elastic scale** | Scale with spring easing, quick snap-back on active |
| **Underline grow** | Pseudo-element width 0→100% |
| **Image zoom** | Overflow hidden container, img scale on hover |
| **Desaturate** | grayscale(100%)→0% or reverse |

### Cursor Effects

| Effect | Description |
|--------|-------------|
| **Custom cursor** | Fixed element follows mouse, `cursor: none` on container |
| **Cursor trail** | Multiple elements with staggered transition delays |
| **Spotlight** | `mask-image: radial-gradient()` follows mouse position |

### Ambient Motion

| Effect | Description |
|--------|-------------|
| **Floating** | translateY oscillation with ease-in-out, staggered children |
| **Breathing** | Scale 1→1.05→1 pulse |
| **Gradient shift** | `background-position` animation on large gradient |
| **Particles** | Positioned elements with float animation (or tsParticles for complex) |
| **Film grain** | SVG noise overlay with subtle opacity |
| **Scan lines** | Repeating-linear-gradient stripes |

### Text Effects

| Effect | Description |
|--------|-------------|
| **Typewriter** | Width animation with steps(), blinking caret border |
| **Scramble** | Characters cycle through random before settling (requires JS) |
| **Wave** | Characters translateY with staggered delays |
| **Variable font** | `font-variation-settings` animation (requires variable font) |
| **Marquee** | Continuous translateX with duplicated content |

### 3D & Depth

| Effect | Description |
|--------|-------------|
| **Perspective rotate** | Container `perspective`, child `rotateY` on scroll |
| **Card flip** | `backface-visibility: hidden`, rotateY(180deg) |
| **Deep parallax** | Multiple layers with translateZ and scale compensation |

### Page Transitions

| Effect | Description |
|--------|-------------|
| **Crossfade** | Opacity out/in |
| **Slide** | translateX out/in |
| **Mask wipe** | clip-path circle/polygon animation |
| **Shared element** | `view-transition-name` (View Transitions API) |

### Glitch & Chaos (Wild Mode)

| Effect | Description |
|--------|-------------|
| **RGB split** | Pseudo-elements with offset colors and clip-paths |
| **Screen shake** | Random translate/rotate keyframes |
| **Corruption** | Burst of invert/hue-rotate/skew filters |
| **Flicker** | Irregular opacity keyframes |

---

## Implementation Notes

### CSS-Only (Safe for Proposals)

All transitions, keyframe animations, scroll-driven animations (`animation-timeline`), hover/focus states.

### Requires JavaScript

| Effect | Library Options |
|--------|-----------------|
| Complex parallax | Lenis, Locomotive Scroll |
| Physics/spring | Framer Motion, GSAP |
| Cursor tracking | Custom (mouse position → CSS vars) |
| Particle systems | tsParticles |
| 3D scenes | Three.js |
| Text scramble | Custom implementation |

### Performance

```css
.animated { will-change: transform, opacity; }
```

Remove `will-change` after animation completes.

### Accessibility

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

### Mobile

Disable heavy effects (parallax, particles, custom cursor) on touch devices:
```css
@media (hover: none), (max-width: 768px) {
  .parallax-layer { transform: none !important; }
  .particles, .cursor-custom { display: none; }
}
```

---

## Motion in Proposals

### 1. Declare Motion Level

```
DNA: H4-L5-G2-D8-C2-N4
Motion Level: N4 (Parallax)
```

### 2. Specify Effects

```markdown
## Motion Design

### Scroll: 3-layer parallax hero, staggered card reveals
### Hover: Elastic buttons, image zoom, underline grow
### Ambient: Floating decorations, subtle grain
### JS Required: Magnetic buttons, smooth scroll (Lenis)
```

### 3. Demonstrate in Preview

Working CSS animations for:
- At least one scroll effect
- All hover states
- Any ambient motion

---

## Motion by Theme Type

| Type | Level | Effects |
|------|-------|---------|
| Editorial | N2-N3 | Fade-up reveals, elegant underlines, image zoom |
| Gallery | N3-N4 | Parallax hero, staggered grid, lightbox zoom |
| Dashboard | N2 | Chart animations, micro-interactions, skeleton loaders |
| Brutalist | N5-N6 | Aggressive hovers, cursor effects, constant motion |
| Wild | N7-N9 | Glitch, shake, chaotic particles, unpredictable timing |
