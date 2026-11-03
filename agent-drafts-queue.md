# Agent drafts queue

[Token Effort](https://pyrolistical.github.io/token-effort/) · [Markdown](https://pyrolistical.github.io/token-effort/agent-drafts-queue.md)

![Grid of draft editors grouped by provider, with fake data](https://pyrolistical.github.io/token-effort/agent-drafts-queue.9cde149197c8e5f1.png)

Keep your agents working through a queue while you are away

- Write drafts for each provider
- One agent per provider works through its drafts in order
- Finishing a draft clears it and starts a fresh session on the next
- Agents resume automatically after usage resets

## Implementation

- The queue is a tmux pane grid of Neovim editors
- `draft next` command
  - Prints the calling agent's first pending file path
- `draft done` command
  - Clears the draft through its editor
  - Starts a fresh `do draft` session when more remain
- `do draft` agent skill
  - Run `draft next` and read the file. If it prints no path, report that no drafts remain and stop
  - Do the draft
  - Run `draft done FILE` as your final tool call
- `tmux respawn-pane`
- `tmux paste-buffer`
- `at` jobs
- Scheduled usage checks
  - Claude: `https://api.anthropic.com/api/oauth/usage`
  - Codex: `codex app-server` `account/rateLimits/read`

## Polish

- Drafts
  - Autosaving editor grid
  - Live reload from disk
  - Late-bound contents
  - Whitespace counts as empty
  - Skip drafts needing an offline host
- Completion
  - Record draft and referenced file versions on first read
  - Compare versions on `draft done`
  - Refuse once on change, then accept after review
  - Hash editor buffer against read draft
  - Rename by typing `/rename TITLE` into the agent's own pane
- Resuming
  - When usage runs out, schedule `continue` for after it resets
  - Send early if usage returns first
  - Resend after server overload, such as `payload.error.codex_error_info: "server_overloaded"` on the last entry of `~/.codex/sessions/*.jsonl`

## Related

- [Mirror tmux agents](https://pyrolistical.github.io/token-effort/mirror-tmux-agents.html)

Last modified 2026-11-02
