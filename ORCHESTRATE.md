# Orchestrator Workflow

Full workflow for the orchestrator: reference research, app capture, variance planning, agent spawning, and index generation.

---

## Phase 1: Reference Research (Optional)

### When User Provides URLs

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

4. Write extracted patterns to `tmp/makeover/references/summary.json`

### When User Provides Keywords Only

Do NOT browse external sites. Use keywords to inform style direction during variance planning (Phase 3).

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
- Follow any visible routes in the UI
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
├── {page}.snapshot      # One per discovered page
└── images.json
```

**manifest.json:**
```json
{
  "app_url": "http://localhost:3000",
  "captured_at": "...",
  "styling_system": "...",
  "pages": [
    { "slug": "...", "url": "...", "purpose": "..." }
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
[list discovered pages]

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

### Agent Prompt Template

```
Task(
  subagent_type="general-purpose",
  description="Propose {name} theme",
  prompt="""
Create theme proposal: {name} ({mode} mode)

Read and follow PROPOSE_{mode}.md exactly.

Assignment:
- Theme name: {name}
- Mode: {mode}
- Constraints: tmp/makeover/constraints.json
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

---

## Phase 5: Generate Preview Index

After all proposals complete, generate `tmp/makeover/themes/index.html` using **templates/index.html** as the base. Replace placeholders with actual proposal data.

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
