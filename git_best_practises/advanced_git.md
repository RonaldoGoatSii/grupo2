# Advanced Concepts




## Git Rebase

### The Concept (What & Why)

At its core, `git rebase` is an operation to integrate changes from one branch onto another. It serves the same purpose as `git merge`, but the philosophy and the result are completely different.

**The `merge` Philosophy (An Auditor's History):**
`git merge` answers the question: "What *actually* happened?" It takes two histories and joins them with a new "merge commit." This commit has two parents and clearly shows, "At this point in time, the work from `feature` was combined with `main`." This creates a branching, graph-like history. It is 100% accurate but can become very messy and difficult to read.

