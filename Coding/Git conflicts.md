---
title: Git conflicts
description:
modificationDate: 2024-11-08 10:29
tags:
  - git
---

---

### Gestione dei conflitti in Git

Quando si lavora in Git, può capitare che si presentino conflitti tra la versione locale e quella remota del repository. Ecco alcuni metodi per risolvere questi conflitti e allineare il repository locale a quello remoto, a seconda delle esigenze.

---

### 1. Push Forzato

Se Git rileva conflitti che bloccano il push, è possibile forzare un aggiornamento della versione remota con le seguenti istruzioni:

```bash
git add .
git commit -m "Forced push"
git push origin master --force
```

**Nota:** Usare il `--force` con attenzione, poiché può sovrascrivere le modifiche sul repository remoto, potenzialmente cancellando il lavoro degli altri collaboratori.

---

### 2. Pull Forzato

Se si desidera che il repository locale corrisponda esattamente alla versione remota, ignorando tutte le modifiche locali, si possono seguire vari metodi. Ogni metodo è adatto a diversi scenari:

#### Metodo 1: Hard Reset e Pull

Questo metodo reimposta la branch locale alla versione remota, scartando tutte le modifiche locali, sia quelle commesse che non commesse.

1. **Aggiornare il repository locale con le modifiche più recenti da remoto:**

    ```bash
    git fetch origin
    ```

2. **Reimpostare la branch locale per allinearla con la versione remota:**

    ```bash
    git reset --hard origin/main
    ```

    *(Sostituisci* `main` *con il nome della branch, se diverso). Questo comando scarta tutte le modifiche ai file tracciati.*

3. **Pulire eventuali file non tracciati:**

    ```bash
    git clean -fd
    ```

    *(Rimuove tutti i file e le directory non tracciati, garantendo che la directory di lavoro sia completamente pulita).*

---

#### Metodo 2: Conservazione delle Modifiche con `Stash`

Se desideri conservare le modifiche locali per un possibile recupero futuro, puoi metterle in "stash" prima di eseguire il pull.

1. **Salvare le modifiche locali con** `stash`**:**

    ```bash
    git stash push -u
    ```

    *(L'opzione* `-u` *include anche i file non tracciati).*

2. **Eseguire il pull delle modifiche più recenti da remoto:**

    ```bash
    git pull origin main
    ```

3. **(Opzionale) Eliminare le modifiche salvate nello stash:**

    ```bash
    git stash drop
    ```

    *(Usa questo comando solo se decidi che non ti servono più le modifiche locali salvate nello stash).*

---

#### Metodo 3: Cancellazione e Re-clone del Repository

Se ci sono molti conflitti complessi o problemi irrisolvibili, è possibile eliminare il repository locale e clonarlo di nuovo da remoto.

1. **Eliminare la cartella del repository locale:**

    ```bash
    rm -rf path/to/your/repository
    ```

    *(Assicurati di navigare fuori dalla directory del repository prima di eseguire questo comando).*

2. **Clonare nuovamente il repository:**

    ```bash
    git clone https://your.repository.url
    ```

    *(Sostituisci* `https://your.repository.url` *con l’URL reale del repository).*

---

### Scegli il Metodo Adatto

- **Metodo 1:** se vuoi scartare completamente le modifiche locali e riflettere esattamente la branch remota.

- **Metodo 2:** se preferisci mantenere la possibilità di applicare le modifiche locali in un secondo momento.

- **Metodo 3:** se desideri un nuovo inizio, particolarmente utile per repository di grandi dimensioni o con problemi complessi.

Ciascun metodo permette di allineare il repository locale con quello remoto; scegli il più adatto a seconda della necessità di recuperare o meno le modifiche locali.

---
