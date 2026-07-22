# Git & GitHub Overview

A concise, industry-standard reference for Git — the version control system every developer relies on. Covers core concepts, essential and advanced commands, useful flags, real-world workflows, and best practices, from beginner to advanced.

## Table of Contents

- [Introduction](#introduction)
- [Why Use Git?](#why-use-git)
- [Essential Commands](#essential-commands)
- [Advanced Commands](#advanced-commands)
- [Understanding Flags](#understanding-flags)
- [Useful Git Flags](#useful-git-flags)
- [Real-World Use Cases](#real-world-use-cases)
- [Best Practices](#best-practices)
- [Branch Naming Conventions](#branch-naming-conventions)

---

## Introduction

Git is the industry-standard distributed version control system used to track changes in code and collaborate efficiently with others. It maintains a complete history of a project, making it easy to review past work, undo mistakes, and coordinate changes across teams — whether working solo, on a team, or contributing to open source.

This guide covers core Git commands with their flags, when and why to use them, and practical workflows for maintaining a clean commit history, resolving merge conflicts, and recovering from mistakes using `reset` and `revert`.

## Why Use Git?

Git brings several advantages to individual developers and teams alike:

| Feature | Benefit |
|---|---|
| **Version Control** | Track every change made to a project over time |
| **Staging Area** | Review and prepare changes before committing |
| **Undoing Mistakes** | Multiple ways to revert or reset unwanted changes |
| **Collaboration** | Multiple developers can work on the same codebase simultaneously |
| **Branching & Merging** | Isolate work in progress without affecting the main codebase |
| **Distributed System** | Every clone is a full backup of the project history |
| **Tracking Changes** | Full audit trail of who changed what, and when |
| **Integration** | Works with CI/CD, IDEs, and countless developer tools |
| **Community & Support** | Massive ecosystem, documentation, and tooling |
| **Industry Standard** | The default expectation in virtually every dev role |

## Essential Commands

### Initialize a repository
```bash
git init
```
Creates a new Git repository in the current directory, setting up the files needed to start tracking changes.

### Clone a repository
```bash
git clone [repository URL]
```
Creates a local copy of an existing repository, including its full history.

### Add files to staging
```bash
git add [file/directory]
```
Stages a file or directory, preparing it for the next commit.

### Commit with a message
```bash
git commit -m "[commit message]"
```
Records staged changes to the local repository with a descriptive message.

### Push changes
```bash
git push
```
Uploads local commits to the remote repository.

### Pull changes
```bash
git pull
```
Fetches changes from the remote repository and merges them into the current branch.

### Fetch changes
```bash
git fetch
```
Downloads changes from the remote without merging them into the local branch.

### Check status
```bash
git status
```
Shows staged, unstaged, and untracked changes in the working directory.

### Check differences
```bash
git diff [file]
```
Shows line-by-line differences between the working directory and the staging area or repository.

### List branches
```bash
git branch
```
Lists all local branches, marking the current branch with an asterisk.

### Switch a branch
```bash
git checkout [branch name]
```
Switches the working directory to the specified branch.

### Merge a branch
```bash
git merge [branch name]
```
Merges the specified branch into the current branch.

### View commit history
```bash
git log
```
Displays the commit history, including author, date, and message for each commit.

### List remote repositories
```bash
git remote -v
```
Shows all remotes connected to the local repository along with their URLs.

### Reset a file
```bash
git reset [file]
```
Removes a file from the staging area without deleting its changes.

### Revert a commit
```bash
git revert [commit]
```
Creates a new commit that undoes the changes from a specified commit, preserving history.

## Advanced Commands

### Stash
```bash
git stash
```
Temporarily saves uncommitted changes so you can switch branches or context without losing work.

### Cherry-pick
```bash
git cherry-pick [commit]
```
Applies a specific commit from one branch onto another, without merging the entire branch.

### Bisect
```bash
git bisect
```
Performs a binary search through commit history to identify which commit introduced a bug.

### Blame
```bash
git blame
```
Shows who last modified each line of a file and when — useful for tracing the origin of a change.

### Reflog
```bash
git reflog
```
Displays a log of all reference changes, useful for recovering lost or "deleted" commits.

### Worktree
```bash
git worktree
```
Allows checking out multiple branches into separate working directories simultaneously.

### Filter-branch
```bash
git filter-branch
```
Rewrites Git history by applying filters — commonly used to remove sensitive data from a repository.

### Merge squash
```bash
git merge --squash
```
Combines all changes from a branch into a single commit when merging, keeping history clean.

### Submodule
```bash
git submodule
```
Includes one Git repository inside another, useful for reusing external code.

### Submodule foreach
```bash
git submodule foreach
```
Runs a Git command across every submodule at once.

### Interactive rebase
```bash
git rebase -i
```
Interactively reorder, edit, squash, or remove commits to clean up history before pushing.

### Rebase
```bash
git rebase
```
Reapplies commits from one branch on top of another, producing a linear history.

## Understanding Flags

Flags (or options) modify the behavior of a Git command. They typically start with a single dash (`-`) for short flags or a double dash (`--`) for long-form flags.

- **Customization** — tailor a command to a specific workflow
- **Efficiency** — combine flags to reduce the number of steps
- **Control** — gain finer control over how an operation behaves

## Useful Git Flags

| Flag | Used With | Description |
|---|---|---|
| `-m "message"` | `git commit` | Provide a commit message directly from the command line |
| `-u` | `git add` | Stage changes to already-tracked files only |
| `--amend` | `git commit` | Modify the last commit's changes or message |
| `--oneline` | `git log` | Show each commit on a single line for readability |
| `--graph` | `git log` | Visualize commit history as a branch graph |
| `-b <name>` | `git checkout` | Create a new branch and switch to it in one step |
| `--no-ff` | `git merge` | Force a merge commit even when a fast-forward is possible |
| `--rebase` | `git pull` | Reapply local commits on top of fetched changes for a cleaner history |
| `--force` | `git push` | Overwrite the remote branch — use with caution |
| `--hard <commit>` | `git reset` | Discard all changes and reset working directory + staging to a commit |
| `--soft <commit>` | `git reset` | Move HEAD only, keeping changes staged |
| `--mixed <commit>` (default) | `git reset` | Move HEAD and unstage changes, but keep them in the working directory |
| `--no-commit` | `git revert` | Apply the revert without immediately committing it |
| `--no-edit` | `git revert` | Skip opening the commit message editor |
| `push` | `git stash push` | Save local changes to a new stash entry |
| `list` | `git stash list` | List all stashed changes |
| `apply stash@{n}` | `git stash apply` | Apply a specific stash without removing it |
| `pop` | `git stash pop` | Apply the latest stash and remove it from the list |
| `drop stash@{n}` | `git stash drop` | Delete a specific stash entry |

## Real-World Use Cases

### Collaborating on a Team Project
Multiple developers work on separate branches for different parts of a feature (e.g., frontend UI, backend API). Once complete, each branch is merged into the main codebase without overwriting others' work.
**Key features:** Branching, Merging

### Handling Hotfixes on a Live Site
A critical bug appears in production while the team continues development elsewhere. A hotfix branch is created from `main`, fixed, merged back into `main` for immediate deployment, and also merged into the development branch to stay in sync.
**Key features:** Branching, Staging, Merging

### Rolling Back a Buggy Release
After a faulty release, the team reverts specific commits that introduced bugs, or resets the project to a known-good commit.
**Key features:** `git revert`, `git reset`, `git log`

### Experimenting with New Features
A developer creates an isolated branch (e.g., `feature/new-auth-system`) to test new functionality without risking the stability of the main project. Once validated, it's merged back.
**Key features:** Branching, Merging

### Maintaining a Clean Commit History
Before pushing, a developer uses interactive rebase to squash multiple small commits into cleaner, more meaningful ones.
**Key features:** `git rebase -i`, `git commit --amend`

## Best Practices

- **Start with the basics** — master `add`, `commit`, `push`, `pull`, and `clone` before moving to advanced workflows.
- **Understand branching** — practice creating, switching, and merging branches; it's a safe way to experiment without risking the main codebase.
- **Commit often and meaningfully** — small, frequent commits with clear messages are easier to track and troubleshoot than one large commit.
- **Use GitHub features** — Pull Requests, code reviews, and issue comments streamline collaboration.
- **Stage and review before committing** — use `git status` and `git diff` to confirm exactly what you're about to commit.
- **Use `.gitignore` properly** — exclude dependencies, build artifacts, and local configs from version control.
- **Get comfortable undoing changes** — `reset`, `revert`, and `checkout` give you the confidence to experiment freely.
- **Learn to use remotes** — practice pushing, pulling, and cloning across GitHub, GitLab, or Bitbucket.
- **Use aliases** — shortcuts like `git st` (status) or `git co` (checkout) save time on repetitive commands.
- **Read the documentation** — the official Git docs are a reliable resource when you're stuck.
- **Practice with real projects** — contributing to open-source or team projects builds real-world experience with conflict resolution and branch management.

## Branch Naming Conventions

Consistent branch names keep a repository organized and easy to navigate.

- **Use a consistent prefix format:** `feature/`, `bugfix/`, or `hotfix/` followed by a short description.
  - Example: `feature/user-authentication`, `bugfix/navbar-alignment`
- **Use lowercase letters and hyphens** — avoid spaces and uppercase letters.
  - Good: `feature/new-ui-design`
  - Avoid: `Feature/NewUIDesign`
- **Be descriptive but concise** — avoid vague names like `fix` or `update`.
  - Good: `feature/user-profile-page`
  - Avoid: `feature/profile`
- **Include issue/ticket numbers when applicable** (e.g., Jira integration):
  - Example: `feature/JIRA-1234-user-auth`
- **Keep names short** — long branch names are hard to read and manage.
  - Good: `hotfix/critical-bug`
  - Avoid: `hotfix/critical-bug-in-header-footer`
- **Use team/project-specific prefixes for larger teams:**
  - Example: `backend/feature/api-endpoint`, `frontend/feature/user-dashboard`

---

*A quick-reference guide to Git and GitHub fundamentals — from first commit to advanced workflows.*
