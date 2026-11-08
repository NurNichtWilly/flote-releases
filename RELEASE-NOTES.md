# flote 3.20.1

Released 8 November 2026 — build 20. macOS 14 or later; universal Apple Silicon and Intel application. Local speech recognition requires Apple Silicon; Parakeet Redux also requires macOS 15 or later.

## Start recording while the model loads

Meetings now open audio sources while the cached transcription model loads. Early audio enters a bounded queue; Stop & save and Hide remain available. If loading takes too long, dropped windows appear as explicit transcript gaps. Download a model once in Settings → Dictation; starting a meeting does not automatically download weights.

Interrupted model loading now shows a readable recovery message instead of a raw Swift Cancellation Error. Cancelling a cached Whisper load preserves downloaded weights. Failed loading stops capture and preserves recoverable metadata, gaps and any audio saved through Keep audio. An interrupted recognition window becomes a visible gap rather than a misleading storage error.

## Stop repeated recording requests

Missing buffers, silence, permission denial and system-audio errors no longer automatically restart both audio sources. This removes repeated macOS recording requests caused by timed retries. Failed-source status stays visible; use Retry sources explicitly after restoring permission or a device. Microphone engine startup/shutdown runs off UI work so the window stays responsive.

System audio still needs macOS permission. Under System Settings → Privacy & Security → Screen & System Audio Recording, allow the installed flote app if requested. macOS may still show its own permission requests or recording reminders. A permission granted to a separate development/test app does not grant it to your installed flote app.

## Hide the window reliably

⌘W and the Hide button work during model loading, recording and errors. Hiding the floating window keeps recording active. Reopen it with the configurable Meetings shortcut (default ⌥⌘M), then use Stop & save to finish.

## Verification and remaining limits

190 regression tests passed, including cached Whisper Base English/German recognition, cancelled-load cache preservation, startup buffering, permission/start cancellation and retry behavior. Native UI acceptance covered hiding during loading/errors, restarting and stopping. Signed development and universal builds passed signature checks.

A separately signed, system-only physical test on Apple M4/macOS 27.2 received real playback from a known synthetic file in another process and Whisper Base recognized its words. No microphone was opened in that probe. This does not certify the other M1 Pro Mac, simultaneous microphone/playback, all call apps, device switching, sleep/wake, screen sharing, acoustic echo or optional speaker identification. Meetings remain an early version; review source health and transcript gaps.

Existing notes, recordings, preferences, cached models and the stable update channel are retained. Packages use ad-hoc Apple signatures and are not notarized; macOS may require first-launch approval or renewed privacy permission after an update.
