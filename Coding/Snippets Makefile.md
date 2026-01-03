---
type: Zettel
title: Snippets Makefile
description: null
modificationDate: 2025-08-20 05:46
tags: []
coverImage: null
---

```shell
all: manuscript.pdf
manuscript.pdf: data/iris_prepped.csv manuscript.Rmd
  Rscript -e 'rmarkdown::render("manuscript.Rmd")'
data/iris_prepped.csv: R/prepare_data.R data/iris.csv
  Rscript -e 'source("R/prepare_data.R")'
```

