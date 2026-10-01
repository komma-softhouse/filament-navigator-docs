# Changelog

All notable changes to `filament-navigator` are documented here. The format
follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this
project adheres to [Semantic Versioning](https://semver.org/).

## [1.2.0](https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.2.0) - 2026-10-01

### Added

- Settings page for long menus: groups fold (native collapsible sections, remembered per browser) and show their first icons while folded; *Collapse all* / *Expand all*; every group folds by itself while a group is dragged and returns to its state on drop.
- Group titles become drop targets while an item is dragged, folded groups included; the item goes to the end of that group.
- Search box on the settings page that filters rows and groups and opens the groups with matches.
- Multiple selection (per row and per group) with a bar to move the selection to a group, hide, show or release it.
- *Appearance* slide-over: item icon size, group icon and marker size (`sm`, `md`, `lg`, `xl`) and sidebar density (`compact`, `normal`, `spacious`) with a live preview of the panel's groups. Stored per panel in the new `navigator_settings` table; defaults through `->iconSize()`, `->groupIconSize()`, `->density()` or the `appearance` config keys.
- *Export JSON* / *Import JSON* (merge or replace) with image symbols embedded in the file.
- Migrations `create_navigator_settings_table` and `ensure_navigator_rich_icon_columns` (both additive).

### Changed

- Larger icons by default in the sidebar (items 1.35rem, groups 1.15rem) and on the settings page.
- The *Unsorted* / *Discovered* column stays in view while the settings page scrolls.
- *Export JSON*, *Import JSON* and *Reset* live under a *More* header action.

### Fixed

- Dropping an item outside a list (a group title, the padding of a card, the empty *Discovered* box) sent it back to where it came from; titles are now targets and empty lists show a real drop area.
- The empty-list hint never appeared, because Blade leaves whitespace inside the list and `:empty` does not match it.
- While filtering the sidebar, groups with no matches kept their spacing and pushed the results far down; they are hidden now and the sidebar scrolls back to the top when filtering starts.
- On a fresh installation the marker column was never created: package migrations run by file name, so `add_markers_and_rich_icons_to_navigator_tables` ran before the tables existed. `ensure_navigator_rich_icon_columns` brings every installation to the same schema.

## [v1.1.0](https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.1.0/compare/v1.1.0...v1.1.0) - 2026-09-19

### What's Changed

* Release 1.1.0: icon name guard, commercial licence and directory README by @edeoliv in https://github.com/komma-softhouse/filament-navigator/pull/4

**Full Changelog**: https://github.com/komma-softhouse/filament-navigator/compare/v1.0.1...v1.1.0

## [1.1.0](https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.1.0) - 2026-09-19

### Added

- Per-group marker (any short text) shown before the label; precedence
  marker → icon → global marker.
- Group and item symbols can be a Blade icon name, pasted SVG (sanitised)
  or an uploaded image (PNG, JPG, WebP, GIF, AVIF, SVG file) rendered at
  icon size.
- Symbol selector with live preview in the create/edit modals;
  `->iconsDisk()` / `->iconsDirectory()` options.
- Migration `add_markers_and_rich_icons_to_navigator_tables` (additive).
- Security policy (`SECURITY.md`).

### Changed

- "How it works" help moved to a slide-over that opens by itself while the
  panel has no configuration; colour accents on the settings page.
- README follows the Filament directory layout: banner hidden on the
  directory (`filament-hidden`), a Screenshots section with one image per
  line, installation through the private Composer repository, and the
  support, security, credits and licence sections.

### Fixed

- An icon name that no icon set of the application provides can no longer
  be saved from the settings page, and a stored one (a typo from before, an
  icon package removed later) is ignored when the sidebar is rendered
  instead of throwing on every page of the panel: the group shows its
  marker and the item the icon its page or resource declares.
- `LICENSE.md` carries the commercial licence the package is sold under;
  the MIT text inherited from the plugin skeleton is gone. `composer.json`
  already declared `proprietary`.

## [1.0.1](https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.0.1) - 2026-09-17

### Changed

- CI: `actions/checkout` 4 → 7.

## [1.0.0](https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.0.0) - 2026-09-13

### Added

- Sidebar replacement rendered from a database-driven configuration per
  panel: groups, order, labels, icons, badges, visibility, roles, custom
  links.
- Optional topbar replacement with brand block and tagline.
- Optional type-to-filter box in the sidebar.
- Settings page with drag and drop between groups, the Unsorted bucket and
  the Discovered list; per-row edit, hide and release actions; import of
  the native navigation; reset.
- `navigator:snapshot` and `navigator:reset` artisan commands.
- Named badge resolvers registered through the plugin.
- Token-driven stylesheet (`--kn-*`) with light and dark defaults.
- Spanish translation.
