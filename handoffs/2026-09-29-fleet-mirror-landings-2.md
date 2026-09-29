# 2026-09-29 fleet mirror landings, session 2 (Instinct relay operator)

Author: Instinct (backup-fleet relay operator). Count correction (same-day
follow-up): the session was 54 relay jobs landing 53 refs across 19 private
backup repos (one job objects-only), not 49/20 as the board section first
said. Covers main-relayed bundles
and tars from 2026-09-28 ~18:50 IST to 2026-09-29 ~05:40 IST. Every landing
below was verified by an authenticated no-store GET of the ref after the
write; bundle/tar SHA-256s were verified against main's relay notes before
any push.

## Landings (final tips per repo)

| backup repo | ref | tip | note |
|---|---|---|---|
| tilth-backup | master | 7d5b53c06eb9a165fb58460bb6db7be99469464a | chain v2.22 -> v2.26 web + Godot v0.17 -> v0.21, 8 ff landings |
| aurelia-backup | improve/klatt | be1b47e7cdbbf4915e50fc4c612983a8d12fd80d | chunk-8 brass (r3.1 twins + merge), chunk-8b Vc, chunk-8c timpani, chunk-8 r1 strings; see twin section |
| aurelia-backup | meta | 14fa9b4539135710cc01c23fc4c4734de5e00262 | MAPPING.md, chunk-8 section |
| kin-backup | godot-prototype | b731869e26361a175ce85c3ecf5f61f17481467a | c113 -> c120, 8 ff landings |
| increment-backup | mission-causality-local | 2248cb5bf61e786ef4abb942d35f7909eefc08fb | 3 ff landings |
| synthesis-backup | master | c5faffb97b7970dbfa4c934277a47becd0044270 | checkpoints N -> S, 6 ff landings |
| money-tools-backup | main | 8720bd972698d24a6182a77e371398be78e41893 | batches 2+3, 18 tools; go-live held for owner's Oct 5 window |
| cell-sim-backup | main | 29a655120682aaa821d3e524f3cfb9ad9304481b | v0.7, supersedes v0.5 |
| sumi-e-backup | godot-take | b49c2ba1ffe02b4cfce664171493b060a2e39525 | NEW repo; 431-commit unsigned twin line of the full signed hitofuri/sumi-e history |
| sumi-e-backup | meta | f179a2dbdd07189a06ac253a1412c844e85e87d2 | MAPPING.md, 190 mappings, root commit |
| hitofuri-backup | godot-take | d15b9aea4df7b72997d44b60fde9cdc5d85b9231 | frozen; see divergence note |
| asset-stage-backup | main | 5ee7c67cbc6555ac4c99513a16c317263e993059 | |
| v15-cctv-backup | main | d40e414e8a57cdb251db52cb9422c5ee4ef028c1 | |
| ee-backup | master | ba11ec95fc15803db4c6a4c4e3caae322cc730b9 | 2 landings |
| vani-backup | main | cf66e883be0a6580a90c4ebe2f417bd3a79d1e1b | 4 ff landings |
| outward-backup | main | 3b3b2ed9ef2882d9d8fd970c142d48a29ff46642 | |
| reality-js-backup | main | 1b70a691173c8c492ec2819b2950f8dff3cdea7e | |
| three-bells-backup | main | d3a77ef4a3e2e10790c2380487ee9ddf84346415 | |
| skytether-backup | godot | e326a083de4658e79bd9538e5c263958064bcd88 | |
| keep-the-light-backup | main | 4add605bfac31e44fbe0c80823d65fdeac895ea8 | |
| low-tide-backup | main | 12ca29dca8706b32cc4108e519965e51723abcf5 | |

## hitofuri-backup vs sumi-e-backup: divergence is BY DESIGN

- hitofuri-backup godot-take sits at d15b9ae with the original unsigned
  commit shas from the early mirror.
- sumi-e-backup godot-take (b49c2ba1) is the unsigned TWIN line of the full
  signed 431-commit history (gpgsig stripped, parents remapped
  recursively); MAPPING.md on refs/heads/meta maps real -> twin.
- These two lines cannot be unified without either force-moving
  hitofuri-backup or rewriting sumi-e-backup. Per main 2026-09-29 02:41,
  the owner's standing rule is never delete anything in his accounts, so
  hitofuri-backup stays as-is (frozen at d15b9ae) and sumi-e-backup is the
  live mirror going forward. Recorded here so the divergence is honest and
  intentional, not drift.

## aurelia-backup twin-line mechanics this session

The remote carries the signature-stripped twin line from a72305c onward
plus supersede-merges. New builder commits land as unsigned twins
(identity/message preserved, parents remapped) followed by a
supersede-merge (tree = intended content, parents = [twin, previous tip],
fleet identity). Every merge sha was precomputed locally and matched
GitHub's creation byte-for-byte. Chain this session: 2fb51f07 (chunk-8)
-> 4310d4b5 (8b) -> 17414485 (8c) -> be1b47e7 (8 r1).

## Open Muse

Gen 34 (9214197) is live at https://aeiouvcode.github.io/open-muse/; local
main is 5 ahead of origin/main. Go-live gate remains closed: nothing public
without the owner's explicit yes via main; PRIVATE Instinct File publishes,
commits, and QA continue.

## Relay mechanics addendum (this session)

- GitHub create-commit stores the message exactly as sent; precomputing the
  commit sha locally requires byte-exact message reproduction (a trailing
  newline mismatch shifts the sha).
- vault fill into a planted offscreen input fails; the staging input must be
  a visible labelled textbox (aria-label) addressed by its snapshot ref.
- Builder tars without git metadata land as full-tree snapshot commits with
  fleet identity and the source commit id + sha256 in the message.
