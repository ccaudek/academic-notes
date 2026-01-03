---
title: Add a Google Colab Badge
modificationDate: 2024-11-09 05:14
tags:
  - teaching
  - l24
---

To add a Google Colab badge to each Jupyter notebook on your Quarto website, follow these steps:

1. **Add a Badge Link in Markdown**: You can add a link to open the notebook in Google Colab by placing a markdown cell at the top of each notebook.

2. **Set Up the Badge with a Template URL**: The link will point to the notebook’s GitHub URL, allowing users to open it directly in Colab.

Here’s a step-by-step guide:

### Step 1: Add the Badge to Your Notebook

In the first cell of each Jupyter notebook, insert the following markdown:

```markdown
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/your-username/your-repo-name/blob/main/path/to/your-notebook.ipynb)
```

Replace `your-username`, `your-repo-name`, and `path/to/your-notebook.ipynb` with the actual path to the notebook in your GitHub repository.

### Step 2: Structure the URL for Each Notebook

The URL should be structured like this:

```text
https://colab.research.google.com/github/your-username/your-repo-name/blob/main/path/to/your-notebook.ipynb
```

- **your-username**: Your GitHub username.

- **your-repo-name**: The repository where the notebooks are stored.

- **path/to/your-notebook.ipynb**: The file path within the repository to the specific notebook.

### Example

If your notebook is located in `notebooks/example.ipynb` in a GitHub repository named `my-research` under the username `johndoe`, the badge code will look like this:

```markdown
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/johndoe/my-research/blob/main/notebooks/example.ipynb)
```

### Step 3: Compile with Quarto

Once you add the badge to each notebook, compile your project using Quarto, and the badge will appear as a clickable link on the Quarto-generated website. Users can click the badge to open the notebook in Colab, allowing them to interact with it directly.

This approach provides an easy way for readers to work with the notebooks in an interactive Colab environment!

