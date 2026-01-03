---
type: Zettel
title: Conda Virtual Environments
description: null
modificationDate: 2024-11-08 10:40
tags: [python, conda]
coverImage: null
---

# Managing virtual environments

## Introduction

Four virtual environment tools can be used: `venv`, `virtualenv`, `pipenv` , `conda`. While `venv` and `virtualenv` use `pip` as their package manager,  `pipenv`  and `conda` can be used for both *managing packages* and *virtual environments*. 

This note is about `conda` and requires that `conda` has been already installed on your machine.

## Using Conda

List virtual environments:

```bash
conda env list
```

Create the `my_env` virtual environment:

```bash
conda create -n my_env
```

Activate the `my_env` virtual environment:

```bash
conda activate my_env
```

To deactivate the active environment:

```bash
conda deactivate
```

A conda environment is a directory that contains a specific collection of Conda packages. To see the locations of your conda environments, use the command:

```bash
conda info -e
```

Install packages in the active virtual environment:

```bash
conda install python  
conda install numpy
```

For example, install `kivy` from `conda-forge`:

```bash
conda install -c conda-forge kivy
```

List packages in the active environment:

```bash
conda list
```

To update a package in the active environment, use:

```bash
conda update package_name
```

## Remove

To remove a package, use:

```bash
conda remove package_name
```

To remove the entire environment, use:

```bash
conda env remove -n my_env
```

## Rename

Get out of the environment.

```bash
conda deactivate
```

Rename using `clone` command.

```bash
conda create --name new_env --clone old_env
```

Remove old environment.

```bash
conda remove --name old_env --all
```

## Generate dependency yaml file

You can write down the contents of an environment using:

```bash
conda env export > environment.yaml
```

and the environment can be re-created with:

```bash
conda env create -f environment.yaml
```

## Packages and Python versions

La versione di python che è attiva nell'ambiente virtuale in uso si ottiene con:

```bash
python --version
```

Per trovare l'ultima versione di un pacchetto su conda-forge, usa

```bash
conda search pymc --channel conda-forge
```

## Update conda

In the `base` virtual environment, update all packages (this will also upgrade `conda`):

```bash
conda update --all
conda list
```

Or else, in the `base` virtual environment, if you only want to upgrade `conda`, use

```bash
conda update conda
```

This latter option is not guaranteed to work. It would be better to use the first one.

## Using pip

If you use a [virtual environment](https://docs.python.org/3/library/venv.html), `pip` will always be the correct `pip` (in the sense of `pip` vs `pip3`).

> [!warning]

# Mixing PyPI and Conda Packages

Be aware that it is usually preferable to use `conda install -n venv_name <package name>` instead of `pip`. The common practice is to only use `pip` in a Conda environment when the package is not available through a Conda repository. Follow the best practices found in the "[Using pip in an environment](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#pip-in-env)" documentation.

## Clone a virtual environment on another machine

You can export your Anaconda environment using:

```python
conda env export > environment.yml
```

Remove or comment the last row of `environment.yml` starting with `prefix:`

```python
# prefix: /Users/corrado/opt/anaconda3/envs/psychopy_env
```

Recreate the virtual environment using:

```python
conda env create -f environment.yml
```

## Further information

You should use virtual environments which allows you to create a certain environment that is separated from that of your machine.

> [!question] Info

- Getting started with [conda](https://conda.io/projects/conda/en/latest/user-guide/getting-started.html)

- These notes taken from this [page](https://python.plainenglish.io/virtual-environments-1d09041771d).

- See also this [link](https://aaltoscicomp.github.io/python-for-scicomp/dependencies/).

- Istruzioni sul managment degli ambienti `conda` sono disponibili nel [link](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-pkgs.html).

