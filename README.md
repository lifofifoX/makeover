# Makeover

A Claude Code plugin that redesigns any existing application with distinctive, production-grade visual themes.

## Installation

Add marketplace:
```
/plugin marketplace add https://github.com/lifofifoX/makeover
```

Install plugin:
```
/plugin install makeover
```

### Dependencies

| Dependency | Installation |
|------------|--------------|
| frontend-design plugin | `/plugin marketplace add anthropics/claude-plugins-official` then `/plugin install frontend-design` |
| Browser automation | Claude Chrome (`--chrome` flag), [agent-browser](https://github.com/vercel-labs/agent-browser), or [Playwright MCP](https://github.com/microsoft/playwright-mcp) |

Falls back to code analysis if no browser tool installed.

## Usage

Start your app first, then:

```
# Generate theme proposals
/makeover:propose 3 "dark" "minimal"

# Wild mode for experimental designs
/makeover:propose 2 --wild "vaporwave"

# Implement a proposal
/makeover:implement midnight-cinema
```

Proposals use your **real app content**, not mocks. Review at `tmp/makeover/themes/index.html`.

Attach screenshots or mood boards with propose for better results.

## License

MIT
