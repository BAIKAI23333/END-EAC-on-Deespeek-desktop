# END-EAC-on-Deespeek-desktop

面向官方 DeepSeek Harness Desktop 的 EAC 插件整合包交付仓。
本仓库不修改官方桌面程序本体，也不提供 EAC 桌面壳。

整合包 `@dsh-eac/desktop-pack` 把 EAC 的 12 个插件聚合为一次可安装的交付，
让本机 DeepSeek Harness Desktop（当前安装版本 `0.2.0-rc.2`）获得终端、人格卡、插件市场、文件变更等能力。

- 插件上游源码：[`DSH-EAC/DSH-Desktop-EAC`](https://github.com/DSH-EAC/DSH-Desktop-EAC)
- 可安装产物：见 [Releases](../../releases)

## 仓库结构

```
├── artifacts/desktop-pack/     整合包源材料
│   ├── ACCEPTANCE.md           12 项验收矩阵
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

1. 到 [Releases](../../releases) 下载与 Harness `0.2.0-rc.2` 匹配的 desktop pack。
2. 校验 SHA-256：

   ```powershell
   Get-FileHash .\dsh-eac-desktop-pack-1.1.0.tgz -Algorithm SHA256
   ```

   应为：

   ```
   9393044BB7D501D17F7DFE8900F4432366EA0560C21FF640A2262681AB5718C6
   ```

3. 在本机 DeepSeek Harness Desktop 的插件管理器内选择该 `.tgz`。
   本机托管 profile 名称是 `desktop`，其实际目录为 `%USERPROFILE%\.dsh\profiles\desktop`。
4. 交给官方管理器完成安装并重启 Desktop。
   **不要**手动复制成员包，**不要**往 profile patch 追加成员 insert 行。
5. 卸载只卸 `@dsh-eac/desktop-pack`；**不要**删 `%USERPROFILE%\.dsh` 下的会话、凭据或工作区文件。

本机适配记录见 [`docs/LOCAL-HARNESS-0.2.0-RC2.md`](docs/LOCAL-HARNESS-0.2.0-RC2.md)。

完整说明见 [`artifacts/desktop-pack/INSTALL.md`](artifacts/desktop-pack/INSTALL.md)。

## 整合包内容

12 个成员插件，由聚合 `cordis.patch.yml` 单层挂载：

| 插件 | 版本 | 插件 | 版本 |
| --- | --- | --- | --- |
| `@dsh-eac/terminal` | 0.1.0 | `@dsh-eac/plugin-manager` | 0.1.0 |
| `dsh-viewport-lock` | 1.0.1 | `dsh-file-drop-eac` | 0.1.2 |
| `dsh-eac-locale-compat` | 1.0.0 | `@dsh-eac/client-file-changes` | 0.1.0 |
| `dsh-compact` | 1.0.0 | `dsh-settings-scroll-fix` | 2.0.2 |
| `dsh-eac-core-bridge` | 1.0.0 | `dsh-unified-market` | 0.4.0 |
| `@dsh-eac/easy-setup` | 0.1.0 | `@dsh-eac/file-changes` | 0.1.0 |

### v1.1.0 移除的成员

以下两个插件**已从整合包剔除**，不再随包分发：

| 插件 | 移除原因 |
| --- | --- |
| `@dsh-eac/ui-skin-loader` | 皮肤能力暂不可用；皮肤管理与 bypass 路径延后交付。本包不含任何皮肤能力与皮肤资产 |
| `dsh-plugin-shield` | 插件保护暂不可用；快照、检查、备份与全树恢复不在本包受支持验收面内 |

v1.0.0 曾在包内保留这两个条目并标注「不得启用」；v1.1.0 选择直接不装，
避免用户看到不可用面板。详见 `artifacts/desktop-pack/DEGRADATIONS.md`。

## ⚠️ 已知降级项

见 [`artifacts/desktop-pack/DEGRADATIONS.md`](artifacts/desktop-pack/DEGRADATIONS.md)。本 beta 交付中：

- `eac-core-bridge` 在无 extension host 时报告 disconnected 并停止调用
- `file-drop-eac` 对目录拖放显示明确的 unsupported 提示
- `client-file-changes` 只恢复单个测试工作区文件，且拒绝覆盖已改动内容
- 原生「用默认程序打开」依赖官方 Desktop 支持，缺失时禁用并给出说明

`ACCEPTANCE.md` 的自动化检查只覆盖包结构、patch 条目唯一性、manifest 与 SHA256；
12 项行为验收仍需在 Windows GUI 上人工执行。

> v1.1.0 已移除 `ui-skin-loader` 与 `plugin-shield`（见上文），故本包**不含换肤能力**。
> 如需换肤，须等皮肤管理与 bypass 路径的后续交付。

## 边界

本仓**不含**：

- 插件源码本体 —— 在 [`DSH-EAC/DSH-Desktop-EAC`](https://github.com/DSH-EAC/DSH-Desktop-EAC)；当前仓库无法单独重打包
- `tauri-shell` 桌面壳与 NSIS/便携安装包 —— 同上，需按 `docs/TEAM-TAKEOVER-2026-09-27.md` §5 重产
- 皮肤包 —— 归属 `DSH-EAC/dsh-ui-skin-loader`
- 启动器源码 —— 归属 `DSH-EAC/dsh-eac-pack-installer`（M8 阶段建仓）

## 许可

MIT
