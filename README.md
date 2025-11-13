# Git Commands Guide - TODO List

This guide covers three main scenarios for working with Git repositories.

## 📋 Table of Contents
1. [Building a New Repository](#1-building-a-new-repository)
2. [Updating an Existing Repository](#2-updating-an-existing-repository)
3. [Removing All Diffs and Creating Clean Initial Commit](#3-removing-all-diffs-and-creating-clean-initial-commit)
4. [Checking Status Commands](#4-checking-status-commands)

---

## 1. Building a New Repository

### Scenario: You don't have a repository yet and want to create one

#### Step 1: Initialize local repository
```bash
git init
```

#### Step 2: Add files to staging area

**Add all files and folders:**
```bash
git add .
```

**Add specific files (any file type):**
```bash
git add filename1.js filename2.html
git add README.md LICENSE
git add script.js styles.css index.html
```

**Add entire folders:**
```bash
git add src/
git add images/
git add .github/
```

**Note:** You can add any file type (JavaScript, HTML, CSS, images, documents, etc.) and any folder structure!

#### Step 3: Create initial commit
```bash
git commit -m "Initial commit: Your project description"
```

**What does `-m` mean?**
- `-m` stands for **"message"** - it allows you to add a comment/description to your commit
- The text inside quotes is your commit message that describes what changes you made
- **Every commit should have a message** - it helps you remember what you changed and why

**Examples of commit messages:**
```bash
git commit -m "Initial commit: Complete study guide with JavaScript examples"
git commit -m "Add new JavaScript functions"
git commit -m "Fix bug in calculation"
git commit -m "Update README with installation instructions"
git commit -m "Add Git commands guide"
git commit -m "Remove unused files"
```

**Why commit messages are important:**
- They help you understand what was changed in each commit
- They make it easier to track your project history
- Other collaborators can understand your changes
- You can search through commit history by message

**Tip:** Write clear, descriptive commit messages that explain WHAT you changed and WHY (if needed).

#### Step 4: Create repository on GitHub
- Go to GitHub.com and create a new repository
- Copy the repository URL (e.g., `https://github.com/username/repo-name.git`)

#### Step 5: Connect local repository to GitHub
```bash
git remote add origin https://github.com/username/repo-name.git
```

#### Step 6: Push to GitHub
```bash
git push -u origin main
```
(Use `master` instead of `main` if that's your default branch name)

**What does `-u` mean?**
- `-u` stands for **"upstream"** - it sets up tracking between your local branch and the remote branch
- After using `-u` once, Git remembers the connection, so you can just use `git push` in the future
- **Only needed the first time** you push a new branch to GitHub
- After that, you can simply use `git push` without `-u`

**How it works:**
```bash
# First time pushing a branch (use -u)
git push -u origin main

# After that, you can just use:
git push              # Git remembers origin/main automatically
```

**Without `-u`:**
```bash
git push origin main     # Works, but doesn't set up tracking
git push                 # Won't work - Git doesn't know where to push
```

**With `-u`:**
```bash
git push -u origin main  # Sets up tracking
git push                 # Now works! Git knows to push to origin/main
```

**Important:** Use `-u` only the first time you push a branch. After that, use `git push` for simplicity.

---

## 2. Updating an Existing Repository

### Scenario: You have a repository and want to update it

#### Step 1: Check current status
```bash
git status
```

#### Step 2: Add changes to staging area

**Add all changes (files and folders):**
```bash
git add .
```

**Add specific files (any file type):**
```bash
git add filename.js
git add filename.html
git add filename.css
git add filename.md
git add filename.json
git add README.md
```

**Add entire folders/directories:**
```bash
git add folder-name/
git add src/
git add images/
git add .github/
```

**Add multiple files at once:**
```bash
git add file1.js file2.html file3.css
```

**Add files by pattern/extension:**
```bash
git add *.js          # All JavaScript files
git add *.html        # All HTML files
git add *.md          # All Markdown files
git add src/**/*.js   # All JS files in src folder and subfolders
```

**Add files by type:**
```bash
git add "*.js"        # JavaScript files
git add "*.html"      # HTML files
git add "*.css"       # CSS files
git add "*.md"        # Markdown files
git add "*.json"      # JSON files
git add "*.png"       # PNG images
git add "*.jpg"       # JPEG images
git add "*.svg"       # SVG images
```

**Examples for different file types:**
```bash
# JavaScript files
git add script.js
git add app.js
git add övning-fil.js

# HTML files
git add index.html
git add script-prompt.html

# CSS files
git add styles.css
git add main.css

# Markdown files
git add README.md
git add GIT_COMMANDS_GUIDE.md

# JSON files
git add package.json
git add config.json

# Image files
git add logo.png
git add image.jpg

# Folders with files
git add .github/          # GitHub Actions folder
git add src/              # Source code folder
git add docs/             # Documentation folder
git add images/           # Images folder
```

**Important:** Git tracks ANY file type you add - text files, images, videos, documents, etc. You can create folders, subfolders, and any file structure you need!

#### Step 3: Commit changes
```bash
git commit -m "Description of what you changed"
```

**What does `-m` mean?**
- `-m` stands for **"message"** - it allows you to add a comment/description to your commit
- The text inside quotes is your commit message that describes what changes you made
- **Every commit should have a message** - it helps you remember what you changed and why

**Examples of commit messages:**
```bash
git commit -m "Add new feature for user authentication"
git commit -m "Fix bug in calculation function"
git commit -m "Update README with new instructions"
git commit -m "Remove unused console.log statements"
git commit -m "Add error handling to API calls"
git commit -m "Update CSS styles for better responsiveness"
```

**Tip:** Write clear, descriptive commit messages for each commit so you can track your changes over time.

#### Step 4: Push to GitHub
```bash
git push origin main
```
or simply:
```bash
git push
```

**When to use which:**
- `git push origin main` - Always works, explicitly specifies where to push
- `git push` - Only works if you used `-u` flag the first time (which sets up tracking)

**If you used `-u` the first time:**
```bash
# After first push with -u, you can just use:
git push              # Git remembers origin/main automatically
```

**If you didn't use `-u` the first time:**
```bash
# You need to specify each time:
git push origin main
```

### If remote has changes you don't have locally:

#### Step 5a: Pull changes from GitHub first
```bash
git pull origin main --no-rebase
```

#### Step 5b: Resolve any merge conflicts if they occur
- Edit conflicted files
- Stage resolved files: `git add filename.js`
- Complete merge: `git commit -m "Merge remote changes"`

#### Step 5c: Push your changes
```bash
git push origin main
```

---

## 3. Removing All Diffs and Creating Clean Initial Commit

### Scenario: You want to remove all history and start fresh with one initial commit

#### Step 1: Create new orphan branch (no history)
```bash
git checkout --orphan new-main
```

#### Step 2: Add all current files
```bash
git add .
```

#### Step 3: Create initial commit
```bash
git commit -m "Initial commit: Complete study guide with all JavaScript concepts and examples"
```

#### Step 4: Delete old main branch
```bash
git branch -D main
```

#### Step 5: Rename new-main to main
```bash
git branch -m new-main main
```

#### Step 6: Force push to GitHub (replaces all history)
```bash
git push -f origin main
```

⚠️ **Warning**: Force push will permanently delete all previous commits and history on GitHub!

---

## 4. Checking Status Commands

### Local Repository Status

#### Check working directory status
```bash
git status
```
Shows:
- Modified files
- Untracked files
- Files ready to commit
- Branch information

#### Check commit history
```bash
git log
```
Shows full commit history with details

#### Check commit history (compact)
```bash
git log --oneline
```
Shows one line per commit

#### Check last N commits
```bash
git log --oneline -5
```
Shows last 5 commits (change number as needed)

#### Check differences since last commit
```bash
git diff
```
Shows unstaged changes

#### Check staged differences
```bash
git diff --staged
```
Shows changes ready to commit

#### Check what files are tracked
```bash
git ls-files
```
Lists all files tracked by Git

### Remote Repository Status

#### Check remote repository URL
```bash
git remote -v
```
Shows:
- Remote name (usually `origin`)
- Fetch URL
- Push URL

#### Check remote branches
```bash
git branch -r
```
Shows all remote branches

#### Check local vs remote status
```bash
git fetch origin
git status
```
Fetches latest info from GitHub and shows status

#### Compare local and remote branches
```bash
git log HEAD..origin/main
```
Shows commits on remote that you don't have locally

```bash
git log origin/main..HEAD
```
Shows commits you have locally that aren't on remote

#### Check if local is ahead/behind remote
```bash
git status
```
Shows: "Your branch is ahead/behind 'origin/main' by X commits"

---

## 🚩 Git Flags Quick Reference

### Most Common Git Flags

#### `-m` (Message)
**What it does:** Adds a commit message/comment  
**Use with:** `git commit`  
**Example:**
```bash
git commit -m "Your commit message here"
```
**Why:** Every commit needs a message to describe what changed

---

#### `-u` (Upstream)
**What it does:** Sets up tracking between local and remote branch  
**Use with:** `git push`  
**Example:**
```bash
git push -u origin main
```
**Why:** Only needed first time - after that you can use `git push` alone

---

#### `-f` (Force)
**What it does:** Force push - overwrites remote history  
**Use with:** `git push`  
**Example:**
```bash
git push -f origin main
```
**Warning:** ⚠️ Permanently deletes remote history! Use carefully.

---

#### `--no-rebase`
**What it does:** Pulls changes from GitHub without "replaying" your local commits on top of the new changes.  
**In plain language:** This means that when you use `git pull` with `--no-rebase`, Git will keep your commit history as it is and make one new commit that combines your changes with the changes from GitHub. It does NOT try to re-apply each of your commits one-by-one like a rebase would.
**Use with:** `git pull`  
**Example:**
```bash
git pull origin main --no-rebase
```
**Why:** It creates a merge commit so you can see a clear point where changes from different places came together, instead of re-writing your commit history.

**User-Friendly vs Industry Standard:**
- ✅ **User-Friendly:** Uses `--no-rebase` explicitly - makes it clear what's happening, easier to understand for beginners
- 📊 **Industry Standard:** Default `git pull` behavior (without any flag) actually does merge by default, so `--no-rebase` is redundant but explicit
- 💡 **Best Practice:** Use `git pull --no-rebase` when learning to understand what's happening, or just `git pull` (which does merge by default)

**Note:** Many professional teams use `--rebase` for cleaner history, but `--no-rebase` (or default merge) is safer and easier for beginners.

---

#### `--rebase` (Advanced)
**What it does:** Pulls changes and replays your local commits on top of the remote changes  
**Use with:** `git pull`  
**Example:**
```bash
git pull origin main --rebase
```
**Why:** Creates a linear commit history without merge commits - looks cleaner

**User-Friendly vs Industry Standard:**
- ⚠️ **Advanced/Beginner Caution:** `--rebase` rewrites commit history - can be confusing if conflicts occur
- 📊 **Industry Standard:** Used by many professional teams for cleaner, linear history
- 💡 **Best Practice:** Use `--rebase` only if you understand Git well and your team prefers it. For beginners, stick with `--no-rebase` or default merge.

**When to use:**
- ✅ You want clean, linear history
- ✅ Your team prefers rebase workflow
- ✅ You're comfortable resolving conflicts
- ❌ Avoid if you're learning Git
- ❌ Avoid if you've already pushed commits (unless you know what you're doing)

---

#### `-A` (All)
**What it does:** Adds all changes including deletions  
**Use with:** `git add`  
**Example:**
```bash
git add -A
```
**Why:** Includes file deletions, not just new/modified files

---

#### `-r` (Remote)
**What it does:** Shows remote branches  
**Use with:** `git branch`  
**Example:**
```bash
git branch -r
```
**Why:** Lists all branches on remote repository

---

#### `-v` (Verbose)
**What it does:** Shows detailed information  
**Use with:** `git remote`  
**Example:**
```bash
git remote -v
```
**Why:** Shows both fetch and push URLs

---

#### `--oneline`
**What it does:** Shows compact one-line commit history  
**Use with:** `git log`  
**Example:**
```bash
git log --oneline
```
**Why:** Easier to read - one commit per line

---

#### `--allow-unrelated-histories`
**What it does:** Allows merging unrelated Git histories  
**Use with:** `git pull`  
**Example:**
```bash
git pull origin main --allow-unrelated-histories
```
**Why:** Needed when merging repositories with different histories

---

#### `-D` (Force Delete)
**What it does:** Force deletes a branch  
**Use with:** `git branch`  
**Example:**
```bash
git branch -D branch-name
```
**Warning:** ⚠️ Permanently deletes branch even if it has unmerged changes

---

#### `-m` (Rename/Move)
**What it does:** Renames or moves files/branches  
**Use with:** `git branch` or `git mv`  
**Example:**
```bash
git branch -m old-name new-name
git mv old-file.js new-file.js
```
**Why:** Renames branches or moves/renames files in Git

---

#### `--orphan`
**What it does:** Creates branch with no history  
**Use with:** `git checkout`  
**Example:**
```bash
git checkout --orphan new-branch
```
**Why:** Starts fresh branch without commit history

---

#### `--soft`
**What it does:** Undoes commit but keeps changes staged  
**Use with:** `git reset`  
**Example:**
```bash
git reset --soft HEAD~1
```
**Why:** Undo commit but keep your changes ready to commit again

---

#### `--hard`
**What it does:** Undoes commit and discards all changes  
**Use with:** `git reset`  
**Example:**
```bash
git reset --hard HEAD~1
```
**Warning:** ⚠️ Permanently deletes changes! Use carefully.

---

### Quick Flag Cheat Sheet

| Flag | Command | Purpose | User-Friendly | Industry Standard |
|------|---------|---------|---------------|-------------------|
| `-m` | `git commit` | Add commit message | ✅ Yes | ✅ Yes |
| `-u` | `git push` | Set upstream tracking (first time only) | ✅ Yes | ✅ Yes |
| `-f` | `git push` | Force push (overwrites remote) | ⚠️ Dangerous | ⚠️ Use carefully |
| `-A` | `git add` | Add all changes including deletions | ✅ Yes | ✅ Yes |
| `-r` | `git branch` | Show remote branches | ✅ Yes | ✅ Yes |
| `-v` | `git remote` | Show verbose remote info | ✅ Yes | ✅ Yes |
| `--oneline` | `git log` | Compact commit history | ✅ Yes | ✅ Yes |
| `-D` | `git branch` | Force delete branch | ⚠️ Dangerous | ⚠️ Use carefully |
| `--soft` | `git reset` | Undo commit, keep changes | ✅ Yes | ✅ Yes |
| `--hard` | `git reset` | Undo commit, discard changes | ⚠️ Dangerous | ⚠️ Use carefully |
| `--orphan` | `git checkout` | Create branch without history | ⚠️ Advanced | ✅ Yes |
| `--no-rebase` | `git pull` | Pull without rebasing (explicit merge) | ✅ Yes (Beginner-friendly) | ✅ Yes (Default behavior) |
| `--rebase` | `git pull` | Pull with rebase (linear history) | ⚠️ Advanced | ✅ Yes (Many teams prefer) |
| `--allow-unrelated-histories` | `git pull` | Merge unrelated histories | ✅ Yes | ✅ Yes |

**Legend:**
- ✅ **User-Friendly:** Safe and easy to use, especially for beginners
- 📊 **Industry Standard:** Commonly used in professional development
- ⚠️ **Dangerous/Advanced:** Can cause data loss or requires advanced knowledge

---

## 📝 Quick Reference

### Most Common Commands
```bash
# Check status
git status

# Add all changes
git add .

# Commit changes
git commit -m "Your message"

# Push to GitHub
git push origin main

# Pull from GitHub
git pull origin main
```

### Useful Aliases (Optional)
You can add these to your Git config for shortcuts:
```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
```

Then use: `git st` instead of `git status`, etc.

---

## 🔍 Troubleshooting

### If you get "refusing to merge unrelated histories"
```bash
git pull origin main --allow-unrelated-histories
```

### If you need to undo last commit (keep changes)
```bash
git reset --soft HEAD~1
```

### If you need to undo last commit (discard changes)
```bash
git reset --hard HEAD~1
```

### If you need to restore a deleted file
```bash
git checkout HEAD -- filename.js
```

---

**Last Updated:** 2025  
**Repository:** https://github.com/Ajaxy12/funktions2
