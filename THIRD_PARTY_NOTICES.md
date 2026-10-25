# Third-party notices

These dependencies retain their upstream licenses; this document does not assign a license to flote. Full original license/notice texts are in `licenses/` beside this file and are included in the app distribution. Versions and source revisions match Package.resolved. Some resolved packages provide transitive functionality rather than a separately loaded library.

| Dependency | Version | Revision | Original texts |
|---|---|---|---|
| [Argmax OSS / WhisperKit](https://github.com/argmaxinc/argmax-oss-swift) | 1.1.1 | `1bbc57cb7fe6410248a685b1c5a3c6d56adc2ed4` | [MIT license](licenses/argmax-oss-swift-LICENSE), [incorporated third-party notices](licenses/argmax-oss-swift-NOTICES) |
| [FluidAudio](https://github.com/FluidInference/FluidAudio) | 0.17.3 | `a6b826ce9a09028fc685a4b32a8927ec920c3188` | [Apache 2.0 license](licenses/fluidaudio-LICENSE), [fastcluster](licenses/fluidaudio-fastcluster-LICENSE.md), [VBx](licenses/fluidaudio-vbx-LICENSE.md), [NeMo](licenses/fluidaudio-NemoTextProcessing-LICENSE.md), [Japanese G2P](licenses/fluidaudio-JapaneseG2P-LICENSE.md), [Kokoro G2P](licenses/fluidaudio-KokoroAneSpanishFrenchG2P-LICENSE.md) |
| [Swift Argument Parser](https://github.com/apple/swift-argument-parser) | 1.8.2 | `6a52f3251125d74daf04fcbd5e6f08a75d074382` | [LICENSE](licenses/swift-argument-parser-LICENSE.txt) |
| [Sparkle](https://github.com/sparkle-project/Sparkle) | 2.10.0 | `eef1a539a373c1f1a320624b1130fc5de7b2e100` | [LICENSE](licenses/sparkle-LICENSE) |
| [eventsource](https://github.com/mattt/EventSource.git) | 1.5.1 | `86b5096ac59ab46e66bd1f6377c604bc1dab0bc2` | [LICENSE.md](licenses/eventsource-LICENSE.md) |
| [keyboardshortcuts](https://github.com/sindresorhus/KeyboardShortcuts.git) | 3.1.0 | `772133d9dbe800fdac0473226822994c5c162c58` | [license](licenses/keyboardshortcuts-license) |
| [onnxruntime-swift-package-manager](https://github.com/microsoft/onnxruntime-swift-package-manager.git) | 1.24.2 | `b7fb7f7dea8a2469e6335d95a61b8f36d0dc83b2` | [LICENSE](licenses/onnxruntime-swift-package-manager-LICENSE) |
| [swift-asn1](https://github.com/apple/swift-asn1.git) | 1.7.3 | `3b6410f7dee09eb33cdd26260c5fd47fda19b0e2` | [NOTICE.txt](licenses/swift-asn1-NOTICE.txt), [LICENSE.txt](licenses/swift-asn1-LICENSE.txt) |
| [swift-async-algorithms](https://github.com/apple/swift-async-algorithms.git) | 1.1.7 | `13713a4ffdee8abd929f92568ee9462a46ae26e0` | [LICENSE.txt](licenses/swift-async-algorithms-LICENSE.txt) |
| [swift-collections](https://github.com/apple/swift-collections.git) | 1.7.1 | `98ef3c98609a1e31b7e157b5b619579001a789d6` | [LICENSE.txt](licenses/swift-collections-LICENSE.txt) |
| [swift-crypto](https://github.com/apple/swift-crypto.git) | 4.5.2 | `da9d28d69ebe3894b18376c8f2395c2f37b8448f` | [NOTICE.txt](licenses/swift-crypto-NOTICE.txt), [LICENSE.txt](licenses/swift-crypto-LICENSE.txt) |
| [swift-huggingface](https://github.com/huggingface/swift-huggingface.git) | 0.13.0 | `f0a0cb43cb1b402d2bbf6fb10d8981328c449c48` | [LICENSE](licenses/swift-huggingface-LICENSE) |
| [swift-jinja](https://github.com/huggingface/swift-jinja.git) | 2.5.1 | `4588064a20f3fc093c95f2f7d3359999bf30cae5` | [LICENSE](licenses/swift-jinja-LICENSE) |
| [swift-transformers](https://github.com/huggingface/swift-transformers.git) | 1.3.4 | `c21fdcde390313a6d98d8e33a346f2c3486c3ab0` | [LICENSE](licenses/swift-transformers-LICENSE) |
| [yyjson](https://github.com/ibireme/yyjson.git) | 0.12.0 | `8b4a38dc994a110abaec8a400615567bd996105f` | [LICENSE](licenses/yyjson-LICENSE) |

## ONNX Runtime

The native runtime distribution is Microsoft ONNX Runtime 1.24.2, MIT licensed. Its full [upstream third-party notices](licenses/onnxruntime-1.24.2-ThirdPartyNotices.txt) are reproduced without filtering; the upstream list can include components unused by this particular CPU build. BoringSSL attribution for Swift Crypto is also included in [the upstream license](licenses/boringssl-LICENSE).

## Optional downloaded model

Dictation optionally downloads multilingual Whisper Base or Tiny Core ML assets from [argmaxinc/whisperkit-coreml](https://huggingface.co/argmaxinc/whisperkit-coreml), which declares MIT, or [FluidInference/parakeet-redux-coreml](https://huggingface.co/FluidInference/parakeet-redux-coreml), which declares CC BY 4.0. Parakeet Redux is the Core ML conversion of moondream's ternary retraining of NVIDIA Parakeet TDT 0.6B v3; see the [upstream model card](licenses/parakeet-redux-model-card.md) for attribution and conversion details. These downloads use the SDK-managed upstream model repositories and caches, rather than pinned app-bundled weights. The selected engine is prepared only on an explicit user action; recognition runs locally. SDK licenses above apply separately from the model licenses.

Model weights are **not bundled**. Settings downloads `Xenova/multilingual-e5-small` export revision `761b726dd34fb83930e26aab4e9ac3899aa1fa78`, derived from `intfloat/multilingual-e5-small` (Microsoft multilingual E5, Liang Wang and contributors). The original model declares MIT; the pinned export card references that base model and declares no separate license: [pinned export card](licenses/e5-export-model-card.md), [original card](licenses/e5-original-model-card.md). The [Microsoft UniLM repository license](licenses/unilm-model-repository-LICENSE) is included as upstream project attribution. Download sizes and SHA-256 hashes are pinned in LocalModelManager.swift; see that source for exact artifact provenance. A one-time Hugging Face download is required; inference is local afterward.

License texts were copied from the resolved package checkouts and the upstream URLs listed in [provenance.json](licenses/provenance.json).

## Built-in language generation

The app links [llama.cpp](https://github.com/ggml-org/llama.cpp) b5046, MIT licensed ([license](licenses/llama.cpp-LICENSE)), from its universal macOS XCFramework. The upstream archive SHA-256 is `c19be78b5f00d8d29a25da41042cb7afa094cbf6280a225abe614b03b20029ab`, pinned in `Packages/FloteLlama/Package.swift`.

Optional Qwen weights are downloaded separately from `Qwen/Qwen2.5-0.5B-Instruct-GGUF`, revision `9217f5db79a29953eb74d5343926648285ec7e67`, file `qwen2.5-0.5b-instruct-q4_k_m.gguf`. Size: 491,400,032 bytes. SHA-256: `74a4da8c9fdbcd15bd1f6d01d621410d31c6fc00986f5eb687824e7b93d7a9db`. The [Apache 2.0 license](licenses/qwen2.5-LICENSE) and [pinned model card](licenses/qwen2.5-model-card.md) are included. The model is not bundled in the app.

Additional optional Qwen 2.5 Q4_K_M downloads:

| Model | Pinned revision | File size | SHA-256 | Terms |
|---|---|---|---|---|
| 1.5B | `91cad51170dc346986eccefdc2dd33a9da36ead9` | 1,117,320,736 bytes | `6a1a2eb6d15622bf3c96857206351ba97e1af16c30d7a74ee38970e434e9407e` | [Apache 2.0](licenses/qwen2.5-1.5b-LICENSE), [model card](licenses/qwen2.5-1.5b-model-card.md) |
| 3B | `7dabda4d13d513e3e842b20f0d435c732f172cbe` | 2,104,932,768 bytes | `626b4a6678b86442240e33df819e00132d3ba7dddfe1cdc4fbb18e0a9615c62d` | [Qwen Research](licenses/qwen2.5-3b-LICENSE), [model card](licenses/qwen2.5-3b-model-card.md) |

The 3B model's Qwen Research license permits research/evaluation use; commercial use requires a separate license from Alibaba Cloud. This restriction applies to that optional model, separately from flote's freeware terms. Models download directly from the pinned upstream repositories and are not bundled in flote.

Qwen is licensed under the Qwen RESEARCH LICENSE AGREEMENT, Copyright (c) Alibaba Cloud. All Rights Reserved.
