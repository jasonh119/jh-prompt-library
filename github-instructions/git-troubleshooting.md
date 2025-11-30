# Git Troubleshooting Guide

## Common Issues and Solutions

### Merge Conflicts

#### Problem: Conflicts during merge
```bash
# Identify conflicted files
git status

# View conflict markers in file:
<<<<<<< HEAD
Your changes
=======
Their changes
>>>>>>> branch-name

# Resolution steps:
# 1. Edit files to resolve conflicts
# 2. Remove conflict markers
# 3. Stage resolved files
git add <resolved-file>

# 4. Complete merge
git commit

# If you want to abort
git merge --abort
```

---

### Branch Divergence

#### Problem: Local and remote branches have diverged
```bash
# Situation: "Your branch and 'origin/main' have diverged"

# Option 1: Merge remote changes
git pull --no-rebase

# Option 2: Rebase on top of remote
git pull --rebase

# Option 3: Force push (use with caution)
git push --force-with-lease
```

---

### Authentication Issues

#### Problem: Authentication failed
```bash
# For HTTPS:
# Use Personal Access Token instead of password
# Update remote URL to use token:
git remote set-url origin https://<token>@github.com/user/repo.git

# For SSH:
# Check SSH key setup
ssh -T git@github.com

# Switch from HTTPS to SSH
git remote set-url origin git@github.com:user/repo.git

# macOS Keychain issue fix
git config --global credential.helper osxkeychain
```

---

### Accidental Commits

#### Problem: Committed wrong files
```bash
# Undo last commit, keep changes
git reset --soft HEAD~1

# Undo last commit, unstage changes
git reset HEAD~1

# Undo last commit, discard changes
git reset --hard HEAD~1

# Remove file from last commit
git reset HEAD~1 <file>
git add <correct-files>
git commit -c ORIG_HEAD
```

#### Problem: Committed sensitive information
```bash
# Remove file from history (use with caution)
git filter-branch --force --index-filter \
  "git rm --cached --ignore-unmatch <path-to-file>" \
  --prune-empty --tag-name-filter cat -- --all

# Then force push
git push --force --all
```

---

### Detached HEAD State

#### Problem: In detached HEAD state
```bash
# Check current state
git status

# Option 1: Create branch from current state
git checkout -b <new-branch-name>

# Option 2: Return to a branch
git checkout main
```

---

### Stale References

#### Problem: Remote branch deleted but still shows locally
```bash
# Clean up stale references
git fetch --prune

# Or with pull
git pull --prune

# Remove all stale branches
git remote prune origin
```

---

### Large Files

#### Problem: Repository too large or file too big
```bash
# Remove large file from history
git filter-repo --path <large-file> --invert-paths

# Or use BFG Repo-Cleaner
bfg --delete-files <large-file>

# For future large files, use Git LFS
git lfs install
git lfs track "*.psd"
git add .gitattributes
```

---

### Wrong Branch

#### Problem: Made commits on wrong branch
```bash
# Move commits to new branch
git branch <new-branch-name>
git reset --hard HEAD~<number-of-commits>
git checkout <new-branch-name>

# Move last commit to existing branch
git checkout <target-branch>
git cherry-pick <commit-hash>
git checkout <original-branch>
git reset --hard HEAD~1
```

---

### Corrupted Repository

#### Problem: Repository appears corrupted
```bash
# Verify repository integrity
git fsck

# Recover lost commits
git reflog
git checkout <lost-commit-hash>

# If fsck shows issues
git gc --aggressive --prune=now
```

---

### Line Ending Issues

#### Problem: Line ending conflicts
```bash
# Configure line ending handling
# Windows:
git config --global core.autocrlf true

# macOS/Linux:
git config --global core.autocrlf input

# Normalize line endings in repository
git add --renormalize .
git commit -m "Normalize line endings"
```

---

### Ignored Files Still Tracked

#### Problem: .gitignore not working for tracked files
```bash
# Remove from Git but keep local file
git rm --cached <filename>

# Remove directory
git rm -r --cached <directory>

# Then commit
git add .gitignore
git commit -m "Update .gitignore"
```

---

### Slow Git Operations

#### Problem: Git commands are slow
```bash
# Optimize repository
git gc --aggressive

# Prune unreachable objects
git prune

# Clean up unnecessary files
git clean -fd

# Check repository size
git count-objects -vH
```

---

### Uncommitted Changes Blocking Pull

#### Problem: Can't pull due to local changes
```bash
# Option 1: Stash changes
git stash
git pull
git stash pop

# Option 2: Commit changes
git add .
git commit -m "WIP: temporary commit"
git pull

# Option 3: Discard changes (careful!)
git reset --hard
git pull
```

---

## Prevention Tips

1. **Commit Often:** Small, frequent commits
2. **Pull Regularly:** Stay up to date
3. **Use Branches:** Isolate work
4. **Review Before Commit:** Check `git status` and `git diff`
5. **Use .gitignore:** Properly from the start
6. **Backup:** Push regularly to remote
7. **Test Locally:** Before pushing

---

## Emergency Commands

### Nuclear Options (use with extreme caution)

```bash
# Reset to remote state (loses all local changes)
git fetch origin
git reset --hard origin/main

# Start fresh (keep files)
rm -rf .git
git init
git add .
git commit -m "Initial commit"

# Clean everything
git clean -fdx  # Removes all untracked files and directories
```

---

## Getting Help

```bash
# Git help
git help <command>
git <command> --help

# Check Git version
git --version

# Verbose output for debugging
GIT_TRACE=1 git <command>
```
