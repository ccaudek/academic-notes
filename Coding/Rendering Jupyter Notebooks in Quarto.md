---
title: Rendering Jupyter Notebooks in Quarto
modificationDate: 2025-12-11 16:59
tags:
  - teaching
  - JupyterNotebook
  - quarto
---

## Compilare il sito web localmente

Con questo comando, il sito verrà ricompilato automaticamente ogni volta che modifichi un file `.qmd` o `.ipynb`:

```shell
quarto preview --render all --no-browse
```

Con l'istruzione precedente, Quarto inizierà a monitorare i file di input e rigenererà il sito automaticamente al rilevamento di modifiche. Questo comando rende l'esperienza più interattiva, monitorando le modifiche ai file e aggiornando il sito senza necessità di riavviare manualmente il processo di compilazione.

L'opzione `--no-watch-input` disabilita invece il monitoraggio dei file di input (come `qmd` e  `.ipynb`), quindi Quarto non ricompilerà automaticamente il sito quando questi file vengono modificati.

Per compilare un singolo .qmd file (per esempio, syllabus.qmd), esegui:

```shell
quarto render syllabus.qmd
```

## Pubblicare su GitHub Pages

Il comando `ghp-import` è utilizzato per pubblicare un sito web statico generato con Quarto su GitHub Pages:

```shell
ghp-import -n -p -f docs
```

Opzioni:

1. `-n`:

    - Non aggiunge un file `.nojekyll` al branch.

    - Il file `.nojekyll` viene solitamente aggiunto per evitare che il motore Jekyll di GitHub elabori i file del sito. In questo caso, l'opzione `-n` lo disabilita, il che è utile se il sito utilizza funzionalità compatibili con Jekyll o non ha conflitti con Jekyll.

2. `-p`:

    - Pubblica i cambiamenti direttamente. Dopo aver copiato i file nel branch `gh-pages`, esegue automaticamente un push sul repository remoto.

    - Senza questa opzione, i cambiamenti verrebbero applicati solo localmente e dovresti fare il push manualmente.

3. `-f`:

    - Forza l'aggiornamento dei file nel branch `gh-pages`.

    - Anche se ci sono conflitti o cambiamenti non sincronizzati, questa opzione sovrascrive tutto con i file presenti nella directory `docs`.

4. `docs`:

    - Specifica la directory che contiene il sito statico generato da Quarto. Questa directory viene caricata nel branch `gh-pages`.

## Link

[Markdown syntax in Quarto](./Markdown%20syntax%20in%20Quarto.md)

