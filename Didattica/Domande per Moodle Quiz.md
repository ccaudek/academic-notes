---
type: Zettel
title: Domande per Moodle Quiz
description: null
modificationDate: 2025-06-14 07:50
tags: [teaching, moodle]
coverImage: null
---

## Prompt GPT

Devo generare delle domande a scelta multipla, con 5 alternative, una sola corretta, da usare in Moodle. Voglio aggiungere il feedback complessivo, che verrà mostrato dopo che lo studente ha chiuso il test. La risposta corretta viene valutata con **+1** punto, qualsiasi risposta errata viene valutatra con **-0.25** punti, e la risposta non data viene valutata con **0** punti (valore di default quando lo studente non risponde). Inoltre, voglio fornire un feedback complessivo che verrà mostrato dopo la chiusura del Quiz. In tutta questa chat NON usare simboli diversi da quelli ASCII. Ti chiedo di crere un file **scaricabile**. Il file deve essere leggibile da Moodle in formato .gift. Un esempio della sintassi è mostrato qui sotto.

```markdown
::Grid_BB_1::
In uno studio sull'efficacia di un training cognitivo, prima dell'esperimento si assume che la probabilità di successo sia distribuita come Beta(2, 2). Dopo aver osservato 6 successi su 10 tentativi, qual è il valore a posteriori più probabile (MAP)?
{
=0.6361
~%-25%0.5000
~%-25%0.4000
~%-25%0.7000
~%-25%0.8000
#### FEEDBACK
Codice R:
p_grid <- seq(0, 1, length.out=10000)
prior <- dbeta(p_grid, 2, 2)
likelihood <- dbinom(6, size=10, prob=p_grid)
posterior <- prior * likelihood
p_grid[which.max(posterior)]
}

```

## Procedura

Prima si genera un file .gift che contiene gli esercizi. Sopra c'è un esempio. Si deve specificare la penalizzazione per le risposte sbagliate, per esempio, ~%-25%0.8000. Il feedback, dopo i #### va inserito prima della chiusura della parentesi graffa.

Il file così creato può essere importato in Moodle. È necessario andare su Deposito delle domande. Da lì si sceglie la categoria genitore. Poi, si seleziona Domande/Categorie, per esempio. E da quella pagina si può generare una nuova categoria. La nuova categoria sarà figlia della categoria dalla quale si è scelto Domande/Categorie. A questo punto si può importare il file .gift.

### Sintassi

**NB: Usare la penalizzazione di 0.25 per le risposte sbagliate**.

**NB:** nella sintassi GIFT di Moodle si possono usare **le lettere accentate italiane**, come è, ò, à, ì, ù**.**

**NB:** Nel formato `.gift` utilizzato da Moodle, **non esiste un supporto nativo per la formattazione di blocchi di codice**, come quelli che normalmente useresti in Markdown (con triple backtick `````) o HTML. Tuttavia, puoi **includere codice R nel testo** come parte del corpo della domanda o del feedback, a condizione che:

1. Usi solo **caratteri ASCII semplici**.

2. Non usi backtick o markdown.

3. Il codice sia inserito come **testo preformattato**, magari rientrato o delimitato con righe guida (es. con commenti o linee `###`).

**NB: se nella risposta di una domanda si usa il simbolo "=", va preceduto da "\", ovvero "\=".** Per esempio:

```markdown
::DiffProp_Theo_01::
Qual e' l'ipotesi nulla per un test sulla differenza tra due proporzioni?
{
=H0: p1 - p2 \= 0
~%-25%H0: p1 \= 1
~%-25%H0: p1 maggiore di p2
~%-25%H0: p1 - p2 diverso da 0
~%-25%H0: p1 \= p1_stimato
#### FEEDBACK
L'ipotesi nulla piu' comune e' che le due proporzioni siano uguali, quindi p1 - p2 = 0.
}
```


