#tech #awk #sed #grep #ripgrep #utilities

# `grep` – Global Regular Expression Print

---

### What is `grep`?

`grep` is a Unix command-line utility that searches for lines in files that match a given pattern (regular expression).

### Philosophy:

- Simple, powerful text searching.
- Works well in pipes and scripts.
- Based on regular expressions.

### Basic Syntax:

```bash
grep [options] pattern [file...]
```

### ⚡ Commonly Used Options:

| Option       | Description                            |
| ------------ | -------------------------------------- |
| `-i`         | Case insensitive search                |
| `-r` or `-R` | Recursively search directories         |
| `-n`         | Show line numbers                      |
| `-v`         | Invert match (show non-matching lines) |
| `-c`         | Count of matching lines                |
| `-l`         | Show file names with matches           |
| `-o`         | Show only the matching part of lines   |
| `-E`         | Use extended regex (same as `egrep`)   |
| `-w`         | Match whole word                       |
| `-A N`       | Show N lines After match               |
| `-B N`       | Show N lines Before match              |
| `-C N`       | Show N lines of Context around match   |

### Examples:

```bash
grep "error" logfile.txt               # Match 'error'
grep -i "error" logfile.txt            # Case-insensitive match
grep -r "TODO" .                      # Search recursively in current dir
grep -n "main" main.cpp               # Show line numbers
grep -v "DEBUG" app.log               # Show lines that don't contain DEBUG
grep -A 2 "Failed" server.log         # Match + 2 lines after
grep -E "foo|bar" file.txt            # Match "foo" or "bar"
```

---

## ⚡ `ripgrep` (`rg`)

### What is `ripgrep`?

`ripgrep` (or `rg`) is a modern replacement for `grep`, written in Rust. It's faster, smarter, and integrates well with coding projects (respects `.gitignore` by default).

### Philosophy:

- Fast recursive search.
- Smart by default: ignores binary files, `.gitignore`, hidden dirs etc.
- Developer-friendly.

### Basic Syntax:

```bash
rg [options] pattern [path]
```

### ⚡ Commonly Used Options:

| Option                   | Description                                     |
| ------------------------ | ----------------------------------------------- |
| `-i`                     | Case insensitive                                |
| `-n`                     | Show line numbers                               |
| `-v`                     | Invert match                                    |
| `-c`                     | Count matches                                   |
| `-l`                     | Show matching file names                        |
| `-o`                     | Only matching part                              |
| `-w`                     | Whole word                                      |
| `-A N` / `-B N` / `-C N` | Context before/after/both                       |
| `--hidden`               | Include hidden files                            |
| `--no-ignore`            | Don’t respect `.gitignore`                      |
| `-t <lang>`              | Filter by programming language (like `-t rust`) |
| `-g`                     | Include or exclude glob patterns                |

### Examples:

```bash
rg "main" .                            # Search for "main" in current dir
rg -i "error" logs/                    # Case-insensitive in logs dir
rg -n "def" *.py                       # Show matches in Python files with line numbers
rg -v "DEBUG" app.log                  # Exclude lines with DEBUG
rg "foo|bar" file.txt                  # Regex: "foo" or "bar"
rg -g "*.js" "console.log"            # Search in .js files only
rg --no-ignore "TODO"                 # Ignore .gitignore
rg -t c++ "printf"                    # Search only in C++ files
```

---

## `grep` vs `ripgrep`

| Feature                  | `grep`     | `ripgrep (rg)`            |
| ------------------------ | ---------- | ------------------------- |
| Speed                    | Slower     | Faster (Rust-based)       |
| Recursive                | Needs `-r` | Always recursive          |
| Ignores binary files     | No         | Yes                       |
| `.gitignore` support     | No         | Yes                       |
| Regex engine             | POSIX      | Rust regex (faster)       |
| Better defaults          | No         | Yes                       |
| Include/exclude globs    | Basic      | Advanced (`-g`, `--glob`) |
| Language-specific search | No         | Yes (`-t`)                |

# `sed` – Stream Editor

---

### What is `sed`?

`sed` is a stream editor that performs basic text transformations on an input stream (a file or input from a pipeline). It's non-interactive and is often used in shell scripts or command-line one-liners.

### Philosophy

- Process and transform text line by line.
- Efficient for automation and scripting.
- Uses a small but powerful scripting language.
- Works without modifying the original file unless redirected or used with `-i`.

---

## Basic Syntax

```bash
sed [options] 'command' [file...]
```

You can use `sed`:

- On standard input (e.g., via a pipe)
- On files directly
- With multiple expressions

---

## Most Useful `sed` Commands

### 1. Substitution (find and replace)

#### Syntax:

```bash
sed 's/pattern/replacement/[flags]' file
```

#### Common Flags:

| Flag     | Description                     |
| -------- | ------------------------------- |
| `g`      | Replace all matches in the line |
| `i`      | Case insensitive                |
| `1,3`    | Apply on lines 1 to 3           |
| `n`      | Apply on line n                 |
| `p`      | Print the substituted line      |
| `w file` | Write output to file            |

#### Examples:

```bash
sed 's/foo/bar/' file.txt          # Replace first 'foo' with 'bar' per line
sed 's/foo/bar/g' file.txt         # Replace all 'foo' with 'bar' per line
sed 's/foo/bar/gi' file.txt        # Replace all case-insensitive
sed '3s/foo/bar/' file.txt         # Replace on line 3 only
sed '1,5s/foo/bar/g' file.txt      # Replace in lines 1 to 5
```

### 2. In-place Editing (modify original file)

#### Syntax:

```bash
sed -i 's/foo/bar/g' file.txt
```

#### Examples:

```bash
sed -i 's/localhost/127.0.0.1/g' /etc/hosts     # Replace directly in file
```

Note: Use `-i.bak` to create a backup file:

```bash
sed -i.bak 's/foo/bar/g' file.txt
```

### 3. Delete lines

#### Syntax:

```bash
sed 'Nd' file.txt
```

#### Examples:

```bash
sed '3d' file.txt              # Delete line 3
sed '1,5d' file.txt            # Delete lines 1 to 5
sed '/^$/d' file.txt           # Delete all blank lines
sed '/pattern/d' file.txt      # Delete lines matching pattern
```

### 4. Print lines

By default, `sed` prints every line (unless suppressed with `-n`).

#### Examples:

```bash
sed -n '3p' file.txt           # Print line 3 only
sed -n '/error/p' file.txt     # Print lines that match 'error'
```

### 5. Insert and Append lines

| Command | Action                    |
| ------- | ------------------------- |
| `i`     | Insert text before a line |
| `a`     | Append text after a line  |

#### Examples:

```bash
sed '3i\This is inserted' file.txt       # Insert before line 3
sed '3a\This is appended' file.txt       # Append after line 3
sed '/pattern/i\New line above match'    # Insert above matching line
sed '/pattern/a\New line below match'    # Append below matching line
```

### 6. Replace whole line

#### Syntax:

```bash
sed '3c\New content' file.txt     # Replace line 3 completely
```

### 7. Multiple commands

Use `-e` or semicolon (`;`) inside quotes:

```bash
sed -e 's/foo/bar/' -e 's/baz/qux/' file.txt

# Or
sed 's/foo/bar/; s/baz/qux/' file.txt
```

### 8. Read from file and insert

```bash
sed '/pattern/r filename.txt' file.txt
```

---

## Real-World Examples

1. Remove comments and blank lines

```bash
sed '/^\s*#/d; /^\s*$/d' script.sh
```

2. Convert tabs to spaces

```bash
sed 's/\t/    /g' file.txt
```

3. Number only non-empty lines

```bash
sed '/./=' file.txt | sed 'N; s/\n/ /'
```

4. Backup config files while replacing values

```bash
sed -i.bak 's/^Port 22/Port 2222/' /etc/ssh/sshd_config
```

---

# `awk` – Pattern-Scanning and Processing Language

Here's a detailed and beginner-friendly guide to the `awk` command, perfect for your Linux notes.

---

## `awk` – Pattern-Scanning and Processing Language

### What is `awk`?

`awk` is a powerful text-processing tool and a mini scripting language for working with structured data (mostly column-based). It's ideal for reporting, field manipulation, and filtering.

It works line-by-line, breaking input into fields (columns), which can be processed based on patterns and actions.

---

## Philosophy

- Designed for report generation, text scanning, and column-based data transformation.
- Treats each line as a record and each column as a field.
- Perfect for parsing logs, CSV files, and tabular outputs.

---

## Basic Syntax

```bash
awk 'pattern { action }' file
```

- `pattern` — condition to match (optional)
- `action` — what to do if the pattern matches
- If no pattern: apply action to every line
- If no action: print matching lines (like `grep`)

---

## Field & Record Variables

| Variable              | Meaning                               |
| --------------------- | ------------------------------------- |
| `$0`                  | Entire current line (record)          |
| `$1`, `$2`, ..., `$n` | Individual fields (columns)           |
| `NF`                  | Number of fields in current line      |
| `NR`                  | Current line number (record number)   |
| `FNR`                 | Line number in current file           |
| `FS`                  | Field Separator (default: whitespace) |
| `OFS`                 | Output Field Separator                |
| `RS`                  | Record Separator (default: newline)   |

---

## Examples

### 1.

Print specific fields

```bash
awk '{ print $1 }' file.txt         # Print first column
awk '{ print $1, $3 }' file.txt     # Print 1st and 3rd columns
```

### 2. Use a custom field separator

```bash
awk -F ':' '{ print $1 }' /etc/passwd   # Use ':' as field separator
awk -F ',' '{ print $2 }' data.csv      # Print second column of CSV
```

### 3. Pattern filtering

```bash
awk '$3 > 50 { print $1, $3 }' file.txt     # Print lines where 3rd column > 50
awk '$1 ~ /Ahmad/ { print $0 }' file.txt    # Lines where 1st column contains "Ahmad"
awk '$1 !~ /test/' file.txt                 # Lines where 1st column does NOT contain "test"
```

### 4. Add computed columns

```bash
awk '{ total = $2 * $3; print $1, total }' file.txt
```

### 5. Count lines

```bash
awk 'END { print NR }' file.txt        # Total number of lines
```

### 6. Print line number and content

```bash
awk '{ print NR, $0 }' file.txt
```

### 7. Set output delimiter

```bash
awk 'BEGIN { OFS = "," } { print $1, $2 }' file.txt
```

### 8. BEGIN and END blocks

```bash
awk 'BEGIN { print "Name\tMarks" } { print $1, $2 } END { print "Done" }' marks.txt
```

---

## Real-World Examples

### CSV parsing:

```bash
awk -F, '$3 > 90 { print $1 }' marks.csv
```

### Add header to file:

```bash
awk 'BEGIN { print "User\tScore" } { print $1, $2 }' scores.txt
```

### Calculate total and average:

```bash
awk '{ sum += $2 } END { print "Total:", sum, "Average:", sum/NR }' marks.txt
```

### Print non-comment, non-empty lines:

```bash
awk '!/^#/ && NF > 0' file.conf
```

---

## Summary of Common Usage

| Task                | Command                                               |
| ------------------- | ----------------------------------------------------- |
| Print column(s)     | `awk '{ print $1, $2 }'`                              |
| Set input delimiter | `awk -F, '{ print $2 }'`                              |
| Filter rows         | `awk '$3 > 50'`                                       |
| Add new column      | `awk '{ print $1, $2 * 100 }'`                        |
| Count lines         | `awk 'END { print NR }'`                              |
| Sum a column        | `awk '{ sum += $2 } END { print sum }'`               |
| Add header/footer   | `awk 'BEGIN{print "Start"} {print} END{print "End"}'` |

---

## `awk` vs `sed` vs `grep`

| Feature         | `awk`   | `sed`   | `grep` |
| --------------- | ------- | ------- | ------ |
| Full scripting  | Yes     | Limited | No     |
| Field awareness | Yes     | No      | No     |
| Substitution    | Limited | Yes     | No     |
| Regex filtering | Yes     | Yes     | Yes    |
