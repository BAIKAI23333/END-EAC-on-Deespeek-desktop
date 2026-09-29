# Known degradations

- eac-core-bridge reports disconnected and stops calls when no extension host is available.
- file-drop-eac shows an explicit unsupported message for directory drops; normal files remain bounded by size and path authorization.
- plugin-shield does not perform service-stopping full-tree restore in this release; checks and backups remain available.
- client-file-changes only restores a single test-workspace file and refuses to overwrite changed content.
- Native open-in-default-program actions depend on official Desktop support; missing actions are disabled with an explanation.
