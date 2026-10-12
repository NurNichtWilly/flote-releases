# Chat with notes and AI tags

Open **Settings → AI Generation — Chat and Tags** and explicitly enable generation. Semantic search remains a separate setting. Choose one generation provider:

- **Google Gemini**: save your API key in Keychain and choose a Gemini model supporting structured output. The initial model is `gemini-2.5-flash`. Selected excerpts and your question are sent to Google. The key is shared with Gemini semantic search.
- **Local — Ollama**: start Ollama on this Mac. Choose an installed chat model directly in Chat → **Models**, or download Qwen 3.5 2B/4B or Gemma 4 through the local-model download panel. Other installed completion models are also selectable. flote talks only to `127.0.0.1:11434`, with no automatic cloud fallback.
- **Local — built into flote**: choose Qwen 2.5 Instruct Q4_K_M in 0.5B (491 MB), 1.5B (1.12 GB), or 3B (2.10 GB). Download and select it inside Chat → **Models** or Settings → **Download local models**. flote verifies pinned size and SHA-256 before installation. CPU inference works with the universal macOS app; no separate service is required. The 3B option uses the Qwen Research license (research/evaluation only; commercial use requires a separate model license); 0.5B and 1.5B use Apache 2.0. Small models can produce weaker answers and tags than larger models. Invalid responses show a retryable error.

## Chat

Semantic search also supports **Ollama — EmbeddingGemma 2** in Settings. Start Ollama and install `embeddinggemma-2`, then check availability and enable semantic search. This local provider needs no Gemini key and can be used by local chat. Its 768-dimensional vectors use separate search-query/document prefixes and a distinct cache identity, so switching from E5 or Gemini rebuilds the derived index. Only text embeddings are currently supported; the model's image/audio features are not used.

Choose **Chat with Notes** from the menu bar or press `⌥⌘C`. Rebind the shortcut in Settings. Repeated activation focuses the same chat. Enter a message: keyword matches appear as clickable **Related notes** before semantic inference finishes, then semantic matches refine the suggestions. Open a suggested note while the model works. The answer text streams incrementally with Ollama, Gemini, or the built-in runtime; supporting citations become buttons only after the final answer passes validation. You can cancel or start a new conversation. Closing the panel cancels a request and retains completed turns in memory until a new conversation, configuration change or app exit.

Chat searches flote notes by default. **Include Obsidian vault** explicitly adds Markdown files from the selected vault as read-only sources. Configure the vault in the Obsidian settings section first. It does not authorize changes to external files.

Retrieval combines keywords with optional semantic ranking for managed notes. External vault sources use keywords. Local chat uses semantic retrieval only with local embeddings; it never sends your question to Gemini embeddings. If search is configured for cloud embeddings, local chat uses keywords instead. The answer uses up to six excerpts, with a total 9,000-character source budget; this is not an exhaustive read of every note. Sources over 1 MB are skipped, the loaded corpus is limited to 20 MB, and vault inventory is capped at 10,000 files. The retrieval mode appears in the chat. Common German/English question words are removed from keyword matching.

Supporting sources appear as buttons. Managed notes resolve by their stable UUID after renaming; external sources open as files in the granted vault. Missing files report an error. A changed managed source opens its current contents and warns that the answer used an older snapshot. The assistant responds normally to greetings and general knowledge questions; purely general answers are labeled **General knowledge**. Personal facts require note evidence, and missing or conflicting evidence is shown when reported by the model. Technical citation validation does not guarantee that every model claim is factually grounded.

Changing the model or provider cancels an in-flight answer while retaining completed turns. Changing the source scope clears the conversation. A late or cancelled response cannot replace newer state. Chat never writes to source notes, runs commands or invokes tools. Source instructions are treated as untrusted text.

## Tags

Enable **Suggest AI tags after saving notes**. A settled save queues a suggestion after a short delay. Open the saved note and choose **Review tags**, edit the comma-separated tags and apply them. **Suggest tags** retries manually; **Stop** cancels pending work for the note. **Reject suggestions** records the rejected tags without removing your own tags. **Later** keeps the suggestion available.

**Automatically accept suggested tags** is a separate option, off by default. When enabled, valid suggestions are applied to flote notes after the source is checked again. Changes made while generation runs prevent application. An open note must match the source and receives the change through the editor/undo/autosave flow. Closed files use a coordinated comparison before writing and do not create conflict copies or resurrect deleted notes.

Generated tags are ordinary inline Obsidian tags in a dedicated `flote-ai-tags` Markdown section. Its HTML comments store provenance, processing signatures and rejected tags; flote hides those metadata comments in the editor. Existing inline tags, all frontmatter and the remaining Markdown stay intact. **Edit AI tags** corrects or removes generated tags. Rejected tags are suppressed on later processing. Unchanged notes do not repeatedly generate or write tags.

`Topics.md` groups both authored and generated tags. Existing topic/backlink navigation is reused; links refresh after managed renaming, retagging and deletion. Handwritten content outside `flote-generated` markers remains untouched. Index generation detects changed managed snapshots and retries through the normal refresh. Uncoordinated external editors remain a concurrency limitation.

## Verification

Normal unit tests use synthetic sources and fake transports. Run the real local-model test explicitly:

```sh
TEST_RUNNER_FLOTE_GENERATION_MODEL_TEST=1 xcodebuild \
  -project flote.xcodeproj -scheme flote \
  -destination 'platform=macOS,arch=arm64' \
  -parallel-testing-enabled NO \
  -only-testing:floteTests/IntegratedGenerationTests test
```

For an installed Ollama model, set `TEST_RUNNER_FLOTE_OLLAMA_MODEL_TEST` to its name and run `OllamaGenerationTests`. This sends synthetic text to the local service only.

The test downloads and verifies the pinned model in the test sandbox, then checks real structured tags and a sourced budget answer. Native chat UI coverage is in `ChatUITests`. This change also verified the local Ollama service with `gemma4:12b` and a clean Obsidian 1.14.4 vault: tags, nested tags, frontmatter, image asset, index links, managed rename and deletion. Gemini is covered by fake transport tests, not a live API call. The small real-model checks do not replace a broader grounding evaluation.

Provider integration references: [Gemini structured output](https://ai.google.dev/gemini-api/docs/structured-output), [Ollama chat API](https://docs.ollama.com/api/chat), [llama.cpp Swift runtime example](https://github.com/ggml-org/llama.cpp/tree/b5046/examples/llama.swiftui).
