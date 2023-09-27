# Git Commands Tutorial

This tutorial provides an overview of essential Git commands and their usage for version control and collaboration in software development projects.

## Table of Contents

- [Introduction to Git](#introduction-to-git)
- [Getting Started](#getting-started)
- [Basic Git Commands](#basic-git-commands)
- [Working with Branches](#working-with-branches)
- [Collaboration and Remotes](#collaboration-and-remotes)
- [Advanced Git Commands](#advanced-git-commands)
- [Team Workflows](#team-workflows)

---

## Introduction to Git

Git is a distributed version control system that helps you track changes, collaborate with others, and manage your project's history effectively.

## Getting Started

To begin using Git, you'll first need to install it on your system. Download and install Git from the [official website](https://git-scm.com/downloads). Once installed, open a terminal or command prompt and configure your identity using the following commands:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

## Basic Git Commands

### 1. Initializing a Git Repository

**Usage:** When starting a new project.

**Example:**
```bash
git init
```

### 2. Checking Repository Status

**Usage:** To see the status of files in your repository, including changes to be committed and untracked files.

**Example:**
```bash
git status
```

### 3. Adding and Committing Changes

**Usage:** To save changes and create a new version.

**Example:**
```bash
git add <file>  # Add a specific file
git commit -m "Commit message"
```

### 4. Viewing Commit History

**Usage:** To see the history of commits, including who made them and when.

**Example:**
```bash
git log
```

### 5. Ignoring Files

**Usage:** To prevent certain files from being tracked by Git.

**Example:** Create a `.gitignore` file with patterns to ignore.

## Working with Branches

### 1. Creating a Branch

**Usage:** When starting a new feature or fixing a bug, it's good practice to create a new branch to isolate the changes.

**Example:**
```bash
git branch <branch_name>
```

### 2. Switching Branches

**Usage:** To switch between different features or bug fix branches.

**Example:**
```bash
git checkout <branch_name>
```

### 3. Merging Branches

**Usage:** To combine changes from one branch into another, typically after completing a feature or fixing a bug.

**Example:**
```bash
git merge <branch_name>
```

## Collaboration and Remotes

### 1. Cloning a Repository

**Usage:** To start working on an existing project.

**Example:**
```bash
git clone <repository_url>
```

### 2. Pushing Changes

**Usage:** To share your local changes with others in a remote repository.

**Example:**
```bash
git push origin <branch_name>
```

### 3. Pulling Changes

**Usage:** To get the latest changes from the remote repository and merge them into your local branch.

**Example:**
```bash
git pull origin <branch_name>
```

## Advanced Git Commands

## Git Rebase and Merge

This section provides an overview of the `git rebase` command and its comparison with the `git merge` command, along with practical applications and considerations for integrating rebasing into the Git workflow.

### Merging vs. Rebasing

The `git rebase` command can significantly simplify the development process -- but it must be used with caution. Below we'll compare `git rebase` with `git merge`, exploring when and how to use them effectively.

### Conceptual Overview

Git rebase and git merge are both used to integrate changes from one branch into another but operate in distinct ways. Git merge creates a "merge commit" that ties the histories of both branches, resulting in a non-destructive operation. However, it can lead to a cluttered feature branch history if main is actively updated.

**The Merge Option**

Merging the main branch into the feature branch using `git merge` creates a merge commit and preserves the complete history.

```plaintext
*   Merge branch 'main' into feature
|\  
| * Commit C3 (main)
| * Commit C2 (main)
| * Commit C1 (main)
|/  
* Commit F2 (feature)
* Commit F1 (feature)
```

However, it can lead to a cluttered feature branch history if main is actively updated.

**The Rebase Option**

Rebasing the feature branch onto the main branch using `git rebase` results in a linear project history.

```plaintext
* Commit C3 (main)
* Commit C2 (main)
* Commit C1 (main)
* Commit F2 (feature)
* Commit F1 (feature)
```

However, it can be potentially catastrophic if used incorrectly and loses the context provided by a merge commit.

**Interactive Rebasing**

Interactive rebasing allows altering commits during the rebase process, providing complete control over the branch's commit history.

```plaintext
* Commit C3 (main)
* Commit C2 (main)
* Commit C1 (main)
* Commit F3 (feature - squashed)
```

This is useful for cleaning up a messy history before merging a feature branch into the main branch.

**The Golden Rule of Rebasing**

The golden rule of git rebase is to avoid using it on public branches to prevent confusing history and diverging main branches. Force-pushing should be used cautiously and preferably on private branches.

### Workflow Walkthrough

Rebasing can be integrated into the Git workflow at various stages of a feature's development:

1. **Local Cleanup**: Periodically perform an interactive rebase to clean up in-progress features and make commits more focused and meaningful.

2. **Incorporating Upstream Changes**: Incorporate upstream changes from the main branch using either `git merge` or `git rebase` to keep the feature branch up to date.

3. **Reviewing a Feature with a Pull Request**: Clean up code with an interactive rebase before submitting a pull request to present a clean and easy-to-follow feature branch history.

4. **Integrating an Approved Feature**: Rebase the feature onto the main branch to maintain a linear history before merging the feature into the main codebase.

### Summary

Understanding when and how to use `git rebase` and `git merge` allows you to choose between a clean, linear history using rebase and a complete project history with merge. Both options are valid, and leveraging the benefits of `git rebase` can lead to a more streamlined Git workflow.

---

The examples are now incorporated in line with the respective explanations to provide a visual representation of Git history in different scenarios.

### 2. Tagging

**Usage:** To mark specific points in history, such as release versions.

**Example:**
```bash
git tag <tag_name>
```

### 3. Cherry-Picking

**Usage:** To apply a specific commit from one branch to another.

**Example:**
```bash
git cherry-pick <commit_hash>
```
## Team Workflows

### 1. Feature Branch Workflow

The core idea behind the Feature Branch Workflow is that all feature development should take place in a dedicated branch instead of the main branch. This encapsulation makes it easy for multiple developers to work on a particular feature without disturbing the main codebase. It also means the main branch will never contain broken code, which is a huge advantage for continuous integration environments.


**Example: Suzanne and Prashant each have their own feature branches**

#### Suzanne begins a new feature
Before she starts developing a feature, Suzanne needs an isolated branch to work on. She can request a new branch with the following command:

**Example:**
```bash
git checkout -b suzannes-feature main
```

#### Meanwhile, Prashant is doing the exact same thing
While Suzanne and Prashant are working on suzannes-feature and discussing it in her pull request, Prashant is doing the exact same thing with his own feature branch. By isolating features into separate branches, everybody can work independently, yet developers can still have visibility into each others' changes and can collaborate as needed.


---

This tutorial covers basic Git commands and provides examples to help you understand when and why you would use these operations in a real-world scenario. Explore and experiment with these commands to become proficient in using Git for your projects. Happy coding!
