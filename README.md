# GitHub basics: a beginner's guide

This guide shows how to create a GitHub repository and use it from Windows
PowerShell. Git is the program that records changes on your computer; GitHub
hosts Git repositories online so you can back them up and work with others.

## 1. Create a GitHub account

1. Visit [github.com](https://github.com/) and sign up.
2. Verify your email address.
3. Sign in and create a new repository using the **+** menu, then **New
   repository**.
4. Give it a short name, such as `learning-github`.
5. Choose **Public** if anyone may view it, or **Private** if access should be
   restricted.
6. For a new project, select **Add a README file**, then click **Create
   repository**.

The repository page shows the files and provides the repository's URL. Do not
put passwords, API keys, or other secrets in a repository.

## 2. Install Git and set your name

Install Git for Windows from [git-scm.com/download/win](https://git-scm.com/download/win).
Open PowerShell and check that it is installed:

```powershell
git --version
```

Set the name and email that Git will attach to your future commits. Use the
email associated with your GitHub account, or your GitHub-provided private
email if you do not want your personal email shown publicly:

```powershell
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

These settings identify commits; they do not sign you in to GitHub.

## 3. Copy the repository to your computer

On the repository page, click **Code**, copy the HTTPS URL, then run the
following in PowerShell. Replace the sample URL with the one you copied:

```powershell
cd $HOME
git clone https://github.com/YOUR-USERNAME/learning-github.git
cd learning-github
```

`clone` downloads the repository. You only need to clone it once on each
computer. If Git asks you to authenticate, follow the browser sign-in prompt.
GitHub does not accept your account password for Git operations. Never paste a
token or password into a chat or save it in a project file.

## 4. Make and save a change

Edit or add a file inside the repository folder. For example, open `README.md`
in a text editor and add a sentence. Then check what changed:

```powershell
git status
git diff
```

Tell Git which changes to include, and save them as a commit:

```powershell
git add README.md
git commit -m "Update project README"
```

A **commit** is a named snapshot of your changes. Use a short message that
describes the change. To stage all changed files instead, use `git add .`;
check `git status` first so you do not include files you did not intend to
share.

## 5. Upload your commit to GitHub

Send your local commits to GitHub:

```powershell
git push
```

Refresh the repository page to see the uploaded changes. The first time you
push a new branch, Git may show a command to set its upstream; run the command
Git provides.

## 6. Get the latest changes

Before starting work, or when someone else has updated the repository, get
their latest changes:

```powershell
git pull
```

If Git reports a conflict, it needs you to choose how to combine edits to the
same part of a file. Open the listed files, resolve the conflict markers, save
the files, then stage and commit the resolved changes as Git instructs.

## 7. Use a branch and open a pull request

A **branch** lets you work on a change separately from the main project.
A **pull request (PR)** is a request to review and merge that change.

```powershell
git switch -c add-project-notes
# Edit files, then:
git add .
git commit -m "Add project notes"
git push -u origin add-project-notes
```

On GitHub, open the repository page and click **Compare & pull request**. Add
a title and a short description, then create the pull request. After review,
choose **Merge pull request** if you have permission and the project is ready
to merge. Once merged, return to the main branch and update it:

```powershell
git switch main
git pull
```

## A simple daily routine

1. `git pull` to get recent work.
2. Edit files.
3. `git status` and `git diff` to review your changes.
4. `git add` and `git commit` to save a snapshot.
5. `git push` to upload it.

## Useful commands

```powershell
git status                 # Show changed files and current branch
git log --oneline          # Show recent commits
git branch                 # List local branches
git switch main            # Switch to the main branch
```

If a command fails, read the full error message before retrying. In particular,
do not force-push or delete branches to try to fix a problem unless you
understand the effect.
