# flote 3.15

Released 29 October 2026 — build 14. macOS 14 or later; universal Apple Silicon and Intel application. Speech recognition requires Apple Silicon; Parakeet Redux also requires macOS 15 or later.

## Dictionary and optional local AI cleanup

- Add recognized words or phrases and their preferred spellings in Settings → Dictation. Dictionary corrections apply to final text even with AI cleanup disabled. URLs, email addresses, paths and backtick code are protected.
- AI text cleanup is off by default. Enable it separately and choose its own built-in Qwen2.5 0.5B, 1.5B or 3B model, independently of Chat. 1.5B is preselected; download the model explicitly before use.
- Cleanup adds punctuation/capitalization and removes selected filler words locally. A conservative content check rejects word changes, translations, changed numbers and damaged protected text. Failure, rejection or a configurable 3/8/15/30-second budget preserves recognized text with dictionary corrections. Native processing steps can briefly exceed the budget.
- Run the optional local benchmark to compare all offered models, actual examples, content-check outcomes and your personal quality rating. Missing models download sequentially and are deleted after testing; installed models remain. Cancel or normal quit unloads and removes temporary assets. Force quit/power loss can leave OS-temporary files.
- Speed labels start as estimates and use your Mac's measurements afterward. The benchmark saves only fixed synthetic examples and results, never your dictated text or audio. Four short cases are a comparison aid, not a general accuracy score.
- The 3B model has research/evaluation licensing restrictions; its license notice appears in Settings. Longer dictations may need a larger processing budget.

## Templates, dates and a steadier editor

- Create named Markdown templates in Settings → Notes & Obsidian; insert them from `/template`, `/vorlage` or by searching their name.
- Templates support `{{date}}`, `{{time}}`, `{{datetime}}`, explicit formats such as `{{date:yyyy-MM-dd}}` and named custom fields with optional defaults. A small insertion form asks for custom values. Cancel keeps the source text; changes to the note prevent a stale replacement.
- Insert the current date/time directly with slash commands, including within a line after whitespace. English and German command aliases work in either interface language.
- Built-in slash command titles, hints, empty results and accessibility labels follow the app language.
- Undo/Redo treats slash/template insertion as an edit. Repeated Enter reliably leaves lists and quotes; subsequent Enter, Tab and Backspace no longer operate on the preceding item. Cached paragraph invalidation is bounded after large template undo operations.

## System-wide Fn evaluation

The normal public app remains sandboxed and supports dictation inside notes. System-wide Fn dictation is available in the separate **flote Dictation Dev** evaluation package in the private development release, using its own app identity, permissions and settings. It cannot install the normal app through the stable updater. Hold Fn to speak and release to insert; double-tap for hands-free recording, Escape to cancel. TextEdit and Chrome insertion have been exercised; broader app/fullscreen/security-field acceptance remains in progress. This is not a claim that the normal sandboxed download supports global Fn capture.

## Installation and updates

Quit flote and move flote.app from **flote-3.15-14.dmg** into Applications, or use **Check for Updates…** on a public-feed version (3.7 or later). Existing notes, settings and retained compatibility identifiers remain. Models download separately. Full previous-version Sparkle installation/relaunch has not been revalidated for this version; feed/archive signatures and package structure are verified separately. Intel binaries are verified structurally; runtime tests run on Apple Silicon.

The universal offline CLI is included at flote.app/Contents/Helpers/flote. See VAULT-AND-CLI.md for setup. Public packages are ad-hoc signed and not notarized. The app is proprietary freeware; LICENSE.txt and THIRD_PARTY_NOTICES.md accompany the distribution. Source and internal verification files are not included.
