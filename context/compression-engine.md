# Compression engine — "better than the frontier"

World-class compression software; research/harness phase. Named top priority
among core projects by Vansh (09-25).

## Facts
- Shape: local library + CLI + WASM browser UI.
- Harness-first: the benchmark harness is built before any codec, so "better"
  becomes a published number. Covers zstd/brotli/xz with byte-exact roundtrip
  checks and time/memory tracking.
- Corpus: dated GH Archive slice from 2026-09-24.
- Bars to beat: brotli-11 at 13.4%, xz-9 at 13.6%, zstd-22 at 13.9% of
  original size.

## Current state
- Research finding (Instinct's, not yet confirmed by Vansh): no codec wins on
  everything — cmix/ts_zip win ratio but are impractical, zstd wins speed,
  xz/brotli win practical ratio.
- Proposed gap nobody fills: byte-exact, streaming log compression that
  tolerates schema drift and decodes in the browser.
- Neural archival judged a trap for now.

## Decisions
- Harness before codec (proposed; Vansh has not explicitly said go/no-go on
  harness-first).

## Open items
- [ ] Codec design phase, measured against the published bars.
- [ ] Confirm harness-first direction with Vansh.

## Grades
- UNTESTED — no codec to grade yet; harness numbers above are the baseline.
