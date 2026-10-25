# flote 3.13

Released 25 October 2026 — build 12. Requires macOS 14 or later; includes Apple Silicon and Intel binaries. Dictation requires Apple Silicon; Parakeet Redux additionally requires macOS 15 or later.

## What's new

- Dictate into a note with Whisper Base, Whisper Tiny or Parakeet Redux. Open **Dictation**, choose an engine and language, and explicitly download/prepare the model before recording.
- Stop recording to transcribe locally, review the text, then insert it at the current caret or selection. Insertions support normal undo/redo and autosave.
- Whisper Base is the default. Tiny uses less space and memory with lower recognition quality; Parakeet Redux offers multilingual recognition with an approximately 220 MB download.
- Audio stays in memory on your Mac. Only model preparation downloads assets; recording and transcription do not upload audio. Only one note can record at a time, and recordings stop after 55 seconds.
- Discard or close the note to cancel pending recording/transcription. Late results cannot alter another or closed note. Uninserted preview text is discarded when the note closes.

## Verification and known limitations

Unit and snapshot regressions cover editor behavior, persistence, model preparation, cancellation, permission denial and note isolation. Native UI checks cover engine selection and normal editing. Real-model checks transcribe synthetic German and English speech with all three models and reload cached installations. A native microphone check verifies real audio capture.

These checks do not measure accuracy across different speakers, accents, background noise or extended sessions. Transcription starts after recording stops. Parakeet detects language automatically; the selected language supplies a script hint. Model assets are downloaded separately and retained in SDK-managed caches.

Intel binaries are verified structurally; Intel runtime execution is not covered by the Apple Silicon tests. Other app features remain available on Intel, while dictation controls require Apple Silicon. Full update installation/relaunch from a previous public release has not been revalidated for this version.

## Installation and updates

Quit the existing app and move flote.app from flote-3.13-12.dmg into Applications. Existing notes, settings and compatibility identifiers are retained. Users of 3.7 or later can use Check for Updates… in the menu bar or Settings. Older versions require a manual installation to migrate to the public update feed. Allow Microphone access when starting dictation; this build may require a new macOS permission grant.

The app includes the universal CLI at flote.app/Contents/Helpers/flote. Install it through Settings → Terminal / CLI into a bin folder in your PATH. See VAULT-AND-CLI.md for setup and commands. AI models download separately; Ollama must be installed and running for its providers. Gemini requires your own API key and sends selected content to Google only when you choose its provider.

The app is ad-hoc signed and not notarized. flote is proprietary freeware; LICENSE.txt and THIRD_PARTY_NOTICES.md accompany the package. Source code is not included.
