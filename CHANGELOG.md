# Changelog

## v1.2.0 (2026-09-15)
- Site layer: `user/site/css/site.css`, `user/site/css/blocks/<type>.css`, `user/site/js/site.js` and `user/site/templates/` overrides, so client sites customise without editing the shared theme.

## v1.1.0 (2026-09-15)
- Per-device visibility: shared `hide_on` setting (`mobile`/`tablet`/`desktop`) with `hide-on-*` utilities and the `maw_visibility` filter.
- Documented breakpoints in `css/tokens.css` (mobile ≤ 640px, tablet 641–960px, desktop ≥ 961px).
- Extracted into its own repository.

## v1.0.0
- Initial block library, tokens, CLI (sync, new-block, lint, normalize, styleguide), inline-editing markers.