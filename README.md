# flote

A lightweight macOS menu-bar app for quick notes, Markdown, bullet outlines and optional semantic search, streamed note chat and AI tag suggestions. Press a global shortcut to open a fresh floating note. Notes are stored as local Markdown files.

## Current release: flote 3.16

One normal app and update channel now supports both note dictation and optional system-wide dictation. The sandbox is disabled in the signed Release build; macOS privacy permissions still apply. Do not delete the previous app container: existing data continues to live there.

Dictate into notes with local speech recognition, a personal dictionary and optional local AI text cleanup. Cleanup starts off, has its own model and time budget, and preserves recognized text with dictionary corrections when its content check fails or processing times out. Live previews remain raw.

An optional local benchmark compares all three offered Qwen2.5 models on your Mac, with real examples, content-check counts, measured speed and personal quality ratings. Missing test models download one at a time and are removed afterward; installed models are retained. Your dictated text and audio are never used for benchmarks. See [dictionary and cleanup](DICTATION-CLEANUP.md).

Create named Markdown templates in Settings → Notes & Obsidian. Insert them from the slash menu, with automatic date/time values, custom formats and named fields with optional defaults. Direct date/time commands and English/German aliases work within a line after whitespace. List exits and Undo/Redo are more reliable, including after large template insertions.

Open a dictation note with configurable ⌥⌘D; open Settings globally with ⌥⌘, or ⌘, inside flote. Prepare speech models explicitly in Settings → Dictation. Speech recognition requires Apple Silicon; Parakeet Redux additionally requires macOS 15+. Other app features remain available on Intel. The normal public release now runs without App Sandbox and includes optional system-wide Fn dictation. Enable Dictate everywhere in Settings and allow Accessibility/Microphone access through macOS; no second app is needed. Existing notes, settings and model files are retained on update.

See [release notes](RELEASE-NOTES.md), [AI setup](AI-GENERATION.md) and [vault/CLI setup](VAULT-AND-CLI.md). Optional Qwen2.5 3B has research/evaluation licensing restrictions; smaller built-in Qwen models use Apache 2.0. Models are downloaded separately and are not bundled.

## Download

[Download the latest release](https://github.com/NurNichtWilly/flote-releases/releases/latest)

Requires macOS 14 or later. Downloads include Apple Silicon and Intel binaries.

Open the DMG, quit any existing flote instance and move flote.app to Applications. Launch the installed copy. The app is ad-hoc Apple signed and is not notarized; macOS may require Finder → Open or System Settings → Privacy & Security → Open Anyway on first launch.

## Updates

Version 3.7 is the first release using this public update feed. Earlier releases require one manual installation of 3.7. After that, use Check for Updates… in the menu bar or Settings. Automatic checks and installation are opt-in.

Updates and the feed are Ed25519-signed. The stable feed is [appcast.xml](https://github.com/NurNichtWilly/flote-releases/releases/latest/download/appcast.xml). Signature verification does not replace Apple notarization.

## License

flote is proprietary freeware: you may use the official app free of charge for personal and professional purposes under the [Freeware License](LICENSE.txt). Source code is private and is not included in this repository. No open-source license is granted to flote. Future versions may have different terms; the permission to use versions supplied under these terms remains.

Third-party components retain their [upstream licenses and notices](THIRD_PARTY_NOTICES.md). Full texts are in licenses/ and accompany the application. The optional local search model downloads separately. Gemini search is optional and uses your own API key.

## Support

[Report an issue](https://github.com/NurNichtWilly/flote-releases/issues). Do not include private notes, API keys or personal screenshots in public reports.

This repository contains distribution documentation and binary releases only. GitHub-generated source archives contain this documentation, not the application's source code.
