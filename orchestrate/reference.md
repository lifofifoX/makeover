# Reference Research

**Skip if:** `tmp/makeover/references/summary.json` exists
**Ask if:** User provided no URLs, images, or keywords
**Output:** `tmp/makeover/references/summary.json`

---

## When User Provides URLs

Using browser adapter (see `lib/browser.md`):

1. Navigate to each URL
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

---

## When User Provides Keywords Only

Do NOT browse external sites. Use keywords to inform style direction during variance planning.

Store keywords in `tmp/makeover/references/summary.json`:
```json
{
  "type": "keywords",
  "keywords": ["warm", "editorial", "serif"],
  "extracted_at": "..."
}
```

---

## When User Provides Images

Use Read tool to analyze reference images:

| Element | Look For |
|---------|----------|
| Colors | Dominant hue, accents, contrast, saturation |
| Typography | Serif/sans/display, weight, case, spacing |
| Layout | Centered/asymmetric, grid/organic, dense/spacious |
| Texture | Grain/smooth, matte/glossy, layered/flat |
| Mood | Era, emotion, energy level |

Write analysis to `tmp/makeover/references/summary.json`

---

## When NOT to Browse

- Do NOT screenshot generated proposal HTML files
- Do NOT browse without user request or reference URLs
- Skip if references already cached
