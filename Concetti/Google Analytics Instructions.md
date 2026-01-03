---
type: Zettel
title: Google Analytics Instructions
description: null
modificationDate: 2025-01-29 08:52
tags: [teaching, research]
coverImage: null
---

# Aggiungere una pagina web

Per aggiungere Google Analytics alla tua pagina web personale, segui questi passaggi:

1. Accedi a Google Analytics

- Vai su [https://analytics.google.com/](https://analytics.google.com/)

- Effettua il login con il tuo account Google

1. Crea una nuova proprietà

- Nella schermata principale, clicca su "Aggiungi proprietà"

- Inserisci il nome del tuo sito web ([https://ccaudek.github.io/](https://ccaudek.github.io/))

- Seleziona le impostazioni appropriate per l'industria e la zona oraria

1. Ottieni il codice di tracciamento

- Dopo aver creato la proprietà, Google ti fornirà un codice di tracciamento JavaScript (tag G-)

- Il codice avrà un aspetto simile a:

    ```html
    <!-- Google tag (gtag.js) -->
    <script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
    <script>
      window.dataLayer = window.dataLayer || [];
      function gtag(){dataLayer.push(arguments);}
      gtag('js', new Date());
      gtag('config', 'G-XXXXXXXXXX');
    </script>
    ```

1. Aggiungi il codice al tuo sito GitHub Pages

- Apri il file `_layouts/default.html` o `index.html` del tuo repository

- Incolla il codice di tracciamento appena prima del tag `</head>`

1. Commit e Push

- Salva le modifiche

- Fai commit e push sul tuo repository GitHub

Dopo questi passaggi, Google Analytics inizierà a tracciare il traffico del tuo sito web.

# Locate Tracking Tag

To find the tracking tag in Google Analytics:

1. Go to Admin section

2. Click on "Data Streams" under the Property column

3. Select "Web" data stream

4. You'll find the Measurement ID (starts with G-) there

5. Click "View tag instructions" to see the full tracking code

The code will look like:

```html
<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

# Add the Google Analytics tag to `_quarto.yml`

Add the Google Analytics tag "G-K1F64JCQ7Q" to the `_quarto.yml` file under the `website:` section with `google-analytics:`. This means Quarto will automatically inject the tracking script into all pages.



