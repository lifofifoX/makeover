# Proposal HTML Template

**Every proposal MUST follow the structure in `templates/proposal.html` with all 5 sections.**

Read `templates/proposal.html` for the exact HTML structure to use.

## Section Requirements

| Section | Must Include |
|---------|--------------|
| **1. Theme Header** | Name, tagline/concept, DNA or structure, 2-3 references |
| **2. Color Palette** | Palette name, color story, 5-7 swatches with HSL values |
| **3. App Content** | All captured pages with real content |
| **4. UI Elements** | Buttons (5 states), Inputs (6 types + states), Cards, Alerts (4), Modal, Loading, Empty, **+ app-specific elements** |
| **5. Motion** | Interactive demos of hover/transitions/animations |

**Missing any section = invalid proposal.**

---

## Image Usage

Use images from `tmp/makeover/capture/images.json` in your proposals:
- Include the app's logo if captured
- Use content images in Section 3 (App Content) to show theme applied to real visuals
- Reference images via their `src` URLs (the app must be running to view proposals)

---

## App-Specific UI Elements

Read `tmp/makeover/capture/ui-elements.json` for custom components unique to this app. These MUST appear in Section 4 alongside standard elements.
