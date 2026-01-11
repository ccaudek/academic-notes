---
modificationDate: 2025-12-11 16:59
tags:
  - teaching
  - quarto
---
## Compilare il sito web localmente

Il comando che uso di norma per lavorare su un sito Quarto e' semplicemente:

```
quarto preview
```

Questo comando:

- avvia un server di preview locale;
- compila il sito (o il documento) se necessario;
- **monitora automaticamente** i file di input (.qmd, .ipynb, file di configurazione);
- rigenera le parti modificate al rilevamento dei cambiamenti;
- **apre automaticamente il browser** all'indirizzo del sito.

Per la maggior parte dei casi, `quarto preview` e' sufficiente ed e' la scelta consigliata per lo sviluppo interattivo.

## Differenze rispetto a `quarto preview --render all --no-browse`

Il comando:

```
quarto preview --render all --no-browse
```

introduce due differenze importanti rispetto al comportamento di default.

### Opzione `--render all`

- Con `quarto preview` (senza opzioni), Quarto rigenera **solo i file che considera necessari** in base alle modifiche rilevate.
- Con `--render all`, **l'intero sito viene ricompilato a ogni cambiamento**, indipendentemente da quali file siano stati modificati.

Questa opzione e' utile quando:

- le dipendenze tra pagine non sono rilevate correttamente;
- sono stati modificati file condivisi (ad esempio dati, file di configurazione, o include comuni);
- si vogliono evitare risultati incoerenti dovuti a build parziali.

Lo svantaggio e' che la compilazione puo' essere sensibilmente piu' lenta per siti di grandi dimensioni.

### Opzione `--no-browse`

- Con `quarto preview`, il browser viene aperto automaticamente all'avvio del server.
- Con `--no-browse`, Quarto **non apre il browser**, ma il server di preview e' comunque attivo.

Questa opzione e' utile quando:

- si lavora da terminale e non si vuole interrompere il flusso di lavoro;
- si avvia il preview su un server remoto;
- si apre manualmente il browser solo quando necessario.

## Monitoraggio dei file di input

Sia `quarto preview` sia  
`quarto preview --render all --no-browse` **monitorano automaticamente** i file di input.

Se si vuole disabilitare il monitoraggio (caso raro), si puo' usare:

```
quarto preview --no-watch-input
```

In questo caso:

- le modifiche ai file .qmd o .ipynb **non** attivano la ricompilazione;
- e' necessario rilanciare manualmente il comando di rendering.
## Compilare un singolo file

Per compilare un singolo file Quarto (ad esempio `syllabus.qmd`) senza avviare il server di preview:

```
quarto render syllabus.qmd
```

Questo comando e' utile per:

- build non interattive;
- script automatici;
- verifiche rapide su un singolo documento.
## Riepilogo rapido

- Usa `quarto preview` per lo sviluppo quotidiano.
- Usa `quarto preview --render all` se sospetti problemi di dipendenze o build incomplete.
- Aggiungi `--no-browse` se non vuoi l'apertura automatica del browser.
- Usa `quarto render` per build puntuali o automatizzate.
    
## Pubblicare il sito su GitHub Pages

Per pubblicare un sito statico generato con Quarto su GitHub Pages, e' possibile usare il comando `ghp-import`:

```
ghp-import -n -p -f docs
```

Questo comando copia il contenuto della directory `docs` nel branch `gh-pages` del repository e lo pubblica su GitHub Pages.

### Significato delle opzioni

- `-n`  
    Non aggiunge il file `.nojekyll` al branch `gh-pages`.
    
    Il file `.nojekyll` viene normalmente usato per disabilitare il motore Jekyll di GitHub. In questo caso, l'opzione `-n` evita la sua creazione. Questa scelta puo' essere utile se il sito non presenta conflitti con Jekyll o se si desidera mantenere il comportamento standard di GitHub Pages.
    
- `-p`  
    Esegue automaticamente il push sul repository remoto dopo aver aggiornato il branch `gh-pages`.
    
    Senza questa opzione, le modifiche resterebbero solo in locale e sarebbe necessario eseguire manualmente il push.
    
- `-f`  
    Forza l'aggiornamento del branch `gh-pages`.
    
    Eventuali contenuti esistenti nel branch vengono sovrascritti con i file presenti nella directory specificata, anche in presenza di conflitti o differenze non sincronizzate.
    
- `docs`  
    Specifica la directory che contiene il sito statico generato da Quarto. Il contenuto di questa directory viene pubblicato nel branch `gh-pages`.
## Link

[Markdown syntax in Quarto](./Markdown%20syntax%20in%20Quarto.md)

