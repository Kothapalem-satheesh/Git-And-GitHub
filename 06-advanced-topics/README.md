# 🚀 Advanced Git Topics

Once you've mastered the basics, these advanced topics will make you a Git power user!

## 🔖 Tags and Releases

Tags mark specific points in history (like version numbers).

### Creating Tags

```bash
# Lightweight tag (just a pointer)
git tag v1.0.0

# Annotated tag (recommended - has metadata)
git tag -a v1.0.0 -m "Release version 1.0.0"

# Tag specific commit
git tag -a v1.0.0 <commit-hash> -m "Release 1.0.0"
```

### Viewing Tags

```bash
# List all tags
git tag

# List tags matching pattern
git tag -l "v1.*"

# Show tag details
git show v1.0.0
```

### Pushing Tags

```bash
# Push single tag
git push origin v1.0.0

# Push all tags
git push --tags

# Push all tags (alternative)
git push origin --tags
```

### Deleting Tags

```bash
# Delete local tag
git tag -d v1.0.0

# Delete remote tag
git push origin --delete v1.0.0
# or
git push origin :refs/tags/v1.0.0
```

### GitHub Releases

1. Go to repository → **Releases** → **Create a new release**
2. Choose tag (or create new)
3. Add release title and description
4. Attach binaries if needed
5. Publish release

## 📦 Stashing Changes

Stashing temporarily saves your changes so you can switch branches.

### Basic Stashing

```bash
# Stash current changes
git stash

# Stash with message
git stash save "Work in progress on feature X"

# Stash including untracked files
git stash -u
# or
git stash --include-untracked
```

### Viewing Stashes

```bash
# List stashes
git stash list

# Show stash contents
git stash show

# Show detailed diff
git stash show -p
```

### Applying Stashes

```bash
# Apply most recent stash (keeps stash)
git stash apply

# Apply specific stash
git stash apply stash@{2}

# Apply and remove from stash list
git stash pop

# Apply specific stash and remove
git stash pop stash@{2}
```

### Managing Stashes

```bash
# Delete specific stash
git stash drop stash@{1}

# Delete all stashes
git stash clear

# Create branch from stash
git stash branch new-branch-name
```

## 🔄 Rebasing

Rebasing replays commits on top of another branch (alternative to merging).

### Basic Rebase

```bash
# Rebase current branch onto main
git checkout feature-branch
git rebase main

# Rebase interactively
git rebase -i main
```

### Interactive Rebase

```bash
# Rebase last 3 commits
git rebase -i HEAD~3

# Options in interactive rebase:
# pick - use commit as-is
# reword - change commit message
# edit - modify commit
# squash - combine with previous
# fixup - like squash but discard message
# drop - remove commit
```

### Rebase vs Merge

**Merge:**
```
main:    A---B---C-------F
                \       /
feature:         D---E
```
Creates merge commit, preserves history.

**Rebase:**
```
main:    A---B---C
                \
feature:         D'---E'
```
Linear history, no merge commit.

### When to Rebase

✅ **Good for:**
- Cleaning up commit history
- Keeping feature branch up-to-date
- Before merging to main

❌ **Avoid:**
- Rebasing public/shared branches
- After pushing to remote (unless force push)

### Aborting Rebase

```bash
# If conflicts occur during rebase
git rebase --abort

# Continue after resolving conflicts
git add .
git rebase --continue
```

## 🎣 Git Hooks

Hooks are scripts that run automatically at certain Git events.

### Hook Types

**Client-side hooks:**
- `pre-commit`: Before commit
- `commit-msg`: Validate commit message
- `post-commit`: After commit
- `pre-push`: Before push

**Server-side hooks:**
- `pre-receive`: Before accepting pushes
- `update`: Before updating ref
- `post-receive`: After accepting pushes

### Creating Hooks

```bash
# Hooks are in .git/hooks/
# Example: pre-commit hook
cat > .git/hooks/pre-commit << 'EOF'
#!/bin/sh
# Run linter before commit
npm run lint
EOF

chmod +x .git/hooks/pre-commit
```

### Pre-commit Hook Example

```bash
#!/bin/sh
# Prevent committing to main directly
branch="$(git rev-parse --abbrev-ref HEAD)"
if [ "$branch" = "main" ]; then
  echo "You can't commit directly to main!"
  exit 1
fi
```

## 🔍 Advanced Searching

### Searching Commits

```bash
# Search commit messages
git log --grep="bug fix"

# Search by author
git log --author="John"

# Search by date
git log --since="2024-01-01" --until="2024-12-31"

# Search in code
git log -S "functionName" --source --all

# Search in specific file
git log -- path/to/file.js
```

### Searching Code

```bash
# Find when function was added
git log -p -S "functionName"

# Find when line was added/removed
git log -L :functionName:file.js

# Blame (who changed what line)
git blame file.js
```

## 🧹 Cleaning Up

### Remove Untracked Files

```bash
# See what would be removed
git clean -n

# Remove untracked files
git clean -f

# Remove untracked files and directories
git clean -fd

# Interactive removal
git clean -i
```

### Prune Remote References

```bash
# Remove deleted remote branches locally
git remote prune origin

# Or
git fetch --prune
```

## 📊 Advanced Logging

```bash
# Custom format
git log --pretty=format:"%h - %an, %ar : %s"

# Graph with decorations
git log --oneline --graph --all --decorate

# Show file statistics
git log --stat

# Show only merge commits
git log --merges

# Show commits that changed specific lines
git log -L 10,20:file.js
```

### Log Format Options

- `%h` - Abbreviated commit hash
- `%an` - Author name
- `%ar` - Author date, relative
- `%s` - Subject (commit message)
- `%d` - Ref names

## 🔐 Advanced Remote Operations

### Multiple Remotes

```bash
# Add multiple remotes
git remote add upstream https://github.com/original/repo.git
git remote add fork https://github.com/yourname/repo.git

# Push to specific remote
git push upstream main
git push fork main

# Fetch from all remotes
git fetch --all
```

### Remote Tracking

```bash
# Set upstream for branch
git branch --set-upstream-to=origin/main main

# Push and set upstream
git push -u origin main
```

## 🎯 Cherry-Picking

Apply specific commits from one branch to another.

```bash
# Cherry-pick a commit
git checkout main
git cherry-pick <commit-hash>

# Cherry-pick multiple commits
git cherry-pick commit1 commit2 commit3

# Cherry-pick range
git cherry-pick commit1^..commit3

# Cherry-pick without committing
git cherry-pick -n <commit-hash>
```

## 📝 Rewriting History

### Amend Last Commit

```bash
# Change last commit message
git commit --amend -m "New message"

# Add files to last commit
git add forgotten-file.js
git commit --amend --no-edit
```

### Interactive Rebase for History

```bash
# Edit last 3 commits
git rebase -i HEAD~3

# In editor:
# - Change 'pick' to 'edit' to modify commit
# - Change to 'squash' to combine commits
# - Change to 'reword' to change message
```

## 🖼️ Advanced Visualization

```bash
# Show branch structure
git log --graph --oneline --all --decorate

# Show file history
git log --follow -- file.js

# Show changes over time
git log --stat --graph

# Custom graph
git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset'
```

## 💡 Pro Tips

### 1. Use Aliases

```bash
# Create useful aliases
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.lg "log --oneline --graph --all --decorate"

# Now use: git st, git co, git br, git lg
```

### 2. Reflog (Safety Net)

```bash
# See all recent actions
git reflog

# Recover "lost" commits
git reflog
git checkout <commit-hash>
```

### 3. Bisect (Find Bugs)

```bash
# Start bisect
git bisect start

# Mark current as bad
git bisect bad

# Mark known good commit
git bisect good <commit-hash>

# Git checks out middle commit
# Test and mark good/bad
git bisect good  # or bad

# Continue until bug is found
git bisect reset  # when done
```

## 🖼️ Screenshots

Add screenshots to `../images/screenshots/06-advanced-topics/`:
- `git-tags.png` - Tags in repository
- `github-release.png` - Creating GitHub release
- `rebase-diagram.png` - Rebase visualization
- `git-hooks.png` - Hooks directory

## ✅ Practice Exercise

1. Create and push a tag
2. Make changes, stash them, switch branches
3. Practice interactive rebase
4. Create a pre-commit hook
5. Use cherry-pick to apply a commit
6. Create useful Git aliases
7. Explore reflog

## 🎓 Key Takeaways

- Tags mark important versions
- Stashing saves work temporarily
- Rebasing creates linear history
- Hooks automate Git workflows
- Cherry-picking applies specific commits
- Reflog helps recover "lost" work

## ➡️ Next Steps

Learn [Best Practices](./../07-best-practices/README.md) to use Git effectively!

---

**Pro Tip:** Master these advanced features to become a Git expert! 🚀

