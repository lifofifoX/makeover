# Orchestrator Workflow

Router for proposal generation. Check JSON files and load only needed modules.

---

## Execution Flow

| Step | Check File | If Missing | If Exists |
|------|------------|------------|-----------|
| 1 | `references/summary.json` | → `orchestrate/reference.md` (if URLs/images provided) | Skip |
| 2 | `capture/manifest.json` | → `orchestrate/capture.md` | Skip |
| 3 | `capture/ui-elements.json` | → `orchestrate/ui-elements.md` | Skip |

All paths relative to `tmp/makeover/`.

---

## Clarify Intent

If user prompt is ambiguous or could benefit from clarification, use AskUserQuestion to understand their intent before planning. Probe what they actually mean - don't offer prescriptive options.

---

## Variance Planning

Pre-compute constraints to ensure diverse proposals.

### Normal Mode

**Read `./DNA_CODES.md` for valid code options.**

Ensure ≥3 DNA position differences between proposals:

| Axis | Rule |
|------|------|
| Header (H) | No duplicates across proposals |
| Layout (L) | No duplicates across proposals |
| Color Temperature | At least 2 different (warm/cool/neutral) |
| Motion | Spread across N1-3, N4-6, N7-9 |

### Wild Mode

Assign different structural mutations to each proposal. No two proposals share the same primary mutation.

---

## Spawn Proposal Agents

Before launching agents, read and prepare:
1. `tmp/makeover/capture/ui-elements.json` - inline in prompt
2. `tmp/makeover/capture/images.json` - filter to valid URLs only
3. `tmp/makeover/capture/instructions.md` - technical constraints (if exists)

Launch all agents in parallel with inlined content:

```
Task(
  subagent_type="general-purpose",
  description="Propose {name} theme",
  prompt="""
Create theme proposal: {name} ({mode} mode)

Read and follow PROPOSE_{mode}.md exactly.

Assignment:
- Theme name: {name}
- Mode: {mode}
- Constraints: {inlined constraints for this agent}

App-specific UI elements:
{inlined ui-elements.json content}

Technical constraints:
{inlined instructions.md content, or "None" if file doesn't exist}

Images — NO PLACEHOLDERS, use only these URLs:
{inlined valid image URLs from images.json}
"""
)
```

After all complete, generate `tmp/makeover/themes/index.html` using **./templates/index.html** as base.

---

## Final Output

```
tmp/makeover/
├── capture/
│   ├── manifest.json
│   ├── {page}.snapshot (per page)
│   ├── images.json
│   ├── ui-elements.json
│   └── instructions.md (if provided)
├── references/ (if browsed)
│   └── summary.json
└── themes/
    ├── index.html
    └── {name}.html (per proposal)
```

Report to user: **"Open tmp/makeover/themes/index.html to compare proposals"**
