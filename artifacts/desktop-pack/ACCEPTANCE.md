# 12-item acceptance matrix

本矩阵对应 `v1.1.0` 包（**12 插件 / 内核 `0.1.7-rc.2`**）。

> 本仓另有面向 **`0.2.0-rc.2`** 的 `v1.2.0-beta.1`（**7 插件**），其验收记录见
> [PR #1](https://github.com/DSH-EAC/END-EAC-on-Deespeek-desktop/pull/1)。
> 两个内核目标的产物**不可混用**；差异见
> [`docs/LOCAL-HARNESS-0.2.0-RC2.md`](../../docs/LOCAL-HARNESS-0.2.0-RC2.md)。

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
