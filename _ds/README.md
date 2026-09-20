# exports/_ds — tracked design-system CSS

This folder is the **tracked** copy of the shared design-system CSS/JS files
that `exports/*/source.dc.html` link via `_ds/<project-id>/<path>` hrefs. The
project-id segment is flattened away here; sub-paths are preserved.

Source of truth for these bytes is the gitignored mirror at
`apps/web/design-system/claude-design/` (Claude Design DesignSync mirror,
project "Deha Design System (Bora)",
`9684cda3-7f54-4e07-b933-c216065cad53`). Global fixes produced by the frontend
pass (`plans/claude-design-frontend-pass.md`) land here. The push plan
(`plans/claude-design-fix-loop-push.md`) uploads this folder's contents back
up to that Claude Design project. `inline-ds.mjs` reads design-system assets
from here when pointed at this directory instead of the mirror.

File set (20 files):
- colors_and_type.css, styles.css
- preview/_base.css, preview/_darkmode.css, preview/_shared-feedback.css
- preview/done/jsx/_ai-caveat.css, _ai-message-box.css, _animated-list.css,
  _buttons.css, _cards.css, _colors-neutrals.css, _colors-semantic.css,
  _controls.css, _fab.css, _iconography.css, _metric-circle.css,
  _multisteps.css, _pills.css, _spacing-shadows.css, _type-display.css

`_ds_bundle.js` is intentionally absent: it does not exist in the mirror and
`inline-ds.mjs` drops that script tag by design.

Copied from the mirror on 2026-09-11.
