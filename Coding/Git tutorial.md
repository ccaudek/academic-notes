---
modificationDate: 2024-11-09
tags:
  - git
---
## Git workflow

- **Step 1:** create an empty GitHub repository (for example `my_project`).
- **Step 2:** clone locally the Github repository in the appropriate directory.

    ```bash
    cd _repositories
    git clone https://github.com/ccaudek/my_project.git
    ```

- **Step 3:** make changes locally and push your changes to the remote.

    ```bash
    cd my_project
    git add -A
    git commit -m "update something"
    git push
    ```

## git init

`git init` turns any directory into a Git repository.

```bash
git init
```

To initialize a repository, Git creates a hidden directory called `.git`. That directory stores all of the objects and refs that Git uses and creates as a part of your project's history. This hidden `.git` directory is what separates a regular directory from a Git repository.

> [!info] `git init` gone wrong
Running `git init` in the wrong place will create unintended repositories. To fix this, you first need to track down which directory is the unintended repository. Once you find the `.git` directory, and you are sure that you don't want that to be a Git repository, use `rm -rf .git`. This will remove the `.git` directory, effectively un-initializing that repository. Run `git status` to confirm that Git is no longer tracking any of these files. (It could be possible that multiple layers of `.git` directories are present.)

## Git add

The `git add` command adds new or changed files in your working directory to the Git staging area. In the example I add the single file README.md to the staging area.

```bash
git add README.md
```

Alternatively, I can stage all available files.

```bash
git add -A
```

`git add -A`: stages all files, including new, modified, and deleted files, including files in the current directory *and* in higher directories that still belong to the same git repository.

## Git commit

`git commit` creates a commit, which is like a snapshot of your repository. You should make new commits often, based around logical units of change. Commits include lots of metadata in addition to the contents and message, like the author, timestamp, and more.

```bash
git commit -m "update the README.md with link to contributing guide"
```

## Git push

`git push` uploads all local branch commits to the corresponding remote branch.

The first time we want to push, we use

```bash
git push -u origin main
```

Useful when pushing a new branch, this creates an upstream tracking branch with a lasting relationship to your local branch.

If the push is too large, a simple solution is to increase the HTTP post buffer size to allow for larger chunks to be pushed up to the remote repo. To do that, simply type:

```bash
git config http.postBuffer 52428800
```

The number is in bytes, so in this case I have set it to 50MB. The default is 1MB.

After the first time, it is sufficient to do `git push` .

```bash
git push
```

> [!help]
Se viene richiesta la password, **inserire la password del Mac**.

## Git pull

`git pull` updates your current local working branch, and all of the remote tracking branches. It's a good idea to run `git pull` regularly on the branches you are working on locally. Without `git pull`, your local branch wouldn't have any of the updates that are present on the remote.

```bash
git pull
```

> [!tip]
It's a good idea to run `git pull` regularly on the branches you are working on locally. `git pull` is the most common way to update your repository.

### Git reset

To pull changes from a remote repository while *disregarding any local changes* in a Git repository, you can use the following commands:

```bash
git reset --hard HEAD 
git pull
```

This method is straightforward but destructive, as it removes all local changes without the possibility of recovery. This will discard all local changes (both staged and working directory changes).

## Show the current state of your Git working directory

`git status` shows the current state of your Git working directory and staging area.

```bash
git status
```

> [!tip]
When in doubt, run `git status`. This is *always* a good idea.
The `git status` command only outputs information, it won't modify commits or changes in your local repository. During merge conflicts, `git status` will also tell you exactly which files are the source of the conflict.

## Quick backup

> [!Warning]
Remember `git pull` before adding anything to git!!

```bash
git status
git add -A
git commit -m "updated something"
git push
```

## How to force `git pull`

> [!Warning] This will overwrite all local files changes!

```bash
git reset --hard HEAD
git pull
```

## Force pull to overwrite local files

From this [link](https://www.git-tower.com/learn/git/faq/git-force-pull).

Step 1: cleaning up the working copy

a) Saving local changes on a Stash

```bash
git stash --include-untracked
```

b) Discard local changes

```bash
git reset --hard
git clean -fd
```

Step 2: Pull again

```bash
git pull
```

When it does not work, reconcile divergent branches with the following:

```bash
git config pull.rebase true
```

## How to force push

If you want to keep your local changes and discard the changes on GitHub (and other remote repositories), you can follow these steps:

To discard the changes on GitHub and other remote repositories, you can use the `git push --force` command. This will forcefully push your local changes and overwrite the remote repository.

```bash
git push --force origin main
```

Please note that using `git push --force` can potentially cause data loss on the remote repository if other collaborators have made changes that you are discarding. Make sure you communicate with your team and understand the consequences before using this command.

## Adding wiki pages

Notes on adding a wiki page to a repository and use git: [[add_wiki_pages]].

## Branching

A discussion on branching: [[git_branch]].

## gitignore

A [[gitignore]] file specifies intentionally untracked files that Git should ignore.

## Obsidian Git

Notes on Obsidian Git can be found here: [[obsidian_git]]

## Access on GitHub

Notes on the access on GitHub can be found here: [[GitHub instructions]]

## Cleaning up a git repo

Some considerations about reducing the repository size can be found following this [link](https://medium.com/@sangeethkumar.tvm.kpm/cleaning-up-a-git-repo-for-reducing-the-repository-size-d11fa496ba48).

