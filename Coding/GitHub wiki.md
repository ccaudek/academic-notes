---
type: Zettel
title: GitHub wiki
description: null
modificationDate: 2024-11-08 10:26
tags: []
coverImage: null
---

# Adding wiki pages

- On GitHub.com, navigate to the main page of the repository.

- Under your repository name, click  **Wiki**.

    ![Untitled](https://docs.github.com/assets/cb-50195/images/help/wiki/wiki-menu-link.png)
    [Untitled](../Images/Untitled%20(1).md)

- Use the text editor to add your page's content.In the "Edit message" field, type a commit message describing the new file you’re adding.

- To commit your changes to the wiki, click **Save Page**.

- In the upper-right corner of the page, click **New Page**.

## [Cloning wikis to your computer](https://docs.github.com/en/communities/documenting-your-project-with-wikis/adding-or-editing-wiki-pages#cloning-wikis-to-your-computer)

Every wiki provides an easy way to clone its contents down to your computer. Once you've created an initial page on GitHub, you can clone the repository to your computer with the provided URL:

```shell
$ git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.wiki.git
# Clones the wiki locally
```

Once you have cloned the wiki, you can add new files, edit existing ones, and commit your changes. You and your collaborators can create branches when working on wikis, but only changes pushed to the default branch will be made live and available to your readers.

> [!Warning]
The local wiki operates as a distinct Git repository, separate from the main project. To update it, you'll need to first navigate to the wiki's local directory. Once there, you can stage your changes with `git add`, commit them using `git commit`, and finally push them to the remote repository with `git push`.


