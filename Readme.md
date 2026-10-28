# Git and GitHub Learning Notes

## Introduction

This repository documents my learning journey with Git and GitHub. It covers repository creation, staging, committing, pushing, pulling, resetting, branching, pull requests, reverting changes, merging, and rebasing.

The purpose of these notes is to provide a practical reference for Git commands and their use in software development.

## 1. What Is Git?

Git is a distributed version control system that tracks changes in files over time. It allows developers to maintain project history, work on separate features, and collaborate with other developers.

## 2. What Is GitHub?

GitHub is an online platform for hosting Git repositories. It provides tools for collaboration, code reviews, pull requests, and project management.

- **Git:** Tracks changes and manages version history.
- **GitHub:** Hosts Git repositories online and supports collaboration.

## 3. Creating a Repository

A repository stores project files and their version history.

### Initialize a local repository

```bash
git init
```

### Check repository status

```bash
git status
```

### Connect to a GitHub repository

```bash
git remote add origin https://github.com/USERNAME/REPOSITORY.git
```

Replace `USERNAME` and `REPOSITORY` with your actual GitHub username and repository name.

### View remote repositories

```bash
git remote -v
```

## 4. Staging Changes

Staging prepares changes for the next commit.

### Stage a specific file

```bash
git add README.md
```

### Stage all changes

```bash
git add .
```

### Unstage a file

```bash
git restore --staged README.md
```

This unstages the file while keeping its changes in the working directory.

## 5. Committing Changes

A commit records staged changes in the repository's history.

### Create a commit

```bash
git commit -m "Add Git learning notes"
```

### View commit history

```bash
git log
```

### View a concise commit history

```bash
git log --oneline
```

### View the latest commit

```bash
git show
```

**Best practice:** Use meaningful commit messages that describe the changes made.

## 6. Pushing Changes to GitHub

Pushing uploads local commits to a remote repository.

### Push to the main branch

```bash
git push origin main
```

### Push a new branch and set its upstream

```bash
git push -u origin feature-login
```

After setting the upstream branch, you can usually use:

```bash
git push
```

## 7. Pulling Changes from GitHub

Pulling retrieves remote changes and integrates them into the current local branch.

```bash
git pull origin main
```

To download remote changes without integrating them immediately:

```bash
git fetch origin
```

## 8. Branching

Branches allow developers to work on features independently without directly changing the main development line.

### List branches

```bash
git branch
```

### Create a new branch

```bash
git branch feature-login
```

### Create and switch to a new branch

```bash
git checkout -b feature-login
```

### Switch to an existing branch

```bash
git checkout main
```

### Delete a merged branch

```bash
git branch -d feature-login
```

### Force-delete a branch

```bash
git branch -D feature-login
```

Use force deletion carefully because it can remove a branch containing unmerged work.

### Example feature workflow

```bash
git checkout -b feature-login
git add .
git commit -m "Add login feature"
git push -u origin feature-login
```

## 9. Pull Requests (PRs)

A pull request is a GitHub feature that proposes merging changes from one branch into another.

For example, a pull request can propose merging `feature-login` into `main`.

### Steps for creating a pull request

1. Create a feature branch.
2. Make changes and commit them.
3. Push the feature branch to GitHub.
4. Open your repository on GitHub.
5. Create a pull request with `main` as the base branch and `feature-login` as the compare branch.
6. Review the changes and address feedback.
7. Merge the pull request when the changes are approved and ready.

A pull request allows code review before the changes are merged.

## 10. Resetting Changes

The `git reset` command moves the current branch to an earlier commit. Depending on the option, it can also change the staging area and working directory.

### Soft reset

```bash
git reset --soft HEAD~1
```

Moves the branch back one commit while keeping the changes staged.

### Mixed reset

```bash
git reset --mixed HEAD~1
```

Moves the branch back one commit and unstages the changes while keeping them in the working directory.

### Hard reset

```bash
git reset --hard HEAD~1
```

Moves the branch back one commit and discards the corresponding changes from the staging area and working directory.

**Warning:** A hard reset can permanently discard uncommitted work. Use it carefully.

### Reset to a specific commit

```bash
git reset --soft COMMIT_HASH
```

Replace `COMMIT_HASH` with the actual commit hash.

## 11. Reverting Changes

The `git revert` command reverses the effect of an earlier commit by creating a new commit.

### Revert the latest commit

```bash
git revert HEAD
```

### Revert a specific commit

```bash
git revert COMMIT_HASH
```


 Reset versus revert

Reset: Moves the branch reference to an earlier commit and may alter staged or working files.
Revert: Creates a new commit that reverses an earlier commit's changes.

For commits already shared with other developers, reverting is generally safer than rewriting shared history.





 Resolve conflicts during a rebase

1. Open the conflicting files.
2. Resolve the conflict markers.
3. Stage the resolved files.
4. Continue the rebase.




## 14. Merge versus Rebase
git merge combines changes from one branch into another while preserving the existing branch history.

git rebase takes commits from your current branch and replays them on top of another branch's latest commit.



The following example demonstrates the main commands from repository initialization to feature development.

```bash
# Initialize the repository
git init

# Check the repository status
git status

# Stage project files
git add .

# Commit the changes
git commit -m "Initial project setup"

# Connect to GitHub
git remote add origin https://github.com/USERNAME/REPOSITORY.git

# Rename the current branch to main
git branch -M main

# Push the initial commit
git push -u origin main

# Create and check out a feature branch
git checkout -b feature-login

# Stage and commit feature changes
git add .
git commit -m "Add login feature"

# Push the feature branch
git push -u origin feature-login

# After merging the pull request on GitHub,
# return to the main branch
git checkout main

# Update the local main branch
git pull origin main
```

Replace the repository URL with your own GitHub repository URL. If the remote repository already contains commits, check its history before initializing or pushing new history.


Through this learning process, I have learned that:

- Git tracks changes and maintains project history.
- GitHub hosts repositories and supports collaboration.
- Staging selects changes for a commit.
- Committing records changes locally.
- Pushing uploads local commits to GitHub.
- Pulling integrates remote changes into a local branch.
- Branching allows independent feature development.
- Pull requests support code review before merging.
- Resetting moves a branch to an earlier commit.
- Reverting reverses a commit without removing the original history.
- Merging integrates changes from different branches.
- Rebasing replays commits onto a new base and can rewrite history.
- `git checkout` can be used to switch branches and create new branches.


