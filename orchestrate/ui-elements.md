# UI Elements Discovery

**Skip if:** `tmp/makeover/capture/ui-elements.json` exists
**Ask if:** Always confirm detected elements with user
**Output:** `tmp/makeover/capture/ui-elements.json`

---

## Auto-Detection

Scan captured `.snapshot` files for UI elements beyond the standard set (buttons, inputs, cards, alerts, modal, loading, empty state).

---

## User Confirmation

```
"I detected these UI elements in your app:

[list detected by category]

Are there any custom components I should include in theme proposals?"

Options: [These are correct] [Add more...]
```

---

## Output

Write to `tmp/makeover/capture/ui-elements.json`:
```json
{
  "detected": [...],
  "user_added": [...],
  "priority": [...]
}
```

The `priority` field indicates which elements should be prominently featured in Section 4 of proposals.
