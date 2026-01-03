---
type: Zettel
title: Stan Workflow
description: null
modificationDate: 2025-06-03 07:13
tags: [coding, research, bayes]
coverImage: null
---

[Workflow](./Workflow.md)

Creare una cartella per ciascuna serie di modelli Stan che richiedono lo stesso input. Come template, considera questo [repository](https://github.com/stan-dev/example-models/tree/master/jupyter/sum-to-zero). Gli scripts nel repository devono essere self-contained: ci deve essere uno script che crea l'input per Stan, lo script R per eseguire il campionamento e il sommario dei risultati, e lo script Stan con il modello. È necessaria la presenza di un `README.md` file che spiega gli obiettivi dell'analisi, l'uso degli script e fornisce un sommario dei risultati. Si distinguono lo script principale (nel tutorial GitHub è [sum_to_zero_evaluation.qmd](https://github.com/stan-dev/example-models/blob/master/jupyter/sum-to-zero/sum_to_zero_evaluation.qmd)) dagli script di supporto (nel tutorial sono `utils_nyc_map.py` ecc.). I nomi dei file di supporto iniziano con `utils_`). 

