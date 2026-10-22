# flote 3.12

Released 22 October 2026 — build 11. Requires macOS 14 or later; includes Apple Silicon and Intel binaries.

## What's new

- Open **Settings → Tasks** to turn Apple Reminders integration on or off. It starts disabled; connect it explicitly when you want to use your reminders.
- Choose the reminder lists flote may show and use for new tasks. Multiple list choices are saved across restarts. Read-only lists remain viewable.
- Turning the integration off clears reminders from the task window and stops Reminders access in flote. Your reminders and list choices are kept, so you can enable it again later. Local Markdown tasks remain available.
- Fix a crash when loading reminders after granting access: EventKit's background response now crosses safely into the app's Swift 6 UI state.
- Settings stay accessible above floating notes and task windows, including when connecting Reminders.

## Verification and known limitations

453 unit tests and two native UI workflows passed. A live test against the authorized macOS Reminders database verified creation from flote, external rename/completion, completion writeback, selected-list switching, disabling/re-enabling and external deletion. Disposable test lists were removed. Cross-device iCloud propagation was not tested.

Intel binaries are verified structurally; Intel runtime execution is not covered by the Apple Silicon tests. Full update installation/relaunch from a previous public release has not been revalidated for this version.

## Installation and updates

Quit the existing app and move flote.app from flote-3.12-11.dmg into Applications. Existing notes, settings and compatibility identifiers are retained. Users of 3.7 or later can use Check for Updates… in the menu bar or Settings. Older versions require a manual installation to migrate to the public update feed. Enable Reminders in Settings → Tasks and select your lists after updating; macOS may ask you to grant Reminders access to the new build.

The app includes the universal CLI at flote.app/Contents/Helpers/flote. Install it through Settings → Terminal / CLI into a bin folder in your PATH. See VAULT-AND-CLI.md for setup and commands. AI models download separately; Ollama must be installed and running for its providers. Gemini requires your own API key and sends selected content to Google only when you choose its provider.

The app is ad-hoc signed and not notarized. flote is proprietary freeware; LICENSE.txt and THIRD_PARTY_NOTICES.md accompany the package. Source code is not included.
