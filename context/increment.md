# INCREMENT — life-aboard astronaut simulator

Realistic astronaut-life sim: five station days on Houston's timeline —
procedures, CO2 limits, exercise, consumables.

## Facts
- Live at `aeiouvcode.github.io/increment` (Godot-first, per the standing
  game-engine direction).
- Hero view is 4-layer WebGL parallax, not a Gaussian splat.

## Current state
- Live since 2026-09-23 22:28.
- After Vansh's note that the hero scene "feels more like a comic": the
  station now moves on its own — second crew member, idle tumbles, blinking
  racks.
- Included in the 09-27 batch go-live; live tip 5eb65acf (gauge + header
  repaint optimization) 2026-09-28.
- Local-only branch splat-module-local (static landing hero within a
  visible frame window) mirrored to increment-backup 2026-09-28; not live.

## Decisions
- Godot-first (Vansh's standing direction for games).

## Open items
- [ ] On-device verdict pending.

## Grades
- UNTESTED on device.
