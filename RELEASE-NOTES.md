# flote 3.19

Released 5 November 2026 — build 18. macOS 14 or later; universal Apple Silicon and Intel application. Local speech recognition requires Apple Silicon; Parakeet Redux also requires macOS 15 or later.

## More reliable dictation

System-wide Fn dictation now reconnects automatically when Accessibility access returns or keyboard monitoring is interrupted. Settings and the menu explain permission recovery. Recording and model preparation share one lifecycle across note windows and external apps, with safer cancellation, microphone-permission changes and quitting.

Longer takes use bounded recognition windows in Whisper Base, Whisper Tiny and Parakeet Redux. This release fixes a Whisper Tiny finalization stall involving repeated context. Recognition quality still varies by model, language, noise and recording; the take limit remains 55 seconds. Audio stays in memory, and speech/model downloads remain explicit in Settings.

## Recording controls that disappear automatically

After you release Fn or press Stop, the recording overlay disappears after five seconds once text insertion has completed. If processing takes longer, it stays visible until completion. Insertion errors keep the recognized text available through Copy text. Starting another take cancels the previous hide timer.

Live text continues to appear in the focused supported application and is revised by the final result instead of being appended twice. Native/user acceptance includes Claude, ChatGPT, Chrome, Obsidian, Safari including fullscreen, and Terminal. This does not promise compatibility with every editor or physical display layout. Password fields are excluded; changed, read-only or unsupported destinations use recovery.

## Terminal input without automatic submission

Terminal and iTerm transcripts containing line breaks or control characters are retained for explicit Copy review instead of being entered automatically. Ordinary Unicode text and emoji remain supported. This prevents spoken formatting commands from automatically submitting a command.

## Updating and verification

Existing notes, folder grants, settings, model caches and the stable update channel are retained. The normal Release remains unsandboxed. Packages use ad-hoc Apple signatures and are not notarized; macOS may require approval or renewed Accessibility permission after an update. If Fn no longer starts, check Settings → Dictation and restore access under System Settings → Privacy & Security → Accessibility.

Validation includes focused lifecycle/editor/input regressions, native Settings/note workflows, signed native insertion/field-protection checks, direct/sandboxed upgrade-access tests, and same-audio clean/noisy German/English, UK-English and 55-second comparisons across all three engines. Recognition is imperfect; benchmark fixtures are synthetic. Intel speech inference, universal cross-app compatibility and every physical keyboard/display layout are not claimed.
