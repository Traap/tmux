# tmux

Personal tmux configuration for terminal work across Linux, Ghostty, Windows
Terminal with WSL, SSH sessions, and Neovim.

## What this config does

- Uses `Ctrl-Space` as the tmux prefix instead of the default `Ctrl-B`.
- Keeps a fallback prefix sender on `prefix b`, which is useful inside nested
  tmux sessions.
- Enables mouse support and tmux clipboard integration by default.
- Adds `prefix m` and `prefix M` to turn mouse support on and off.
- Uses `tmux-256color` and declares RGB support for `xterm-256color`,
  `ghostty`, and `kitty`.
- Keeps 10,000 lines of scrollback history.
- Sets `escape-time` to `0` for faster key response.
- Starts window and pane indexes at `1` and automatically renumbers windows.
- Reloads the config with `prefix r`.
- Splits panes from the current pane path:
  - `prefix j` creates a vertical split.
  - `prefix l` creates a horizontal split.
- Resizes panes one cell at a time with repeatable arrow-key bindings.
- Creates new sessions with `prefix n`.
- Configures `tmux-fzf-session-switch` on `prefix f` for session-only fzf
  switching without previews.
- Preserves `Ctrl-L` redraw behavior through a secondary binding.
- Enables focus events for terminal applications that react to focus changes.
- Shows visual activity notifications.
- Uses a compact custom status bar with host, operating system, session,
  window, pane, uptime, date, and time.
- Uses vi-style copy mode.
- Integrates copy and paste with the system clipboard through `xclip`.
- Enables OSC 52 clipboard forwarding so remote Neovim yanks can reach the
  local clipboard when the terminal supports it.
- Loads optional tmux bindings from `$SESSION_BINDINGS_HOME/tmux.conf` when
  that environment variable is set and the file is readable.
- Manages plugins with TPM.

## Key bindings

| Binding | Action |
| --- | --- |
| `Ctrl-Space` | tmux prefix |
| `prefix b` | send prefix to a nested tmux session |
| `prefix m` | enable mouse support |
| `prefix M` | disable mouse support |
| `prefix r` | reload `~/.tmux.conf` |
| `prefix j` | split pane vertically in the current path |
| `prefix l` | split pane horizontally in the current path |
| `prefix Left` | resize pane left |
| `prefix Down` | resize pane down |
| `prefix Up` | resize pane up |
| `prefix Right` | resize pane right |
| `prefix n` | create a new session named `Bash` |
| `prefix f` | switch sessions with fzf |
| `prefix Space` | enter copy mode |
| `v` in copy mode | begin selection |
| `Ctrl-v` in copy mode | toggle rectangle selection |
| `y` in copy mode | copy selection to system clipboard |
| mouse drag in copy mode | copy selection to system clipboard |
| `prefix p` | paste from system clipboard |

## Plugins

The config uses TPM and declares these plugins:

- `tmux-plugins/tpm`
- `tmux-plugins/tmux-yank`
- `christoomey/vim-tmux-navigator`
- `vndmp4/tmux-fzf-session-switch`

Install TPM first, then press `prefix I` inside tmux to install plugins.

## Requirements

- `tmux`
- `xclip` for the configured Linux clipboard copy and paste bindings
- `fzf` for session switching through `tmux-fzf-session-switch`
- A terminal with RGB and clipboard support for the best color and clipboard
  behavior

## Notes

This repository is the source of truth for the tmux config. The active tmux
configuration is expected to be linked into the user's tmux config location.
