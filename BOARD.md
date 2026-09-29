# Work board

The lock for parallel work. Claim before you start; release when done.
See `PROTOCOL.md` §2.

| task | agent | status | updated | note |
|---|---|---|---|---|
| ISSEN story-phases: run `autoplay-phase=1..5` captures on a real Godot build | open | open | 2026-09-27 | code review only so far; needs device/real-build QA. Renamed HITOFURI 2026-09-27 (owner; store collision) - see handoffs/2026-09-27-issen-renamed-hitofuri.md. |
| ISSEN story-phases: merge to `godot-take` after QA passes | open | open | 2026-09-27 | needs Vansh's go. Renamed HITOFURI 2026-09-27 (owner; store collision) - see handoffs/2026-09-27-issen-renamed-hitofuri.md. |
| Seed context/ for Instinct-side live projects + announce on board | Instinct | done | 2026-09-27 | 13 projects seeded; see handoffs/2026-09-27-instinct-on-board.md |
| Seed context/ for 2026-09-28 fleet additions (11 projects) | Instinct | done | 2026-09-28 | see handoffs/2026-09-28-fleet-context-seeds.md |
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
| HITOFURI - was ISSEN (godot + web) | hitofuri | hitofuri-backup (godot-take frozen at d15b9ae; see 2026-09-29 divergence note) |
| SUMI-E (hitofuri line, twin mirror) | local | sumi-e-backup (live mirror going forward, godot-take tip b49c2ba1 + meta MAPPING) |
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
| Money tools | local | money-tools-backup |
| Cell-sim | local | cell-sim-backup |
| v15 CCTV | local | v15-cctv-backup |
| Reality-js | local | reality-js-backup |
| Three Bells | local | three-bells-backup |
| Open Muse | open-muse | open-muse-backup |
| FRAME ZERO | local | frame-zero-backup |
| Ljusvik | local | ljusvik-backup |
| Patiala Flatball | local | patiala-flatball-backup |
| Temp Mail | local | temp-mail-backup |
| Tidemill | local | tidemill-backup |
| Tiny Patiala | local | tiny-patiala-backup |
| Vargmyra | local | vargmyra-backup |
| EE channel (narration) | local | ee-channel-backup |
| Fleet inventory (durable store) | local | fleet-inventory |
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

## 2026-09-29 05:45 IST - fleet mirror landings session 2 + sumi-e/hitofuri divergence note (backup operator)

- 54 relay jobs landing 53 refs across 19 private backup repos (one job
  was an objects-only upload), all readback-verified. Corrected count:
  the first version of this note said 49 landings across 20 repos.
  Final tips + full chain: handoffs/2026-09-29-fleet-mirror-landings-2.md
- TILTH chain reached web v2.26 + Godot v0.21; KIN c120; synthesis
  checkpoint S; increment 2248cb5b; aurelia chunk-8 round 1 (twin line).
- DIVERGENCE BY DESIGN: hitofuri-backup godot-take (d15b9ae, original
  unsigned shas) vs sumi-e-backup godot-take (b49c2ba1, unsigned twin line
  of the full signed 431-commit history). Per main 2026-09-29 02:41 the
  owner's standing rule is never delete anything in his accounts, so
  hitofuri-backup stays as-is and sumi-e-backup is the live mirror going
  forward. Details in the handoff.
- Open Muse gen 34 (9214197) live; go-live gate closed (nothing public
  without the owner's explicit yes via main).
- money-tools go-live held for the owner's Oct 5 window.

## 2026-09-29 23:12 IST - go-live batches + relay items 91-186 (backup operator)

- 20:03 batch (owner "go now, all"): Open Muse gen-37 live (7d67f3b);
  new public repos paperfold (619a84b) + micro-tools (66f0a27), Pages on;
  keep-the-light c132 live (d852791).
- 22:22 batch (owner "go live on all", WhatsApp, verified on channel):
  - PIXELFOLD v2: new public repo aeiouvcode/pixelfold (0ce1670), Pages
    live, flat static HEIC-to-JPG converter.
  - LOW TIDE v13: public main 2addea6 -> 2d882ae (replaces v3); live
    verified byte-exact against the item-173 mirror bytes.
  - TILTH web v2.41: public main 4031c320 -> 69d36d9; coherent tree with
    real filenames (TILTH agent's numbered staging files replaced); live
    verified byte-exact. Public repo keeps its web-only shape.
- New private repo qrfold-backup (QRFOLD v1 ba8f90b, v2 ca5e065;
  go-live held for owner yes, would deploy v2). tilth-backup gains a
  godot track branch (v0.36, 98deb39).
- reality-js-backup main 0e880e1: mesh8-mesh12 local candidates mirrored;
  index.html still loads mesh-v7.js throughout - nothing promoted, live
  stays mesh7 (df95e42 line public).
- kin-backup godot-prototype c136 (dce3c79, byte-exact replay);
  money-tools-backup batch 8 overlay (a7cfe5d, private only; money-tools
  public go-live still held for the owner's Oct 5 window);
  frame-zero-backup snapshot #9 (8155714); tilth-backup master web v2.42
  (72c15a2, local-only; live stays v2.41).
