# Install and uninstall

> **历史步骤（本仓已归档）。** 新的安装入口见
> [`DSH-EAC/dsh-eac-pack-installer`](https://github.com/DSH-EAC/dsh-eac-pack-installer)。

## Target

本仓有**两个内核目标**的产物，**不可混用**：

| 产物 | 成员数 | 目标内核 | SHA-256 |
| --- | --- | --- | --- |
| `dsh-eac-desktop-pack-1.2.0-beta.1.tgz` | 7 | **`0.2.0-rc.2`** | `5D7062CB444A9CE6ABB2DD7254E494A03D98E09C7E184E3E443A3AC299F87C93` |
| `dsh-eac-desktop-pack-1.1.0.tgz` | 12 | `0.1.7-rc.2` | `9393044BB7D501D17F7DFE8900F4432366EA0560C21FF640A2262681AB5718C6` |

`v1.2.0-beta.1` 由 `zixin947` 在 PR #1 中提出，产物暂托管于其 fork，
待 maintainer review 后迁入本仓 Release。内核差异与适配前置条件见
[`docs/LOCAL-HARNESS-0.2.0-RC2.md`](../../docs/LOCAL-HARNESS-0.2.0-RC2.md)。

## Steps

1. In the official DeepSeek Harness Desktop, select the `.tgz` matching your
   kernel version in the built-in plugin manager. The managed profile is named
   `desktop` (`%USERPROFILE%\.dsh\profiles\desktop`).
2. Let the official manager install the package and restart Desktop. Do not copy member packages or append member insert rows to the profile patch.
3. Uninstall only @dsh-eac/desktop-pack. Do not delete `%USERPROFILE%\.dsh`,
   sessions, credentials, or workspace files.
4. Reinstall is expected to be idempotent. Restart twice and follow ACCEPTANCE.md.
