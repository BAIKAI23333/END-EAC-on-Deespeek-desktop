# Changelog

本项目遵循 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.1.0/) 与
[语义化版本](https://semver.org/lang/zh-CN/)。

## [1.1.0] - 2026-09-29

### Removed

- 从整合包移除 `@dsh-eac/ui-skin-loader`（皮肤插件）与 `dsh-plugin-shield`（插件保护）。
  两者在 v1.0.0 中即已标注「本 beta 交付暂不可用、不得启用」；v1.1.0 改为直接
  不随包分发，避免用户看到不可用面板。成员数 14 → 12。
  - `cordis.patch.yml` 同步移除对应 insert 行（12 行）
  - `assets`/皮肤能力：本包**不含**换肤能力，且不含任何皮肤资产

### Changed

- 版本号 1.0.0 → 1.1.0（`package.json`、`dsh-plugin.json` 同步）
- `ACCEPTANCE.md`：14 项 → 12 项验收矩阵
- `DEGRADATIONS.md`：新增「Excluded from this delivery」段，明确记录被移除的两个成员
- 产物文件名 `dsh-eac-desktop-pack-1.1.0.tgz`

### Notes

- tgz 作为 Release 资产分发，不进版本库
- 剔除经双向文件清单 diff 验证：95 → 82 文件，恰好减少 13 个（9 + 4），无任何新增
- 依赖关系已核实：两个插件不被其他成员依赖，client 端无跨界引用，市场目录未收录

## [1.0.0] - 2026-09-27

首个整合包交付版本。目标内核 `0.1.7-rc.2`。

### Added

- `@dsh-eac/desktop-pack` 整合包：14 个成员插件由聚合 `cordis.patch.yml` 单层挂载。
  - 桌面能力：`@dsh-eac/terminal`、`dsh-viewport-lock`、`dsh-eac-locale-compat`
  - 会话与设置：`dsh-compact`、`@dsh-eac/easy-setup`、`dsh-settings-scroll-fix`
  - 文件：`@dsh-eac/file-changes`、`@dsh-eac/client-file-changes`、`dsh-file-drop-eac`
  - 生态与治理：`dsh-unified-market`、`@dsh-eac/plugin-manager`、`dsh-plugin-shield`
  - 运行时桥接：`dsh-eac-core-bridge`、`@dsh-eac/ui-skin-loader`
- 交付文档：`INSTALL.md`、`ACCEPTANCE.md`（14 项验收矩阵）、`DEGRADATIONS.md`

### Known limitations

- `ui-skin-loader`（皮肤插件）在本交付中**暂不可用**，不得启用或计入通过。
- `plugin-shield`（插件保护）在本交付中**暂不可用**，其检查、备份与恢复不在受支持的验收面内。
- `eac-core-bridge` 在无 extension host 时报告 disconnected 并停止调用。
- `file-drop-eac` 对目录拖放显示明确的 unsupported 提示。
- `client-file-changes` 只恢复单个测试工作区文件，且拒绝覆盖已改动内容。
- 原生「用默认程序打开」依赖官方 Desktop 支持，缺失时禁用并给出说明。

详见 `artifacts/desktop-pack/DEGRADATIONS.md`。

### Notes

- 整合包 tgz 作为 Release 资产分发，不进版本库（见 `.gitignore`）。
- `ACCEPTANCE.md` 的自动化检查仅覆盖包结构、patch 条目唯一性与 SHA-256；
  14 项行为验收需在 Windows GUI 上人工执行。
