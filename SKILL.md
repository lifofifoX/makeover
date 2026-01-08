---
name: makeover
description: Redesign any app with distinctive, production-grade visual themes using real app content.
---

# Makeover

## Dependencies

| Dependency | Installation |
|------------|--------------|
| frontend-design plugin | `/plugins add claude-plugins-official/frontend-design` |
| Playwright MCP | `claude mcp add playwright npx @playwright/mcp@latest` |

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
