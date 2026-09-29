# Known degradations

Excluded from this delivery (not shipped as members; do not expect or enable them):

- `ui-skin-loader` (skin plugin) — removed from the aggregate. Its skin-manager
  bypass path is deferred to a follow-up delivery; this package ships no skin
  capability and no skin assets.
- `plugin-shield` (plugin protection) — removed from the aggregate. Guard
  snapshots, profile checks, backups and full-tree restore are not part of this
  package's supported acceptance surface.

Remaining known degradations:

- eac-core-bridge reports disconnected and stops calls when no extension host is available.
- file-drop-eac shows an explicit unsupported message for directory drops; normal files remain bounded by size and path authorization.
- client-file-changes only restores a single test-workspace file and refuses to overwrite changed content.
- Native open-in-default-program actions depend on official Desktop support; missing actions are disabled with an explanation.
