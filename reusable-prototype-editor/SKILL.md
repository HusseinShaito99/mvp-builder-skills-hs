---
name: reusable-prototype-editor
description: generate or revise complete self-contained html prototypes with an embedded visual feedback editor, stable data-ai metadata, responsive accessible design, and ai-ready markdown feedback export. use when a user asks to create an editable one-file website or product prototype, add the reusable editor to an html mockup, apply exported feedback.md to an existing prototype, or preserve the editor while iterating on prototype source code.
---

# Reusable Prototype Editor

Create and revise browser-openable, one-file HTML prototypes that carry a built-in visual feedback editor. Use the bundled HTML as the canonical implementation reference and preserve the editor across iterations.

## Choose the mode

### Generate

Use this mode when the user provides a product, feature, page, or flow description but no existing prototype to revise.

1. Infer the primary user, goal, content hierarchy, core interaction, and restrained visual direction.
2. Read `references/specification.md` for the required architecture, metadata, accessibility, responsiveness, and editor behavior.
3. Start from `assets/editor-enabled-prototype.html` rather than recreating the editor runtime from memory.
4. Replace the sample product content and product styles while preserving the complete editor runtime.
5. Keep all HTML, CSS, JavaScript, and editor code inline unless the user explicitly requests external dependencies.
6. Return a complete `.html` file, not a partial snippet or outline.

### Revise

Use this mode when the user provides an HTML prototype plus feedback, especially feedback exported as `feedback.md`.

1. Treat the provided HTML as the source of truth.
2. Read the HTML and feedback completely.
3. Read `references/specification.md`, especially evidence priority, target resolution, scope, and vague-feedback translation.
4. Normalize the feedback internally into target, intent, scope, constraints, evidence, and confidence. Do not expose private reasoning.
5. Prefer exact before/after operations and stable identifiers over vague prose.
6. Apply the smallest coherent set of changes.
7. Preserve unrelated content, interactions, responsiveness, existing identifiers, and the full editor runtime.
8. Return one complete revised `.html` file plus a brief applied-changes summary. Mention only items that could not be applied reliably.

### Add the editor to existing HTML

Use this mode when the user provides HTML without the editor and asks to make it editable.

1. Preserve the user's visual design and page behavior.
2. Wrap the product UI in an element carrying `data-ai-canvas` when one is absent.
3. Add stable `data-ai-id`, `data-ai-section`, `data-ai-component`, and `data-ai-label` attributes to important targetable elements.
4. Centralize shared design values as CSS custom properties where practical.
5. Transplant the canonical editor runtime from `assets/editor-enabled-prototype.html` without copying the sample product content.
6. Check that editor UI is isolated from page styles and excluded from selection.
7. Return the complete updated `.html` file.

## Non-negotiable output rules

- Produce a usable prototype, not wireframe commentary.
- Keep one self-contained HTML file that opens directly in a modern browser.
- Preserve or improve semantic structure, labels, keyboard access, focus visibility, and contrast.
- Preserve existing stable identifiers across revisions.
- Make important sections, headings, cards, buttons, inputs, navigation items, and calls to action targetable.
- Keep shared design values in CSS custom properties and use media queries for viewport-specific changes.
- Do not redesign unrelated sections during feedback application.
- Do not claim an edit was applied when target evidence is ambiguous; preserve the original and note the limitation briefly.

## Canonical resources

- `assets/editor-enabled-prototype.html`: canonical working implementation. Copy its editor runtime for generation or editor insertion.
- `references/specification.md`: detailed rules for architecture, feedback normalization, evidence priority, vague feedback, target resolution, scope, and response behavior.

## Final verification

Before returning HTML, verify that:

1. Exactly one `[data-ai-canvas]` product root exists.
2. Important targets have unique, readable, stable `data-ai-id` values.
3. The editor can open, select elements, preview edits, add feedback targets, undo/reset, copy or download Markdown, and download edited HTML.
4. The editor UI cannot select itself and remains isolated from product styles.
5. The page remains usable with the editor panel closed.
6. Desktop and narrow-screen layouts remain functional.
7. The response contains the complete file rather than omitted sections or placeholders.
