Una cartella contiene molte sotto-cartelle. Voglio l’elenco dei file .qmd che contengono la stringa `cut-off`:

```bash
grep -r --include="*.qmd" "cut-off" .
```