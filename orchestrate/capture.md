# App Discovery & Capture

**Skip if:** `tmp/makeover/capture/manifest.json` exists
**Ask if:** Never
**Output:** `tmp/makeover/capture/manifest.json`, `*.snapshot`, `images.json`, `instructions.md`

---

## Step 0: Detect Browser Tool

Follow `lib/browser.md` to detect available browser automation.

**Announce:** "Using [tool name] for browser automation." or "No browser available, analyzing code instead."

If no browser tool available, skip to **Step 1b: Code Analysis Mode**.

---

## Step 1: Get App URL

```
"Where is your app running?"
Default: http://localhost:3000
```

---

## Step 1b: Code Analysis Mode (No Browser)

**Only if no browser tool available.**

Instead of browsing, analyze app source code:

1. Find view files: `*.html`, `*.erb`, `*.jsx`, `*.tsx`, `*.vue`, `*.svelte`
2. Find route definitions: `routes.rb`, `router.js`, `pages/` directory
3. Read files and extract:
   - Page structure (headings, sections, components)
   - Image references (`<img>`, `Image` components)
   - Navigation structure (links, menus)
   - Styling system (Tailwind classes, CSS imports)

Generate manifest with `"source": "code_analysis"`:
```json
{
  "app_url": "http://localhost:3000",
  "source": "code_analysis",
  "captured_at": "...",
  "styling_system": "...",
  "pages": [...]
}
```

**Skip to Step 5** after code analysis.

---

## Step 2: Discover Pages

Using browser adapter (see `lib/browser.md`), navigate and explore:
- Click navigation links
- Follow any visible routes in the UI
- Look at DOM for route information

For each distinct page, note:
- URL/route
- Page purpose
- Key content elements

---

## Step 3: Capture to Files

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
    { "slug": "...", "url": "...", "purpose": "...", "included": true }
  ]
}
```

**{page}.snapshot** (one per page):
- Accessibility tree snapshot via browser adapter
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

Rules:
- Extract `src` via JS execution (`document.querySelectorAll('img')`) when available
- Fallback: parse accessibility tree for image elements if JS execution unavailable
- Full URLs only — never truncate
- Only `<img>` elements — skip iframes, embedded content, data URIs
- Skip decorative/icon images (small UI elements)

---

## Step 4: Detect Styling System

Quick detection from DOM/files:

| System | Detection |
|--------|-----------|
| Tailwind | Classes like `bg-blue-500`, `px-4`, `flex` |
| CSS Modules | Classes like `styles_button__abc123` |
| Styled-components | `sc-` prefixed classes |
| Vanilla CSS | Standard class names, inline styles |

Record in manifest.json.

---

## Step 5: Confirm Pages with User

```
"I found these pages in your app:
[list discovered pages]

Which pages should appear in the theme proposals?"

Options: [All of these (Recommended)] [Select specific pages]
```

Update manifest.json with `"included": true/false` per page.

---

## Step 6: App Quirks

```
"Are there any technical quirks about your app that proposals should account for?"

Options: [No, continue] [Yes, let me describe them]
```

If user provides quirks, write to `tmp/makeover/capture/instructions.md`.

**Technical constraints only** - NOT design direction (that comes from the propose prompt).
