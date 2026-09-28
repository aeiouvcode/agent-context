# Open Muse

Open-source, local-first personal-agent web app (BYO key, zero backend).
Recurring self-improvement build loop run by Instinct.

## Facts
- Repo: `github.com/aeiouvcode/open-muse` — live at `aeiouvcode.github.io/open-muse/`.
- Static app; Gemini is the default provider; live model catalog is read when a
  key is saved (17 current ids as offline fallback). On-device engine option via
  the EDGE//AI bridge (verified live).
- Privacy cloak: synthetic twins substituted before anything leaves the device;
  verified against real provider traffic (provider only ever saw twins).
- Bar: works out of the box with a real key; honest PASS/PARTIAL/FAIL; 390px
  phone-first design QA; hostile-critic gate X/10, bar 8, before any ship.

## Current state
- **2026-09-27:** gens 20–31 live on Pages — multi-conversation sessions,
  checkpoints + fork, retry variants, PWA install, model hub with HuggingFace
  community search and resumable downloads, memory benchmark, Observe/Ask/Auto
  permission modes, backup import preview + merge.
- Gens 32 + 33 LIVE on Pages 2026-09-28 (tip 07eeea93, batch go-live;
  Pages md5-verified). Gen 32: PII sentinel fixture matrix (fail-loud),
  web-search cloak, PAN/Aadhaar detectors. Gen 33: private File QA build
  (revision filerevision-01M3JP1PZ0FHHDRT8N0H9TD5T0), critic 8/10 round 1.
- Competitive frame: LibreChat and Jan. Deliberately not chasing microVMs or
  agents that run while closed.

## Decisions
- 2026-09-24: benchmark plan vs LibreChat/Jan — multi-conversation sessions,
  checkpoints/fork, shareable workforce templates, per-agent sandbox scopes, PWA.
- Modes: Agent | Chat | Coder three-way segment; Coder has an inspect-only Plan
  mode (from the minimax-code port).

## Open items
- [ ] Deploy gen 32+ to Pages (needs Vansh's go).
- [ ] Name decision with Vansh: CopilotKit shipped an unrelated "OpenMuse"
  (server-side agent shell) on 09-22 — keep or rename is open.
- [ ] Coder-mode benchmark harness (planned next move; T3 Code is the
  test-harness reference Vansh sent).

## Grades
- 2026-09-27 — gen 32: PASS on local QA (sentinel matrix fail-loud, cloak
  verified); not yet public.
