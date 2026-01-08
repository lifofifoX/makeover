# CLAUDE.md

Routing guide for makeover skill. **Do not duplicate content from other files here.**

## Dependencies

1. **frontend-design plugin**: `/plugins add claude-plugins-official/frontend-design`
2. **Playwright MCP**: `claude mcp add playwright npx @playwright/mcp@latest`

## File Routing

| Role | Phase | Read |
|------|-------|------|
| Orchestrator | Capture & Planning | CAPTURE.md |
| Agent | Normal proposal | TEMPLATE.md, PROPOSE_NORMAL.md, captures from tmp/makeover/capture/ |
| Agent | Wild proposal | TEMPLATE.md, PROPOSE_WILD.md, captures from tmp/makeover/capture/ |
| Agent | Needs DNA/scale details | + DESIGN_SYSTEM.md |
| Agent | N3+ motion | + MOTION.md |
| Agent | Implementation | IMPLEMENT.md |

**Principle:** Agents read from files, not inline prompts. Captures and constraints stored in tmp/makeover/.

## Orchestrator Workflow

1. Read CAPTURE.md for complete workflow
2. **Phase 1:** Browse references (if user provides URLs/keywords)
3. **Phase 2:** Discover and capture app pages to tmp/makeover/capture/
4. **Phase 3:** Pre-compute variance constraints to tmp/makeover/constraints.json
5. **Phase 4:** Spawn proposal agents in parallel (pass file paths, not content)
6. **Phase 5:** Generate index.html linking all proposals
7. Report: "Open tmp/makeover/themes/index.html to compare"

## File-Based Architecture

```
tmp/makeover/
├── capture/
│   ├── manifest.json      # Pages, styling system
│   ├── {page}.snapshot    # DOM captures per page
│   └── images.json        # Extracted image URLs
├── references/            # Optional: browsed reference sites
│   └── summary.json
├── constraints.json       # Pre-computed variance constraints
└── themes/
    ├── index.html         # Comparison page
    └── {name}.html        # Individual proposals
```

## Mode Summary

| Mode | DNA | Key Constraint |
|------|-----|----------------|
| Normal | Required: `H#-L#-G#-D#-C#-N#` | Systematic design, spacing scale, no pure #000/#FFF |
| Wild | Optional: `DNA: FREEFORM` | **Structural transformation required** — visual wild alone fails |

## Both Modes

- **Follow TEMPLATE.md structure exactly** — all 5 sections required
- Real app content only (no placeholders)
- Real images from app (or realistic internet images)
- Cite 2-3 specific references
- Embed MAKEOVER_METADATA comment
