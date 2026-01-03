---
title: Comprimere e convertire .mov
description:
modificationDate: 2025-09-23 16:49
tags:
  - code
---
# File QuickTime

Con i file `.mov` di QuickTime ci sono alcune strade efficaci:

---

## 🔧 1. Esporta con QuickTime stesso (semplice ma limitato)

- Vai su **File → Esporta come → 720p o 1080p**.

- QuickTime ricodifica il video in H.264 con un bitrate più basso → file più leggero.

- Svantaggio: non puoi controllare bene i parametri (bitrate, qualità).

---

## 🔧 2. Usa **HandBrake** (gratuito, interfaccia grafica)

- Scarica HandBrake ([https://handbrake.fr](https://handbrake.fr)).

- Apri il tuo `.mov`.

- Scegli il preset **“Fast 1080p30”**.

- Imposta formato di output **.mp4**.

- Puoi regolare:

    - **Constant Quality**: un valore tra 20–23 è un buon compromesso (più basso = più qualità, ma file più pesante).

    - **Web Optimized** (se devi caricarlo online).

- Risultato: file molto più leggero, con perdita di qualità minima.

---

## 🔧 3. Usa **ffmpeg** (rapido e preciso da terminale)

Se vuoi controllo totale:

```bash
ffmpeg -i input.mov -vcodec libx264 -crf 23 -preset veryslow -acodec aac output.mp4
```

- `-crf`: qualità costante (da 18 = molto alta a 28 = bassa; 23 è un buon compromesso).

- `-preset`: influenza velocità/compressione (da `ultrafast` a `veryslow`; più lento = file più piccolo a parità di qualità).

- `-acodec aac`: converte l’audio in AAC, standard per MP4.

---

## 💡 Consiglio pratico

- Se vuoi una **soluzione rapida e zero smanettamenti** → usa **HandBrake**.

- Se sei a tuo agio con il Terminale → usa **ffmpeg** con `-crf 23` e `-preset slow`: ottieni file piccoli e qualità ottima.

---

Ti lascio **2 comandi ffmpeg** già pronti (ottimi per screencast con testo + voce). Scegli A se vuoi mantenere la risoluzione, B se vuoi ridurre a 1080p per alleggerire molto.

---

## A) Mantieni la risoluzione originale (qualità alta, file più leggero)

```bash
ffmpeg -i input.mov \
  -c:v libx264 -preset slow -crf 20 -r 30 -pix_fmt yuv420p \
  -movflags +faststart \
  -c:a aac -b:a 128k \
  output.mp4
```

**Perché funziona bene per screencast**

- `-crf 20` = ottimo compromesso qualità/peso (più alto = più leggero, p.es. 22–24).

- `-preset slow` = comprime meglio a parità di qualità (puoi usare `medium` se hai fretta).

- `-r 30` = frame rate standard per slide/screencast.

- `-pix_fmt yuv420p` + `-movflags +faststart` = massima compatibilità (web, player).

---

## B) Riduci a 1080p (molto più leggero, qualità ancora ottima)

```bash
ffmpeg -i input.mov \
  -vf "scale=-2:1080:flags=lanczos" \
  -c:v libx264 -preset slow -crf 22 -r 30 -pix_fmt yuv420p \
  -movflags +faststart \
  -c:a aac -b:a 96k \
  output_1080p.mp4
```

**Note**

- `scale=-2:1080:flags=lanczos` = downscale nitido mantenendo proporzioni; `-2` forza larghezza compatibile (multiplo di 2).

- `-crf 22` è un filo più compresso (puoi scendere a 20 se il testo ti sembra un po’ “morbido”).

---

### Suggerimenti rapidi (per scegliere i parametri)

- **Testa prima 30–60 secondi**:
aggiungi `-t 60` e valuta peso/qualità prima di processare tutto.

- **Molto testo fine?** Usa `-crf 18–20`.
**Più leggerezza?** prova `-crf 23–24`.

- **Slide quasi statiche?** puoi aggiungere `-tune stillimage` per comprimere meglio (se il video è davvero poco dinamico):

    ```bash
    ... -c:v libx264 -tune stillimage -preset slow -crf 20 ...
    ```

- **Audio**: 96–128 kbps AAC è più che sufficiente per voce.

---

### Installazione veloce (se ti serve)

```bash
brew install ffmpeg
```

Se vuoi, dimmi **dimensione e risoluzione del file originale** (es. 2880×1800, durata, MB) e ti ottimizzo i parametri per arrivare a un peso-target (es. “~100 MB per 30 minuti”).

