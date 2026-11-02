
# Session 6: Bitbucket Pull Requests and Code Reviews

## 1. Understanding Pull Requests

### What is a Pull Request?

A Pull Request (PR) is a request to merge changes from one branch into another branch.

It allows developers to share their code changes with team members for review before merging them into the destination branch.

### Why Do We Use Pull Requests?

- To review code before merging.
- To identify bugs and mistakes.
- To maintain code quality.
- To discuss changes with team members.
- To collaborate with other developers.
- To ensure changes are ready before merging.

### Example

Suppose a developer creates a new feature in a branch called `feature-login`.

After completing the feature, the developer creates a Pull Request to merge it into the `main` branch.

```text
feature-login
      |
      | Pull Request
      v
     main
```

The team can review the changes before approving and merging them.

-----------------------------------------------------------------------------------------------------------

## 2. Creating a Pull Request in Bitbucket

### Steps to Create a Pull Request

1. Log in to your Bitbucket account.
2. Open the required repository.
3. Navigate to the **Pull requests** section.
4. Click **Create pull request**.
5. Select the source branch.
6. Select the destination branch.
7. Enter a meaningful title.
8. Add a description explaining the changes.
9. Add reviewers if required.
10. Click **Create pull request**.

Your Pull Request is now created.

### Example

**Title:**

```text
Added login functionality
```

**Description:**

```text
Implemented the login page.

Changes include:
- Added login form.
- Added username and password fields.
- Updated login page styling.
```

**Note:** A good Pull Request title and description help reviewers understand the purpose of the changes.

------------------------------------------------------------------------------------------------

## 3. Source and Destination Branches

When creating a Pull Request, two important branches must be selected.

### Source Branch

The source branch contains the changes that you want to merge.

Example:

```text
feature-login
```

### Destination Branch

The destination branch is where you want to merge the changes.

Example:

```text
main
```

### Example

Suppose you have two branches:

```text
main
feature-login
```

You have completed the login functionality in `feature-login`.

Now, you want to merge those changes into `main`.

```text
Source Branch:      feature-login

Destination Branch: main
```

### Important

- Source branch = Where the changes are coming from.
- Destination branch = Where the changes are going.

Always verify the source and destination branches before creating a Pull Request.

-----------------------------------------------------------------------------------------------------

## 4. Reviewing Changes and Adding Comments

### What is a Code Review?

A Code Review is the process of examining code changes before they are merged into the target branch.

Reviewers check whether the code follows project standards and works as expected.

### What Do Reviewers Check?

- Code quality and readability.
- Coding standards.
- Potential bugs.
- Duplicate code.
- Unnecessary changes.
- Whether the implementation meets requirements.

### Reviewing Changes in Bitbucket

Follow these steps:

1. Open the Pull Request.
2. Navigate to the **Diff** section.
3. Review the changed files.
4. Check added and removed lines.
5. Identify issues or improvements.
6. Add comments wherever necessary.

### Understanding Diff Changes

Bitbucket highlights code changes using different colors.

| Highlight | Meaning |
|---|---|
| Green | Added lines. |
| Red | Removed lines. |
| Unchanged | Existing lines that were not modified. |

### Adding Comments

Reviewers can add comments to specific lines of code.

Example:

```text
Can we move this validation logic into a separate method
to improve code readability?
```

Comments help developers understand what needs to be improved.

-------------------------------------------------------------------------------------------------------

## 5. Addressing Review Feedback

After reviewing the Pull Request, reviewers may suggest changes.

The developer needs to address the feedback before the changes are approved.

### Steps to Address Review Feedback

1. Open the Pull Request.
2. Read the reviewer's comments.
3. Switch to the source branch locally.
4. Make the requested changes.
5. Stage the changes.
6. Commit the changes.
7. Push the updated changes to Bitbucket.

### Example Commands

Switch to the source branch:

```bash
git switch feature-login
```

Make the requested code changes.

Stage the changes:

```bash
git add .
```

Commit the changes:

```bash
git commit -m "Addressed pull request review comments"
```

Push the changes:

```bash
git push origin feature-login
```

The existing Pull Request will automatically display the updated changes.

**Note:** You do not need to create a new Pull Request. New commits pushed to the same source branch are reflected in the existing Pull Request.

-------------------------------------------------------------------------------------------

## 6. Approving and Merging Pull Requests

Once the reviewer is satisfied with the changes, they can approve the Pull Request.

### What is Pull Request Approval?

Approval indicates that a reviewer has reviewed the changes and considers them ready for merging.

### Steps to Approve a Pull Request

1. Open the Pull Request in Bitbucket.
2. Review all code changes.
3. Check whether feedback has been addressed.
4. Click **Approve**.

The Pull Request will now show the approval status.

### Merging a Pull Request

After the required approvals and other repository checks are completed, the Pull Request can be merged.

Follow these steps:

1. Open the approved Pull Request.
2. Verify the source and destination branches.
3. Check that all required approvals are completed.
4. Click **Merge**.
5. Select the required merge strategy, if prompted.
6. Confirm the merge.

The changes from the source branch will now be integrated into the destination branch.

### Common Merge Strategies

| Strategy | Description |
|---|---|
| Merge commit | Combines branches and creates a merge commit. |
| Squash | Combines multiple commits into a single commit. |
| Fast-forward | Moves the destination branch forward when possible. |

**Note:** Available merge strategies depend on the repository configuration and branch history.

-------------------------------------------------------------------------------

## 7. Difference Between a Pull Request and `git merge`

Both Pull Requests and `git merge` are used to integrate changes from one branch into another, but they serve different purposes.

| Pull Request | `git merge` |
|---|---|
| A collaboration and review process. | A Git command used to combine branches. |
| Usually created through Bitbucket UI. | Executed through the terminal. |
| Supports code reviews and comments. | Does not provide a built-in code review process. |
| Allows reviewers to approve changes. | Does not have an approval workflow by itself. |
| Can include automated checks and branch restrictions. | Depends on the local Git workflow and repository configuration. |
| Used commonly in team development. | Can be used in both individual and team development. |

### Example: Pull Request Workflow

```text
Developer creates feature branch
             |
             v
      Makes code changes
             |
             v
       Pushes to Bitbucket
             |
             v
      Creates Pull Request
             |
             v
        Code Review
             |
             v
      Reviewer Approval
             |
             v
       Merge in Bitbucket
             |
             v
        Updated main
```

### Example: Using `git merge`

```bash
# Switch to the destination branch
git switch main

# Merge the source branch
git merge feature-login
```

This directly merges the changes into the current local branch.

**Important:** A Pull Request is not a Git command. It is a feature provided by platforms like Bitbucket and GitHub to manage code reviews and merging.

--------------------------------------------------------------------------------------
