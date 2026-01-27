# Browser Adapter

Unified interface over available browser automation tools. Auto-detects and uses the best available option.

## Tool Detection

Check tools in priority order, use first available:

| Priority | Tool | Detection |
|----------|------|-----------|
| 1 | claude-in-chrome | `mcp__claude-in-chrome__navigate` tool exists |
| 2 | agent-browser | Bash `which agent-browser` returns path |
| 3 | Playwright MCP | `mcp__playwright__browser_navigate` tool exists |

**Announce selection:** "Using [tool name] for browser automation."

---

## Setup

Run before first browser operation:

| Tool | Setup Required |
|------|----------------|
| claude-in-chrome | `tabs_context_mcp` then `tabs_create_mcp` to get tabId |
| agent-browser | None |
| Playwright MCP | None |

Store tabId (claude-in-chrome) for subsequent operations.

---

## Operations

### navigate(url)

| Tool | Method |
|------|--------|
| claude-in-chrome | `navigate` with `url` and `tabId` params |
| agent-browser | `agent-browser navigate {url}` via Bash |
| Playwright MCP | `browser_navigate` with `url` param |

### snapshot()

Returns accessibility tree of current page.

| Tool | Method |
|------|--------|
| claude-in-chrome | `read_page` with `tabId` |
| agent-browser | `agent-browser snapshot` via Bash |
| Playwright MCP | `browser_snapshot` |

### click(target)

Click element by text, role, or selector.

| Tool | Method |
|------|--------|
| claude-in-chrome | `find` to get ref, then `computer` with `action=left_click` and `ref` |
| agent-browser | `agent-browser click "{target}"` via Bash |
| Playwright MCP | `browser_click` with `element` param |

### executeJS(code)

Execute JavaScript in page context. Returns result.

| Tool | Method |
|------|--------|
| claude-in-chrome | `javascript_tool` with `text` (code) and `tabId` |
| agent-browser | `agent-browser evaluate "{code}"` via Bash |
| Playwright MCP | `browser_evaluate` with `expression` param |

**Fallback:** If tool lacks JS execution, parse accessibility tree for needed data (e.g., img elements).

### getText()

Get page text content.

| Tool | Method |
|------|--------|
| claude-in-chrome | `get_page_text` with `tabId` |
| agent-browser | `agent-browser text` via Bash |
| Playwright MCP | Extract from `browser_snapshot` |

---

## No Browser Available

If no browser tool detected:

1. Announce: "No browser automation available. Analyzing app code instead."
2. Read app source files (HTML, JSX, ERB, etc.) to understand structure
3. Generate manifest from code analysis rather than live browsing
4. Note in `manifest.json`: `"source": "code_analysis"` instead of `"source": "browser"`

This provides degraded but functional experience without requiring browser setup.
