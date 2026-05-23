# Git Commands Reference
> Quick reference — copy & use anytime

---

## 1. `git status`
**What it does:** Shows the current state of your working directory — which files are modified, staged, or untracked.

```bash
git status
```

**Output means:**
- `modified` → file changed but not staged
- `staged` → ready to commit
- `untracked` → new file Git doesn't know about yet

---

## 2. `git add <file>`
**What it does:** Stages a specific file — moves it to the preparation zone for your next commit.

```bash
git add train.py
git add model/resnet.py
```

---

## 3. `git add .`
**What it does:** Stages ALL changed and new files in the current directory at once.

```bash
git add .
```

> ⚠️ Adds everything — make sure you don't have junk files. Use `.gitignore` to exclude files like `__pycache__/` or `.env`.

---

## 4. `git commit -m 'message'`
**What it does:** Saves all staged changes as a permanent snapshot in history with a descriptive message.

```bash
git commit -m "Add ResNet-20 training script for CIFAR-10"
git commit -m "Fix weed detection preprocessing bug"
```

**Good message format:** `<verb>: <what you did>`
- `Add: ...`
- `Fix: ...`
- `Update: ...`
- `Remove: ...`

---

## 5. `git branch`
**What it does:** Lists all local branches. The current branch is marked with `*`.

```bash
git branch                    # list branches
git branch feature/new-model  # create a new branch
git checkout -b feature/test  # create + switch in one step
git branch -d feature/test    # delete a branch
```

---

## 6. `git remote -v`
**What it does:** Shows all remote connections (e.g. GitHub) your local repo is linked to, with their URLs.

```bash
git remote -v
```

**Example output:**
```
origin  https://github.com/MuhammadKhuram/deep-learning-computer-vision.git (fetch)
origin  https://github.com/MuhammadKhuram/deep-learning-computer-vision.git (push)
```

---

## 7. `git remote add origin <url>`
**What it does:** Links your local repo to a GitHub repo for the first time.

```bash
git remote add origin https://github.com/MuhammadKhuram/deep-learning-computer-vision.git
```

> Only needed once when setting up a new repo. After this, `origin` is the nickname for your GitHub remote.

---

## 8. `git pull`
**What it does:** Downloads latest commits from GitHub AND merges them into your current local branch.

```bash
git pull origin main          # pull from main branch
git pull                      # shortcut after upstream is set
```

> ✅ Always run this at the start of a session (before editing) to sync changes from Colab or other devices.

---

## 9. `git push`
**What it does:** Uploads your local commits to GitHub.

```bash
git push origin main          # push to main branch
git push -u origin main       # first push — sets upstream so future pushes just need `git push`
git push                      # shortcut after upstream is set
```

---

## 10. `git log`
**What it does:** Shows the full commit history — each commit's ID (hash), author, date, and message.

```bash
git log                       # full history
git log --oneline             # compact one-line per commit (recommended)
git log --oneline -10         # last 10 commits only
```

**Example output (`--oneline`):**
```
a3f2c1b Add ResNet-20 training script
9d1e4f0 Fix preprocessing pipeline
3b8c7a2 Initial commit
```

---

## 11. `git diff`
**What it does:** Shows exactly what lines changed in your files that are NOT yet staged (line-by-line).

```bash
git diff                      # unstaged changes
git diff train.py             # diff for a specific file
```

**Reading the output:**
- Lines starting with `-` (red) → removed
- Lines starting with `+` (green) → added

---

## 12. `git diff --staged`
**What it does:** Same as `git diff` but shows changes that ARE staged (already `git add`-ed). Final review before committing.

```bash
git diff --staged
```

> ✅ Good habit: run this just before `git commit` to confirm exactly what you're about to save.

---

## 13. `git restore <file>`
**What it does:** Discards ALL unsaved changes in a file and reverts it back to the last commit.

```bash
git restore train.py          # discard changes in one file
git restore .                 # discard ALL unstaged changes
```

> ⚠️ **Permanent.** You cannot undo this. Only use when you want to throw away your edits completely.

---

## 14. `git stash`
**What it does:** Temporarily saves all uncommitted work to a stack and reverts your files to the last commit — without making a commit.

```bash
git stash                     # save current work
git stash pop                 # restore most recent stash
git stash list                # see all saved stashes
git stash drop stash@{0}      # delete a specific stash
```

> ✅ Use when you need to switch branches or pull updates but aren't ready to commit yet.

---

## Daily Workflow (Copy & Run)

```bash
# Start of session
git pull origin main

# After making changes
git status
git add .
git diff --staged
git commit -m "Your message here"
git push origin main
```

---

## Quick Cheat Sheet

| Command | One-line purpose |
|---|---|
| `git status` | What changed? |
| `git add <file>` | Stage one file |
| `git add .` | Stage everything |
| `git commit -m '...'` | Save snapshot |
| `git branch` | List/create branches |
| `git remote -v` | Show GitHub link |
| `git remote add origin <url>` | Link to GitHub (first time) |
| `git pull` | Download + merge from GitHub |
| `git push` | Upload to GitHub |
| `git log --oneline` | View compact history |
| `git diff` | See unstaged changes |
| `git diff --staged` | See staged changes |
| `git restore <file>` | Discard file changes |
| `git stash` | Temporarily save work |
| `git stash pop` | Restore stashed work |
