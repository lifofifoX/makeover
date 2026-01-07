# Makeover

A Claude Code skill that redesigns any existing application with distinctive, production-grade visual themes.

## Requirements

| Dependency | Purpose | Installation |
|------------|---------|--------------|
| **frontend-design plugin** | Generates distinctive, high-quality designs | `/plugins add claude-plugins-official/frontend-design` |
| **[Playwright MCP](https://github.com/microsoft/playwright-mcp)** | Browses your app to capture real UI | `claude mcp add playwright npx @playwright/mcp@latest` |

## Installation

```bash
mkdir -p .claude/skills
git clone https://github.com/lifofifoX/makeover .claude/skills/makeover
```

## Quick Start

```bash
# 1. Start your app
npm run dev  # or your dev command

# 2. Generate theme proposals
/makeover propose 3 "dark" "minimal"
# → Asks for app URL
# → Browses with Playwright, captures your UI
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
2. Browses your app with Playwright, discovers pages
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

## License

MIT
