# Browser Adapter

Unified interface over available browser automation tools. Auto-detects and uses the best available option.

## Tool Detection

Check tools in priority order, use first **working** option:

| Priority | Tool | Detection | Verification |
|----------|------|-----------|--------------|
| 1 | claude-in-chrome | Tool exists | `tabs_context_mcp` succeeds (no "not connected" error) |
| 2 | agent-browser | `which agent-browser` returns path | None |
| 3 | Playwright MCP | Tool exists | None |

**Important:** For claude-in-chrome, the tool existing is not enough. Call `tabs_context_mcp` first. If it returns "Browser extension is not connected", skip to next option.

**Announce selection:** "Using [tool name] for browser automation."

---

## Setup

Run before first browser operation:

| Tool | Setup Required |
|------|----------------|
| claude-in-chrome | `tabs_create_mcp` to get tabId (context already verified during detection) |
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

If no browser tool is working (either doesn't exist or verification fails):

1. Announce: "No browser automation available. Analyzing app code instead."
2. Read app source files (HTML, JSX, ERB, etc.) to understand structure
3. Generate manifest from code analysis rather than live browsing
4. Note in `manifest.json`: `"source": "code_analysis"` instead of `"source": "browser"`

This provides degraded but functional experience without requiring browser setup.

---

## Detection Flow Example

```
1. Check claude-in-chrome tool exists? Yes
2. Call tabs_context_mcp
3. Response contains "not connected"? → Skip, try next
4. Check agent-browser: `which agent-browser` → Not found → Skip
5. Check Playwright MCP tool exists? No → Skip
6. No working tools → Use code analysis mode
```
