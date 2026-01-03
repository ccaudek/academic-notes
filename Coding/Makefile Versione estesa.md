---
title: "Makefile: Versione estesa"
modificationDate: 2025-08-20 07:04
tags:
  - coding
  - R
---
## Template

Qui sotto trovi una **versione estesa** del Makefile descitto in [R Project Managment](./R%20Project%20Managment.md) Makefile. In questa versione, il Makefile resta essenziale ma integra alcune idee “scalabili” (pattern/variabili, directory “order-only”, parametri per Quarto, help, clean/diagnostica). È pronta da incollare:

```text
# =========================
# Project Makefile (R + Quarto + cmdstanr)
# =========================
# ---- Programmi (override da CLI: es. `make RSCRIPT="Rscript --vanilla"` )
RSCRIPT ?= Rscript
RFLAGS  ?= --vanilla
QUARTO  ?= quarto
QFLAGS  ?=
# ---- Cartelle (se servono cambia qui una volta sola)
DATA_DIR   := data
SCRIPTS    := scripts
FITS       := fits
FIG        := fig
STAN       := stan
REPORTS    := .
# ---- File principali (nomi centrali in variabili)
RAW_CSV      := $(DATA_DIR)/raw.csv
PROC_RDS     := $(DATA_DIR)/processed.rds
FIT_M1_RDS   := $(FITS)/model1.rds
PLOT_ACC_PNG := $(FIG)/acc_vs_time.png
REPORT_QMD   := report.qmd
# Puoi scegliere l'output del report: html|pdf|docx (default: html)
OUT_EXT ?= html
REPORT_OUT := $(basename $(REPORT_QMD)).$(OUT_EXT)
# ---- Target "user-facing"
.PHONY: all help clean distclean dirs diagnose
all: $(REPORT_OUT) ## Build completo: dati -> modello -> figure -> report
help: ## Mostra questa guida
	@awk 'BEGIN {FS = ":.*##"; printf "\nTargets disponibili:\n"} /^[a-zA-Z0-9_\.-]+:.*##/ { printf "  \033[36m%-18s\033[0m %s\n", $$1, $$2 }' $(MAKEFILE_LIST)
	@echo "\nVariabili utili (override da CLI):"
	@echo "  RSCRIPT='Rscript' RFLAGS='--vanilla' QUARTO='quarto' QFLAGS=''"
	@echo "  OUT_EXT=html|pdf|docx (default html)"
	@echo "\nEsempi:"
	@echo "  make -j4                      # parallelizza dove possibile"
	@echo "  make OUT_EXT=pdf              # report in PDF"
	@echo "  make QFLAGS='-P subject=\"S01\"'  # passa parametri a Quarto"
	@echo ""
diagnose: ## Mostra cosa verrebbe eseguito (dry-run)
	@$(MAKE) -n all
dirs: $(DATA_DIR) $(FITS) $(FIG) ## Crea le directory necessarie
# ---- Regole di alto livello (pipeline)
$(REPORT_OUT): $(REPORT_QMD) $(PLOT_ACC_PNG) $(FIT_M1_RDS) | dirs ## Render del report
	$(QUARTO) render $(REPORT_QMD) $(QFLAGS) --to $(OUT_EXT)
$(PLOT_ACC_PNG): $(SCRIPTS)/20_plot_acc.R $(FIT_M1_RDS) | dirs ## Figura principale
	$(RSCRIPT) $(RFLAGS) $<
$(FIT_M1_RDS): $(SCRIPTS)/10_fit_model1.R $(PROC_RDS) $(STAN)/model1.stan | dirs ## Fit del modello (cmdstanr dentro R)
	$(RSCRIPT) $(RFLAGS) $<
$(PROC_RDS): $(SCRIPTS)/01_clean.R $(RAW_CSV) | dirs ## Pulizia/preprocessing dati
	$(RSCRIPT) $(RFLAGS) $<
# ---- Directory (order-only prerequisites)
$(DATA_DIR) $(FITS) $(FIG):
	mkdir -p $@
# ---- Utility
clean: ## Rimuove artefatti di run (mantiene dati grezzi)
	@echo "Cleaning intermediate outputs..."
	@rm -f $(PROC_RDS) $(FIT_M1_RDS) $(PLOT_ACC_PNG)
distclean: clean ## Ripulisce anche i report
	@echo "Removing rendered reports..."
	@rm -f $(basename $(REPORT_QMD)).html $(basename $(REPORT_QMD)).pdf $(basename $(REPORT_QMD)).docx
# ---- Sicurezza/robustezza
.DELETE_ON_ERROR:
.SUFFIXES:
```

## Cosa aggiunge, concretamente

1. **Variabili centrali e OUT_EXT**
Cambi estensione del report una volta sola:
`make OUT_EXT=pdf` → produce `report.pdf` senza toccare le regole.

2. **Order-only prerequisites per le directory**
Le cartelle (data/, fig/, fits/) si creano se mancano ma **non** forzano rebuild inutili:

    ```text
    target: deps | dirs
    ```

3. **Parametri a Quarto senza toccare il Makefile**
Passi parametri con `QFLAGS`, es.:
`make QFLAGS='-P subject="S01" -P run_date="2025-08-20"'`

4. **Help/diagnose**
`make help` mostra i target disponibili;
`make diagnose` fa il **dry-run** (`-n`) così vedi cosa verrebbe eseguito.

5. **Pulizia graduata**
`make clean` rimuove solo intermedi; `make distclean` rimuove anche i report renderizzati.

6. **Parallelizzazione facile**
Se hai passi indipendenti, basta `make -j4`. Qui la pipeline è seriale (dipendenze in cascata), ma in progetti più grandi la parallelizzazione viene “gratis”.

---
### Estendere senza fatica

- **Aggiungere un secondo modello** (stesso schema):

    ```text
    FIT_M2_RDS := $(FITS)/model2.rds
    $(FITS)/model2.rds: $(SCRIPTS)/11_fit_model2.R $(PROC_RDS) $(STAN)/model2.stan | dirs
    	$(RSCRIPT) $(RFLAGS) $<
    all: $(FITS)/model2.rds
    ```

- **Più figure**:

    ```text
    $(FIG)/roc.png: $(SCRIPTS)/21_plot_roc.R $(FIT_M1_RDS) | dirs
    	$(RSCRIPT) $(RFLAGS) $<
    $(REPORT_OUT): $(FIG)/roc.png
    ```

- **Parametri per soggetto/condizione** (senza toccare gli script):
Dentro R leggi variabili d’ambiente impostate da Make:

    ```r
    subj <- Sys.getenv("SUBJECT", unset = "ALL")
    ```

    E lanci:

    ```text
    make SUBJECT=S01
    ```

    (Dentro gli script usa `Sys.getenv("SUBJECT")` per filtrare i dati o scegliere il file di output.)

---
### Nota su “pattern rules”

In questo Makefile le regole sono **esplicite** (leggibili). Se il progetto cresce (molti script che seguono la stessa convenzione), puoi introdurre **pattern rules** per ridurre il boilerplate, ad es.:

```text
# Esempio (solo se adotti una convenzione di nomi coerente)
# data/xyz.rds si costruisce da scripts/00_xyz.R e data/raw.csv
$(DATA_DIR)/%.rds: $(SCRIPTS)/00_%.R $(RAW_CSV) | dirs
	$(RSCRIPT) $(RFLAGS) $<
```
