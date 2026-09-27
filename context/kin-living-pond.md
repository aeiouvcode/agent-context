# KIN — living koi/goldfish pond

Browser koi pond chasing RYUKIN (Masataka Hakozaki) as the grading reference.

## Facts
- Repo: `github.com/aeiouvcode/kin-living-pond`.
- Live surfaces: `/kin-living-pond/` (WebGL main), `/godot/` (koi bowl Godot
  build), `/next/` (Pond Next preview).
- Grading references: Hakozaki's RYUKIN (pinned by Vansh 09-21; pastel lavender
  bowl, silk veil fins per his X post) and the Play Store "Koi - Aquarium" app.
- Method: split fish lab + water lab (solo debug scene per fish with sliders
  before joining the pond) — the Hakozaki method. Water uses the Clearwater
  repo's caustics method.

## Current state
- **2026-09-27:** c77 koi build live at `/godot/` (commit `ded22f7` on
  `godot-prototype`, workflow build verified from the same commit). Root and
  `/next/` byte-unchanged in that deploy.
- Two-scene build (pond + bowl) is the live shape; KIN Pond Next QA'd and
  waiting on a live-switch go.
- Distance-to-reference audit vs Hakozaki drives the fix order.

## Decisions
- 2026-09-24: both koi pond and fish bowl scenes (Vansh's pick).
- True refraction and ray-traced bounce deliberately out for phone performance.

## Open items
- [ ] Close the remaining gaps vs Hakozaki: black fish fan density, fish
  anatomy, blossom field.
- [ ] KIN Pond Next live switch at `/next/` (needs Vansh's go).
- [ ] PWA packaging offered, not ordered.

## Grades
- KIN VII: PARTIAL+ vs Hakozaki (caustic filaments, chromatic fringe, fin
  deformation in; refraction out by decision).
- c77 (2026-09-27): deployed and chain-verified; phone verdict pending.
