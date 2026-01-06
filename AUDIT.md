# Audit Phase (Optional)

Analyze the current design to inform proposals. **This phase is optional** — use it when you want data-driven redesign recommendations.

---

## AUDIT CHECKLIST

After audit, verify:

- [ ] **Color audit** — all colors extracted, harmony analyzed
- [ ] **Typography audit** — fonts, sizes, hierarchy assessed
- [ ] **Spacing audit** — consistency evaluated
- [ ] **Component audit** — patterns cataloged
- [ ] **Accessibility audit** — contrast, focus states checked
- [ ] **Consistency audit** — variations and conflicts noted
- [ ] **Report saved** — `tmp/makeover/audit.md` generated

---

## AUDIT METHODOLOGY

### 1. Color Extraction

Extract all colors used in the application:

```bash
# From CSS files
grep -rohE "#[0-9a-fA-F]{3,8}" --include="*.css" | sort | uniq -c | sort -rn

# From Tailwind classes
grep -rohE "(bg|text|border|fill|stroke)-[a-z]+-[0-9]+" --include="*.{jsx,tsx,vue,html}" | sort | uniq -c

# From inline styles
grep -rohE "color:\s*[^;]+" --include="*.{jsx,tsx,vue,html,css}"

# From CSS variables
grep -rohE "--[a-z-]+:\s*#[0-9a-fA-F]+" --include="*.css"
```

**Analyze:**
- Total unique colors (more than 15 = possible inconsistency)
- Color groupings (how many "blues", "grays", etc.)
- Orphan colors (used once, doesn't fit system)
- Contrast ratios for text/background pairs

### 2. Typography Analysis

```bash
# Font families
grep -rohE "font-family:[^;]+" --include="*.css" | sort | uniq

# Font sizes
grep -rohE "font-size:\s*[^;]+" --include="*.css" | sort | uniq -c | sort -rn

# Font weights
grep -rohE "font-weight:\s*[^;]+" --include="*.css" | sort | uniq -c

# Line heights
grep -rohE "line-height:\s*[^;]+" --include="*.css" | sort | uniq
```

**Analyze:**
- Number of font families (more than 3 = review needed)
- Font size scale coherence (follows a ratio?)
- Heading hierarchy (clear h1 > h2 > h3?)
- Body text readability (size, line-height, measure)

### 3. Spacing Analysis

```bash
# Padding values
grep -rohE "padding[^:]*:\s*[^;]+" --include="*.css" | sort | uniq -c | sort -rn

# Margin values
grep -rohE "margin[^:]*:\s*[^;]+" --include="*.css" | sort | uniq -c | sort -rn

# Gap values
grep -rohE "gap:\s*[^;]+" --include="*.css" | sort | uniq -c
```

**Analyze:**
- Follows a consistent scale? (4px, 8px, 16px, etc.)
- Magic numbers (17px, 23px = not systematic)
- Spacing ratios between elements
- Container max-widths and padding

### 4. Component Pattern Analysis

For each major component type, assess:

**Buttons:**
- Number of distinct button styles
- Consistent padding/sizing?
- Hover/active/disabled states defined?
- Focus states visible?

**Cards:**
- Consistent border-radius?
- Shadow usage consistent?
- Padding internal consistency?

**Forms:**
- Input styling consistent?
- Label positioning consistent?
- Error state styling defined?
- Focus rings visible?

**Navigation:**
- Active state clear?
- Hover feedback present?
- Mobile adaptation exists?

### 5. Accessibility Quick Audit

```bash
# Focus styles
grep -r "focus" --include="*.css" | grep -v "node_modules"

# aria attributes
grep -roh "aria-[a-z]+" --include="*.{jsx,tsx,vue,html}" | sort | uniq

# alt text patterns
grep -r 'alt="' --include="*.{jsx,tsx,vue,html}" | head -10

# Skip links
grep -ri "skip" --include="*.{jsx,tsx,vue,html}" | grep -i "nav\|main\|content"
```

**Check:**
- Color contrast (4.5:1 for text, 3:1 for large text)
- Focus visible on all interactive elements
- Alt text present on images
- Heading hierarchy logical
- Skip links present

### 6. Consistency Score

Rate each area 1-5:

| Area | Score | Notes |
|------|-------|-------|
| Color system | | |
| Typography | | |
| Spacing | | |
| Components | | |
| Accessibility | | |
| **Overall** | | |

**Scoring guide:**
- 5: Systematic, documented, consistent
- 4: Mostly consistent, minor variations
- 3: Inconsistent but salvageable
- 2: Significant inconsistencies
- 1: No apparent system

---

## AUDIT REPORT TEMPLATE

Generate at `tmp/makeover/audit.md`:

```markdown
# Design Audit: [App Name]

Generated: [timestamp]

## Executive Summary

**Overall Score: [X/5]**

[2-3 sentence summary of current design state]

### Top Strengths
1. [strength]
2. [strength]
3. [strength]

### Priority Improvements
1. [improvement]
2. [improvement]
3. [improvement]

---

## Color Audit

**Score: [X/5]**

### Current Palette

| Color | Hex | Usage | Count |
|-------|-----|-------|-------|
| [name] | [hex] | [where used] | [times] |

### Analysis

- **Total unique colors**: [count]
- **Primary palette coherence**: [assessment]
- **Orphan colors**: [list any that don't fit]

### Contrast Issues

| Combination | Ratio | WCAG | Location |
|-------------|-------|------|----------|
| [text/bg] | [ratio] | [pass/fail] | [where] |

### Recommendations

- [specific recommendation]

---

## Typography Audit

**Score: [X/5]**

### Font Stack

| Role | Family | Weights | Sizes |
|------|--------|---------|-------|
| Headings | [font] | [weights] | [sizes] |
| Body | [font] | [weights] | [sizes] |
| Mono | [font] | [weights] | [sizes] |

### Type Scale

| Element | Size | Line Height | Weight |
|---------|------|-------------|--------|
| h1 | | | |
| h2 | | | |
| h3 | | | |
| body | | | |
| small | | | |

### Analysis

- **Scale coherence**: [does it follow a ratio?]
- **Hierarchy clarity**: [clear visual hierarchy?]
- **Readability**: [body text assessment]

### Recommendations

- [specific recommendation]

---

## Spacing Audit

**Score: [X/5]**

### Current Scale

[list spacing values found, frequency]

### Analysis

- **Systematic**: [yes/no, explanation]
- **Base unit**: [identified or inconsistent]
- **Problem areas**: [specific inconsistencies]

### Recommendations

- [specific recommendation]

---

## Component Audit

**Score: [X/5]**

### Buttons

| Variant | Padding | Border Radius | States |
|---------|---------|---------------|--------|
| Primary | | | hover: ✓/✗, focus: ✓/✗, disabled: ✓/✗ |
| Secondary | | | |

**Issues**: [list any]

### Cards

| Variant | Padding | Shadow | Border Radius |
|---------|---------|--------|---------------|
| Default | | | |

**Issues**: [list any]

### Forms

| Element | Styling | Focus | Error |
|---------|---------|-------|-------|
| Text input | | ✓/✗ | ✓/✗ |
| Select | | | |
| Checkbox | | | |

**Issues**: [list any]

### Navigation

| Element | Active State | Hover | Mobile |
|---------|--------------|-------|--------|
| Main nav | ✓/✗ | ✓/✗ | ✓/✗ |
| Footer links | | | |

**Issues**: [list any]

---

## Accessibility Audit

**Score: [X/5]**

### Contrast Compliance

- **Text**: [X of Y pass WCAG AA]
- **Large text**: [X of Y pass]
- **UI components**: [X of Y pass]

### Interactive Elements

- **Focus visible**: [all/some/none]
- **Focus order logical**: [yes/no]
- **Touch targets (48px)**: [all/some/none]

### Semantic Structure

- **Heading hierarchy**: [correct/issues]
- **Landmark regions**: [present/missing]
- **Alt text**: [all/some/none]

### Recommendations

- [specific recommendation]

---

## Recommendations Summary

### Quick Wins (Low effort, high impact)

1. [recommendation]
2. [recommendation]

### Medium Priority

1. [recommendation]
2. [recommendation]

### Major Refactors

1. [recommendation]
2. [recommendation]

---

## Design System Opportunity

Based on this audit, a systematic redesign could address:

- [opportunity 1]
- [opportunity 2]
- [opportunity 3]

Recommended approach: [light touch / systematic overhaul / incremental migration]
```

---

## AUDIT AGENT PROMPT

Use this when spawning audit agents:

```
You are auditing an application's current design.

## Prerequisites

Read the app profile at `tmp/makeover/profile.md` first.

## Your Task

1. Extract and analyze all design decisions
2. Score each area objectively
3. Identify strengths and weaknesses
4. Provide actionable recommendations

## Audit Areas

1. **Colors** — extract all, check contrast, assess system
2. **Typography** — fonts, scale, hierarchy
3. **Spacing** — consistency, scale, rhythm
4. **Components** — patterns, states, variations
5. **Accessibility** — contrast, focus, semantics

## Tools to Use

- Grep: extract patterns from code
- Read: examine specific files
- Bash: run extraction commands

## Scoring Guidelines

- Be objective, not harsh
- Note both positives and negatives
- Specific examples for every critique
- Actionable recommendations only

## DO NOT

- Modify any files
- Be unnecessarily critical
- Make vague recommendations
- Skip the numerical scoring

## Output

1. Write audit to: `tmp/makeover/audit.md`
2. Return summary:
   - Overall score
   - Top 3 strengths
   - Top 3 priorities
   - Recommended redesign approach
```

---

## USING AUDIT IN PROPOSALS

When the audit is complete, proposal agents should:

1. **Read audit first** — understand current strengths/weaknesses
2. **Preserve strengths** — don't fix what isn't broken
3. **Address priorities** — proposals should solve top issues
4. **Reference audit** — "This addresses the spacing inconsistency noted in audit"

The audit creates constraints that make proposals more targeted and useful.
