# 🤝 Collaboration with Git & GitHub

Learn how to work effectively with teams using Git and GitHub. This guide covers forking, pull requests, code reviews, and team workflows.

## 🌐 Collaboration Concepts

### Repository Ownership Models

1. **Direct Access**: Team members have write access
2. **Fork & Pull Request**: Contributors fork, make changes, submit PRs
3. **Organization**: Multiple repositories under one organization

## 🍴 Forking Repositories

Forking creates your own copy of someone else's repository.

### Why Fork?

- Contribute to open source projects
- Experiment without affecting original
- Create your own version
- Submit changes via Pull Requests

### How to Fork

**On GitHub:**
1. Go to repository you want to fork
2. Click **"Fork"** button (top right)
3. Choose where to fork (your account or organization)
4. Done! You now have your own copy

**Clone Your Fork:**
```bash
# Clone your fork
git clone https://github.com/your-username/repo-name.git
cd repo-name

# Add original as upstream (to sync changes)
git remote add upstream https://github.com/original-owner/repo-name.git

# Verify remotes
git remote -v
```

### Keeping Fork Updated

```bash
# Fetch changes from original repository
git fetch upstream

# Switch to main branch
git checkout main

# Merge upstream changes
git merge upstream/main

# Push to your fork
git push
```

## 🔄 Pull Requests (PRs)

Pull Requests let you propose changes to a repository.

### Creating a Pull Request

**Step 1: Make Changes**
```bash
# Fork and clone repository
git clone https://github.com/your-username/repo-name.git
cd repo-name

# Create feature branch
git checkout -b feature/my-contribution

# Make changes
# (Edit files, add features, fix bugs)

# Commit changes
git add .
git commit -m "Add new feature"

# Push to your fork
git push -u origin feature/my-contribution
```

**Step 2: Open Pull Request on GitHub**
1. Go to your fork on GitHub
2. Click **"Compare & pull request"** button
3. Fill out PR description:
   - What changes you made
   - Why you made them
   - Any related issues
4. Click **"Create pull request"**

### PR Best Practices

**Good PR Description:**
```markdown
## Description
Adds user authentication feature with login and signup.

## Changes
- Added login form component
- Implemented JWT token authentication
- Added password validation
- Created user session management

## Related Issues
Closes #123

## Testing
- [x] Unit tests pass
- [x] Manual testing completed
- [x] No breaking changes
```

**PR Checklist:**
- [ ] Code follows project style
- [ ] Tests added/updated
- [ ] Documentation updated
- [ ] No merge conflicts
- [ ] PR description is clear

## 👥 Code Reviews

### As a Reviewer

**What to Look For:**
- Code quality and style
- Logic correctness
- Performance issues
- Security concerns
- Test coverage
- Documentation

**Review Comments:**
```markdown
# Good review comment
This function could be optimized. Consider using a hash map 
instead of nested loops for O(n) instead of O(n²) complexity.

# Suggestion
Maybe add error handling here? What if the API call fails?
```

### As a Contributor

**Responding to Reviews:**
1. Read all comments carefully
2. Ask questions if unclear
3. Make requested changes
4. Push updates to same branch
5. Mark conversations as resolved
6. Request re-review if needed

```bash
# Make changes based on review
git add .
git commit -m "Address review comments: add error handling"
git push
```

## 🏢 Team Workflows

### Centralized Workflow

Small teams with direct access:

```bash
# Everyone works on main
git checkout main
git pull
# Make changes
git add .
git commit -m "Changes"
git push
```

### Feature Branch Workflow

Each feature gets its own branch:

```bash
# Create feature branch
git checkout -b feature/new-feature

# Work and commit
git add .
git commit -m "Work in progress"

# Push branch
git push -u origin feature/new-feature

# Create PR on GitHub
# After approval, merge via GitHub
```

### Git Flow

Structured branching model:

```
main (production)
  └── develop (integration)
       ├── feature/* (new features)
       ├── release/* (preparing release)
       └── hotfix/* (urgent fixes)
```

## 🔐 Permissions & Access

### Repository Roles

1. **Owner**: Full control
2. **Admin**: Manage settings
3. **Write**: Push directly
4. **Read**: Clone and view
5. **Triage**: Manage issues/PRs
6. **Maintain**: Merge PRs

### Adding Collaborators

**On GitHub:**
1. Repository → Settings → Collaborators
2. Add username or email
3. Choose permission level
4. Collaborator accepts invitation

## 📋 Issue Tracking

### Creating Issues

**Good Issue Template:**
```markdown
## Description
Brief description of the problem or feature request.

## Steps to Reproduce (for bugs)
1. Step one
2. Step two
3. See error

## Expected Behavior
What should happen

## Actual Behavior
What actually happens

## Environment
- OS: Windows 10
- Browser: Chrome 90
- Version: 1.2.3
```

### Linking Issues to Commits

```bash
# Reference issue in commit
git commit -m "Fix login bug

Closes #123"
# or
git commit -m "Add feature (Fixes #456)"
```

## 🔍 Reviewing Changes

### Viewing PR Changes

On GitHub:
- **Files changed** tab shows all modifications
- **Conversation** tab shows discussion
- **Commits** tab shows commit history
- **Checks** tab shows CI/CD status

### Local Review

```bash
# Checkout PR locally
git fetch origin pull/123/head:pr-123
git checkout pr-123

# Review changes
git diff main..pr-123

# Test the changes
# (Run tests, manual testing)

# Switch back
git checkout main
```

## 🚀 Collaborative Best Practices

### 1. Communication
- Use clear commit messages
- Write descriptive PR descriptions
- Comment on code when needed
- Respond to reviews promptly

### 2. Keep PRs Small
- One feature per PR
- Easier to review
- Faster to merge
- Less conflict-prone

### 3. Sync Frequently
```bash
# Update your branch before creating PR
git checkout main
git pull
git checkout your-branch
git merge main
# Resolve conflicts if any
git push
```

### 4. Use Labels
- `bug`: Something broken
- `enhancement`: New feature
- `documentation`: Docs update
- `good first issue`: Beginner-friendly

### 5. Follow Code Style
- Use project's linter
- Follow naming conventions
- Match existing code style
- Run tests before PR

## 🖼️ Collaboration Workflow Diagram

```
Developer A          Developer B          Main Repository
     │                    │                      │
     │  Fork             │                      │
     ├───────────────────┼──────────────────────┤
     │                    │                      │
     │  Clone            │                      │
     │<──────────────────┼──────────────────────┤
     │                    │                      │
     │  Work & Commit    │  Work & Commit       │
     │                    │                      │
     │  Push             │  Push                 │
     ├───────────────────┼──────────────────────┤
     │                    │                      │
     │  Create PR        │  Create PR            │
     ├───────────────────┼──────────────────────>│
     │                    │                      │
     │                    │                      │ Review
     │                    │                      │ Merge
     │                    │                      │
     │  Pull Updates     │  Pull Updates         │
     │<──────────────────┼──────────────────────┤
```

*See `../images/diagrams/collaboration-workflow.png` for visual representation*

## 🖼️ Screenshots

Add screenshots to `../images/screenshots/05-collaboration/`:
- `fork-button.png` - How to fork a repository
- `create-pr.png` - Creating a pull request
- `pr-page.png` - Pull request interface
- `code-review.png` - Code review comments
- `merge-pr.png` - Merging a pull request

## ✅ Practice Exercise

1. Fork a repository (or use your own)
2. Clone your fork
3. Create a feature branch
4. Make some changes
5. Push to your fork
6. Create a Pull Request
7. Review the PR interface
8. Practice resolving merge conflicts

## 🎓 Key Takeaways

- Forking creates your copy of a repository
- Pull Requests propose changes
- Code reviews improve code quality
- Keep PRs small and focused
- Communicate clearly with team
- Sync frequently to avoid conflicts

## ➡️ Next Steps

Ready for advanced topics? Check out [Advanced Topics](./../06-advanced-topics/README.md)!


