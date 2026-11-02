
# Session 2: Git Basics — Tracking, Staging, and Commits

## 1. Checking Whether Git Is Installed

### What is Git?

Git is a distributed version control system used to track changes in source code.

It helps developers to:
- Track changes made to files.
- Maintain different versions of a project.
- Collaborate with other developers.
- Restore previous versions of files.
- Manage code history.

### Check Git Installation

To check whether Git is installed on your system, open the terminal or command prompt and execute:

```bash
git --version
```

**Example Output:**

```text
git version 2.x.x
```

If Git is installed, the above command displays the installed version.

If Git is not installed, download and install it from:

https://git-scm.com/

---

## 2. Understanding the `.git` Folder

### What is the `.git` Folder?

The `.git` folder is a hidden directory created inside a repository when Git is initialized.

It stores all the information required by Git to track and manage changes in the project.

It contains:
- Commit history.
- Repository configuration.
- Branch information.
- Staging information.
- References to commits.

### How to Create a `.git` Folder?

Navigate to your project directory and execute:

```bash
git init
```

**Example Output:**

```text
Initialized empty Git repository
```

This command initializes Git in the current directory and creates the `.git` folder.

### How to View the `.git` Folder?

On Linux/macOS:

```bash
ls -a
```

On Windows Command Prompt:

```cmd
dir /a
```

**Note:** Do not manually delete or modify the `.git` folder. It contains important repository information.

---

## 3. Checking File Status Using `git status`

### What is `git status`?

The `git status` command displays the current state of files in the Git repository.

It helps us identify:
- New files that are not tracked.
- Modified files.
- Files staged for commit.
- Files that are not yet committed.

### Command

```bash
git status
```

### Example

Suppose you create a new file called `index.html`.

Execute:

```bash
git status
```

Git displays the new file under:

```text
Untracked files
```

**Note:** Run `git status` frequently to understand the current state of your repository.

---

## 4. Tracking and Staging Files Using `git add`

### What is Staging?

Staging is the process of selecting changes that should be included in the next commit.

Git uses a staging area (also called the Index) to prepare changes before committing them.

### What is `git add`?

The `git add` command moves new or modified file changes into the staging area.

### Common Commands

**1. Add a specific file:**

```bash
git add index.html
```

**2. Add multiple files:**

```bash
git add index.html style.css
```

**3. Add all changes in the current directory:**

```bash
git add .
```

### Verify Staged Files

After executing `git add`, run:

```bash
git status
```

The staged files will appear under:

```text
Changes to be committed
```

**Note:** `git add` does not create a commit. It only prepares changes for the next commit.

---

## 5. Committing Changes Using `git commit`

### What is a Commit?

A commit is a snapshot of the staged changes in your Git repository.

It records the changes along with a commit message.

### What is `git commit`?

The `git commit` command saves the staged changes into the repository history.

### Command

```bash
git commit -m "Initial commit"
```

Here:
- `git commit` creates a commit.
- `-m` is used to provide a commit message.
- `"Initial commit"` describes the changes.

### Example

```bash
git add .
git commit -m "Added initial project files"
```

**Good Commit Message Examples:**

```text
Initial commit
Added login page
Updated README file
Fixed header styling
Added user registration functionality
```

**Note:** Always write meaningful commit messages so that changes can be easily understood later.

---

## 6. Reviewing Changes Using `git diff`

### What is `git diff`?

The `git diff` command is used to compare changes made to files.

It helps developers understand what has changed before committing.

### Common Commands

**1. View unstaged changes:**

```bash
git diff
```

Displays changes made to tracked files that are not yet staged.

**2. View staged changes:**

```bash
git diff --staged
```

Displays changes that have been added to the staging area.

**3. Compare two commits:**

```bash
git diff commit1 commit2
```

Displays the differences between two commits.

### Understanding the Output

Git uses the following symbols:

| Symbol | Meaning |
|---|---|
| `+` | Added lines |
| `-` | Removed lines |

**Example:**

```diff
- Welcome to Git
+ Welcome to Bitbucket and Git
```

This indicates that the old line was replaced with a new line.

---

## 7. Understanding the Git Workflow

The basic Git workflow consists of three important steps:

1. Working Directory – Create or modify files.
2. Staging Area – Select changes using `git add`.
3. Repository – Save changes using `git commit`.

### Basic Git Workflow

```text
Working Directory
       |
       | git add
       v
  Staging Area
       |
       | git commit
       v
 Git Repository
```

### Complete Example

```bash
# Initialize Git repository
git init

# Check repository status
git status

# Create or modify project files

# Stage all changes
git add .

# Review staged changes
git diff --staged

# Commit changes
git commit -m "Initial commit"

# Check repository status again
git status
```

-----------------------------------------------------------

