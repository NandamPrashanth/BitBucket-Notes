
# Session 4: Removing Files and Undoing Changes

## 1. Removing Files Using `git rm`

### What is `git rm`?

The `git rm` command is used to remove files from the Git repository and the working directory.

It stages the file deletion so that it can be included in the next commit.

### Common Commands

**1. Remove a specific file:**

```bash
git rm index.html
```

**2. Remove multiple files:**

```bash
git rm index.html style.css
```

**3. Remove a file from Git tracking but keep it locally:**

```bash
git rm --cached config.txt
```

### Example

Suppose you have the following files:

```text
project/
    index.html
    style.css
    README.md
```

Execute:

```bash
git rm index.html
```

The `index.html` file will be removed from the working directory and its deletion will be staged.

Check the status:

```bash
git status
```

You will see the deleted file under:

```text
Changes to be committed
```

**Note:** The deletion becomes part of the repository history only after committing it.

---

## 2. Restoring Files Using `git restore`

### What is `git restore`?

The `git restore` command is used to discard unwanted changes in files and restore them to a previous state.

It is commonly used when you accidentally modify a file and want to undo those changes.

### Command

```bash
git restore filename
```

### Example

Suppose you have a file called `index.html`.

You modify its content accidentally and want to discard the changes.

Execute:

```bash
git restore index.html
```

Git restores the file to its previously staged or committed version.

### When to use it?

- When you accidentally modify a file.
- When you want to discard unwanted changes.
- When you want to restore a file to its previous state.

**Important:** `git restore` can permanently discard uncommitted changes in the specified file.

---------------------------------------------------------------------------------------------

## 3. Unstaging Changes Using `git restore --staged`

### What is Unstaging?

Unstaging means removing changes from the staging area without deleting those changes from the working directory.

### Command

```bash
git restore --staged filename
```

### Example

Suppose you modify a file and stage it using:

```bash
git add index.html
```

Now, you realize that you don't want to include this file in the next commit.

Execute:

```bash
git restore --staged index.html
```

The file will be removed from the staging area, but your modifications will remain in the working directory.

Check the status:

```bash
git status
```

The file will now appear under:

```text
Changes not staged for commit
```

### Unstage All Staged Changes

```bash
git restore --staged .
```

This removes all staged changes from the staging area without discarding the actual file modifications.

**Note:** Unstaging changes does not delete or discard your modifications.

------------------------------------------------------------------------------------------

## 4. Understanding `git revert`

### What is `git revert`?

The `git revert` command is used to undo the changes introduced by a previous commit.

Instead of deleting the existing commit, Git creates a new commit that reverses those changes.

### Why do we use `git revert`?

- To undo unwanted commits.
- To safely reverse changes in shared repositories.
- To maintain the complete commit history.
- To correct mistakes without rewriting existing history.

### Command

```bash
git revert <commit-id>
```

Here, `<commit-id>` represents the commit that you want to revert.

**Note:** Git may open a text editor to confirm the revert commit message. Save and close the editor to complete the revert.

------------------------------------------------------------------------------------

## 5. Reverting a Commit

### Example

Suppose your repository has the following commit history:

```text
Commit C - Added payment functionality
Commit B - Added login functionality
Commit A - Initial commit
```

Now, you realize that Commit B introduced an issue.

You can revert Commit B using:

```bash
git revert <commit-id-of-B>
```

Git creates a new commit that reverses the changes introduced by Commit B.

### Updated Commit History

```text
Commit D - Revert "Added login functionality"
Commit C - Added payment functionality
Commit B - Added login functionality
Commit A - Initial commit
```

Notice that Commit B still exists in the history.

Git creates a new commit (Commit D) to reverse its changes.

### Reverting Without Opening an Editor

```bash
git revert --no-edit <commit-id>
```

This uses the default revert commit message without opening the editor.

**Important:** If the changes introduced by the original commit conflict with later changes, Git may require you to resolve conflicts before completing the revert.

--------------------------------------------------------------------------------------------------------

## 6. Difference Between `git reset` and `git revert`

Both commands are used to undo changes, but they work differently.

| git reset | git revert |
|---|---|
| Moves the current branch reference to an earlier commit. | Creates a new commit to reverse previous changes. |
| Can rewrite commit history. | Preserves existing commit history. |
| Commonly used for local commits. | Commonly used for shared commits. |
| Supports `--soft`, `--mixed`, and `--hard`. | Creates a new commit that reverses changes. |
| Can discard uncommitted changes with `--hard`. | Does not normally discard unrelated uncommitted changes. |

### Example: git reset

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

The current branch moves back to Commit B.

### Example: git revert

Before revert:

```text
Commit C  <-- HEAD
Commit B
Commit A
```

Execute:

```bash
git revert <commit-id-of-B>
```

After revert:

```text
Commit D  <-- HEAD (Revert B)
Commit C
Commit B
Commit A
```

A new commit is created to reverse the changes introduced by Commit B.

### Which One Should We Use?

- **Use `git reset`** when you want to move your local branch back to an earlier commit and understand the impact on your changes.
- **Use `git revert`** when you want to undo a commit while preserving the existing commit history, especially in shared branches.

**Note:** Be careful when using `git reset --hard`, especially when you have important uncommitted changes.

-------------------------------------------------------------------------------------
