---
type: Zettel
title: Workflow
description: null
modificationDate: 2024-11-14 22:41
tags: [research]
coverImage: null
---

# **Best practices**

**Best practices** per il flusso di lavoro in un progetto di ricerca.

## Archiviazione

- **Progetti in corso:** salvati in un repository GitHub.

- **Progetti conclusi:** archiviati su:

    - OneDrive `archive/<final_project_name>`,

## UUID

Un Universally Unique Identifier (UUID) è assegnato a ciascun progetto:

```r
RcppUUID::uuid_generate_random()
```

L’UUID viene riportato nel README.md file nella cartella del progetto, in ciascuno R-script e Jupyter notebook.

## Cartella di lavoro su ciascun computer

- Il progetto corrente è salvato nella cartella `~/repositories/<project_name>` che è stato clonato da corrispondente GitHub repository.

- Dal push su GitHub vengono esclusi, tramite `.gitignore`, i file di gradi dimensioni e la cartella `sandbox`.

- Si fanno anche dei backup periodici su Google Drive).

- Nella cartella del progetto inserisco solo i dati e gli scripts. I pdf degli articoli della letteratura sono salvati su OneDrive in  `other/literature/projects` in una cartella con lo stesso nome del progetto.

## OSF

Per ciascun progetto viene creato un repository OSF. Il repository contiene:

- i dati grezzi;

- il [[codebook | codebook / data dictionary]] fornisce una spiegazione dettagliata del significato di ciascuna colonna del data set;

- una descrizione dettagliata del disegno sperimentale;

- i materiali del comitato etico.

## Project Template

Un template che riproduce la struttura di Project Template si trova su [Github](https://github.com/ccaudek/project_template) e su Dropbox. Un Project Template ha la seguente struttura.

```text
.
├── README.md
├── data
│   ├── processed
│   │   └── README.md
│   └── raw
│       └── README.md
├── project_template.Rproj
├── reports
│   └── README.md
├── saved_fits
│   └── README.md
└── src
    ├── R
    │   ├── figures
    │   │   └── README.md
    │   ├── functions
    │   │   └── README.md
    │   ├── sandbox
    │   │   └── README.md
    │   └── scripts
    │       ├── name_exp_1
    │       │   ├── 01_preprocessing
    │       │   │   └── README.md
    │       │   └── 02_descriptive_stats
    │       │       └── README.md
    │       └── name_exp_2
    │           └── README.md
    └── python
        └── README.md
```

- Nel folder `data` ci sono le cartelle `raw` e `processed`.

    - Nella cartella `raw` c’è un folder per ciascun esperimento (es., prl, task_switching, …). In `raw` ci sono i dati grezzi senza alcuna manipolazione.

    - La cartella `processed` ha la stessa struttura di `raw`(es., prl, task_switching, …). In `processed` vengono salvate le manipolazioni di *data wrangling*.

- Nel folder `src` ci sono le cartelle `R` e `python`.

- Nel folder `scr/R` ci sono le cartelle `functions`, `scripts`, `sandbox`, `figures`.

    - La cartella `functions` ha diversi folders, uno per ciascun esperimento. In ciascuno di questi folders, le funzioni R sono raggruppate tematicamente in diversi file R.

    - La cartella `scripts` ha diversi folders, uno per ciascun esperimento. All’interno di ciascuna di queste cartelle, ci sono altre cartelle. In ciascuna di queste cartelle ci sono gli scripts usati per rispondere ad una specifica domanda.

        - Le domande di ricerca sono specificate nel file README.md situato nella cartella root del progetto.

        - A ciascuna domanda di ricerca corrisponde una cartella nel folder `scripts`. Ad es., una domanda della ricerca è la seguente: c’è un deficit dominio-specifico nell’apprendimento associativo? Per rispondere a questa domanda, si può replicare l’analisi statistica descritta da Santangelo et al. (2022) usando il modello hDDMrl per i dati del PRL task somministrato ai pazienti con disturbi alimentari e ai controlli.

        - Idealmente, l’output di questa analisi è un testo che riporta tutte le informazioni descritte da Santangelo et al. (2022) nella sezione risultati del suo articolo.

        - L’output desiderato può essere prodotto in maniera automatizzata mediante la pipeline `makepipe`.

- Nel folder `scr/python` ci sono le cartelle `ipynb` e `sandbox`.

    - Nella cartella `scr/python/ipynb` ci sono i Jupyter Notebook usati per le analisi statistiche svolte in python. Ad esempio, i Jupyter Notebook usati per l’analisi dei dati del PRL task con il modello hDDMrl.

    - La cartella `sandbox` contiene i Jupyter Notebook usati per vari test.

- Nel folder `saved_fits` sono salvati i file con le stime MCMC dei parametri dei modelli statistici creati da R e da Python.

    - Questi dati non verranno caricati su GitHub: la cartella `saved_fits` viene specificata in `.gitignore` (si veda la descrizione in [gitignore](./gitignore.md)).

    - Invece, un backup di tutto il progetto (che include anche questa cartella) viene eseguito periodicamente su Google Drive.

- Il file `README.md` nella cartella root del progetto contiene una descrizione dettagliata del progetto:

    - elenco delle domande della ricerca;

    - descrizioni delle scale, con le scoring keys;

    - descrizione della metodologia (bozza della sezione *Methods* dell’articolo).

## Backup

Spazio di archiviazione su

1. **GitHub**: archiviazione dei progetti in corso e dei progetti conclusi.

2. **Google Drive**: backup dei progetti in corso, materiali della didattica, folders condivisi.

3. **OneDrive**: pdf della letteratura, archiviazione di progetti conclusi, archiviazione dei materiali didattici, materiali personali e miscellanea.

4. **iCloud**: materiali didattici dell’AA corrente; funzionamento macOS, iOS e watchOS.

5. **Dropbox**: da dismettere, dato che può essere usato solo su 3 macchine.

## Other workflow information

- [[workflow_with_r_and_python]]

- [[brm_workflow]]

- [[rlssm_workshop]]

- [[snakemake_workflow]]

- [[reproducibility_guide]]

## Non-research materials

L’archiviazione dei materiali non di ricerca segue queste [[archiviazione_su_cloud | linee guida]].

# Archiviazione su Cloud

## Didattica

- Il materiale dell'AA corrente è nella cartella `Documents` (con backup su iCloud).

- I materiali degli AA precedenti sono su OneDrive in `teaching/archive`.

- Google Drive è usato per i materiali da condividere con gli studenti.

## Personale

- Tutti i materiali personali sono salvati su OneDrive in `other/personal`.

## Coding

### Projects

- In `OneDrive/coding/python/py_projects` viene salvato il codice Python dei vari progetti.

### Learning

- In `OneDrive/coding/python/py_learning` viene salvato il codice Python che uso per lo studio.

