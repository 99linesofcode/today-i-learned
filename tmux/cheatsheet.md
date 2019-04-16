# TMUX

By default, `CTRL + B` is the default leader key combination.

| Screen         | Description                   |
| -------------- | ----------------------------- |
| `<leader> <c>` | Create a new screen           |
| `<leader> <,>` | Rename the current screen     |
| `<leader> <n>` | Focus the next screen         |
| `<leader> <p>` | Focus the previous screen     |
| `<leader> <w>` | List all screens              |
| `<leader> <%>` | Split the screen vertically   |
| `<leader> <">` | Split the screen horizontally |
| `<leader> <:>` | Execute a named command       |

| Windows        | Description                   |
| -------------- | ----------------------------- |
| `<leader> <%>` | Split the window vertically   |
| `<leader> <">` | Split the window horizontally |
| `<leader> <x>` | Kill currently active window  |

| Session                    | Description                    |
| -------------------------- | ------------------------------ |
| `tmux new -s <session>`    | Create a new named session     |
| `<leader> <d>`             | Detach from current session    |
| `tmux list-sessions`       | List all sessions              |
| `tmux attach -t <session>` | Re-attach to an active session |
