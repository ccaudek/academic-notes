---
type: Zettel
title: failed to push
description: null
modificationDate: 2025-09-20 20:34
tags: [coding, git]
coverImage: null
---

Hai già committato due file enormi (fit_A.qs ~197 MB, fit_B.qs ~257 MB) e il push è stato rifiutato da GitHub (limite 100 MB). Devi:
- Escludere i .qs d’ora in poi
- Togliere quei blob dalla cronologia che stai cercando di pushare.

# Scenario A — i .qs sono nel **tuo ultimo commit** (branch “ahead by 1 commit”)

```shell
# 1) Ignora i .qs in futuro
echo '*.qs' >> .gitignore
git add .gitignore

# 2) Togli i file dal tracking (li lasci sul disco)
git rm --cached fit_A.qs fit_B.qs

# 3) Riscrivi l’ultimo commit rimuovendo i blob e includendo il .gitignore
git commit --amend --no-edit

# 4) Push riscrivendo solo la tua punta (sicuro per i collaboratori se nessuno ha tirato il tuo commit rifiutato)
git push --force-with-lease
```

Note:

- `--amend` sostituisce l’ultimo commit con una versione **senza** i .qs.

- `--force-with-lease` è più sicuro di `--force` perché evita di sovrascrivere lavori altrui inavvertitamente.

- Se ricevi ancora errore, vuol dire che i blob grossi non erano solo nell’ultimo commit → passa allo Scenario B.

# Scenario B — i .qs sono già in **commit più vecchi**

Servono strumenti di “history rewrite”. Ti propongo `git filter-repo` (consigliato) oppure BFG.

## Opzione 1: git filter-repo (consigliato)

Installazione (una tantum):

- macOS con Homebrew: `brew install git-filter-repo`

- oppure scarica lo script da GitHub (repo ufficiale di git-filter-repo).

Poi:

```shell
# 0) Assicurati di essere sul branch giusto
git checkout main

# 1) Rimuovi i file grandi ovunque compaiano nella storia
git filter-repo --path fit_A.qs --path fit_B.qs --invert-paths
# In alternativa, per rimuovere TUTTI i blob >100MB:
# git filter-repo --strip-blobs-bigger-than 100M

# 2) Aggiungi .gitignore per evitare futuri tracking
echo '*.qs' >> .gitignore
git add .gitignore
git commit -m "Ignore .qs artifacts"

# 3) Push forzato della nuova storia
git push --force-with-lease

```

Dopo un rewrite, i collaboratori dovranno fare `git fetch` e **resettare** o riclonare:

`git fetch origin && git reset --hard origin/main` (se non hanno commit locali), altrimenti rebase/correzioni manuali.


