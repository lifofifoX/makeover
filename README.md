# Makeover

A Claude Code skill that redesigns any existing application with distinctive, production-grade visual themes.

## Installation

```bash
mkdir -p .claude/skills
git clone https://github.com/YOUR_USERNAME/makeover .claude/skills/makeover
```

## Quick Start

```bash
# 1. Analyze your app
/makeover discover

# 2. Generate theme proposals
/makeover propose 3 "dark" "minimal"

# 3. Review proposals
open tmp/makeover/themes/index.html

# 4. Implement your favorite
/makeover implement chosen-theme-name
```

## How It Works

### Step 1: Discovery

```bash
/makeover discover
```

The skill scans your codebase and learns:
- What pages/routes exist
- Your styling approach (Tailwind, CSS modules, vanilla, etc.)
- Interactive patterns (modals, dropdowns, auth states)
- Build commands

This creates `tmp/makeover/profile.md` — review it to ensure accuracy. **Edit this file** to add context the skill missed or to specify preferences.

### Step 2: Proposals

```bash
/makeover propose 3 "inspiration keywords"
```

Generates self-contained HTML previews you can open in a browser. Each proposal shows every page with the new design applied.

### Step 3: Implementation

```bash
/makeover implement theme-name
```

Converts the approved proposal into production code, adapting to your existing styling system.

## Using Image References

The most effective way to communicate your vision is with images:

```
Here are some screenshots of designs I like [attach images]

/makeover propose 2
```

Share:
- Screenshots of websites you admire
- Album covers, posters, or artwork
- Your current app (for context)
- Mood boards or design inspiration

The skill analyzes colors, typography, layout patterns, and mood from your references.

## Adapting to Your App

### Training the Profile

After discovery, edit `tmp/makeover/profile.md` to:

- Correct any misdetected pages or patterns
- Add context about your app's purpose
- Specify constraints ("must keep sidebar nav", "auth modal is critical")
- Note any third-party components

### Project-Specific Patterns

If your app has unique interactive patterns, document them in the profile:

```markdown
## Custom Patterns

### Toast Notifications
- Triggered via `window.showToast(message)`
- Positioned top-right
- Auto-dismiss after 3s
```

The skill will preserve these during implementation.

### Iterating on Proposals

Proposals are starting points. After reviewing:

```
I like the "aurora" theme but:
- Make the header sticky
- Use more contrast on buttons
- The cards should have more padding

/makeover propose 1 --refine aurora
```

## Commands

| Command | Purpose |
|---------|---------|
| `/makeover discover` | Analyze app structure |
| `/makeover audit` | Optional design health check |
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

- **Start with discover** — always run this first on a new project
- **Use images** — visual references are more effective than keywords
- **Edit the profile** — add your knowledge about the app
- **Iterate** — refine proposals with specific feedback
- **Check mobile** — proposals include responsive layouts

## Requirements

- [Claude Code](https://claude.ai/code) CLI
- `frontend-design` plugin (for generating proposals)

## License

MIT
