# flote 3.11

Released 21 October 2026 — build 10. Requires macOS 14 or later; includes Apple Silicon and Intel binaries.

## What's new

- Press **⌥⌘T** or choose **Tasks** in the menu bar to manage your tasks in a minimal floating window. Type a task and press Return to add it, click its circle to complete it, and use the options menu to show completed tasks.
- Local tasks use Markdown checkboxes in your managed notes. Existing checkboxes appear in the task list; new tasks are saved as Markdown notes. A task's context menu opens its source note. Completion updates preserve the rest of the note and refuse to overwrite a newer edit.
- Select **Apple Reminders** from the task source menu and connect it to choose an existing list, add reminders and complete them directly. Read-only lists can be viewed. Reminders access is optional and requested only when connecting; local tasks work without it.
- Task and search windows now share the plain appearance and floating behavior of notes, including dragging, a corner resize grip and remembered window geometry.
- Change the task shortcut under Settings → Shortcuts. The default ⌥⌘T is assigned only when no existing flote shortcut already uses it. Task controls include German translations.

## Verification and known limitations

Task persistence, protection against concurrent note edits, shortcut conflicts and the native task/search keyboard workflows passed automated checks. Live Apple Reminders synchronization after granting macOS access still needs manual verification. Intel binaries are verified structurally; Intel runtime execution is not covered by the Apple Silicon tests. Full update installation/relaunch from a previous public release has not been revalidated for this version.

## Installation and updates

Quit the existing app and move flote.app from flote-3.11-10.dmg into Applications. Existing notes, settings and compatibility identifiers are retained. Users of 3.7 or later can use Check for Updates… in the menu bar or Settings. Older versions require a manual installation to migrate to the public update feed.

The app includes the universal CLI at flote.app/Contents/Helpers/flote. Install it through Settings → Terminal / CLI into a bin folder in your PATH. See VAULT-AND-CLI.md for setup and commands. AI models download separately; Ollama must be installed and running for its providers. Gemini requires your own API key and sends selected content to Google only when you choose its provider.

The app is ad-hoc signed and not notarized. flote is proprietary freeware; LICENSE.txt and THIRD_PARTY_NOTICES.md accompany the package. Source code is not included.
