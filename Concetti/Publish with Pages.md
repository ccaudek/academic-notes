---
title: Publish with Pages
modificationDate: 2024-11-14 22:41
tags:
  - github
---
## Guida alla Pubblicazione su GitHub Pages

### Passo 1: Creare il Repository

Crea un repository su GitHub. Ricorda di aggiungere un file `README.md` e un file `.gitignore` durante la creazione.
### Passo 2: Clonare il Repository

Clona il repository sul tuo computer locale usando il seguente comando:

```bash
git clone https://github.com/ccaudek/psicometria
```
### Passo 3: Aggiungere Contenuti e Visualizzare il Sito Localmente

Aggiungi i contenuti desiderati nella cartella locale del repository. Per eseguire un'anteprima del sito in locale, utilizza questo comando:

```bash
quarto preview --render all --no-browse
```
### Passo 4: Eseguire il Backup su GitHub

Dopo aver apportato le modifiche, esegui il backup del lavoro su GitHub con i seguenti comandi:

```bash
git add -A
git commit -m "Descrizione del commit"
git push
```
### Passo 5: Configurare GitHub Pages

Vai nelle impostazioni del repository su GitHub. Nella sezione **Pages/Build and Deployment**, configura le seguenti opzioni:

- `Select branch`: seleziona `gh-pages`
- `Select folder`: seleziona `/(root)`

Salva le impostazioni.
### Passo 6: Pubblicare il Sito con `ghp-import`

Dopo aver modificato le impostazioni di GitHub Pages, utilizza il comando `ghp-import` per evitare la creazione di un'ulteriore branch:

```bash
ghp-import -n -p -f docs
```

In questo modo, assicuri che il sito venga generato correttamente a partire dalla branch `gh-pages`.
### Passo 7: Verificare la Pubblicazione

Se tutto è stato eseguito correttamente, su GitHub Pages dovrebbe apparire il messaggio:

```text
Your site is live at https://ccaudek.github.io/psicometria
```

