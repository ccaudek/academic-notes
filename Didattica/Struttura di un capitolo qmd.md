---
type: Zettel
title: Struttura di un capitolo .qmd
description: null
modificationDate: 2025-08-31 09:07
tags: []
coverImage: null
---

Questa è la struttura di un capitolo `.qmd` che utilizzo per il book Quarto di Psicometria:

```shell
# Il ciclo di vita di un progetto di analisi dei dati {#sec-eda-proj-structure}

::: {.epigraph}
> “Se la tua analisi non è riproducibile, non è scienza.”
>
> -- **Gary King**, Professore di Scienze Sociali e Statistica, Università di Harvard
:::

## Introduzione {.unnumbered .unlisted}

<p class="capo">
  <span class="capo-initial" data-bg="1">L'</span>
  inferenza bayesiana ...
</p>

### Panoramica del capitolo {.unnumbered .unlisted}

- Pianificazione iniziale.
- Come configurare l’ambiente R.

::: {.callout-tip collapse=true}
## Prerequisiti
- Leggere [Veridical Data Science](https://vdsbook.com) [@yu2024veridical] focalizzandoti sul primo capitolo.
:::

::: {.callout-caution collapse=true title="Preparazione del Notebook"}

```{r}
# Carica il file _common.R per impostazioni di pacchetti e opzioni
here::here("code", "_common.R") |> 
  source()
```
:::

Titolo di una classe ornamentale dedicata:

<span class="sottopasso">1. Impostare obiettivo predefinito<span>

## Riflessioni conclusive {.unnumbered .unlisted}

La riproducibilità computazionale rappresenta ...

::: {.callout-note collapse=true title="Informazioni sull'ambiente di sviluppo"}
```{r}
sessionInfo()
```
:::

## Bibliografia {.unnumbered .unlisted}

```


