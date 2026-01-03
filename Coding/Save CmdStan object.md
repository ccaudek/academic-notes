---
title: Save CmdStan object
modificationDate: 2025-06-23 06:03
tags:
  - cmdstan
  - R
  - coding
  - bayes
---
Save the cmdstan fit and read it later rather than running the model:

```r
# mod <- cmdstan_model("model/skim_logit_ela.stan")

# fit_laplace <- mod$sample(
#   data = data, chains = num_chains,
#   parallel_chains = num_chains,
#   iter_warmup = num_warm,
#   iter_sampling = num_post, seed = 123)
# 
# fit_laplace$save_object("saved_fits/skim_logit_ela.fit.RDS")

# For convenience, read in saved fit rather than run model
fit_laplace <- readRDS("saved_fits/skim_logit_ela.fit.RDS")
```


