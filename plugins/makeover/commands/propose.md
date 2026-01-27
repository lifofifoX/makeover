---
name: makeover:propose
description: Generate distinctive theme proposals for your running app. Captures real UI content and creates multiple design variations.
argument-hint: [count] [keywords...] [--wild]
---

# Makeover Propose

Generate theme proposals using real app content.

## Dependencies

- **frontend-design plugin**
- **Browser automation** - Claude Chrome (`--chrome`), agent-browser, or Playwright MCP

## Arguments

Parse from $ARGUMENTS:

| Argument | Default | Effect |
|----------|---------|--------|
| `count` | 3 | Number of proposals |
| `keywords` | none | Style hints (browse references, influence design) |
| `--wild` | false | Wild mode (structural mutations required) |

## Workflow

1. Parse arguments from $ARGUMENTS
2. Read and follow `skills/makeover/ORCHESTRATE.md`
