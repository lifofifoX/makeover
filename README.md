# Makeover

A Claude Code plugin that redesigns any existing application with distinctive, production-grade visual themes.

## Installation

```bash
/plugin marketplace add https://github.com/lifofifoX/makeover
/plugin install makeover
```

### Dependencies

| Dependency | Purpose | Installation |
|------------|---------|--------------|
| **frontend-design plugin** | Generates distinctive designs | `/plugins add claude-plugins-official/frontend-design` |
| **Browser automation** (one of these) | Browses your app to capture real UI | See below |

#### Browser Automation Options

| Option | Setup | Notes |
|--------|-------|-------|
| Claude Chrome | Run Claude with `--chrome` flag | Native, recommended |
| agent-browser | `npm i -g agent-browser && agent-browser install` | Lightweight |
| Playwright MCP | `claude mcp add playwright npx @playwright/mcp@latest` | Full-featured |

The skill auto-detects which tool is available. If none are configured, it falls back to code analysis mode (no live browsing).

## Quick Start

```bash
# 1. Start your app
npm run dev  # or your dev command

# 2. Generate theme proposals
/makeover propose 3 "dark" "minimal"
# → Asks for app URL
# → Browses with available tool, captures your UI
# → Asks which pages to include
# → Generates proposals using your real content

# Or go wild
/makeover propose 2 --wild "vaporwave"

# 3. Review proposals
open tmp/makeover/themes/index.html

# 4. Implement your favorite
/makeover implement chosen-theme-name
```

## How It Works

### Propose

```bash
/makeover propose 3 "inspiration keywords"
```

1. Asks where your app is running (default: localhost:3000)
2. Browses your app with browser automation, discovers pages
3. Asks which pages to include in proposals
4. Captures real DOM content, images, text
5. Detects your styling system (Tailwind, CSS modules, etc.)
6. Generates HTML previews using your actual UI

Proposals show exactly how themes look on **your real app**, not mock content.

### Implement

```bash
/makeover implement theme-name
```

Reads the approved proposal, extracts embedded metadata and CSS, adapts to your styling system.

## Using Image References

Visual references are the most effective way to communicate your vision:

```
Here are some screenshots of designs I like [attach images]

/makeover propose 2
```

Share:
- Screenshots of websites you admire
- Album covers, posters, or artwork
- Mood boards or design inspiration

## Commands

| Command | Purpose |
|---------|---------|
| `/makeover propose N [hints...]` | Generate N theme proposals |
| `/makeover propose N --wild` | Experimental/unconventional themes |
| `/makeover implement name` | Build approved theme |

## Wild Mode

For experimental designs that break conventions:

```bash
/makeover propose 2 --wild "cyberpunk"
```

Wild themes use unconventional navigation, theatrical data presentation, visual chaos, and ambient motion effects.

## Tips

- **Start your app first** — proposals need a running app to browse
- **Use images** — visual references are more effective than keywords
- **Iterate** — refine proposals with specific feedback
- **Check mobile** — proposals include responsive layouts

## Troubleshooting

### "Required dependency missing" error

Install the frontend-design plugin:
```bash
/plugins add claude-plugins-official/frontend-design
```

### Browser automation not working

1. Verify one of the browser tools is installed (see Dependencies above)
2. If using Claude Chrome, make sure you're running with `--chrome` flag
3. Check that your app is running and accessible at the URL you provide

### Proposals not matching my app

- Make sure the app is fully loaded before running `/makeover propose`
- Check `tmp/makeover/capture/manifest.json` to see what pages were captured
- Add specific instructions in `tmp/makeover/capture/instructions.md` for app quirks

## License

MIT
