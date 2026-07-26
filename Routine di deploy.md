---
tags:
  - teaching
  - UTET
  - quarto
modificationDate: 2026-07-26T15:02:00
---
Per il progetto UTET

```
./deploy.sh "controllo link interni"
```
## Cercare una stringa nei file di una cartella

Usare `grep` per cercare, ad esempio, `@sec-likelihood-properties`, nella cartella `chapters\`:

```
grep -rn "@sec-likelihood-properties" chapters/
```
