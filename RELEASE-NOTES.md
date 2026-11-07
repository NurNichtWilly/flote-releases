# flote 3.20

Released 7 November 2026 — build 19. macOS 14 or later; universal Apple Silicon and Intel application. Local speech recognition requires Apple Silicon; Parakeet Redux also requires macOS 15 or later.

## Meetings in a floating window

Start a meeting explicitly with microphone, other apps’ playback audio, or both. The compact transcript-first window follows Flote’s floating behavior. Hide it while recording continues, and reopen it with the configurable Meetings shortcut (default ⌥⌘M). Source health and Stop remain available; history, participants and advanced options appear on demand.

Meeting capture is an early version. Real-call/device switching, permission recovery, screen sharing, acoustic echo and speaker identification still need broader physical testing. Playback and microphone can contain the same voice; complete echo suppression is not promised. Optional speaker identification is off by default and inferred labels remain uncertain; manually confirm participant names when attribution matters. Stop a meeting before quitting the app.

## Durable transcripts and optional audio

Timestamped transcripts are saved in the selected collection independently of AI generation. Keep audio is an explicit option; transcript-only meetings remain searchable and navigable. Retained audio supports playback, pause and timestamp seeking. Interrupted saves can recover, and deletion controls remove retained audio or the meeting while preserving ordinary notes and shared models.

## Evidence-based notes and reviewed next steps

Process the whole transcript in bounded statement units, including late decisions. Notes preserve original source statements, distinguish proposals, promises, decisions, questions and revisions, and flag uncertain classifications for review. Background topics stay collapsed. This is extractive evidence, not a promise of fluent abstractive summaries.

Owners require manually confirmed speaker evidence; unknown owners stay unknown. Dates remain literal source wording. Review proposed tasks before creating them; repeated generation preserves manual notes and avoids duplicate accepted tasks, including multiple actions from one segment. Saved transcripts remain usable when a model is missing or generation fails.

## Search and ask meetings

History and keyword search work without an AI model, including long and nested meeting artifacts. Source links open the transcript moment and seek retained audio when available. Meeting chat shows original source context, keeps meetings separate and marks answers whose generated evidence selection could not be verified. Retrieval is bounded; relevant passages may be missed. Verify the cited statements before relying on an answer.

Processing is local by default. Cloud text processing requires a separate explicit meeting setting; meeting audio is not uploaded. Models are prepared explicitly and remain separate from the app download.

## Updating and verification

Existing notes, folder grants, preferences, cached models and the stable update channel are retained. Packages use ad-hoc Apple signatures and are not notarized; macOS may require approval or renewed Accessibility permission after an update.

Validation includes 179 meeting tests with each cached 0.5B and 1.5B model, native floating-window/source navigation, muted audio seeking and pause, transcript-only access, no-model search, physical storage-failure probes, and universal package/signature checks. Fixtures are synthetic. These checks do not certify live-call quality, physical speaker attribution or Intel inference. Existing dictation and note-taking remain available.
