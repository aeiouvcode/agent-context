# Work board

The lock for parallel work. Claim before you start; release when done.
See `PROTOCOL.md` §2.

| task | agent | status | updated | note |
|---|---|---|---|---|
| ISSEN story-phases: run `autoplay-phase=1..5` captures on a real Godot build | open | open | 2026-09-27 | code review only so far; needs device/real-build QA. Renamed HITOFURI 2026-09-27 (owner; store collision) - see handoffs/2026-09-27-issen-renamed-hitofuri.md. |
| ISSEN story-phases: merge to `godot-take` after QA passes | open | open | 2026-09-27 | needs Vansh's go. Renamed HITOFURI 2026-09-27 (owner; store collision) - see handoffs/2026-09-27-issen-renamed-hitofuri.md. |
| Seed context/ for Instinct-side live projects + announce on board | Instinct | done | 2026-09-27 | 13 projects seeded; see handoffs/2026-09-27-instinct-on-board.md |
| ISSEN: evaluate scene-shader uniform appetite (GLES3 floor 224; shader wants >261) | open | open | 2026-09-27 | apk-smoke evidence; see handoffs/2026-09-27-issen-shader-uniform-finding.md. Comment (Instinct, 2026-09-27): explained as instrument artifact - gate renderer recalibrated swiftshader->angle_indirect; control + real builds both green (runs 36316454914, 36316455894); see handoffs/2026-09-27-issen-smoke-gate-recalibrated.md |

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

**Relay mechanics (set 2026-09-27):** agent sandboxes have no GitHub token, so
no agent can git-push directly. At each task/milestone completion the working
agent creates a git bundle (`git bundle create <name>.bundle <base>..<branch>`,
or `--all` for a first mirror) and attaches it to main; main relays it to
Instinct, which verifies the bundle SHA-256, applies it, and pushes the real
branch ref to the backup repo with the poincaré token. The push recreates the
bundle's objects byte-identical via the Git Data API, so the commit SHAs on
the backup repo are the true ones (verified by sha-chain match at readback).
Report the bundle SHA-256, base, tip, and target branch with every relay.

### Repo map

| project | work source | backup repo (private) |
|---|---|---|
| KIN - living koi pond | kin-living-pond | kin-backup |
| Aurelia / Swan Lake | aurelia | aurelia-backup |
| Toro-wan | local-only (rebuilding) | toro-wan-backup |
| HITOFURI - was ISSEN (godot + web) | hitofuri | hitofuri-backup (godot-take mirrored 2026-09-28, tip 5440c8e0) |
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
| Calm app (Hushfield lofi) | local (queued) | calm-app-backup |
| Asset-stage pipeline | local (recovered v1) | asset-stage-backup |
| Synthesis (64-piece checkpoint) | local (checkpoints) | synthesis-backup |
| TALUS | local (checkpoints) | talus-backup |
| TILTH (Godot farm) | local | tilth-backup |
| LOW TIDE | local | low-tide-backup |
| LOW TIDE MAIL | local | low-tide-mail-backup |
| STILLFRAME | local | stillframe-backup |
| Open Muse | open-muse | open-muse-backup |
| FRAME ZERO | local | frame-zero-backup |
| Ljusvik | local | ljusvik-backup |
| Patiala Flatball | local | patiala-flatball-backup |
| Temp Mail | local | temp-mail-backup |
| Tidemill | local | tidemill-backup |
| Tiny Patiala | local | tiny-patiala-backup |
| Vargmyra | local | vargmyra-backup |
| agent-context | agent-context | agent-context-backup |

First mirrors seeded 2026-09-27 via GitHub Importer (full revision history).

## 2026-09-27 16:35 IST - CI keystore pin + relay mechanics (backup operator)

- FOR ISSEN AGENT: pin ONE CI keystore for the apk build workflow. The debug keystore is currently minted per run, so every CI APK carries a different signing cert (v0.19.1 ci-smoke cert sha256 cc968f6da0a18b4637faa715c3e269ba7c6871d433a271c048bcf4d0dfc129fb; trim cert 9564d7e7ecb5b891a02cdaca200d9e9c59250b47b90a36fc8d845a27fa88f5c9). Different certs = INSTALL_FAILED_UPDATE_INCOMPATIBLE between CI builds on the owner phone. Commit one debug keystore (or use a repo secret) and sign every CI build with it.
- Relay mechanics: GitHub create-tree accepts entries referencing nonexistent subtrees and returns the sha WITHOUT persisting the object - create trees LEAVES-FIRST or the commit 422s "Tree SHA does not exist".
- Relay mechanics: REST GET normalizes commit dates to Z, but the raw tz string is part of the commit hash - byte-identical recreation needs the raw offset from cat-file. Bundle-sourced commits carry their own dates and are unaffected.

## 2026-09-27 19:05 IST - ISSEN renamed HITOFURI (owner decision)

- The ISSEN game is now HITOFURI. Reason: "ISSEN: Samurai Slash" (PixelRyu)
  occupies the name on the iOS App Store + Google Play (same one-cut sumi-e
  concept); "Ninja Issen" is on Steam. HITOFURI (一振り, "one swing") was
  clear on all three stores.
- Repo aeiouvcode/issen KEEPS its name for now: a rename would break links,
  CI references, and live release URLs (dbgprobe-v3 probe in use).
- Details: handoffs/2026-09-27-issen-renamed-hitofuri.md
