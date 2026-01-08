# Capture Workflow

Playwright-based app discovery and content capture. **Orchestrator reads this, not proposal agents.**

---

## Step 1: Get App URL

```
"Where is your app running?"
Default: http://localhost:3000
```

## Step 2: Browse and Discover Pages

Navigate to the app URL. Explore by:
- Clicking navigation links
- Checking common routes (/dashboard, /settings, /profile, /[id])
- Looking at the DOM for route information

For each distinct page:
- Take a snapshot (accessibility tree)
- Note the URL/route
- Note the page purpose

## Step 3: Ask User Which Pages

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

## Step 4: Capture DOM Structure

For each selected page, extract:
- **Actual content** — real text, headings, labels
- **Real images** — actual image URLs from the page
- **Component structure** — buttons, cards, forms, modals
- **Current classes** — detect Tailwind, CSS modules, etc.

Store this as context for proposal agents.

## Step 5: Detect Styling System

Quick detection from DOM/files:
- Tailwind: class names like `bg-blue-500`, `px-4`
- CSS Modules: class names like `styles_button__abc123`
- Styled-components: `sc-` prefixed classes
- Vanilla CSS: standard class names, inline styles

Note the system for proposal metadata.

---

## Visual Research (Optional)

### Browsing Reference Sites

When user mentions inspiration sources, use Playwright to visit them:

```
"I want something like stripe.com and linear.app"
→ Navigate to stripe.com, take snapshots
→ Navigate to linear.app, take snapshots
→ Analyze: typography, spacing, color, layout patterns, motion
```

**When to browse:**
- User mentions specific sites ("like Notion", "Vercel vibes")
- User provides URLs
- Vague inspiration ("minimal SaaS") — find canonical examples

**When NOT to browse:**
- Do NOT screenshot generated proposal HTML files
- Do NOT browse unless user explicitly asks or provides reference URLs

### Analyzing Image References

When user provides reference images, use Read tool to analyze:

| Element | What to Look For |
|---------|------------------|
| Colors | Dominant hue, accents, contrast, saturation, temperature |
| Typography | Serif/sans/display, weight, case, spacing, era |
| Layout | Centered/asymmetric, grid/organic, dense/spacious |
| Texture | Grain/smooth, matte/glossy, layered/flat |
| Mood | Era, emotion, energy level, cultural context |

---

## Spawning Proposal Agents

After capture, spawn agents in parallel:

```
Task(subagent_type="general-purpose", description="Propose {name} theme", prompt="...")
```

Pass to each agent:
1. Captured page content (DOM, text, images)
2. Detected styling system
3. Which file to read (PROPOSE_NORMAL.md or PROPOSE_WILD.md)
4. Theme assignment (name, references, palette direction)

---

## Preview Index Generation

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
    .card-dna { font-family: ui-monospace, monospace; font-size: 0.75rem; color: #888; margin: 0 0 0.75rem; }
    .card-desc { font-size: 0.875rem; color: #555; margin: 0; line-height: 1.5; }
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
        <h2 class="card-title">[Theme Name]</h2>
        <p class="card-dna">DNA: [code]</p>
        <p class="card-desc">[Brief description]</p>
      </div>
    </a>
  </div>
</body>
</html>
```
