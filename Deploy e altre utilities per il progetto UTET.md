---
tags:
  - teaching
  - UTET
  - quarto
modificationDate: 2026-07-26T15:02:00
---
## Deploy

Per il progetto UTET

```
./deploy.sh "controllo link interni"
```
## Cercare una stringa nei file di una cartella

Usare `grep` per cercare, ad esempio, `@sec-likelihood-properties`, nella cartella `chapters\`:

```
grep -rn "@sec-likelihood-properties" chapters/
```

## Utilizzare lo stile scelto per il pdf

Per utilizzare lo stile specificato nello yml, installare l’estensione seguente nella root directory del progetto:

```
quarto add pandoc-ext/section-bibliographies --no-prompt
```
