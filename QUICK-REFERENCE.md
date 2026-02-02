# ⚡ Git & GitHub Quick Reference

A quick cheat sheet for common Git and GitHub commands.

## 🔧 Setup & Configuration

```bash
# Configure user
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# View configuration
git config --list

# Set default editor
git config --global core.editor "code --wait"
```

## 📦 Repository Operations

```bash
# Initialize repository
git init

# Clone repository
git clone <url>

# View remotes
git remote -v

# Add remote
git remote add origin <url>

# Remove remote
git remote remove origin
```

## 📊 Status & Information

```bash
# Check status
git status

# View changes
git diff

# View staged changes
git diff --staged

# View commit history
git log
git log --oneline
git log --graph --all --decorate

# View specific commit
git show <commit-hash>
```

## 📝 Staging & Committing

```bash
# Stage file
git add <file>

# Stage all files
git add .

# Stage all changes
git add -A

# Commit
git commit -m "Message"

# Commit all tracked files (skip staging)
git commit -am "Message"

# Amend last commit
git commit --amend -m "New message"
```

## 🌿 Branching

```bash
# List branches
git branch

# Create branch
git branch <name>

# Create and switch
git checkout -b <name>
git switch -c <name>

# Switch branch
git checkout <name>
git switch <name>

# Delete branch
git branch -d <name>
git branch -D <name>  # Force delete
```

## 🔀 Merging

```bash
# Merge branch
git checkout main
git merge <branch-name>

# Abort merge
git merge --abort
```

## 🔄 Remote Operations

```bash
# Push to remote
git push
git push origin <branch>

# Push and set upstream
git push -u origin <branch>

# Pull from remote
git pull
git pull origin <branch>

# Fetch (no merge)
git fetch
git fetch origin
```

## 🔙 Undoing Changes

```bash
# Unstage file
git reset HEAD <file>

# Discard changes (⚠️ destructive)
git checkout -- <file>
git restore <file>

# Undo last commit (keep changes)
git reset HEAD~1

# Undo last commit (discard changes)
git reset --hard HEAD~1  # ⚠️ destructive
```

## 📦 Stashing

```bash
# Stash changes
git stash
git stash save "Message"

# List stashes
git stash list

# Apply stash
git stash apply
git stash pop

# Delete stash
git stash drop
git stash clear
```

## 🔖 Tags

```bash
# Create tag
git tag <name>
git tag -a <name> -m "Message"

# List tags
git tag

# Push tags
git push --tags
git push origin <tag-name>

# Delete tag
git tag -d <name>
git push origin --delete <tag-name>
```

## 🔍 Searching

```bash
# Search commits
git log --grep="search term"
git log --author="Name"

# Search code
git log -S "functionName"

# Find file history
git log -- <file>

# Blame (who changed what)
git blame <file>
```

## 🧹 Cleaning

```bash
# Remove untracked files
git clean -n    # Preview
git clean -f    # Remove files
git clean -fd   # Remove files and directories
```

## 🔄 Rebasing

```bash
# Rebase onto branch
git rebase <branch>

# Interactive rebase
git rebase -i HEAD~3

# Abort rebase
git rebase --abort

# Continue after resolving conflicts
git rebase --continue
```

## 🎯 Cherry-Picking

```bash
# Apply specific commit
git cherry-pick <commit-hash>

# Cherry-pick without committing
git cherry-pick -n <commit-hash>
```

## 📋 Useful Aliases

```bash
# Create aliases
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.lg "log --oneline --graph --all --decorate"
```

## 🚨 Emergency Commands

```bash
# Recover "lost" commits
git reflog
git checkout <commit-hash>

# Find when bug was introduced
git bisect start
git bisect bad
git bisect good <commit-hash>
# Test and mark good/bad, repeat
git bisect reset
```

## 📚 Common Workflows

### Daily Workflow
```bash
git pull                    # Get latest
# Make changes
git add .
git commit -m "Message"
git push
```

### Feature Branch
```bash
git checkout main
git pull
git checkout -b feature/name
# Work and commit
git push -u origin feature/name
# Create PR on GitHub
# After merge:
git checkout main
git pull
git branch -d feature/name
```

### Fix Merge Conflict
```bash
# When conflict occurs:
# 1. Open conflicted file
# 2. Resolve conflicts (remove markers)
# 3. Stage file
git add <file>
# 4. Complete merge
git commit
```

## 🎓 Best Practices

- ✅ Commit often with clear messages
- ✅ Use branches for features
- ✅ Pull before pushing
- ✅ Review before committing
- ✅ Write descriptive commit messages
- ✅ Never commit secrets
- ✅ Keep commits focused

---

**Print this page or keep it handy while learning!** 📌

