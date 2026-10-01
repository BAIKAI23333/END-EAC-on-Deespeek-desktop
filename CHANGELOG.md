# Changelog

本项目遵循 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.1.0/) 与
[语义化版本](https://semver.org/lang/zh-CN/)。

## [Archived] - 2026-10-01

### Changed

- **本仓归档（Archived）**，不再接收新功能、新版本或内容更新。
  新的安装入口转至 `DSH-EAC/dsh-eac-pack-installer`，整合包来源索引转至 `DSH-EAC/dsh-mojobox`。
- README 重写为归档说明：补充交付物一览、归档原因、未移交 Mojobox 的原因与归档后边界。
- 记录两个并存的**内核目标**产物，明确二者不可混用：
  `v1.2.0-beta.1`（7 插件 / `0.2.0-rc.2`，`zixin947` fork 托管，待迁入）
  与 `v1.1.0`（12 插件 / `0.1.7-rc.2`，本仓）。
  `INSTALL.md` 与 `ACCEPTANCE.md` 由单目标改为双目标表述。
- 更正前一次提交的误判：`0.2.0-rc.2` 并非「文档与产物不一致」，
  而是 [PR #1](https://github.com/DSH-EAC/END-EAC-on-Deespeek-desktop/pull/1)（`zixin947`）的**有意更新**，且配套产物真实存在
  （`5D7062CB444A9CE6ABB2DD7254E494A03D98E09C7E184E3E443A3AC299F87C93`）。
  该提交曾把 `INSTALL.md` / `ACCEPTANCE.md` 的目标内核改回 `0.1.7-rc.2`，
  现已恢复并扩展为双目标说明。

### Notes

- 归档时未向 `dsh-mojobox` 移交收录：其收录规范只接收 `eac-feature-pack-v1` 薄包，
  明确排除内嵌插件代码，且归档上限 2 MiB；本仓产物为内嵌 12 插件的厚包。
  成员中多个 `@dsh-eac/*` 为 EAC 原研私有插件，无独立发布源，薄清单无法引用。
- Release 资产保留（v1.0.0 / v1.1.0），已发出的下载链接继续有效。
- `docs/` 内历史交接文档按当时状态冻结，不代表当前事实。

### TODO

- [ ] `v1.2.0-beta.1` 产物从 `zixin947` fork 迁入本仓 Release
- [ ] 仓库描述更新为归档定位（归档后无法编辑）

## [Unreleased] - 2026-09-29

### Changed

- 交付目标从 `0.1.7-rc.2` 更新为本机 DeepSeek Harness Desktop `0.2.0-rc.2`。
- 安装说明改为使用本机 `desktop` profile（`%USERPROFILE%\.dsh\profiles\desktop`）。
- 增加本机运行时盘点文档；插件源码和匹配 `0.2.0-rc.2` 的 tgz 不在本仓库，行为兼容性仍需在上游源码仓重建并验收。

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
