# flote 3.16

Released 29 October 2026 — build 15. macOS 14 or later; universal Apple Silicon and Intel application. Speech recognition requires Apple Silicon; Parakeet Redux also requires macOS 15 or later.

## One app with optional system-wide dictation

The normal flote release now runs without App Sandbox. **Dictate everywhere** is available in Settings → Dictation in the same app and stable update channel; no separate evaluation app is needed.

Enable system-wide dictation, explicitly prepare a speech model, and allow Accessibility and Microphone access when macOS requests them. Hold Fn to speak and release to insert; double-tap for hands-free recording, press again to finish, and Escape to cancel. A configurable alternative shortcut is available. In macOS Keyboard settings, set the Globe/Fn action to Do Nothing to avoid conflicts with Apple's actions or other voice apps.

## Existing data and settings

The app keeps its existing identity and update feed. On the first direct launch it imports the previous sandbox preferences once, taking current sandbox values over stale historical direct settings and retaining the original bookmark bytes. Existing model/index files and unsaved-note recovery files are reused in place; no note folder or Keychain identifier is renamed or deleted. New installations use normal Application Support. An unreadable existing preferences file produces a recovery message rather than silently opening first-run setup.

Note storage, vault links, CLI installation and folder recovery support both direct access and legacy security-scoped bookmarks. Test preference suites cannot overwrite the production CLI collection configuration. Previous dictionary, optional local cleanup, benchmark and template features are retained.

## Permissions and distribution

macOS privacy protections still apply. Enabling system-wide dictation requires your permission; disabling the feature stops its keyboard monitoring. App Sandbox is a signed build property and cannot be switched on or off inside the running app.

Packages continue to use ad-hoc signatures and are not notarized. macOS may ask you to approve the app or its Accessibility permission again after updating. Developer ID signing is not included in this release. Do not remove the old app container; the updated app continues using existing data there.

The universal offline CLI is included at flote.app/Contents/Helpers/flote; see VAULT-AND-CLI.md. The app is proprietary freeware; LICENSE.txt and THIRD_PARTY_NOTICES.md accompany the distribution. Models download separately. Qwen2.5 3B remains for research/evaluation; its separate license restrictions still apply.

## Verification scope

Automated tests cover preference import, retained bookmarks, file writes/recovery, dictation state, update validation and editor behavior. Synthetic German/English speech checks exercise local recognition. TextEdit/Chrome Fn insertion was previously exercised in the development implementation. Intel execution, every external app/secure-field/fullscreen combination, and a fresh physical Fn recording in this exact release are not claimed as fully validated.
