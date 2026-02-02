# 📘 Git Basics

## What is Git?

Git is a **distributed version control system** that tracks changes in your files. Think of it as a time machine for your code that allows you to:
- Save snapshots of your project
- Go back to any previous version
- Work on different features simultaneously
- Collaborate with others without conflicts

## 🖼️ Visual Concept

```
Timeline of Your Project:
┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐
│ Commit 1│ -> │ Commit 2│ -> │ Commit 3│ -> │ Commit 4│
│ v0.1    │    │ v0.2    │    │ v0.3    │    │ v1.0    │
└─────────┘    └─────────┘    └─────────┘    └─────────┘
```

*See `../images/diagrams/git-timeline.png` for visual representation*

## 🚀 Installation

### Windows
1. Download Git from [git-scm.com](https://git-scm.com/download/win)
2. Run the installer
3. Use default settings (recommended)
4. Verify: Open Git Bash and type `git --version`

### macOS
```bash
# Option 1: Download from git-scm.com
# Option 2: Use Homebrew
brew install git
```

### Linux
```bash
# Ubuntu/Debian
sudo apt-get update
sudo apt-get install git

# Fedora
sudo dnf install git
```

## ⚙️ Initial Configuration

After installation, configure Git with your identity:

```bash
# Set your name
git config --global user.name "John Doe"

# Set your email
git config --global user.email "john.doe@example.com"

# Verify configuration
git config --list
```

## 📂 Understanding Git Repository

A Git repository is a folder where Git tracks changes. It contains:
- **Working Directory**: Your actual project files
- **Staging Area**: Files ready to be committed
- **Repository**: Committed snapshots (history)

```
┌─────────────────────────────────────┐
│      Working Directory              │
│  (Your files: code, docs, etc.)     │
│           ↓                         │
│      Staging Area                   │
│  (Files ready to commit)            │
│           ↓                         │
│      Repository                     │
│  (Committed snapshots)              │
└─────────────────────────────────────┘
```

*See `../images/diagrams/git-structure.png` for visual representation*

## 🔧 Essential Git Commands

### 1. Initialize a Repository

```bash
# Create a new Git repository in current folder
git init

# Initialize in a specific folder
git init my-project
```

**What it does:** Creates a hidden `.git` folder that tracks all changes.

### 2. Check Status

```bash
git status
```

**Output example:**
```
On branch main
Changes not staged for commit:
  modified:   README.md
Untracked files:
  new-file.txt
```

### 3. Add Files to Staging

```bash
# Add a specific file
git add filename.txt

# Add all files in current directory
git add .

# Add all files of a specific type
git add *.js

# Add a directory
git add folder/
```

### 4. Commit Changes

```bash
# Commit with a message
git commit -m "Add new feature"

# Commit with detailed message
git commit -m "Add user authentication
- Implemented login functionality
- Added password validation
- Created user session management"
```

**Best Practice:** Write clear, descriptive commit messages!

### 5. View Commit History

```bash
# View commit history
git log

# One-line format
git log --oneline

# With graph
git log --oneline --graph

# Last 5 commits
git log -5
```

### 6. View Changes

```bash
# See what changed (unstaged)
git diff

# See staged changes
git diff --staged

# See changes in a specific file
git diff filename.txt
```

## 🎯 Your First Git Repository

Let's create your first repository step by step:

```bash
# 1. Create a new folder
mkdir my-first-project
cd my-first-project

# 2. Initialize Git
git init

# 3. Create a file
echo "# My First Project" > README.md

# 4. Check status
git status

# 5. Add the file
git add README.md

# 6. Commit
git commit -m "Initial commit: Add README"

# 7. View history
git log
```

## 📊 Command Cheat Sheet

| Command | Description |
|---------|-------------|
| `git init` | Initialize a new repository |
| `git status` | Check repository status |
| `git add <file>` | Stage a file for commit |
| `git commit -m "message"` | Commit staged changes |
| `git log` | View commit history |
| `git diff` | View changes |
| `git config --global user.name` | Set your name |
| `git config --global user.email` | Set your email |

## 🖼️ Screenshots

Add screenshots to `../images/screenshots/01-git-basics/`:
- `git-status-output.png` - Example of `git status` output
- `git-log-output.png` - Example of `git log` output
- `git-init-terminal.png` - Terminal showing `git init`

## ✅ Practice Exercise

1. Create a new folder called `practice-project`
2. Initialize a Git repository
3. Create a file called `hello.txt` with "Hello, Git!"
4. Add and commit the file
5. Modify the file and see the changes with `git diff`
6. Add and commit the changes

## 🎓 Key Takeaways

- Git tracks changes in your files
- `git init` creates a new repository
- `git add` stages files for commit
- `git commit` saves a snapshot
- `git status` shows current state
- `git log` shows history

## ➡️ Next Steps

Ready to learn more? Move on to [Git Workflow](./../02-git-workflow/README.md)!


