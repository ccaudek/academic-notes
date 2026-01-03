---
modificationDate: 2024-11-14 22:41
tags:
  - git
  - github
---
## Introduction

A gitignore file specifies intentionally untracked files that Git should ignore.

Git sees every file in your working copy as one of three things:

1. tracked - a file which has been previously staged or committed;

2. untracked - a file which *has not* been staged or committed; or

3. ignored - a file which Git has been explicitly told to ignore.

Ignored files are usually build artifacts and machine generated files that should not be committed:

- the contents of `/packages`

- compiled code, such as `.o`, `.pyc`, and `.class` files

- build output directories, such as `/bin`, `/out`, or `/target`

- files generated at runtime, such as `.log`, `.lock`, or `.tmp`

- hidden system files, such as `.DS_Store` or `Thumbs.db`

Ignored files are tracked in a special file named `.gitignore` that is checked in at the root of your repository.

A `.gitignore` file is a plain text file where each line contains a pattern for files/directories to ignore. Each line in a `gitignore` file specifies a pattern. The `.gitignore` file must be edited and committed by hand when you have new files that you wish to ignore.

The GitHub guide can be found [here](https://github.com/git-guides/git-status).

`.gitignore` uses [globbing patterns](http://linux.die.net/man/7/glob) to match against file names. You can construct your patterns using various symbols, as explained [here](https://www.atlassian.com/git/tutorials/saving-changes/gitignore).

In addition to these characters, you can use # to include comments in your `.gitignore` file:

```bash
# ignore all logs
*.log
```

You can use \ to escape `.gitignore` pattern characters if you have files or directories containing them:

```bash
# ignore the file literally named foo[01].txt
foo\[01\].txt
```

## Personal Git ignore rules

You can also define personal ignore patterns for a particular repository in a special file at `.git/info/exclude`. These are not versioned, and not distributed with your repository, so it's an appropriate place to include patterns that will likely only benefit you. For example if you have a custom logging setup, or special development tools that produce files in your repository's working directory, you could consider adding them to `.git/info/exclude`to prevent them from being accidentally committed to your repository.

## Literal File Names

The easiest pattern is a literal file name, for example:

```bash
.DS_Store
```

This will ignore any files named `.DS_Store`, which is a common file on macOS.

## Directories

You can ignore entire directories, just by including their paths and putting a `/` on the end:

```bash
node_modules/
logs/
```

If you leave the slash off of the end, it will match both files and directories with that name.

## Wildcard

The `*` matches 0 or more characters (except the `/`). So, for example, `*.log`matches any file ending with the `.log` extension.

Another example is `*~`, which matches any file ending with `~`, such as `index.html~`

You can also use the `?`, which matches any one character except for the `/`. 

## Negation

You can use a prefix of `!` to negate a file that would be ignored.

```bash
*.log
!example.log
```

In this example, `example.log` is not ignored, even though all other files ending with `.log` are ignored.

But be aware, you can't negate a file inside of an ignored directory:

```bash
logs/
!logs/example.log
```

Due to performance reasons, git will still ignore `logs/example.log` here because the entire `logs` directory is ignored.

## Double Asterisk

`**` can be used to match any number of directories.

- `**/logs` matches all files or directories named logs (same as the pattern `logs`)

- `**/logs/*.log` matches all files ending with `.log` in a logs directory

- `logs/**/*.log` matches all files ending with `.log` in the logs directory and any of its subdirectories

`**` can also be used to match all files inside of a directory, so for example `logs/**` matches all files inside of logs.

### Esamples

```bash
sites/*/settings*.php
sites/*/files
sites/*/private
```

### Comments

Any lines that start with `#` are comments:

```bash
# macOS Files
.DS_Store
```

## What If I Already Have It Checked In?

Git will not ignore the file if you've already committed it. You'll have to untrack the file first, then it will start ignoring it. You can untrack the file with this command:

```bash
git rm --cached FILENAME
```

Move to the project root folder and create a `.gitignore` file by typing

```bash
touch .gitignore
```

## gitignore in Obsidian

My `.gitignore` in Obsidian is the following:

```bash
.DS_Store
.obsidian/workspaces.json
.obsidian/workspace-mobile.json
```

## gitignore in Quarto

```bash
# Quarto
.quarto/
*_files/
# Mac generated file
.DS_Store
# The code directory
code/
# History files
.Rhistory
.Rapp.history
# Session Data files
.RData
# User-specific files
.Ruserdata
# Example code in package build process
*-Ex.R
# Output files from R CMD build
/*.tar.gz
# Output files from R CMD check
/*.Rcheck/
# RStudio files
.Rproj.user/
# produced vignettes
vignettes/*.html
vignettes/*.pdf
# OAuth2 token, see https://github.com/hadley/httr/releases/tag/v0.3
.httr-oauth
# knitr and R markdown default cache directories
*_cache/
/cache/
# Temporary files created by R markdown
*.utf8.md
*.knit.md
# R Environment Variables
.Renviron
/.quarto/
```

