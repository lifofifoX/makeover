# Design Craft

Principles that separate elite design from merely good design. **Read before generating proposals.**

---

## The Elite Design Mindset

### 1. Restraint Over Decoration

Elite designers know when NOT to design. They remove elements rather than add them.

**The Removal Test:**
Look at your design and ask: "What can I remove without losing function or clarity?"
- If nothing can be removed, you've achieved elegance
- If things can be removed, remove them
- Repeat until removal would cause harm

**Signs of Over-Design (Avoid):**
- Gradients where flat color would work
- Shadows on elements that don't need depth
- Borders around things that don't need containment
- Icons next to text that's already clear
- Multiple visual treatments competing for attention
- Decorative elements that don't serve hierarchy

**The Confidence of Simplicity:**
A single strong idea executed with conviction beats three competing ideas hedged together. Pick one direction and commit.

### 2. Systematic Thinking

Elite design is built on systems, not individual decisions. Every choice relates to every other choice.

**What This Means:**
- If you use 16px somewhere, there's a reason it's 16px
- If you use #333 for text, you know why it's not #222 or #444
- Every spacing value comes from a scale
- Every color has a defined role

**Ask Yourself:**
- "Why this value and not another?"
- "How does this relate to the rest of the system?"
- "Would I make this same choice if I saw only the component in isolation?"

### 3. Hierarchy Through Reduction

Don't add emphasis to make things stand out. Remove competing elements.

| Weak Approach | Strong Approach |
|---------------|-----------------|
| Make the CTA button bigger | Reduce visual weight of surrounding elements |
| Add bold + color + size to headline | Let headline be the only large element |
| Use icons + labels + colors | Pick the single strongest differentiator |

**The Squint Test:**
Blur your vision or step back from the screen. The hierarchy should still be obvious. If everything blurs into sameness, your hierarchy is weak.

---

## Spacing & Rhythm

### The Spacing Scale

**Always use a scale.** Never use arbitrary values.

Recommended base-8 scale:
```
4px  - micro (icon padding, tight gaps)
8px  - small (related element gaps)
12px - medium-small
16px - medium (comfortable breathing room)
24px - large (section gaps)
32px - x-large (major section breaks)
48px - 2x-large
64px - 3x-large (page-level divisions)
```

**The Rule:** Every spacing value in your design should appear in this list. If you need 17px, you're doing it wrong.

### Vertical Rhythm

Text should sit on an invisible baseline grid. This creates subconscious order.

```css
/* Base line height establishes rhythm */
--baseline: 8px;
--line-height-body: 24px; /* 3 × baseline */
--line-height-heading: 32px; /* 4 × baseline */

/* Spacing between elements follows rhythm */
--space-after-heading: 16px; /* 2 × baseline */
--space-after-paragraph: 24px; /* 3 × baseline */
```

### Component Internal Spacing

Spacing inside components should be consistent and proportional:

```
Button padding: horizontal = 2× vertical
Card padding: consistent on all sides, or bottom slightly more
Input padding: match button padding for visual alignment
```

---

## Typography Craft

### Micro-Typography (What Separates Pros)

**Proper Punctuation:**
| Wrong | Right | Character |
|-------|-------|-----------|
| "quotes" | "quotes" | Curly quotes (U+201C, U+201D) |
| 'apostrophe' | 'apostrophe' | Curly apostrophe (U+2019) |
| 10-20 | 10–20 | En dash for ranges (U+2013) |
| word - word | word — word | Em dash for breaks (U+2014) |
| ... | … | Ellipsis character (U+2026) |

**Letterspacing by Size:**
- Headlines (24px+): Tighten slightly (-0.01em to -0.02em)
- Body text (14-18px): Default tracking (0)
- Small text (12px-): Loosen slightly (+0.01em to +0.02em)
- ALL CAPS: Always loosen (+0.05em to +0.1em)

**Line Length:**
- Optimal: 45-75 characters per line
- Maximum: 90 characters
- Short measure (sidebars): 30-40 characters

**Line Height by Size:**
```
Small text (12-14px): 1.6-1.7
Body text (16-18px): 1.5-1.6
Subheadings (20-24px): 1.3-1.4
Headlines (32px+): 1.1-1.2
Display (48px+): 1.0-1.1
```

### Font Pairing Rules

**The 2-Font Maximum:**
Use at most 2 typeface families. More creates chaos.

**Pairing Strategies:**
1. **Serif + Sans:** Classic, reliable (Freight Text + Founders Grotesk)
2. **Display + Neutral:** Impact + readability (Druk + Inter)
3. **Mono + Sans:** Technical + human (JetBrains Mono + Inter)
4. **Same Family:** Different weights/styles (Söhne + Söhne Mono)

**Avoid:**
- Two fonts that are too similar (why bother?)
- Two fonts that are both decorative (chaos)
- Fonts from different eras that clash (Victorian serif + geometric sans)

### Optical Alignment

Mathematical centering isn't always visual centering.

**Text in Buttons:**
Text often needs 1-2px more padding on bottom than top to appear centered.

**Icons Next to Text:**
Icons may need slight vertical offset to align with text x-height.

**Play Buttons:**
Triangle play icons need to shift right slightly to appear centered in circles.

---

## Color Sophistication

### Why Pure Black is Usually Wrong

`#000000` against `#FFFFFF` creates:
- Excessive contrast that causes eye strain
- Halation (text appears to vibrate)
- A harsh, digital feeling

**Instead:**
- Dark text: `#1a1a1a`, `#171717`, `#0d0d0d`
- Dark backgrounds: `#0a0a0a`, `#111111`, `#0f0f0f`

### Neutral Temperature

Every neutral has an undertone. Be intentional.

| Temperature | Hex Example | Feels Like |
|-------------|-------------|------------|
| Warm gray | `#8B8680` | Cozy, organic, sophisticated |
| True gray | `#808080` | Neutral, digital, cold |
| Cool gray | `#788084` | Technical, modern, clean |
| Blue-gray | `#64748B` | Professional, corporate |
| Green-gray | `#6B7A6F` | Natural, calm |

**Consistency Rule:** All neutrals in your palette should share the same temperature undertone.

### The 60-30-10 Rule

For balanced palettes:
- 60%: Dominant (background, large surfaces)
- 30%: Secondary (cards, containers, supporting)
- 10%: Accent (CTAs, highlights, emphasis)

### Color Relationships

**Don't just pick colors. Design relationships:**

1. **Background to Surface:** Surface should be 1-2 steps lighter/darker, not drastically different
2. **Text to Background:** WCAG AA minimum (4.5:1), AAA preferred (7:1)
3. **Accent to Neutral:** Accent should pop against both background and surface
4. **Border to Surface:** Borders should be visible but not prominent (low contrast)

### Opacity Over New Colors

Instead of defining 47 gray values, use opacity:

```css
--color-text-primary: #1a1a1a;
--color-text-secondary: rgba(26, 26, 26, 0.7);
--color-text-muted: rgba(26, 26, 26, 0.5);
--color-border: rgba(26, 26, 26, 0.1);
```

This ensures automatic harmony and reduces palette complexity.

---

## The Anti-AI Checklist

**AI-generated designs often exhibit these tells. Actively avoid them:**

### Visual Tells

| AI Pattern | Elite Alternative |
|------------|-------------------|
| Gradient backgrounds on everything | Flat colors, strategic gradient use |
| Identical border-radius on all elements | Varied radii based on element size |
| Shadows on every card | Shadows only where depth serves function |
| Every element has a hover state | Hover only on interactive elements |
| Saturated accent colors at full strength | Muted, sophisticated accent usage |
| Generic blob/wave decorations | No decoration, or highly specific |
| Icons for everything | Text-only where words suffice |
| Multiple font weights in one line | Single weight, hierarchy via size |

### Structural Tells

| AI Pattern | Elite Alternative |
|------------|-------------------|
| Perfect symmetry everywhere | Intentional asymmetry with balance |
| Same spacing between all elements | Grouped spacing (related items closer) |
| Cards in perfect grids | Varied layouts, masonry, or asymmetric |
| Every section has same structure | Rhythm variation keeps interest |
| Components feel "templatey" | Each component designed for its content |

### Color Tells

| AI Pattern | Elite Alternative |
|------------|-------------------|
| Pure black (#000) | Near-black with undertone |
| Too many accent colors | One accent, used sparingly |
| Rainbow gradients | Monochromatic or analogous |
| Neon/electric colors at full saturation | Desaturated or tinted variants |
| Background colors for every section | Strategic color blocking |

### Motion Tells

| AI Pattern | Elite Alternative |
|------------|-------------------|
| Everything animates on scroll | Strategic reveals for key content |
| Same easing on all transitions | Varied easing by context |
| Hover effects too dramatic | Subtle, confident interactions |
| Animations that distract from content | Animations that enhance content |
| Parallax on every section | Parallax for hero only, or none |

---

## Polish Details

### The Details Checklist

**Before a design is "done," verify:**

**Typography:**
- [ ] Real curly quotes and apostrophes
- [ ] En-dashes for ranges, em-dashes for breaks
- [ ] Proper ellipsis character (not three periods)
- [ ] Letterspacing adjusted for ALL CAPS text
- [ ] Line lengths don't exceed 75 characters
- [ ] No orphans (single words on last line) in headlines

**Spacing:**
- [ ] All spacing values from the scale
- [ ] Related items grouped with smaller gaps
- [ ] Unrelated items separated with larger gaps
- [ ] Component internal padding is consistent
- [ ] Page margins feel generous

**Color:**
- [ ] No pure #000 or #FFF unless intentional
- [ ] Text passes contrast requirements
- [ ] Accent color used sparingly (≤10% of surface)
- [ ] All neutrals share same temperature
- [ ] Borders are low-contrast, not prominent

**Interactive States:**
- [ ] Hover states only on interactive elements
- [ ] Focus states visible (accessibility)
- [ ] Active/pressed states feel responsive
- [ ] Disabled states clearly different but readable
- [ ] Loading states don't shift layout

**Consistency:**
- [ ] All similar elements styled identically
- [ ] Icon sizes consistent within context
- [ ] Button sizes consistent (48px min touch target)
- [ ] Consistent alignment throughout

### Empty States

Empty states reveal design quality. They should:
- Feel designed, not like an error
- Maintain the visual language of the app
- Provide clear next action
- Not be apologetic or sad (avoid the sad-face pattern)

```
Good empty state: "No projects yet. Create your first project."
Bad empty state: "Oops! Nothing here :("
```

### Loading States

Loading should feel intentional:
- Skeleton screens maintain layout
- Spinners match design system
- Progress indicators are honest
- Content loads top-to-bottom, not randomly

---

## Responsive Craft

### Not Just Smaller

Mobile design isn't desktop shrunk down. It's a different context:
- Touch targets minimum 48×48px
- Thumb-friendly placement of key actions
- Consider one-handed use
- Simplified navigation patterns
- Larger text for outdoor visibility

### Breakpoints as Ranges

Don't design for specific breakpoints. Design for content needs:
- Layout breaks when content breaks
- Typography scales smoothly
- Spacing reduces proportionally (not arbitrarily)

### Mobile-Specific Decisions

| Desktop | Mobile |
|---------|--------|
| Hover reveals info | Info always visible |
| Multi-column layouts | Single column |
| Sidebar navigation | Bottom or hamburger nav |
| Large click targets | Larger touch targets |
| Dense information display | Prioritized information |

---

## Wild Mode: Intentional Rule-Breaking

Wild mode doesn't mean abandoning craft — it means **breaking rules with purpose**. The difference between amateur chaos and elite chaos is intentionality.

### What STILL Applies in Wild Mode

| Principle | Why It Still Matters |
|-----------|---------------------|
| **Typography craft** | Curly quotes, proper dashes — this is correctness, not style |
| **Intentionality** | Every choice should be deliberate, even chaotic ones |
| **Hierarchy** | Users still need to find things — chaos serves content, not obscures it |
| **Internal consistency** | Wild ≠ random. Pick a logic and commit |
| **The squint test** | Hierarchy should still read, even if unconventional |

### What CAN Be Deliberately Broken

| Normal Rule | Wild Exception | But With Purpose |
|-------------|----------------|------------------|
| No pure #000/#FFF | Harsh contrast allowed | For brutalist impact, CRT effect, high drama |
| Spacing from scale | Intentional irregularity | Tension, unease, broken grid energy |
| One accent color | Multiple clashing colors | Maximalist, fever dream, corruption aesthetic |
| No decorative elements | Textures, stains, noise | If it serves the concept (xerox, VHS, decay) |
| Subtle hover states | Dramatic interactions | Glitch, shake, aggressive feedback |
| Restrained gradients | Wild gradients | Thermal, iridescent, corrupted — not generic |

### The Wild Craft Test

Before using a "rule-breaking" element, ask:

1. **Is this intentional or lazy?** Breaking rules because they serve the concept ≠ breaking rules because you didn't think about it
2. **Does it serve the theme?** A glitch effect in a "corrupted file" theme = good. Random glitch on a "luxury" theme = bad.
3. **Is there internal logic?** Even chaos has patterns. What's the organizing principle?
4. **Would removing it weaken the concept?** If yes, keep it. If no, it's decoration.

### Wild ≠ Sloppy

| Sloppy Wild | Crafted Wild |
|-------------|--------------|
| Random colors everywhere | Intentional color clash that creates tension |
| Arbitrary spacing | Deliberately broken grid with rhythm |
| Every effect at once | Curated chaos — 2-3 strong effects, committed |
| Generic "glitch filter" | Hand-crafted corruption that fits the concept |
| Chaos that confuses | Chaos that delights then resolves |

### The Elite Wild Standard

Ask: "Would David Carson approve, or would he say it's trying too hard?"

Elite wild design:
- Has a **concept** driving the chaos
- Shows **confidence** in its choices
- Creates **tension that resolves**
- Is **memorable**, not just "weird"
- Could be **defended** in a design crit

Generic wild design:
- Throws effects at the wall
- Hedges with "a little bit of everything"
- Confuses without payoff
- Is forgettable chaos
- Can't explain why anything is there

---

## The Final Test

Before submitting any design, answer:

1. **Can I remove anything?** If yes, do it.
2. **Is the hierarchy obvious?** Squint and check.
3. **Is every value intentional?** No arbitrary numbers.
4. **Does it avoid AI tells?** Check the anti-AI list.
5. **Would a top designer approve?** Imagine showing this to your design hero.

**The ultimate question:** Does this look like something from a studio that charges $500/hour, or something generated in 30 seconds?

---

## Reference: Elite Design Sources

Study these for calibration:

**Web:**
- Stripe.com (systematic, confident, restrained)
- Linear.app (polish in every detail)
- Notion.so (warmth within minimalism)
- Vercel.com (bold simplicity)
- Apple.com (luxury restraint)

**Studios:**
- Pentagram (systematic identity)
- Collins (bold conceptual)
- Wolff Olins (strategic restraint)
- ManvsMachine (motion craft)
- Buck (animation polish)

**Publications:**
- The Gentlewoman (editorial sophistication)
- Apartamento (imperfect perfection)
- Monocle (systematic editorial)
- Bloomberg Businessweek (bold editorial)

**The pattern:** All of these exhibit restraint, system, and confidence. None of them over-design.
