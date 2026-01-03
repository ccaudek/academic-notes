---
title: Specificare il modello Stan dentro lo script R
modificationDate: 2025-09-17 03:33
tags:
  - cmdstan
---

Senza scrivere il modello Stan in un file separato.

**Specificare il modello:**

```r
stancode <- "
data {
  int<lower=1> N;
  vector[N] x;
  vector[N] y;
}
parameters {
  real alpha;
  real beta;
  real<lower=0> sigma;
}
model {
  y ~ normal(alpha + beta * x, sigma);
  alpha ~ normal(0, 2.5);
  beta ~ normal(0, 2.5);
  sigma ~ normal(0, 2.5);
}
generated quantities {
  array[N] real y_rep = normal_rng(alpha + beta * x, sigma);
}
"
```

**Compilare:**

```r
#| output: false
mod <- cmdstan_model(
  write_stan_file(stancode),
  compile = TRUE
)
```

**Eseguire il campionamento MCMC:**

```r
#| output: false
fit1 <- mod$sample(
  data = stan_data,
  iter_warmup = 1000,
  iter_sampling = 2000,
  chains = 4,
  parallel_chains = 4,
  refresh = 0,
  seed = 20250917
)
```

