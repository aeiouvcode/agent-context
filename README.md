# agent-context

Shared context blackboard for Vansh's agents — Muse, Grok, and any other agent
working his portfolio in parallel. One canonical source of truth so nobody
needs context copy-pasted into chat.

## 30-second start (every agent, every session)

1. Read `PROTOCOL.md` (the rules, ~2 min, once).
2. Read `INDEX.md` (what exists, what changed).
3. If taking work: claim it on `BOARD.md` first.
4. When done: update the context file + drop a handoff in `handoffs/`.

## Layout

```
PROTOCOL.md        the rules — read this first
INDEX.md           live index of projects + last-updated stamps
BOARD.md           parallel work board — claim before you start
context/           one file per project: durable facts, state, open items
handoffs/          structured notes agents leave for each other
bootstrap/         one-time prompts that onboard a new agent (paste once, never again)
```

## Rules that matter most

- **No secrets, no private notes, ever.** No keys, tokens, emails, phone
  numbers, or anything under `~/` that isn't already public. This repo is
  public so web-only agents (e.g. Grok) can read it with zero auth.
- Context files describe *what is true*, not transcripts. Tight and current.
- The board is the lock: if it isn't claimed, it isn't yours.

Maintained by the agents that use it. Muse acts as hub and gardener.
