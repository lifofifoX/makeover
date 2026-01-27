---
title: Flexible Browser Automation
type: refactor
date: 2026-01-27
---

# Flexible Browser Automation

Remove Playwright MCP as hard dependency. Use whatever browser automation is available: claude-in-chrome, agent-browser CLI, or Playwright MCP.

## Problem

- Current: SKILL.md requires Playwright MCP installation
- Friction: Users must configure MCP server before using skill
- claude-in-chrome now available natively via `--chrome` flag
- agent-browser CLI claims 93% less context usage

## Proposed Solution

Detect available browser tools at runtime, use best available option with unified interface.

**Priority order:**
1. claude-in-chrome (native, no setup if `--chrome`)
2. agent-browser (lightweight, context-efficient)
3. Playwright MCP (most capable, current default)

## Technical Approach

### 1. Create Browser Adapter Layer

New file: `lib/browser.md` - abstraction over browser tools

**Detection via tool availability:**
```
claude-in-chrome: mcp__claude-in-chrome__* tools present
agent-browser: check `which agent-browser` returns path
Playwright MCP: mcp__playwright__* tools present
```

**Unified operations mapping:**

| Operation | claude-in-chrome | agent-browser | Playwright MCP |
|-----------|------------------|---------------|----------------|
| Navigate | `navigate` | `agent-browser navigate <url>` | `browser_navigate` |
| Click | `computer` action=left_click | `agent-browser click <selector>` | `browser_click` |
| Snapshot | `read_page` | `agent-browser snapshot` | `browser_snapshot` |
| Execute JS | `javascript_tool` | `agent-browser evaluate <code>` | `browser_evaluate` |
| Get text | `get_page_text` | `agent-browser text` | via snapshot |

### 2. Update orchestrate/capture.md

Replace Playwright-specific references with adapter calls:
- "Navigate with Playwright" → "Navigate with browser adapter"
- Add tool selection announcement at start
- Handle capability gaps gracefully

### 3. Update orchestrate/reference.md

Same adapter usage for reference URL browsing.

### 4. Update SKILL.md

**Current:**
```markdown
| Dependency | Installation |
|------------|--------------|
| Playwright MCP | `claude mcp add playwright npx @playwright/mcp@latest` |
```

**New:**
```markdown
## Browser Automation (one of these)

| Option | Setup | Notes |
|--------|-------|-------|
| Claude Chrome | Run with `--chrome` flag | Native, recommended |
| agent-browser | `npm i -g agent-browser && agent-browser install` | Lightweight |
| Playwright MCP | `claude mcp add playwright npx @playwright/mcp@latest` | Full-featured |

Skill auto-detects available tool. No config needed if using `--chrome`.
```

### 5. Update settings.local.json

Add permissions for all browser tools:
```json
"mcp__claude-in-chrome__*",
"mcp__playwright__*"
```

### 6. Handle No Browser Available

If no browser tool detected:
1. List installation options
2. Offer degraded mode: user provides screenshots manually
3. Analyze provided images with Read tool instead of browsing

## Acceptance Criteria

- [x] `/makeover propose` works with only claude-in-chrome available
- [x] `/makeover propose` works with only agent-browser available
- [x] `/makeover propose` works with only Playwright MCP available
- [x] Clear error message when no browser tool available
- [x] Tool selection announced to user at capture start
- [x] Existing Playwright MCP users unaffected

## Files to Modify

```
SKILL.md                        # Update dependencies section
lib/browser.md                  # NEW - browser adapter
orchestrate/capture.md          # Use adapter instead of Playwright
orchestrate/reference.md        # Use adapter instead of Playwright
.claude/settings.local.json     # Add claude-in-chrome permissions
```

## Open Questions

1. **agent-browser JS execution** - Does `agent-browser evaluate` exist? Docs unclear. Need to test.

2. **Snapshot format parity** - Do `read_page` and `browser_snapshot` return equivalent structures? May need format normalization.

3. **Tab management** - claude-in-chrome requires `tabs_context_mcp` first. Adapter needs to handle this.

4. **Degraded mode scope** - If tool lacks JS execution, skip image extraction or fail entirely?

## MVP

### lib/browser.md

```markdown
# Browser Adapter

Unified interface over available browser automation tools.

## Detection

Check in order, use first available:

1. **claude-in-chrome**: `mcp__claude-in-chrome__navigate` tool exists
2. **agent-browser**: Bash `which agent-browser` succeeds
3. **Playwright MCP**: `mcp__playwright__browser_navigate` tool exists

## Before First Use

If claude-in-chrome: call `tabs_context_mcp` then `tabs_create_mcp`
If agent-browser: no setup needed
If Playwright: no setup needed

## Operations

### navigate(url)

claude-in-chrome: `navigate` with url param
agent-browser: `agent-browser navigate {url}`
Playwright: `browser_navigate` with url param

### snapshot()

claude-in-chrome: `read_page` with tabId
agent-browser: `agent-browser snapshot`
Playwright: `browser_snapshot`

### click(target)

claude-in-chrome: `find` then `computer` action=left_click with ref
agent-browser: `agent-browser click {target}`
Playwright: `browser_click` with element param

### executeJS(code)

claude-in-chrome: `javascript_tool` with text param
agent-browser: `agent-browser evaluate {code}`
Playwright: `browser_evaluate` with expression param

### getText()

claude-in-chrome: `get_page_text`
agent-browser: `agent-browser text`
Playwright: via snapshot
```

### capture.md changes

```diff
## Step 2: Discover Pages

+**Browser tool:** Announce which tool was detected and will be used.
+
-Navigate and explore:
+Using detected browser adapter, navigate and explore:
- Click navigation links
- Follow any visible routes in the UI
- Look at DOM for route information
```

## References

- claude-in-chrome: Native Chrome extension via `--chrome` flag
- agent-browser: https://github.com/vercel-labs/agent-browser
- Playwright MCP: https://github.com/playwright-community/mcp
