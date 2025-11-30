# Git Branching Strategies

## Branch Basics

### Creating and Switching Branches
```bash
# Create new branch
git branch <branch-name>

# Switch to branch
git checkout <branch-name>

# Create and switch in one command
git checkout -b <branch-name>

# Switch to branch (newer syntax)
git switch <branch-name>

# Create and switch (newer syntax)
git switch -c <branch-name>
```

### Listing and Managing Branches
```bash
# List local branches
git branch

# List all branches (local and remote)
git branch -a

# List remote branches
git branch -r

# Delete local branch
git branch -d <branch-name>

# Force delete local branch
git branch -D <branch-name>

# Delete remote branch
git push origin --delete <branch-name>

# Rename current branch
git branch -m <new-name>
```

---

## Merging Branches

### Merge Strategies
```bash
# Merge branch into current branch
git merge <branch-name>

# Merge without fast-forward
git merge --no-ff <branch-name>

# Squash commits during merge
git merge --squash <branch-name>

# Abort merge (if conflicts)
git merge --abort
```

### Resolving Conflicts
```bash
# 1. Identify conflicted files
git status

# 2. Edit files to resolve conflicts
# (look for <<<<<<, =======, >>>>>> markers)

# 3. Stage resolved files
git add <resolved-file>

# 4. Complete merge
git commit
```

---

## Rebasing

### Rebase Basics
```bash
# Rebase current branch onto another
git rebase <branch-name>

# Interactive rebase (last n commits)
git rebase -i HEAD~n

# Continue after resolving conflicts
git rebase --continue

# Skip current commit
git rebase --skip

# Abort rebase
git rebase --abort
```

### When to Rebase vs Merge
- **Merge:** Public branches, preserving history
- **Rebase:** Local branches, cleaning up history

---

## Branching Strategies

### Feature Branch Workflow
```bash
# 1. Create feature branch from main
git checkout main
git pull
git checkout -b feature/new-feature

# 2. Work on feature
# ... make changes and commits ...

# 3. Keep feature branch updated
git checkout main
git pull
git checkout feature/new-feature
git rebase main

# 4. Merge feature back
git checkout main
git merge feature/new-feature
git push

# 5. Delete feature branch
git branch -d feature/new-feature
```

### Git Flow
```
main/master     - Production-ready code
develop         - Integration branch
feature/*       - New features
hotfix/*        - Urgent fixes
release/*       - Release preparation
```

### GitHub Flow (Simplified)
```
main            - Always deployable
feature/*       - Work branches
```

---

## Branch Naming Conventions

### Common Patterns
```
feature/feature-name    - New features
bugfix/bug-description  - Bug fixes
hotfix/urgent-fix       - Critical fixes
release/version-number  - Release preparation
chore/task-description  - Maintenance tasks
docs/documentation      - Documentation updates
```

### Examples
```
feature/user-authentication
bugfix/login-error-handling
hotfix/critical-security-patch
release/v1.2.0
chore/update-dependencies
docs/api-documentation
```

---

## Working with Remote Branches

### Tracking Remote Branches
```bash
# Fetch remote branches
git fetch origin

# Create local branch tracking remote
git checkout -b <branch-name> origin/<branch-name>

# Set upstream for existing branch
git branch --set-upstream-to=origin/<branch-name>

# Push new branch to remote
git push -u origin <branch-name>
```

### Cleaning Up
```bash
# Remove stale remote-tracking branches
git fetch --prune

# List merged branches
git branch --merged

# Delete merged branches
git branch -d $(git branch --merged | grep -v "\\*\\|main\\|develop")
```

---

## Best Practices

1. **Branch Often:** Create branches for features, bugs, experiments
2. **Keep Branches Short-lived:** Merge or delete quickly
3. **Use Descriptive Names:** Clear branch purpose
4. **Update Regularly:** Keep branches in sync with main
5. **Clean Up:** Delete merged branches
6. **Protect Main:** Use branch protection rules
7. **Review Before Merge:** Use pull requests

---

## Common Workflows

### Create Feature Branch
```bash
git checkout main
git pull origin main
git checkout -b feature/my-feature
# ... work on feature ...
git add .
git commit -m "Add new feature"
git push -u origin feature/my-feature
```

### Update Feature Branch with Main
```bash
git checkout main
git pull origin main
git checkout feature/my-feature
git rebase main
git push --force-with-lease
```

### Complete and Merge Feature
```bash
# After pull request approval
git checkout main
git pull origin main
git merge feature/my-feature
git push origin main
git branch -d feature/my-feature
git push origin --delete feature/my-feature
```
