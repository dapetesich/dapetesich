# Git Reference Guide

## All Commands

| Command | What it does |
|---|---|
| `git config --global user.name "Name"` | Tells Git who you are (one-time setup) |
| `git config --global user.email "email"` | Tells Git your email (one-time setup) |
| `git init` | Starts tracking a folder with Git |
| `git add .` | Stages all changed files for the next commit |
| `git add filename.py` | Stages one specific file |
| `git commit -m "message"` | Saves a checkpoint with a description |
| `git push` | Uploads your commits to GitHub |
| `git status` | Shows what's changed since last commit |
| `git diff` | Shows the actual line-by-line changes |
| `git log --oneline` | Shows your commit history |
| `git show abc123` | Shows what changed in a specific commit |
| `git show abc123:filename.py` | Shows how a file looked at that commit |
| `git checkout abc123` | Time travel to an old commit (temporary) |
| `git checkout main` | Come back to the present |
| `git checkout filename.py` | Undo uncommitted changes to a file |
| `git revert abc123` | Permanently undo a commit (creates new commit) |
| `git remote add origin [url]` | Connects your folder to a GitHub repo |
| `git branch -M main` | Names your main branch "main" |
| `git push -u origin main` | First-time push to GitHub |

---

## Workflows

### Starting a brand new project with Git

```bash
cd /path/to/your/folder
git init
git add .
git commit -m "Initial commit"
```

### Connecting to GitHub (first time only)

```bash
git remote add origin https://github.com/username/repo-name.git
git branch -M main
git push -u origin main
```

### Daily work: editing, testing, saving a checkpoint

```bash
# Edit your files, run your scripts, check output — no Git needed

# See what's changed
git status

# When you're happy with changes: git add filename.py
# Stage specific files (or use . for everything)
git add .

# Commit with a descriptive message
git commit -m "Added late fee calculation logic"

# Optionally back up to GitHub:
git push
```

### Checking what you've changed before committing

```bash
git status           # See which files changed
git diff             # See the actual changes
```

### Looking at your history

```bash
git log --oneline    # See commit history
git show abc123      # See what changed in a specific commit

# See who changed what line (useful for your own notes later)
git blame filename.py
```

### Going back to an old version (just to look or test)

```bash
git log --oneline           # Find the commit ID you want
git checkout abc123         # Go back in time
# Look around, run the code, etc.
git checkout main           # Come back to present
```

### Undoing changes you haven't committed yet

```bash
git checkout filename.py    # Resets that file to last commit
```

### Undoing a commit you already made

```bash
git revert abc123           # Creates a new commit that undoes it
```

---

## Key Concepts

- **Staging area**: `git add` moves changes to a "staging area" before committing — this lets you commit related changes together
- **Commits**: Think of these as save points you can always return to
- **Local vs Remote**: Everything works locally with just `git commit`. You only need `git push` to back up to GitHub or share with others.
- **Commit IDs**: Those weird letter-number combos (like `a1b2c3d`) are unique names for each checkpoint

---

## Remember

- You can edit and run your scripts normally — Git just watches in the background
- You don't have to commit or push until you're happy with your changes
- `git commit` saves locally, `git push` backs up to GitHub
- You can always go back to any checkpoint you've made
