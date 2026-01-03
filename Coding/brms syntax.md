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

To avoid printing the output messages in a Quarto book:

```text
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

