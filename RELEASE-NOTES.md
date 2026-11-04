# flote 3.17

Released 4 November 2026 — build 16. macOS 14 or later; universal Apple Silicon and Intel application. Speech recognition requires Apple Silicon; Parakeet Redux also requires macOS 15 or later.

## Speak immediately

Recording starts before the cached speech model finishes loading. You can speak as soon as microphone access is available; audio is buffered in memory and recognition catches up. Releasing Fn during model loading stops capture and transcribes the recorded audio when the model is ready.

## Live dictation across apps

Recognized text appears while you speak through the app's normal keyboard-input path. New words extend the current dictation, recognition corrections revise its suffix, and final recognition or optional cleanup updates that same passage without inserting a second copy.

A keyboard fallback supports editors that do not expose readable text or editable selections through macOS Accessibility. Where the destination exposes its text, flote verifies the result. Otherwise it reports the text as sent and retains Copy text for recovery. App-specific text handling can still affect compatibility; password fields and secure keyboard input remain excluded.

Typing yourself, moving with navigation keys or clicking outside the recording controls stops further dictation input. Normal Fn release lets an already-started text update complete before finalizing.

## Smaller recording controls

The recording window is more compact and stays at a screen edge, away from the pointer and available caret bounds. Its position is chosen again for every recording.

## Updating and permissions

Existing notes, settings, model files and the stable update channel are retained. Enable Dictate everywhere in Settings → Dictation and allow Accessibility and Microphone access. In macOS Keyboard settings, set the Globe/Fn action to Do Nothing to avoid competing actions. Models are prepared explicitly in Settings; recording does not initiate a download.

Packages continue to use ad-hoc Apple signatures and are not notarized. macOS may require app approval or renewed Accessibility permission after updating. The bundled offline CLI and freeware/third-party license terms remain included.

## Verification scope

60 focused dictation tests cover recording during model loading, pending edits at Fn release, Unicode and shorter corrections, keyboard fallback behavior, focus/user-input interruptions, clipboard recovery and delayed text/caret updates. The local development build was manually tested by the user. Compatibility with every external editor and Intel runtime execution are not claimed as fully validated.
