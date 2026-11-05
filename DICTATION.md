# Dictation in flote

Local speech recognition requires Apple Silicon. Whisper Base/Tiny support
macOS 14 or later; Parakeet Redux requires macOS 15 or later. Downloads are
explicit in Settings → Dictation; recordings do not download a model for you.

## Dictate into another app

1. Prepare your speech model in Settings → Dictation.
2. Enable **Dictate everywhere** and, if wanted, **Use Fn / Globe key**.
3. Allow Accessibility access in macOS Privacy & Security. Microphone access is
   requested when you start recording. If macOS requests Input Monitoring, allow
   that separately. Set the Globe key to **Do Nothing** in macOS Keyboard settings
   to avoid conflicts with Apple Dictation/Emoji and other Fn utilities.
4. Focus a supported text field, hold Fn to speak and release to finish. Double-tap
   for hands-free recording, then press again to finish. Escape cancels. The
   configurable alternative shortcut uses the same gestures.

The overlay stays away from the typing area. It disappears five seconds after
release/Stop once insertion is complete; slower processing remains visible.
Failed insertion keeps **Copy text** available. Use **Dictate everywhere** from
the menu or **Show recording controls** in Settings to reopen the controls.

Live words can be revised as recognition improves. Final dictionary, formatting
and optional local cleanup revise the same owned text rather than adding a second
copy. Typing/clicking during a take stops further live input. Password fields are
excluded; read-only, changed and unsupported fields use recovery. Some custom
editors cannot confirm text consumption, so check the output before starting
another take. Not every editor/keyboard/display configuration is guaranteed.

## Notes, language and formatting

**New Dictation Note** stays a separate action. Notes and external dictation share
one microphone session and prepared models. Choose automatic language detection
or an explicit language in Settings. Whisper Base usually offers better accuracy
than Tiny; Redux is another local option. Quality varies with language, noise and
recording. Each take is limited to 55 seconds; audio stays in memory.

Personal dictionary corrections, optional spoken punctuation/number commands and
local AI cleanup are independent options. See [formatting](DICTATION-FORMATTING.md)
and [dictionary/cleanup](DICTATION-CLEANUP.md). Live previews are unprocessed.

## Terminal and recovery

Terminal/iTerm input containing newlines or other control characters is retained
for explicit Copy review instead of automatic entry. This avoids submitting a
command through spoken formatting; the app does not press Return automatically.
Ordinary Unicode text and emoji remain available.

If Fn stops working after an update, open Settings → Dictation and inspect the
keyboard-control status. Under System Settings → Privacy & Security → Accessibility,
remove the obsolete flote entry and add/enable the current installed app if needed.
Monitoring reconnects automatically when access returns. Public packages are
ad-hoc signed and unnotarized, so macOS can require renewed approval after updates.
The app cannot grant itself these permissions.
