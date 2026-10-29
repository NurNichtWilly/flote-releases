# flote 3.14

Released 28 October 2026 — build 13. Requires macOS 14 or later; includes Apple Silicon and Intel binaries. Dictation requires Apple Silicon; Parakeet Redux additionally requires macOS 15 or later.

## Live, multilingual dictation

- Recognized text appears directly in your note while you speak. Stop dictation to finish recognition; no preview or manual insertion step is required.
- A single Dictation / Stop button stays in the note. Model selection, preparation and language choices are in Settings → Dictation.
- Automatic (multilingual) is the default. You can still provide an explicit language hint. Whisper Base, Whisper Tiny and Parakeet Redux remain available.
- Use the configurable ⌥⌘D shortcut to open a note and start dictating. Prepare your model once in Settings before the first recording.
- Audio stays in memory on this Mac. Transcription runs locally, recordings stop after 55 seconds, and only explicit model preparation downloads assets.
- Recognition can revise earlier words. Editing the note during recognition stops dictation so your changes are preserved. Text already inserted remains in the note when the session is cancelled or the window closes.

## Keyboard-friendly Settings

- Open Settings from any app with the configurable ⌥⌘, shortcut, or use ⌘, inside flote.
- ⌘1–8 selects a category; Control-Tab / Control-Shift-Tab switches categories; ⌘0 focuses the sidebar.
- Tab / Shift-Tab moves through controls. Space / Return activates menus, buttons and switches. Use arrow keys to choose menu items or an appearance, and Escape to dismiss menus, cancel shortcut recording or close dialogs.
- Focus a shortcut control and press Space / Return to record. Escape cancels, Delete clears, and Tab / Shift-Tab navigates even while recording.
- Shortcut edits retain the current form instead of rebuilding it and losing focus. English interface workflows are the acceptance-test baseline.

## Verification and limitations

Automated regressions cover dictation lifecycle, live editor insertion, Unicode selections, undo/redo, cancellation, note isolation, storage and keyboard-only Settings navigation. Real microphone and real-model integration tests remain opt-in and are not part of the standard automated run. The earlier three-model synthetic speech checks are not a new accuracy evaluation of live recognition.

Recognition latency and quality depend on the model, hardware, speakers and background noise. Intel packages are verified structurally; runtime execution is tested on Apple Silicon. Full installation/relaunch through Sparkle from the previous public release has not been revalidated for this version.

## Installation and updates

Quit the existing app and move flote.app from flote-3.14-13.dmg into Applications. Existing notes, settings and compatibility identifiers are retained. Users of 3.7 or later can use Check for Updates… in the menu bar or Settings. Older versions require a manual installation to migrate to the public update feed. Allow Microphone access when starting dictation if macOS asks.

The app includes the universal CLI at flote.app/Contents/Helpers/flote. Install it through Settings → Advanced into a bin folder in your PATH. See VAULT-AND-CLI.md for setup and commands. AI models download separately; Ollama must be installed and running for its providers. Gemini requires your own API key and sends selected content to Google only when you choose its provider.

The app is ad-hoc signed and not notarized. flote is proprietary freeware; LICENSE.txt and THIRD_PARTY_NOTICES.md accompany the package. Source code is not included.
