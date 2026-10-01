# Filament Navigator

<p align="center" class="filament-hidden">
    <img
        src="art/banner.jpeg"
        alt="Filament Navigator — database-driven sidebar and topbar for Filament v5"
        width="100%"
    >
</p>

Official documentation for Filament Navigator: the navigation of a
[Filament](https://filamentphp.com) 5.x panel, run from the panel itself.
Whoever administers the application rearranges the menu, renames it, adds
links to anything — internal pages, external tools, documentation — and
gives every entry its own symbol: a text marker, any Blade icon, **pasted
SVG or an uploaded PNG, JPG, WebP, GIF or AVIF**, not just the icon set the
developer installed. No code, no deploy, no view override: the change is
live in the sidebar the moment it is saved.

Underneath, the sidebar (and optionally the topbar) is rendered by the
plugin's own Livewire components from a per-panel configuration stored in
the database, so the panel also stops looking like stock Filament.

[![Filament 5.x](https://img.shields.io/badge/Filament-5.x-e89a1a?style=flat-square)](https://filamentphp.com)
[![Laravel 13](https://img.shields.io/badge/Laravel-13-ff2d20?style=flat-square)](https://laravel.com)
[![PHP 8.4+](https://img.shields.io/badge/PHP-8.4%2B-777bb4?style=flat-square)](https://www.php.net)
[![License](https://img.shields.io/badge/license-commercial-17151f?style=flat-square)](https://github.com/komma-softhouse/filament-navigator-docs/blob/main/LICENSE.md)

## What this plugin does

- **A menu edited at runtime, not in code.** Groups, order, labels,
  visibility and role restrictions are rows in the database, arranged on a
  settings page with drag and drop — between groups, out of them, back to
  where the code put them. Every save refreshes the sidebar on the spot.
- **Links to anywhere.** *Add link* puts any URL in the sidebar — a path of
  the application, an external tool, a help centre — with its own label,
  symbol, group, badge, role restriction and "open in a new tab". A
  registered page or resource can also have its URL overridden.
- **Any symbol, not only an icon set.** Every group and item takes a text
  marker (`;`, `→`, `$`, `//`), a Blade icon name from whatever icon
  packages the application has, **pasted SVG markup** or an **uploaded
  image** (PNG, JPG, WebP, GIF, AVIF or an SVG file) — the logo of the tool
  a link opens, a brand's own pictogram, a drawing exported from Figma.
  Chosen in a selector with a live preview of the row.
- **SVG made safe.** Pasted markup is sanitised before it is stored and
  again before it is rendered: scripts, event handlers, foreign objects and
  external references are removed, it is sized by CSS, and it follows the
  text colour (active state included) unless the drawing brings its own
  colours.
- **Built for long menus.** Groups fold on the settings page (a folded
  group shows its first icons), fold all at once, and fold by themselves
  while a group is being dragged, so reordering twenty groups is moving
  twenty compact cards. While an item is dragged every group title turns
  into a drop target, collapsed or not. A search box filters rows and
  groups, and a selection bar moves, hides, shows or releases many rows in
  one go.
- **Sized to taste, with a preview.** An *Appearance* slide-over sets the
  size of item icons, the size of group icons and markers (`sm`, `md`,
  `lg`, `xl`) and the density of the sidebar (`compact`, `normal`,
  `spacious`), with a live preview built from the panel's real groups.
- **Logos instead of names.** *Symbol only* hides the name of a group or
  item whose symbol is an icon, SVG or image — a product logo that already
  says it — while the name stays in the tooltip, for screen readers and for
  the quick filter.
- **Every panel, safely.** The settings page only exists with an
  authorisation rule, can arrange other panels you declare (each with its
  own pages, resources and arrangement), and checks both on the server on
  every action.
- **Multi-tenant ready.** One global arrangement on a central connection,
  optionally personalised by each tenant in its own database, falling back
  to the global one until the tenant changes something.
- **Portable.** *Export JSON* downloads the whole arrangement — groups,
  items, appearance and the uploaded image symbols embedded in the same
  file — and *Import JSON* loads it in another environment or panel,
  merging by key or replacing.
- **Rename and re-icon what the code declares.** Label, symbol, URL and
  badge of a registered page or resource can be overridden from the page;
  an empty field keeps what the class declares, and *Release* gives the
  item back to the code.
- **Live badges.** Named resolvers registered on the plugin; an item is
  given one from a select. Resolved once per request.
- **Replaces the sidebar, and optionally the topbar**, with its own
  Livewire components: brand block with tagline, type-to-filter box,
  monospace group markers. Every render hook of the stock sidebar and
  topbar is honoured in the same position.
- **Nothing disappears.** Items the panel registers but the configuration
  has not placed stay visible under their native group. Rows whose page or
  resource is gone are skipped, not shown broken.
- **Filament decides who sees what.** The plugin rearranges the navigation
  Filament already composed for the current user, so `canAccess()`,
  `shouldRegisterNavigation()` and cluster rules keep working. Role
  restrictions in the plugin are an extra layer on top.
- **Per panel.** One configuration per panel id; the plugin can be
  registered on several panels of the same application.
- **Themeable.** Every colour, size and font is a `--kn-*` custom property
  with a neutral fallback, in light and dark mode.
- **Explains itself.** A *How it works* slide-over on the settings page
  walks through the flow and opens by itself on a panel with no
  configuration yet.

## Screenshots

![Settings page — groups, Unsorted and Discovered, drag and drop between lists](art/01-settings-page.jpeg)

![Symbol selector — marker, icon, SVG or image, with a live preview of the row](art/02-symbol-selector.jpeg)

![Pasted SVG as the symbol of an item](art/03-symbol-svg.jpeg)

![Uploaded image as the symbol of an item — a product logo in the sidebar](art/04-symbol-image.jpeg)

![Adding a custom link — URL, symbol, group and new tab](art/05-add-link.jpeg)

![Sidebar — markers, icons, SVG and image symbols, badges and the active state](art/06-sidebar.jpeg)

![Sidebar in dark mode](art/07-sidebar-dark.jpeg)

![Editing a group — label, symbol, collapsible, visibility and roles](art/08-edit-group.jpeg)

![Editing an item — label, URL, symbol, badge and roles](art/14-edit-item.jpeg)


![Collapsed groups — each one shows its first icons; fold or unfold all from the toolbar](art/15-collapsed-groups.png)

![Dragging an item — every group title becomes a drop target](art/16-drop-on-title.jpeg)

![Search and multiple selection — the bar moves, hides, shows or releases the selection](art/17-bulk-selection.png)

![Appearance — icon sizes and density with a live preview of the panel's groups](art/18-appearance.png)

![Import JSON — merge or replace from a file exported in another environment](art/19-import.png)

![Symbol only — logos as group titles, the name kept in the tooltip](art/20-symbol-only.png)

![Panels — tabs to arrange the navigation of every panel from one page](art/21-panels.png)

![No group · top and the origin of each row](art/22-top-and-origin.png)

![How it works — the help slide-over](art/12-how-it-works.jpeg)

## Requirements

- PHP >= 8.4
- Laravel >= 13.0
- Filament >= 5.7

## Installation

This is a commercial package distributed through
[Anystack](https://anystack.sh) — it is not on public Packagist. Your
license key is what authenticates the download.

**1. Add the private repository** to your project's `composer.json`:

```json
{
    "repositories": [
        {
            "type": "composer",
            "url": "https://filament-navigator.composer.sh"
        }
    ]
}
```

**2. Require the package:**

```bash
composer require komma-softhouse/filament-navigator
```

Composer will prompt for authentication against
`filament-navigator.composer.sh`:

- **Username**: the email address your license is registered to.
- **Password**: your license key. If your license policy requires a
  fingerprint, append it to the key separated by a colon —
  `your-license-key:your-domain.com` — using the fingerprint you entered
  when activating the license.

Answer yes when Composer offers to store the credentials (they go in
`auth.json` — add that file to `.gitignore`). For CI, configure the same
credentials as http-basic auth from your secrets instead:

```bash
composer config http-basic.filament-navigator.composer.sh your@email.com YOUR-LICENSE-KEY
```

**3. Migrate and publish the assets:**

```bash
php artisan migrate
php artisan filament:assets
```

The migrations are loaded from the package; publish them, or the config
file, only if you need to edit them:

```bash
php artisan vendor:publish --tag=filament-navigator-migrations
php artisan vendor:publish --tag=filament-navigator-config
```

**4. Register the plugin** on your panel provider:

```php
use Komma\Navigator\NavigatorPlugin;

public function panel(Panel $panel): Panel
{
    return $panel
        // ...
        ->plugin(
            NavigatorPlugin::make()
                ->topbar()
                ->settingsPage()
                ->quickFilter()
                ->groupMarker(';')
                ->brandTagline('Admin')
                ->badges([
                    'tenants' => fn (): int => Tenant::query()->count(),
                ])
                ->authorizeSettingsUsing(fn (): bool => auth()->user()?->hasRole('super-admin') ?? false),
        );
}
```

`->authorizeSettingsUsing()` is required: without it the settings page is
not registered (a warning is logged) and nobody can open it.

**5. Import the navigation.** Open the settings page
(`/{panel}/navigator`) and press **Import current navigation**, or run:

```bash
php artisan navigator:snapshot admin
```

Until you do, the sidebar shows exactly the tree Filament builds — the
plugin changes the look, not the structure.

## Configuration

The sidebar replacement is always on. Everything else ships disabled.

| Method | Getter | Default | Config key | What it does |
| --- | --- | --- | --- | --- |
| `->topbar(bool $condition = true)` | `hasTopbar()` | `false` | `topbar` | Replaces the panel topbar with the plugin's (brand block with tagline, sidebar controls, global search, notifications, user menu). Top navigation mode is not supported by the replacement topbar. |
| `->settingsPage(bool $condition = true)` | `hasSettingsPage()` | `false` | `settings_page` | Registers the **Navigation** page in the panel (slug `navigator`, group *Settings*). |
| `->quickFilter(bool $condition = true)` | `hasQuickFilter()` | `false` | `quick_filter` | Type-to-filter box at the top of the sidebar; filters the rendered items client-side, `Esc` clears. |
| `->brandTagline(string \| Closure \| null $tagline)` | `getBrandTagline()` | `null` | `brand_tagline` | Short monospace line under the logo, in the sidebar header and in the replacement topbar. |
| `->groupMarker(?string $marker)` | `getGroupMarker()` | `''` | `group_marker` | Monospace character printed before every group label instead of an icon (`;`, `→`, `//`). |
| `->unsortedLabel(?string $label)` | `getUnsortedLabel()` | `'Unsorted'` | `unsorted_label` | Label of the trailing group that holds placed rows without a group. Passed through `__()`. |
| `->badges(array $resolvers)` | `getBadges()` | `[]` | — | Named closures. An item configured with one of these keys shows the returned value as its badge; `null` or `''` hides it. Resolved once per request; a throwing resolver hides the badge. |
| `->authorizeSettingsUsing(?Closure $callback)` | `canManageSettings()` | nobody | — | Who may open the settings page. **Required** for the page to be registered; checked when the page opens and again on every action. In a panel tenants use, make it a rule a tenant cannot satisfy (a global role, not a team-scoped one). |
| `->managesPanels(array \| Closure $panels)` | `getManagedPanels()` | `[]` | — | Ids of other panels this panel's settings page may arrange. Only panels that register the plugin are offered; any other id is rejected with 403, even when sent by hand. |
| `->connection(?string $connection)` | `getConnection()` | `null` | `connection` | Connection of the navigator tables for the whole application. `null` uses the default connection of each request (in a multi-database tenancy, the tenant's). |
| `->tenantOverrides(bool $condition = true)` | `hasTenantOverrides()` | `false` | `tenant_overrides` | With a base `connection`: inside a tenant, its own arrangement in its own database, falling back to the base one. See *Multi-tenancy*. |
| `->iconsDisk(?string $disk)` | `getIconsDisk()` | `'public'` | `icons.disk` | Filesystem disk for image symbols uploaded from the settings page. Must be publicly reachable. |
| `->iconsDirectory(?string $directory)` | `getIconsDirectory()` | `'navigator'` | `icons.directory` | Directory on that disk. |
| `->iconSize(IconScale \| string $size)` | `getDefaultAppearance()` | `'md'` | `appearance.icon_size` | Default size of item icons: `sm`, `md`, `lg`, `xl`. What the *Appearance* slide-over stores for the panel wins over it. |
| `->groupIconSize(IconScale \| string $size)` | `getDefaultAppearance()` | `'md'` | `appearance.group_icon_size` | Default size of group icons and markers: `sm`, `md`, `lg`, `xl`. |
| `->density(Density \| string $density)` | `getDefaultAppearance()` | `'normal'` | `appearance.density` | Default row height and space between groups: `compact`, `normal`, `spacious`. |

Config file (`config/filament-navigator.php`):

| Key | Default | What it does |
| --- | --- | --- |
| `connection` | `null` | Database connection of the navigator tables (models and migration). |
| `tables.groups` / `tables.items` / `tables.settings` | `navigator_groups` / `navigator_items` / `navigator_settings` | Table names. Change before the first migration. |
| `cache_ttl` | `3600` | Seconds the composed configuration of a panel stays cached. Every write flushes it; `0` disables the cache. |
| `unsorted_label`, `topbar`, `settings_page`, `quick_filter`, `brand_tagline`, `group_marker` | see above | Defaults for the fluent options. Environment variables: `FILAMENT_NAVIGATOR_CONNECTION`, `FILAMENT_NAVIGATOR_CACHE_TTL`, `FILAMENT_NAVIGATOR_TOPBAR`, `FILAMENT_NAVIGATOR_SETTINGS_PAGE`, `FILAMENT_NAVIGATOR_QUICK_FILTER`, `FILAMENT_NAVIGATOR_BRAND_TAGLINE`, `FILAMENT_NAVIGATOR_GROUP_MARKER`. |
| `icons.disk` / `icons.directory` | `public` / `navigator` | Where uploaded image symbols are stored. Environment variables: `FILAMENT_NAVIGATOR_ICONS_DISK`, `FILAMENT_NAVIGATOR_ICONS_DIRECTORY`. |
| `appearance.icon_size` / `appearance.group_icon_size` / `appearance.density` | `md` / `md` / `normal` | Defaults for the look of the sidebar until the settings page stores one. |
| `tenant_overrides` | `false` | Default for `->tenantOverrides()`. |

`getAppearance(?string $panelId = null)` returns the resolved look of a panel (stored settings over the defaults) as an `Komma\Navigator\Support\Appearance`.

## The settings page

A **How it works** header action opens a slide-over with the flow and the meaning of every row action; it opens by itself the first time, while the panel has no configuration. Two columns. On the left, the configured groups with their items; on the right, the **Unsorted** bucket and the **Discovered** list (items the panel registers that have no row yet). Everything is drag and drop, between lists included:

- drag a discovered item into a group to place it;
- drag a placed item back to *Discovered* to release it (custom links cannot be released, only deleted);
- drag groups to reorder them.

Header actions: **Import current navigation** (imports every native group and item as rows, keeping existing rows), **New group**, **Add link** (a custom URL, optionally in a new tab), **Appearance** (icon sizes and density with a live preview) and, under **More**, **Export JSON**, **Import JSON** and **Reset** (deletes the panel's configuration; the sidebar returns to what Filament builds).

### Panels

With `->managesPanels(['app', 'dev'])`, tabs at the top of the page switch between this panel and the declared ones. Each panel is arranged from its own navigation — Filament builds it with that panel as the current one — and stored under its own id; nothing is shared or copied between panels. Discovery runs as the signed-in user: items that user cannot see in the other panel are not listed. A panel whose navigation cannot be built from here (for example one that needs a tenant in its URLs) shows a notice and an empty *Discovered* list; what is already stored for it still applies.

### No group · top, origin of each row

- **No group · top** holds rows shown at the very top of the sidebar without a heading — the place for Dashboard. *Import current navigation* puts the items of the native group without a label there. *Unsorted* keeps the rows shown at the end.
- Every row shows its **origin** next to the native group: `App` or the vendor namespace of the package that registers it (`Komma\Verifactu`), read from its key. Two resources with the same label from two plugins are told apart, and the search box filters by origin.

### Long lists

- **Folding.** A group folds from its title or chevron and shows its first icons while folded; *Collapse all* / *Expand all* sit next to the search box. While a group is dragged every group folds by itself and returns to its previous state when it is dropped. The folded state is remembered per browser.
- **Drop on a title.** While an item is dragged, the title of every group becomes a drop target, including folded groups: the item goes to the end of that group. The lists themselves are highlighted as targets, and the *Unsorted* / *Discovered* column stays in view while the page scrolls.
- **Search.** Filters rows and groups by label (a group whose name matches shows all its rows) and opens the groups with matches; `Esc` clears it. Dragging is paused while a search is active.
- **Selection.** A box on every placed row and one per group (selects all its visible rows). The bar at the bottom moves the selection to a group — appended at the end, in the order the page shows them —, hides, shows or releases it (custom links are never released in bulk).

### Appearance

Stored per panel in the `navigator_settings` table and written on the sidebar as `data-kn-icon`, `data-kn-group-icon` and `data-kn-density`, which the stylesheet maps to `--kn-item-icon-size`, `--kn-group-icon-size`, `--kn-marker-size`, `--kn-item-height`, `--kn-group-gap` and `--kn-items-gap`.

| Key | Item icons | Group icons | Group markers |
| --- | --- | --- | --- |
| `sm` | 1.1rem | 0.95rem | 0.85rem |
| `md` | 1.35rem | 1.15rem | 1rem |
| `lg` | 1.6rem | 1.4rem | 1.15rem |
| `xl` | 1.9rem | 1.7rem | 1.3rem |

| Density | Row height | Space between groups |
| --- | --- | --- |
| `compact` | 2rem | 0.7rem |
| `normal` | 2.35rem | 1.1rem |
| `spacious` | 2.8rem | 1.5rem |

### Export and import

*Export JSON* downloads a `komma-filament-navigator` document (format version 1): groups with their items in order, the *Unsorted* rows, the appearance and every uploaded image symbol embedded as base64. *Import JSON* reads it into the current panel:

- **Merge** updates groups and items that share a key and adds the rest;
- **Replace** deletes the panel's arrangement first.

On import, SVG is sanitised again, icon names the application does not have are dropped, image files are only written inside the icons directory with an image extension and up to 512 KB, and custom links without label or URL are skipped. Items whose page or resource the target panel does not register are kept as rows and shown as *Not registered*.

Per group: edit (label, symbol, collapsible, collapsed by default, visible, roles) and delete (its items move to Unsorted). Per item: hide/show, edit (label, symbol, URL, badge, roles, new tab, visible — empty fields keep what the page or resource declares) and release/delete.

### Custom links

**Add link** creates a navigation item that no page or resource declares.
It takes a label, a URL — a path of the application (`/admin/reports`) or a
full address (`https://status.example.com`) —, a symbol, the group it goes
in (or *Unsorted*) and whether it opens in a new tab. From then on it is a
row like any other: drag it, edit it, give it a badge, restrict it to
roles, hide it. It is highlighted as active while the current URL is its
own. A custom link cannot be released, because there is no code to give it
back to; it is deleted.

A registered page or resource accepts a URL too: filled in, the item keeps
its place, access rules and active state and points somewhere else.

### Symbols: markers, icons, SVG, images

Every group and item — custom links included — has a **Symbol**, picked in its create or edit modal with a live preview of how the row will look. An icon name the application does not have is flagged in the preview and cannot be saved; one that stops existing later (an icon package removed) is ignored at render time, so a row never breaks the panel:

| Choice | Groups | Items | Stored as |
| --- | --- | --- | --- |
| Default | the plugin's `groupMarker()` (or the native icon if the group has one) | what the page or resource declares | `NULL` |
| Marker | any short text up to 16 characters (`;`, `→`, `$`, `//`), monospace, in the accent colour | — | `marker` column |
| Icon | a Blade icon name available in the app (`heroicon-o-home`, `phosphor-…`) | same | `icon` column |
| SVG | pasted markup, sanitised (scripts, event handlers, foreign objects and external references removed; sized by CSS; `fill="currentColor"` unless the drawing brings its own colours) | same | `icon` column, `<svg…` |
| Image | PNG, JPG, WebP, GIF, AVIF or an SVG file up to 512 KB, uploaded to the icons disk and rendered as `<img>` at icon size | same | `icon` column, path on the disk |

Rendering precedence for a group: its marker → its icon → the plugin's global marker.

**Symbol only.** Groups and items whose symbol is an icon, SVG or image (or, for a registered item, the icon its class declares) have a *Symbol only* toggle. The sidebar then shows just the symbol — an image may be up to four times as wide as it is tall — and keeps the name as the tooltip, for screen readers and for the quick filter. The flag is ignored, and the name shown, whenever the row has a text marker or its symbol does not resolve, so a row never renders empty. On the settings page the name stays visible with a *Symbol only* badge. Stored in the `hide_label` column, added by the migration `update_navigator_tables_add_symbol_only`; until it runs the toggle is not offered.

Images keep their own colours in light and dark mode and do not react to the active state — good for product logos, SVG is better for menu icons. Uploads go to `->iconsDisk('public')` / `->iconsDirectory('navigator')` (config `icons.disk` / `icons.directory`); the disk must be publicly reachable.

Only items the current user can access are listed, because discovery reads the navigation Filament composed for that user: arrange the panel with an account that sees everything.

Roles are stored as an array of names and checked with `hasAnyRole()` on the panel's user model when that method exists (spatie/laravel-permission). Without it, role restrictions are ignored.

## How the composition works

1. `$panel->getNavigation()` — Filament's own tree for the current user.
2. Rows in *No group · top* → a group without a label, first.
3. Configured groups, in their order, with the rows placed in them. Rows whose key is not registered any more are skipped.
4. Rows without a group → the *Unsorted* group.
5. Registered items without a row → appended under their native group label, in native order; those of the native group without a label join the top group.

*Import current navigation* matches a native group to an existing one by key or by label (case-insensitive) and only creates a group when one of its items has no row yet, so importing again never adds empty duplicates.

## Multi-tenancy

Where the arrangement lives is decided by `->connection()` and `->tenantOverrides()`:

| Setup | Who sees what |
| --- | --- |
| `->connection('central')` | One arrangement per panel on the central connection, the same for every tenant. |
| no connection | Each request uses its default connection; in a multi-database tenancy every tenant has its own arrangement and none sees the central one. |
| `->connection('central')->tenantOverrides()` | The central arrangement is the global one. Inside a tenant (the default connection is another one) the tenant sees the global arrangement until it changes something; from then on it has its own, in its own database. *Back to the global navigation* deletes it; *Start from the global navigation* copies the global one as the starting point. |

Reads are cached per connection, database and panel under a key that carries the panel's configuration version, which every write increments, so a change is seen on the next request in every context — tenants with their own cache prefix included.

Tenant databases are not reached by `php artisan migrate`. Create or update the navigator tables in them with `navigator:schema`, which runs every package migration against the connection of the context and can be run again safely. With stancl/tenancy:

```bash
php artisan tinker --execute="\App\Models\Tenant::all()->each(fn (\$tenant) => \$tenant->run(fn () => \Illuminate\Support\Facades\Artisan::call('navigator:schema')));"
```

A tenant database without the navigator tables simply reads the global arrangement.

With no rows at all for the panel the native tree is returned untouched, so installing the plugin changes the look but not the structure until you arrange it.

Item keys are what Filament assigns: the resource or page class for discovered items, the label for hand-made `NavigationItem` instances, `custom:{slug}-{random}` for links created from the page. Renaming a class orphans its row (it is skipped, never shown broken); release it from the page and place the item again.

## Artisan commands

```bash
php artisan navigator:snapshot {panel} [--fresh]   # import the native navigation (--fresh deletes the current rows first)
php artisan navigator:reset {panel} [--force]      # delete the configuration of a panel
php artisan navigator:schema [--connection=]       # create or update the navigator tables on a connection (e.g. a tenant database)
```

The snapshot command runs without an authenticated user: pages and resources that gate navigation on the user register nothing there. Use the page action when that matters.

## Theming

The stylesheet reads these custom properties (defaults shown for light mode; `.dark` redefines the colours). Override them in the panel theme:

```css
:root {
    --kn-bg: #ffffff;
    --kn-bg-elevated: color-mix(in srgb, var(--gray-50) 70%, #ffffff);
    --kn-fg: var(--gray-700);
    --kn-fg-strong: var(--gray-950);
    --kn-fg-muted: var(--gray-500);
    --kn-line: color-mix(in srgb, var(--gray-950) 8%, transparent);
    --kn-accent: var(--primary-600);
    --kn-accent-soft: color-mix(in srgb, var(--primary-500) 10%, transparent);
    --kn-hover: color-mix(in srgb, var(--gray-950) 5%, transparent);
    --kn-active-bg: color-mix(in srgb, var(--primary-500) 12%, transparent);
    --kn-active-fg: var(--gray-950);
    --kn-icon: var(--gray-400);
    --kn-icon-active: var(--primary-600);
    --kn-badge-bg: color-mix(in srgb, var(--primary-500) 16%, transparent);
    --kn-badge-fg: var(--primary-700);

    --kn-font: var(--font-family);
    --kn-mono: var(--mono-font-family);
    --kn-radius: 0.55rem;
    --kn-item-height: 2.35rem;
    --kn-group-gap: 1.1rem;
    --kn-label-size: 0.875rem;
    --kn-group-size: 0.66rem;
    --kn-group-tracking: 0.14em;
    --kn-marker-size: 0.9rem;
    --kn-pad-x: 0.9rem;
    --kn-items-gap: 0.1rem;
    --kn-item-icon-size: 1.35rem;
    --kn-group-icon-size: 1.15rem;
}
```

The *Appearance* settings redefine the size and density tokens through `[data-kn-icon]`, `[data-kn-group-icon]` and `[data-kn-density]` on the sidebar, so a theme that sets them on `:root` only changes the defaults.

Class hooks, for anything the tokens do not cover: `.kn-sidebar`, `.kn-header`, `.kn-brand`, `.kn-brand-tagline`, `.kn-filter`, `.kn-nav`, `.kn-group`, `.kn-group-head`, `.kn-group-marker`, `.kn-group-label`, `.kn-item`, `.kn-item-link`, `.kn-item-icon`, `.kn-item-label`, `.kn-item-badge-ctn`, `.kn-footer`, `.kn-topbar`, `.kn-topbar-brand`, `.kn-topbar-end`. Active states: `.kn-item-active`, `.kn-item-parent-active`, `.kn-group-active`, `.kn-collapsed`.

All render hooks of the stock sidebar and topbar (`SIDEBAR_START`, `SIDEBAR_LOGO_BEFORE/AFTER`, `SIDEBAR_NAV_START/END`, `SIDEBAR_FOOTER`, `TOPBAR_START/END`, `TOPBAR_LOGO_BEFORE/AFTER`, `GLOBAL_SEARCH_BEFORE/AFTER`) are honoured in the same positions.

## Dark mode and translations

Every surface the plugin renders — sidebar, topbar, settings page and the
help slide-over — follows Filament's own light/dark toggle with no
configuration; `.dark` redefines the `--kn-*` colour tokens.

Strings are English literals wrapped in `__()`; a Spanish translation
ships in `resources/lang/es.json`, and the keys resolve against your own
application's `lang/{locale}.json` too. Publish to add a language:

```bash
php artisan vendor:publish --tag=filament-navigator-translations
```

## Testing

```bash
composer test
```

## Changelog

Please see [CHANGELOG](https://github.com/komma-softhouse/filament-navigator-docs/blob/main/CHANGELOG.md) for more information on
what has changed recently.

## Support and community

The plugin's source is private. Everything public lives in the docs
repository:

- **[Documentation](https://github.com/komma-softhouse/filament-navigator-docs)** — this README.
- **[Issues](https://github.com/komma-softhouse/filament-navigator-docs/issues)** — bugs and feature requests.
- **[Discussions](https://github.com/komma-softhouse/filament-navigator-docs/discussions)** — questions, integration help, show and tell.

## Security Vulnerabilities

Never in a public issue or discussion. Please review
[our security policy](https://github.com/komma-softhouse/filament-navigator-docs/blob/main/SECURITY.md) — a private advisory on
the docs repository, or **security@kommasofthouse.com**.

## Credits

- [Elias Olivtradet](https://github.com/edeoliv)
- [Komma SoftHouse](https://github.com/komma-softhouse)

## License

This is commercial software. Please see [License File](https://github.com/komma-softhouse/filament-navigator-docs/blob/main/LICENSE.md)
for the full terms.
