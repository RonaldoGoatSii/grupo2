
# Pull Request Workflow & Code Review Guide

## 📑 Table of Contents

1. [Create a Branch or Fork](#create-a-branch-or-fork)  
2. [Commit Your Changes](#commit-your-changes)  
3. [Push the Branch to GitHub](#push-the-branch-to-github)  
4. [Open a Pull Request (PR)](#open-a-pull-request-pr)  
5. [Discuss and Review](#discuss-and-review)  
6. [Merge or Close](#merge-or-close)  
7. [Merge Options](#merge-options)  
8. [Code Review Guide](#code-review-guide)  
9. [Best Practices](#best-practices)  
10. [Lifecycle Diagram](#lifecycle-diagram)  
11. [Practical Workflow Example](#practical-workflow-example)  
12. [Additional Resources](#additional-resources)

---

## Create a Branch or Fork

When you want to make changes, start by creating your own workspace:

- **If you have permission to write to the repository:**  
  Create a new branch to work on your changes. This keeps your work separate from the main code.  
  Example branch name: `feature/add-login-page`  

  git checkout -b feature/add-login-page


* **If you don’t have permission:**
  Fork (copy) the repository to your own GitHub account. Then clone your fork to your computer.
  Work on your fork and create branches there.

---

## Commit Your Changes

After you make changes to files:

1. **Stage your changes** to prepare them for commit:

   ```bash
   git add .
   ```
2. **Commit your changes** with a clear message describing what you did.
   Use [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) format to keep messages consistent:

   ```bash
   git commit -m "feat(login): add user authentication flow"
   ```

---

## Push the Branch to GitHub

Send your local branch and commits to GitHub:

```bash
git push origin feature/add-login-page
```

---

## Open a Pull Request (PR)

* Go to the original repository on GitHub.
* You might see a **Compare & pull request** button—click it.
* Choose the base branch (usually `main` or `master`) and your branch.
* Write a clear title and detailed description explaining your changes and why.
* Submit the Pull Request (PR) to start the review process.

---

## Discuss and Review

* Your teammates will review the PR and leave comments or suggestions.
* You can reply to feedback, make improvements, commit, and push updates.
* All new commits automatically update the PR.

---

## Merge or Close

* After approval and successful tests, merge your PR into the base branch.
* Delete your feature branch to keep the repository clean.
* If your changes are no longer needed, close the PR without merging.

---

## Merge Options

GitHub offers different ways to merge your changes:

| Merge Type           | What it does                                                  | When to use                                       |
| -------------------- | ------------------------------------------------------------- | ------------------------------------------------- |
| **Merge Commit**     | Keeps all commits and adds a merge commit to history.         | When you want full history and context.           |
| **Squash and Merge** | Combines all commits into one clean commit.                   | To keep the main branch history simple and clean. |
| **Rebase and Merge** | Applies your commits on top of the base branch without merge. | To create a linear, easy-to-follow history.       |

---

## Code Review Guide

Code reviews help improve quality and share knowledge:

* Check if the code works correctly and follows style guidelines.
* Give clear, respectful, and helpful feedback.
* Suggest specific improvements using GitHub's review tools.
* Verify tests and documentation are updated if needed.

---

## Best Practices

### For PR Authors

* Keep your PRs small and focused on one thing.
* Use clear, descriptive titles and commit messages.
* Add tests for any new features or fixes.
* Link related issues, e.g., `Fixes #123`.
* Review your own code before submitting.

### For Reviewers

* Be polite and constructive.
* Focus on the code, not the person.
* Ask questions if something is unclear.
* Approve promptly when concerns are addressed.

---

## Lifecycle Diagram

Here’s the basic Pull Request process:

1. Create a branch
2. Make and commit changes
3. Open a Pull Request
4. Discuss and review the changes
5. Make updates if needed
6. Approve and merge the PR
7. Delete the feature branch

If reviewers request changes, repeat steps 4 and 5.

---

# Practical Workflow Example


## Clone the repository
```
git clone https://github.com/username/repo.git
cd repo
```

## Create a new branch for your work
```
git checkout -b docs/explain-pull-requests
```

## Edit files (e.g., README.md)
```
nano README.md
```

## Stage and commit your changes
```
git add README.md
git commit -m "docs(readme): add pull request workflow and code review guide"
```

## Push the branch to GitHub
```
git push origin docs/explain-pull-requests
```
## Then open a Pull Request on GitHub and request review



## Additional Resources

* [GitHub Docs: About Pull Requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-project/about-pull-requests)
* [GitHub Docs: Reviewing Changes in Pull Requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/about-code-reviews)
* [GitHub Flow Guide](https://docs.github.com/en/get-started/using-git/github-flow)
* [Conventional Commits Specification](https://www.conventionalcommits.org/en/v1.0.0/)


