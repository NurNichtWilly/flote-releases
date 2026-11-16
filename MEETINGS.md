# Saved meeting retranscription

Record with **Keep audio** enabled to retain microphone and selected system audio.
Open the completed meeting and choose **… → Retranscribe…**. Select an existing
local Whisper model and the spoken language, or automatic detection.

flote detects Homebrew `whisper` and cached `~/.cache/whisper/*.pt` checkpoints,
including Large v3 and Large v3 Turbo. You can select another executable or model
file in the dialog. Install Python Whisper and its dependencies separately;
models are not bundled and this action initiates no model download. Inference
runs locally on CPU. Larger models can take substantially longer.

The action creates a new transcript version. Use **… → Transcript versions** to
return to the original or another version. Manual notes and retained audio remain
shared. Older citations open the version containing their source segment.
Generated notes belong to the selected transcript. Review new speaker labels;
prior manual assignments are not guessed onto new words. Existing reviewed tasks
remain saved. Cancel or failure preserves the active transcript.

Recording, dictation/model preparation and conflicting meeting edits/deletion
are blocked during processing. Progress and Cancel remain available. Quitting
waits for cancellation. Meetings recorded without retained audio cannot be
retranscribed later. Removing retained audio clears playback references across
all transcript versions while preserving text.

System audio needs macOS Screen & System Audio Recording permission for the
installed app. Check source health and use Retry sources after restoring access.
Closing/Escape hides the meeting window; recording continues until Stop & save.
Optional speaker identification remains experimental and starts off. Distant-room
speech, acoustic echo and real call/device/sleep/sharing cases still require
review; a larger model does not guarantee a correct transcript.
