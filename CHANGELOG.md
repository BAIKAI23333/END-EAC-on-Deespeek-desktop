# Changelog

本项目遵循 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.1.0/) 与
[语义化版本](https://semver.org/lang/zh-CN/)。

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
