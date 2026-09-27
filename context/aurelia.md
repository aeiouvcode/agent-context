# Aurelia — realtime browser music synthesis engine

Generalist engine: tell it a song, it synthesizes and plays it with a live
score view. Not a MIDI player; scores are composed, never downloaded.

## Facts
- Repo: `github.com/aeiouvcode/aurelia` — the working build is the GitHub
  Pages deploy (audio is dead inside sandboxed file previews).
- Engine direction (Vansh, 09-26 21:28): abc.js notation as the source of
  truth (write the score, read notes back, play them — "like image to audio")
  + Fluid R3_GM + custom convolution reverb.

## Current state
- Lacrimosa: render 336s → 116s, deterministic; choir consonants sung as an
  ensemble; reverb has stage depth. Louder/deeper-hall pass cost dynamic
  range — the current gap.
- Swan Lake: rebuilt note by note against a public-domain Barbirolli/LPO
  reference after v2 was rejected. Melody must own the mix; more cinematic
  orchestra feel; deeper tone change at the 10s mark.
- A/B tests pending on Vansh's ear: tone (VSCO vs Fluid R3_GM) and hall
  (classic vs v2 frequency-dependent reverb); 09-27 he answered "keep both".

## Decisions
- 2026-09-23: written-score-first path (engraved score, notes light as they
  play, sampled instruments).
- 2026-09-26: notation-first engine direction per Vansh.

## Open items
- [ ] A/B evaluation on Vansh's ear (tone + hall).
- [ ] Dynamic range recovery after the louder/deeper-hall pass.
- [ ] Swan Lake from critic 8 toward 10.

## Grades
- Swan Lake (09-26/27): critic "deserves 8, can be improved to a 10".
- Lacrimosa: PARTIAL — choir weakest; volume/depth gap vs the YouTube
  reference.
