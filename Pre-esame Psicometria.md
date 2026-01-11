---
tags:
  - teaching
modificationDate: 11/01/2025
---
# Syllabus: pre-esame
## Pre-esame di verifica delle conoscenze di base

Per poter sostenere le prove in itinere del corso è obbligatorio superare un **pre-esame di verifica delle conoscenze di base**.  Il pre-esame ha lo scopo di accertare il possesso degli strumenti minimi di calcolo e di probabilità necessari per seguire proficuamente il corso di Analisi dei Dati con orientamento bayesiano.

Il pre-esame **non contribuisce al voto finale** e ha esclusivamente esito _superato / non superato_.

### Contenuti del pre-esame

Il pre-esame verte sui seguenti argomenti:

- sommatorie elementari;
- statistica descrittiva (media, varianza, deviazione standard);
- elementi di base di teoria della probabilità;
- distribuzione campionaria della media, legge della probabilità totale, regole della somma e del prodotti, Teorema del Limite Centrale;
- calcolo di probabilità mediante l’uso delle tavole della distribuzione normale e della distribuzione t di Student;
- regole elementari di calcolo combinatorio;
- proprietà delle scale di misura.

### Modalità di svolgimento

- **Durata:** 30 minuti
- **Strumenti consentiti:** calcolatrice
- **Struttura:**
    - 10 quesiti a risposta numerica, somministrati tramite quiz Moodle a scelta multipla (5 alternative, una sola corretta);
    - consegna obbligatoria di un **foglio cartaceo** contenente lo svolgimento dettagliato di ciascun esercizio.
### Valutazione e superamento

Il pre-esame si considera **superato** se e solo se **entrambe** le seguenti condizioni sono soddisfatte:

1. punteggio al quiz Moodle **maggiore o uguale a 8/10**;
2. per **ciascun quesito risolto correttamente nel quiz Moodle** è presente uno svolgimento:

    - coerente con la risposta selezionata,
    - completo nei passaggi essenziali,
    - leggibile e logicamente ricostruibile.
        
In caso di svolgimento mancante, gravemente incompleto o incoerente con la risposta selezionata, il pre-esame è considerato **non superato**, indipendentemente dal punteggio ottenuto nel quiz Moodle.

### Seconda possibilità

È prevista **una seconda possibilità** di sostenere il pre-esame, con modalità, contenuti e criteri di valutazione identici.

### Conseguenze del mancato superamento

Gli studenti che non superano il pre-esame **non possono sostenere le prove in itinere** e dovranno sostenere l’esame secondo le modalità previste per i non frequentanti.

# Esempio del pre-esame

## Esempio di pre-esame

**Durata:** 30 minuti  
**Strumenti consentiti:** calcolatrice  
**Istruzioni:**  
Per ciascun quesito selezionare **una sola risposta**. Riportare sul foglio cartaceo lo svolgimento dettagliato di ogni esercizio.

### Quesito 1 – Sommatorie

Sia $X = {2, -1, 5}$ un insieme di tre osservazioni.  Calcolare  
$$
\sum_{i=1}^{3} (X_i - \bar X)^2,  
$$
dove $\bar X$ è la media campionaria.

A) 12  
B) 14  
C) 18  
D) 20  
E) 24

**Svolgimento atteso (minimo):**  
$\bar X = 2$;  
$(2-2)^2 + (-1-2)^2 + (5-2)^2 = 0 + 9 + 9 = 18$.

✅ Risposta corretta: **C**

### Quesito 2 – Scale di misurazione 

Un test psicologico di **umore** assegna a ciascun soggetto un punteggio numerico su una **scala a intervalli**, in cui il valore 0 non rappresenta assenza di umore ma è scelto in modo convenzionale.  
Un ricercatore decide di trasformare i punteggi (X) secondo la relazione  
$$ 
Y = 2X + 10.  
$$

Quale delle seguenti affermazioni è **corretta**?

A) La trasformazione non è ammissibile perché altera i rapporti tra i punteggi  
B) La trasformazione è ammissibile e preserva le differenze tra i punteggi  
C) La trasformazione è ammissibile solo se il valore 0 rappresenta assenza della caratteristica  
D) Dopo la trasformazione è lecito affermare che un soggetto con (Y=40) ha il doppio dell’umore di un soggetto con (Y=20)  
E) Dopo la trasformazione non è più possibile calcolare la media dei punteggi

✅ **Risposta corretta: B**

### Svolgimento atteso (minimo accettabile)

- una scala a intervalli ammette trasformazioni del tipo (Y = aX + b), con (a>0);
- tali trasformazioni **preservano le differenze**, ma non i rapporti;
- l’origine è arbitraria e non ha significato assoluto;
- operazioni come somma, differenza e media restano lecite.
    
👉 Non serve scrivere tutto: bastano 2–3 righe che mostrino che lo studente **sa cosa distingue una scala a intervalli**.

### Quesito 3 – Statistica descrittiva (calcolo della deviazione standard)

Un campione di punteggi a un test di attenzione è costituito dai valori:  
$$
X = {4,\; 6,\; 10}.  
$$

Calcolare la **deviazione standard campionaria** (con denominatore (n)).

A) 2  
B) $\sqrt{6}$ 
C) $\sqrt{8}$ 
D) $\sqrt{12}$  
E) 4

**Svolgimento atteso (minimo):**  
$\bar X = \frac{4+6+10}{3} = \frac{20}{3}$;  
$$ 
\frac{1}{3}\left[(4-\bar X)^2+(6-\bar X)^2+(10-\bar X)^2\right]=\frac{24}{3}=8;  
\quad \sigma=\sqrt{8}.  
$$


---

### Quesito 4 – Statistica descrittiva (SD, scarto tipico e MAD)

In un campione di punteggi a un test psicologico, la **deviazione standard** è pari a 8.  
La **MAD** (deviazione assoluta mediana), calcolata sugli stessi dati, è pari a 6.

Quale delle seguenti affermazioni è **corretta**?

A) La MAD fornisce una stima dello scarto tipico dei punteggi concettualmente diversa, ma coerente con ciò che rappresenta la deviazione standard  
B) La MAD misura lo scarto medio dei punteggi dalla media ed è quindi equivalente alla deviazione standard  
C) La differenza tra MAD e deviazione standard indica necessariamente la presenza di outlier estremi  
D) La deviazione standard non può essere interpretata in termini di scarto tipico  
E) La MAD è una misura di dispersione utilizzabile solo per scale ordinali

✅ **Risposta corretta: A**

### Svolgimento atteso (minimo accettabile)

- la deviazione standard rappresenta uno **scarto tipico** rispetto alla media;
- la MAD è una misura diversa (basata su scarti assoluti dalla mediana) ma fornisce una **descrizione intuitiva** della dispersione;
- valori comparabili indicano coerenza nella descrizione della variabilità dei dati.
    
👉 È sufficiente che emerga l’idea: **misure diverse, stesso fenomeno descritto in modo compatibile**.

### Quesito 5 – Probabilità di base (legge della probabilità totale)

Un evento $A$ ha probabilità $P(A)=0.3$.  
Un evento $B$ è tale che:  
$$ 
P(B \mid A)=0.4, \qquad P(B \mid A^c)=0.2.  
$$

Calcolare $P(B)$.

A) 0.22  
B) 0.24  
C) 0.26  
D) 0.28  
E) 0.30

✅ **Risposta corretta: C**

### Svolgimento (minimo accettabile)

Per la **legge della probabilità totale**:  
$$
P(B)=P(B \mid A)P(A)+P(B \mid A^c)P(A^c).  
$$

Poiché:  
$$ 
P(A^c)=1-P(A)=0.7,  
$$  
si ottiene:  
$$ 
P(B)=0.4\cdot 0.3 + 0.2\cdot 0.7  
= 0.12 + 0.14  
= 0.26.  
$$

Ecco un esercizio **pulito, tipico per psicologia**, perfettamente adatto a **Moodle + svolgimento cartaceo**, sul **valore atteso di una variabile aleatoria discreta**.

---

### Quesito 6 – Valore atteso di una variabile aleatoria discreta

Il punteggio (X) ottenuto da un soggetto a un breve test di attenzione può assumere i seguenti valori:

|(x)|0|1|2|
|---|---|---|---|
|(P(X=x))|0.2|0.5|0.3|

Calcolare il **valore atteso** di (X).

A) 0.9  
B) 1.0  
C) 1.1  
D) 1.3  
E) 1.5

✅ **Risposta corretta: C**

---

### Svolgimento (minimo accettabile)

Per definizione, il valore atteso di una variabile aleatoria discreta è:  
$$
E[X] = \sum_x x,P(X=x).  
$$

Pertanto:  
$$ 
E[X] = 0\cdot 0.2 + 1\cdot 0.5 + 2\cdot 0.3  
= 0 + 0.5 + 0.6  
= 1.1.  
$$

### Quesito 7 – Distribuzione della media campionaria

Una popolazione ha media $\mu=10$ e deviazione standard $\sigma=2$.  
Calcolare la **deviazione standard della media campionaria** per $n=16$.

A) 0.25  
B) 0.5  
C) 1  
D) 2  
E) 4

✅ Risposta corretta: **B**

---

### Quesito 8 – Teorema Centrale del Limite

Sia (\bar X) la media campionaria del quesito precedente.  
Calcolare (P(\bar X > 10.5)) usando l’approssimazione normale.

A) 0.1587  
B) 0.3085  
C) 0.5  
D) 0.6915  
E) 0.8413

✅ Risposta corretta: **A**

---

### Quesito 9 – Uso delle tavole

Sia $Z \sim N(0,1)$.  Calcolare $P(Z < 1.28)$.

A) 0.8000  
B) 0.8500  
C) 0.8997  
D) 0.9250  
E) 0.9500

✅ Risposta corretta: **C**

---

### Quesito 10 – Calcolo combinatorio

In quanti modi distinti si possono scegliere 2 elementi da un insieme di 6?

A) 12  
B) 15  
C) 20  
D) 30  
E) 36

✅ Risposta corretta: **B**

## Nota sullo svolgimento

Per ciascun quesito è richiesto uno svolgimento che renda chiaro:

- il modello utilizzato,
- le formule applicate,
- i passaggi di calcolo essenziali.
    
La sola risposta numerica **non è sufficiente**.
