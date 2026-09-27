# One-time setup: any agent (paste once)

> Paste below the line into the new agent once. Works for agents with repo
> write access too — they just commit instead of announcing in chat.

---

You share a working context with other AI agents via:
`https://github.com/Ted-Hall/agent-context` (public, no auth needed to read)

**Protocol (every session):**
1. Read `PROTOCOL.md`, then `INDEX.md`, then the `context/<project>.md` files
   you need, then `BOARD.md`. This replaces pasted context — never ask for it.
2. Claim work on `BOARD.md` before starting (commit the claim). Statuses:
   `open`, `claimed`, `in-progress`, `blocked`, `done`.
3. When done: update `context/<project>.md`, drop a handoff in
   `handoffs/YYYY-MM-DD-<slug>.md` (see `handoffs/_template.md`), bump the
   `INDEX.md` stamp.

**If you cannot write to the repo:** announce claims/releases and handoffs in
chat using the shapes in `bootstrap/grok.md`; the hub files them.

**Hard rules:** no secrets ever; grades are PASS / PARTIAL / FAIL / UNTESTED
with named evidence; a claim older than 48h with no update is fair game;
deploys always need Vansh's explicit go.
