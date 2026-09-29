# END-EAC-on-Deespeek-desktop

DSH-Desktop-EAC 在官方 DeepSeek Desktop 上的整合包**源码仓**。

整合包 `@dsh-eac/desktop-pack` 把 EAC 的 14 个插件聚合为一次可安装的交付，
让官方 DSH Desktop（内核 `0.1.7-rc.2`）获得终端、人格卡、插件市场、文件变更等能力。

- 上游主仓：[`DSH-EAC/DSH-Desktop-EAC`](https://github.com/DSH-EAC/DSH-Desktop-EAC)
- 可安装产物：见 [Releases](../../releases)

## 仓库结构

```
├── artifacts/desktop-pack/     整合包源材料
│   ├── ACCEPTANCE.md           14 项验收矩阵
│   ├── INSTALL.md              安装/卸载步骤
│   ├── DEGRADATIONS.md         已知降级项
│   └── SHA256SUMS.txt          校验值
├── docs/                       交接与规格文档
│   ├── TEAM-TAKEOVER-2026-09-27.md      团队接手总览：分支地图、资产清单、任务表
│   ├── T4-DELIVERY-2026-09-27.md        T4 桌面交付验收记录
│   ├── STAGE-5-PR-HANDOFF.md            Stage 5 Skin manager bypass：不可变输入凭据
│   └── docs-snapshot/                   上游文档快照
├── reports/                    交付完成报告与验收记录
└── CHANGELOG.md
```

## 安装

整合包 **tgz 作为 Release 资产分发，不进版本库**（见 `.gitignore`）。

1. 到 [Releases](../../releases) 下载 `dsh-eac-desktop-pack-1.0.0.tgz`
2. 校验 SHA-256：

   ```powershell
   Get-FileHash .\dsh-eac-desktop-pack-1.0.0.tgz -Algorithm SHA256
   ```

   应为：

   ```
   7A328030E4BA8472BC5F53E439BD969F8212F6AFFE73F339865CC9C95023D187
   ```

3. 在官方 Electron Desktop 内打开插件管理器，选择该 `.tgz`。
   （托管 `desktop` profile 刻意仅限 GUI；官方 CLI 拒绝对该 profile 直接改动。）
4. 交给官方管理器完成安装并重启 Desktop。
   **不要**手动复制成员包，**不要**往 profile patch 追加成员 insert 行。
5. 卸载只卸 `@dsh-eac/desktop-pack`；**不要**删 `DSH_HOME`、会话、凭据或工作区文件。

完整说明见 [`artifacts/desktop-pack/INSTALL.md`](artifacts/desktop-pack/INSTALL.md)。

## 整合包内容

14 个成员插件，由聚合 `cordis.patch.yml` 单层挂载：

| 插件 | 版本 | 插件 | 版本 |
| --- | --- | --- | --- |
| `@dsh-eac/terminal` | 0.1.0 | `@dsh-eac/plugin-manager` | 0.1.0 |
| `dsh-viewport-lock` | 1.0.1 | `dsh-plugin-shield` | 0.1.0 |
| `dsh-eac-locale-compat` | 1.0.0 | `dsh-file-drop-eac` | 0.1.2 |
| `dsh-compact` | 1.0.0 | `@dsh-eac/client-file-changes` | 0.1.0 |
| `dsh-eac-core-bridge` | 1.0.0 | `@dsh-eac/ui-skin-loader` | 1.1.0 |
| `@dsh-eac/easy-setup` | 0.1.0 | `dsh-settings-scroll-fix` | 2.0.2 |
| `@dsh-eac/file-changes` | 0.1.0 | `dsh-unified-market` | 0.4.0 |

## ⚠️ 已知降级项

见 [`artifacts/desktop-pack/DEGRADATIONS.md`](artifacts/desktop-pack/DEGRADATIONS.md)。本 beta 交付中：

- **皮肤插件（`ui-skin-loader`）暂不可用** —— 不要启用，不要计入通过
- **插件保护（`plugin-shield`）暂不可用** —— 其检查/备份/恢复不在受支持的验收面内
- `eac-core-bridge` 在无 extension host 时报告 disconnected 并停止调用
- `file-drop-eac` 对目录拖放显示明确的 unsupported 提示
- `client-file-changes` 只恢复单个测试工作区文件，且拒绝覆盖已改动内容
- 原生「用默认程序打开」依赖官方 Desktop 支持，缺失时禁用并给出说明

`ACCEPTANCE.md` 的自动化检查只覆盖包结构、patch 条目唯一性、manifest 与 SHA256；
14 项行为验收仍需在 Windows GUI 上人工执行。

## 边界

本仓**不含**：

- 插件源码本体 —— 在 [`DSH-EAC/DSH-Desktop-EAC`](https://github.com/DSH-EAC/DSH-Desktop-EAC)
- `tauri-shell` 桌面壳与 NSIS/便携安装包 —— 同上，需按 `docs/TEAM-TAKEOVER-2026-09-27.md` §5 重产
- 皮肤包 —— 归属 `DSH-EAC/dsh-ui-skin-loader`
- 启动器源码 —— 归属 `DSH-EAC/dsh-eac-pack-installer`（M8 阶段建仓）

## 许可

MIT
