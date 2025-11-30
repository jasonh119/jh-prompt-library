# Git Basics - Essential Commands

## Configuration

### Initial Setup
```bash
# Set your identity
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Check configuration
git config --list
```

---

## Repository Management

### Creating Repositories
```bash
# Initialize new repository
git init

# Clone existing repository
git clone <repository-url>

# Clone with specific branch
git clone -b <branch-name> <repository-url>
```

---

## Basic Workflow

### Status and Information
```bash
# Check repository status
git status

# View commit history
git log
git log --oneline
git log --graph --oneline --all

# Show changes
git diff
git diff --staged
```

### Adding Changes
```bash
# Add specific file
git add <filename>

# Add all changes
git add .
git add -A

# Add by pattern
git add *.js
```

### Committing Changes
```bash
# Commit with message
git commit -m "Your commit message"

# Commit all tracked changes
git commit -am "Your commit message"

# Amend last commit
git commit --amend
```

---

## Syncing with Remote

### Fetching and Pulling
```bash
# Fetch changes from remote
git fetch

# Pull changes (fetch + merge)
git pull

# Pull with rebase
git pull --rebase

# Pull specific branch
git pull origin <branch-name>
```

### Pushing Changes
```bash
# Push to remote
git push

# Push specific branch
git push origin <branch-name>

# Force push (use with caution)
git push --force

# Push and set upstream
git push -u origin <branch-name>
```

---

## Remote Management

### Working with Remotes
```bash
# List remotes
git remote -v

# Add remote
git remote add <name> <url>

# Remove remote
git remote remove <name>

# Rename remote
git remote rename <old-name> <new-name>

# Change remote URL
git remote set-url origin <new-url>
```

---

## Undoing Changes

### Unstaging and Reverting
```bash
# Unstage file
git restore --staged <filename>
git reset HEAD <filename>

# Discard local changes
git restore <filename>
git checkout -- <filename>

# Revert commit (creates new commit)
git revert <commit-hash>

# Reset to previous commit
git reset --soft HEAD~1  # Keep changes staged
git reset --mixed HEAD~1 # Keep changes unstaged
git reset --hard HEAD~1  # Discard changes
```

---

## File Management

### Removing and Moving Files
```bash
# Remove file from Git and filesystem
git rm <filename>

# Remove file from Git only (keep local)
git rm --cached <filename>

# Move/rename file
git mv <old-filename> <new-filename>
```

---

## Stashing Changes

### Temporary Storage
```bash
# Stash current changes
git stash

# Stash with message
git stash save "Work in progress"

# List stashes
git stash list

# Apply most recent stash
git stash apply

# Apply specific stash
git stash apply stash@{n}

# Apply and remove stash
git stash pop

# Drop stash
git stash drop stash@{n}

# Clear all stashes
git stash clear
```

---

## Best Practices

1. **Commit Often:** Make small, focused commits
2. **Write Clear Messages:** Use descriptive commit messages
3. **Pull Before Push:** Always pull latest changes before pushing
4. **Check Status:** Use `git status` frequently
5. **Review Changes:** Use `git diff` before committing
6. **Branch for Features:** Don't work directly on main/master
7. **Use .gitignore:** Keep repository clean

---

## Common Workflows

### Standard Workflow
```bash
# 1. Check status
git status

# 2. Pull latest changes
git pull

# 3. Make changes to files

# 4. Stage changes
git add .

# 5. Commit changes
git commit -m "Descriptive message"

# 6. Push to remote
git push
```

### Quick Fix Workflow
```bash
# Fix issue, then
git add <fixed-file>
git commit -m "Fix: brief description"
git push
```
