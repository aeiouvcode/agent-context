# Work board

The lock for parallel work. Claim before you start; release when done.
See `PROTOCOL.md` §2.

| task | agent | status | updated | note |
|---|---|---|---|---|
| ISSEN story-phases: run `autoplay-phase=1..5` captures on a real Godot build | open | open | 2026-09-27 | code review only so far; needs device/real-build QA |
| ISSEN story-phases: merge to `godot-take` after QA passes | open | open | 2026-09-27 | needs Vansh's go |
| Seed context/ for Instinct-side live projects + announce on board | Instinct | done | 2026-09-27 | 13 projects seeded; see handoffs/2026-09-27-instinct-on-board.md |
| ISSEN: evaluate scene-shader uniform appetite (GLES3 floor 224; shader wants >261) | open | open | 2026-09-27 | apk-smoke evidence; see handoffs/2026-09-27-issen-shader-uniform-finding.md |

Status: `open` `claimed` `in-progress` `blocked` `done`.
A claim older than 48h with no update is fair game — note the takeover.

## Standing rule: private backup mirrors (set by Vansh 2026-09-27)

Every active project has a private `<slug>-backup` repository on aeiouvcode.
The moment an agent completes a task or milestone on a project, it mirrors its
work to that project's backup repo - event-based, not on a clock ("let the
agent backup every single point where it completes a task"). Public repos stay
untouched; backups are private and invisible to the world. If you start work
on a project with no backup repo, create it (private, `<slug>-backup`) before
your first push.

### Repo map

| project | work source | backup repo (private) |
|---|---|---|
| KIN - living koi pond | kin-living-pond | kin-backup |
| Aurelia / Swan Lake | aurelia | aurelia-backup |
| Toro-wan | local-only (rebuilding) | toro-wan-backup (awaits first mirror) |
| ISSEN (godot + web) | issen | issen-backup |
| SKYTETHER (web + godot) | skytether | skytether-backup |
| FrameForge | frameforge-studio | frameforge-backup |
| Vani | vani | vani-backup |
| EDGE//AI | edge-ai | edge-ai-backup |
| OUTWARD (arrows) | outward | outward-backup |
| Compression engine | local harness | compression-engine-backup (awaits first mirror) |
| INCREMENT (astronaut sim) | increment | increment-backup |
| KEEP THE LIGHT | keep-the-light | keep-the-light-backup |
| Folio | Instinct File | folio-backup (awaits first mirror) |
| Rock-collector game | local (in progress) | rock-collector-backup (awaits first mirror) |
| Calm app | local (queued) | calm-app-backup (awaits first mirror) |
| agent-context | agent-context | agent-context-backup |

First mirrors seeded 2026-09-27 via GitHub Importer (full revision history).
