
# Session 1: Bitbucket Introduction and Setup

## 1. Introduction to Bitbucket

### What is Bitbucket?

Bitbucket is a Git-based code hosting and version control platform developed by Atlassian.

It helps developers to:
- Store and manage source code.
- Track code changes using Git.
- Collaborate with team members.
- Manage different versions of a project.
- Review code using Pull Requests.

### Why do we use Bitbucket?

- To maintain code in a central location.
- To track changes made by developers.
- To collaborate with team members.
- To maintain project history.

**Official Website:** https://bitbucket.org/

------------------------------------------------------------------------

## 2. Creating a Bitbucket Account

To get started with Bitbucket:

1. Visit https://bitbucket.org/
2. Click **Get it free** or Sign up.
3. Create an account using your email address or Atlassian account.
4. Complete the registration process.
5. Log in to Bitbucket.

Once logged in, you can create workspaces and repositories.

------------------------------------------------------------------------------------------

## 3. Exploring the Bitbucket UI

After logging in, explore the Bitbucket dashboard.

Some important sections are:

| Section | Description |
|---|---|
| Workspaces | Manage repositories and collaborate with teams. |
| Projects | Group related repositories together. |
| Repositories | Store and manage source code. |
| Pull Requests | Review and merge code changes. |
| Branches | Work on different versions of code. |
| Settings | Manage repository and workspace configurations. |

---------------------------------------------------------------------------------------------------

## 4. Understanding Workspaces, Projects, and Repositories

Bitbucket organizes code using three important concepts.

### Workspace

- A workspace is the top-level container in Bitbucket.
- It helps teams organize and manage their repositories.
- A workspace can contain multiple projects.

### Project

- A project is used to group related repositories.
- It helps organize repositories based on applications or modules.

### Repository

- A repository is where the project's source code is stored.
- It maintains code history and tracks changes using Git.

### Example

```text
Workspace: my-company
    |
    |--- Project: E-Commerce
    |       |
    |       |--- Repository: frontend
    |       |--- Repository: backend
    |
    |--- Project: Banking
            |
            |--- Repository: payment-service
            |--- Repository: user-service
```

---------------------------------------------------------------------------

## 5. Creating a Repository

Follow these steps to create a new repository:

1. Log in to your Bitbucket account.
2. Navigate to your workspace.
3. Click **Create** and select **Repository**.
4. Enter the repository name.
5. Select the repository access level:
   - **Private:** Only authorized users can access the repository.
   - **Public:** Anyone can view the repository.
6. Select Git as the version control system.
7. Click **Create repository**.

Your repository is now ready!

--------------------------------------------------------------------------------------------------------

## 6. Understanding Repository Clone URLs

### What is a Clone URL?

A Clone URL is the web address used to copy a remote repository from Bitbucket to your local machine.

It allows developers to work on the project locally.

Bitbucket generally provides two types of clone URLs:

### 1. HTTPS

```bash
git clone https://bitbucket.org/workspace-name/repository-name.git
```

### 2. SSH

```bash
git clone git@bitbucket.org:workspace-name/repository-name.git
```

### Difference between HTTPS and SSH

| HTTPS | SSH |
|---|---|
| Uses HTTPS authentication. | Uses SSH key-based authentication. |
| May require authentication or an app password/access token, depending on the setup. | Requires SSH key configuration. |
| Easy to get started. | Convenient for regular development. |

-----------------------------------------------------------------------------------------------------------------
