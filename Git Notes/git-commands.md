# Git Commands Reference

## Setup & Configuration

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

---

## Basic Commands

```bash
git init                    # Initialize new repository
git clone <url>             # Clone remote repository
git status                  # Check status
git add .                   # Stage all changes
git add <file>              # Stage specific file
git commit -m "message"     # Commit changes
git push                    # Push to remote
git pull                    # Pull from remote
```

---

## Branching

```bash
git branch                  # List branches
git branch <name>           # Create branch
git checkout <branch>       # Switch branch
git checkout -b <branch>    # Create and switch
git merge <branch>          # Merge branch
git branch -d <branch>      # Delete branch
```

---

## Remote Operations

```bash
git remote add origin <url> # Add remote
git remote -v               # View remotes
git push -u origin main     # Push and set upstream
git fetch                   # Fetch changes
```

---

## Undo Changes

```bash
git reset HEAD <file>       # Unstage file
git checkout -- <file>      # Discard changes
git revert <commit>         # Revert commit
git reset --hard <commit>   # Reset to commit
```

---

## Cherry Pick

```bash
git cherry-pick <commit>    # Apply specific commit to current branch
git cherry-pick <hash1> <hash2>  # Pick multiple commits
git cherry-pick --continue  # Continue after resolving conflicts
git cherry-pick --abort     # Cancel cherry-pick
```

---

## View History

```bash
git log                     # View commit history
git log --oneline           # Compact history
git diff                    # View changes
```

---

## Common Workflow

```bash
# Daily workflow
git pull                    # Get latest changes
git checkout -b feature     # Create feature branch
# Make changes
git add .
git commit -m "Add feature"
git push -u origin feature
# Create PR/MR on GitHub/GitLab
```

---

## GitHub/GitLab Flow

```bash
# Fork workflow
git clone <your-fork>
git remote add upstream <original-repo>
git fetch upstream
git merge upstream/main
git push origin main
```

---

## VS Code Git Workflow

### Initial Setup (After creating GitHub repository)

1. **Initialize repository**
   ```bash
   git init
   ```

2. **Check status**
   ```bash
   git status
   ```

3. **Add files**
   ```bash
   git add .
   ```

4. **Commit changes**
   ```bash
   git commit -m "first commit"
   ```

5. **Set main branch**
   ```bash
   git branch -M main
   ```

6. **Add remote origin**
   ```bash
   git remote add origin https://github.com/username/repo-name.git
   ```

7. **Push to remote**
   ```bash
   git push -u origin main
   ```

### Subsequent Changes

```bash
git stash              # Stash current changes
git pull               # Pull latest changes
git stash apply        # Apply stashed changes
git add .
git commit -m "message"
git push
```

---

## Quick Reference

| Command | Description |
|---------|-------------|
| `git init` | Initialize repository |
| `git status` | Check file status |
| `git add .` | Stage all changes |
| `git commit -m "msg"` | Commit with message |
| `git push` | Push to remote |
| `git pull` | Pull from remote |
| `git branch` | List branches |
| `git checkout -b <name>` | Create and switch branch |
| `git merge <branch>` | Merge branch |
| `git stash` | Temporarily save changes |
| `git log` | View commit history |