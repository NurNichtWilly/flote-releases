# flote 3.10

Released 12 October 2026 — build 9. Requires macOS 14 or later; includes Apple Silicon and Intel binaries.

## What's new

- A consistent macOS interface with native Liquid Glass for navigation and compact controls on macOS 26 or later. Image editing, the command menu, search, chat and tag review share the updated design; older macOS versions retain a compatible material appearance.
- Choose System, Light or Dark in Settings → General → Appearance. The preference is saved, updates open windows immediately and also applies to focus mode. Settings use a native sidebar, with German interface localization.
- Chat with your notes using Gemini, Ollama or a model downloaded directly into flote. Answers stream as they are generated; related notes appear early and remain clickable. Optional Obsidian vault sources stay read-only.
- Select local chat models and manage downloads from Chat → Models or Settings. Built-in Qwen 2.5 models are available in 0.5B, 1.5B and 3B sizes; Ollama models remain selectable separately. The optional 3B model is for research/evaluation; commercial use requires its separate model license.
- Generate AI tag suggestions after saving a note, review or edit them, or opt into automatic acceptance. Generation is optional and disabled until you enable it.
- Local semantic search can use Ollama EmbeddingGemma 2 in addition to multilingual E5 Small. Gemini remains an optional cloud provider. Model/provider changes rebuild the derived search index without changing Markdown notes.
- More reliable collection access avoids false missing-note warnings while preserving saved notes and external-edit recovery.
- In-app update notes now render Markdown formatting correctly.

## Installation and updates

Quit the existing app and move flote.app from flote-3.10-9.dmg into Applications. Existing notes, settings and compatibility identifiers are retained. Users of 3.7 or later can use Check for Updates… in the menu bar or Settings. Older versions require a manual installation to migrate to the public update feed.

The app includes the universal CLI at flote.app/Contents/Helpers/flote. Install it through Settings → Terminal / CLI into a bin folder in your PATH. See VAULT-AND-CLI.md for setup and commands. AI models download separately; Ollama must be installed and running for its providers. Gemini requires your own API key and sends selected content to Google only when you choose its provider.

The app is ad-hoc signed and not notarized. flote is proprietary freeware; LICENSE.txt and THIRD_PARTY_NOTICES.md accompany the package. Source code is not included.
