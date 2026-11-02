
# Session 5: Branches, Merging, and Merge Conflicts

## 1. Understanding Git Branches

### What is a Git Branch?

A branch in Git is an independent line of development that allows developers to work on different features or fixes without directly affecting the main codebase or main branch.

Developers can create multiple branches for different tasks.

### Why Do We Use Branches?

- To work on new features independently.
- To fix bugs without affecting existing code.
- To allow multiple developers to work simultaneously.
- To keep the main branch stable.
- To organize development work.

### Common Branches

| Branch | Purpose |
|---|---|
| `main` | Contains the main codebase. |
| `develop` | Used for ongoing development. |
| `feature` | Used to develop new features. |
| `bugfix` | Used to fix bugs. |

### Example

```text
main
 |
 |------ feature-login
 |
 |------ feature-payment
 |
 |------ bugfix-header
```

Each branch can have its own changes and commits.

-----------------------------------------------------------------------------------------------

## 2. Creating and Switching Branches

Git provides commands to create and switch between branches.

### Common Commands

**1. Check available branches:**

```bash
git branch
```

Displays the local branches in the repository.

**2. Create a new branch:**

```bash
git branch feature-login
```

Creates a new branch called `feature-login`.

**3. Switch to an existing branch:**

```bash
git switch feature-login
```

Switches to the `feature-login` branch.

**4. Create and switch to a new branch:**

```bash
git switch -c feature-payment (we can also use checkout instead of switch)
```

Creates a new branch and switches to it.

**5. Switch back to main:**

```bash
git checkout main
```

**6. View all branches, including remote branches:**

```bash
git branch -a
```

**Note:** The currently active branch is marked with an asterisk (`*`) when you execute `git branch`.

---

## 3. Making Changes in Different Branches

Each branch can contain different changes and commits.

### Example

Suppose you have a project with a `main` branch.

You want to develop a login feature without modifying the main branch directly.

**Step 1: Create a new branch**

```bash
git switch -c feature-login or git checkout -b branch-name
```

**Step 2: Create or modify project files**

For example, create a file called:

```text
login.html
```

**Step 3: Stage the changes**

```bash
git add .
```

**Step 4: Commit the changes**

```bash
git commit -m "Added login functionality"
```

**Step 5: Switch back to main**

```bash
git switch main or git checkout main
```

Now, the login feature changes exist in the `feature-login` branch and have not yet been merged into `main`.

**Note:** Always check your current branch using `git branch` before making changes.

---------------------------------------------------------------------

## 4. Understanding `git merge`

### What is Git Merge?

Git merge is used to combine changes from one branch into another branch.

It helps developers integrate their work after completing a feature or bug fix.

### Why Do We Use Git Merge?

- To combine changes from different branches.
- To integrate completed features into the main branch.
- To bring bug fixes into the main codebase.
- To collaborate with other developers.

### Command

```bash
git merge branch-name
```

Here, `branch-name` represents the branch whose changes you want to merge into your current branch.

**Important:** Git merges the specified branch into the currently checked-out branch.

--------------------------------------------------------------------------------------------

## 5. Merging One Branch into Another

### Example

Suppose you have two branches:

- `main`
- `feature-login`

You have completed the login functionality in the `feature-login` branch.

Now, you want to merge those changes into `main`.

### Steps

**Step 1: Switch to the main branch**

```bash
git switch main
```

**Step 2: Merge the feature branch**

```bash
git merge feature-login
```

**Step 3: Check the repository status**

```bash
git status
```

**Step 4: View the commit history**

```bash
git log --oneline --graph --all
```

The changes from `feature-login` are now integrated into `main`.

### Example Branch Flow

Before merging:

```text
main
 |
 A
 |
 B

feature-login
 |
 A
 |
 B
 |
 C
```

After merging:

```text
main
 |
 A
 |
 B
 |\
 | C
 |/
```
---------------------------------------------------------------------------------------------------------------

## 6. Understanding Merge Conflicts

### What is a Merge Conflict?

A merge conflict occurs when Git cannot automatically combine changes from different branches.

This commonly happens when two branches modify the same part of the same file differently.

### Example

Suppose two developers are working on different branches.

**Developer 1 (main branch):**

```text
Welcome to Git
```

**Developer 2 (feature branch):**

```text
Welcome to Bitbucket
```

Both developers modify the same line in the same file.

When Git tries to merge these changes, it cannot automatically decide which version should be kept.

This results in a merge conflict.

### Common Reasons for Merge Conflicts

- Two branches modify the same line differently.
- One branch modifies a file while another branch deletes it.
- Multiple developers make conflicting changes to the same file.

**Note:** Merge conflicts are normal in collaborative development. They need to be resolved manually.

-------------------------------------------------------------------------------------------------------------------

## 7. Resolving Merge Conflicts

When a merge conflict occurs, Git marks the conflicting sections inside the affected file.

### Example Conflict

```text
<<<<<<< HEAD
Welcome to Git
=======
Welcome to Bitbucket
>>>>>>> feature-login
```

### Understanding Conflict Markers

| Marker | Meaning |
|---|---|
| `<<<<<<< HEAD` | Start of the current branch changes. |
| `=======` | Separates the two conflicting changes. |
| `>>>>>>> feature-login` | End of the incoming branch changes. |

### Steps to Resolve a Merge Conflict

**Step 1: Identify the conflicted files**

```bash
git status
```

Git displays the files that have merge conflicts.

**Step 2: Open the conflicted file**

Open the file in your code editor.

**Step 3: Review the conflicting changes**

Understand both versions and decide what the final content should be.

**Step 4: Edit the file**

For example, you may decide to keep:

```text
Welcome to Git and Bitbucket
```

Remove all conflict markers:

```text
<<<<<<< HEAD
=======
>>>>>>> feature-login
```

**Step 5: Save the file**

Make sure the final content is correct and all conflict markers are removed.

**Note:** Git does not automatically decide which change is correct. The developer must choose the appropriate final content.

---

## 8. Completing a Merge

After resolving all merge conflicts, you need to complete the merge.

### Steps

**Step 1: Stage the resolved files**

```bash
git add .
```

Alternatively, stage only the resolved files:

```bash
git add filename
```

**Step 2: Check the status**

```bash
git status
```

Make sure all merge conflicts have been resolved.

**Step 3: Complete the merge**

```bash
git commit
```

Git will use a default merge commit message. Save and close the editor to complete the merge.

If Git has already prepared a default merge message, you can also use:

```bash
git merge --continue
```

**Step 4: Verify the merge**

```bash
git log --oneline --graph --all
```

Your merge is now complete.

### Useful Merge Commands

**Abort an ongoing merge:**

```bash
git merge --abort
```

This attempts to return the repository to its state before the merge started.

**Check merge status:**

```bash
git status
```

**View branch history:**

```bash
git log --oneline --graph --all
```

-----------------------------------------------------------------------------------
