# Discovery Phase

Everything needed to analyze an app and build its profile. **Read this entire file before running discovery.**

---

## DISCOVERY CHECKLIST

After discovery, verify:

- [ ] **Pages identified** — list of views/routes with purpose
- [ ] **Layout detected** — shared layout/shell components
- [ ] **Styling system** — Tailwind, CSS modules, styled-components, etc.
- [ ] **Interactive patterns** — modals, dropdowns, toasts, auth states
- [ ] **Component library** — reusable UI components
- [ ] **Output paths** — where styles/templates live
- [ ] **Build commands** — how to compile/preview changes
- [ ] **Profile saved** — `tmp/makeover/profile.md` generated

---

## DETECTION STRATEGIES

### 1. Page/Route Detection (Universal Heuristics)

Scan for common patterns across frameworks:

```bash
# Directory-based routing
ls -la pages/ app/ views/ src/pages/ src/views/ src/routes/

# Route configuration files
find . -name "routes.*" -o -name "router.*" -o -name "*routing*"

# Framework-specific
grep -r "createBrowserRouter\|Route\|path:" --include="*.{js,jsx,ts,tsx}"
grep -r "get\|post\|match" --include="routes.rb"
```

**Pattern priority:**
1. `pages/` or `app/` directory (Next.js, Nuxt, SvelteKit)
2. `views/` or `templates/` directory (Rails, Django, Express)
3. Route config files (React Router, Vue Router)
4. Controller files (MVC frameworks)

### 2. Layout Detection

Find shared layout/shell components:

```bash
# Common layout locations
find . -name "*layout*" -o -name "*shell*" -o -name "*wrapper*"
find . -name "_app.*" -o -name "root.*" -o -name "App.*"

# Look for common layout patterns
grep -r "children\|outlet\|yield\|slot" --include="*.{jsx,tsx,vue,svelte,erb,html}"
```

**Identify:**
- Main layout wrapper (header/footer)
- Auth layouts (logged in vs logged out)
- Admin/dashboard layouts
- Public/marketing layouts

### 3. Styling System Detection

Detect existing design system:

```bash
# Tailwind
[ -f tailwind.config.* ] && echo "Tailwind detected"
grep -l "tailwindcss" package.json

# CSS Modules
find . -name "*.module.css" -o -name "*.module.scss"

# Styled-components / Emotion
grep -l "styled-components\|@emotion" package.json

# CSS-in-JS
grep -r "styled\.\|css\`" --include="*.{js,jsx,ts,tsx}" | head -5

# Design tokens
find . -name "*tokens*" -o -name "*variables*" -o -name "*theme*" | grep -E "\.(css|scss|json)$"

# Component libraries
grep -E "chakra|material-ui|antd|radix|shadcn" package.json
```

**Extract:**
- Color tokens/variables
- Spacing scale
- Typography scale
- Breakpoints
- Shadow/elevation system

### 4. Interactive Pattern Detection

Find JavaScript-driven UI patterns:

```bash
# Modal patterns
grep -r "modal\|dialog\|overlay" --include="*.{js,jsx,ts,tsx,vue,svelte}"

# Dropdown/menu patterns
grep -r "dropdown\|menu\|popover" --include="*.{js,jsx,ts,tsx,vue,svelte}"

# Toast/notification patterns
grep -r "toast\|notification\|alert\|snackbar" --include="*.{js,jsx,ts,tsx,vue,svelte}"

# Auth state patterns
grep -r "isAuthenticated\|isLoggedIn\|user\s*=\s*null\|currentUser" --include="*.{js,jsx,ts,tsx,vue,svelte}"

# Loading states
grep -r "isLoading\|loading\|skeleton\|spinner" --include="*.{js,jsx,ts,tsx,vue,svelte}"
```

**Document:**
- How modals open/close (state, data attributes, classes)
- Auth-dependent UI (show/hide patterns)
- Loading/skeleton states
- Form validation display
- Error message patterns

### 5. Component Library Detection

Find reusable UI components:

```bash
# Common component directories
ls -la components/ src/components/ ui/ src/ui/

# Component files
find . -path "*/components/*" -name "*.{jsx,tsx,vue,svelte}" | head -20

# Shared partials (server-rendered)
find . -path "*/partials/*" -o -path "*/_*" | grep -E "\.(erb|ejs|hbs|pug)$"
```

**Catalog:**
- Button variants
- Card components
- Form inputs
- Navigation components
- Data display (tables, lists)

### 6. Build System Detection

Find how to compile and preview:

```bash
# Package.json scripts
cat package.json | grep -A 50 '"scripts"'

# Common build tools
find . -name "webpack.config.*" -o -name "vite.config.*" -o -name "rollup.config.*"

# CSS compilation
find . -name "postcss.config.*" -o -name ".postcssrc*"
```

**Document:**
- Dev server command
- Build command
- CSS compilation command
- Asset output directory

---

## APP PROFILE TEMPLATE

Generate this at `tmp/makeover/profile.md`:

```markdown
# App Profile: [App Name]

Generated: [timestamp]

## Tech Stack

- **Framework**: [React, Vue, Rails, etc.]
- **Styling**: [Tailwind, CSS Modules, styled-components]
- **Build tool**: [Vite, Webpack, esbuild]
- **Component library**: [none, shadcn, Radix, custom]

## Pages Detected

| Page | Route/Path | Purpose | Layout |
|------|------------|---------|--------|
| Home | `/` or `index` | Landing/dashboard | main |
| [page] | [route] | [purpose] | [layout] |

## Layouts

| Layout | Location | Usage |
|--------|----------|-------|
| Main | [path] | Default layout |
| Auth | [path] | Logged-in users |
| Public | [path] | Marketing pages |

## Styling System

### Colors
```css
--primary: [hex];
--secondary: [hex];
--background: [hex];
--text: [hex];
--accent: [hex];
```

### Spacing Scale
[e.g., 4px base, 8px, 16px, 24px, 32px, 48px]

### Typography
- **Headings**: [font family, weights]
- **Body**: [font family, weights]
- **Mono**: [font family]

### Breakpoints
- sm: [value]
- md: [value]
- lg: [value]
- xl: [value]

## Interactive Patterns

### Modals
- **Trigger**: [how opened - button click, route change]
- **State management**: [useState, data-state attribute, class toggle]
- **Close behavior**: [ESC, click outside, X button]
- **Location**: [component path]

### Dropdowns
- **Pattern**: [headless UI, custom, native]
- **Location**: [component path]

### Auth States
- **Check**: [how auth determined]
- **Show when logged in**: [selectors/components]
- **Show when logged out**: [selectors/components]

### Loading States
- **Pattern**: [skeleton, spinner, shimmer]
- **Location**: [component path]

### Toast/Notifications
- **Library**: [react-hot-toast, sonner, custom]
- **Location**: [component path]

## Component Library

| Component | Location | Variants |
|-----------|----------|----------|
| Button | [path] | primary, secondary, ghost |
| Card | [path] | default, elevated |
| Input | [path] | text, select, checkbox |
| [etc.] | | |

## Build Commands

```bash
# Development
[dev command]

# Build
[build command]

# CSS only
[css command if separate]
```

## Output Paths

| Type | Path | Notes |
|------|------|-------|
| Styles | [path] | Main CSS location |
| Templates | [path] | If server-rendered |
| Components | [path] | UI components |
| Assets | [path] | Static files |

## Notes

[Any unusual patterns, gotchas, or important context]
```

---

## DISCOVERY AGENT PROMPT

Use this when spawning discovery agents:

```
You are analyzing an application to build a profile for redesign.

## Your Task

1. Scan the codebase systematically
2. Detect pages, layouts, styling, and patterns
3. Generate a comprehensive profile

## Detection Order

1. **Package.json / dependencies** — understand the stack
2. **Directory structure** — find pages, components, styles
3. **Route configuration** — map all pages
4. **Layout files** — identify shared structure
5. **Style files** — detect design system
6. **Interactive components** — find modals, dropdowns, auth
7. **Build configuration** — understand compilation

## Tools to Use

- Glob: find files by pattern
- Grep: search file contents
- Read: examine specific files
- Bash(ls): list directories

## DO NOT

- Modify any files
- Run build commands
- Make assumptions without evidence
- Skip any detection step

## Output

1. Create directory: `mkdir -p tmp/makeover`
2. Write profile to: `tmp/makeover/profile.md`
3. Return summary of findings:
   - Number of pages detected
   - Styling system identified
   - Interactive patterns found
   - Any unusual patterns or concerns
```

---

## HANDLING EDGE CASES

### Monorepo Detection

```bash
# Check for workspaces
grep -l "workspaces" package.json
find . -name "package.json" -not -path "*/node_modules/*" | head -10
```

If monorepo detected, ask user which package to analyze.

### Server-Rendered vs SPA

```bash
# Server-rendered indicators
find . -name "*.erb" -o -name "*.ejs" -o -name "*.hbs" -o -name "*.blade.php"

# SPA indicators
grep -l "createRoot\|ReactDOM.render\|createApp" --include="*.{js,jsx,ts,tsx}"
```

Profile should note rendering strategy as it affects implementation.

### Hybrid Apps

Some apps mix patterns. Document both:
- Which pages are server-rendered
- Which are client-rendered
- How they share styles

### No Clear Design System

If no tokens/variables found:
- Extract colors from existing CSS
- Note inline style patterns
- Flag as "ad-hoc styling" in profile
- Recommend establishing tokens during implementation

---

## PROFILE VALIDATION

Before completing discovery, verify:

1. **Can navigate to each detected page** — paths are real
2. **Layout files contain expected structure** — header/footer/slot
3. **Style system tokens are accurate** — colors match what you see
4. **Interactive patterns are documented** — can describe open/close behavior
5. **Build commands work** — validated in package.json

If gaps exist, note them in the profile's "Notes" section.
