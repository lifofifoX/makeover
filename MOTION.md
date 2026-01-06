# Motion & Immersive Effects

Dynamic, scroll-driven, and interactive design elements that bring themes to life. **Read this file when designing proposals that need motion.**

---

## Motion DNA (N Codes)

Every theme should declare a motion intensity level:

| Code | Style | Description | Techniques |
|------|-------|-------------|------------|
| `N1` | **Static** | Minimal animation, only essential | Hover color changes, focus states |
| `N2` | **Subtle** | Micro-interactions, polish | Hover lifts, button feedback, smooth transitions |
| `N3` | **Responsive** | Scroll-triggered, entrance animations | Fade-ins, staggered reveals, intersection-based |
| `N4` | **Parallax** | Layered depth, scroll-linked movement | 2-3 parallax layers, scroll-linked opacity |
| `N5` | **Kinetic** | Constant ambient motion | Floating elements, breathing, gradient animation |
| `N6` | **Interactive** | Cursor-responsive, physics | Magnetic buttons, tilt cards, cursor effects |
| `N7` | **Cinematic** | Dramatic reveals, page transitions | Mask wipes, shared element morphs, orchestrated timing |
| `N8` | **Immersive** | 3D space, environmental effects | WebGL, shaders, particle systems, spatial audio hooks |
| `N9` | **Chaotic** | Glitch, disruption, unpredictable | Screen shake, corruption, random triggers |

**Extended DNA format:** `H4-L5-G2-D8-C2-N4` (includes motion level)

---

## Effect Categories

### Scroll Effects

#### Parallax Layering

Multiple elements moving at different speeds relative to scroll:

```css
/* CSS-only parallax with scroll-timeline */
@keyframes parallax-slow {
  from { transform: translateY(0); }
  to { transform: translateY(-100px); }
}

@keyframes parallax-fast {
  from { transform: translateY(0); }
  to { transform: translateY(-300px); }
}

.parallax-layer-back {
  animation: parallax-slow linear;
  animation-timeline: scroll();
}

.parallax-layer-front {
  animation: parallax-fast linear;
  animation-timeline: scroll();
}
```

**Variations:**
| Type | Description | Use Case |
|------|-------------|----------|
| **Vertical parallax** | Layers move up/down at different rates | Hero sections, backgrounds |
| **Horizontal parallax** | Side-to-side movement on scroll | Decorative elements |
| **Depth parallax** | Scale + translate for z-axis illusion | Immersive intros |
| **Rotational parallax** | Elements rotate as you scroll | Playful, dynamic |
| **Opacity parallax** | Fade in/out based on scroll position | Text reveals, transitions |

#### Scroll-Linked Transformations

Elements that transform continuously with scroll position:

```css
/* Element scales from 0.5 to 1 over scroll */
.scale-on-scroll {
  animation: scale-up linear;
  animation-timeline: scroll();
  animation-range: entry 0% cover 50%;
}

@keyframes scale-up {
  from { transform: scale(0.5); opacity: 0; }
  to { transform: scale(1); opacity: 1; }
}
```

**Transform properties to animate:**
- `translateX/Y/Z` — position shifts
- `scale` — grow/shrink
- `rotate` — spinning
- `skew` — perspective distortion
- `opacity` — fade
- `blur` — focus/defocus
- `clip-path` — shape reveals

#### Sticky with Progression

Element sticks, then transforms while pinned:

```css
.sticky-section {
  position: sticky;
  top: 0;
  height: 300vh; /* Scroll distance while sticky */
}

.sticky-content {
  animation: sticky-transform linear;
  animation-timeline: scroll(nearest);
}

@keyframes sticky-transform {
  0% { transform: scale(1); }
  50% { transform: scale(1.5); }
  100% { transform: scale(1) translateY(-100%); }
}
```

**Use cases:**
- Hero that zooms into content
- Image that reveals text underneath
- Card that flips to show details
- Counter that ticks up as you scroll

#### Horizontal Scroll Sections

Convert vertical scroll to horizontal movement:

```css
.horizontal-scroll-container {
  overflow-x: hidden;
}

.horizontal-scroll-track {
  display: flex;
  width: 400vw; /* 4 screens wide */
  animation: scroll-horizontal linear;
  animation-timeline: scroll(nearest block);
}

@keyframes scroll-horizontal {
  to { transform: translateX(-75%); }
}
```

**Enhance with:**
- Parallax within horizontal sections
- Items that animate as they enter center
- Progress indicator

#### Scroll Snap with Transitions

Full-page sections with animated transitions between:

```css
.snap-container {
  scroll-snap-type: y mandatory;
  overflow-y: scroll;
  height: 100vh;
}

.snap-section {
  scroll-snap-align: start;
  height: 100vh;

  /* Animate when section is active */
  animation: section-enter linear;
  animation-timeline: view();
}

@keyframes section-enter {
  0% { opacity: 0; transform: translateY(50px); }
  10%, 90% { opacity: 1; transform: translateY(0); }
  100% { opacity: 0; transform: translateY(-50px); }
}
```

---

### Entrance Animations

#### Fade Variations

```css
/* Fade up */
@keyframes fade-up {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

/* Fade scale */
@keyframes fade-scale {
  from { opacity: 0; transform: scale(0.9); }
  to { opacity: 1; transform: scale(1); }
}

/* Fade blur */
@keyframes fade-blur {
  from { opacity: 0; filter: blur(10px); }
  to { opacity: 1; filter: blur(0); }
}
```

#### Clip Reveals

```css
/* Wipe from left */
@keyframes clip-left {
  from { clip-path: inset(0 100% 0 0); }
  to { clip-path: inset(0 0 0 0); }
}

/* Circle expand */
@keyframes clip-circle {
  from { clip-path: circle(0% at 50% 50%); }
  to { clip-path: circle(100% at 50% 50%); }
}

/* Diagonal wipe */
@keyframes clip-diagonal {
  from { clip-path: polygon(0 0, 0 0, 0 100%, 0 100%); }
  to { clip-path: polygon(0 0, 100% 0, 100% 100%, 0 100%); }
}
```

#### Staggered Entrances

```css
.stagger-container > * {
  animation: fade-up 0.6s ease-out backwards;
}

.stagger-container > *:nth-child(1) { animation-delay: 0ms; }
.stagger-container > *:nth-child(2) { animation-delay: 100ms; }
.stagger-container > *:nth-child(3) { animation-delay: 200ms; }
.stagger-container > *:nth-child(4) { animation-delay: 300ms; }
/* ... */

/* Or use CSS custom properties */
.stagger-item {
  animation-delay: calc(var(--index) * 100ms);
}
```

#### Split Text Reveals

```css
/* Word by word */
.split-words span {
  display: inline-block;
  animation: word-reveal 0.5s ease-out backwards;
  animation-delay: calc(var(--word-index) * 0.1s);
}

@keyframes word-reveal {
  from {
    opacity: 0;
    transform: translateY(100%) rotateX(-90deg);
    transform-origin: top;
  }
  to {
    opacity: 1;
    transform: translateY(0) rotateX(0);
  }
}

/* Character by character */
.split-chars span {
  display: inline-block;
  animation: char-reveal 0.3s ease-out backwards;
  animation-delay: calc(var(--char-index) * 0.03s);
}

@keyframes char-reveal {
  from { opacity: 0; transform: translateY(-50%); }
  to { opacity: 1; transform: translateY(0); }
}
```

---

### Hover & Interaction Effects

#### Magnetic Buttons

Elements that pull toward cursor:

```javascript
// Requires JS - note in proposal
button.addEventListener('mousemove', (e) => {
  const rect = button.getBoundingClientRect();
  const x = e.clientX - rect.left - rect.width / 2;
  const y = e.clientY - rect.top - rect.height / 2;

  button.style.transform = `translate(${x * 0.3}px, ${y * 0.3}px)`;
});

button.addEventListener('mouseleave', () => {
  button.style.transform = 'translate(0, 0)';
});
```

```css
.magnetic-btn {
  transition: transform 0.3s cubic-bezier(0.33, 1, 0.68, 1);
}
```

#### 3D Tilt Cards

Cards that tilt toward cursor:

```css
.tilt-card {
  transform-style: preserve-3d;
  perspective: 1000px;
  transition: transform 0.1s ease-out;
}

.tilt-card:hover {
  /* JS sets --rotateX and --rotateY based on cursor position */
  transform: rotateX(var(--rotateX, 0)) rotateY(var(--rotateY, 0));
}

.tilt-card-content {
  transform: translateZ(50px); /* Pops forward */
}
```

#### Elastic Hover

```css
.elastic-btn {
  transition: transform 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
}

.elastic-btn:hover {
  transform: scale(1.1);
}

.elastic-btn:active {
  transform: scale(0.95);
  transition-duration: 0.1s;
}
```

#### Underline Animations

```css
/* Grow from left */
.underline-grow {
  position: relative;
}

.underline-grow::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 2px;
  background: currentColor;
  transition: width 0.3s ease-out;
}

.underline-grow:hover::after {
  width: 100%;
}

/* Slide in from left, out to right */
.underline-slide {
  background: linear-gradient(currentColor, currentColor) no-repeat;
  background-size: 0% 2px;
  background-position: left bottom;
  transition: background-size 0.3s ease;
}

.underline-slide:hover {
  background-size: 100% 2px;
}
```

#### Image Hover Effects

```css
/* Zoom within container */
.img-zoom {
  overflow: hidden;
}

.img-zoom img {
  transition: transform 0.5s ease-out;
}

.img-zoom:hover img {
  transform: scale(1.1);
}

/* Color to B&W (or reverse) */
.img-desaturate img {
  filter: grayscale(100%);
  transition: filter 0.3s ease;
}

.img-desaturate:hover img {
  filter: grayscale(0%);
}

/* Reveal overlay */
.img-reveal .overlay {
  opacity: 0;
  transform: translateY(20px);
  transition: all 0.3s ease;
}

.img-reveal:hover .overlay {
  opacity: 1;
  transform: translateY(0);
}
```

---

### Cursor Effects

#### Custom Cursor

```css
/* Hide default cursor */
.custom-cursor-area {
  cursor: none;
}

/* Custom cursor element */
.cursor {
  position: fixed;
  pointer-events: none;
  width: 20px;
  height: 20px;
  border: 2px solid var(--color-accent);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  transition: transform 0.1s, width 0.2s, height 0.2s;
  z-index: 10000;
  mix-blend-mode: difference;
}

/* Expanded state on interactive elements */
.cursor.is-active {
  width: 50px;
  height: 50px;
  border-color: var(--color-primary);
}
```

#### Cursor Trail

```css
.cursor-trail {
  position: fixed;
  pointer-events: none;
  width: 8px;
  height: 8px;
  background: var(--color-accent);
  border-radius: 50%;
  opacity: 0.5;
  z-index: 9999;
}

/* Multiple trail elements with delays */
.cursor-trail:nth-child(1) { transition: all 0.05s; }
.cursor-trail:nth-child(2) { transition: all 0.1s; }
.cursor-trail:nth-child(3) { transition: all 0.15s; }
/* ... creates trailing effect */
```

#### Spotlight/Flashlight

```css
.spotlight-container {
  position: relative;
  background: #000;
}

.spotlight-content {
  /* Visible area follows cursor */
  mask-image: radial-gradient(
    circle 150px at var(--mouse-x) var(--mouse-y),
    black 0%,
    transparent 100%
  );
  -webkit-mask-image: radial-gradient(
    circle 150px at var(--mouse-x) var(--mouse-y),
    black 0%,
    transparent 100%
  );
}
```

---

### Ambient Motion

#### Floating Elements

```css
@keyframes float {
  0%, 100% { transform: translateY(0) rotate(0deg); }
  25% { transform: translateY(-10px) rotate(1deg); }
  50% { transform: translateY(-5px) rotate(-1deg); }
  75% { transform: translateY(-15px) rotate(0.5deg); }
}

.floating {
  animation: float 6s ease-in-out infinite;
}

/* Offset multiple elements */
.floating:nth-child(2) { animation-delay: -1.5s; }
.floating:nth-child(3) { animation-delay: -3s; }
.floating:nth-child(4) { animation-delay: -4.5s; }
```

#### Breathing/Pulsing

```css
@keyframes breathe {
  0%, 100% { transform: scale(1); opacity: 0.8; }
  50% { transform: scale(1.05); opacity: 1; }
}

.breathing {
  animation: breathe 4s ease-in-out infinite;
}

/* Subtle glow pulse */
@keyframes glow-pulse {
  0%, 100% { box-shadow: 0 0 20px rgba(255,107,107,0.3); }
  50% { box-shadow: 0 0 40px rgba(255,107,107,0.6); }
}
```

#### Gradient Animation

```css
@keyframes gradient-shift {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}

.animated-gradient {
  background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
  background-size: 400% 400%;
  animation: gradient-shift 15s ease infinite;
}
```

#### Particle Systems

```css
/* CSS-only particles (limited but no JS) */
.particles {
  position: absolute;
  inset: 0;
  overflow: hidden;
  pointer-events: none;
}

.particle {
  position: absolute;
  width: 4px;
  height: 4px;
  background: var(--color-accent);
  border-radius: 50%;
  animation: particle-float 10s infinite linear;
}

@keyframes particle-float {
  0% {
    transform: translateY(100vh) translateX(0);
    opacity: 0;
  }
  10% { opacity: 1; }
  90% { opacity: 1; }
  100% {
    transform: translateY(-100vh) translateX(100px);
    opacity: 0;
  }
}

/* Distribute randomly with nth-child */
.particle:nth-child(1) { left: 10%; animation-delay: 0s; animation-duration: 12s; }
.particle:nth-child(2) { left: 30%; animation-delay: -3s; animation-duration: 8s; }
/* ... generate 20-50 particles */
```

**For complex particles, note:** "Enhanced with tsParticles for [effect]"

#### Film Grain/Noise

```css
.grain-overlay {
  position: fixed;
  inset: 0;
  pointer-events: none;
  z-index: 9998;
  opacity: 0.05;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)'/%3E%3C/svg%3E");
}

/* Animated grain */
@keyframes grain {
  0%, 100% { transform: translate(0, 0); }
  10% { transform: translate(-5%, -10%); }
  20% { transform: translate(-15%, 5%); }
  30% { transform: translate(7%, -25%); }
  40% { transform: translate(-5%, 25%); }
  50% { transform: translate(-15%, 10%); }
  60% { transform: translate(15%, 0%); }
  70% { transform: translate(0%, 15%); }
  80% { transform: translate(3%, 35%); }
  90% { transform: translate(-10%, 10%); }
}

.animated-grain {
  animation: grain 0.5s steps(10) infinite;
}
```

#### Scan Lines

```css
.scanlines {
  position: fixed;
  inset: 0;
  pointer-events: none;
  z-index: 9997;
  background: repeating-linear-gradient(
    0deg,
    rgba(0, 0, 0, 0.15),
    rgba(0, 0, 0, 0.15) 1px,
    transparent 1px,
    transparent 2px
  );
}

/* Animated scan line */
@keyframes scan {
  0% { transform: translateY(-100%); }
  100% { transform: translateY(100vh); }
}

.scanning-line {
  position: fixed;
  left: 0;
  right: 0;
  height: 4px;
  background: linear-gradient(
    transparent,
    rgba(255, 255, 255, 0.1),
    transparent
  );
  animation: scan 8s linear infinite;
  pointer-events: none;
}
```

---

### Text Effects

#### Typewriter

```css
.typewriter {
  overflow: hidden;
  white-space: nowrap;
  border-right: 3px solid;
  animation:
    typing 3s steps(40, end),
    blink-caret 0.75s step-end infinite;
}

@keyframes typing {
  from { width: 0; }
  to { width: 100%; }
}

@keyframes blink-caret {
  50% { border-color: transparent; }
}
```

#### Scramble/Decode

```javascript
// Requires JS - note in proposal
// Characters scramble then resolve to final text
class TextScramble {
  // Implementation creates cipher effect
  // Characters cycle through random letters before settling
}
```

**CSS approximation for proposals:**
```css
.scramble-text {
  animation: scramble 0.5s steps(10);
}

@keyframes scramble {
  0% { opacity: 0; letter-spacing: 10px; filter: blur(5px); }
  50% { opacity: 0.5; letter-spacing: 5px; filter: blur(2px); }
  100% { opacity: 1; letter-spacing: normal; filter: blur(0); }
}
```

#### Wave Text

```css
.wave-text span {
  display: inline-block;
  animation: wave 1s ease-in-out infinite;
  animation-delay: calc(var(--char-index) * 0.05s);
}

@keyframes wave {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
}
```

#### Variable Font Animation

```css
/* Requires variable font */
@keyframes weight-shift {
  0%, 100% { font-variation-settings: 'wght' 300; }
  50% { font-variation-settings: 'wght' 900; }
}

.variable-text {
  font-family: 'Inter', sans-serif; /* Variable font */
  animation: weight-shift 3s ease-in-out infinite;
}

/* Staggered per character */
.variable-text span {
  animation: weight-shift 2s ease-in-out infinite;
  animation-delay: calc(var(--char-index) * 0.1s);
}
```

#### Marquee

```css
.marquee {
  overflow: hidden;
  white-space: nowrap;
}

.marquee-content {
  display: inline-block;
  animation: marquee 20s linear infinite;
}

@keyframes marquee {
  from { transform: translateX(0); }
  to { transform: translateX(-50%); }
}

/* Duplicate content for seamless loop */
.marquee-content::after {
  content: attr(data-text);
  padding-left: 50px;
}
```

---

### 3D & Depth Effects

#### Perspective Transforms

```css
.perspective-container {
  perspective: 1000px;
  perspective-origin: center;
}

.perspective-element {
  transform: rotateY(15deg);
  transform-style: preserve-3d;
}

/* On scroll, rotate */
.scroll-rotate {
  animation: rotate-in linear;
  animation-timeline: view();
}

@keyframes rotate-in {
  from { transform: rotateY(45deg) translateZ(-200px); opacity: 0; }
  to { transform: rotateY(0) translateZ(0); opacity: 1; }
}
```

#### Card Flip

```css
.flip-card {
  perspective: 1000px;
  width: 300px;
  height: 400px;
}

.flip-card-inner {
  width: 100%;
  height: 100%;
  transition: transform 0.6s;
  transform-style: preserve-3d;
}

.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

.flip-card-front,
.flip-card-back {
  position: absolute;
  inset: 0;
  backface-visibility: hidden;
}

.flip-card-back {
  transform: rotateY(180deg);
}
```

#### Layered Parallax (5+ layers)

```css
.deep-parallax {
  height: 100vh;
  perspective: 1px;
  perspective-origin: center center;
  overflow-x: hidden;
  overflow-y: scroll;
}

.parallax-layer {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Further = slower scroll */
.layer-1 { transform: translateZ(-4px) scale(5); z-index: 1; }
.layer-2 { transform: translateZ(-3px) scale(4); z-index: 2; }
.layer-3 { transform: translateZ(-2px) scale(3); z-index: 3; }
.layer-4 { transform: translateZ(-1px) scale(2); z-index: 4; }
.layer-5 { transform: translateZ(0); z-index: 5; }
```

---

### Page Transitions

#### Crossfade

```css
@keyframes page-fade-out {
  to { opacity: 0; }
}

@keyframes page-fade-in {
  from { opacity: 0; }
}

/* Apply to page containers */
.page-exit { animation: page-fade-out 0.3s forwards; }
.page-enter { animation: page-fade-in 0.3s; }
```

#### Slide

```css
@keyframes slide-out-left {
  to { transform: translateX(-100%); }
}

@keyframes slide-in-right {
  from { transform: translateX(100%); }
}
```

#### Mask Wipe

```css
@keyframes wipe-out {
  to { clip-path: circle(0% at 50% 50%); }
}

@keyframes wipe-in {
  from { clip-path: circle(0% at 50% 50%); }
  to { clip-path: circle(150% at 50% 50%); }
}
```

#### Shared Element Morph

```css
/* View Transitions API (modern browsers) */
.shared-element {
  view-transition-name: hero-image;
}

::view-transition-old(hero-image),
::view-transition-new(hero-image) {
  animation-duration: 0.5s;
}
```

---

### Glitch & Chaos (Wild Mode)

#### RGB Split

```css
.glitch-text {
  position: relative;
}

.glitch-text::before,
.glitch-text::after {
  content: attr(data-text);
  position: absolute;
  inset: 0;
}

.glitch-text::before {
  color: #ff0000;
  animation: glitch-1 2s infinite linear alternate-reverse;
  clip-path: polygon(0 0, 100% 0, 100% 45%, 0 45%);
}

.glitch-text::after {
  color: #00ffff;
  animation: glitch-2 3s infinite linear alternate-reverse;
  clip-path: polygon(0 55%, 100% 55%, 100% 100%, 0 100%);
}

@keyframes glitch-1 {
  0%, 100% { transform: translateX(0); }
  20% { transform: translateX(-3px); }
  40% { transform: translateX(3px); }
  60% { transform: translateX(-1px); }
  80% { transform: translateX(2px); }
}

@keyframes glitch-2 {
  0%, 100% { transform: translateX(0); }
  20% { transform: translateX(3px); }
  40% { transform: translateX(-3px); }
  60% { transform: translateX(1px); }
  80% { transform: translateX(-2px); }
}
```

#### Screen Shake

```css
@keyframes shake {
  0%, 100% { transform: translate(0, 0) rotate(0); }
  10% { transform: translate(-5px, -5px) rotate(-1deg); }
  20% { transform: translate(5px, -5px) rotate(1deg); }
  30% { transform: translate(-5px, 5px) rotate(0deg); }
  40% { transform: translate(5px, 5px) rotate(1deg); }
  50% { transform: translate(-5px, -5px) rotate(-1deg); }
  60% { transform: translate(5px, -5px) rotate(0deg); }
  70% { transform: translate(-5px, 5px) rotate(-1deg); }
  80% { transform: translate(-5px, -5px) rotate(1deg); }
  90% { transform: translate(5px, -5px) rotate(0deg); }
}

.shake-trigger:hover {
  animation: shake 0.5s ease-in-out;
}
```

#### Corruption/Static Burst

```css
@keyframes corrupt {
  0%, 90%, 100% {
    filter: none;
    transform: none;
  }
  92% {
    filter: invert(1) hue-rotate(90deg);
    transform: skewX(5deg);
  }
  94% {
    filter: saturate(5) contrast(2);
    transform: skewX(-5deg) scale(1.02);
  }
  96% {
    filter: invert(1);
    transform: translateX(5px);
  }
  98% {
    filter: hue-rotate(180deg) saturate(3);
    transform: translateX(-5px) skewY(2deg);
  }
}

.corruption-loop {
  animation: corrupt 5s infinite;
}
```

#### Flicker

```css
@keyframes flicker {
  0%, 100% { opacity: 1; }
  41% { opacity: 1; }
  42% { opacity: 0.8; }
  43% { opacity: 1; }
  45% { opacity: 0.3; }
  46% { opacity: 1; }
  50% { opacity: 1; }
  51% { opacity: 0.6; }
  52% { opacity: 1; }
  53% { opacity: 0.9; }
  54% { opacity: 1; }
}

.flicker {
  animation: flicker 3s infinite;
}
```

---

## Implementation Notes

### CSS-Only (Safe for Proposals)

These work without JavaScript:
- All transitions and transforms
- Keyframe animations
- Scroll-driven animations (`animation-timeline: scroll()`)
- Hover/focus states
- Media queries for reduced motion

### Requires JavaScript (Note in Proposal)

Document these as enhancement opportunities:

| Effect | Library | Note |
|--------|---------|------|
| Complex parallax | Lenis, Locomotive Scroll | Smooth scroll + parallax |
| Physics animations | Framer Motion, GSAP | Spring, inertia, complex timing |
| Cursor tracking | Custom | Mouse position → CSS variables |
| Particle systems | tsParticles, particles.js | Many moving elements |
| 3D scenes | Three.js, React Three Fiber | WebGL required |
| Shaders | GLSL, ShaderToy | Distortion, liquid effects |
| Scroll hijacking | Scrollama, GSAP ScrollTrigger | Precise scroll control |
| Text scramble | Custom | Character-by-character |
| View Transitions | Native API | Page-to-page morphs |

### Performance Considerations

```css
/* GPU acceleration */
.animated-element {
  will-change: transform, opacity;
  transform: translateZ(0); /* Force GPU layer */
}

/* Clean up will-change after animation */
.animated-element.animation-complete {
  will-change: auto;
}
```

### Accessibility

```css
/* Respect reduced motion preference */
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}

/* Provide motion toggle */
[data-reduce-motion="true"] * {
  animation: none !important;
  transition: none !important;
}
```

### Mobile Considerations

```css
/* Disable heavy effects on mobile */
@media (max-width: 768px) {
  .parallax-layer {
    transform: none !important;
  }

  .particles {
    display: none;
  }

  .cursor-custom {
    display: none;
  }
}

/* Reduce complexity on low-power devices */
@media (hover: none) {
  /* Touch devices - simplify hover effects */
  .hover-effect:hover {
    transform: none;
  }
}
```

---

## Motion in Proposals

When creating proposals, include:

### 1. Motion DNA Declaration

```
DNA: H4-L5-G2-D8-C2-N4
Motion Level: N4 (Parallax)
```

### 2. Motion Specification Section

```markdown
## Motion Design

### Scroll Effects
- Hero: 3-layer parallax (clouds, mountains, foreground)
- Cards: Stagger fade-up on scroll (100ms delay each)
- Section transitions: Opacity crossfade

### Interactions
- Buttons: Elastic scale (1.05) with spring easing
- Cards: Subtle lift (translateY -4px) + shadow expansion
- Links: Underline grow from left

### Ambient
- Floating decorative elements (6s cycle)
- Subtle grain overlay (0.03 opacity)
- Gradient background shift (20s cycle)

### Enhancements (JS Required)
- Magnetic button effect on CTAs
- Cursor follower with blend mode
- Smooth scroll with Lenis
```

### 3. Demonstrate in Preview

The HTML preview should include working CSS animations for:
- At least one scroll-triggered effect
- Hover states on all interactive elements
- Any ambient motion
- Loading/entrance animations

---

## Motion by Theme Type

### Editorial (N2-N3)
- Subtle fade-up on scroll
- Elegant underline animations
- Image zoom on hover
- Smooth page transitions

### Gallery (N3-N4)
- Parallax hero images
- Staggered grid reveals
- Lightbox zoom animations
- Crossfade between pieces

### Dashboard (N2)
- Chart animations on load
- Micro-interactions on controls
- Skeleton loaders
- Toast slide-ins

### Brutalist (N5-N6)
- Aggressive hover effects
- Cursor interactions
- Constant ambient motion
- Disruptive transitions

### Wild Mode (N7-N9)
- Glitch effects
- Screen disruption
- Chaotic particles
- Unpredictable timing
