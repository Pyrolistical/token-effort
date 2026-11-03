# Mirror tmux agents

[Token Effort](https://pyrolistical.github.io/token-effort/) · [Markdown](https://pyrolistical.github.io/token-effort/mirror-tmux-agents.md)

![Agent list beside an open agent, with fake data](https://pyrolistical.github.io/token-effort/mirror-tmux-agents.65fac3952a753aaf.png)

Control all your agents across providers from one interface on the go

- List every coding agent running in tmux
- Mirror agents' screens live
- Send agents messages
- Typing and scrolling feel local, with the agent catching up behind them

## Implementation

- `tmux list-panes`
- `tmux capture-pane`
- `tmux send-keys`
- WebSocket
- PWA
- Hot reloading
- Latency compensation
  - Predictive local echo
  - Compositor-style scrolling

## Polish

- Home
  - Provider usage
  - Usage reset countdown
  - New agent button
  - Working spinner
  - Unseen highlight
  - Empty session label
  - Queued message countdown
  - Swipe to close
  - Swipe to clear
- Navigation
  - Slide transitions
  - Swipe back
  - Unseen count
  - Reopen last agent
- Screen
  - Fit pane to viewport
  - Spinner until a new pane has text
  - Restore pane size
  - Follow keyboard height
  - Flicker-free redraws
- Touch
  - Tap as mouse click
  - Tap toggles keyboard
  - Drag to move cursor
  - Long press to copy
- Typing
  - Native text field overlay
  - Esc, tab, @ and newline keys
  - Image upload and paste
- Scrolling
  - Client-side scrollback
  - Cached image tiles instead of raw text
  - Momentum scrolling
  - Rubber band overscroll
  - Pinned prompt
- Connection
  - Offline cache
  - Offline indicator
  - Input queue across reconnects
  - Client error reporting

## Related

- [Agent drafts queue](https://pyrolistical.github.io/token-effort/agent-drafts-queue.html)

Last modified 2026-11-02
