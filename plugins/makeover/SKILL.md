---
name: makeover
description: Redesign any app with distinctive, production-grade visual themes using real app content.
---

# Makeover

## Dependencies

| Dependency | Installation |
|------------|--------------|
| frontend-design plugin | `/plugins add claude-plugins-official/frontend-design` |

### Browser Automation (one of these)

| Option | Setup | Notes |
|--------|-------|-------|
| Claude Chrome | Run with `--chrome` flag | Native, recommended |
| agent-browser | `npm i -g agent-browser && agent-browser install` | Lightweight, context-efficient |
| Playwright MCP | `claude mcp add playwright npx @playwright/mcp@latest` | Full-featured |

Skill auto-detects available tool. No config needed if using `--chrome`. Without browser tools, skill analyzes code instead.

## Command Parsing

```
/makeover propose [count] [keywords...] [--wild]
/makeover implement [name]
```

| Argument | Default | Effect |
|----------|---------|--------|
| `count` | 3 | Number of proposals to generate |
| `keywords` | none | Inspiration hints (browse references, influence style) |
| `--wild` | false | Wild mode (structural transformation required) |

## Orchestrator Workflow

1. Parse arguments (count, mode, keywords)
2. Read and follow ORCHESTRATE.md
