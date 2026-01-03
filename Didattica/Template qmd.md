---
type: Zettel
title: Template qmd
description: null
modificationDate: 2025-01-25 02:41
tags: [teaching, quarto]
coverImage: null
---

```bash
---
execute:
  freeze: auto
---

# Flusso di lavoro {#sec-data-cleaning}

::: callout-important
## In questo capitolo imparerai a

- verificare, pulire e trasformare i dati 
- applicare regole coerenti per denominazione e codifica
:::

::: callout-tip
## Prerequisiti

- Leggere [Cleaning sample data in standardized way](https://cghlewis.com/blog/data_clean_03/) di Crystal Lewis.
:::

::: callout-caution
## Preparazione del Notebook

```{r}
here::here("code", "_common.R") |> 
  source()

# Load packages
if (!requireNamespace("pacman")) install.packages("pacman")
pacman::p_load(mice, labelled, haven, pointblank)
```
:::

## Informazioni sull'Ambiente di Sviluppo {.unnumbered} 

```{r}
sessionInfo()
```

## Bibliografia {.unnumbered}

```

## Flusso di lavoro con Quarto

Nell'ambiente virtuale `base` **compilo** il progetto con

```bash
quarto preview
```

oppure

```bash
quarto render
```

Poi eseguo `add` , `commit` e `push`:

```bash
git add -A
git commit -m "updated file"
git push
```

Per **aggiornare** GitHub Pages, uso la funzione `ghp-import` nell'ambiente virtuale `myenv`. 

(1) Attivo l'ambiente virtuale:

```bash
source myenv/bin/activate
```

(2) Eseguo:

```bash
ghp-import -n -p -f docs
```

in home:

```text
tree -L 1
.
├── Desktop
├── Documents
├── Downloads
├── Library
├── Movies
├── Music
├── OneDrive - unifi.it -> /Users/corrado/Library/CloudStorage/OneDrive-unifi.it
├── Pictures
├── Public
├── _repositories
└── myenv
```

