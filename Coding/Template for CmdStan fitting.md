---
title: Template for CmdStan fitting
modificationDate: 2025-07-21 07:42
tags:
  - coding
  - cmdstan
---

```r
library(cmdstanr)
library(bayesplot)

standata <- list(
  m = m,
  logor = sim_binary_ce$logor,
  se = sqrt(sim_binary_ce$se2)
)

stancode <- "
data {
  int m;
  array[m] real logor;
  array[m] real<lower=0> se;
}
parameters {
  real theta;
}
transformed parameters {
	real or;
	or = exp(theta);
}
model {
  theta ~ normal(0, 3);
  for(j in 1:m) {
    logor[j] ~ normal(theta, se[j]);
  }
}
"

stanmod <- cmdstan_model(
  write_stan_file(stancode), 
  compile = TRUE
)

stanfit <- stanmod$sample(
  data=standata,
  iter_warmup=1000,
  iter_sampling=10000,
  chains = 2,
  parallel_chains = 2,
  refresh=1000,
  seed=4790
)

print(stanfit$summary())
standraws <- stanfit$draws(format="draws_matrix")

print(posterior::summarise_draws(
  standraws,
  mean,
  ~quantile(.x, probs=c(0.025, 0.5, 0.975))
  )
)

mcmc_trace(standraws, pars=c('theta', 'or'))
```


