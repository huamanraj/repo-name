# Complete Step-by-Step Guide to Your First Open Source Contribution

## Initial Setup (One-Time Steps)

### 1. Setup Git on Your Computer
```bash
# Install Git (if not already installed)
# For Ubuntu/Debian
sudo apt-get install git

# Configure your identity
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### 2. Create GitHub Account and SSH Key
```bash
# Generate SSH key
ssh-keygen -t ed25519 -C "your.email@example.com"

# Start SSH agent
eval "$(ssh-agent -s)"

# Add SSH key to agent
ssh-add ~/.ssh/id_ed25519

# Copy your public key (add to GitHub settings)
cat ~/.ssh/id_ed25519.pub
```

## Making Your Contribution

### 1. Fork and Clone
```bash
# First, fork on GitHub (click Fork button)
# Then clone your fork
git clone https://github.com/your-username/project-name
cd project-name

# Add original repository as upstream
git remote add upstream https://github.com/original-owner/project-name

# Verify remotes
git remote -v
```

### 2. Create Branch and Make Changes
```bash
# Get latest changes from upstream
git fetch upstream
git checkout main
git merge upstream/main

# Create new branch
git checkout -b fix-issue-123

# Check which files you modified
git status

# See your specific changes
git diff

# Stage your changes
git add filename.txt
# Or stage all changes:
git add .

# Commit changes
git commit -m "fix: describe your changes here"
```

### 3. Push Changes and Create PR
```bash
# Push your branch to your fork
git push origin fix-issue-123
```

## Handling Review Feedback

### 1. Making Additional Changes
```bash
# After making requested changes
git add .
git commit -m "fix: address review feedback"
git push origin fix-issue-123
```

### 2. Updating Your PR with Latest Changes
```bash
# Get latest main branch changes
git fetch upstream
git checkout main
git merge upstream/main

# Update your feature branch
git checkout fix-issue-123
git rebase main

# Force push if you rebased
git push origin fix-issue-123 --force-with-lease
```

## Common Scenarios and Solutions

### If You Made a Mistake in Your Last Commit
```bash
# Edit last commit message
git commit --amend -m "New message"

# Add forgotten files to last commit
git add forgotten-file.txt
git commit --amend --no-edit

# Push amended commit
git push origin fix-issue-123 --force-with-lease
```

### If You Need to Undo Changes
```bash
# Undo staged changes
git restore --staged filename.txt

# Discard local changes
git restore filename.txt

# Undo last commit but keep changes
git reset --soft HEAD~1

# Completely undo last commit
git reset --hard HEAD~1
```

## Best Practices for Each Stage

### 1. Before Making Changes
```bash
# Create new branch for each feature/fix
git checkout -b descriptive-branch-name

# Make sure you're up to date
git pull upstream main
```

### 2. While Making Changes
```bash
# Commit often with clear messages
git commit -m "type(scope): description"

# Example commits:
git commit -m "fix(login): resolve authentication timeout"
git commit -m "docs: update installation instructions"
git commit -m "feat(api): add user profile endpoint"
```

### 3. Before Submitting PR
```bash
# Run tests if available
npm test  # or appropriate test command

# Check your changes
git diff main

# Ensure clean commits
git rebase -i main  # to squash commits if needed
```

### 4. After PR Review Requests
```bash
# Apply review suggestions
git add .
git commit -m "fix: address review comments"

# Update PR branch
git fetch upstream
git rebase upstream/main
git push origin fix-issue-123 --force-with-lease
```

## Tips for Success

1. **Check Project Guidelines**
   - Read CONTRIBUTING.md first
   - Follow coding style guidelines
   - Use their commit message format

2. **PR Best Practices**
   - Include issue reference: "Fixes #123"
   - Add detailed description
   - Include screenshots for UI changes
   - Respond promptly to feedback

3. **If Things Go Wrong**
```bash
# Save your changes without committing
git stash

# Start fresh
git checkout main
git pull upstream main
git checkout -b new-branch

# Reapply your changes
git stash pop
```

Would you like me to explain any of these parts in more detail or provide examples for specific scenarios?
