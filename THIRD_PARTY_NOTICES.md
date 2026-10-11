# Third-party notices

These dependencies retain their upstream licenses; this document does not assign a license to flote. Full original license/notice texts are in `licenses/` beside this file and are included in the app distribution. Versions and source revisions match Package.resolved. Some resolved packages provide transitive functionality rather than a separately loaded library.

| Dependency | Version | Revision | Original texts |
|---|---|---|---|
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

Model weights are **not bundled**. Settings downloads `Xenova/multilingual-e5-small` export revision `761b726dd34fb83930e26aab4e9ac3899aa1fa78`, derived from `intfloat/multilingual-e5-small` (Microsoft multilingual E5, Liang Wang and contributors). The original model declares MIT; the pinned export card references that base model and declares no separate license: [pinned export card](licenses/e5-export-model-card.md), [original card](licenses/e5-original-model-card.md). The [Microsoft UniLM repository license](licenses/unilm-model-repository-LICENSE) is included as upstream project attribution. Download sizes and SHA-256 hashes are pinned in LocalModelManager.swift; see that source for exact artifact provenance. A one-time Hugging Face download is required; inference is local afterward.

License texts were copied from the resolved package checkouts and the upstream URLs listed in [provenance.json](licenses/provenance.json).
