# flote

A lightweight macOS menu-bar app for quick notes, Markdown, bullet outlines and optional semantic search, streamed note chat and AI tag suggestions. Press a global shortcut to open a fresh floating note. Notes are stored as local Markdown files.

## Current release: flote 3.14

Dictate directly into a note and see recognized text appear while you speak. The note has one Dictation / Stop button; model preparation and language options live in Settings → Dictation. Automatic multilingual recognition is the default. Whisper Base, Whisper Tiny and Parakeet Redux are available. Audio stays in memory on your Mac.

Open a dictation note with the configurable ⌥⌘D shortcut. Open Settings with ⌥⌘, globally or ⌘, inside flote. Settings support full keyboard navigation: ⌘1–8 selects a category, Control-Tab cycles categories, ⌘0 focuses the sidebar, and Tab / Shift-Tab moves through controls. Space / Return activates controls; arrow keys choose options. Focus a shortcut control and press Space / Return to record; Escape cancels, Delete clears, and Tab / Shift-Tab continues navigation.

Dictation requires Apple Silicon; Parakeet Redux additionally requires macOS 15+. Other app features remain available on Intel. Automated regressions cover live editor insertion, cancellation and keyboard-only Settings navigation. Real microphone and model checks remain opt-in; these checks do not measure recognition accuracy across accents or background noise.

See [release notes](RELEASE-NOTES.md), [AI setup and behavior](AI-GENERATION.md) and [vault/CLI setup](VAULT-AND-CLI.md). The optional Qwen 2.5 3B model has a research/evaluation license; commercial use requires a separate model license. Smaller built-in Qwen models use Apache 2.0.

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
