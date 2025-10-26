#tech #vim #computer #productivity #self-development 

**Vim operates in different modes:** Normal (default, press Esc), Insert (typing text, press i/a/o), Visual (selecting text, press v), and Command (executing commands, press :)

## Tips for Beginners

- Start with **vimtutor** - run this command in your terminal for an interactive tutorial
- Use **hjkl** for movement instead of arrow keys to build muscle memory
- Stay in normal mode as much as possible - only enter insert mode when actively typing
- Learn one new command per day rather than trying to memorize everything at once
- Practice the most common operations: navigation, insertion, deletion, and saving
- Use **:help** extensively - Vim's built-in documentation is excellent

## Configuration

Add these common settings to your `~/.vimrc` file:

### Display Settings
```vim
set number          " Show line numbers
set relativenumber  " Show relative line numbers
syntax on           " Enable syntax highlighting
```

### Buffer Settings
```vim
set hidden                  " Allow unsaved buffer switching
set autowrite              " Auto-save when switching buffers
set confirm                 " Ask before discarding changes
set switchbuf=useopen       " Jump to existing window if open
```

### Indentation
```vim
set tabstop=4       " Set tab width
set shiftwidth=4    " Set indent width
set expandtab       " Use spaces instead of tabs
set autoindent      " Auto-indent new lines
```

### Search Settings
```vim
set hlsearch        " Highlight search results
set incsearch       " Incremental search
set ignorecase      " Case-insensitive search
set smartcase       " Case-sensitive if uppercase present
```

### Interface Settings
```vim
set cursorline      " Highlight current line
set showmatch       " Highlight matching brackets
set ruler           " Show cursor position
set laststatus=2    " Always show status line
set wildmenu        " Enhanced command completion
set scrolloff=5     " Keep lines above/below cursor
```

### Editor Behavior
```vim
set noswapfile              " Disable swap files
set nobackup               " Disable backup files
set undofile               " Enable persistent undo
set clipboard=unnamedplus  " Use system clipboard
set mouse=a                " Enable mouse support
```

---

## Modes

### Mode Switching
| Command  | Description       |
| -------- | ----------------- |
| `Esc`    | Normal mode       |
| `v`      | Visual mode       |
| `V`      | Visual line mode  |
| `Ctrl+v` | Visual block mode |

### Entering Insert Mode from Normal Mode
| Command | Description             |
| ------- | ----------------------- |
| `i`     | Insert mode             |
| `I`     | Insert at line start    |
| `a`     | Append after cursor     |
| `A`     | Append at line end      |
| `o`     | New line below          |
| `O`     | New line above          |
| `s`     | Delete char and insert  |
| `S`     | Delete line and insert  |
| `gi`    | Insert at last position |

## Navigation

### Basic Movement
| Command | Description |
|---------|-------------|
| `h j k l` | Left, down, up, right |

### Word Movement
| Command | Description |
|---------|-------------|
| `w` | Word forward |
| `b` | Word backward |
| `e` | End of word |
| `W` | WORD forward |
| `B` | WORD backward |
| `E` | End of WORD |

### Line Movement
| Command | Description |
|---------|-------------|
| `0` | Line start |
| `^` | First non-blank char |
| `$` | Line end |

### Screen Movement
| Command | Description      |
| ------- | ---------------- |
| `H`     | Top of screen    |
| `M`     | Middle of screen |
| `L`     | Bottom of screen |

### File Navigation
| Command  | Description       |
| -------- | ----------------- |
| `gg`     | Go to top         |
| `G`      | Go to bottom      |
| `:N`     | Go to line number |
| `Ctrl+f` | Page down         |
| `Ctrl+b` | Page up           |
| `Ctrl+d` | Half page down    |
| `Ctrl+u` | Half page up      |

### Jump Navigation
| Command | Description |
|---------|-------------|
| `Ctrl+o` | Jump back |
| `Ctrl+i` | Jump forward |
| `g;` | Previous change |
| `g,` | Next change |

### Character Motions
| Command | Description |
|---------|-------------|
| `f{char}` | Find character forward |
| `F{char}` | Find character backward |
| `t{char}` | To character forward |
| `T{char}` | To character backward |
| `;` | Repeat character motion |
| `,` | Reverse character motion |

## Editing

### Delete & Change
| Command | Description |
|---------|-------------|
| `x` | Delete character |
| `X` | Delete char before cursor |
| `dd` | Delete line |
| `dw` | Delete word |
| `d$` | Delete to end of line |
| `d0` | Delete to start of line |
| `D` | Delete to end of line |
| `cw` | Change word |
| `cc` | Change line |
| `r` | Replace character |

### Copy & Paste
| Command | Description |
|---------|-------------|
| `yy` | Copy line |
| `yw` | Copy word |
| `y$` | Copy to end of line |
| `y0` | Copy to start of line |
| `p` | Paste after |
| `P` | Paste before |

### Undo & Redo
| Command | Description |
|---------|-------------|
| `u` | Undo |
| `Ctrl+r` | Redo |
| `U` | Undo line changes |

## Text Objects

### Word & Paragraph
| Command | Description |
|---------|-------------|
| `iw` | Inner word |
| `aw` | A word (with space) |
| `is` | Inner sentence |
| `as` | A sentence |
| `ip` | Inner paragraph |
| `ap` | A paragraph |

### Brackets & Quotes
| Command | Description |
|---------|-------------|
| `i(` | Inner block |
| `a(` | A block |
| `ib` | Inner block |
| `ab` | A block |
| `i"` | Inside quotes |
| `a"` | Around quotes |

### Useful Combinations
| Command | Description |
|---------|-------------|
| `ciw` | Change inner word |
| `di"` | Delete inside quotes |
| `ya(` | Yank around block |
| `>ip` | Indent paragraph |
| `=G` | Auto-indent to end |

## Registers

### Named Registers
| Command | Description |
|---------|-------------|
| `"ay` | Yank to register a |
| `"ap` | Paste from register a |
| `"Ay` | Append to register a |

### Special Registers
| Command | Description |
|---------|-------------|
| `"+` | System clipboard |
| `"*` | Selection clipboard |
| `"0` | Last yank |
| `"1` | Last delete |
| `"_` | Black hole register |
| `:reg` | Show all registers |

## Search & Replace

### Searching
| Command | Description |
|---------|-------------|
| `/pattern` | Search forward |
| `?pattern` | Search backward |
| `n` | Next match |
| `N` | Previous match |
| `*` | Search word under cursor |
| `#` | Search word under cursor (back) |

### Replacing
| Command | Description |
|---------|-------------|
| `:s/old/new/` | Replace first on line |
| `:s/old/new/g` | Replace all on line |
| `:%s/old/new/g` | Replace all in file |
| `:%s/old/new/gc` | Replace all with confirm |

## Global Commands

### Pattern Matching
| Command | Description |
|---------|-------------|
| `:g/pattern/cmd` | Execute on matching lines |
| `:v/pattern/cmd` | Execute on non-matching lines |

### Common Examples
| Command | Description |
|---------|-------------|
| `:g/pattern/d` | Delete lines containing pattern |
| `:g/^$/d` | Delete empty lines |
| `:g/pattern/t$` | Copy matching lines to end |
| `:g/pattern/m$` | Move matching lines to end |
| `:g/pattern/p` | Print matching lines |
| `:g/pattern/#` | Print with line numbers |

## File Operations

| Command | Description |
|---------|-------------|
| `:w` | Save file |
| `:w filename` | Save as |
| `:q` | Quit |
| `:q!` | Force quit |
| `:wq` | Save and quit |
| `:x` | Save and quit |
| `:e filename` | Open file |
| `:r filename` | Insert file contents |
| `:sp filename` | Horizontal split open |
| `:vsp filename` | Vertical split open |

## Shell Commands

### Execute Commands
| Command | Description |
|---------|-------------|
| `:!command` | Run shell command |
| `:r!command` | Insert command output |
| `:%!command` | Filter through command |
| `:shell` | Open shell |

### Common Examples
| Command | Description |
|---------|-------------|
| `:r!date` | Insert date |
| `:%!sort` | Sort lines |
| `:%!jq .` | Format JSON |
| `:!wc %` | Word count |

## Visual Mode

### Visual Selection
| Command | Description |
|---------|-------------|
| `v` | Character-wise selection |
| `V` | Line-wise selection |
| `Ctrl+v` | Block-wise selection |
| `o` | Go to other end |
| `gv` | Reselect last selection |

### Operations on Selection
| Command | Description |
|---------|-------------|
| `d` | Delete selection |
| `y` | Copy selection |
| `c` | Change selection |
| `U` | Uppercase |
| `u` | Lowercase |
| `>` | Indent right |
| `<` | Indent left |
| `=` | Auto-indent |

## Folding

### Create & Toggle
| Command | Description |
|---------|-------------|
| `zf` | Create fold |
| `za` | Toggle fold |
| `zo` | Open fold |
| `zc` | Close fold |
| `zd` | Delete fold |

### Fold Levels
| Command | Description |
|---------|-------------|
| `zR` | Open all folds |
| `zM` | Close all folds |
| `zr` | Open one level |
| `zm` | Close one level |
| `:set fdm=indent` | Fold on indent |

## Buffers

| Command | Description |
|---------|-------------|
| `:ls` | List buffers |
| `:b N` | Switch to buffer |
| `:bn` | Next buffer |
| `:bp` | Previous buffer |
| `:bd` | Delete buffer |

## Windows

### Window Splits
| Command | Description |
|---------|-------------|
| `:split` | Split horizontal |
| `:vsplit` | Split vertical |
| `Ctrl+w s` | Split horizontal |
| `Ctrl+w v` | Split vertical |

### Window Navigation
| Command | Description |
|---------|-------------|
| `Ctrl+w w` | Switch windows |
| `Ctrl+w h` | Move to left window |
| `Ctrl+w j` | Move to bottom window |
| `Ctrl+w k` | Move to top window |
| `Ctrl+w l` | Move to right window |
| `Ctrl+w c` | Close window |
| `Ctrl+w o` | Close all other windows |
| `Ctrl+w =` | Equalize window sizes |

### Window Resizing
| Command | Description |
|---------|-------------|
| `Ctrl+w +` | Increase height |
| `Ctrl+w -` | Decrease height |
| `Ctrl+w >` | Increase width |
| `Ctrl+w <` | Decrease width |

## Advanced

### Marks
| Command | Description |
|---------|-------------|
| `m[a-z]` | Set local mark |
| `m[A-Z]` | Set global mark |
| `'[mark]` | Go to line of mark |
| `` `[mark] `` | Go to exact position |
| `''` | Go to previous position |
| `'.` | Go to last edit |

### Macros
| Command | Description |
|---------|-------------|
| `q[a-z]` | Record macro |
| `q` | Stop recording |
| `@[a-z]` | Execute macro |
| `@@` | Repeat last macro |

### Repeat & Help
| Command | Description |
|---------|-------------|
| `.` | Repeat last command |
| `:set nu` | Show line numbers |
| `:help [cmd]` | Get help |

## Emergency

| Command | Description |
|---------|-------------|
| `Esc` | Return to normal mode |
| `Ctrl+c` | Return to normal mode |
| `:q!` | Quit without saving |
| `u` | Undo mistake |
| `:help` | Get help |


# Extra
---
#tech #vim  #productivity #text-editor
## Basic Movement

- `h` - Move cursor left.
- `j` - Move cursor down.
- `k` - Move cursor up.
- `l` - Move cursor right.
- `0` - Move to the start of the line.
- `$` - Move to the end of the line.
- `G` - Move to the end of the file.
- `gg` - Move to the start of the file.
- `<C-g>` - Show cursor location and file status.
- `number G` - Move to a specific line number.

## Editing Commands

- `x` - Delete the character under the cursor.
- `dw` - Delete a word.
- `d$` - Delete to the end of the line.
- `dd` - Delete the entire line.
- `u` - Undo the last change.
- `U` - Undo all changes on the current line.
- `<C-r>` - Redo the last undone change.
- `p` - Paste text after the cursor.
- `P` - Paste text before the cursor.
- `r` - Replace the character under the cursor.
- `R` - Enter Replace mode (replace multiple characters).
- `ce` - Change text until the end of the word.
- `c$` - Change text until the end of the line.
- `o` - Open a new line below the cursor and enter Insert mode.
- `O` - Open a new line above the cursor and enter Insert mode.
- `a` - Append text after the cursor.
- `A` - Append text at the end of the line.
- `i` - Insert text before the cursor.
- `y` - Yank (copy) text.
- `yw` - Yank a word.
- `yy` - Yank a line.

## Search and Replace

- `/phrase` - Search forward.
- `?phrase` - Search backward/
- `n` - Repeat the last search in the same direction.
- `N` - Repeat the last search in the opposite direction.
- `%` - Move to the matching parenthesis, bracket, or brace.
- `:s/old/new/` - Substitute "new" for the first occurrence of "old" in the current line.
- `:s/old/new/g` - Substitute "new" for all occurrences of "old" in the current line.
- `:#,#s/old/new/g` - Substitute "new" for "old" between two line numbers.
- `:%s/old/new/g` - Substitute "new" for "old" in the entire file.
- `:%s/old/new/gc` - Substitute with confirmation for each occurrence.

## File Operations

- `:w` - Save the file.
- `:w FILENAME` - Save the file with a new name.
- `:q` - Quit Neovim.
- `:q!` - Quit Neovim without saving changes.
- `:wq` - Save and quit.
- `:r FILENAME` - Insert the contents of a file below the cursor.
- `:r !command` - Insert the output of a shell command below the cursor.
- `:!command` - Execute a shell command (e.g., `:!ls`).

## Visual Mode

- `v` - Start Visual mode (character-wise selection).
- `V` - Start Visual mode (line-wise selection).
- `y` - Yank (copy) the selected text.
- `d` - Delete the selected text.
- `:w FILENAME` - Save the selected lines to a file.

## Settings and Options

- `:set ic` - Ignore case in searches.
- `:set noic` - Disable ignore case in searches.
- `:set hls` - Highlight search matches.
- `:set is` - Enable incremental search.
- `:set invic` - Toggle ignore case.
- `:nohlsearch` - Remove search highlighting.

## Help and Completion

- `:help` - Open the help system.
- `:help TOPIC` - Get help on a specific topic.
- `<C-d>` - Show command completions.
- `<Tab>` - Use a completion.
## Miscellaneous

- `<Esc>` - Return to Normal mode.
- `<C-w><C-w>` - Switch between windows.
- `<C-o>` - Go back to the previous cursor position.
- `<C-i>` - Go forward to the next cursor position.

---

# Vim Cheatsheet


See helpful vim commands right from your editor, narrow down your list by toggling off the once you’ve memorised/mastered. Make sure vim you’ve installed vim extention link.

## Insert Mode - inserting/appending text

- i – insert before the cursor
- I – insert at beginning of the line
- a – insert (append) after the cursor
- A – insert (append) at the end of the line
- o – append (open) a new line below the current line
- O – append (open) a new line above the current line
- ea – insert (append) at the end of the word
- Ctrl + h – delete the character before the cursor during insert mode
- Ctrl + w – delete the word before the cursor during insert mode
- Ctrl + j – begin new line during insert mode
- Ctrl + t – indent(move right) line one shiftwidth during insert mode
- Ctrl + d – de-indent(move left) line one shiftwidth during insert mode
- Ctrl + n – insert(auto-complete) next match before the cursor during insert mode
- Ctrl + p – insert(auto-complete) previous match before the cursor during insert mode
- Ctrl + rx – insert the contents of register x
- Ctrl + ox – Temporarily enter normal mode to issue one normal-mode command x.
- Esc – exit insert mode

Editing

- r – replace a single character.
- R – replace more than one character, until ESC is pressed.
- J – join line below to the current one with one space in between.
- gJ – join line below to the current one without space in between.
- gwip – reflow paragraph.
- g~ – switch case up to motion.
- gu – change to lowercase up to motion.
- gU – change to uppercase up to motion.
- cc – change (replace) entire line.
- c$ or C – change (replace) to the end of the line.
- ciw – change (replace) entire word.
- cw or ce – change (replace) to the end of the word.
- s – delete character and substitute text.
- S – delete line and substitute text (same as cc).
- xp – transpose two letters(delete and paste).
- u – undo.
- U – restore (undo) last change line.
- Ctrl + r – redo.
- . – repeat last command.

Marking Text (Visual Mode)

- v – start visual mode, mark lines, then do a command (like y-yank)
- V – start linewise visual mode.
- o – move to other end of marked area.
- Ctrl + v – start visual block mode.
- O – move to other corner of block.
- aw – mark a word.
- ab – a block with ().
- aB – a block with {}.
- at – a block with <> tags.
- ib – inner block with ().
- iB – inner block with {}.
- it – inner block with <> tags.
- Esc – exit visual mode.

## ![basic cursor movements|1010x31](https://file+.vscode-resource.vscode-cdn.net/home/ahmad/.vscode/extensions/andenetalexander.vim-cheatsheet-0.0.1/images/light-bulb.svg) Tip

Instead of **b** or **B** one can also use **(** or **{**, respectively.

Visual commands (In Visual mode)

- > – shift text right
- < – shift text left
- y – yank (copy) marked text
- d – delete marked text
- ~ – switch case
- u – change marked text to lowercase
- U – change marked text to uppercase

Registers

- :reg[isters] – show registers content
- "xy – yank into register x
- "xp – paste contents of register x
- "+y – yank into the system clipboard register
- "+p – paste from the system clipboard register

## ![basic cursor movements|1010x31](https://file+.vscode-resource.vscode-cdn.net/home/ahmad/.vscode/extensions/andenetalexander.vim-cheatsheet-0.0.1/images/light-bulb.svg) Tip

Registers are being stored in ~/.viminfo, and will be loaded again on next restart of vim.

## ![basic cursor movements|1010x31](https://file+.vscode-resource.vscode-cdn.net/home/ahmad/.vscode/extensions/andenetalexander.vim-cheatsheet-0.0.1/images/light-bulb.svg) Tip Special registers:

- 0 - last yank
- " - unnamed register, last delete or yank
- % - current file name
- # - alternate file name
- * - clipboard contents (X11 primary)
- + - clipboard contents (X11 clipboard)
- / - last search pattern
- : - last command-line
- . - last inserted text
- - - last small (less than a line) delete
- = - expression register
- _ - black hole register

Mark and Positions

- :marks – list of marks
- ma - set current position for mark A
- `a - jump to position of mark A
- y`a - yank text to position of mark A
- `0 - go to the position where Vim was previously exited
- `" - go to the position when last editing this file
- `. - go to the position of last editing this file
- `` - go to the position before the last last jump
- :ju[mps] - list of jumps
- Ctrl + i - go to newer position in jump list
- Ctrl + o - go to older position in jump list
- :changes - list of changes
- g - go to newer position in change list
- g; - go to older position in change list
- Ctrl + ] - jump to the tag under cursor

## ![basic cursor movements|1010x31](https://file+.vscode-resource.vscode-cdn.net/home/ahmad/.vscode/extensions/andenetalexander.vim-cheatsheet-0.0.1/images/light-bulb.svg) Tip

To jump to a mark you can either use a backtick (`) or an apostrophe ('). Using an apostrophe jumps to the beginning (first non-blank) of the line holding the mark.

Macros

- qa – record macro a
- q – stop recording macro
- @a – run macro a
- @@ – rerun last run macro

Cut and paste

- yy – yank (copy) a line
- 2y – yank (copy) 2 lines
- yw – yank (copy) the characters of the word from the cursor posion to the start of the next word
- yiw – yank (copy) word under the cursor
- yaw – yank (copy) word under the cursor and the space after or before it
- y$ or Y – yank (copy) to the end of line
- p – put (paste) the clipboard after cursor
- P – put (paste) before cursor
- gp – put (paste) the clipboard after cursor and leave cursor after the new text
- gP – put (paste) the clipboard before cursor and leave cursor after the new text
- dd – delete (cut) a line
- 2dd – delete (cut) 2 lines
- diw – delete (cut) word under the cursor
- daw – delete (cut) word under the cursor and the space after or before it
- d$ or D – delete (cut) to the end of the line
- x – delete (cut) character

Indent text

- >> – indent (move right) line one shiftwidth
- << – de-indent (move left) line one shiftwidth
- >% – indent a block with () or {} (cursor on brace) line one shiftwidth
- >ib – indent inner block with ()
- >at – indent a block with <> tags
- 3== – re-indent 3 lines
- =% – re-indent a block with () or {} (cursor on brace)
- =iB – re-indent inner block with {}
- gg=G – re-indent entire buffer
- ]p – paste and adjust indent to current line

Exiting

- :w – write (save) the file, but don't exit
- :w !sudo tee % – write out the current file using sudo
- :wq or or :x or ZZ – write (save) and quite
- :q – quit (fails if there are unsaved changes)
- :q! or ZQ – quit and throw away unsaved changes
- :wqa or ZQ – write (save) and quit on all tab

Search and replace

- /pattern – search for pattern
- ?pattern – search backward for pattern
- pattern – 'very magic' pattern: non-alphanumeric characters are interpreted as special regex symbols (no escaping needed)
- n – repeat search in same direction
- N – repeat search in opposite direction
- :%s/old/new/g – replace all old with new throught file
- :%s/old/new/gc – replace all old with new throught file with confirmations
- :noh[lsearch] – remove highlighting of search matches

Diff

- za – toggle fold under the cursor
- zo – open fold under the cursor
- zc – close fold under the cursor
- zr – reduce (open) all folds by one level
- zm – fold more (close) all folds by one level
- zi – toggle folding functionality
- ]c – jump to start of next change
- [c – jump to start of previous change
