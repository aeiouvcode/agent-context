# FrameForge — browser video editor (long-horizon)

Professional browser video editor; competes with Premiere/DaVinci, targets
beating CapCut. Custom engine from scratch, no forks.

## Facts
- Repo: `github.com/aeiouvcode/frameforge-studio` — live on Pages.
- Engine direction: Zig→WASM core (Rust tested and kept out).
- Milestone cadence with an honest grade each milestone; gauntlet loop is the
  standing instruction ("keep building until better than the frontier").

## Current state
- Through M189 live: speed ramps carry audio, chroma key, real export presets.
- 2026-09-25 audit found M147–M172 and the inspector's effect toggles were
  UI-only shells — rewired to real processing; audit of remaining edit
  surfaces continues.
- Shipped earlier: Auto Cut (Silero VAD silence stripping), on-device Whisper
  auto-captions (Hindi readable, ~1-in-5 spelling fixes), transcript editing
  (delete words to cut), 12x faster demo export, scopes (RGB parade, zebras,
  false colour), frame-exact scrub, pinch zoom, clip virtualization (150-clip
  projects), curve editor, color grading with luma scope, caption system
  (SRT/WebVTT roundtrip, karaoke cues), encrypted-at-rest project vault.

## Decisions
- On-device Whisper closed the #1 gap vs CapCut.
- Auto-removing "um"s parked (it cut real words).

## Open items
- [ ] Realtime export audio truncation bug.
- [ ] Proxy transcodes, pan/EQ automation, codec breadth.
- [ ] Pro color/audio finishing; the AI + touch layer meant to beat CapCut.
- [ ] Design and mobile remain the front of the queue (Vansh 09-18).

## Grades
- 2026-09-19: PASS on the deployed site — Auto Cut inference, real 36s VP9
  export, encrypted vault all verified.
