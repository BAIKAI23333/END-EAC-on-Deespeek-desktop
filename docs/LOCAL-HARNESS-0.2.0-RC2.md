# 本机 DeepSeek Harness 适配记录

盘点日期：2026-09-29

本机安装位置：

`C:\Users\jackey\AppData\Local\Programs\DeepSeek Harness`

检测到的桌面程序版本：

- ProductVersion：`0.2.0.0`
- FileVersion：`0.2.0-rc.2`
- profile：`desktop`
- profile 目录：`%USERPROFILE%\.dsh\profiles\desktop`
- profile 当前 bundles：`@deepseek-ai/dsh-base`、`@deepseek-ai/dsh-web-app`
- 运行时 Node：`24.18.1`
- 运行时 pnpm：`11.7.0`

## 与旧交付的差异

仓库原交付锁定 `0.1.7-rc.2`，不能把旧 tgz 直接视为
`0.2.0-rc.2` 兼容包。内核服务、客户端协议和插件 peer 约束都可能发生变化；
尤其是过去从 `0.1.5-rc.2` 升到 `0.1.7-rc.2` 时，`settingsScope` 已被
`configForms`/`settingsSchema` 替代，说明仅修改版本字符串是不够的。

本仓库只包含交付文档和校验材料，不包含 12 个 EAC 插件源码，也不包含可重打的
desktop pack tgz。因此本次仓库变更只能完成目标版本和本机 profile 的交付对齐；
真正的插件适配必须在插件上游仓库中用 `0.2.0-rc.2` 的官方内核重新安装依赖、
重打包，再执行 Windows GUI 验收。

## 安装边界

将匹配 `0.2.0-rc.2` 的 pack 交给 Harness Desktop 插件管理器安装。
不要手工复制成员包，也不要向 `cordis.patch.yml` 追加成员的 `insert` 行；
bundle 成员应只通过 bundle 层加载，避免同一服务被注册两次。
