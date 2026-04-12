---
tags:
  - coding
---
**Per aggiornare i cask in Homebrew** (applicazioni GUI installate con `brew install --cask`), utilizza il comando:

```bash
brew update && brew upgrade --greedy
```

**Cosa fa esattamente?**  
- `brew update` → aggiorna la lista delle formule e dei cask disponibili.  
- `brew upgrade --greedy` → aggiorna **tutti** i pacchetti obsoleti (sia formule che cask), includendo anche i cask con `auto_updates true` o `version :latest`, che di default verrebbero ignorati da `brew upgrade` semplice.

**Nota:** se vuoi aggiornare **solo i cask** (escludendo le formule), puoi usare:

```bash
brew upgrade --cask --greedy
```

**Attenzione:** l’opzione `--greedy` può forzare l’aggiornamento di cask che si auto-aggiornano (es. browser, IDE). In alcuni casi potrebbe scaricare una versione già presente. Usalo con consapevolezza.
