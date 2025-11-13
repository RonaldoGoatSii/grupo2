# Advanced Concepts




## Git Rebase

### The Concept (What & Why)

At its core, `git rebase` is an operation to integrate changes from one branch onto another. It serves the same purpose as `git merge`, but the philosophy and the result are completely different.

**The `merge` Philosophy (An Auditor's History):**
`git merge` answers the question: "What *actually* happened?" It takes two histories and joins them with a new "merge commit." This commit has two parents and clearly shows, "At this point in time, the work from `feature` was combined with `main`." This creates a branching, graph-like history. It is 100% accurate but can become very messy and difficult to read.

When you `git rebase origin/main` from your `feature` branch, Git does the following:
1.  **Finds the Base:** It finds the common ancestor commit between your `feature` branch and `origin/main`.
2.  **Saves Your Commits:** It temporarily saves all the *new* commits you made on `feature` (that aren't on `main`) as "patches."
3.  **Resets Your Branch:** It resets your local `feature` branch to be identical to `origin/main`.
4.  **Re-applies Your Commits:** It takes your saved commits (patches) and applies them, one by one, on top of the new head of `origin/main`.

The result is a perfectly **linear history**. It looks like you started your work *today*, based on the very latest version of `main`, even if you actually started two weeks ago.

### The Action (How)

**Standard Rebase (Catching up with `main`):**
Your goal is to bring the new commits from `main` into your `feature` branch.

```bash
# 1. Fetch the latest state of the remote repository
# This updates your 'origin/main' reference without touching your local files.
git fetch origin

# 2. Ensure you are on the branch you want to rebase
git checkout feature/my-button

# 3. Execute the rebase
# This command means: "Re-apply my current branch's commits on top of 'origin/main'"
git rebase origin/main