# Implementation Phase

Everything needed to implement approved themes. **Read this entire file before spawning implementation agents.**

---

## IMPLEMENTATION CHECKLIST

### Prerequisites
- [ ] **Discovery complete** — `tmp/makeover/profile.md` exists
- [ ] **Proposal approved** — `tmp/makeover/themes/{name}.html` exists
- [ ] **Profile reviewed** — know output paths, patterns, build commands

### Implementation
- [ ] **Strategy chosen** — drop-in or incremental
- [ ] **Styling output** — matches detected system (Tailwind, CSS vars, etc.)
- [ ] **Interactive patterns** — preserved from profile
- [ ] **All pages covered** — every page from profile
- [ ] **Components styled** — all detected components

### Verification
- [ ] **Build succeeds** — all build commands pass
- [ ] **Pages render** — no broken layouts
- [ ] **Interactions work** — modals, dropdowns, forms
- [ ] **Mobile works** — responsive breakpoints
- [ ] **Matches proposal** — colors, layout, components match preview

---

## IMPLEMENTATION STRATEGY

### Determine Strategy

Read from profile:
- **App complexity** (number of pages, components)
- **Styling system** (how intertwined with functionality)
- **Risk tolerance** (user preference if stated)

| Complexity | Risk | Strategy |
|------------|------|----------|
| Simple (< 5 pages, clear separation) | Low | Drop-in replacement |
| Medium (5-15 pages, some coupling) | Medium | Incremental with theme toggle |
| Complex (> 15 pages, deep coupling) | High | Incremental with gradual migration |

### Drop-in Replacement

Replace style files wholesale:

1. **Backup existing** (git handles this)
2. **Replace style files** at detected paths
3. **Update any templates** if layout changes
4. **Run build**
5. **Test all pages**

Best for:
- Small apps
- Clean separation of styles
- Low-risk projects

### Incremental Migration

Theme coexistence with toggle:

1. **Add new theme alongside old**
2. **Create theme toggle mechanism**
3. **Migrate page by page**
4. **Remove old theme when complete**

Pattern:
```html
<body class="theme-{old}" data-theme="{old}">
<!-- Toggle switches class and data-theme -->
<body class="theme-{new}" data-theme="{new}">
```

Best for:
- Large apps
- Tightly coupled styles
- Production apps needing safe rollback

---

## OUTPUT FORMAT BY STYLING SYSTEM

### Tailwind CSS

If profile shows Tailwind, output Tailwind-native:

```css
/* app/styles/theme-{name}.css */
@import "tailwindcss";

@theme {
  --color-bg: #0f0f0f;
  --color-surface: #1a1a1a;
  --color-primary: #ffffff;
  --color-accent: #ff6b35;
  /* ... */
}

/* Custom components */
@layer components {
  .btn-primary {
    @apply bg-accent text-white px-4 py-2 rounded;
  }
}
```

And update `tailwind.config.*` if needed:
```js
theme: {
  extend: {
    colors: {
      // Reference CSS variables or add colors
    }
  }
}
```

### CSS Modules

If profile shows CSS modules:

```css
/* ComponentName.module.css */
.container {
  background: var(--color-bg);
  padding: var(--space-4);
}

.title {
  color: var(--color-primary);
  font-size: var(--text-xl);
}
```

With global variables:
```css
/* globals.css or variables.css */
:root {
  --color-bg: #0f0f0f;
  --color-surface: #1a1a1a;
  /* ... */
}
```

### Styled-Components / Emotion

If profile shows CSS-in-JS:

```jsx
// theme.js
export const theme = {
  colors: {
    bg: '#0f0f0f',
    surface: '#1a1a1a',
    primary: '#ffffff',
    accent: '#ff6b35',
  },
  space: {
    1: '4px',
    2: '8px',
    // ...
  }
};

// Component usage
const Button = styled.button`
  background: ${({ theme }) => theme.colors.accent};
  color: white;
  padding: ${({ theme }) => `${theme.space[2]} ${theme.space[4]}`};
`;
```

### Vanilla CSS

If no system detected, use CSS custom properties:

```css
/* styles/theme-{name}.css */
:root {
  /* Colors */
  --color-bg: #0f0f0f;
  --color-surface: #1a1a1a;
  --color-primary: #ffffff;
  --color-secondary: #a0a0a0;
  --color-accent: #ff6b35;
  --color-border: #333333;

  /* Typography */
  --font-sans: 'Inter', system-ui, sans-serif;
  --font-mono: 'JetBrains Mono', monospace;
  --text-xs: 0.75rem;
  --text-sm: 0.875rem;
  --text-base: 1rem;
  --text-lg: 1.125rem;
  --text-xl: 1.25rem;
  --text-2xl: 1.5rem;

  /* Spacing */
  --space-1: 0.25rem;
  --space-2: 0.5rem;
  --space-3: 0.75rem;
  --space-4: 1rem;
  --space-6: 1.5rem;
  --space-8: 2rem;

  /* Shadows */
  --shadow-sm: 0 1px 2px rgba(0,0,0,0.1);
  --shadow-md: 0 4px 6px rgba(0,0,0,0.1);
  --shadow-lg: 0 10px 15px rgba(0,0,0,0.1);

  /* Border radius */
  --radius-sm: 0.25rem;
  --radius-md: 0.5rem;
  --radius-lg: 1rem;
  --radius-full: 9999px;
}

/* Dark mode variant */
[data-theme="dark"] {
  --color-bg: #0f0f0f;
  /* ... */
}

/* Component classes */
.btn {
  display: inline-flex;
  align-items: center;
  padding: var(--space-2) var(--space-4);
  border-radius: var(--radius-md);
  font-weight: 500;
  transition: all 0.2s;
}

.btn-primary {
  background: var(--color-accent);
  color: white;
}
```

---

## PRESERVING INTERACTIVE PATTERNS

### From Profile

Read the "Interactive Patterns" section of profile.md carefully.

### Common Patterns

#### Modal with data-state

If profile says modals use `data-state`:

```css
/* Modal closed */
[data-state="closed"] {
  display: none;
}

/* Modal open */
[data-state="open"] {
  display: flex;
  position: fixed;
  inset: 0;
  z-index: 10000;
  align-items: center;
  justify-content: center;
}
```

#### Modal with class toggle

If profile says modals use class:

```css
.modal {
  display: none;
  /* ... */
}

.modal.is-open,
.modal.show {
  display: flex;
}
```

#### Auth-dependent UI

If profile identifies auth patterns:

```css
/* Default: logged out */
.show-when-authenticated {
  display: none;
}

.hide-when-authenticated {
  display: block;
}

/* When authenticated (class on body or wrapper) */
.authenticated .show-when-authenticated {
  display: block;
}

.authenticated .hide-when-authenticated {
  display: none;
}
```

#### Loading States

```css
.skeleton {
  background: linear-gradient(90deg, var(--color-surface) 25%, var(--color-border) 50%, var(--color-surface) 75%);
  background-size: 200% 100%;
  animation: skeleton-loading 1.5s infinite;
}

@keyframes skeleton-loading {
  0% { background-position: 200% 0; }
  100% { background-position: -200% 0; }
}
```

---

## COMMON FAILURES

| Symptom | Cause | Fix |
|---------|-------|-----|
| Styles not loading | Wrong output path | Check profile for correct path |
| Modals broken | Pattern mismatch | Use exact pattern from profile |
| Build fails | Syntax error or missing import | Check build command output |
| Layout broken | CSS specificity issue | Increase specificity or use !important |
| Mobile broken | Missing media queries | Add responsive styles |
| Colors wrong | Variables not defined | Ensure all vars in :root |
| Fonts missing | CDN not loaded | Add Google Fonts link |
| Doesn't match proposal | CSS rewritten | Copy directly from proposal |

### The #1 Implementation Problem

**Implementation doesn't match proposal.** To fix:

1. Read the proposal HTML section by section
2. Copy CSS rules directly from proposal's `<style>` tags
3. Use **exact same class names**
4. Compare each page visually against proposal

---

## VERIFICATION CHECKLIST

### Build
- [ ] All build commands pass
- [ ] No console errors
- [ ] No missing dependencies

### Visual Match
- [ ] Colors match proposal palette
- [ ] Typography matches proposal
- [ ] Layout matches DNA
- [ ] Spacing feels the same

### Functionality
- [ ] Navigation works
- [ ] Modals open/close
- [ ] Forms submit
- [ ] Auth states toggle correctly
- [ ] Loading states appear

### Responsive
- [ ] Desktop (>1024px) works
- [ ] Tablet (768-1024px) works
- [ ] Mobile (<768px) works
- [ ] No horizontal scroll on mobile
- [ ] Touch targets adequate (48px)

### Accessibility
- [ ] Focus visible on all interactive elements
- [ ] Color contrast passes
- [ ] Text remains readable

---

## IMPLEMENTATION AGENT PROMPT

```
You are implementing a theme from an approved preview.

## CRITICAL: Read First

1. Read tmp/makeover/profile.md — understand app structure
2. Read tmp/makeover/themes/{name}.html — the approved design
3. Read IMPLEMENT.md — technical patterns

## App Context

[INSERT PROFILE SUMMARY]

Output paths: [from profile]
Styling system: [from profile]
Build commands: [from profile]
Interactive patterns: [from profile]

## Use frontend-design Plugin

Invoke: Skill tool: skill="frontend-design", args="Implement {name} theme"

## Match the Preview EXACTLY

The preview shows the approved design. Your implementation must match:
- Same colors (extract from palette section)
- Same typography
- Same layout structure
- Same component styling

## How to Match the Proposal

### 1. Copy CSS Directly

The proposal HTML contains ALL CSS inline in `<style>` tags:
- Extract CSS rules and adapt to styling system
- Keep class names consistent
- DO NOT rewrite or "improve" the CSS

### 2. Adapt to Styling System

If Tailwind:
- Convert to @theme variables and utility classes
- Use @layer components for custom classes

If CSS Modules:
- Create module files per component
- Use CSS variables for tokens

If vanilla:
- Create comprehensive variables
- Organize by component

### 3. Preserve Interactions

Use EXACT patterns from profile:
- Modal open/close mechanism
- Auth state display logic
- Loading state patterns
- Form validation display

## Output Files

Create files at paths specified in profile:
- Main style file(s)
- Component styles (if applicable)
- Any template updates (if layout changed)

## Verification

After creating files:
1. Run build commands from profile
2. Test each page
3. Test all interactions
4. Check mobile responsiveness
5. Confirm visual match to proposal

## Return

- Files created (list paths)
- Build status
- Verification results
- Any issues encountered
```

---

## ROLLBACK PLAN

If implementation fails:

### Git-based (Preferred)

```bash
# See what changed
git status
git diff

# Rollback all changes
git checkout .

# Or rollback specific files
git checkout -- path/to/file
```

### Manual (If no git)

1. Backup is at `tmp/makeover/backup/` (if created)
2. Copy original files back
3. Run build to restore

### Document Failures

If implementation fails, document:
- What broke
- Why it broke
- What the fix should be

Add to profile.md notes for future attempts.
