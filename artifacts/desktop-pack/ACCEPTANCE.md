# 12-item acceptance matrix

Pinned runtime: official DSH Desktop / DSH kernel 0.1.7-rc.2.

| Plugin | Required first-release result |
| --- | --- |
| terminal | Run a command in the current workspace and show output |
| viewport-lock | No abnormal page scroll or composer occlusion |
| eac-locale-compat | Language switching keeps official pages usable |
| compact | Configuration read/write and compaction action work |
| eac-core-bridge | Shows disconnected and stops calls without an extension host |
| easy-setup | Remaining settings persist after restart |
| file-changes | Test file edits are recorded |
| settings-scroll-fix | Settings page scrolls normally |
| unified-market | Query and install use the current official profile |
| plugin-manager | Real state is visible and official pluginManager remains available |
| file-drop-eac | A normal file can be saved and added to a conversation |
| client-file-changes | Changes are shown; one-file restore rejects content conflicts |

Automated checks cover package structure, unique patch entries, manifests, and SHA256. Windows GUI acceptance is still required for the actions above.
