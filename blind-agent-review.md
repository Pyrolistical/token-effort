# Blind agent review

[Token Effort](https://pyrolistical.github.io/token-effort/) · [Markdown](https://pyrolistical.github.io/token-effort/blind-agent-review.md)

Get independent reviews of a commit from several agents

- Several agents review the same commit unattended
- Each review is independent
- All reviews are compared together

## Implementation

- `git worktree add --detach` per reviewer
- Temporary `HOME` per reviewer
  - Claude: `claude -p` with a `claude setup-token` token
  - Codex: `codex exec` with the login linked in
- Atomic `rename` into an inbox directory
- systemd path unit with `DirectoryNotEmpty=` starting a root service
- Reviews kept under `/root`
- `runuser` to hand them back
- BEL character

## Polish

- Isolation
  - Copy global instructions, settings and hooks into each home
  - Remote Control off
  - Temporary files inside the home
  - Delete checkout and home after each reviewer and on interrupt
  - No output on the terminal
- Collection
  - Accept only single-link regular files with expected names, within size and time limits
  - Keep a reviewer's second file under a timestamp
  - Install root's copies by hand, not from the checkout
  - Start the next reviewer after collection
- Rounds
  - Name by local start time
  - Record instructions, commit and each reviewer's outcome outside scratch
  - Read the token at a child shell prompt
  - Bell when the last reviewer ends
  - Continue past a reviewer that fails or writes nothing
  - Refuse to start over leftovers, an unread inbox, a stopped collector or a missing login

## Related

- [Agent drafts queue](https://pyrolistical.github.io/token-effort/agent-drafts-queue.html)
- [Mirror tmux agents](https://pyrolistical.github.io/token-effort/mirror-tmux-agents.html)

Last modified 2026-11-03
