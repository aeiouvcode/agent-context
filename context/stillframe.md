# Stillframe - private portrait editor prototype

Static TypeScript app: imports JPEG/PNG/WebP (25MB max), orientation-corrects,
resizes to 2400px long edge, light/color controls, crop, spot softening,
before/after, 12-step undo/redo, PNG export (canvas pixels, no EXIF carryover),
encrypted project files. Nothing persisted by the app.

## Facts
- Work source: local (bundles via relay).
- Backup: `aeiouvcode/stillframe-backup` (private), `master`.

## Current state
- Mirrored 2026-09-28 (master tip 2a06dc23).

## Decisions
- Backup mirror convention (owner, 2026-09-27/28).

## Open items
- [ ] None tracked on Instinct's side.

## Grades
- 2026-09-28: UNTESTED by Instinct (mirror operator only).
