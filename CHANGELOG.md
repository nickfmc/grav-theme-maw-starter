# Changelog

## v1.5.0 (2026-09-20)
Navigation can now come from a menu instead of the page tree.

- **Menus.** With the [MAW Menus](https://github.com/nickfmc/maw-menus) plugin installed and a menu named `header` built, the primary nav renders that menu: any order, custom and external links, hidden pages, icons, descriptions, and items styled as a button. New `header.menu` theme setting picks which menu to use.
- **Nothing changes without one.** `partials/navigation.html.twig` falls back to `partials/navigation-auto.html.twig` — today's automatic page tree, moved unchanged — whenever no such menu exists, including when the plugin is not installed. The theme registers no-op `maw_menu()` / `maw_menu_exists()` stubs in that case, so templates never error.
- New `partials/menu.html.twig` renders menu nodes into the markup the existing nav CSS expects (bare nested `<ul>`, `.is-active`, `aria-current`). It switches on a node's `kind`, so an item type a future plugin version adds still renders as a link or as text rather than breaking.
- New CSS for menu items only: `.menu-item__text`, `.menu-item__desc`, `.menu-item--button`, `.menu-item--highlight`. Existing nav rules are untouched.
- The header CTA (`header.cta`) is unchanged and still sits outside the nav; a menu item flagged `button` is the in-nav alternative.
- Fix: `bin/maw.php` could not find the Grav root when the theme is a junction or symlink to its own repo (a dev checkout), because it counted directories up from `__DIR__`.

## v1.4.1 (2026-09-15)
- Fix: `brand.container` was emitted through `|e('css')`, which escapes the decimal point — `72.5rem` became `72\2E 5rem`. That invalidated the `.container` width declaration, so every container on the site stretched to full width. The value is now validated as a CSS length (the same way `brand.accent` is validated as a hex colour) and written unescaped; anything that is not a plain length is ignored and the `tokens.css` default applies.

## v1.4.0 (2026-09-15)
- `hero`: new `video` (YouTube/Vimeo URL) and `video_title` fields; in the split layout the video replaces the image.
- Images: cropped images keep their shape in CSS (`.img-crop`: aspect-ratio + object-fit: cover) instead of a server-side crop, so every srcset candidate has the right ratio and sites can set the focal point with `object-position`.
- Spacing: the plain-section gap collapse no longer applies right after a hero.

## v1.3.1 (2026-09-15)
- Fix: `collection` block ignored `limit` (Grav only applies it with pagination); the list is now capped in the template.
- Fix: `show_image: false` / `show_date: false` were ignored on collection cards (Twig `|default` treats false as empty).
- Fix: consecutive plain sections no longer collapse the gap when the first one draws a divider. New `section--divided` class (put it in a block's `class` setting) adds the line and keeps the spacing.

## v1.3.0 (2026-09-15)
- New `team` block: people grid with photo, name, role, bio and profile link.
- New `donate` block: giving band with suggested-amount card linking to a donation page (`?amount=`).
- `hero` (split) and `media-text`: optional image caption card (`image_caption_label`, `image_caption`).
- `media-text`: optional attribution (`attribution_name`, `attribution_role`).
- `ui.caption()` macro; `.media-frame`, `.media-caption` and `.attribution` component styles.

## v1.2.0 (2026-09-15)
- Site layer: `user/site/css/site.css`, `user/site/css/blocks/<type>.css`, `user/site/js/site.js` and `user/site/templates/` overrides, so client sites customise without editing the shared theme.

## v1.1.0 (2026-09-15)
- Per-device visibility: shared `hide_on` setting (`mobile`/`tablet`/`desktop`) with `hide-on-*` utilities and the `maw_visibility` filter.
- Documented breakpoints in `css/tokens.css` (mobile ≤ 640px, tablet 641–960px, desktop ≥ 961px).
- Extracted into its own repository.

## v1.0.0
- Initial block library, tokens, CLI (sync, new-block, lint, normalize, styleguide), inline-editing markers.