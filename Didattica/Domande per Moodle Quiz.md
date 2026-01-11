---
title: Domande per Moodle Quiz
modificationDate: 2025-06-14 07:50
tags:
  - teaching
  - moodle
---
## Prompt GPT

Devo generare domande a scelta multipla da utilizzare in Moodle, nel formato GIFT (.gift).

Requisiti delle domande:

- Ogni domanda deve avere 5 alternative di risposta.
- Deve esserci una sola risposta corretta.
- La risposta corretta vale +1 punto.
- Ogni risposta errata vale -0.25 punti.
- La risposta non data vale 0 punti (valore di default in Moodle).
    
Per ogni domanda voglio includere un feedback complessivo, che verra' mostrato allo studente solo dopo la chiusura del quiz.

In tutta questa chat NON devono essere usati simboli diversi da quelli ASCII.

Devi creare un file scaricabile, leggibile da Moodle, nel formato .gift.

Qui sotto e' riportato un esempio della sintassi GIFT da utilizzare.

```markdown
::Grid_BB_1::
In uno studio sull'efficacia di un training cognitivo, prima dell'esperimento si assume che la probabilita' di successo sia distribuita come Beta(2, 2). Dopo aver osservato 6 successi su 10 tentativi, qual e' il valore a posteriori piu' probabile (MAP)?
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

1. Si genera un file con estensione .gift che contiene tutte le domande.
2. Per ogni risposta errata va specificata la penalizzazione, ad esempio:  
    ~%-25%0.8000
3. Il feedback complessivo deve essere inserito dopo la riga "#### FEEDBACK" e prima della chiusura della parentesi graffa }.
4. 
Il file .gift cosi' creato puo' essere importato in Moodle seguendo questi passaggi:

- Accedere al Deposito delle domande.
- Selezionare la categoria genitore desiderata.
- Andare su Domande / Categorie.
- Creare una nuova categoria (che sara' figlia della categoria selezionata).
- Importare il file .gift nella categoria appena creata.

## Sintassi e note importanti

**NB:** Usare sempre una penalizzazione di 0.25 per le risposte sbagliate.
**NB:** Nella sintassi GIFT di Moodle si possono usare le lettere accentate italiane (è, ò, à, ì, ù).

NB: Nel formato .gift utilizzato da Moodle non esiste un supporto nativo per la formattazione di blocchi di codice come in Markdown o HTML. Tuttavia, e' possibile includere codice R come semplice testo nel corpo della domanda o nel feedback, a condizione che:

1. Si usino solo caratteri ASCII.
2. Non si utilizzino backtick o sintassi Markdown.
3. Il codice sia inserito come testo preformattato, ad esempio rientrato o delimitato con righe guida (come commenti o linee con ###).

NB: Se in una risposta compare il simbolo "=", questo deve essere preceduto dal carattere di escape "" (cioe' "\=").

Esempio:

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

