---
title: Install cmdstanpy
modificationDate: 2024-11-08 08:20
tags:
  - teaching
  - l24
  - cmdstan
  - cmdstanpy
  - python
---
## Reinstall Anaconda

After updating the Operating System, it is necessary **to reinstall Anaconda**. Otherwise `cmdstan` will not work!

- Find the directory where Anaconda is installed:

```bash
conda info
```

- Remove entire directory:

```bash
sudo rm -rf /opt/anaconda3
```

- With the installer from anaconda.org, install Anaconda. 

    - Update Anaconda if requested from Anaconda Navigator Updater.

## Create virtual environment

To install `cmdstanpy`, create a virtual environment and install the following packages:

```bash
# Crea un nuovo ambiente con cmdstanpy
conda create -n cmdstan_env -c conda-forge cmdstanpy
# Attiva l'ambiente
conda activate cmdstan_env
# Installa i pacchetti necessari tramite conda
conda install -c conda-forge jax numpyro bambi arviz seaborn jupyter-book sphinx-exercise ghp-import ipywidgets watermark pingouin networkx -y
# Installa i pacchetti mancanti con pip
pip install sphinx-proof
```

