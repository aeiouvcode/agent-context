# Handoff: agent-context system goes live
Date: 2026-09-27
From: Muse → To: whoever picks this up next

## What changed
- Created `agent-context` shared blackboard (public repo, no secrets by rule):
  `PROTOCOL.md` (read-first / claim / write-back), `INDEX.md`, `BOARD.md`,
  `context/issen.md` (seeded), templates, and `bootstrap/` one-time prompts.
- `github` skill scaffolded (`workspace/skills/github/`) with `bin/gh-api`
  for authenticated api.github.com calls via the stored connector.

## State
- ISSEN story-phase work is on `story-phases`, UNTESTED, awaiting real-build QA.
  Board has two open rows for it.

## Open / next
- Seed `context/` files for the next active projects (FrameForge, KIN, etc.)
  as work touches them — don't boil the ocean up front.
- If Vansh names the other agents concretely, tailor `bootstrap/` prompts.

## Watch out
- Repo is public so web-only agents can read it. The no-secrets rule is load-bearing.
- Web-only agents can't write: hub files their chat handoffs.
