# Install and uninstall

> **历史步骤（本仓已归档）。** 新的安装入口见
> [`DSH-EAC/dsh-eac-pack-installer`](https://github.com/DSH-EAC/dsh-eac-pack-installer)。

Target: official DSH Desktop / DSH kernel **0.1.7-rc.2**.

> ⚠️ 本包钉住内核 `0.1.7-rc.2`（见包内 `package.json` 的 `engines.dsh`）。
> 本仓**没有**面向 `0.2.0-rc.2` 的产物；内核差异与适配前置条件见
> [`docs/LOCAL-HARNESS-0.2.0-RC2.md`](../../docs/LOCAL-HARNESS-0.2.0-RC2.md)。

SHA256: 9393044BB7D501D17F7DFE8900F4432366EA0560C21FF640A2262681AB5718C6

1. In the official DSH Desktop, select this `.tgz` in the built-in plugin
   manager. The managed profile is named `desktop`
   (`%USERPROFILE%\.dsh\profiles\desktop`).
2. Let the official manager install the package and restart Desktop. Do not copy member packages or append member insert rows to the profile patch.
3. Uninstall only @dsh-eac/desktop-pack. Do not delete `%USERPROFILE%\.dsh`,
   sessions, credentials, or workspace files.
4. Reinstall is expected to be idempotent. Restart twice and follow ACCEPTANCE.md.
