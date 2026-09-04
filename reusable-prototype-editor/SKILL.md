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
- Make important sections, headings, cards, buttons, inputs, navigation items, calls to action, and prototype-owned popup content targetable.
- Keep shared design values in CSS custom properties and use media queries for viewport-specific changes.
- Do not redesign unrelated sections during feedback application.
- Do not claim an edit was applied when target evidence is ambiguous; preserve the original and note the limitation briefly.
- Preserve the existing Markdown feedback format. Do not replace it with JSON, a ZIP handoff, or a new schema.
- Keep **Copy Markdown** as the editor's primary action.

## Default speed mode

- Do not run browser automation, interaction testing, screenshot comparison, or a separate verification pass by default. Return the completed prototype promptly.
- Never imply that an unvalidated prototype was tested or verified.
- Clearly tell the user: **“This prototype was not browser-validated to keep the response fast. Ask me to validate it for a higher-confidence result.”**
- When the user explicitly asks to validate, test, verify, QA, or check the prototype, enter Validation mode and perform the full checklist below.

## Canonical resources

- `assets/editor-enabled-prototype.html`: canonical working implementation. Copy its editor runtime for generation or editor insertion.
- `references/specification.md`: detailed rules for architecture, feedback normalization, evidence priority, vague feedback, target resolution, scope, editor behavior, and response behavior.

## Validation mode — only when requested

When the user explicitly requests validation, verify that:

1. Exactly one `[data-ai-canvas]` product root exists.
2. Important targets have unique, readable, stable `data-ai-id` values.
3. The editor opens and its sections collapse and expand.
4. Selection mode minimizes the panel and permits free page selection.
5. Open dialogs, menus, dropdowns, drawers, tooltips, and portal-mounted popup content remain selectable without closing unexpectedly.
6. Selection hierarchy controls move between deeper children and bigger parents.
7. Nested labels can be edited without removing icons, SVGs, badges, or sort indicators.
8. Multi-select and compatible bulk edits work.
9. Duplicate, delete, hide/show, reorder, drag-and-drop, undo, and redo work.
10. Change highlights distinguish edited, added, moved, and feedback-targeted elements.
11. Copy Markdown is the primary action and the exported Markdown keeps the canonical format.
12. The progress-loss warning appears and `beforeunload` activates only after edits or feedback.
13. Downloaded HTML removes transient editor overlays while preserving the editor runtime and applied changes.
14. The editor UI cannot select itself and remains isolated from product styles.
15. Desktop and narrow-screen layouts remain functional.

After requested validation, report what was tested, what passed, and any remaining limitations. Do not use the default “not browser-validated” notice after a successful validation pass.
