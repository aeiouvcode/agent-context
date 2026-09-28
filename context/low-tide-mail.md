# LOW TIDE MAIL - personal mailbox kit

Personal mailbox on standard protocols, not a web API: Postfix (SMTP), Dovecot
(IMAP), Maildir on an operator-owned LUKS volume, stdlib-only Python client.
Local-only by default; no credentials or messages in Git.

## Facts
- Work source: local (bundles via relay).
- Backup: `aeiouvcode/low-tide-mail-backup` (private), `master`.

## Current state
- Mirrored v2 2026-09-28 (master tip 748e0962, supersedes v1).

## Decisions
- Backup mirror convention (owner, 2026-09-27/28).

## Open items
- [ ] None tracked on Instinct's side.

## Grades
- 2026-09-28: UNTESTED by Instinct (mirror operator only).
