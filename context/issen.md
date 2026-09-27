# ISSEN 一閃

Sumi-e sword duel. Web build (Three.js, `main` branch) + Godot take
(`godot-take` branch) shipped to Android. You are the hub's current focus.

## Facts
- Web repo: `github.com/aeiouvcode/issen` — live at `aeiouvcode.github.io/issen/`.
- Godot source lives on the `godot-take` branch under `godot/` (scripts, art, shaders).
- Godot web export artifacts also on `main` under `godot/`.
- Bar: original working builds, PASS/PARTIAL/FAIL/UNTESTED with named evidence.
  Desktop QA is not phone proof. No deploys without Vansh's go.

## Current state
- **2026-09-27:** story-phase system implemented on branch `story-phases`
  (commits `bca67db`, `3dae5b4`, `3bbd725`, not pushed, not merged).
  - `godot/art/phases.json`: premise + 5 phases (Stranger, Teacher, Mirror,
    Truth, Issen) mapped to the 5 chapter boss duels.
  - Ring telegraph on boss windups; feints in phases 2–4; mirror echo in 3+;
    face resolves in 4; single-exchange finale + ending fork in 5.
  - Premise replaced: "The Man Beneath the Gate" is out; the memory premise
    ("You are already dead. This is the last second before it — replayed in ink.")
    is the approved story, per Vansh 2026-09-26.
  - QA hook: `godot -- --autoplay-phase=N` (N=1..5).
- **Grade: UNTESTED** — no Godot binary in this environment; code review only.
  Needs `autoplay-phase=1..5` captures on a real build before merge/deploy.

## Decisions
- 2026-09-26: five narrative phases map onto the five chapter boss duels;
  in-fight boss escalation (boss_phase 1–4) kept but gated per phase.
- 2026-09-26: phase 5 boss HP = 8 (weakest cut deals 9.6; 12 would not one-shot).

## Open items
- [ ] Run autoplay-phase captures on a real Godot build; verify ring, face, feints, epilogues.
- [ ] Merge `story-phases` → `godot-take` after QA (needs Vansh's go).
- [ ] v0.17 Android combat/story verdict on Vansh's phone (from earlier validation queue).
