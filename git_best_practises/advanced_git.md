# Advanced Concepts




## Git Rebase

### The Concept 

`git rebase` is an operation to integrate changes from one branch onto another. It serves the same purpose as `git merge`, but the philosophy and the result are completely different.

**The `merge` Philosophy (An Auditor's History):**
`git merge` answers the question: "What *actually* happened?" It takes two histories and joins them with a new "merge commit." This commit has two parents and clearly shows, "At this point in time, the work from `feature` was combined with `main`." This creates a branching, graph-like history. It is 100% accurate but can become very messy and difficult to read.

When you `git rebase origin/main` from your `feature` branch, Git does the following:
1.  **Finds the Base:** It finds the common ancestor commit between your `feature` branch and `origin/main`.
2.  Saves Your Commits: It temporarily saves all the *new* commits you made on `feature` (that aren't on `main`) as "patches."
3.  Resets Your Branch:** It resets your local `feature` branch to be identical to `origin/main`.
4.  **Re-applies Your Commits:** It takes your saved commits (patches) and applies them, one by one, on top of the new head of `origin/main`.

The result is a perfectly **linear history**. It looks like you started your work *today*, based on the very latest version of `main`, even if you actually started two weeks ago.

### The Action (How)

**Standard Rebase (Catching up with `main`):**
Your goal is to bring the new commits from `main` into your `feature` branch.


1. Fetch the latest state of the remote repository
 This updates your 'origin/main' reference without touching your local files.
git fetch origin

2. Ensure you are on the branch you want to rebase
git checkout feature/my-button

3. Execute the rebase
This command means: "Re-apply my current branch's commits on top of 'origin/main'"
git rebase origin/main




## Git Squash

### The Concept

`git squash` (usually performed via interactive rebase) is an operation to combine multiple small commits into a single, cohesive commit. It serves to condense "Work In Progress" steps into a final product.

**The `wip` Philosophy (The Developer's Draft):**
During development, history is often messy. It answers the question: "How was this built?" It includes typos, quick saves, and broken code (`wip`, `fix`, `temp`). While accurate to the process, this noise makes the final history hard to scan and understand.

When you `git rebase -i` to squash your commits, Git does the following:
1.  **Opens the List:** It opens your text editor with a list of the commits you selected to review.
2.  **Marks for Meltdown:** You change the command from `pick` to `squash` on the commits you want to dissolve.
3.  **Combines Changes:** It takes the file changes from all the squashed commits and merges them into the first commit.
4.  **Rewrites the Message:** It asks you to write a single, new commit message that represents the entire group of changes.

The result is a **cleaner history** where one feature equals exactly one commit, making code reviews and rollbacks significantly easier.

### The Action (How)

**Interactive Rebase (Compacting Commits):**
Your goal is to combine your last few "WIP" commits into one clean commit before pushing.

```bash
# 1. Start the interactive rebase
# 'HEAD~4' means you want to operate on the last 4 commits of your history.
git rebase -i HEAD~4

# 2. Mark commits to squash (Action inside the editor)
# Change 'pick' to 'squash' (or 's') for the lines you want to combine into the top one.
# Then save and close the file.

# 3. Create the new message (Action inside the editor)
# Git will open the editor again. Write one final message for the combined commit.
```

## Git Cherry-pick

### The Concept

`git cherry-pick` is an operation to copy a specific commit from one branch and apply it to another. It serves to move precise changes without merging the entire history of a branch.

**The `cherry-pick` Philosophy (The Surgical Transplant):**
`git cherry-pick` answers the question: "How do I get *just that one fix*?" Unlike `merge` or `rebase`, which bring the entire history of a branch, `cherry-pick` allows you to select a specific commit from anywhere in the repository (e.g., a bug fix in `dev`) and "transplant" it onto your current branch (e.g., `production`) without the rest of the `dev` code.



When you `git cherry-pick <commit-hash>` onto your current branch, Git does the following:
1.  **Reads the Commit:** It identifies the specific snapshot and changes associated with the Hash ID you provided.
2.  **Calculates the Diff:** It figures out exactly what changed in that commit compared to its parent.
3.  **Applies the Patch:** It applies those exact changes to your current working branch as a new patch.
4.  **Creates a New Commit:** It commits the changes with the same message and author, but generates a brand new commit hash.

The result is that **specific work is duplicated** onto your branch without bringing along any unwanted history or unfinished features.

### The Action (How)

**Standard Cherry-pick (Moving a specific fix):**
Your goal is to copy a specific commit (by its ID) to your current branch.

```bash
# 1. Find the Commit ID (Hash)
# Use git log to find the ID (e.g., a1b2c3d) of the specific fix you need.
git log --oneline

# 2. Ensure you are on the target branch
# Switch to the branch where you want the commit to land.
git checkout main

# 3. Execute the cherry-pick
# This command copies the changes from 'a1b2c3d' to your current branch.
git cherry-pick a1b2c3d