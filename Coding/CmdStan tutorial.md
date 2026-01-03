---
modificationDate: 2024-11-14 22:40
tags:
  - cmdstan
---
## Stan Syntax

A Stan program is usually saved as a `.stan` file and accessed through R (or other interfaces) and it is organized into a sequence of optional and obligatory blocks, which must be written in order.

- Every statement ends in a semi-colon, `;`.
- Blocks (`{}`) do not end in semi-colons.

> [!tip]
The package `rstan` provides the function `lookup()` to look up for translations of functions from R to Stan.

*Example:* `lookup(plogis)`

Every variable needs to be declared at the beginning of a block with its type (real, integer, vector, matrix, etc.).
## Normal Likelihood

### Model definition

```text
stan_code <- "
data {
  int<lower = 1> N;  // Total number of trials
  vector[N] y;  // Score in each trial
}
parameters {
  real mu;
  real<lower = 0> sigma;
}
model {
  // Priors:
  target += normal_lpdf(mu | 0, 20);
  target += lognormal_lpdf(sigma | 3, 1);
  // Likelihood:
  for(i in 1:N)
    target += normal_lpdf(y[i] | mu, sigma);
}
"
```

The variable `target` is a special reserved keyword in Stan that accumulates contributions to the unnormalized log posterior density of the model. Essentially, each statement with `target +=` adds a term to this density function, effectively modifying the numerator of the Bayesian posterior distribution in its logarithmic form.

#### What does `target` do?

To understand how `target` works, let's consider one hypothetical iteration of the MCMC sampler. During each iteration, the sampler explores the posterior distribution by proposing new values for the parameters $\mu$ and $\sigma$. These proposed values are points in the Hamiltonian space where the algorithm momentarily "pauses."

Suppose that, in one such iteration, $\mu$ = 1.77 and $\sigma$ = 10.703. Here's what happens in the model block:

- **Prior for** $\mu$: The line `target += normal_lpdf(mu | 0, 20);` calculates the log density of a Normal(0, 20) distribution evaluated at $\mu$ = 1.77. This value is then added to `target`. In R, this operation would be equivalent to computing `dnorm(x = 1.77, mean = 0, sd = 20, log = TRUE)`.

- **Prior for** $\sigma$: The line `target += lognormal_lpdf(sigma | 3, 1);` calculates the log density of a LogNormal(3, 1) distribution evaluated at $\sigma$ = 10.703. This is added to the existing value of `target`. In R, the equivalent operation is `dlnorm(x = 10.703, meanlog = 3, sdlog = 1, log = TRUE)`.

- **Likelihood**: In the `for` loop, the model adds the log density of a Normal distribution with mean $\mu$ = 1.77 and standard deviation $\sigma$ = 10.703, evaluated at each observed value $y[i]$. In R, this would be analogous to computing `sum(dnorm(y, mean = 1.77, sd = 10.703, log = TRUE))`.

The total value stored in `target` at this iteration represents the height of the unnormalized posterior distribution at the coordinates $\mu$ = 1.77, $\sigma$ = 10.703. The actual height of the unnormalized posterior at these coordinates would be $e^{\text{target}}$.

#### Additional Notes

- The value of `target` is returned as `lp__` (log probability) in the Stan output and can be useful for diagnostic purposes.

- While you can't print `target` directly inside a Stan model, you can inspect its value by examining the `lp__` field in the Stan output.

By accumulating these log densities, Stan efficiently computes the posterior distribution, enabling the exploration of complex models with high-dimensional parameter spaces.

#### Sampling notation

Stan also allows for specifying priors and likelihood with the so-called sampling notation with the following code.

```text
parameter ~ pdf_name(..)
```

The following two lines of code lead to the same behavior in Stan.

```text
y ~ normal(mu, sigma);
target += normal_lpdf(y | mu, sigma);
```

There is, nonetheless, an important difference between them: The sampling notation (the notation with the ∼) will *drop normalizing constants*.

The advantage of the sampling notation is that it can be faster (when many terms are ignored), but the disadvantage is that (i) it is not compatible with the calculation of Bayes factor with bridge sampling, and (ii) for some complex models the sampling notation cannot be used (for example, the mixture models).

```text
stan_code <- "
data {
  int<lower = 1> N;  // Total number of trials
  vector[N] y;  // Score in each trial
}
parameters {
  real mu;
  real<lower = 0> sigma;
}
model {
  // Priors:
  mu ~ normal(0, 20);
  sigma ~ exponential(1.0/10);
  // Likelihood:
  y ~ normal(mu, sigma); 
}
"
```

### Compile the model

```text
stan_file <- write_stan_file(stan_code)
mod <- cmdstan_model(stan_file)
```

### Data

Provide the data in the appropriate format.

```text
Y <- rnorm(n = 100, mean = 3, sd = 10)
stan_data <- list(
  N = length(Y), 
  y = Y
)
```

### Running MCMC

Fit the model to the data.

```text
fit <- mod$sample(
  data = stan_data,
  iter_sampling = 2000,
  iter_warmup = 1000,
  chains = 4
)
fit$summary()
```

## Post-processing

You can get the list of parameters, transformed parameters and generated quantities as well as data with `mod$variables()`:

```r
names(mod$variables()$parameters)
```

Use `$summary()` to perform hypothesis testing.

```r
fit$summary("mu", pr_lt_half = ~ mean(. <= 0.0))
```

Add 95% CI.

```r
fit$summary(
  variables = NULL,
  posterior::default_summary_measures(),
  extra_quantiles = ~posterior::quantile2(., probs = c(.0275, .975))
)
```

Convert cmdstan object into stanfit object.

```r
stanfit <- rstan::read_stan_csv(fit$output_files())
```

Generate a traceplot.

```r
mcmc_trace(stanfit, pars = c("mu", "sigma"))
```

Plot with the credibility intervals.

```r
mcmc_intervals(stanfit, pars = c("mu", "sigma"))
mcmc_areas(
  stanfit, 
  pars = c("mu", "sigma"),
  prob = 0.8, # 80% intervals
  prob_outer = 0.95, # 95%
  point_est = "mean"
)
```

### Create a `stanfit` object

If you have RStan installed then it is also possible to create a `stanfit` object from the csv output files written by CmdStan. This can be done by using  `rstan::read_stan_csv()`  in combination with the `$output_files()` method of the  `CmdStanMCMC` object.

```r
stanfit <- rstan::read_stan_csv(fit$output_files())
```

This is only needed if you want to fit a model with CmdStanR but already have a lot of post-processing code that assumes a  `stanfit` object. Otherwise we recommend using the post-processing functionality provided by CmdStanR itself.

### HDI interval

Intervallo di massima densità (HDI):

```r
stanfit <- rstan::read_stan_csv(fit$output_files())
bayestestR::hdi(stanfit, ci = 0.94)
```

### PP_check in cmdstan

[Posterior Predictive Check](https://discourse.mc-stan.org/t/cmdstanpy-with-arviz-ppc-plot-differs-from-cmdstanr-with-bayesplot/23473)

```r
y_rep <- fit$draws("y_rep", format = "matrix")
ppc_dens_overlay(y = df$y, yrep = y_rep[1:200, ])
```

## Running optimization and variational inference

##  Linear Algebra Types

Stan contains three basic linear algebra types, `vector`, `row_vector`, and `matrix`. But Stan also allows for building arrays of any dimension from any type of element (integer, real, etc.). This means that there are several ways to define one-dimensional N-sized containers of real numbers,

```text
array[N] real a;
vector[N] a;
row_vector[N] a;
```

as well as, two-dimensional N1×N2-sized containers of real numbers:

```text
array[N1, N2] real m;
matrix[N1, N2] m;
array[N1] vector[N2] b;
array[N1] row_vector[N2] b;
```

These distinctions affect either what we can do with these variables, or the speed of our model, and sometimes are interchangeable.

> [!warning]
**Matrix algebra** is only defined for (row) vectors and matrices, that is we cannot multiply arrays.

The following line requires all the one-dimensional containers (`p_size`and `c_load`) to be defined as vectors (or row_vectors):

```text
vector[N] mu = alpha + c_load * beta;
```

Many “vectorized” operations are also valid for arrays, that is, `normal_lpdf`, accepts (row) vectors (as we did in our code) or arrays as in the next example. There is of course no point in converting a vector to an array as follows, but this shows that Stan allows both type of one-dimensional containers.

```text
array[N] real mu = to_array_1d(alpha + c_load * beta);
target += normal_lpdf(p_size | mu, sigma);
```

By contrast, the outcome of “vectorized” pseudorandom number generator (`_rng`) functions can only be stored in an array. The following example shows the only way to vectorize this type of function:

```text
array[N] real p_size_pred = normal_rng(
	alpha + c_load * beta, sigma);
```

Alternatively, one can always use a for-loop, and it won’t matter if `p_size_pred` is an array or a vector:

```text
vector[N] p_size_pred;
for(n in 1:N)
    p_size_pred[n] = normal_rng(alpha + c_load[n] * beta, sigma);
```

See also Stan’s manual section on matrices, vector, and arrays (Stan Development Team [2021](https://vasishth.github.io/bayescogsci/book/ch-introstan.html#ref-Stan2021)).

To define a one-dimensional *array* of `N` elements that contains integers (bounded between 1 and `N_subj`), we use

```text
array [N] int<lower = 1, upper = N_subj> subj;
```

As explained in Box [10.4](https://vasishth.github.io/bayescogsci/book/ch-introstan.html#thm:stancontainers), the difference between vectors and one-dimensional arrays is that vectors can only contain real numbers and can be used with matrix algebra functions, and arrays can contain any type but can’t be used with matrix algebra functions.

## Write a Stan model in an R script

```text
lines <- "
	data {
	  int <lower = 1> n;
	  vector[n] x;
	  vector[n] y;
	  real true_beta;
	}
	parameters {
	  real beta;
	}
	model {
	  y ~ normal(x * beta, 1);
	  beta ~ normal(0, 1);
	}
"
writeLines(lines, "mymodel.stan")
```

## Saving fitted model objects

See the [link](https://community.r-multiverse.org/cmdstanr/doc/cmdstanr.html)

The [http://mc-stan.org/cmdstanr/reference/fit-method-save_object.html](http://mc-stan.org/cmdstanr/reference/fit-method-save_object.html) method provided by CmdStanR is the most convenient way to save a fitted model object to disk and ensure that all of the contents are available when reading the object back into R.

```text
fit$save_object(file = "fit.RDS")
# can be read back in using readRDS
fit2 <- readRDS("fit.RDS")
```

But if your model object is large, then [http://mc-stan.org/cmdstanr/reference/fit-method-save_object.html](http://mc-stan.org/cmdstanr/reference/fit-method-save_object.html) could take a long time. [http://mc-stan.org/cmdstanr/reference/fit-method-save_object.html](http://mc-stan.org/cmdstanr/reference/fit-method-save_object.html) reads the CmdStan results files into memory, stores them in the model object, and saves the object with `saveRDS()`. To speed up the process, you can emulate [http://mc-stan.org/cmdstanr/reference/fit-method-save_object.html](http://mc-stan.org/cmdstanr/reference/fit-method-save_object.html) and replace `saveRDS` with the much faster `qsave()` function from the [https://github.com/traversc/qs](https://github.com/traversc/qs) package.

```text
# Load CmdStan output files into the fitted model object.
fit$draws() # Load posterior draws into the object.
try(fit$sampler_diagnostics(), silent = TRUE) # Load sampler diagnostics.
try(fit$init(), silent = TRUE) # Load user-defined initial values.
try(fit$profiles(), silent = TRUE) # Load profiling samples.
# Save the object to a file.
qs::qsave(x = fit, file = "fit.qs")
# Read the object.
fit2 <- qs::qread("fit.qs")
```

Storage is even faster if you discard results you do not need to save. The following example saves only posterior draws and discards sampler diagnostics, user-specified initial values, and profiling data.

```text
# Load posterior draws into the fitted model object and omit other output.
fit$draws()
# Save the object to a file.
qs::qsave(x = fit, file = "fit.qs")
# Read the object.
fit2 <- qs::qread("fit.qs")
```

