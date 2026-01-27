# Design System Reference

Spacing, typography, and color system for normal mode proposals.

---

## Spacing Scale

**Use only these values. No arbitrary spacing.**

| Value | Use |
|-------|-----|
| 4px | Micro (icon padding, tight gaps) |
| 8px | Small (related element gaps) |
| 12px | Medium-small (form spacing) |
| 16px | Medium (standard padding) |
| 24px | Large (section gaps) |
| 32px | X-large (major divisions) |
| 48px | 2X-large (page sections) |
| 64px | 3X-large (hero/page divisions) |

**Principles:**
- Start with too much space, remove until right
- Related elements closer than unrelated
- Fixed widths often beat fluid grids

---

## Typography Scale

| Size | Use |
|------|-----|
| 12px | Captions, metadata |
| 14px | Secondary text, labels |
| 16px | Body text |
| 18px | Emphasized body |
| 20px | Small headings |
| 24px | Section headings |
| 30px | Page headings |
| 36px | Large headings |
| 48px | Display |
| 60px+ | Hero |

### Line Height

| Text Size | Line Height |
|-----------|-------------|
| Small (12-14px) | 1.6-1.7 |
| Body (16-18px) | 1.5-1.6 |
| Subheads (20-24px) | 1.3-1.4 |
| Headlines (32px+) | 1.1-1.2 |

### Letter-Spacing

| Context | Adjustment |
|---------|------------|
| Headlines (24px+) | Tighten -0.01em |
| ALL CAPS | Loosen +0.05em to +0.1em |

### Micro-Typography

- Use `" "` not `" "` (curly quotes)
- Use `–` for ranges, `—` for breaks
- Use `…` not `...`
- Line length: 45-75 characters (`max-width: 65ch`)

---

## Color System

### Use HSL

Always define colors in HSL. It makes relationships obvious:

```css
--primary-500: hsl(220, 65%, 50%);  /* Base */
--primary-400: hsl(220, 65%, 60%);  /* Lighter */
--primary-600: hsl(220, 65%, 40%);  /* Darker */
```

### Gray Temperature

Never use pure gray. Add subtle saturation:
- **Warm grays:** `hsl(30, 5%, X%)` — yellow/orange tint
- **Cool grays:** `hsl(220, 5%, X%)` — blue tint

Match gray temperature to your palette's dominant hue.

### Building a Palette

1. **Pick base (500)** — works as button background, `hsl(H, S, 50%)`
2. **Find edges**: darkest (900) `hsl(H, S, 15%)`, lightest (100) `hsl(H, S, 95%)`
3. **Fill gaps**: 700, 300, then 800, 600, 400, 200

**You need:** 8-10 gray shades, 5-10 primary shades, 5-10 accent shades.

### Critical Rules

- **No pure black/white:** Use `hsl(0, 0%, 10%)` and `hsl(0, 0%, 98%)`
- **60-30-10 rule:** 60% dominant, 30% secondary, 10% accent
- **Accent ≤10%:** Accent colors should pop, not dominate

---

## Shadow System

**Light comes from above.** Define 5 elevation levels:

```css
--shadow-xs: 0 1px 2px rgba(0,0,0,0.05);
--shadow-sm: 0 1px 3px rgba(0,0,0,0.1), 0 1px 2px rgba(0,0,0,0.06);
--shadow-md: 0 4px 6px rgba(0,0,0,0.1), 0 2px 4px rgba(0,0,0,0.06);
--shadow-lg: 0 10px 15px rgba(0,0,0,0.1), 0 4px 6px rgba(0,0,0,0.05);
--shadow-xl: 0 20px 25px rgba(0,0,0,0.1), 0 10px 10px rgba(0,0,0,0.04);
```

| Element | Shadow Level |
|---------|--------------|
| Buttons | xs/sm |
| Cards | sm/md |
| Dropdowns | md/lg |
| Modals | lg/xl |

### Theme-Dependent Shadows

Shadows behave differently in dark mode:

| Light Theme | Dark Theme Alternative |
|-------------|----------------------|
| Drop shadows | Reduced opacity or glow effects |
| Black rgba shadows | Darker surface + subtle light edge |
| High contrast shadows | Softer, ambient occlusion style |

**Dark mode strategy:** Instead of shadows, use layered surfaces with progressively lighter backgrounds. Each elevation step increases lightness slightly while maintaining the same hue and saturation.

---

## Anti-AI Checklist

Avoid these patterns that mark AI-generated design:

| AI Pattern | Better Alternative |
|------------|-------------------|
| Gradient backgrounds everywhere | Flat colors, strategic gradients |
| Same border-radius on everything | Varied radii by element size |
| Shadow on every card | Shadows only where elevation matters |
| Perfect symmetry | Intentional asymmetry with balance |
| Same spacing between all elements | Grouped spacing (related items closer) |
| Hover states that only change opacity | Transform, color shift, underline grow |
| Inter, Roboto, Open Sans fonts | Distinctive typography choices |
| Blue as primary accent | Unexpected color choices |

---

## Hierarchy Techniques

**Size isn't everything.** Use multiple tools:

| Tool | Effect |
|------|--------|
| Font weight | 400-500 normal, 600-700 emphasis |
| Color | Dark = primary, gray = secondary, light = tertiary |
| Spacing | More breathing room = more prominence |

**Key techniques:**
- Emphasize by de-emphasizing competitors
- Labels are a last resort — data speaks for itself
