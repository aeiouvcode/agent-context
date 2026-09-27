# Protocol — agent to agent context transfer

Every agent working Vansh's portfolio follows this. It replaces
copy-pasting context into chat.

## 1. Cold start (every session, before any work)

1. Fetch `INDEX.md`. Note `last-updated` stamps.
2. Fetch the `context/<project>.md` files for whatever you're touching.
3. Fetch `BOARD.md`. Do not start unclaimed work that overlaps an active claim.

One fetch of INDEX + the files you need replaces the whole paste.

## 2. Parallel work — the board is the lock

`BOARD.md` has one table: `| task | agent | status | updated | note |`.

- **Claim:** add your row (or flip `open` → `claimed`) and commit *before*
  starting. Status values: `open`, `claimed`, `in-progress`, `blocked`, `done`.
- **Collision:** if the task you want is `claimed`/`in-progress` by another
  agent, pick something else or leave a note in its row. Never duplicate work.
- **Release:** flip to `done` (or back to `open`) when finished, with a
  one-line note pointing at the handoff.

If you cannot write to the repo (web-only agent): announce your claim in
chat in the exact row format and the hub files it.

## 3. Writing back (every session that changed something)

- Update the relevant `context/<project>.md`: facts, state changes, decisions.
  Keep it tight — durable truth, not a transcript.
- Drop a handoff in `handoffs/YYYY-MM-DD-<slug>.md` using
  `handoffs/_template.md`. Whoever picks this up next reads the handoff, not
  the chat log.
- Bump the `last-updated` stamp in `INDEX.md`.

## 4. What goes where

| Content | Where |
|---|---|
| Durable project facts, current state, open items | `context/<project>.md` |
| Who's doing what right now | `BOARD.md` |
| Session notes for the next agent | `handoffs/` |
| Grade of a build (PASS / PARTIAL / FAIL / UNTESTED) + evidence | the handoff, and `context/` state |

## 5. Hard rules

1. **No secrets, no private notes.** No API keys, tokens, passwords, emails,
   phone numbers, or personal identifiers. No Situation Monitor content.
   When in doubt, leave it out — the hub can hold the sensitive half
   out-of-band.
2. **Don't rewrite another agent's claim.** Comment in its row instead.
3. **Small commits, clear messages.** One logical change per commit.
4. **Stale rows die.** A claim older than 48h with no update is fair game —
   note the takeover in the row.
5. **This repo never deploys anything.** It's context only. Deploys still
   need Vansh's explicit go, per project.

## 6. Roles

- **Hub (Muse):** full read/write, files other agents' handoffs, gardens
  INDEX/BOARD, resolves conflicts.
- **Peer agents (repo access):** read/write, follow the protocol.
- **Web-only agents (no repo access):** read via public URLs, follow the
  protocol for claims/handoffs in chat; the hub files them.
