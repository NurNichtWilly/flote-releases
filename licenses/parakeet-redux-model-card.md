---
license: cc-by-4.0
base_model: moondream/parakeet-redux
language: [en, de, fr, es, it, pt, ru, uk, hr, sl, lv, lt, et, fi, sv, da, nl, pl, cs, sk, hu, ro, bg, el, mt]
pipeline_tag: automatic-speech-recognition
tags: [coreml, parakeet, tdt, ternary, speech-recognition, apple-silicon]
library_name: fluidaudio
---

# parakeet-redux-coreml

Core ML build of [moondream/parakeet-redux](https://huggingface.co/moondream/parakeet-redux), the ternary
(every encoder weight ∈ {-1, 0, +1}) re-training of `nvidia/parakeet-tdt-0.6b-v3`. Same 25 languages, tokenizer and
output conventions as v3. Encoder is **183 MB** (vs 445 MB for the 6-bit v3 encoder); whole model dir ~220 MB.

The encoder keeps the checkpoint's exact ternary weights: 2-bit palettized codes with the model's own per-row,
per-128 fp16 scales (iOS 18 / macOS 15 `constexpr_lut_to_dense` + `constexpr_blockwise_shift_scale`), so no
re-quantization noise is added. Decoder and JointDecision are re-exported from the redux checkpoint (its post-training
recovery also touched the joint). Preprocessor and vocabulary are the v3 ones.

## Usage (FluidAudio ≥ next release)

```swift
let models = try await AsrModels.downloadAndLoad(version: .redux)  // iOS 18+ / macOS 15+
let asr = AsrManager()
try await asr.initialize(models: models)
let result = try await asr.transcribe(audioFileURL)
```

```bash
swift run fluidaudiocli transcribe audio.wav --model-version redux
swift run fluidaudiocli asr-benchmark --subset test-clean --max-files 100 --model-version redux
```

## Files

| File | Notes |
|------|-------|
| `Encoder.mlmodelc` | 183 MB, 2-bit ternary, iOS 18+/macOS 15+, fixed 15 s window (`mel [1,128,1501]` → `encoder [1,1024,188]`) |
| `Decoder.mlmodelc` | RNNT prediction net, fp16, iOS 17+ |
| `JointDecisionv3.mlmodelc` | single-step joint + argmax/softmax + top-64, fp16, iOS 17+ |
| `Preprocessor.mlmodelc` | mel front-end, identical to parakeet-tdt-0.6b-v3-coreml |
| `parakeet_vocab.json` | identical to v3 |

## Compute units

The encoder runs on the **Neural Engine** by default in FluidAudio, like v3, so iOS apps can keep transcribing in the
background (iOS does not allow GPU work there). The first ANE load compiles the 2-bit weights for several minutes
(~7 min measured on an M-series Mac); Core ML caches the result and later loads take seconds. Warm, it runs
45–52 ms per 15 s window.

Pass `encoderComputeUnits: .cpuAndGPU` to skip the long first compile when background execution does not matter: the
GPU decompresses the 2-bit weights in-kernel, loads in about a second and runs ≈21 ms per window.

Requires iOS 18 / macOS 15 (the 2-bit encoding uses iOS 18 Core ML ops). On iOS 17 / macOS 14 FluidAudio refuses to
load Redux and points to
[parakeet-ultra-coreml](https://huggingface.co/FluidInference/parakeet-ultra-coreml) instead.

## Accuracy

Full LibriSpeech, FluidAudio `asr-benchmark`, default compute units (ANE), both models back to back, M-series Mac. Corpus WER (total edit distance over
total reference words); RTFx = total audio / total processing time.

| Set | parakeet-tdt-0.6b-v3-coreml | parakeet-redux-coreml |
|-----|---------------------------:|----------------------:|
| test-clean (2620 files) | **2.27 %** | 2.71 % |
| test-other (2939 files) | **4.12 %** | 5.12 % |
| RTFx, test-clean | **128.6×** | 83.9× |

On English this build is 0.44 (clean) and 1.00 (other) points behind v3 — the same gap the upstream card reports
(+0.44 / +1.21). Absolute values are above the card's because FluidAudio decodes in 15 s windows and uses a simpler
text normalizer than the Open ASR Leaderboard; both models are scored identically here.

The Core ML transcripts match a PyTorch fp32 decode of the redux checkpoint to 0.19 % WER, so this is the
checkpoint's behaviour and not a conversion loss.

### FLEURS, 24 languages, 100 samples each

| | parakeet-tdt-0.6b-v3-coreml | parakeet-redux-coreml |
|---|---:|---:|
| mean WER | 14.81 % | **13.06 %** |
| duration-weighted WER | 14.65 % | **12.89 %** |
| languages won | 11 | **13** |
| RTFx | **149×** | 134× |

(`es_es` is absent from FluidAudio's FLEURS set; both models are scored on the same 24.)

Redux wins the multilingual average by 1.74 points, taking the low-resource languages by wide margins — Latvian
−11.1, Maltese −7.7, Slovene −7.2, Estonian −7.0, Greek −5.2, Lithuanian −5.1 — and conceding the high-resource
ones: French +3.7, Russian +2.6, Dutch +1.9, English +1.9, Polish +1.7, Ukrainian +1.4. The per-language direction
matches the upstream card in 23 of 24 languages.

**Pick this model for multilingual work and for download size; pick
[parakeet-tdt-0.6b-v3-coreml](https://huggingface.co/FluidInference/parakeet-tdt-0.6b-v3-coreml) for English.**

## License

CC-BY-4.0, same as the upstream checkpoint and nvidia/parakeet-tdt-0.6b-v3. Model by moondream (vik); Core ML
conversion by Fluid Inference (conversion recipe: `mobius/models/stt/parakeet-redux/coreml`).
