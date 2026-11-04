# Daily reports

Use **Daily report…** in the menu bar, or **Settings → AI → Open daily report**.
Select a day, adjust the saved report instructions, and click **Generate daily
report**. Review the plain-text Markdown preview, then **Save as new note**.
**Open saved report** opens the result in the normal editor for manual changes.
Repeated Save does not create another note. Regeneration creates a new preview;
it never overwrites an existing report or a source note.

The source set is the managed collection's saved Markdown notes whose filesystem
modification time falls within the chosen local calendar day. This includes older
notes edited that day; it does not reconstruct historical versions or include
unsaved editor text. Save open notes first. A day uses a half-open interval from
local midnight to the next midnight, including DST transitions. The read-only
Obsidian vault, generated daily reports, Topics.md and Backlinks.md are excluded.
Reports include a source list with local note links and stable note identities.

Instructions persist across relaunch. Generation follows the existing enabled
AI provider and selected model: built-in local, local Ollama, or Google Gemini.
The panel displays that scope before generation. Gemini receives full selected
source text and report instructions; local generation does not read the cloud
API key and never falls back to cloud. There are no automatic downloads or
scheduled/background reports.

All source text is processed in bounded 3,000-character windows. Partial reports
are combined pairwise with a 2,400-character response bound. One request runs at
a time; every stage checks cancellation. The daily input limit is 200 notes /
200 KB of UTF-8 body text. An excessive corpus, unreadable selected note, oversized
note, empty day or invalid model output produces an explicit error, not silent
source truncation. Closing the window or changing generation/folder settings
cancels pending work; late results are rejected. A folder change blocks saving
an old preview into the new collection. Failed generation/save preserves the
existing preview, saved reports and source files for retry.

The model is instructed to preserve names, amounts, negations and uncertainty,
distinguish proposals from commitments, and avoid invented task owners/deadlines.
These are model instructions, not a guarantee of factual accuracy. The preview
requires manual review; report generation never writes Reminders or tasks.

Tests use a synthetic provider without downloading models or sending notes to a
network service. They verify calendar boundaries (including a 25-hour day), full
long-source coverage, bounded requests/reduction, malformed output, explicit
limits, instruction persistence, preview-before-save, single save, unchanged
sources, cancellation and folder-change rejection. Native UI coverage exercises
custom instructions, Generate, Save and Open in an isolated collection. Real
model summary quality remains dependent on the selected provider/model.
