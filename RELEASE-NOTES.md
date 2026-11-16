# flote 3.21

Released 16 November 2026 — build 21. macOS 14 or later; universal Apple Silicon and Intel application. Live local speech recognition requires Apple Silicon; Parakeet Redux also requires macOS 15 or later.

## Transcribe saved meetings again

Open a saved meeting and choose **… → Retranscribe…** to use a larger model from your existing local Whisper installation. flote detects Homebrew Whisper and cached `.pt` models, including Large v3 and Large v3 Turbo. You can choose another executable/checkpoint and select the spoken language or automatic detection. The existing local Python Whisper installation and its dependencies are required; flote does not download a model for this action. Processing runs locally on CPU and large models may take longer.

The meeting must have been recorded with **Keep audio** enabled. Microphone and system recordings are processed separately, preserving source time and visible gaps. Progress and Cancel remain available. Success creates a new transcript version; **… → Transcript versions** switches back to the original or another version. Manual notes remain shared, and older citations still open their source version. Review speaker labels in the new transcript. A failed or cancelled job leaves the active transcript intact.

## More reliable recording and window controls

Short audio interruptions now remain explicit gaps instead of being joined into continuous speech. Repeated or stale capture windows cannot rewind transcript time; invalid word timestamps leave a visible explanation. Exact non-speech markers are filtered. Source-health reporting distinguishes silence from verified audio, while retry and elapsed time use a monotonic clock.

The meeting close control stays on screen at small window sizes and after display changes. Closing or pressing Escape hides the meeting window; reopen it with the Meetings shortcut (default ⌥⌘M). Use **Stop & save** to finish an active recording. Manual transcript scrolling also suspends following reliably.

## Verification and remaining limits

The final feature regression passed 215 tests across 20 suites. Existing Large v3 and Large v3 Turbo checkpoints actually retranscribed a synthetic retained-audio fixture without downloads. Both complete 1,049-second natural-recording benchmarks were processed during acceptance work. These checks do not certify every conferencing app or recording environment; distant-room recognition and optional speaker identification still have substantial quality limits. Review transcripts and source health. Physical call/device/sleep/screen-sharing and acoustic-echo acceptance remains incomplete.

Existing notes, retained recordings, preferences, cached models and the stable update channel are preserved. Packages use ad-hoc Apple signatures and are not notarized; macOS may require first-launch approval or renewed privacy permission after an update.
