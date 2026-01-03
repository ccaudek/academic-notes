---
type: Zettel
title: Procedura per Importare Esami da Excel
description: null
modificationDate: 2025-06-19 05:02
tags: [teaching, esami, firma_digitale]
coverImage: null
---

Questa nota descrive la procedura per importare esami da un file Excel nel portale della firma digitale UniFi.

## **1. Preparazione del file condiviso con gli studenti**

- Ordinare gli studenti in ordine alfabetico (cognome-nome)

- Verificare la presenza delle seguenti colonne:

    - **Matricola** (obbligatoria, formato numerico)

    - **Cognome e Nome** (consigliato per verifica incrociata)

    - **Voto/Esito** (formati accettati: `IDO` per idoneità, `30L` per 30 e lode)

    - **Data esame** (formato: `GG/MM/AA` es. `18/06/25`)

## **2. Verifica Preliminare sul Portale**

1. Accedere al portale della firma digitale

2. Inserire manualmente l'esito di **uno studente campione**

3. Verificare che i dati siano visualizzati correttamente

4. Esportare il template Excel dal portale (questo sarà il nostro file di lavoro)

## **3. Compilazione del File Excel**

**Sequenza operativa consigliata:**

1. **Inserimento voti**:

    - Utilizzare la colonna specificata dal template

    - Formati speciali:

        - `IDO` per idoneità

        - `30L` per 30 e lode

        - Valori numerici per altri voti (es. `28`, `25`)

2. **Inserimento date**:

    - Formato obbligatorio: `GG/MM/AA` (es. `18/06/25`)

    - **Pro-tip**: Per copiare una data senza incremento:

        1. Selezionare la cella con la data

        2. Tenere premuto **Ctrl** (Windows/Linux) o **⌘** (Mac)

        3. Trascinare il quadratino in basso a destra

3. **Domande d'esame** (ultimo step):

    - Inserire nell'apposita sezione del template

    - Verificare la formattazione richiesta dal portale

## **4. Importazione Finale**

1. Tornare sul portale della firma digitale

2. Selezionare l'opzione "Importa da Excel"

3. Caricare il file completato

4. Verificare gli esami importati

**Nota**: Consigliamo sempre di conservare una copia del file originale condiviso con gli studenti e del file esportato dal portale per eventuali verifiche future.


