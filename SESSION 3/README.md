
# Session 3: Git History and Reset

## 1. Understanding HEAD and Commit IDs

### What is HEAD?

`HEAD` is a reference that points to the currently checked-out commit in Git.

In simple words, HEAD tells Git which commit or branch you are currently working on.

### What is a Commit ID?

Every commit in Git has a unique identifier called a Commit ID (SHA-1 hash).

It helps identify a specific commit in the repository history.

**Example:**

```text
commit a1b2c3d4e5f6...
Author: Developer
Message: Initial commit
```

Here, `a1b2c3d4e5f6...` represents the **Commit ID**.

### Important HEAD References

| Reference | Meaning |
|---|---|
| `HEAD` | Current commit. |
| `HEAD~1` | Previous commit (one commit before HEAD). |
| `HEAD~2` | Two commits before HEAD. |
| `HEAD~3` | Three commits before HEAD. |

--------------------------------------------------------

## 2. Viewing History Using `git log`

### What is `git log`?

The `git log` command displays the commit history of a repository.

It helps us understand:
- Who made the changes.
- When the changes were made.
- Commit messages.
- Commit IDs.

### Common Commands

**1. View complete commit history:**

```bash
git log
```

**2. View commit history in a short format:**

```bash
git log --oneline
```

**Example Output:**

```text
a1b2c3d Added login functionality
e4f5g6h Updated README file
i7j8k9l Initial commit
```

**3. View commit history in graphical format:**

```bash
git log --oneline --graph --all
```

This command displays commit history in a graphical representation.

-------------------------------------------------

## 3. Viewing a Specific Commit Using `git show`

### What is `git show`?

The `git show` command displays detailed information about a specific commit.

It helps us understand what changes were introduced in that commit.

### Common Commands

**1. View the latest commit:**

```bash
git show
```

**2. View a specific commit using its Commit ID:**

```bash
git show <commit-id>
```

**Example:**

```bash
git show a1b2c3d
```

This displays:
- Commit ID.
- Author details.
- Commit date.
- Commit message.
- Changes introduced in that commit.

-----------------------------------------------------------------------------------------

## 4. Understanding `git reset`

### What is `git reset`?

The `git reset` command is used to move the current branch reference to another commit.

It is commonly used to undo commits or remove changes from the staging area.

Git provides three reset modes:

| Mode | Description |
|---|---|
| `--soft` | Moves HEAD but keeps changes staged. |
| `--mixed` | Moves HEAD and keeps changes unstaged. |
| `--hard` | Moves HEAD and discards affected tracked changes from the staging area and working directory. |

### Understanding the Difference

Suppose you have the following commit history:

```text
Commit C  <-- HEAD
Commit B
Commit A
```

After executing a reset to `HEAD~1`:

```text
Commit B  <-- HEAD
Commit A
```

The branch now points to Commit B instead of Commit C.

The difference between reset modes is how they handle the changes introduced by Commit C.

---

## 5. Using `git reset --soft HEAD~1`

### What is `--soft`?

The `--soft` option moves HEAD to the previous commit but keeps the changes from the latest commit in the staging area.

In simple words:
- The latest commit is undone.
- Changes are preserved.
- Changes remain staged.
- You can create a new commit with those changes.

### Command

```bash
git reset --soft HEAD~1
```

### Example

Before reset:

```text
Commit C  <-- HEAD
Commit B
Commit A
```

Execute:

```bash
git reset --soft HEAD~1
```

After reset:

```text
Commit B  <-- HEAD
Commit A
```

The changes introduced in Commit C are still available in the staging area.

Check the status:

```bash
git status
```

You will see the changes under:

```text
Changes to be committed
```

**When to use it?**

- When you want to undo the latest commit.
- When you want to modify the previous commit's changes.
- When you want to create a new commit with a different message.

------------------------------------------------------

## 6. Using `git reset --hard HEAD~1`

### What is `--hard`?

The `--hard` option moves HEAD to the previous commit and resets the staging area and working directory to match that commit.

In simple words:
- The latest commit is undone from the current branch history.
- Staged changes are removed.
- Tracked working directory changes are discarded.
- Changes introduced by the removed commit are no longer present in the working directory.

### Command

```bash
git reset --hard HEAD~1
```

### Example

Before reset:

```text
Commit C  <-- HEAD
Commit B
Commit A
```

Execute:

```bash
git reset --hard HEAD~1
```

After reset:

```text
Commit B  <-- HEAD
Commit A
```

The changes introduced in Commit C are removed from the working directory.

**Important Warning:**

`git reset --hard` can permanently discard uncommitted changes and should be used carefully.

Before executing this command, make sure you do not need the changes you are about to discard.

**When to use it?**

- When you want to completely discard the latest commit's changes from your current working state.
- When you want to return your tracked files to an earlier commit.

-----------------------------------------------------------------------------------------------------------

## 7. Recovering References Using `git reflog`

### What is `git reflog`?

The `git reflog` command displays the history of changes to HEAD and other local references.

It is especially useful when you accidentally reset a commit and want to find its previous Commit ID.

### Command

```bash
git reflog
```

### Example Output

```text
a1b2c3d HEAD@{0}: reset: moving to HEAD~1
e4f5g6h HEAD@{1}: commit: Added login functionality
i7j8k9l HEAD@{2}: commit: Initial commit
```

Here:
- `HEAD@{0}` represents the latest reference update.
- `HEAD@{1}` represents the previous reference update.
- `HEAD@{2}` represents an earlier reference update.

### How to Recover a Previous Commit?

Suppose you accidentally executed:

```bash
git reset --hard HEAD~1
```

And you want to recover the previous commit.

**Step 1: Check the reflog**

```bash
git reflog
```

**Step 2: Identify the Commit ID**

Find the Commit ID of the commit you want to recover.

**Step 3: Create a recovery branch**

```bash
git switch -c recovery-branch <commit-id>
```

This creates a new branch pointing to the selected commit, allowing you to access the recovered commit without immediately changing your current branch.

**Note:** Reflog entries are local and expire over time. They are not a permanent backup. Recovery is not guaranteed if Git has already pruned the relevant objects.

-------------------------------------------------------------------------------
