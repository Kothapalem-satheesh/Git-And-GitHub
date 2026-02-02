# 📦 Sample Project

This is a sample project to practice Git and GitHub commands. Use this project to follow along with the tutorials.

## 🎯 Purpose

This project serves as a hands-on learning tool where you can:
- Practice Git commands
- Experiment with branches
- Learn GitHub workflows
- Make mistakes safely
- Build confidence

## 🚀 Getting Started

### 1. Clone or Initialize

```bash
# If this is on GitHub, clone it:
git clone https://github.com/your-username/sample-project.git
cd sample-project

# Or create locally:
mkdir sample-project
cd sample-project
git init
```

### 2. Create Initial Files

```bash
# Create a simple HTML file
cat > index.html << 'EOF'
<!DOCTYPE html>
<html>
<head>
    <title>Sample Project</title>
</head>
<body>
    <h1>Welcome to Git Learning!</h1>
    <p>This is a sample project for practicing Git.</p>
</body>
</html>
EOF

# Create a simple CSS file
cat > style.css << 'EOF'
body {
    font-family: Arial, sans-serif;
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
}

h1 {
    color: #333;
}
EOF

# Create a JavaScript file
cat > app.js << 'EOF'
console.log('Hello from Git learning project!');

function greet(name) {
    return `Hello, ${name}! Welcome to Git.`;
}

console.log(greet('Learner'));
EOF
```

### 3. Create .gitignore

```bash
cat > .gitignore << 'EOF'
# OS files
.DS_Store
Thumbs.db

# Editor files
.vscode/
.idea/
*.swp

# Logs
*.log
EOF
```

### 4. Initial Commit

```bash
# Add all files
git add .

# Commit
git commit -m "Initial commit: Add basic HTML, CSS, and JS files"

# View status
git status

# View history
git log --oneline
```

## 🎓 Practice Exercises

### Exercise 1: Basic Commits

1. Modify `index.html` - add a new section
2. Check status: `git status`
3. See changes: `git diff`
4. Stage and commit: `git add index.html && git commit -m "Add new section"`

### Exercise 2: Working with Branches

```bash
# Create a feature branch
git checkout -b feature/add-styling

# Modify style.css
# Add new styles

# Commit changes
git add style.css
git commit -m "Add new styling features"

# Switch back to main
git checkout main

# Merge feature branch
git merge feature/add-styling

# Delete branch
git branch -d feature/add-styling
```

### Exercise 3: Handling Conflicts

```bash
# On main branch
git checkout main
# Modify a line in index.html
git add index.html
git commit -m "Update main branch"

# On feature branch
git checkout -b feature/conflict-test
# Modify the same line differently
git add index.html
git commit -m "Update feature branch"

# Try to merge (will create conflict)
git checkout main
git merge feature/conflict-test

# Resolve conflict, then:
git add index.html
git commit -m "Resolve merge conflict"
```

### Exercise 4: Stashing

```bash
# Make some changes
# (Edit files but don't commit)

# Stash changes
git stash

# Switch branches
git checkout -b feature/new-feature

# Make commits here

# Switch back
git checkout main

# Apply stash
git stash pop
```

### Exercise 5: GitHub Workflow

```bash
# Create repository on GitHub first

# Add remote
git remote add origin https://github.com/your-username/sample-project.git

# Push to GitHub
git push -u origin main

# Create feature branch
git checkout -b feature/github-practice

# Make changes and commit
git add .
git commit -m "Practice GitHub workflow"

# Push branch
git push -u origin feature/github-practice

# Create Pull Request on GitHub
# Merge via GitHub interface
# Pull updates locally
git checkout main
git pull
```

## 📝 Project Structure

```
sample-project/
├── README.md
├── index.html
├── style.css
├── app.js
└── .gitignore
```

## 🎯 Learning Goals

By working through this project, you'll practice:

- ✅ Initializing repositories
- ✅ Making commits
- ✅ Creating branches
- ✅ Merging branches
- ✅ Resolving conflicts
- ✅ Working with remotes
- ✅ Pushing to GitHub
- ✅ Creating pull requests

## 💡 Tips

- **Make mistakes!** This is a learning project
- **Experiment freely** - you can always reset
- **Try every command** from the tutorials
- **Break things** to learn how to fix them
- **Use `git reflog`** if you lose commits

## 🔄 Reset Practice

If you want to start over:

```bash
# Remove all commits but keep files
git checkout --orphan new-main
git add .
git commit -m "Fresh start"

# Or delete .git and start fresh
rm -rf .git
git init
```

## 📚 Next Steps

1. Complete all exercises above
2. Try advanced Git commands
3. Experiment with GitHub features
4. Create your own practice scenarios
5. Apply what you learned to real projects

---

**Happy Learning!** Use this project to build confidence with Git and GitHub! 🚀

