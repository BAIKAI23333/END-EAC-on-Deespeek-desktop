# Install and uninstall

Target: local DeepSeek Harness Desktop 0.2.0-rc.2.

SHA256: 9393044BB7D501D17F7DFE8900F4432366EA0560C21FF640A2262681AB5718C6

1. In the local DeepSeek Harness Desktop, select the matching `.tgz` in the
   built-in plugin manager. The managed profile is named `desktop`.

2. Let the official manager install the package and restart Desktop. Do not copy member packages or append member insert rows to the profile patch.
3. Uninstall only @dsh-eac/desktop-pack. Do not delete `%USERPROFILE%\.dsh`,
   sessions, credentials, or workspace files.
4. Reinstall is expected to be idempotent. Restart twice and follow ACCEPTANCE.md.
