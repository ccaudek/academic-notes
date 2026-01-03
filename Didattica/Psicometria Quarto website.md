---
type: Zettel
title: Psicometria Quarto website
description: null
modificationDate: 2024-12-02 18:18
tags: [teaching, l24, python]
coverImage: null
---

# Compile the website

```bash
quarto preview --render all --no-browse
```

# Output directory

Nel file `_quarto.yml`, ho specificato che l'output del libro viene generato nella directory `docs` con questa configurazione:

```yaml
output-dir: docs
```

Ciò significa che la directory di output è `docs`. Pertanto, devo usare `docs` nel comando `ghp-import`:

```bash
ghp-import -n -p -f docs
```

# GitHub Push

Per eseguire il backup su GitHub, usare:

```bash
git add -A
git commit -m "updated stan normal model"
git push
```

# Publish to Pages

Per pubblicare il progetto su GitHub Pages, usare:

```bash
ghp-import -n -p -f docs
```

See also [Publish with Pages](./Publish%20with%20Pages.md)

---

# Render

Per rendere un **book Quarto** dalla command line, segui questi passaggi:

### 1. Navigare nella directory del progetto

Apri il terminale e spostati nella directory principale del progetto Quarto che contiene il file di configurazione `_quarto.yml`. Usa il comando:

```bash
cd /percorso/della/tua/cartella
```

### 2. Comando per rendere il book

Usa il comando `quarto render` per generare il book:

```bash
quarto render
```

### 3. Specificare opzioni aggiuntive (opzionale)

Puoi aggiungere opzioni al comando per personalizzare il rendering:

#### Rendere un formato specifico

Per esempio, per generare solo la versione PDF del book:

```bash
quarto render --to pdf
```

Per generare solo la versione HTML:

```bash
quarto render --to html
```

#### Renderizzare un file specifico

Per generare solo un file specifico all'interno del progetto:

```bash
quarto render nomefile.qmd
```

#### Pulire i file intermedi

Per eliminare file intermedi creati durante il rendering:

```bash
quarto render --clean
```

#### Forzare il rendering di tutti i file

Per rigenerare tutti i file, anche quelli che non sono stati modificati:

```bash
quarto render --execute
```

### 4. Verifica del risultato

Dopo aver completato il comando, il book sarà generato nella directory di output specificata nel file `_quarto.yml` (di solito `./_book` o `./docs`).

Puoi aprire il book generato nel browser o visualizzarlo nel formato appropriato (PDF, HTML, EPUB, ecc.). Ad esempio, per un book HTML:

```bash
open _book/index.html
```

Assicurati che il file `_quarto.yml` sia configurato correttamente per il tuo progetto.

