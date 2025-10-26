#tmux #session #neovim #terminal 

## 📌 What is `tmux`?

`tmux` stands for **Terminal Multiplexer**. It allows you to:

* Run multiple terminal sessions within one terminal window
* Detach from a session and reattach later
* Split the terminal window into multiple panes
* Persist sessions even after disconnection

---

## 🎯 Why Use `tmux`?

`tmux` solves several problems for developers, sysadmins, and terminal users:

* Keep long-running processes alive after SSH disconnection
* Organize tasks into multiple windows/panes
* Avoid having dozens of terminal tabs open
* Enable session sharing (useful for pair programming or support)
* Make your terminal workflow more productive

---

## 🧠 Philosophy of `tmux`

* **Persistence**: Your sessions and processes continue even if the terminal closes.
* **Modularity**: Organize work into sessions, windows, and panes.
* **Efficiency**: Perform many tasks from the keyboard, without leaving the terminal.
* **Customizability**: tmux is highly configurable with themes, plugins, and keybinds.

---

## 🧱 Core Concepts

| Concept | Description                                    |
| ------- | ---------------------------------------------- |
| Session | A full workspace that can have many windows    |
| Window  | Like a tab, contains one or more panes         |
| Pane    | Subdivision of a window, like a split terminal |

---

## 💡 Basic Commands (Run in shell)

```bash
tmux                # Start a new tmux session
tmux new -s name    # Create session with a custom name
tmux ls             # List all sessions
tmux attach -t name # Attach to a session
tmux kill-session -t name  # Kill a specific session
tmux kill-server    # Kill all tmux sessions
```

---

## ⌨️ Default Keybinds (Prefix: `Ctrl+b`)

Almost all commands in tmux start with the **prefix key**, which is `Ctrl+b` by default.

| Action                       | Keybind (After `Ctrl+b`)          |
| ---------------------------- | --------------------------------- |
| **Help (show all keybinds)** | `?`                               |
| Create new window            | `c`                               |
| Switch window                | `n` (next), `p` (previous)        |
| Rename window                | `,`                               |
| Close current pane           | `x`                               |
| Split pane vertically        | `%`                               |
| Split pane horizontally      | `"`                               |
| Move between panes           | Arrow keys or `o`                 |
| Resize pane                  | `Ctrl+b` then hold `Ctrl` + Arrow |
| Detach session               | `d`                               |
| Reattach session             | `tmux attach` or `tmux a`         |
| List sessions                | `tmux ls`                         |
| Kill pane/window/session     | `x`, `&`, or `tmux kill-...`      |

---

## 🧪 Examples

### Start and detach

```bash
tmux new -s dev
# do some work...
Ctrl+b then d  # detach safely
```

### Reattach

```bash
tmux attach -t dev
```

### Kill a session

```bash
tmux kill-session -t dev
```

---

## 🔧 Customization Example (`~/.tmux.conf`)

```bash
# Set prefix to Ctrl+a (like GNU Screen)
unbind C-b
set -g prefix C-a
bind C-a send-prefix

# Enable mouse support
set -g mouse on

# Easier pane switching
bind -n C-h select-pane -L
bind -n C-j select-pane -D
bind -n C-k select-pane -U
bind -n C-l select-pane -R

# Use vi keys in copy mode
setw -g mode-keys vi

# Set better colors
set -g default-terminal "screen-256color"
```

Reload config without restarting:

```bash
tmux source-file ~/.tmux.conf
```

---

## 🧩 Useful Plugins (via [tpm](https://github.com/tmux-plugins/tpm))

Install `tpm` to manage tmux plugins:

```bash
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

Then in your `~/.tmux.conf`:

```bash
# List of plugins
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'
set -g @plugin 'tmux-plugins/tmux-resurrect'
set -g @plugin 'tmux-plugins/tmux-continuum'

# Initialize TMUX plugin manager
run '~/.tmux/plugins/tpm/tpm'
```

Reload and install with:

```bash
Ctrl+b then I  # (capital i)
```

---

## ✅ Summary

* `tmux` is a must-have tool for terminal users
* It helps organize workflows and boosts productivity
* Sessions, windows, and panes let you structure your tasks
* Customizable via config and plugins
* Great for remote work, scripting, and dev environments
