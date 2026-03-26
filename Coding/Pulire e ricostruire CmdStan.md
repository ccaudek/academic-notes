---
tags:
  - cmdstan
  - R
---
Dopo un <mark>aggiornamento di macOS</mark> e dei <mark>Command Line Tools</mark>, la cosa da fare di solito è **pulire e ricostruire CmdStan**. La documentazione ufficiale di CmdStan dice esplicitamente che aggiornamenti di CmdStan, cambi nelle opzioni del compilatore o aggiornamenti della toolchain C++ possono causare errori di compilazione, e che spesso si risolve con `make clean-all` seguito da `make build`. In `cmdstanr`, l’equivalente consigliato è `rebuild_cmdstan()`. ([Stan](https://mc-stan.org/docs/cmdstan-guide/installation.html "CmdStan Installation"))

Farei così, in quest’ordine.

In R:

```r
library(cmdstanr)

check_cmdstan_toolchain()

rebuild_cmdstan()
```

`check_cmdstan_toolchain()` verifica che la toolchain richiesta ci sia; `rebuild_cmdstan()` “clean and rebuilds” l’installazione esistente di CmdStan in caso di problemi di compilazione. ([Stan](https://mc-stan.org/cmdstanr/reference/install_cmdstan.html "Install CmdStan or clean and rebuild an existing installation — install_cmdstan • cmdstanr"))

Se `rebuild_cmdstan()` non basta, fai una reinstallazione completa di CmdStan dalla stessa interfaccia:

```r
library(cmdstanr)

install_cmdstan(overwrite = TRUE, cores = 4)
```

`install_cmdstan()` reinstalla CmdStan; con `overwrite = TRUE` forza la sovrascrittura dell’installazione esistente. La documentazione lo indica come il modo standard per installare o reinstallare CmdStan. ([Stan](https://mc-stan.org/cmdstanr/reference/install_cmdstan.html "Install CmdStan or clean and rebuild an existing installation — install_cmdstan • cmdstanr"))

Poi prova subito una compilazione di test:

```r
library(cmdstanr)

file <- file.path(cmdstan_path(), "examples", "bernoulli", "bernoulli.stan")
mod <- cmdstan_model(file)
```

La guida ufficiale suggerisce proprio di verificare l’installazione compilando l’esempio `bernoulli`. ([Stan](https://mc-stan.org/docs/cmdstan-guide/installation.html "CmdStan Installation"))

Se preferisci farlo da terminale, nella directory di CmdStan:

```bash
cd ~/.cmdstan/cmdstan-<versione>
make clean-all
make build
```

Questi sono i comandi raccomandati nella guida di installazione quando la compilazione smette di funzionare dopo aggiornamenti della toolchain. ([Stan](https://mc-stan.org/docs/cmdstan-guide/installation.html "CmdStan Installation"))

In pratica, la procedura minima che di solito risolve è:

```r
library(cmdstanr)
check_cmdstan_toolchain()
rebuild_cmdstan()
```

Se vuoi evitare tentativi alla cieca, incollami l’errore di compilazione che ottieni dopo l’update e ti dico il passaggio esatto da fare.