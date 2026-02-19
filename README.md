# Credit: Trainwithshubham

# GitHub CLI (`gh`) - Comprehensive Guide

## Introduction
GitHub CLI, commonly known as `gh`, is an official command-line tool that brings GitHub's features directly to your terminal. It allows developers to interact with repositories, issues, and pull requests without needing to switch to a web browser, significantly streamlining development workflows. 

Built and maintained by GitHub, the tool is cross-platform and works seamlessly on Linux, macOS, and Windows.

## Core Capabilities
With GitHub CLI, you can perform a wide range of tasks directly from the command line:
* Create and manage repositories.
* Handle issues and pull requests.
* Fork and clone repositories.
* View repository details and status.
* Extend functionality through community-built extensions.

---

## Installation

### Linux (Ubuntu/Debian)
To install GitHub CLI on Ubuntu or Debian-based systems, run:
```bash
sudo apt update 
sudo apt install gh -y
```

### macOS
On macOS, you can use Homebrew:
```bash
brew install gh
```

### Windows
For Windows users, installation is available via WinGet:
```powershell
winget install GitHub.cli
```

### Verifying Installation
To ensure the CLI is installed correctly, check the version:
```bash
gh --version
```

---

## Authentication
Authentication is required to interact with your GitHub account.

### Login
Execute the following command to start the interactive authentication process:
```bash
gh auth login
```
During the process, you will be prompted to choose:
* The account type (GitHub.com or GitHub Enterprise).
* Preferred protocol (HTTPS or SSH).
* Authentication method (Web browser or personal access token).

> **Note:** HTTPS is recommended for simplicity, while SSH is ideal if you already have SSH keys configured.

### Authentication Status
To verify your current login status, use:
```bash
gh auth status
```

---

## Repository Management

### Create a New Repository
To create a new repository interactively:
```bash
gh repo create
```
To create a repository non-interactively and push local code:
```bash
gh repo create my-repo --public --source=. --remote=origin --push
```

### Clone a Repository
To clone a repository to your local machine:
```bash
gh repo clone username/repository
```

### Fork a Repository
To fork a repository:
```bash
gh repo fork username/repository
```
To fork and clone simultaneously:
```bash
gh repo fork username/repository --clone
```

### View Repository Info
To view information about the current repository:
```bash
gh repo view
```
To open the repository page in your default browser:
```bash
gh repo view --web
```

---

## Issue Management

### Create an Issue
To start an interactive issue creation process:
```bash
gh issue create
```
To create an issue quickly with a title and body:
```bash
gh issue create --title "Bug in login" --body "Login fails on invalid token"
```

### List and View Issues
List open issues:
```bash
gh issue list
```
Filter issues by state:
```bash
gh issue list --state open
```
View a specific issue by its number:
```bash
gh issue view 12
```
Use the `--web` flag to open the issue in your default browser:
```bash
gh issue view 12 --web
```

### Close an Issue
Once an issue is resolved, close it using its number:
```bash
gh issue close 12
```

---

## Pull Request Management

### Create a Pull Request
To create a pull request interactively:
```bash
gh pr create
```
To create a pull request quickly via flags:
```bash
gh pr create --base main --head feature-branch --title "Add login feature" --body "Implemented login logic"
```

### Manage Pull Requests
List active pull requests:
```bash
gh pr list
```

### View and Checkout Pull Requests
View a specific pull request:
```bash
gh pr view 5
```
View a pull request with its comments and status checks:
```bash
gh pr view 5 --comments
```
Checkout a pull request locally for testing:
```bash
gh pr checkout 5
```

### Merge a Pull Request
To merge a pull request interactively:
```bash
gh pr merge 5
```
You can also specify a specific merge method:
```bash
gh pr merge 5 --merge
gh pr merge 5 --squash
gh pr merge 5 --rebase
```

### Pull Request Status
To see a summary of pull requests relevant to you:
```bash
gh pr status
```

---

## Extensions
GitHub CLI can be extended with additional commands developed by the community. You can browse available extensions [here](https://github.com/topics/gh-extension).

### Managing Extensions
* **Install an Extension:**
    ```bash
    gh extension install owner/extension-name
    ```
* **List Installed Extensions:**
    ```bash
    gh extension list
    ```
* **Uninstall an Extension:**
    ```bash
    gh extension remove owner/extension-name
    ```

### Example: Notification Extension
```bash
# Install
gh extension install meiji163/gh-notify

# Run
gh notify -s

# Uninstall
gh extension remove meiji163/gh-notify
```

---

## Performance Tips and Best Practices

### Useful Commands
* `gh status`: Provides a quick overview of your work in the current repository.
* `gh help`: Accesses the built-in documentation for any command.
* `--web`: Most commands support this flag to transition to the browser when visual detail is needed.

### Core Recommendations
* Always ensure you are authenticated before running commands.
* Run commands from within the local git repository to allow `gh` to automatically detect context.
* Use extensions to automate repetitive tasks specific to your workflow.

### Custom Aliases
You can create custom shortcuts for frequently used commands. For example, to alias `repo list` to `rl`:
```bash
gh alias set rl "repo list"
```
Now, instead of `gh repo list`, you can simply run:
```bash
gh rl
```

---

## Limitations
While GitHub CLI is powerful, certain tasks are still better suited for the web interface:
* Large-scale visual code reviews.
* Managing complex organizational settings.
* Users who are entirely new to GitHub and prefer a purely graphical interface.
