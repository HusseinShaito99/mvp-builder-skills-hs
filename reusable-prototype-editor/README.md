# Reusable AI Prototype Editor

## What this package does

The embedded editor runs locally in the browser. It does not call ChatGPT or any API.

It can select elements, preview direct edits, record exact before/after operations, capture DOM and layout context, add informal notes, and export AI-ready Markdown.

ChatGPT performs the semantic enhancement and final source-code revision after the user uploads:

1. The current HTML.
2. The exported `feedback.md`.
3. The reusable instructions, unless they are already stored in a Project or Skill.

## Workflow

1. Give ChatGPT `AI_PROTOTYPE_EDITOR_INSTRUCTIONS.md`.
2. Describe the product or website.
3. Request one editor-enabled HTML file.
4. Open it in a browser.
5. Open the side panel and select an element.
6. Change text, color, type, spacing, or size and add informal feedback.
7. Add one or more feedback targets.
8. Download `feedback.md`.
9. Upload the current HTML and feedback to ChatGPT.
10. Ask ChatGPT to normalize the feedback internally and return a complete revised HTML file.

## Reuse

The instructions can be:

- Included in a ChatGPT Skill where Skills are available.
- Stored as a file and instruction in a ChatGPT Project.
- Uploaded at the start of a new chat.
- Kept locally and attached with each prototype request.

Keep `data-ai-canvas`, stable `data-ai-*` attributes, centralized CSS variables, and the editor script when replacing the sample product content.
