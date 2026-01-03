---
type: Zettel
title: Jupyter Book
description: null
modificationDate: 2024-11-15 07:47
tags: [JupyterNotebook]
coverImage: null
---

## Install

To create a **Jupyter Book**, first install `jupyter-book`.

```bash
conda install -c conda-forge jupyter-book
```

Also install the `sphinx-exercise` add-on.

```bash
pip install sphinx-exercise
```

## Jupyter Book GitHub Pages

The easiest way to use GitHub Pages with your built HTML is to use the [https://github.com/davisp/ghp-import](https://github.com/davisp/ghp-import) package. `ghp-import` is a lightweight Python package that makes it easy to push HTML content to a GitHub repository.

`ghp-import` works by copying *all* of the contents of your built book (i.e., the `_build/html` folder) to a branch of your repository called `gh-pages`, and pushes it to GitHub. The `gh-pages` branch will be created and populated automatically for you by `ghp-import`.

A description showing how to publish (host) the Jupyter Book on Github Pages using `ghp-import` is provided [here](https://jupyterbook.org/en/stable/publish/gh-pages.html) and [here](https://jupyterbook.org/en/stable/publish/gh-pages.html#option-2-automatically-push-your-build-files-with-ghp-import).

To use `ghp-import` to host your book online with GitHub Pages follow the steps below:

1. Install `ghp-import`

    ```bash
    pip install ghp-import
    ```

2. From the `master` branch of your book’s root directory (which should contain the `_build/html` folder) call `ghp-import` and point it to your HTML files, like so:

    ```bash
    ghp-import -n -p -f _build/html
    ```

Typically after a few minutes your site should be viewable online at a url such as: `https://<user>.github.io/<myonlinebook>/`.

If not, check your repository settings under **Pages** to ensure that

- the `gh-pages` branch is configured as the build source for GitHub Pages;

- the folder `/(root)` is selected.

The repository settings under **Pages** also shows the url address GitHub is building for you.

## Creare e Aggiornare un Jupyter Book (JB) su GitHub

Descrivo qui la procedura completa. Per pubblicare un Jupyter Book online, il primo passo è creare un repository su GitHub. Dopo averlo creato, è necessario clonarlo sul proprio computer. Ad esempio:

```bash
git clone https://github.com/ccaudek/ds4psy.git
```

Successivamente, si può iniziare a popolare il repository locale.

- Inizia creando un file `.gitignore` per escludere file non necessari.

- Successivamente, copia i file nella cartella locale e procedi con l'aggiunta (add), la conferma (commit) e il caricamento (push) su GitHub. È consigliabile effettuare push incrementali per semplificare il processo, specialmente con file di grandi dimensioni, come immagini. Ad esempio, per aggiungere tutte le immagini che iniziano con la lettera `a`, si può usare:

```bash
git add images/a*
```

Una volta aggiunti tutti i file al repository locale, è possibile generare il Jupyter Book con:

```bash
jupyter-book build .
```

Per aggiornare il Jupyter Book online:

1. Modifica i contenuti nel repository locale.

2. Ricostruisci il libro localmente.

3. Usa `ghp-import -n -p -f _build/html` per caricare i nuovi file HTML sulla branch `gh-pages`.

Dopo aver modificato i file `.ipynb`, esegui la costruzione localmente:

```bash
jb build .
```

e poi

```bash
# backup on GitHub
git add -A
git commit -m "updated something"
git push
# carica i nuovi file HTML costruiti su gh-pages
ghp-import -n -p -f _build/html
```

### Configurazione del file `config.yml`

Il file `.config.yml` contiene la seguente specificazione:

```bash
# Information about where the book exists on the web
repository:
	url: https://github.com/ccaudek/ds4psy # Online location of your book
	path_to_book: docs/ # Optional path to your book, relative to the repository root
branch: main # Which branch of the repository should be used when creating links (optional)
```

Non è chiaro se sia necessario specificare `path_to_book`, ma questa configurazione sembra funzionare.

### GitHub Pages

Nelle impostazioni di GitHub (`Settings/Pages`), sotto **Branch** dovrebbe apparire:

> Your GitHub Pages site is currently being built from the `gh-pages` branch. [Learn more about configuring the publishing source for your site](https://docs.github.com/articles/configuring-a-publishing-source-for-github-pages/).

Inoltre, dal menu `gh-pages`, seleziona `/(root)` come percorso.

## Sito web `Perfezionamento`

Il sito web per il mio intervento nel corso di Perfezionamento è costruito come un **Jupyter Book** (non l'ho ancora trasformato in Quarto).

Per il rendering del JB, usare la directory 

```shell
/Users/corradocaudek/_repositories/perfezionamento/compassion_book
```

Nell'ambiente virtuale `cmdstan_env`, compilo con:

```shell
jb build .
```

Per aggiornare Pages:

```shell
ghp-import -n -p -f _build
```


