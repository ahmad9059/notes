#cli #filemanager #rust #productivity


### What is Yazi?

**Yazi** is a modern, **blazingly fast terminal file manager** written in **Rust**. It's heavily inspired by **nnn**, **ranger**, and **fzf**, combining their strengths with a clean UI and strong keyboard-focused UX.

Yazi uses **TUI** (terminal user interface) and works well in both terminal emulators and TTYs. It’s designed for power users who prefer the keyboard and want highly customizable workflows.

---

## Philosophy

- **Speed**: Written in Rust with performance in mind.
- **Modal interface**: Like `vim`, it has modes (Normal, Select, etc.).
- **Minimalism + Power**: Minimal UI with powerful extensibility.
- **Keyboard-first**: You rarely need to touch the mouse.
- **Async file preview**: Previews images, videos, text, PDFs, etc.

---

## Installation

### Arch Linux (yay or paru):

```bash
yay -S yazi
```

### Cargo (Rust toolchain):

```bash
cargo install yazi-cli
```

### Debian-based:

Check releases on GitHub: [https://github.com/sxyazi/yazi](https://github.com/sxyazi/yazi)

Download the binary or use:

```bash
curl -sS https://raw.githubusercontent.com/sxyazi/yazi/main/install.sh | bash
```

---

## Basic Usage

```bash
yazi [directory]
```

- Launch `yazi` in current directory or a specified path.

---

## Navigation Basics (Normal Mode)

|Key|Action|
|---|---|
|`j` / `k`|Move down/up|
|`h`|Go to parent directory|
|`l` or `Enter`|Enter directory or open file|
|`gg` / `G`|Go to top / bottom|
|`q`|Quit|
|`:`|Enter command-line mode|
|`/`|Search/filter in current directory|
|`.`|Toggle hidden files|
|`<C-f>` / `<C-b>`|Page down / up|

---

## File Operations

|Key|Action|
|---|---|
|`yy`|Yank (copy)|
|`dd`|Delete (cut)|
|`pp`|Paste (copy or move)|
|`u`|Undo|
|`r`|Rename file/directory|
|`a`|Create file|
|`A`|Create directory|
|`x`|Delete file or directory|
|`s`|Select/Unselect item|
|`v`|Visual selection mode|
|`:`|Enter command mode (`:help`, `:shell`, etc.)|

---

## Preview System

- Yazi can preview:
    - Text files
    - Images (via `viu`, `ueberzugpp`, `kitty`)
    - PDFs
    - Archives
    - Videos and audio (via `ffmpegthumbnailer`)
    - Code with syntax highlighting (via `bat`)
### Dependencies for preview:

Make sure to install:

```bash
sudo pacman -S yazi ffmpeg 7zip jq poppler fd ripgrep fzf zoxide resvg imagemagick
```

- `bat` – Syntax highlighting
- `ueberzugpp` or `kitty +kitten icat` – Image preview
- `fd`, `rg`, `fzf` – Fuzzy search and indexing
- `poppler` – PDF previews

---

## Command Mode (like Vim)

Press `:` to enter command mode.

Useful commands:

```bash
:help            # Show help
:shell <cmd>     # Run shell command
:cd <dir>        # Change directory
:sort <method>   # Sort (name, size, modified)
:config          # Reload config
```

---

## Configuration

Config files live in:

```
~/.config/yazi/
```

### Key files:

- `yazi.toml` – main config
- `keymap.toml` – key bindings
- `plugin/` – plugin scripts
- `theme.toml` – colors and styles

To create default config:

```bash
yazi --generate-config
```

Then modify as needed.

---

## Fuzzy Finder (fzf integration)

Search and jump quickly using `/` or `fzf` plugin.

- Type `/` to filter
- Type `:` and use `:shell fd <pattern>` for custom searches

---

## Plugins

Yazi supports shell-based plugin scripting.

Typical use cases:

- Bulk renaming
- Image conversions
- Git integration
- Fzf-jumping
- Batch processing

Plugins live in:

```
~/.config/yazi/plugin/
```

Use `shell:` commands to call them.

---

## Custom Key Bindings

Edit `keymap.toml` to remap keys:

Example:

```toml
[keys.normal]
"J" = "seek +10"
"K" = "seek -10"
```

---

## Comparison to Other File Managers

| Feature         | Yazi              | Ranger       | NNN          | lf     |
| --------------- | ----------------- | ------------ | ------------ | ------ |
| Speed           | High (Rust)       | Medium       | High         | Medium |
| Previews        | Yes (async)       | Yes          | With plugins | Yes    |
| Modal interface | Yes               | No           | No           | Yes    |
| Image support   | Yes (with tools)  | Yes          | Limited      | Yes    |
| Vim-style keys  | Yes               | Yes          | Yes          | Yes    |
| Plugins         | Yes (shell-based) | Yes (Python) | Yes (shell)  | Yes    |

---

## Example Workflow

1. Launch `yazi`
2. Navigate to a project folder using `j`, `k`, `l`, `h`
3. Press `.` to show dotfiles
4. Use `/` to filter for `*.cpp`
5. Press `Enter` to open with your `$EDITOR` or external apps
6. Press `yy` to copy, `pp` to paste into a new folder
7. Use `:shell git status` inside Yazi to check git status
8. Press `q` to exit

---

## Tips

- Use `export EDITOR=nvim` to open files in your favorite editor
- Combine with `tmux` for productivity
- Alias it:

```bash
alias y="yazi"
```
