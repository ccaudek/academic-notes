---
title: Markdown syntax in Quarto
description: Tips to use Markdown in Quarto notebooks
modificationDate: 2025-12-11
tags:
  - quarto
  - teaching
  - l24
---
# Callout Blocks

```markdown
::: {.callout-note}
Note that there are five types of callouts, including:
`note`, `warning`, `important`, `tip`, and `caution`.
:::
```

---

### Callout con titolo

```markdown
::: {.callout-tip title="In questo capitolo imparerai a"}
- calcolare proporzioni e tabelle di contingenza
- costruire grafici a barre
:::
```

## Collapsed Callout

```markdown
::: {.callout-tip title="Soluzioni" collapse="true"}

:::
```

```markdown
::: {.callout-important title="Problemi" collapse="true"}

:::
```

## Cross-referencing

Cross-references make it easier for readers to navigate your document by providing numbered references and hyperlinks to various entities like figures and tables. Every cross-referenceable entity requires a label (unique identifier prefixed with type e.g. `#fig-element`) and caption (description). The man page is [here](https://quarto.org/docs/authoring/cross-references.html#theorems-and-proofs).

### Equation cross-referencing

Provide an `#eq-` label immediately after an equation to make it referenceable. For example:

```markdown
Tutti conosciamo la media aritmetica di $\{x_1, x_2, \dots, x_n\}$, ovvero il numero reale $\bar{x}$ definito da

$$
\bar{x}=\frac{1}{n}\sum_{i=1}^n x_i.
$$ {#eq-mean}

Nell'@eq-mean abbiamo usato ...
```

### Section cross-referencing

La cross-reference alla sezione `#sec-mass-prob` si ottiene con `@sec-mass-prob`:

```markdown
# Funzione di massa di probabilità {#sec-mass-prob}

... come discusso nella @sec-mass-prob ...
```

Note that when using section cross-references, you will also need to enable the `number-sections` option (so that section numbering is visible to readers).

### Call-out e cross-referencing per Esercizi ed Esempi

Esempi di call-out e cross-referencing per **Esempi** e **Esercizi** sono i seguenti:

```markdown
The first example is @exm-1:

::: {#exm-1}
This should be Example 1.1.
:::

It is followed by the first exercise, @exr-1:

::: {#exr-1}
This should be Exercise 1.2.
:::
```

Approfondimento nel seguente [link](https://stackoverflow.com/questions/73288264/shared-counter-in-quarto-for-exercises-examples-etc).

### Call-out Definizione

Il call-out **Definizione** si specifica nel modo seguente:

```text
::: {#def-}
Sia $Y$ è una variabile casuale discreta che assume i valori $y_1, \dots, y_n$ con distribuzione $P(Y = y_i) = p(y_i)$. Per definizione il *valore atteso* di $Y$, $\mathbb{E}(Y)$, è

$$
\mathbb{E}(Y) = \sum_{i=1}^n y_i \cdot p(y_i).
$$ {#eq-expval-discr}
:::
```

---

## Esempi, esercizi e soluzioni

Gli esercizi e le soluzioni si scrivono nel modo seguente. Questo è il testo dell'**esercizio**:

```markdown
::: {#exr-prob-cond-1}
Da un mazzo di 52 carte (13 carte per ciascuno dei 4 semi) ne viene estratta una in modo casuale. Qual è la probabilità che esca una figura di cuori? Sapendo che la carta estratta ha il seme di cuori, qual è la probabilità che il valore numerico della carta sia 7, 8 o 9?
:::
```

Questa è la **soluzione**:

```markdown
::: solution
Ci sono 13 carte di cuori,
:::
```

---

Per il callout-block di un **esempio**, usiamo `::: {#exm-}`.

## Callout blocks

There are five different types of callout blocks available: `note`, `warning`, `important`, `tip`, `caution`. For details, follow this [link](https://quarto.org/docs/authoring/callouts.html).

### Syntax

```markdown
::: {.callout-note}
Note that there are five types of callouts, including: `note`, `warning`, `important`, `tip`, and `caution`.
:::
```

---

## LaTeX

In $\LaTeX$, `R` si scrive `\mathsf{R}`.

---

## Tables

È possibile formattare le tabelle Markdown con il pacchetto `kableExtra`:

```r
tibble(z, pz, cum_prob) |> 
  kbl() |> 
  kable_paper("hover", full_width = FALSE) |> 
  kable_styling(bootstrap_options = c("striped", "hover", "condensed"))
```

Oppure è possible crearle "manualmente":

```markdown
|Simbolo          | Nome           | È qualcosa che conosciamo?     |
|:----------------|:-------------|:--------------------|
|$s$              |Deviazione standard del campione    |Sì, la calcoliamo dai dati grezzi |
|$\sigma$         |Deviazione standard della popolazione  | No, tranne in casi particolari o nelle simulazioni  |
: {tbl-colwidths="[10, 40, 50]"}
```

**Nota:** l'istruzione nell'ultima riga consente di determinare in maniera relativa l'ampiezza delle colonne.

## Figures in pdf, png, jpeg

```markdown
::: {#fig-like}
![](../../figures/test.png){width="80%"}

Funzione di verosimiglianza nel caso di 7 successi in 10 prove Bernoulliane (pannello di sinistra), di 70 successi in 100 prove (pannello centrale) e di 700 successi in 1000 prove (pannello di destra).
:::
```

## Impostazioni per-chunk raccomandate

Nel .qmd, per grafici ggplot:

```shell
#| out-width: 100%
#| fig-cap: "Relazione tra NA e trait."
```

Per immagini raster (fotografie/heatmap):

```shell
#| fig-format: png
#| dpi: 144
#| out-width: 100%
```

---

### In `_quarto.yml`

- **Specificare dimensioni fisse delle figure in HTML**: in generale **no**; meglio responsive + `out-width`, lasciando le dimensioni fisse al profilo **PDF**.

- **Passare a** `svg` **per i grafici** in HTML; tenere PNG solo dove davvero serve raster.

### Figure cross-reference:

```markdown
Vedi la @fig-my-label
```

### Figura con aspect ratio 1

~~~
```{r fig.asp=1}

```
~~~

oppure

~~~
```r
#| fig-asp: 1
#| fig-width: 6
#| fig-height: 6
```
~~~

## Stringhe che non devono andare a capo

Per blocchi di testo che devono rimanere uniti, puoi avvolgerli in uno `<span>` e applicare `white-space: nowrap;` tramite CSS. 

Nel file `.qmd`: 

```markdown
Questo è un testo <span class="no-break">(che non deve mai andare a capo)</span>.
```

Nel tuo file CSS (`style.css` o simile):

```css
.no-break {
    white-space: nowrap;
}
```

## Colori Okabe-Ito nel pacchetto `see`

```markdown
scale_fill_okabeito() 
```

## Convert LaTeX table in Markdown

Online tool for converting $\LaTeX$ table in markdown [here.](https://pandoc.org/try/)

# R in LaTeX

In $\LaTeX$, $\mathsf{R}$ si scrive `\mathsf{R}`

