---
type: Zettel
title: Colori omogenei nei grafici
description: null
modificationDate: 2025-09-30 09:47
tags: [coding, UTET]
coverImage: null
---

### Scelte consigliate (semplici e robuste)

- **Distribuzione singola (un solo scenario)**
Usa **blu** Tol come default:

    - `fill = modern_palette$blue` `#4477AA`

    - `color = modern_palette$white` per il bordo

    - `alpha = 0.8`

- **Confronto di due scenari** (es. *prior vago* vs *prior informativo*)
Mappa i significati a colori costanti lungo tutto il manuale:

    - *prior vago* → **rosso** `modern_palette$red` `#EE6677` (segnale “warning”)

    - *prior informativo* → **verde** `modern_palette$green` `#228833`

    - Bordo sempre `modern_palette$white`, `alpha = 0.65–0.75`, `position = "identity"` per istogrammi sovrapposti oppure **facet** per evitare clutter.

- **Confronto di 3+ scenari**
Usa `palette_discrete` (Tol) nell’ordine predefinito; se vuoi mantenere la semantica sopra, specifica una scala manuale con nomi.

### Snippet pronti

**1) Istogramma “standard” coerente**

```r
ggplot(df, aes(x = y)) +
  geom_histogram(
    aes(y = after_stat(density)),
    bins = 11,
    fill = modern_palette$blue,
    color = modern_palette$white,
    alpha = 0.8,
    linewidth = 0.2
  ) +
  scale_x_continuous(breaks = 0:10)
```

**2) Due scenari, colori semantici fissi**

```r
chapter_cols <- c(
  "Prior vago"        = modern_palette$red,   # #EE6677
  "Prior informativo" = modern_palette$green  # #228833
)
ggplot(df_long, aes(x = y, fill = scenario)) +
  geom_histogram(
    aes(y = after_stat(density)),
    bins = 11,
    position = "identity",
    alpha = 0.7,
    color = modern_palette$white,
    linewidth = 0.2
  ) +
  scale_fill_manual(values = chapter_cols) +
  scale_x_continuous(breaks = 0:10) +
  legenda_in_alto
```

**3) Densità sovrapposte (quando preferisci evitare barre sovrapposte)**

```r
ggplot(df_long, aes(x = y, color = scenario)) +
  geom_density(linewidth = 1) +
  scale_color_manual(values = chapter_cols) +
  nessuna_griglia + legenda_in_alto
```

### Dettagli utili

- Mantieni **bordo bianco** sulle barre: tiene il grafico pulito su sfondo chiaro e rispetta il tuo tema.

- Usa **facet** (`+ facet_wrap(~scenario, ncol = 1)`) quando le sovrapposizioni diventano poco leggibili.

- Per i grafici `bayesplot::ppc_*` hai già `color_scheme_set("blue")` nel bootstrap: va benissimo; se vuoi segnalare scenari “problematici”, prima del plot puoi temporaneamente usare `color_scheme_set("red")` e poi ripristinare.

Con queste scelte avrai istogrammi coerenti, leggibili e con un **significato cromatico stabile** in tutto il manuale.

