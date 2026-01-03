---
title: brms syntax
modificationDate: 2025-02-27
tags:
  - coding
  - quarto
  - teaching
  - cmdstan
  - R
---
To prevent printing the output messages during sampling in a Quarto book, use `silent = 0` :

```r
#| message: false
#| warning: false
#| output: false

fit_1 = brm(
  bf(height ~ 1 + weight_c, center = FALSE), 
  data = df, 
  backend = "cmdstanr", 
  silent = 0
)
```

