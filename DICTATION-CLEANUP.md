# Dictionary, local cleanup and model comparison

Settings → Dictation has three independent sections:

- **Personal dictionary**: explicit recognized phrase → preferred spelling. The
  replacement runs once after final recognition, even when AI cleanup is off.
  Matching ignores case, respects Unicode word boundaries and prefers the longest
  overlapping phrase. It excludes URLs, email addresses, paths and backtick code.
  No fuzzy matching or speech-model vocabulary boosting is enabled.
- **AI text cleanup**: disabled by default. Its model is independent of Chat and
  uses only the pinned, built-in Qwen2.5 0.5B/1.5B/3B Q4_K_M models on CPU. No cloud
  provider or Ollama fallback. Download the chosen model explicitly; dictation
  never downloads it. Live previews stay raw. Final note text and system-wide Fn
  dictation share the same pipeline.
- **Local cleanup benchmark**: explicitly opt in with “Benchmark all cleanup
  models”. Models run sequentially against four fixed German/English samples.
  The benchmark downloads missing weights to unique temporary directories, checks
  their pinned size/SHA256, unloads each runtime, and removes its own download.
  Installed weights are borrowed read-only and never removed. Cancellation and
  normal app quit await unloading/removal; force-killing the app or a power loss
  can leave files in the app's temporary directory until system cleanup.

Cleanup may add punctuation/capitalization and remove unambiguous fillers. It
cannot safely interpret ambiguous false starts, rewrite sentences, correct
arbitrary words, translate, summarize or answer dictated questions. A strict
ordered-word check rejects additions, omissions (except selected fillers),
translations, changed numbers and damaged URLs/code/paths. Dictionary spellings
receive an additional check. The German word “um” is preserved because it can be
meaningful. Repeated words are preserved. The check is conservative, not a proof
of semantic equivalence: punctuation itself can affect meaning. Review important
text as with normal speech recognition.

Choose a 3/8/15/30-second processing budget (default 8). A missing model, rejected
response, context limit, failure or timeout keeps the recognized text with the
explicit dictionary corrections. Deadlines/cancellation are checked between
native load/decode steps; an in-progress native step can briefly exceed the
budget. Cancelling or closing a dictation session suppresses late results. Note
edits made during processing remain protected by the existing editor checks.

Optional per-app exclusions use exact bundle IDs captured at recording start.
Terminal, iTerm2 and Warp start excluded. These exclusions skip AI cleanup, while
explicit dictionary corrections still apply. A browser exclusion affects all its
tabs; there is no tab classification.

The benchmark stores only its synthetic input/output examples, content-check
outcomes, timings, hardware/OS/runtime information, model revision, corpus version
and your optional 1–5 quality rating. It stores no dictated text or audio. The
median covers accepted examples only, so **always compare the pass count and the
actual examples**. Rejected output is shown for inspection but would never be
inserted by the dictation pipeline. “Fast” means at most 1 second, “Medium” at
most 3 seconds, “Slow” above 3 seconds for these short samples. These are not
promises for long dictations. Cold load includes integrity verification; download
time is excluded and filesystem caches can affect repeated runs. Existing local
Chat work finishes before measurement; new built-in generation and dictation
wait until the benchmark ends. Other apps and thermal load can affect results.

Measurements replace relative size-based estimates only when hardware/OS, model
revision and corpus version match. Selecting a benchmark result sets only the
cleanup model; it does not enable cleanup or install the temporary benchmark
weights. The 3B research/evaluation license notice is retained in both selection
and benchmark settings.

