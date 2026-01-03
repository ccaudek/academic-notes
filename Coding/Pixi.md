---
type: Zettel
title: Pixi
description: null
modificationDate: 2024-12-09 20:07
tags: [R, workflow]
coverImage: null
---

# Progetto di Data Analysis con R e Pixi

## Prerequisiti

- Installare Pixi (`https://github.com/prefix-dev/pixi`)

- R installato sul sistema

- RStudio (opzionale ma consigliato)

## Struttura del Progetto

```shell
data-analysis-project/
│
├── pixi.toml               # File di configurazione Pixi
├── pixi.lock               # Lockfile per dipendenze
│
├── data/                   # Directory per i dati raw
│   ├── raw/
│   └── processed/
│
├── src/                    # Codice sorgente R
│   ├── data_cleaning.R
│   ├── analysis.R
│   └── visualization.R
│
├── reports/                # Output e report
│   ├── figures/
│   └── report.Rmd
│
└── README.md               # Documentazione del progetto
```

Configurazione Pixi (`pixi.toml`)

```yaml
[project]
name = "r-data-analysis"
description = "Progetto di data analysis con R"
authors = ["Tuo Nome <tua.email@example.com>"]
channels = ["conda-forge"]
platforms = ["linux-64", "osx-64", "win-64"]

[dependencies]
r-base = "4.3.1"
r-tidyverse = "*"
r-readr = "*"
r-dplyr = "*"
r-ggplot2 = "*"
r-knitr = "*"
r-rmarkdown = "*"

[tasks]
clean = "rm -rf reports/figures/* data/processed/*"
data-prep = "Rscript src/data_cleaning.R"
analysis = "Rscript src/analysis.R"
report = "Rscript -e 'rmarkdown::render(\"reports/report.Rmd\")'"
all = { depends-on = ["clean", "data-prep", "analysis", "report"] }
```

## Esempio di Script di Pulizia Dati (`src/data_cleaning.R`)

```r
library(readr)
library(dplyr)

# Caricamento dati
raw_data <- read_csv("data/raw/dati_esempio.csv")

# Pulizia dati
cleaned_data <- raw_data %>%
  filter(!is.na(valore)) %>%
  mutate(categoria = factor(categoria)) %>%
  group_by(categoria) %>%
  summarise(media = mean(valore, na.rm = TRUE))

# Salvataggio dati puliti
write_csv(cleaned_data, "data/processed/dati_puliti.csv")
```

## Esempio di Analisi (`src/analysis.R`)

```r
library(dplyr)
library(ggplot2)

# Caricamento dati puliti
dati <- read_csv("data/processed/dati_puliti.csv")

# Analisi statistica
risultati_analisi <- dati %>%
  group_by(categoria) %>%
  summarise(
    media = mean(media),
    deviazione_standard = sd(media)
  )

# Salvataggio risultati
write_csv(risultati_analisi, "reports/risultati_analisi.csv")

# Visualizzazione
ggplot(dati, aes(x = categoria, y = media)) +
  geom_bar(stat = "identity") +
  theme_minimal() +
  ggtitle("Media per Categoria")

ggsave("reports/figures/media_categoria.png")
```

## Esempio di Report (`reports/report.Rmd`)

```r
---
title: "Report di Data Analysis"
output: html_document
---

## Risultati dell'Analisi

```{r, echo=FALSE}
library(knitr)
risultati <- read_csv("risultati_analisi.csv")
kable(risultati)
```

# Comandi Pixi

```shell
# Inizializzazione progetto
pixi init

# Installazione dipendenze
pixi install

# Esecuzione task
pixi run data-prep
pixi run analysis
pixi run report

# Esecuzione task combinati
pixi run all
```

# Clean up

Dato che il repository creato da Pixi è molto grande, posso eliminare la directory `.pixi` con:

```bash
rm -rf .pixi
```

