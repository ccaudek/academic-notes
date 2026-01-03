---
type: Zettel
title: Inserire video in Quarto
description: null
modificationDate: 2025-09-23 17:07
tags: []
coverImage: null
---

Mi chiedo se sia possibile inserire in Quarto un video che dipende da un .mp4 file salvato su un Google Drive.

Con Google Drive ci sono due strade, e una è molto più affidabile dell’altra.

---

## Opzione consigliata (affidabile): **iframe “preview” di Google Drive**

Drive non fornisce un link MP4 “pulito” e stabile per l’`<video>` HTML; però offre un player embeddabile via iframe.

**Passi:**

1. Carica il video su Drive e imposta la condivisione su **Chiunque abbia il link → Visualizzatore**.

2. Apri il video in Drive → **⋮ → Apri in una nuova finestra** → di nuovo **⋮ → Incorpora elemento (Embed item)** → copia il codice `<iframe>`. (Se non vedi “Incorpora”, apri in nuova finestra: appare lì.) (Google Help)

**In Quarto (.qmd):** incolla l’iframe in un blocco HTML grezzo:

```markdown
::: {style="aspect-ratio:16/9"}
<iframe
  src="https://drive.google.com/file/d/FILEID/preview"
  width="100%" height="100%" style="border:0"
  allow="autoplay; fullscreen" allowfullscreen>
</iframe>
:::
```

Questo funziona bene nelle pagine **HTML** generate da Quarto (l’iframe è accettato). (Quarto)

---

## Opzione possibile ma fragile: **link diretto al file MP4**

Quarto supporta anche un URL a un **file .mp4** remoto usando il suo shortcode:

```markdown
{{< video https://.../video.mp4 >}}
```

Funziona perfettamente *se* il server restituisce gli header giusti (MIME type, CORS, range requests). (Quarto)

Con **Google Drive** i “finti diretti” tipo
`https://drive.google.com/uc?export=download&id=FILEID`
spesso rompono autoplay/seek o danno 403/finestre anti-virus su file grandi: non è garantito per l’HTML5 `<video>`. Meglio l’iframe “preview”. (Guide e thread su “direct link” esistono, ma non sono stabili per embedding pubblico.) (Google Help)

---

## Riassunto pratico

- **Vuoi che “semplicemente funzioni”?** usa **iframe** `.../file/FILEID/preview` dentro il .qmd.

- **Vuoi controllare pienamente player e sorgente** `<video>`**?** ospita l’MP4 su un server statico (es. nel tuo sito Quarto/GitHub Pages o un CDN) e usa `{{< video https://.../file.mp4 >}}`. (Quarto)

Se vuoi, dimmi **il link Drive** e ti preparo **l’esatto snippet .qmd** pronto-incolla (iframe o shortcode) per la tua pagina.

