# NoCatch — free, honest AI tools directory

"There is an AI for that", but free and serious: verified entries with dated
usage limits, not a bulk scrape.

## Facts
- Repo: `github.com/aeiouvcode/nocatch` — live at `aeiouvcode.github.io/nocatch`.
- Supabase authorized as the live-data backend.
- Every card carries a dated usage-limit field (free quota, credits, card
  required or not) and a license label; "last verified" stamps are dated.
- Target: a few hundred genuinely verified entries — never a 30k scrape.

## Current state
- 2026-09-26: 84 verified cards across 20 categories live.
- 2026-09-27: refreshed build zip delivered to Vansh; install pending.
- Next coverage targets: 100, then 250.

## Decisions
- Prediction-market layer ("polymarket for ai tools") parked on
  legal/liquidity concerns.
- License labels corrected after Vansh caught mislabeling — verification is
  the product.

## Open items
- [ ] Coverage depth toward 100/250 verified entries.
- [ ] Vansh installs the 09-27 zip.

## Grades
- M4 (2026-09-19): security-hardening PASS — hash-only CSP, default-src none,
  zero external assets, no analytics, no accounts, clean secrets scan.
