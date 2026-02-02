# 🔄 Git Workflow

Understanding the Git workflow is crucial for effective version control. This guide covers the complete cycle of working with Git.

## 📊 The Git Workflow Cycle

```
┌─────────────┐
│   Working   │
│  Directory  │
└──────┬──────┘
       │ git add
       ↓
┌─────────────┐
│   Staging   │
│    Area     │
└──────┬──────┘
       │ git commit
       ↓
┌─────────────┐
│  Repository │
│  (History)  │
└─────────────┘
```

*See `../images/diagrams/git-workflow-cycle.png` for visual representation*

## 🎯 Three States of Files

### 1. **Modified (Unstaged)**
Files you've changed but haven't staged yet.

```bash
# Check what's modified
git status

# Example output:
# modified:   app.js
# modified:   styles.css
```

### 2. **Staged**
Files ready to be committed (snapshot).

```bash
# Stage files
git add app.js styles.css

# Now they're in staging area
git status
# Output: Changes to be committed:
#         modified:   app.js
#         modified:   styles.css
```

### 3. **Committed**
Files saved in the repository history.

```bash
# Commit staged files
git commit -m "Update app.js and styles.css"

# Now they're in repository
```

## 📝 Common Workflow Commands

### Staging Files

```bash
# Stage a single file
git add index.html

# Stage multiple files
git add file1.js file2.js file3.css

# Stage all files in current directory
git add .

# Stage all files in repository
git add -A
# or
git add --all

# Stage files interactively (choose what to add)
git add -p

# Stage all changes in a directory
git add src/
```

### Committing Changes

```bash
# Basic commit
git commit -m "Your commit message"

# Commit with detailed message
git commit -m "Title" -m "Detailed description
- Point 1
- Point 2"

# Commit and skip staging (only for tracked files)
git commit -am "Quick commit"

# Amend last commit (change message or add files)
git commit --amend -m "New message"
```

### Viewing Changes

```bash
# See unstaged changes
git diff

# See staged changes
git diff --staged
# or
git diff --cached

# See changes in specific file
git diff app.js

# See changes between commits
git diff HEAD~1 HEAD

# See what changed in last commit
git show

# See changes in specific commit
git show <commit-hash>
```

### Viewing History

```bash
# Full history
git log

# One line per commit
git log --oneline

# With graph visualization
git log --oneline --graph --all

# Last N commits
git log -5

# With file statistics
git log --stat

# Search commits by message
git log --grep="bug fix"

# Search commits by author
git log --author="John"

# See commits affecting a file
git log -- app.js
```

## 🔙 Undoing Changes

### Unstage Files (Keep Changes)

```bash
# Unstage a file
git reset HEAD filename.txt

# Unstage all files
git reset HEAD
```

### Discard Changes in Working Directory

```bash
# ⚠️ WARNING: This permanently deletes changes!

# Discard changes in a file
git checkout -- filename.txt
# or (newer syntax)
git restore filename.txt

# Discard all changes
git checkout -- .
# or
git restore .
```

### Undo Last Commit (Keep Changes)

```bash
# Undo commit but keep changes staged
git reset --soft HEAD~1

# Undo commit and unstage changes (keep files)
git reset HEAD~1
# or
git reset --mixed HEAD~1

# Undo commit and discard changes
git reset --hard HEAD~1
# ⚠️ WARNING: This deletes changes!
```

## 📋 Status Output Explained

When you run `git status`, you'll see:

```bash
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)
        modified:   README.md

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes)
        modified:   app.js

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        newfile.txt

no changes added to commit (use "git add" to track)
```

**Understanding the sections:**
- **Changes to be committed**: Files in staging area
- **Changes not staged**: Modified but not staged
- **Untracked files**: New files not yet added to Git

## 🎯 Practical Workflow Example

Let's walk through a typical workflow:

```bash
# 1. Check current status
git status

# 2. Make some changes to your files
# (Edit files in your editor)

# 3. See what changed
git diff

# 4. Stage the files you want to commit
git add app.js utils.js

# 5. Verify what's staged
git status
git diff --staged

# 6. Commit with a meaningful message
git commit -m "Add user authentication feature"

# 7. View your commit
git log --oneline -1

# 8. Continue working...
```

## 📊 Workflow Diagram

```
Start Working
     │
     ↓
Edit Files
     │
     ↓
git status  ← Check what changed
     │
     ↓
git diff    ← Review changes
     │
     ↓
git add     ← Stage files
     │
     ↓
git commit  ← Save snapshot
     │
     ↓
Continue...
```

*See `../images/diagrams/detailed-workflow.png` for visual representation*

## 💡 Pro Tips

### 1. Commit Often
Make small, frequent commits rather than large ones.

```bash
# Good: Small, focused commits
git commit -m "Add login button"
git commit -m "Style login form"
git commit -m "Add form validation"

# Bad: One huge commit
git commit -m "Add login feature with button, styling, and validation"
```

### 2. Review Before Committing
Always check what you're committing:

```bash
git diff --staged  # Review staged changes
git status         # See overall status
```

### 3. Write Good Commit Messages
- Use present tense: "Add feature" not "Added feature"
- Be specific: "Fix login bug" not "Fix bug"
- Keep first line under 50 characters
- Add details if needed

### 4. Use .gitignore
Create a `.gitignore` file to exclude files:

```bash
# .gitignore example
node_modules/
*.log
.env
.DS_Store
dist/
```

## 🖼️ Screenshots

Add screenshots to `../images/screenshots/02-git-workflow/`:
- `git-status-example.png` - Detailed status output
- `git-diff-example.png` - Example of diff output
- `git-log-graph.png` - Graph visualization of commits

## ✅ Practice Exercise

1. Create a file `todo.txt` with some tasks
2. Add and commit it
3. Modify the file (add/remove tasks)
4. Use `git diff` to see changes
5. Stage and commit the changes
6. Use `git log` to see your commits
7. Try unstaging a file with `git reset HEAD`
8. Practice viewing different commit formats

## 🎓 Key Takeaways

- Files go through: Modified → Staged → Committed
- `git add` moves files to staging
- `git commit` saves to repository
- `git diff` shows what changed
- `git log` shows history
- You can undo changes at different stages

## ➡️ Next Steps

Ready for GitHub? Learn about [GitHub Essentials](./../03-github-essentials/README.md)!


