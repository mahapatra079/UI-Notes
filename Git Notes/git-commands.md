# Git Commands Reference

## Setup & Configuration
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

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

## Branching
```bash
git branch                  # List branches
git branch <name>           # Create branch
git checkout <branch>       # Switch branch
git checkout -b <branch>    # Create and switch
git merge <branch>          # Merge branch
git branch -d <branch>      # Delete branch
```

## Remote Operations
```bash
git remote add origin <url> # Add remote
git remote -v               # View remotes
git push -u origin main     # Push and set upstream
git fetch                   # Fetch changes
```

## Undo Changes
```bash
git reset HEAD <file>       # Unstage file
git checkout -- <file>      # Discard changes
git revert <commit>         # Revert commit
git reset --hard <commit>   # Reset to commit
```

## Cherry Pick
```bash
git cherry-pick <commit>    # Apply specific commit to current branch
git cherry-pick <hash1> <hash2>  # Pick multiple commits
git cherry-pick --continue  # Continue after resolving conflicts
git cherry-pick --abort     # Cancel cherry-pick
```

## View History
```bash
git log                     # View commit history
git log --oneline           # Compact history
git diff                    # View changes
```

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

## GitHub/GitLab Flow
```bash
# Fork workflow
git clone <your-fork>
git remote add upstream <original-repo>
git fetch upstream
git merge upstream/main
git push origin main
```

# Summary
* Procedure for adding the project files to git  in vs code 
* after creating the repository from git hub :-

* Git init –  it will initialise the empty repository
* Git status – to include the files 
* Git add – to add entire files
* git commit -m "first commit"
* git branch -M main or else directly  below link 
* git remote add origin https://github.com/mahapatra079/my-app.git
* git push -u origin main
* next changes  stash, pull, stash latest apply and then commit & push

**git commit -m "Remove ....** - anything to be reverted from the git hub