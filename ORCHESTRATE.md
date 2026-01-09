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

## Variance Planning

Pre-compute constraints to ensure diverse proposals. Write to `tmp/makeover/constraints.json` (or append if file exists).

### Normal Mode

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

Launch all agents in parallel:

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
- Constraints: tmp/makeover/constraints.json
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
├── constraints.json
└── themes/
    ├── index.html
    └── {name}.html (per proposal)
```

Report to user: **"Open tmp/makeover/themes/index.html to compare proposals"**
