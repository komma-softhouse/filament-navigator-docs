# Security Policy

## Supported versions

| Version | Supported |
| --- | --- |
| 1.x | ✅ |

Security fixes land on the latest 1.x release. Older tags are not patched.

## Reporting a vulnerability

Report privately, never in a public issue: open a
[security advisory](https://github.com/komma-softhouse/filament-navigator-docs/security/advisories/new)
on the docs repository, or write to **security@kommasofthouse.com**.

Please include the affected version, the steps to reproduce it, and what an
attacker could obtain or alter. A proof of concept helps, but a clear
description is enough.

What to expect:

- Acknowledgement within 3 working days.
- An assessment, with severity and a fix window, within 10 working days.
- Credit in the release notes when the fix ships, unless you prefer not to
  be named.

Please give us a reasonable window to release a fix before disclosing
publicly.

## Scope

This package stores the navigation of a Filament panel in the database and
renders the sidebar and topbar from it. Reports of the following are
especially welcome:

- Anything that gets markup past the SVG sanitiser (scripts, event
  handlers, foreign objects, external references) and into the rendered
  sidebar or topbar.
- Injection through any other stored field rendered in the navigation:
  labels, markers, badges, custom link URLs.
- Path traversal or unrestricted file types reachable from the symbol
  image upload.
- Authorisation bypasses: opening or writing through the settings page
  without passing `authorizeSettingsUsing()`, or a navigation item shown
  to a user that Filament or the configured role restrictions would hide.
- One panel reading or altering the configuration of another.

Out of scope: findings that require an already-compromised host or
privileged access to the database, actions performed by a user who is
legitimately allowed to manage the settings page, and denial of service
through resource exhaustion.