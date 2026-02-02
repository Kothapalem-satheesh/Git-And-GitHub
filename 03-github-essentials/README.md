# 🐙 GitHub Essentials

GitHub is a cloud-based platform that hosts Git repositories. It's like a social network for code where you can store, share, and collaborate on projects.

## 🌐 What is GitHub?

**Git vs GitHub:**
- **Git**: Version control system (runs on your computer)
- **GitHub**: Platform that hosts Git repositories (cloud-based)

Think of it like:
- Git = The engine (version control)
- GitHub = The garage (where you store and share your projects)

## 🎯 Why Use GitHub?

1. **Cloud Backup**: Your code is safe in the cloud
2. **Collaboration**: Work with teams easily
3. **Portfolio**: Showcase your work
4. **Open Source**: Contribute to projects
5. **Free Hosting**: Host websites with GitHub Pages
6. **Issue Tracking**: Manage bugs and features
7. **Pull Requests**: Review code before merging

## 🚀 Getting Started

### Step 1: Create a GitHub Account

1. Go to [github.com](https://github.com)
2. Click "Sign up"
3. Choose a username (this will be in your repository URLs)
4. Verify your email

### Step 2: Install GitHub CLI (Optional but Recommended)

```bash
# Windows (using winget)
winget install --id GitHub.cli

# macOS
brew install gh

# Linux
# Follow instructions at https://cli.github.com/
```

### Step 3: Authenticate

```bash
# Login via CLI
gh auth login

# Or use SSH keys (more secure)
# See: https://docs.github.com/en/authentication
```

## 📦 Creating a Repository

### Method 1: Create on GitHub Website

1. Click the **"+"** icon → **"New repository"**
2. Enter repository name
3. Choose public or private
4. **Don't** initialize with README (if you have local code)
5. Click **"Create repository"**

### Method 2: Create via Command Line

```bash
# Create new repo on GitHub
gh repo create my-project --public

# Or create with description
gh repo create my-project --public --description "My awesome project"
```

## 🔗 Connecting Local Repository to GitHub

### Push Existing Local Repository

```bash
# 1. Create repository on GitHub first (via website or CLI)

# 2. Add remote (replace with your username and repo name)
git remote add origin https://github.com/username/repo-name.git

# 3. Verify remote
git remote -v

# 4. Push your code
git push -u origin main
# or
git push -u origin master
```

### Clone Existing Repository

```bash
# Clone via HTTPS
git clone https://github.com/username/repo-name.git

# Clone via SSH (if you have SSH keys set up)
git clone git@github.com:username/repo-name.git

# Clone into specific folder
git clone https://github.com/username/repo-name.git my-folder
```

## 📤 Pushing to GitHub

### First Time Push

```bash
# Add remote
git remote add origin https://github.com/username/repo-name.git

# Push and set upstream
git push -u origin main
```

### Subsequent Pushes

```bash
# Simple push (after setting upstream)
git push

# Push to specific branch
git push origin branch-name

# Force push (⚠️ use with caution!)
git push --force
```

## 📥 Pulling from GitHub

```bash
# Pull latest changes
git pull

# Pull from specific branch
git pull origin main

# Fetch without merging
git fetch

# Fetch and merge
git fetch origin
git merge origin/main
```

## 🔄 Common Workflow: Local ↔ GitHub

```
Local Computer          GitHub
     │                    │
     │  git push          │
     ├───────────────────>│
     │                    │
     │  git pull          │
     │<───────────────────┤
     │                    │
```

*See `../images/diagrams/github-workflow.png` for visual representation*

### Daily Workflow

```bash
# 1. Start your day - get latest changes
git pull

# 2. Make your changes locally
# (Edit files, add features, etc.)

# 3. Stage and commit
git add .
git commit -m "Add new feature"

# 4. Push to GitHub
git push

# 5. Repeat!
```

## 🌿 Understanding Branches on GitHub

```bash
# Push a new branch
git push -u origin new-branch-name

# Push all branches
git push --all

# Delete branch on GitHub
git push origin --delete branch-name
```

## 📋 Remote Repository Commands

```bash
# View remotes
git remote -v

# Add remote
git remote add origin <url>

# Remove remote
git remote remove origin

# Change remote URL
git remote set-url origin <new-url>

# Rename remote
git remote rename old-name new-name
```

## 🔐 Authentication Methods

### 1. Personal Access Token (HTTPS)

```bash
# When prompted, use your token instead of password
# Generate token: GitHub → Settings → Developer settings → Personal access tokens
git push
# Username: your-username
# Password: your-token
```

### 2. SSH Keys (Recommended)

```bash
# Generate SSH key
ssh-keygen -t ed25519 -C "your_email@example.com"

# Add to SSH agent
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# Copy public key
cat ~/.ssh/id_ed25519.pub
# Add to GitHub: Settings → SSH and GPG keys → New SSH key

# Test connection
ssh -T git@github.com
```

## 📁 Repository Structure Best Practices

A well-organized repository should have:

```
my-project/
├── README.md          # Project description
├── .gitignore         # Files to ignore
├── LICENSE            # License file
├── CONTRIBUTING.md    # How to contribute
├── src/               # Source code
├── docs/              # Documentation
├── tests/             # Test files
└── examples/          # Example code
```

## 📝 README.md Template

Create a good README for your repository:

```markdown
# Project Name

Brief description of your project.

## Features

- Feature 1
- Feature 2
- Feature 3

## Installation

```bash
git clone https://github.com/username/repo-name.git
cd repo-name
npm install
```

## Usage

```bash
npm start
```

## Contributing

Pull requests are welcome!

## License

MIT
```

## 🖼️ GitHub Interface Overview

### Key Areas:

1. **Repository Tabs**: Code, Issues, Pull Requests, Actions
2. **Branch Selector**: Switch between branches
3. **Clone Button**: Get repository URL
4. **File Browser**: Navigate your code
5. **Commit History**: See all commits
6. **Releases**: Version tags

*See `../images/screenshots/03-github-essentials/github-interface.png` for visual guide*

## 💡 Pro Tips

### 1. Use .gitignore
Don't commit unnecessary files:

```bash
# .gitignore example
node_modules/
.env
*.log
.DS_Store
dist/
build/
```

### 2. Write Good README
- Clear description
- Installation instructions
- Usage examples
- Screenshots/GIFs
- Contributing guidelines

### 3. Use Issues
Track bugs and features:
- Create issues for bugs
- Use labels to organize
- Link issues to commits: `git commit -m "Fix #123"`

### 4. Protect Main Branch
- Use branch protection rules
- Require pull requests
- Require reviews

## 🖼️ Screenshots

Add screenshots to `../images/screenshots/03-github-essentials/`:
- `github-homepage.png` - GitHub homepage
- `create-repo.png` - Creating a new repository
- `repository-page.png` - Repository main page
- `clone-button.png` - How to clone repository
- `push-command.png` - Terminal showing git push

## ✅ Practice Exercise

1. Create a GitHub account (if you don't have one)
2. Create a new repository on GitHub
3. Clone it to your local machine
4. Add a README.md file
5. Commit and push it
6. Make changes locally
7. Push changes to GitHub
8. View your repository on GitHub

## 🎓 Key Takeaways

- GitHub hosts Git repositories in the cloud
- `git remote add` connects local to GitHub
- `git push` uploads your code
- `git pull` downloads changes
- `git clone` copies a repository
- Always use `.gitignore` for unnecessary files

## ➡️ Next Steps

Ready to work with branches? Learn about [Branching & Merging](./../04-branching-merging/README.md)!

---

**Pro Tip:** Keep your GitHub profile updated with your best projects! 🚀

