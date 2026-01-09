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

**Before spawning agents**, read these files to inject into prompts:
- `capture/images.json` - available images
- `capture/ui-elements.json` - app-specific UI elements
- `capture/instructions.md` - critical constraints (if exists)

---

## Clarify Intent

If user prompt is ambiguous or could benefit from clarification, use AskUserQuestion to understand their intent before planning. Probe what they actually mean - don't offer prescriptive options.

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

## Spawn Proposal Agents (Two-Stage)

### Stage 1: Verification

Before reading capture files, orchestrator extracts their contents to inject into prompts.

Launch verification agents in parallel:

```
Task(
  subagent_type="general-purpose",
  description="Verify {name} theme",
  prompt="""
Theme verification: {name} ({mode} mode)

Read and follow PROPOSE_{mode}.md. Output ONLY a verification block - no HTML yet.

Assignment:
- Theme name: {name}
- Mode: {mode}
- Constraints: tmp/makeover/constraints.json

AVAILABLE IMAGES:
{images_json_contents}

APP UI ELEMENTS:
{ui_elements_json_contents}

{instructions_block}
"""
)
```

**Template variables:**
- `{images_json_contents}` - Full contents of `capture/images.json`
- `{ui_elements_json_contents}` - Full contents of `capture/ui-elements.json`
- `{instructions_block}` - Empty if no `capture/instructions.md`, otherwise:
  ```
  CRITICAL CONSTRAINTS (from instructions.md):
  {actual contents}
  ```

### Stage 2: Review & Generate

Review each verification response:
- All fields filled? Images selected from available list?
- DNA/mutation matches constraints.json assignment?
- If issues found, provide feedback and re-run verification.

Once verified, resume agents to generate HTML:

```
Task(
  resume="{agent_id}",
  prompt="Generate HTML. Follow TEMPLATE.md. Output: tmp/makeover/themes/{name}.html"
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
