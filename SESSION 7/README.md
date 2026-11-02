
# Session 7: Git Stash, Cherry-Pick, and Practical Workflow

## 1. Understanding Git Stash

### What is Git Stash?

Git Stash is used to temporarily save uncommitted changes in your working directory.

It allows developers to switch branches without committing unfinished work.

### Why Do We Use Git Stash?

- To temporarily save unfinished changes.
- To switch between branches without committing changes.
- To work on urgent tasks without losing current work.
- To keep the working directory clean.

### Command

```bash
git stash
```

This command temporarily saves changes in the working directory and staging area and cleans those changes from the working directory.

### Example

Suppose you are working on a feature branch:

```text
feature-login
```

You have modified a file but have not completed the task.

Suddenly, you need to switch to another branch to fix an urgent bug.

Instead of committing unfinished changes, you can use:

```bash
git stash
```

Your changes are temporarily saved, and you can switch branches.

--------------------------------------------------------------------------

## 2. Applying and Restoring Stashed Changes

Git provides different commands to view, apply, and restore stashed changes.

### Common Commands

**1. Save changes in the stash:**

```bash
git stash
```

**2. View all stashed changes:**

```bash
git stash list
```

Example Output:

```text
stash@{0}: WIP on feature-login
stash@{1}: WIP on main
```

**3. Apply the latest stash:**

```bash
git stash apply
```

This restores the latest stashed changes but keeps them in the stash list.

**4. Apply a specific stash:**

```bash
git stash apply stash@{1}
```

**5. Apply and remove the latest stash:**

```bash
git stash pop
```

This applies the latest stash and removes it from the stash list if the application succeeds.

**6. Remove a specific stash:**

```bash
git stash drop stash@{0}
```

**7. Remove all stashes:**

```bash
git stash clear
```

**Important:** `git stash clear` removes all stash entries. Use it carefully.

### Difference Between `git stash apply` and `git stash pop`

| git stash apply | git stash pop |
|---|---|
| Applies stashed changes. | Applies stashed changes. |
| Keeps the stash entry. | Removes the stash entry if successfully applied. |
| Useful when you may need the stash again. | Useful when you no longer need the stash. |

### Saving Untracked Files

To stash untracked files as well:

```bash
git stash -u
```

### Example Workflow

```bash
# Check current changes
git status

# Save unfinished changes
git stash

# Switch to another branch
git switch main or git checkout main

# Complete your urgent task

# Switch back to your feature branch
git switch feature-login

# Restore previously saved changes
git stash pop
```

**Note:** Stashing does not create a commit. It temporarily stores your changes so you can work on something else.

---------------------------------------------------------------------------------

## 3. Understanding `git cherry-pick`

### What is Git Cherry-Pick?

Git Cherry-Pick is used to apply a specific commit from one branch to another branch.

Instead of merging the entire branch, it allows you to select only the required commit.

### Why Do We Use Git Cherry-Pick?

- To apply a specific bug fix to another branch.
- To copy selected changes between branches.
- To avoid merging an entire branch.
- To reuse an existing commit in another branch.

### Command

```bash
git cherry-pick <commit-id>
```

Here, `<commit-id>` represents the commit you want to apply.

### Example

Suppose you have two branches:

```text
main
feature-login
```

A developer has fixed an important bug in the `feature-login` branch.

You want to apply only that bug fix to the `main` branch without merging all the changes from `feature-login`.

You can use `git cherry-pick`.

------------------------------------------------------------------------------------------

## 4. Applying a Commit to Another Branch

### Example Scenario

Suppose your repository has the following branches and commits:

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
 |
 D
```

Here:

- Commit A and B are common commits.
- Commit C contains login functionality.
- Commit D contains a bug fix.

You want to apply only Commit D to the `main` branch.

### Steps

**Step 1: Find the required Commit ID**

Switch to the feature branch:

```bash
git switch feature-login or git checkout feature-login
```

View the commit history:

```bash
git log --oneline
```

Example Output:

```text
d4e5f6g Fixed login validation bug
c1d2e3f Added login functionality
b1c2d3e Initial commit
```

Copy the **Commit ID** of the required bug fix.

**Step 2: Switch to the destination branch**

```bash
git switch main
```

**Step 3: Apply the specific commit**

```bash
git cherry-pick d4e5f6g
```

**Step 4: Verify the changes**

```bash
git log --oneline
```

Git creates a new commit on the `main` branch containing the selected changes.

### Updated Commit History

```text
main
 |
 A
 |
 B
 |
 D'  <-- Cherry-picked commit

feature-login
 |
 A
 |
 B
 |
 C
 |
 D
```

**Note:** The cherry-picked commit gets a new Commit ID because Git creates a new commit on the destination branch.

### Useful Cherry-Pick Commands

**Apply a specific commit:**

```bash
git cherry-pick <commit-id>
```

**Apply multiple individual commits:**

```bash
git cherry-pick <commit-id-1> <commit-id-2>
```

**Abort an ongoing cherry-pick:**

```bash
git cherry-pick --abort
```

**Continue after resolving conflicts:**

```bash
git cherry-pick --continue
```
---------------------------------------------------------------------------------

## 5. Difference Between Git Stash and Git Cherry-Pick

Both commands help manage changes, but they serve different purposes.

| Git Stash | Git Cherry-Pick |
|---|---|
| Temporarily saves uncommitted changes. | Applies an existing commit to another branch. |
| Does not normally create a regular commit. | Creates a new commit. |
| Useful for unfinished work. | Useful for selecting specific committed changes. |
| Changes can be restored later. | Selected commit changes are applied immediately. |
| Works with working directory changes. | Works with existing commits. |

### When Should We Use Them?

**Use Git Stash when:**

- You have unfinished changes.
- You need to switch branches temporarily.
- You don't want to commit incomplete work.

**Use Git Cherry-Pick when:**

- You need a specific commit from another branch.
- You want to apply a bug fix to another branch.
- You don't want to merge the entire source branch.

------------------------------------------------------------------------------------------

## 6. Practical Git Workflow

Let's understand how Git Stash and Cherry-Pick can be used in a real-world development scenario.

### Scenario

You are working on a login feature.

Suddenly, your team asks you to fix an urgent bug in the main branch.

You can follow this workflow:

```bash
# Check current branch
git branch

# Check current changes
git status

# Temporarily save unfinished changes
git stash

# Switch to main branch
git switch main

# Create a bug-fix branch
git switch -c bugfix-login

# Fix the bug and stage changes
git add .

# Commit the bug fix
git commit -m "Fixed login validation bug"

# Switch back to the original feature branch
git switch feature-login

# Restore unfinished changes
git stash pop
```

After completing the bug fix, suppose you also need that specific fix in another branch.

You can use:

```bash
# Switch to the destination branch
git checkout main

# Apply the required bug-fix commit
git cherry-pick <commit-id>
```

----------------------------------------------------------------------------------
