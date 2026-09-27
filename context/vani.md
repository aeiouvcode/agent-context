# Vani — on-device voice transcription

Real-time, on-device transcription PWA. Nothing leaves the phone.

## Facts
- Live at `aeiouvcode.github.io/vani` (public GitHub Pages PWA since
  2026-09-26 09:50).
- Reference: Kivi (heykivi.ai). Requirements: real-time transcription, saved
  recording transcription, fast and accurate, optimized for edge devices,
  works in noisy environments.
- Two models: fast, and accurate (141MB, downloaded once and cached).

## Current state
- Noise suppression holds at moderate noise; fails when speech is quieter
  than the noise.
- Vansh's bar is speed: "almost instantaneous" — preload and keep the engine
  warm, stream words live, report open-to-ready and tap-to-first-word times.
- Voz (desert-ant-labs/voz on HuggingFace) under evaluation as a model
  option (his pointer, 09-26).

## Decisions
- On-device only, per the local-first rule across the portfolio.

## Open items
- [ ] Speed pass: preload/warm engine, live word streaming, timing metrics.
- [ ] Live-mic accuracy on Vansh's phone — unverified.
- [ ] Voz model evaluation.

## Grades
- UNTESTED on device (live-mic accuracy pending Vansh's phone).
