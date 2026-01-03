---
title: Ambiente virtuale `vent`
modificationDate: 2025-04-21 07:06
tags:
  - teaching
---

### **Installazione**

Se preferisci evitare modifiche al sistema globale, puoi utilizzare un ambiente virtuale Python (`venv`):

1. Crea un ambiente virtuale:

    ```bash
    python3 -m venv myenv
    ```

2. Attivalo:

    ```bash
    source ~/myenv/bin/activate
    ```

3. Installa `ghp-import` all'interno dell'ambiente virtuale:

    ```bash
    pip install ghp-import
    ```

4. Per aggiornare GitHub Pages, usa il comando:

    ```bash
    ghp-import -n -p -f docs
    ```

Con questi passaggi, sarai in grado di utilizzare `ghp-import` senza dipendere da conda.

### **Eliminazione dell'ambiente virtuale**

Se vuoi rimuovere l'ambiente virtuale, elimina semplicemente la directory `myenv`:

```bash
rm -rf myenv
```

### **Verifica installazione**

Se desideri confermare che `ghp-import` sia stato installato correttamente, puoi verificare la versione:

```bash
ghp-import --version
```

