# Git and Git Flow Cheat Sheet [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)



<p align="center">
    <strong>Your comprehensive guide to mastering Git and Git Flow workflows</strong>
</p>

---

## 📖 About

This comprehensive Git cheat sheet is designed to help developers at all levels master Git commands without memorizing everything. Whether you're just starting with version control or you're an experienced developer looking for a quick reference, this guide covers essential Git operations, best practices, and Git Flow workflows.

### ✨ What You'll Find Here:
- 🔧 Initial setup and configuration
- 📝 Daily workflow commands
- 🌿 Branch management strategies
- 🔄 Collaboration workflows
- ↩️ Undo and recovery operations
- 🌊 Git Flow methodology

### 🤝 Contributions Welcome!

Help make this guide even better! Feel free to:
- ✏️ Fix grammar mistakes or typos
- ➕ Add new commands or use cases
- 🌍 Translate to your language
- 💡 Improve explanations and examples
- 📚 Add best practices and tips

---
## 📋 Table of Contents

### Core Git Commands
- [🔧 Setup](#-setup) - Initial Git configuration
- [⚙️ Configuration Files](#️-configuration-files) - Understanding config scopes
- [🆕 Create Repository](#-create-repository) - Initialize or clone repositories
- [📝 Local Changes](#-local-changes) - Stage, commit, and stash changes
- [🔍 Search](#-search) - Find text and commits in your repository
- [📖 Commit History](#-commit-history) - View and analyze project history
- [📁 Move / Rename](#-move--rename) - Manage file names
- [🌿 Branches & Tags](#-branches--tags) - Branch management and tagging

### Collaboration & Advanced Topics
- [🔄 Update & Publish](#-update--publish) - Sync with remote repositories
- [🔀 Merge & Rebase](#-merge--rebase) - Integrate changes from different branches
- [↩️ Undo](#️-undo) - Recover from mistakes

### Git Flow Workflow
- [🌊 Git Flow](#-git-flow) - Structured branching model for releases

### Additional Resources
- [💡 Best Practices](#-best-practices) - Tips for effective Git usage
- [🤝 Contributing](#-contributing) - How to contribute to this guide
- [📄 License](#-license) - Project license information

---

## 🔧 Setup

### View Configuration

**Show current configuration:**
```bash
git config --list
```

**Show repository configuration:**
```bash
git config --local --list
```

**Show global configuration:**
```bash
git config --global --list
```

**Show system configuration:**
```bash
git config --system --list
```

### User Configuration

**Set your name for version history:**
```bash
git config --global user.name "[firstname lastname]"
```

**Set your email address:**
```bash
git config --global user.email "[valid-email]"
```

### Display & Editor Settings

**Enable automatic command line coloring:**
```bash
git config --global color.ui auto
```

**Set global editor for commits:**
```bash
git config --global core.editor vi
```

**Set default editor to VS Code:**
```bash
git config --global core.editor "code --wait"
```

**Set default editor to Notepad++:**
```bash
git config --global core.editor "'C:/Program Files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"
```

### Additional Useful Configurations

**Enable auto-correct for mistyped commands:**
```bash
git config --global help.autocorrect 1
```

**Set default branch name to 'main':**
```bash
git config --global init.defaultBranch main
```

**Configure line ending handling (Windows):**
```bash
git config --global core.autocrlf true
```

**Configure line ending handling (Mac/Linux):**
```bash
git config --global core.autocrlf input
```

**Create useful aliases:**
```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual '!gitk'
```

---

## ⚙️ Configuration Files

| Scope | Location | Command Flag |
|-------|----------|--------------|
| **Repository** | `<repo>/.git/config` | `--local` |
| **User** | `~/.gitconfig` | `--global` |
| **System** | `/etc/gitconfig` | `--system` |

---

## 🆕 Create Repository

### Clone Existing Repository

**Via SSH:**
```bash
git clone ssh://user@domain.com/repo.git
```

**Via HTTPS:**
```bash
git clone https://domain.com/user/repo.git
```

### Initialize New Repository

**Create repository in current directory:**
```bash
git init
```

**Create repository in specific directory:**
```bash
git init <directory>
```

---

## 📝 Local Changes

### Check Status & Differences

**View working directory status:**
```bash
git status
```

**Show changes to tracked files:**
```bash
git diff
```

**Show changes in specific file:**
```bash
git diff <file>
```

### Staging Changes

**Add all current changes:**
```bash
git add .
```

**Add all changes (including deleted files):**
```bash
git add -A
```

**Add specific files:**
```bash
git add <filename1> <filename2>
```

**Add files by pattern:**
```bash
git add *.js
```

**Interactively add parts of a file:**
```bash
git add -p <file>
```

**Stage modified and deleted files (not new files):**
```bash
git add -u
```

### Committing Changes

**Commit all tracked file changes:**
```bash
git commit -a
```

**Commit staged changes:**
```bash
git commit
```

**Commit with message:**
```bash
git commit -m 'message here'
```

**Skip staging and commit with message:**
```bash
git commit -am 'message here'
```

**Commit with specific date:**
```bash
git commit --date="`date --date='n day ago'`" -am "<Commit Message Here>"
```

### Modify Last Commit

> ⚠️ **Warning:** Don't amend published commits!

**Amend last commit:**
```bash
git commit -a --amend
```

**Amend without changing commit message:**
```bash
git commit --amend --no-edit
```

**Change committer date:**
```bash
GIT_COMMITTER_DATE="date" git commit --amend
```

**Change author date:**
```bash
git commit --amend --date="date"
```

### Stashing Changes

**Save current changes temporarily:**
```bash
git stash
```

**Stash with descriptive message:**
```bash
git stash save "message describing changes"
```

**Stash including untracked files:**
```bash
git stash -u
```

**Stash all files (including ignored files):**
```bash
git stash -a
```

**List all stashes:**
```bash
git stash list
```

**Apply last stashed changes:**
```bash
git stash apply
```

**Apply and remove last stash:**
```bash
git stash pop
```

**Apply specific stash:**
```bash
git stash apply stash@{stash_number}
```

**Show stash contents:**
```bash
git stash show -p stash@{0}
```

**Remove specific stash:**
```bash
git stash drop stash@{stash_number}
```

**Remove all stashes:**
```bash
git stash clear
```

**Create branch from stash:**
```bash
git stash branch <branch_name> stash@{0}
```

**Move uncommitted changes to another branch:**
```bash
git stash
git checkout branch2
git stash pop
```

---

## 🔍 Search

### Text Search

**Search for text in all files:**
```bash
git grep "Hello"
```

**Search in specific version:**
```bash
git grep "Hello" v2.5
```

### Commit Search

**Find commits that introduced specific keyword:**
```bash
git log -S 'keyword'
```

**Search with regular expression:**
```bash
git log -S 'keyword' --pickaxe-regex
```

---

## 📖 Commit History

### Basic History

**Show all commits (detailed):**
```bash
git log
```

**Show commits (one line each):**
```bash
git log --oneline
```

**Show commits by specific author:**
```bash
git log --author="username"
```

**Show changes for specific file:**
```bash
git log -p <file>
```

### Advanced History

**Show commits with diff:**
```bash
git log -p
```

**Show commits with stats:**
```bash
git log --stat
```

**Show commit graph:**
```bash
git log --graph --oneline --all
```

**Show commits in date range:**
```bash
git log --since="2 weeks ago" --until="1 day ago"
```

**Show commits that affected specific lines:**
```bash
git log -L <start>,<end>:<file>
```

**Pretty format log:**
```bash
git log --pretty=format:"%h - %an, %ar : %s"
```

**Compare branches:**
```bash
git log --oneline <origin/master>..<remote/master> --left-right
```

**Show who changed what and when:**
```bash
git blame <file>
```

**Show file changes in commit:**
```bash
git show <commit>:<file>
```

### Reference Logs

**Show reference log:**
```bash
git reflog show
```

**Show reflog for specific branch:**
```bash
git reflog show <branch>
```

**Delete reference log:**
```bash
git reflog delete
```

---

## 📁 Move / Rename

**Rename a file:**
```bash
git mv Index.txt Index.html
```

---

## 🌿 Branches & Tags

### List Branches

**List local branches:**
```bash
git branch
```

**List all branches (local + remote):**
```bash
git branch -a
```

**List remote branches:**
```bash
git branch -r
```

**List merged branches:**
```bash
git branch --merged
```

### Switch & Create Branches

**Switch to existing branch:**
```bash
git checkout <branch>
```

**Create and switch to new branch:**
```bash
git checkout -b <branch>
```

**Switch to previous branch:**
```bash
git checkout -
```

**Create branch from existing branch:**
```bash
git checkout -b <new_branch> <existing_branch>
```

**Create branch from specific commit:**
```bash
git checkout <commit-hash> -b <new_branch_name>
```

**Create branch without switching:**
```bash
git branch <new-branch>
```

**Create tracking branch:**
```bash
git branch --track <new-branch> <remote-branch>
```

### Branch Operations

**Checkout single file from different branch:**
```bash
git checkout <branch> -- <filename>
```

**Apply specific commit from another branch:**
```bash
git cherry-pick <commit hash>
```

**Rename current branch:**
```bash
git branch -m <new_branch_name>
```

**Delete local branch:**
```bash
git branch -d <branch>
```

**Force delete local branch:**
```bash
git branch -D <branch>
```
> ⚠️ **Warning:** You will lose unmerged changes!

**Delete remote branch:**
```bash
git push <remote> --delete <branch>
```

**Prune deleted remote branches:**
```bash
git fetch -p
```

**List branches with last commit:**
```bash
git branch -v
```

**List branches and their tracking info:**
```bash
git branch -vv
```

### Tags

**Create tag at HEAD:**
```bash
git tag <tag-name>
```

**Create annotated tag:**
```bash
git tag -a <tag-name>
```

**Create tag with message:**
```bash
git tag <tag-name> -am 'message here'
```

**List all tags:**
```bash
git tag
```

**List tags with messages:**
```bash
git tag -n
```

---

## 🔄 Update & Publish

### Remote Management

**List configured remotes:**
```bash
git remote -v
```

**Show remote information:**
```bash
git remote show <remote>
```

**Add new remote:**
```bash
git remote add <remote> <url>
```

**Rename remote:**
```bash
git remote rename <remote> <new_remote>
```

**Remove remote:**
```bash
git remote rm <remote>
```
> ℹ️ **Note:** This only removes the remote reference locally, not the remote repository itself.

### Fetch & Pull

**Download changes without merging:**
```bash
git fetch <remote>
```

**Download and merge changes:**
```bash
git pull <remote> <branch>
```

**Get changes from main branch:**
```bash
git pull origin master
```

**Pull with rebase:**
```bash
git pull --rebase <remote> <branch>
```

### Push & Publish

**Publish local changes:**
```bash
git push <remote> <branch>
```

**Delete remote branch:**
```bash
# Git v1.7.0+
git push <remote> --delete <branch>

# Git v1.5.0+
git push <remote> :<branch>
```

**Publish tags:**
```bash
git push --tags
```

---

## 🔀 Merge & Rebase

### Merge Operations

**Merge branch into current HEAD:**
```bash
git merge <branch>
```

**Configure merge tool globally:**
```bash
git config --global merge.tool meld
```

**Use configured merge tool:**
```bash
git mergetool
```

### Rebase Operations

> ⚠️ **Warning:** Don't rebase published commits!

**Rebase current HEAD onto branch:**
```bash
git rebase <branch>
```

**Abort rebase:**
```bash
git rebase --abort
```

**Continue rebase after resolving conflicts:**
```bash
git rebase --continue
```

### Conflict Resolution

**Mark file as resolved:**
```bash
git add <resolved-file>
```

**Remove resolved file:**
```bash
git rm <resolved-file>
```

### Squashing Commits

**Interactive rebase for squashing:**
```bash
git rebase -i <commit-just-before-first>
```

**Example squash configuration:**
```
# Before
pick <commit_id>
pick <commit_id2>
pick <commit_id3>

# After (squash commit_id2 and commit_id3 into commit_id)
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```

---

## ↩️ Undo

### Discard Changes

**Discard all local changes:**
```bash
git reset --hard HEAD
```

**Unstage all files:**
```bash
git reset HEAD
```

**Discard changes in specific file:**
```bash
git checkout HEAD <file>
```

### Reset Operations

**Reset to previous commit (discard all changes):**
```bash
git reset --hard <commit>
```

**Reset to remote branch state:**
```bash
git reset --hard <remote/branch>
# Example: git reset --hard upstream/master
```

**Reset preserving changes as unstaged:**
```bash
git reset <commit>
```

**Reset preserving uncommitted local changes:**
```bash
git reset --keep <commit>
```

### Revert Commits

**Revert commit (create new commit with opposite changes):**
```bash
git revert <commit>
```

### Clean Ignored Files

**Remove accidentally committed files that should be ignored:**
```bash
git rm -r --cached .
git add .
git commit -m "remove ignored files"
```

**Remove untracked files (dry run):**
```bash
git clean -n
```

**Remove untracked files:**
```bash
git clean -f
```

**Remove untracked files and directories:**
```bash
git clean -fd
```

**Remove untracked and ignored files:**
```bash
git clean -fdx
```

---

## 💡 Best Practices

### Commit Messages

**Write clear commit messages:**
- Use present tense ("Add feature" not "Added feature")
- Keep first line under 50 characters
- Add detailed description after blank line if needed
- Reference issue numbers when applicable

**Example:**
```
Add user authentication feature

- Implement JWT token validation
- Add login/logout endpoints
- Include password hashing with bcrypt

Fixes #123
```

### Branching Strategy

**Follow a consistent naming convention:**
- `feature/feature-name` - New features
- `bugfix/bug-description` - Bug fixes
- `hotfix/critical-fix` - Critical production fixes
- `release/version-number` - Release preparation

### Daily Workflow

**Recommended workflow:**
```bash
# Start your day
git checkout main
git pull origin main

# Create feature branch
git checkout -b feature/new-feature

# Make changes and commit frequently
git add .
git commit -m "Descriptive message"

# Before pushing, sync with main
git checkout main
git pull origin main
git checkout feature/new-feature
git rebase main

# Push your changes
git push origin feature/new-feature
```

### Safety Tips

**Before force operations:**
- ✅ Always create a backup branch
- ✅ Communicate with team before force pushing
- ✅ Never force push to main/master
- ✅ Use `--force-with-lease` instead of `--force`

**Useful safety commands:**
```bash
# Create backup before risky operation
git branch backup-branch

# Force push safely
git push --force-with-lease origin feature-branch

# Check what would be pushed
git push --dry-run origin branch
```

### Performance Tips

**For large repositories:**
```bash
# Shallow clone (faster)
git clone --depth 1 <repo-url>

# Sparse checkout (partial clone)
git sparse-checkout init
git sparse-checkout set <directory>

# Clean up repository
git gc --aggressive
```

---

## 🌊 Git Flow

**Improved Git-flow:** [git-flow-avh](https://github.com/petervanderdoes/gitflow-avh)

### 📋 Table of Contents
- [🔧 Setup](#setup-1)
- [🚀 Getting Started](#getting-started)
- [✨ Features](#features)
- [🎁 Make a Release](#make-a-release)
- [🔥 Hotfixes](#hotfixes)
- [📊 Commands Overview](#commands-overview)

---

### 🔧 Setup {#setup-1}

> **Prerequisite:** Working Git installation required. Git-flow works on macOS, Linux, and Windows.

**macOS (Homebrew):**
```bash
brew install git-flow-avh
```

**macOS (MacPorts):**
```bash
port install git-flow
```

**Linux (Debian-based):**
```bash
sudo apt-get install git-flow
```

**Windows (Cygwin):**
> Requires wget and util-linux
```bash
wget -q -O - --no-check-certificate https://raw.githubusercontent.com/petervanderdoes/gitflow/develop/contrib/gitflow-installer.sh install <state> | bash
```

---

### 🚀 Getting Started

Git-flow needs initialization to customize your project setup.

**Initialize (interactive):**
```bash
git flow init
```
> You'll answer questions about branch naming conventions. Default values are recommended.

**Initialize (use defaults):**
```bash
git flow init -d
```

---

### ✨ Features

Features are for developing new functionality for upcoming releases. They typically exist only in developer repositories.

**Start new feature:**
```bash
git flow feature start MYFEATURE
```
> Creates feature branch based on 'develop' and switches to it

**Finish feature:**
```bash
git flow feature finish MYFEATURE
```
> This will:
> 1. Merge MYFEATURE into 'develop'
> 2. Remove the feature branch
> 3. Switch back to 'develop'

**Publish feature (for collaboration):**
```bash
git flow feature publish MYFEATURE
```

**Get published feature:**
```bash
git flow feature pull origin MYFEATURE
```

**Track origin feature:**
```bash
git flow feature track MYFEATURE
```

---

### 🎁 Make a Release

Releases support preparation of new production releases, allowing minor bug fixes and preparing meta-data.

**Start release:**
```bash
git flow release start RELEASE [BASE]
```
> Creates release branch from 'develop'. Optionally specify [BASE] commit SHA-1.

**Publish release:**
```bash
git flow release publish RELEASE
```

**Track remote release:**
```bash
git flow release track RELEASE
```

**Finish release:**
```bash
git flow release finish RELEASE
```
> This will:
> 1. Merge release branch into 'master'
> 2. Tag the release
> 3. Back-merge release into 'develop'
> 4. Remove release branch

> 💡 **Don't forget:** Push your tags with `git push --tags`

---

### 🔥 Hotfixes

Hotfixes address critical issues in live production versions. They branch off from the corresponding tag on master.

**Start hotfix:**
```bash
git flow hotfix start VERSION [BASENAME]
```

**Finish hotfix:**
```bash
git flow hotfix finish VERSION
```
> Merges back into both 'develop' and 'master', and tags the master merge

---

### 📊 Commands Overview

| Command | Description |
|---------|-------------|
| `git flow init` | Initialize git-flow in repository |
| `git flow feature start <name>` | Start new feature |
| `git flow feature finish <name>` | Finish feature |
| `git flow feature publish <name>` | Publish feature to remote |
| `git flow release start <version>` | Start new release |
| `git flow release finish <version>` | Finish release |
| `git flow hotfix start <version>` | Start new hotfix |
| `git flow hotfix finish <version>` | Finish hotfix |

---

## 🆘 Common Issues & Solutions

### Problem: Merge Conflicts

**Solution:**
```bash
# Check conflicted files
git status

# Open and resolve conflicts manually, then:
git add <resolved-file>
git commit

# Or abort the merge
git merge --abort
```

### Problem: Accidentally Committed to Wrong Branch

**Solution:**
```bash
# Reset last commit but keep changes
git reset HEAD~1

# Switch to correct branch
git checkout correct-branch

# Commit changes
git add .
git commit -m "Your message"
```

### Problem: Need to Undo Last Commit

**Solution:**
```bash
# Undo commit, keep changes staged
git reset --soft HEAD~1

# Undo commit, keep changes unstaged
git reset HEAD~1

# Undo commit, discard changes
git reset --hard HEAD~1
```

### Problem: Pushed Sensitive Data

**Solution:**
```bash
# Remove file from history (use with caution!)
git filter-branch --force --index-filter \
  "git rm --cached --ignore-unmatch <path/to/file>" \
  --prune-empty --tag-name-filter cat -- --all

# Force push (coordinate with team!)
git push origin --force --all
```
> ⚠️ **Important:** Change any exposed credentials immediately!

### Problem: Detached HEAD State

**Solution:**
```bash
# Create branch from current state
git checkout -b new-branch

# Or return to previous branch
git checkout -
```

---

## 📚 Additional Resources

### Official Documentation
- [Git Official Documentation](https://git-scm.com/doc)
- [Pro Git Book (Free)](https://git-scm.com/book/en/v2)
- [Git Flow Documentation](https://nvie.com/posts/a-successful-git-branching-model/)

### Interactive Learning
- [Learn Git Branching](https://learngitbranching.js.org/)
- [Git Immersion](http://gitimmersion.com/)
- [GitHub Learning Lab](https://lab.github.com/)

### Quick References
- [Git Cheat Sheet (GitHub)](https://education.github.com/git-cheat-sheet-education.pdf)
- [Visual Git Cheat Sheet](https://ndpsoftware.com/git-cheatsheet.html)

---

## 🤝 Contributing

We welcome contributions! You can:

- 🐛 Report bugs or typos
- ✨ Add new Git commands
- 🌍 Translate to new languages
- 💡 Improve explanations
- 📝 Enhance formatting

**How to contribute:**
1. Fork this repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

## 🌟 Show Your Support

If you found this guide helpful, please consider:

- ⭐ **Starring this repository**
- 🔗 **Sharing with your colleagues**
- 🐛 **Reporting issues or suggesting improvements**
- 🤝 **Contributing new content**

---

## 📧 Contact & Feedback

Have suggestions or found an error? We'd love to hear from you!

- Open an [issue](../../issues)
- Submit a [pull request](../../pulls)
- Share your feedback

---

<p align="center">
    <b>Made with ❤️ by developers, for developers</b>
</p>

<p align="center">
    <sub>Last updated: January 2026</sub>
</p>
