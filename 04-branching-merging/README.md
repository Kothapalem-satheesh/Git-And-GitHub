# 🌿 Branching & Merging

Branches allow you to work on different features simultaneously without affecting the main codebase. This is one of Git's most powerful features!

## 🎯 What are Branches?

A branch is a **separate line of development**. Think of it as creating a parallel universe where you can experiment without affecting the main timeline.

```
Main Branch:     A---B---C---F---G
                           \
Feature Branch:            D---E
```

*See `../images/diagrams/branching-concept.png` for visual representation*

## 💡 Why Use Branches?

- **Isolation**: Work on features without breaking main code
- **Experimentation**: Try new ideas safely
- **Collaboration**: Multiple people can work simultaneously
- **Organization**: Keep different features separate
- **Easy Rollback**: Delete branch if feature doesn't work

## 🌳 Understanding the Main Branch

The default branch is usually called `main` or `master`:

```bash
# View current branch
git branch

# View all branches
git branch -a

# See branch with last commit
git branch -v
```

## 🔨 Creating Branches

### Create and Switch

```bash
# Create and switch to new branch
git checkout -b feature-name

# Or using newer syntax
git switch -c feature-name

# Create branch from specific commit
git checkout -b new-branch <commit-hash>
```

### Create Without Switching

```bash
# Just create branch (stay on current)
git branch feature-name
```

## 🔄 Switching Branches

```bash
# Switch to branch
git checkout branch-name

# Or using newer syntax
git switch branch-name

# Switch to previous branch
git checkout -
```

## 📊 Viewing Branches

```bash
# List local branches
git branch

# List all branches (local + remote)
git branch -a

# List remote branches
git branch -r

# Show branch with last commit info
git branch -v

# Show merged branches
git branch --merged

# Show unmerged branches
git branch --no-merged
```

## 🗑️ Deleting Branches

```bash
# Delete local branch (must be on different branch)
git branch -d branch-name

# Force delete (even if not merged)
git branch -D branch-name

# Delete remote branch
git push origin --delete branch-name
```

## 🔀 Merging Branches

Merging combines changes from one branch into another.

### Fast-Forward Merge

When the branch you're merging is directly ahead:

```bash
# Switch to target branch (usually main)
git checkout main

# Merge feature branch
git merge feature-name
```

### Three-Way Merge

When branches have diverged:

```bash
git checkout main
git merge feature-name
# Git automatically creates a merge commit
```

## 🔀 Merge Types Visualized

```
Fast-Forward Merge:
main:    A---B---C
                \
feature:         D---E
                 
After merge:
main:    A---B---C---D---E
```

```
Three-Way Merge:
main:    A---B---C-------F
                \       /
feature:         D---E
                 
After merge:
main:    A---B---C---F (merge commit)
                \   /
                 D-E
```

*See `../images/diagrams/merge-types.png` for visual representation*

## ⚠️ Handling Merge Conflicts

When Git can't automatically merge, you'll get conflicts:

```bash
# When merge conflict occurs:
Auto-merging file.txt
CONFLICT (content): Merge conflict in file.txt
Automatic merge failed; fix conflicts and then commit the result.
```

### Resolving Conflicts

1. **Open conflicted file** - Look for conflict markers:

```text
<<<<<<< HEAD
Code from current branch (main)
=======
Code from branch being merged (feature)
>>>>>>> feature-name
```

2. **Edit the file** - Choose what to keep:

```text
Final code you want (remove markers)
```

3. **Stage the resolved file**:

```bash
git add file.txt
```

4. **Complete the merge**:

```bash
git commit
```

### Conflict Resolution Tools

```bash
# See conflicted files
git status

# Use merge tool (if configured)
git mergetool

# Abort merge if needed
git merge --abort
```

## 🔄 Common Branching Workflows

### Feature Branch Workflow

```bash
# 1. Start from main
git checkout main
git pull

# 2. Create feature branch
git checkout -b feature/user-login

# 3. Work on feature
# (Make changes, commit)

# 4. Push branch
git push -u origin feature/user-login

# 5. Merge to main (via Pull Request on GitHub)
# Or merge locally:
git checkout main
git merge feature/user-login
git push

# 6. Delete branch
git branch -d feature/user-login
```

### Git Flow (Advanced)

```
main (production)
  └── develop (development)
       ├── feature/user-auth
       ├── feature/payment
       └── hotfix/critical-bug
```

## 📋 Branch Naming Conventions

Good branch names are descriptive:

```bash
# Feature branches
feature/user-authentication
feature/add-search-function

# Bug fixes
bugfix/login-error
fix/memory-leak

# Hotfixes (urgent production fixes)
hotfix/security-patch

# Experiments
experiment/new-algorithm
```

## 🔍 Comparing Branches

```bash
# See differences between branches
git diff main..feature-branch

# See commits in feature not in main
git log main..feature-branch

# See commits in main not in feature
git log feature-branch..main

# See all differences
git diff main...feature-branch
```

## 🎯 Practical Example

Let's create a feature branch:

```bash
# 1. Start on main
git checkout main
git pull

# 2. Create feature branch
git checkout -b feature/add-dark-mode

# 3. Make changes
echo "Dark mode styles" > dark-mode.css
git add dark-mode.css
git commit -m "Add dark mode stylesheet"

# 4. Continue working
# (Make more commits)

# 5. Push to GitHub
git push -u origin feature/add-dark-mode

# 6. On GitHub: Create Pull Request
# 7. After PR approved, merge on GitHub
# 8. Update local main
git checkout main
git pull

# 9. Delete local branch
git branch -d feature/add-dark-mode
```

## 🖼️ Branch Visualization

```bash
# See branch structure
git log --oneline --graph --all

# Example output:
*   abc123 Merge feature/login
|\
| * def456 Add login form
| * ghi789 Add authentication
* | jkl012 Fix header bug
|/
* mno345 Initial commit
```

*See `../images/diagrams/branch-visualization.png` for visual representation*

## 💡 Pro Tips

### 1. Keep Branches Small
- One feature per branch
- Merge frequently
- Don't let branches get too old

### 2. Always Start from Updated Main
```bash
git checkout main
git pull
git checkout -b new-feature
```

### 3. Test Before Merging
- Run tests on feature branch
- Review code
- Then merge to main

### 4. Use Pull Requests
- Review code before merging
- Discuss changes
- Catch issues early

## 🖼️ Screenshots

Add screenshots to `../images/screenshots/04-branching-merging/`:
- `git-branch-output.png` - Branch list
- `merge-conflict.png` - Conflict markers in file
- `git-log-graph.png` - Branch visualization
- `github-branches.png` - GitHub branch interface

## ✅ Practice Exercise

1. Create a new branch called `feature/test-branch`
2. Make some changes and commit
3. Switch back to main
4. Make different changes on main
5. Merge your feature branch into main
6. If conflicts occur, resolve them
7. View branch history with `git log --graph`
8. Delete the feature branch

## 🎓 Key Takeaways

- Branches let you work on features in isolation
- `git checkout -b` creates and switches to branch
- `git merge` combines branches
- Conflicts happen when Git can't auto-merge
- Always test before merging to main
- Use descriptive branch names

## ➡️ Next Steps

Ready to collaborate? Learn about [Collaboration](./../05-collaboration/README.md)!


