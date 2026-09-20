# claude-design-new

Source-of-truth HTML for the Deha / Jeru component library, consumed by Claude Design (GitHub sync). Dark theme only.

## Layout

- `*.dc.html` — one component per file, kebab-case name = component name in Claude Design. Claude Design exports (`<x-dc>` + `<helmet>`), full-document wrappers kept for local preview.
- `_ds/` — Deha design-system CSS the components link to (`colors_and_type.css`, `styles.css`, `preview/`). Every file links `_ds/...` relative to the repo root.
- `support.js`, `image-slot.js`, `_ds/_ds_bundle.js` — Claude Design runtime internals, referenced but intentionally not shipped. Claude Design resolves them itself; local preview works without them.

## Rules for adding a component

Claude Design's own render contract (asked 2026-09-20):

1. Push raw `.html`; it rebuilds each file as a Design Component. No pre-formatting needed.
2. `<style>` / `<script>` belong in `<helmet>`; a `<script>` in the body breaks the streaming render. Behaviour in a separate class per component.
3. Plain CSS, tokens on `:root` (or `_ds/colors_and_type.css`). No Tailwind. No `prefers-color-scheme` block (dark only).
4. States: `data-state="default|hover|pressed|loading|error|empty|disabled"` on elements, or one section per state side by side.
5. No `100vh`/`100vw`; don't style `body`; keep text in markup, not JS (JS-built DOM is not editable).
6. Google Fonts via `<link>` in `<helmet>`, never `@import`.
7. Shared sub-components used 4+ times: `<dc-import name="Button">` referencing a sibling `button.dc.html`.

## History

- 2026-09-20 cleanup: removed 7 `pages__*` files that were byte-for-byte duplicates apart from link paths; renamed all files to kebab-case; unified two design-system link roots into `_ds/`; shipped the DS CSS.

Near-duplicate pairs kept on purpose (different markup, Bora to pick later): `ai-chat-attachments` / `ai-chat-attachment-card`, `ai-chat-inline-citation` / `ai-chat-citation-chip`, `ai-chat-context` / `ai-chat-context-ring`, `password-strength` / `foundations-password-meter`, `save-toggle-button` / `badges-pills-save-toggle(-original)`, `book-a-call-button` / `marketing-onboarding-book-a-call-button`.
