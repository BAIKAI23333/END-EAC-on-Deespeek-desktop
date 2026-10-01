# END-EAC-on-Deespeek-desktop

> ## 📦 本仓已归档（Archived）
>
> **本仓定位为历史交付归档，不再接收新功能、新版本或内容更新。**
>
> - 整合包 `@dsh-eac/desktop-pack` 的既有产物保留在 [Releases](../../releases)，供已下载用户与验收追溯使用
> - **新的安装入口见 [`DSH-EAC/dsh-eac-pack-installer`](https://github.com/DSH-EAC/dsh-eac-pack-installer)**（在官方 Desktop 设置页内浏览并分级安装整合包）
> - 整合包来源索引与分发由 [`DSH-EAC/dsh-mojobox`](https://github.com/DSH-EAC/dsh-mojobox) 承担
> - 插件源码本体在 [`DSH-EAC/DSH-Desktop-EAC`](https://github.com/DSH-EAC/DSH-Desktop-EAC)
>
> 归档原因：本仓以「厚包」形式自行聚合内嵌 12 个成员插件；组织内的整合包分发已转向
> 「Mojobox 收录薄清单 + pack-installer 安装」的平台化路线，两条路线入口重复，故本仓停止演进。
> 详见下文「归档说明」。

---

## 交付物一览

| Release | 成员数 | 目标内核 | SHA-256 |
| --- | --- | --- | --- |
| [v1.1.0](../../releases/tag/v1.1.0) | **12** | `0.1.7-rc.2` | `9393044BB7D501D17F7DFE8900F4432366EA0560C21FF640A2262681AB5718C6` |
| [v1.0.0](../../releases/tag/v1.0.0) | 14 | `0.1.7-rc.2` | `7A328030E4BA8472BC5F53E439BD969F8212F6AFFE73F339865CC9C95023D187` |

> ⚠️ **两个 Release 均面向内核 `0.1.7-rc.2`。本仓没有任何面向 `0.2.0-rc.2` 的产物。**
> 内核差异说明见 [`docs/LOCAL-HARNESS-0.2.0-RC2.md`](docs/LOCAL-HARNESS-0.2.0-RC2.md)。

v1.1.0 相对 v1.0.0 剔除了 `@dsh-eac/ui-skin-loader`（皮肤）与 `dsh-plugin-shield`（插件保护），
两者在 v1.0.0 中即标注「暂不可用、不得启用」；**因此 v1.1.0 不含换肤能力**。

---

## 归档说明

### 为什么归档

本仓是一个**厚包**交付仓：自行把 12 个成员插件聚合内嵌进一个 `.tgz`，放到 GitHub Release，
由用户在官方 Desktop 插件管理器里手动选择安装。

组织内另有两条路线：

| 仓库 | 定位 | 与本仓关系 |
| --- | --- | --- |
| [`dsh-eac-pack-installer`](https://github.com/DSH-EAC/dsh-eac-pack-installer) | EAC 整合包**安装器**：在官方设置壳 `settings.section` 内展示 Pack 卡片，按 L1/L2/L3 分级安装 | **安装入口重复** |
| [`dsh-mojobox`](https://github.com/DSH-EAC/dsh-mojobox) | 插件与整合包的**收录、验证、归档与分发目录** | **分发渠道部分重复** |

三者交付的**功能内容不重复**（本仓的 12 插件聚合产物独有），但**安装路径重复**。
平台化路线（Mojobox 收录 + pack-installer 安装）确立后，本仓停止演进。

### 为什么没有移交 Mojobox 收录

按 [`dsh-mojobox` 收录规范](https://github.com/DSH-EAC/dsh-mojobox/blob/main/docs/intake.md)，
其首版只接收 `eac-feature-pack-v1` **薄包**（ZIP，根 `pack.json`，仅引用插件），并明确
「不接收 preset、skill、非空 overrides、**内嵌插件代码**或其他文件」，归档上限 2 MiB。

本仓产物是内嵌 12 个插件代码的**厚包**，与其收录模型相反。且成员中多个 `@dsh-eac/*`
为 EAC 原研插件（`x-eac.maintenance: eac-private`、`autoUpdate: false`），**没有独立发布渠道**，
薄清单无法引用——这正是当初采用厚包内嵌的原因。

因此移交未执行。若将来需要，前置条件是先让成员插件各自具备公开发布源。

### 归档后的边界

- 本仓**只读**：不再接受 PR、Issue 或推送
- Release 资产**保留**，已发出的下载链接继续有效
- `docs/` 内文档为历史交接记录，**内容按当时状态冻结**，不代表当前事实
- 本仓内 `artifacts/desktop-pack/` 仅为源材料（验收/安装/降级说明），**不含 tgz**（tgz 仅作为 Release 资产）

---

## 整合包内容（v1.1.0）

12 个成员插件，由聚合 `cordis.patch.yml` 单层挂载：

| 插件 | 版本 | 插件 | 版本 |
| --- | --- | --- | --- |
| `@dsh-eac/terminal` | 0.1.0 | `@dsh-eac/plugin-manager` | 0.1.0 |
| `dsh-viewport-lock` | 1.0.1 | `dsh-file-drop-eac` | 0.1.2 |
| `dsh-eac-locale-compat` | 1.0.0 | `@dsh-eac/client-file-changes` | 0.1.0 |
| `dsh-compact` | 1.0.0 | `dsh-settings-scroll-fix` | 2.0.2 |
| `dsh-eac-core-bridge` | 1.0.0 | `dsh-unified-market` | 0.4.0 |
| `@dsh-eac/easy-setup` | 0.1.0 | `@dsh-eac/file-changes` | 0.1.0 |

## 安装（历史步骤，仅供追溯）

整合包 **tgz 作为 Release 资产分发，不进版本库**（见 `.gitignore`）。

1. 到 [Releases](../../releases) 下载 `dsh-eac-desktop-pack-1.1.0.tgz`。
2. 校验 SHA-256：

   ```powershell
   Get-FileHash .\dsh-eac-desktop-pack-1.1.0.tgz -Algorithm SHA256
   ```

   应为 `9393044BB7D501D17F7DFE8900F4432366EA0560C21FF640A2262681AB5718C6`。

3. 在官方 DeepSeek Harness Desktop 的插件管理器内选择该 `.tgz`。
   托管 profile 名称为 `desktop`，实际目录 `%USERPROFILE%\.dsh\profiles\desktop`。
4. 交给官方管理器完成安装并重启 Desktop。
   **不要**手动复制成员包，**不要**往 profile patch 追加成员 insert 行。
5. 卸载只卸 `@dsh-eac/desktop-pack`；**不要**删 `%USERPROFILE%\.dsh` 下的会话、凭据或工作区文件。

完整说明见 [`artifacts/desktop-pack/INSTALL.md`](artifacts/desktop-pack/INSTALL.md)。

---

## ⚠️ 已知降级项（v1.1.0）

见 [`artifacts/desktop-pack/DEGRADATIONS.md`](artifacts/desktop-pack/DEGRADATIONS.md)：

- `eac-core-bridge` 在无 extension host 时报告 disconnected 并停止调用
- `file-drop-eac` 对目录拖放显示明确的 unsupported 提示
- `client-file-changes` 只恢复单个测试工作区文件，且拒绝覆盖已改动内容
- 原生「用默认程序打开」依赖官方 Desktop 支持，缺失时禁用并给出说明

`ACCEPTANCE.md` 的自动化检查只覆盖包结构、patch 条目唯一性、manifest 与 SHA256；
12 项行为验收仍需在 Windows GUI 上人工执行。

---

## 仓库结构

```
├── artifacts/desktop-pack/     整合包源材料（不含 tgz）
│   ├── ACCEPTANCE.md           12 项验收矩阵
│   ├── INSTALL.md              安装/卸载步骤
│   ├── DEGRADATIONS.md         已知降级项
│   └── SHA256SUMS.txt          校验值
├── docs/                       历史交接与规格文档（已冻结）
│   ├── TEAM-TAKEOVER-2026-09-27.md      团队接手总览：分支地图、资产清单、任务表
│   ├── T4-DELIVERY-2026-09-27.md        T4 桌面交付验收记录
│   ├── STAGE-5-PR-HANDOFF.md            Stage 5 Skin manager bypass：不可变输入凭据
│   ├── LOCAL-HARNESS-0.2.0-RC2.md       本机 Harness 0.2.0-rc.2 适配盘点
│   └── docs-snapshot/                   上游文档快照
├── reports/                    交付完成报告与验收记录
└── CHANGELOG.md
```

## 边界

本仓**不含**：

- 插件源码本体 —— 在 [`DSH-EAC/DSH-Desktop-EAC`](https://github.com/DSH-EAC/DSH-Desktop-EAC)；本仓无法单独重打包
- `tauri-shell` 桌面壳与 NSIS/便携安装包 —— 同上，需按 `docs/TEAM-TAKEOVER-2026-09-27.md` §5 重产
- 皮肤包 —— 归属 [`DSH-EAC/dsh-ui-skin-loader`](https://github.com/DSH-EAC/dsh-ui-skin-loader)
- 安装器 —— 归属 [`DSH-EAC/dsh-eac-pack-installer`](https://github.com/DSH-EAC/dsh-eac-pack-installer)

## 许可

MIT
