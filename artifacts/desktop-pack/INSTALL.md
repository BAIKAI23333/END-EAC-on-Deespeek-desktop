# Install and uninstall

Target: official DSH Desktop / kernel 0.1.7-rc.2.

SHA256: 9393044BB7D501D17F7DFE8900F4432366EA0560C21FF640A2262681AB5718C6

1. In the official Electron Desktop, select this file in the built-in plugin
   manager. The managed `desktop` profile is intentionally GUI-only; the
   official CLI rejects direct changes to that profile.

2. Let the official manager install the package and restart Desktop. Do not copy member packages or append member insert rows to the profile patch.
3. Uninstall only @dsh-eac/desktop-pack. Do not delete DSH_HOME, sessions, credentials, or workspace files.
4. Reinstall is expected to be idempotent. Restart twice and follow ACCEPTANCE.md.
