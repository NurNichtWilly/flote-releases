# flote 3.18

Released 4 November 2026 — build 17. macOS 14 or later; universal Apple Silicon and Intel application. Speech recognition requires Apple Silicon; Parakeet Redux also requires macOS 15 or later.

## Daily reports from your notes

Choose Daily report… in the menu bar, select a day and customize how your report should look. Review the generated Markdown preview, then save it as a new note. Sources are saved flote notes last modified on that local calendar day; existing reports and the read-only Obsidian vault are excluded. Save open notes first.

Reports use your selected AI provider: built-in local, local Ollama or Google Gemini. The report window explains the processing scope before generation; Gemini receives the selected notes and your report instructions. No models download automatically. Longer notes are processed in bounded sections, with explicit limits and errors instead of silent truncation. Source notes and your manual report edits are preserved.

## Spoken formatting without an AI cleanup model

Settings → Dictation now offers optional English/German formatting commands with independent punctuation and number switches. Examples include “insert comma”, “insert new paragraph” and “number seven”, or “Komma einfügen”, “Absatz einfügen” and “Zahl sieben”. Select the spoken language explicitly. Bare punctuation words and ordinary number words remain literal; supported number commands cover 0–12 and preserve unsupported compounds.

Dictionary spellings, quoted commands, URLs, paths and code are protected. Rules run on the final transcript after dictionary corrections and before optional local AI cleanup. Live previews remain unprocessed.

## Updating and verification

Existing notes, settings, cached models and the stable update channel are retained. Packages continue to use ad-hoc Apple signatures and are not notarized; macOS may require approval or renewed Accessibility permission after an update. Speech model downloads remain explicit in Settings.

Automated checks cover local calendar/DST boundaries, long-note coverage, source ordering, cancellation, report edits/renames/deletion, formatting boundaries and unsupported compounds. Native UI checks exercise report preview/save/open, ordinary note editing and dictation settings in English and German. Generation tests use synthetic responses; summary accuracy depends on the selected model and should be reviewed before saving. Intel runtime execution and universal external-editor dictation compatibility are not claimed.
