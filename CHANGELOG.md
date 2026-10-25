# Changelog

## 0.6.4 - 2026-10-25

- Expanded the Zotero compatibility ceiling to `99.0.*`, preventing future major-version bumps from disabling the plugin solely because of its version range.
- Retained Zotero 9.0 as the minimum supported version and verified installation on Zotero 10.0.6.
- Replaced the Zotero-major-specific package name with `ice-cream-0.6.4.xpi`.
- Corrected the development manifest to use the public GitHub homepage and update manifest.

## 0.6.3 - 2026-08-25

- Added permanent per-conversation deletion controls.
- Preserved the active conversation when deleting another history entry.
- Automatically loads the newest remaining conversation after deleting the active entry.
- Creates one empty conversation when no saved conversations remain.

See `README.md` for the complete feature and usage documentation.
