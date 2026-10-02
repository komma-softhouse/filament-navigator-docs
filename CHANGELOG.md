# Changelog

All notable changes to `filament-navigator` are documented here. The format
follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this
project adheres to [Semantic Versioning](https://semver.org/).

## [1.6.2](https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.6.2) - 2026-10-02

### Fixed

- First published tag of the 1.6 series; carries everything listed under 1.6.0.

## [v1.6.0](https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.6.0/compare/v1.6.0...v1.6.0) - 2026-10-02

### Added

- Per-panel feature toggles: `->all()`, `->favorites()`, `->recents()`, `->quickLinks()`, `->keyboardShortcuts()`, `->liveBadges()`, `->roleLayouts()`, `->childItems()`, `->separators()`, `->topNavigation()`, `->userMenu()`, `->localizedLabels()`, `->scheduling()`, `->analytics()`, each with its options (`systemLinks()`, `favoritesLimit()`, `recentsLimit()`, `userLinksLimit()`, `badgesInterval()`, `locales()`, `layoutRoles()`).
- Group style in *Appearance*: flat, tree (items hanging from the group with a guide line) and cards.
- Favorites (star on every item, *My favorites* group, own links), recents, quick-access modal with search, `Cmd/Ctrl+K` and number keys.
- Live badges by polling, child items (*Inside*), separators and headings inside groups.
- An arrangement per role with fallback to the base, and the user menu arranged from the settings page.
- Labels per language; *Show from* dates and expiring *New* / *Beta* marks.
- Click analytics per item, user and role; *Hide what nobody uses*.
- Top-navigation rendering of the composed navigation with the panel's `topNavigation()`.
- `NavigationChanged` and `ItemsMoved` events; `resolveLabelUsing()` and `mutateNavigationUsing()` hooks; `navigator:install`; a JSON schema of the export (`vendor:publish --tag=filament-navigator-schema`).
- Migrations `update_navigator_settings_add_group_style`, `create_navigator_user_tables` and `update_navigator_tables_add_children_labels_and_schedule` (all additive).

### Changed

- The export carries group style, group and item labels per language, child items, scheduling and separators/headings.

## [1.6.0](https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.6.0) - 2026-10-02

### Added

- Per-panel feature toggles: `->all()`, `->favorites()`, `->recents()`, `->quickLinks()`, `->keyboardShortcuts()`, `->liveBadges()`, `->roleLayouts()`, `->childItems()`, `->separators()`, `->topNavigation()`, `->userMenu()`, `->localizedLabels()`, `->scheduling()`, `->analytics()`, each with its options (`systemLinks()`, `favoritesLimit()`, `recentsLimit()`, `userLinksLimit()`, `badgesInterval()`, `locales()`, `layoutRoles()`).
- Group style in *Appearance*: flat, tree (items hanging from the group with a guide line) and cards.
- Favorites (star on every item, *My favorites* group, own links), recents, quick-access modal with search, `Cmd/Ctrl+K` and number keys.
- Live badges by polling, child items (*Inside*), separators and headings inside groups.
- An arrangement per role with fallback to the base, and the user menu arranged from the settings page.
- Labels per language; *Show from* dates and expiring *New* / *Beta* marks.
- Click analytics per item, user and role; *Hide what nobody uses*.
- Top-navigation rendering of the composed navigation with the panel's `topNavigation()`.
- `NavigationChanged` and `ItemsMoved` events; `resolveLabelUsing()` and `mutateNavigationUsing()` hooks; `navigator:install`; a JSON schema of the export (`vendor:publish --tag=filament-navigator-schema`).
- Migrations `update_navigator_settings_add_group_style`, `create_navigator_user_tables` and `update_navigator_tables_add_children_labels_and_schedule` (all additive).

### Changed

- The export carries group style, group and item labels per language, child items, scheduling and separators/headings.

## [v1.5.0](https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.5.0/compare/v1.5.0...v1.5.0) - 2026-10-01

### Added

- Discovery from the panel's classes: every registered page and resource is listed on the settings page whatever the admin's permissions or tenant (same filters as Filament except `canAccess()`); the sidebar keeps every access check.
- Each row shows the group its class declares and its class; rows placed elsewhere are flagged (*Code says: …*), can be filtered (*Off their code group*) and put back in bulk (*Back to its code group*).
- Group aliases (*Also collects*): classes declaring another name (e.g. `System`) land in the group on import, on return and in the sidebar.
- Views: List, Tabs (drop on a tab to move), Compact and By code (one card per declared group with the state of each class, *Back to the code*, *Place the rest*, *Assign alias*); remembered per browser.
- *Discovered* grouped by declared group with *Place the rest*.
- *Sort automatically*: groups and items as the code declares or alphabetically, for the whole panel or one group.
- Migration `update_navigator_tables_add_aliases` (additive).

### Changed

- Unplaced items of a declared group join the configured group with that name or alias instead of showing a second group with the same name.

## [1.5.0](https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.5.0) - 2026-10-02

### Added

- Discovery from the panel's classes: every registered page and resource is listed on the settings page whatever the admin's permissions or tenant (same filters as Filament except `canAccess()`); the sidebar keeps every access check.
- Each row shows the group its class declares and its class; rows placed elsewhere are flagged (*Code says: …*), can be filtered (*Off their code group*) and put back in bulk (*Back to its code group*).
- Group aliases (*Also collects*): classes declaring another name (e.g. `System`) land in the group on import, on return and in the sidebar.
- Views: List, Tabs (drop on a tab to move), Compact and By code (one card per declared group with the state of each class, *Back to the code*, *Place the rest*, *Assign alias*); remembered per browser.
- *Discovered* grouped by declared group with *Place the rest*.
- *Sort automatically*: groups and items as the code declares or alphabetically, for the whole panel or one group.
- Migration `update_navigator_tables_add_aliases` (additive).

### Changed

- Unplaced items of a declared group join the configured group with that name or alias instead of showing a second group with the same name.

## [v1.4.1](https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.4.1/compare/v1.4.1...v1.4.1) - 2026-10-01

### Fixed

- The sidebar quick filter showed no results when the match was in a collapsed group: the collapse leaves the list at height 0 with overflow hidden, and only its display was overridden while filtering.

## [1.4.1](https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.4.1) - 2026-10-02

### Fixed

- The sidebar quick filter showed no results when the match was in a collapsed group: the collapse leaves the list at height 0 with overflow hidden, and only its display was overridden while filtering.

## [v1.4.0](https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.4.0/compare/v1.4.0...v1.4.0) - 2026-10-01

### Security

- `->authorizeSettingsUsing()` is required: without it the settings page is not registered and a warning is logged. The rule is checked when the page opens and on every request. **Upgrading:** add the rule to every panel that calls `->settingsPage()`.

### Added

- `->managesPanels([...])`: tabs to arrange other panels from one settings page, each with its own items and arrangement; panels outside the list, without the plugin or sent by hand are rejected with 403.
- `->connection()` and `->tenantOverrides()`: one global arrangement on a base connection, optionally personalised by each tenant in its own database with fallback to the global one; *Start from the global navigation* and *Back to the global navigation* inside a tenant.
- Versioned cache: every write bumps the panel version, so changes reach every context (tenant cache prefixes included) on the next request.
- *No group · top*: rows at the very top of the sidebar without a heading.
- Origin of each row (`App` or the vendor namespace of its package), also searchable.
- `navigator:schema` to create or update the navigator tables on any connection (e.g. tenant databases).
- Migration `update_navigator_tables_add_pinned_and_version` (additive).

### Fixed

- *Import current navigation* created empty duplicate groups when an existing group had another key; groups are now matched by key or label and only created when they receive items.
- Items of the native group without a label ended at the bottom; they now go to the top.

## [1.4.0](https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.4.0) - 2026-10-01

### Security

- `->authorizeSettingsUsing()` is required: without it the settings page is not registered and a warning is logged. The rule is checked when the page opens and on every request. **Upgrading:** add the rule to every panel that calls `->settingsPage()`.

### Added

- `->managesPanels([...])`: tabs to arrange other panels from one settings page, each with its own items and arrangement; panels outside the list, without the plugin or sent by hand are rejected with 403.
- `->connection()` and `->tenantOverrides()`: one global arrangement on a base connection, optionally personalised by each tenant in its own database with fallback to the global one; *Start from the global navigation* and *Back to the global navigation* inside a tenant.
- Versioned cache: every write bumps the panel version, so changes reach every context (tenant cache prefixes included) on the next request.
- *No group · top*: rows at the very top of the sidebar without a heading.
- Origin of each row (`App` or the vendor namespace of its package), also searchable.
- `navigator:schema` to create or update the navigator tables on any connection (e.g. tenant databases).
- Migration `update_navigator_tables_add_pinned_and_version` (additive).

### Fixed

- *Import current navigation* created empty duplicate groups when an existing group had another key; groups are now matched by key or label and only created when they receive items.
- Items of the native group without a label ended at the bottom; they now go to the top.

## [v1.3.2](https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.3.2/compare/v1.3.2...v1.3.2) - 2026-10-01

### Fixed

- Moving an item between lists on the settings page (out of *Unsorted* or from one group to another) was not saved and the item returned to its origin: the page collected the lists from the closest Alpine component, which is the group card, instead of the whole board.

## [1.3.2](https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.3.2) - 2026-10-01

### Fixed

- Moving an item between lists on the settings page (out of *Unsorted* or from one group to another) was not saved and the item returned to its origin: the page collected the lists from the closest Alpine component, which is the group card, instead of the whole board.

## [v1.3.1](https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.3.1/compare/v1.3.1...v1.3.1) - 2026-10-01

### Fixed

- `src/Models/NavigatorSetting.php` shipped with the settings page class instead of the settings model, which stopped the plugin from loading with a "Cannot redeclare class" error.
- The settings page shipped in its previous version, so the edit modals did not offer or save *Symbol only*.

## [1.3.1](https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.3.1) - 2026-10-01

### Fixed

- `src/Models/NavigatorSetting.php` shipped with the settings page class instead of the settings model, which stopped the plugin from loading with a "Cannot redeclare class" error.
- The settings page shipped in its previous version, so the edit modals did not offer or save *Symbol only*.

## [v1.3.0](https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.3.0/compare/v1.3.0...v1.3.0) - 2026-10-01

### Added

- *Symbol only* for groups and items whose symbol is an icon, SVG or image: the sidebar shows just the symbol (images up to four times as wide as tall) and keeps the name as tooltip, for screen readers and for the quick filter. Ignored whenever the row has a text marker or its symbol does not resolve, so a row never renders empty.
- Migration `update_navigator_tables_add_symbol_only` (additive); until it runs the panel works as before and the toggle is not offered.
- `hide_label` travels in the JSON export.

### Fixed

- Wide images were squeezed in the symbol preview of the edit modals.

## [1.3.0](https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.3.0) - 2026-10-01

### Added

- *Symbol only* for groups and items whose symbol is an icon, SVG or image: the sidebar shows just the symbol (images up to four times as wide as tall) and keeps the name as tooltip, for screen readers and for the quick filter. Ignored whenever the row has a text marker or its symbol does not resolve, so a row never renders empty.
- Migration `update_navigator_tables_add_symbol_only` (additive); until it runs the panel works as before and the toggle is not offered.
- `hide_label` travels in the JSON export.

### Fixed

- Wide images were squeezed in the symbol preview of the edit modals.

## [v1.2.2](https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.2.2/compare/v1.2.2...v1.2.2) - 2026-10-01

### Fixed

- Image symbols with a wide aspect ratio (logos) were squeezed into a square and rendered a few pixels tall. Images now take the icon size as height and keep their proportions, up to three times as wide, in the sidebar, the group titles, the rows of the settings page and the strip of collapsed groups.

## [1.2.2](https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.2.2) - 2026-10-01

### Fixed

- Image symbols with a wide aspect ratio (logos) were squeezed into a square and rendered a few pixels tall. Images now take the icon size as height and keep their proportions, up to three times as wide, in the sidebar, the group titles, the rows of the settings page and the strip of collapsed groups.

## [v1.2.0](https://github.com/komma-softhouse/filament-navigator/releases/tag/v1.2.0/compare/v1.2.0...v1.2.0) - 2026-10-01

### What's Changed

* style: add missing newline at end of file by @edeoliv in https://github.com/komma-softhouse/filament-navigator/pull/5
* feat: collapsible groups, drop on titles, search, bulk actions, appearance and JSON transfer (1.2.0) by @edeoliv in https://github.com/komma-softhouse/filament-navigator/pull/6

**Full Changelog**: https://github.com/komma-softhouse/filament-navigator/compare/v1.1.0...v1.2.0

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
