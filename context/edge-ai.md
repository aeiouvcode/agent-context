# EDGE//AI — on-device inference in the browser

On-device AI inference for any phone: zero backend, no key, no account.

## Facts
- Repo: `github.com/aeiouvcode/edge-ai` — live at
  `aeiouvcode.github.io/edge-ai`.
- Device probe reports what the phone can actually run; model shelf
  (SmolLM2, Qwen2.5, Whisper, translation, embeddings, vision, TTS) with
  honest per-device fit; WebGPU with WASM fallback; models cached offline.
- Privacy cloak layer (AgentCloak-style): synthetic twins substituted before
  anything leaves the device.
- Open Muse bridge: Open Muse can select EDGE//AI as its on-device engine —
  verified live.

## Current state
- **Live and verified 2026-09-26 09:25:** 135M model loads in ~35s on phone
  WASM, Stop unloads the model, chat runs in a worker.
- Cloak: engine PASS, end-to-end PARTIAL (cloud routing not built).
- Pocket Lab benchmarking and bring-your-own-model shipped (100x phase 1).

## Decisions
- Pinned, integrity-checked engine files and no remote code after a raw error
  screenshot read as "felt like I downloaded malware" — error handling is a
  design requirement.

## Open items
- [ ] 100x phases 2–6: compat validator, WebLLM dual engine, arena +
  leaderboard, voice loop + PWA, opt-in cloud escalation.
- [ ] Jules build prompt for EDGE//AI v2 delivered; Jules track is Vansh's.

## Grades
- 2026-09-26: design PASS, security PARTIAL.
