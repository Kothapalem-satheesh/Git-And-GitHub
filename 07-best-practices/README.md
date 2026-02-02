# ✨ Git & GitHub Best Practices

Follow these best practices to use Git and GitHub effectively in your projects.

## 📝 Commit Messages

### Good Commit Messages

**Format:**
```
<type>: <subject>

<body (optional)>

<footer (optional)>
```

**Examples:**

```bash
# Good
git commit -m "feat: Add user authentication

- Implemented login functionality
- Added JWT token management
- Created user session handling

Closes #123"

# Also good (simpler)
git commit -m "fix: Resolve memory leak in image processing"
git commit -m "docs: Update API documentation"
git commit -m "refactor: Simplify authentication logic"
```

### Commit Message Types

- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style (formatting, no logic change)
- `refactor`: Code restructuring
- `test`: Adding/updating tests
- `chore`: Maintenance tasks

### Commit Message Rules

✅ **Do:**
- Write in present tense: "Add feature" not "Added feature"
- Keep first line under 50 characters
- Be specific and descriptive
- Explain why, not just what (in body)

❌ **Don't:**
- Write vague messages: "Update files"
- Write too long first line
- Use past tense: "Fixed bug"
- Commit unrelated changes together

## 🌿 Branch Naming

### Good Branch Names

```bash
# Feature branches
feature/user-authentication
feature/add-dark-mode
feature/payment-integration

# Bug fixes
bugfix/login-error
fix/memory-leak
fix/header-styling

# Hotfixes
hotfix/security-patch
hotfix/critical-bug

# Experiments
experiment/new-algorithm
experiment/performance-test
```

### Branch Naming Rules

✅ **Do:**
- Use descriptive names
- Include type prefix (feature/, fix/, etc.)
- Use kebab-case (hyphens)
- Keep names concise but clear

❌ **Don't:**
- Use vague names: `branch1`, `test`, `new`
- Use spaces or special characters
- Make names too long
- Use your name: `john-branch`

## 📁 Repository Structure

### Recommended Structure

```
project-name/
├── README.md              # Project overview
├── LICENSE                # License file
├── .gitignore            # Ignore patterns
├── CONTRIBUTING.md        # Contribution guidelines
├── CHANGELOG.md           # Version history
├── docs/                  # Documentation
│   ├── api/
│   └── guides/
├── src/                   # Source code
│   ├── components/
│   ├── utils/
│   └── tests/
├── tests/                 # Test files
├── examples/              # Example code
└── .github/               # GitHub configs
    ├── workflows/         # CI/CD
    └── ISSUE_TEMPLATE/    # Issue templates
```

## 🚫 .gitignore Best Practices

### Common .gitignore Patterns

```gitignore
# Dependencies
node_modules/
vendor/
venv/
__pycache__/

# Build outputs
dist/
build/
*.o
*.exe

# Environment variables
.env
.env.local
.env.*.local

# IDE files
.vscode/
.idea/
*.swp
*.swo
*~

# OS files
.DS_Store
Thumbs.db
desktop.ini

# Logs
*.log
logs/
npm-debug.log*

# Temporary files
*.tmp
*.temp
.cache/
```

### Language-Specific .gitignore

**Node.js:**
```gitignore
node_modules/
npm-debug.log*
yarn-error.log*
.npm
.yarn/
```

**Python:**
```gitignore
__pycache__/
*.py[cod]
*$py.class
venv/
env/
```

**Java:**
```gitignore
*.class
*.jar
*.war
target/
```

## 🔄 Workflow Best Practices

### 1. Commit Often, Push Regularly

```bash
# Good: Small, frequent commits
git commit -m "Add login button"
git commit -m "Style login form"
git commit -m "Add form validation"

# Bad: One huge commit
git commit -m "Complete login feature with everything"
```

### 2. Keep Main Branch Stable

- Never commit directly to main (use branches)
- Always test before merging
- Use branch protection on GitHub
- Require pull requests for main

### 3. Review Before Committing

```bash
# Always check what you're committing
git status
git diff
git diff --staged
```

### 4. Sync Frequently

```bash
# Start each session by pulling latest
git checkout main
git pull

# Create branch from updated main
git checkout -b feature/new-feature
```

## 🤝 Collaboration Best Practices

### Pull Request Guidelines

**Good PR:**
- Small and focused (one feature/fix)
- Clear description
- Related issues linked
- Tests included
- Documentation updated
- No merge conflicts

**PR Template:**
```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Documentation update
- [ ] Refactoring

## Testing
- [ ] Tests pass locally
- [ ] Manual testing completed

## Checklist
- [ ] Code follows style guidelines
- [ ] Self-review completed
- [ ] Comments added for complex code
- [ ] Documentation updated
```

### Code Review Etiquette

**As Reviewer:**
- Be constructive and kind
- Explain why, not just what
- Suggest alternatives
- Approve when ready

**As Author:**
- Respond to all comments
- Ask questions if unclear
- Make requested changes
- Thank reviewers

## 🔒 Security Best Practices

### 1. Never Commit Secrets

```bash
# ❌ NEVER commit these:
- API keys
- Passwords
- Private keys
- .env files with secrets
- Database credentials
```

**Use environment variables:**
```bash
# .env (in .gitignore)
API_KEY=your-secret-key
DB_PASSWORD=secret-password
```

### 2. Use SSH Keys

```bash
# More secure than HTTPS tokens
ssh-keygen -t ed25519 -C "your_email@example.com"
# Add to GitHub: Settings → SSH and GPG keys
```

### 3. Review Changes Before Pushing

```bash
# Always review what you're pushing
git log origin/main..HEAD
git diff origin/main..HEAD
```

## 📊 Git Configuration

### Useful Global Config

```bash
# Set default editor
git config --global core.editor "code --wait"

# Set default branch name
git config --global init.defaultBranch main

# Enable color output
git config --global color.ui auto

# Set push behavior
git config --global push.default simple

# Create useful aliases
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
```

### Useful Aliases

```bash
# Add to ~/.gitconfig
[alias]
    st = status
    co = checkout
    br = branch
    ci = commit
    unstage = reset HEAD --
    last = log -1 HEAD
    visual = !gitk
    lg = log --oneline --graph --all --decorate
    who = shortlog -sn
    amend = commit --amend
    wipe = !git add -A && git commit -m "WIP" && git reset HEAD~1
```

## 🎯 Common Mistakes to Avoid

### 1. Committing to Main Directly

```bash
# ❌ Bad
git checkout main
git commit -m "New feature"

# ✅ Good
git checkout -b feature/new-feature
git commit -m "New feature"
git push -u origin feature/new-feature
# Create PR on GitHub
```

### 2. Force Pushing to Shared Branches

```bash
# ❌ Bad (on shared branches)
git push --force

# ✅ Good (only on your feature branches)
git push --force-with-lease
```

### 3. Large Commits

```bash
# ❌ Bad
git add .
git commit -m "Everything"

# ✅ Good
git add file1.js
git commit -m "Add user model"
git add file2.js
git commit -m "Add authentication"
```

### 4. Ignoring .gitignore

```bash
# ❌ Bad: Committing node_modules, .env, etc.

# ✅ Good: Proper .gitignore
# Check what you're adding
git status
git add .
```

## 📚 Documentation Best Practices

### README.md Should Include

- Project description
- Installation instructions
- Usage examples
- Contributing guidelines
- License information
- Screenshots/GIFs
- Badges (build status, version, etc.)

### Keep Documentation Updated

- Update README when features change
- Document breaking changes
- Include migration guides
- Keep examples current

## 🖼️ Screenshots

Add screenshots to `../images/screenshots/07-best-practices/`:
- `good-commit-messages.png` - Examples of good commits
- `branch-naming.png` - Branch naming examples
- `pr-template.png` - Pull request template
- `gitignore-example.png` - .gitignore file

## ✅ Checklist for New Projects

- [ ] Initialize Git repository
- [ ] Create .gitignore
- [ ] Add README.md
- [ ] Create LICENSE file
- [ ] Set up branch protection (on GitHub)
- [ ] Configure Git user name/email
- [ ] Create initial commit
- [ ] Push to GitHub
- [ ] Add collaborators (if team project)

## 🎓 Key Takeaways

- Write clear, descriptive commit messages
- Use consistent branch naming
- Keep commits small and focused
- Never commit secrets
- Review before committing
- Use branches for features
- Keep main branch stable
- Document your project well

## 📖 Additional Resources

- [Conventional Commits](https://www.conventionalcommits.org/)
- [GitHub Flow](https://guides.github.com/introduction/flow/)
- [Git Flow](https://nvie.com/posts/a-successful-git-branching-model/)
- [Semantic Versioning](https://semver.org/)

---

**Remember:** Good practices make collaboration easier and code safer! ✨

