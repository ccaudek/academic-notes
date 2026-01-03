---
type: Zettel
title: GitHub instructions
description: null
modificationDate: 2024-11-14 22:41
tags: [github]
coverImage: null
---

## Access to GitHub

When you `git clone`, `git fetch`, `git pull`, or `git push` to a remote repository using HTTPS URLs on the command line, Git will ask for your GitHub username and password.

> [!Warning]
When Git prompts you for your password, **enter your personal access token (PAT)**.

> [!info] Instructions for creating a PAT are [here](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).
After creating a [fine-grained personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token), you can use it instead of a password.

> [!tip]
Remember to change the `User permissions` and the `Repository permissions` of the PAT, otherwise it will not work!!

## To speed up the connection

```bash
git config --global protocol.version 2
```

## Git explained

My notes on git are in [[git_tutorial]].

## Autentification

If autentification fails when doing `push` from a local repository and you get this error message:

```bash
fatal: Authentication failed for 'https://github.com/ccaudek/your_repository.git/'
```

run `git push` again. When Git asks for your credentials after running `git push`, do the following:

1. **Username**: Enter your GitHub username.

2. **Password**: Enter the **PAT** instead of your password.

## Add `.DS_Store` to `.gitignore`

To add `.DS_Store` to your `.gitignore` file when working on macOS, follow these steps:

1. **Open your terminal** and navigate to your repository:

    ```bash
    cd /path/to/your/repo
    ```

2. **Edit the** `.gitignore` **file** (if it doesn’t exist, create one):

    ```bash
    nano .gitignore
    ```

    or

    ```bash
    touch .gitignore
    ```

3. **Add** `.DS_Store` **to the** `.gitignore` **file**:

    ```text
    # Ignore macOS system files
    .DS_Store
    ```

4. **Save and close** the file:

    - If using `nano`, press `CTRL + X`, then `Y` to confirm, and `Enter` to save.

5. **Remove any** `.DS_Store` **files already tracked by Git**:

    ```bash
    git rm --cached .DS_Store
    ```

    This command removes `.DS_Store` files from tracking in your repository without deleting them from your system.

6. **Commit the changes**:

    ```bash
    git commit -m "Add .DS_Store to .gitignore"
    ```

From now on, `.DS_Store` files will be ignored by Git, and you won’t have them tracked in your repository.

