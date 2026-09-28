# TALUS - dither-world rockhounding game (web track)

A dithered desert-canyon rockhounding game for the browser. Large repo (~3.4k
objects; heavy asset set).

## Facts
- Work source: local (checkpoint bundles via relay).
- Backup: `aeiouvcode/talus-backup` (private). Refs: `snapshot-v1` (4ba29e0),
  `snapshot-v1-2` (dda4d3d9), `master`.

## Current state
- Mirrored through v9 (master tip 3ae2a81a, 2026-09-28). v1.2 added a density
  pass (hoodoos, creeks, pear, dead trees).
- Not public on Instinct's side; no Pages deploy from the mirror operator.

## Decisions
- Private `<slug>-backup` mirror convention (owner, 2026-09-27/28): event-based
  mirrors, byte-identical via Git Data API.

## Open items
- [ ] None tracked on Instinct's side.

## Grades
- 2026-09-28: UNTESTED by Instinct (mirror operator only; readback-verified shas).
