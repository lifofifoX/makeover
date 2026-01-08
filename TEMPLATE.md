# Proposal HTML Template

**Every proposal MUST follow this exact structure with all 5 sections.**

```html
<!--
MAKEOVER_METADATA
theme: {name}
dna: {H#-L#-G#-D#-C#-N# or FREEFORM}
styling_system: vanilla
pages: home, collection, detail
wild_mode: {true if wild}
palette: {palette name}
references: {ref1}, {ref2}
-->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{Theme Name} - Makeover Proposal</title>
  <style>/* Your styles */</style>
</head>
<body>

  <!-- ═══════════════════════════════════════════════════════════
       SECTION 1: THEME HEADER (REQUIRED)
       ═══════════════════════════════════════════════════════════ -->
  <header class="theme-header">
    <h1>{Theme Name}</h1>
    <p class="tagline">{One-line concept}</p>
    <p class="dna">DNA: {code} or Structure: {mutation description}</p>
    <p class="references">Inspired by: {2-3 specific references}</p>
  </header>

  <!-- ═══════════════════════════════════════════════════════════
       SECTION 2: COLOR PALETTE (REQUIRED)
       ═══════════════════════════════════════════════════════════ -->
  <section class="color-palette">
    <h2>Color Palette: {Evocative Name}</h2>
    <p class="color-story">{One sentence explaining mood and origin}</p>
    <div class="swatches">
      <div class="swatch" style="background: hsl(220, 60%, 50%)">
        <span>Primary</span>
        <code>hsl(220, 60%, 50%)</code>
      </div>
      <div class="swatch" style="background: hsl(220, 60%, 30%)">
        <span>Primary Dark</span>
        <code>hsl(220, 60%, 30%)</code>
      </div>
      <div class="swatch" style="background: hsl(45, 90%, 55%)">
        <span>Accent</span>
        <code>hsl(45, 90%, 55%)</code>
      </div>
      <div class="swatch" style="background: hsl(220, 10%, 95%)">
        <span>Background</span>
        <code>hsl(220, 10%, 95%)</code>
      </div>
      <div class="swatch" style="background: hsl(220, 10%, 15%)">
        <span>Text</span>
        <code>hsl(220, 10%, 15%)</code>
      </div>
      <!-- Add more swatches as needed (5-7 total) -->
    </div>
  </section>

  <!-- ═══════════════════════════════════════════════════════════
       SECTION 3: APP CONTENT (REQUIRED)
       ═══════════════════════════════════════════════════════════ -->
  <section class="app-content">
    <h2>App Preview</h2>
    <!--
      Your themed redesign of the captured app pages goes here.
      Use REAL content from tmp/makeover/capture/*.snapshot files.
      Include: navigation, hero/profile, collections, detail view, footer.
    -->
  </section>

  <!-- ═══════════════════════════════════════════════════════════
       SECTION 4: UI ELEMENTS (REQUIRED)
       ═══════════════════════════════════════════════════════════ -->
  <section class="ui-elements">
    <h2>UI Elements</h2>

    <h3>Buttons</h3>
    <div class="button-group">
      <button class="btn-primary">Primary</button>
      <button class="btn-secondary">Secondary</button>
      <button class="btn-ghost">Ghost</button>
      <button class="btn-destructive">Destructive</button>
      <button class="btn-primary" disabled>Disabled</button>
    </div>

    <h3>Inputs</h3>
    <div class="input-group">
      <input type="text" placeholder="Text input">
      <input type="text" placeholder="Focus state" class="focus">
      <input type="text" placeholder="Error state" class="error">
      <select><option>Select option</option></select>
      <label><input type="checkbox"> Checkbox</label>
      <label><input type="radio" name="r"> Radio</label>
      <label class="toggle"><input type="checkbox"><span></span> Toggle</label>
    </div>

    <h3>Cards</h3>
    <div class="card-group">
      <!-- Card matching your C-code with hover state demo -->
      <div class="card">
        <img src="..." alt="...">
        <h4>Card Title</h4>
        <p>Card description</p>
      </div>
    </div>

    <h3>Alerts</h3>
    <div class="alert-group">
      <div class="alert alert-success">Success message</div>
      <div class="alert alert-error">Error message</div>
      <div class="alert alert-warning">Warning message</div>
      <div class="alert alert-info">Info message</div>
    </div>

    <h3>Modal</h3>
    <div class="modal-demo">
      <div class="modal-overlay"></div>
      <div class="modal">
        <div class="modal-header">Modal Title</div>
        <div class="modal-body">Modal content goes here.</div>
        <div class="modal-actions">
          <button class="btn-secondary">Cancel</button>
          <button class="btn-primary">Confirm</button>
        </div>
      </div>
    </div>

    <h3>Loading</h3>
    <div class="loading-group">
      <div class="spinner"></div>
      <!-- or skeleton loaders -->
    </div>

    <h3>Empty State</h3>
    <div class="empty-state">
      <div class="empty-icon">📭</div>
      <p>No items found</p>
      <button class="btn-primary">Add Item</button>
    </div>
  </section>

  <!-- ═══════════════════════════════════════════════════════════
       SECTION 5: MOTION SHOWCASE (REQUIRED if N3+ or has animations)
       ═══════════════════════════════════════════════════════════ -->
  <section class="motion-showcase">
    <h2>Motion & Interactions</h2>
    <p>Hover, click, and interact with elements below to see animations.</p>
    <!--
      Demo your hover effects, transitions, scroll animations here.
      Show button hover states, card lifts, fade-ins, etc.
    -->
  </section>

</body>
</html>
```

## Section Requirements

| Section | Must Include |
|---------|--------------|
| **1. Theme Header** | Name, tagline/concept, DNA or structure, 2-3 references |
| **2. Color Palette** | Palette name, color story, 5-7 swatches with HSL values |
| **3. App Content** | All captured pages with real content |
| **4. UI Elements** | Buttons (5 states), Inputs (6 types + states), Cards, Alerts (4), Modal, Loading, Empty, **+ app-specific elements** |
| **5. Motion** | Interactive demos of hover/transitions/animations |

**Missing any section = invalid proposal.**

## App-Specific UI Elements

Look in the captured snapshots for UI elements unique to this app beyond the standard set. Include these in Section 4 alongside the standard elements.

If unsure what app-specific elements exist, use `AskUserQuestion` to ask the user before generating.
