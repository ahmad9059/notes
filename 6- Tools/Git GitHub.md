#tech #git #opensource #version-control #github #gitlab #pull-request


- **Git** is a **distributed version control system**.
- It tracks **changes** in source code during development.
- Enables **collaboration**, **version history**, and **branching**.

### One-liner:

> Git is a tool to track and manage code changes in projects.

---

## 🌐 What is GitHub?

- **GitHub** is a **hosting platform** for Git repositories.
- It allows **cloud storage**, **collaboration**, **issue tracking**, **pull requests**, and **CI/CD**.

### One-liner:

> GitHub is a website where developers host and collaborate on Git repositories.

---

## 🛠️ Basic Setup

### 1. Install Git

```bash
sudo apt install git      # Debian/Ubuntu
sudo pacman -S git        # Arch
```

### 2. Initial Configuration

```bash
git config --global user.name "Ahmad Hassan"
git config --global user.email "ahmad@example.com"
git config --global init.defaultBranch main
```

---

## 📁 Git Project Lifecycle

### 1. Create Repository

```bash
git init
```

> Initializes a new Git repo in the folder.

### 2. Clone Repository

```bash
git clone https://github.com/user/repo.git
```

> Copies a repo from GitHub to your system.

---

## 📋 Git Workflow

### 1. Check Status

```bash
git status
```

> Shows the state of your working directory.

### 2. Track Files

```bash
git add <file>
git add .                # Add all files
```

> Moves changes to the staging area.

### 3. Commit Changes

```bash
git commit -m "Your message"
```

> Saves staged changes to the local repo.

### 4. Push to GitHub

```bash
git push origin main
```

> Uploads local commits to GitHub.

### 5. Pull from GitHub

```bash
git pull
```

> Downloads latest changes from GitHub.

---

## 🌿 Branching & Merging

### 1. Create Branch

```bash
git branch feature-x
```

> Creates a new branch.

### 2. Switch Branch

```bash
git checkout feature-x
```

> Switches to the branch.

### 3. Create & Switch

```bash
git checkout -b feature-x
```

### 4. Merge Branch

```bash
git checkout main
git merge feature-x
```

> Merges feature-x into main.

### 5. Delete Branch

```bash
git branch -d feature-x
```

---

## 🧠 Useful Git Commands
---
### `git log`

#### One-liner:

> View the history of commits in your repository.

#### Syntax:

```bash
git log
```

#### Examples:

```bash
git log --oneline
git log --graph --oneline --all
git log --since="2 days ago"
```

#### Use-cases:

- See commit history
- Track author and timestamp
- Visualize branch merges with `--graph`

---

### `git diff`

#### One-liner:

> Shows line-by-line changes between files, commits, and branches.

#### Syntax:

```bash
git diff [options]
```

#### Examples:

```bash
git diff                # unstaged changes
git diff --staged       # staged changes
git diff HEAD~1         # difference with previous commit
git diff main feature   # diff between branches
```

#### Use-cases:

- Preview changes before staging
- Review what’s different between two branches

---

### `git reset`

#### One-liner:

> Unstages or undoes commits or changes.

#### Syntax:

```bash
git reset [mode] [commit]
```

#### Examples:

```bash
git reset               # unstage files
git reset --soft HEAD~1 # undo last commit, keep changes staged
git reset --mixed HEAD~1 # undo last commit, keep changes
git reset --hard HEAD~1  # undo last commit and delete changes
```

#### Warning:

- `--hard` deletes changes permanently unless backed up.

---

### `git rm`

#### One-liner:

> Remove a file from your working directory and stage the deletion.

#### Syntax:

```bash
git rm <file>
```

###Examples:

```bash
git rm unwanted.txt
git rm -r folder/
```

#### Use-cases:

- Deleting files and tracking the deletion in Git history.

---

### `git mv`

#### One-liner:

> Rename or move a file and stage the change.

#### Syntax:

```bash
git mv <old> <new>
```

#### Examples:

```bash
git mv index.html home.html
git mv src/old.js src/new.js
```

### 🔍 Use-cases:

- Renaming files while keeping Git history.
- Moving files between folders.

---

### `git stash`

#### One-liner:

> Temporarily save changes without committing.

#### Syntax:

```bash
git stash [options]
```

#### Examples:

```bash
git stash                 # save unstaged/staged changes
git stash list            # see stashed items
git stash pop             # apply latest stash and remove it
git stash apply stash@{1} # apply a specific stash
```

#### Use-cases:

- Quickly switch branches without committing.
- Save work-in-progress temporarily.

---

### `git remote`

#### One-liner:

> Manage connections to remote repositories like GitHub.

#### Syntax:

```bash
git remote [command]
```

#### Examples:

```bash
git remote -v                          # list remotes
git remote add origin <url>           # add remote
git remote remove origin              # remove remote
git remote set-url origin <new-url>   # change remote
```

#### Use-cases:

- Link to GitHub or GitLab repositories.
- Change or update repository origin.

---

### `git fetch`

#### One-liner:

> Downloads changes from a remote but doesn’t merge automatically.

#### Syntax:

```bash
git fetch [remote-name]
```

#### Examples:

```bash
git fetch origin
git fetch --all
```

#### Use-cases:

- Update local knowledge of remote branches.
- Preview remote changes without affecting working code.

#### Difference:

- `git pull` = fetch + merge
- `git fetch` = only download

---

### `git rebase`

#### One-liner:

> Reapply your changes on top of another branch’s latest commit (clean history).

#### Syntax:

```bash
git rebase [branch]
```

#### Examples:

```bash
git checkout feature
git rebase main           # replay feature branch on top of main
git rebase -i HEAD~3      # interactive rebase (squash, reorder)
```

#### Use-cases:

- Keep a clean commit history
- Move your work on top of updated main branch

#### Warning:

> Avoid rebasing public/shared branches unless you’re confident.

---

## 🔁 Undoing Changes

| Command                  | Purpose                 |
| ------------------------ | ----------------------- |
| `git restore <file>`     | Revert changes in file  |
| `git checkout -- <file>` | Legacy version of above |
| `git commit --amend`     | Modify last commit      |
| `git reset HEAD~1`       | Uncommit last commit    |
| `git revert <commit>`    | Create reverse commit   |

---



## 🗃️ Tags

```bash
git tag v1.0
git tag -a v1.0 -m "Release 1.0"
git push origin v1.0
```

> Tags are for marking versions/releases.

---

## 👯‍♂️ Collaboration

### 1. **Fork a repo** on GitHub

> Creates a personal copy

### 2. **Clone your fork**

```bash
git clone https://github.com/yourname/project.git
```

### 3. **Make changes & push**

```bash
git push origin branch-name
```

### 4. **Create Pull Request** on GitHub

---

## 🧪 Git Ignore

Create `.gitignore` file to ignore files/folders.

```txt
node_modules/
.env
*.log
```

---

## 📌 Aliases (for faster workflow)

```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.cm "commit -m"
```

---

## 🧰 Pro Git Tips

|Tip|Command|
|---|---|
|See who changed what|`git blame <file>`|
|Clean up branches|`git branch --merged` and delete|
|Graph view|`git log --oneline --graph --all`|
|Show last commit|`git show`|
|Squash commits|`git rebase -i HEAD~n`|

---

## 🐙 GitHub CLI (Optional)

Install:

```bash
sudo pacman -S github-cli
```

Login:

```bash
gh auth login
```

Create repo:

```bash
gh repo create my-repo --public --source=. --push
```

---

## 🧪 Example Workflow

```bash
git init
touch index.html
git add .
git commit -m "Initial commit"
gh repo create my-site --public --source=. --push
```

---

## 🔐 SSH Setup (for GitHub)

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
cat ~/.ssh/id_ed25519.pub
```

> Copy the key and add to GitHub > Settings > SSH & GPG Keys
