# Changelog

All notable changes to `filament-navigator` are documented here. The format
follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this
project adheres to [Semantic Versioning](https://semver.org/).

## [1.1.0] - 2026-09-19

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

## [1.0.1] - 2026-09-17

### Changed
- CI: `actions/checkout` 4 → 7.

## [1.0.0] - 2026-09-13

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

[1.1.0]: https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.1.0
[1.0.1]: https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.0.1
[1.0.0]: https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.0.0