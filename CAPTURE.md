# Capture & Orchestration Workflow

Playwright-based app discovery, content capture, and proposal orchestration. **Orchestrator reads this, not proposal agents.**

---

## Phase 1: Reference Research (Optional)

### When User Provides URLs

```
User: "I want something like stripe.com and linear.app"
```

1. Navigate to each URL with Playwright
2. Take snapshots
3. Extract patterns:

| Element | Extract |
|---------|---------|
| Colors | Dominant hues, accent colors (sample from hero, buttons, text) |
| Typography | Font families, weights, sizes (inspect headings + body) |
| Spacing | Section padding, component gaps (estimate px values) |
| Layout | Grid structure, header type, card patterns |
| Motion | Hover effects, scroll behavior (estimate N-level) |

4. Write to `tmp/makeover/references/`:

```
tmp/makeover/references/
├── stripe.com/
│   ├── snapshot.html
│   └── analysis.json
├── linear.app/
│   └── ...
└── summary.json
```

**summary.json format:**
```json
{
  "sources": ["stripe.com", "linear.app"],
  "extracted": {
    "colors": ["#635BFF", "#0A2540", "#F6F9FC"],
    "typography": {
      "headlines": "sans-serif 600-700",
      "body": "sans-serif 400"
    },
    "spacing": "generous (32-48px sections)",
    "motion_level": "N2-N3"
  },
  "cached_at": "2024-01-15T10:30:00Z"
}
```

### When User Provides Keywords

Map to canonical examples, then browse:

| Keyword | Browse |
|---------|--------|
| minimal, clean | stripe.com, linear.app |
| editorial | nytimes.com, medium.com |
| luxury | aesop.com, apple.com |
| dashboard | vercel.com/dashboard, linear.app |
| brutalist | cargo.site, hfrcc.com |

### When User Provides Images

Use Read tool to analyze reference images:

| Element | Look For |
|---------|----------|
| Colors | Dominant hue, accents, contrast, saturation |
| Typography | Serif/sans/display, weight, case, spacing |
| Layout | Centered/asymmetric, grid/organic, dense/spacious |
| Texture | Grain/smooth, matte/glossy, layered/flat |
| Mood | Era, emotion, energy level |

### When NOT to Browse

- Do NOT screenshot generated proposal HTML files
- Do NOT browse without user request or reference URLs
- Skip if references cached <24h ago

---

## Phase 2: App Discovery & Capture

### Step 1: Get App URL

```
"Where is your app running?"
Default: http://localhost:3000
```

### Step 2: Discover Pages

Navigate and explore:
- Click navigation links
- Check common routes: /, /dashboard, /settings, /profile, /[id]
- Look at DOM for route information

For each distinct page, note:
- URL/route
- Page purpose
- Key content elements

### Step 3: Capture to Files

Create capture directory:
```
tmp/makeover/capture/
├── manifest.json
├── home.snapshot
├── dashboard.snapshot
├── settings.snapshot
└── images.json
```

**manifest.json:**
```json
{
  "app_url": "http://localhost:3000",
  "captured_at": "2024-01-15T10:30:00Z",
  "styling_system": "Tailwind",
  "pages": [
    { "slug": "home", "url": "/", "purpose": "Landing page" },
    { "slug": "dashboard", "url": "/dashboard", "purpose": "Main dashboard" },
    { "slug": "settings", "url": "/settings", "purpose": "User settings" }
  ]
}
```

**{page}.snapshot** (one per page):
- Accessibility tree snapshot from Playwright
- Includes: headings, buttons, forms, images, text content
- Actual content, not structure description

**images.json:**
```json
{
  "images": [
    { "src": "http://localhost:3000/logo.png", "alt": "Company logo", "page": "home" },
    { "src": "http://localhost:3000/hero.jpg", "alt": "Hero image", "page": "home" }
  ]
}
```

### Step 4: Detect Styling System

Quick detection from DOM/files:

| System | Detection |
|--------|-----------|
| Tailwind | Classes like `bg-blue-500`, `px-4`, `flex` |
| CSS Modules | Classes like `styles_button__abc123` |
| Styled-components | `sc-` prefixed classes |
| Vanilla CSS | Standard class names, inline styles |

Record in manifest.json.

### Step 5: Confirm Pages with User

```
"I found these pages in your app:
- / (Home/Landing)
- /dashboard (Main dashboard)
- /settings (User settings)

Which pages should appear in the theme proposals?"

Options: [All of these (Recommended)] [Select specific pages]
```

Update manifest.json with `"included": true/false` per page.

---

## Phase 3: Variance Planning

Before spawning agents, pre-compute constraints to ensure diverse proposals.

### Normal Mode Variance

Ensure ≥3 DNA position differences between proposals:

```json
{
  "proposals": [
    {
      "name": "theme-a",
      "mode": "normal",
      "constraints": {
        "H": [4, 5, 8],
        "L": [1, 2, 3],
        "colorTemp": "warm",
        "motion_range": "N1-N3"
      }
    },
    {
      "name": "theme-b",
      "mode": "normal",
      "constraints": {
        "H": [1, 2, 11],
        "L": [5, 6, 7],
        "colorTemp": "cool",
        "motion_range": "N4-N6"
      }
    }
  ]
}
```

### Wild Mode Variance

Assign different structural mutations:

```json
{
  "name": "wild-a",
  "mode": "wild",
  "constraints": {
    "structural_mutation": "page_collapse",
    "nav_mutation": "abolished"
  }
},
{
  "name": "wild-b",
  "mode": "wild",
  "constraints": {
    "structural_mutation": "page_fragment",
    "nav_mutation": "as_content"
  }
}
```

### Constraint Distribution Rules

| Axis | Rule |
|------|------|
| Header (H) | No duplicates across normal proposals |
| Layout (L) | No duplicates across normal proposals |
| Color Temperature | At least 2 different (warm/cool/neutral) |
| Motion | Spread across N1-3, N4-6, N7-9 |
| Structural (wild) | Each uses different primary mutation |

Write constraints to: `tmp/makeover/constraints.json`

---

## Phase 4: Spawn Proposal Agents

### Agent Prompt Construction

For each proposal:

```
Task(
  subagent_type="general-purpose",
  description="Propose {name} theme",
  prompt="""
You are creating a theme proposal. This is a STRUCTURED PROCESS, not freeform creative work.

## STEP 1: Read Required Files (MANDATORY)

Read these files IN ORDER before doing anything else:
1. PROPOSE_{mode}.md — contains checklist you MUST complete
2. tmp/makeover/capture/manifest.json — pages, styling system
3. tmp/makeover/capture/*.snapshot — real DOM content for each page
4. tmp/makeover/constraints.json — your assigned variance constraints

## STEP 2: Complete Pre-Submit Verification (MANDATORY)

BEFORE generating any code, you must STATE ALOUD your verification:
- For normal mode: Content, DNA, Palette, References, Anti-AI, Constraints checks
- For wild mode: Structural, Decoration Test, Content, Palette, References, Banned checks

The PROPOSE file has the exact verification statements. Copy them and fill in your answers.

## STEP 3: Invoke frontend-design Plugin

Call the frontend-design plugin BEFORE writing HTML.

## STEP 4: Generate HTML

Output: tmp/makeover/themes/{name}.html

Your assignment:
- Theme name: {name}
- Mode: {mode}
- Constraints: Read from tmp/makeover/constraints.json

## CRITICAL: Do Not Skip Steps

If you generate HTML without completing the verification statements, you have failed.
The verification proves you read the captures and constraints.
"""
)
```

### Spawn in Parallel

Launch all proposal agents simultaneously:

```python
# Conceptual - spawn all at once
agents = [
  Task("Propose elegant-mono theme", normal_prompt),
  Task("Propose warm-editorial theme", normal_prompt),
  Task("Propose collapsed-stream wild theme", wild_prompt),
]
```

### What Agents Read

| File | Purpose | Required |
|------|---------|----------|
| PROPOSE_NORMAL.md or PROPOSE_WILD.md | Checklist, requirements | Yes |
| tmp/makeover/capture/manifest.json | Pages, styling system | Yes |
| tmp/makeover/capture/{page}.snapshot | Real DOM content | Yes |
| tmp/makeover/constraints.json | Assigned variance constraints | Yes |
| DESIGN_SYSTEM.md | Detailed DNA/scale definitions | If needed |
| MOTION.md | Animation implementation | If N3+ |

---

## Phase 5: Generate Preview Index

After all proposals complete, generate `tmp/makeover/themes/index.html`:

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
    h1 { font-size: 2rem; font-weight: 600; margin: 0 0 0.5rem; }
    .subtitle { color: #666; margin: 0 0 2.5rem; }
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
      pointer-events: none;
    }
    .card-body { padding: 1.25rem; }
    .card-title { font-size: 1.125rem; font-weight: 600; margin: 0 0 0.5rem; }
    .card-meta { font-family: ui-monospace, monospace; font-size: 0.75rem; color: #888; margin: 0 0 0.75rem; }
    .card-desc { font-size: 0.875rem; color: #555; margin: 0; line-height: 1.5; }
    .badge {
      display: inline-block;
      padding: 0.125rem 0.5rem;
      border-radius: 4px;
      font-size: 0.625rem;
      font-weight: 600;
      text-transform: uppercase;
      letter-spacing: 0.05em;
      margin-left: 0.5rem;
    }
    .badge-normal { background: #e8e8e8; color: #666; }
    .badge-wild { background: #ff6b6b; color: white; }
  </style>
</head>
<body>
  <h1>Makeover Proposals</h1>
  <p class="subtitle">Generated: [timestamp] · Click any card to view full preview</p>
  <div class="grid">
    <!-- Repeat for each proposal -->
    <a href="[name].html" class="card">
      <div class="card-preview">
        <iframe src="[name].html" title="[Theme Name] preview" loading="lazy"></iframe>
      </div>
      <div class="card-body">
        <h2 class="card-title">
          [Theme Name]
          <span class="badge badge-[mode]">[mode]</span>
        </h2>
        <p class="card-meta">DNA: [code] · Refs: [references]</p>
        <p class="card-desc">[Brief description]</p>
      </div>
    </a>
  </div>
</body>
</html>
```

---

## Final Output

```
tmp/makeover/
├── capture/
│   ├── manifest.json
│   ├── {page}.snapshot (per page)
│   └── images.json
├── references/ (if browsed)
│   ├── {domain}/
│   └── summary.json
├── constraints.json
└── themes/
    ├── index.html
    └── {name}.html (per proposal)
```

Report to user: **"Open tmp/makeover/themes/index.html to compare proposals"**
