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
- distribuzione campionaria della media, Teorema Centrale del Limite;
- calcolo di probabilità mediante l’uso delle tavole della distribuzione normale;
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

Sia $X = {2, -1, 5}$ un insieme di tre osservazioni.  
Calcolare  
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

Perfetto. Ti propongo **due quesiti distinti**, entrambi nel **formato identico** agli altri (5 alternative, 1 corretta), calibrati per:

- corso triennale di psicologia;
    
- pre-esame selettivo ma oggettivo;
    
- uno **puramente computazionale**;
    
- uno di **interpretazione concettuale**, ma non opinabile.
    

---

## Quesito – Statistica descrittiva (calcolo della deviazione standard)

Un campione di punteggi a un test di attenzione è costituito dai valori:  
[  
X = {4,; 6,; 10}.  
]

Calcolare la **deviazione standard campionaria** (con denominatore (n)).

A) 2  
B) (\sqrt{6})  
C) (\sqrt{8})  
D) (\sqrt{12})  
E) 4

**Svolgimento atteso (minimo):**  
(\bar X = \frac{4+6+10}{3} = \frac{20}{3});  
[  
\frac{1}{3}\left[(4-\bar X)^2+(6-\bar X)^2+(10-\bar X)^2\right]=\frac{24}{3}=8;  
\quad \sigma=\sqrt{8}.  
]

✅ **Risposta corretta: C**

---

## Quesito – Statistica descrittiva (interpretazione della deviazione standard)

Due gruppi di soggetti svolgono lo stesso test di memoria.  
I due gruppi hanno **la stessa media**, ma il Gruppo A ha deviazione standard pari a 5, mentre il Gruppo B ha deviazione standard pari a 10.

Quale delle seguenti affermazioni è **corretta**?

A) Il Gruppo B ha una media più elevata del Gruppo A  
B) I punteggi del Gruppo A sono più dispersi rispetto a quelli del Gruppo B  
C) I punteggi del Gruppo B sono più dispersi rispetto a quelli del Gruppo A  
D) Nel Gruppo A i punteggi sono tutti uguali  
E) Nel Gruppo B non è possibile calcolare la media

✅ **Risposta corretta: C**

---

### Nota didattica (per te)

Questa coppia funziona molto bene perché:

- il primo quesito seleziona chi **sa calcolare davvero**;
    
- il secondo elimina chi **ripete definizioni senza capirle**;
    
- nessuno dei due è attaccabile sul piano interpretativo.
    

Se vuoi, al prossimo passo posso:

- riformulare il primo quesito con **frequenze** (ancora più psicologico),
    
- oppure preparare **distrattori Moodle ancora più “cattivi”** (errori tipici reali).

### Quesito 5 – Probabilità di base

Un evento $A$ ha probabilità $P(A)=0.3$.  Un evento $B$ è tale che $P(B\mid A)=0.5$ e $P(B\mid A^c)=0.2$.  Calcolare $P(B)$.

A) 0.23  
B) 0.26  
C) 0.29  
D) 0.32  
E) 0.35

✅ Risposta corretta: **B**

---

### Quesito 6 – Probabilità condizionata

Siano (A) e (B) due eventi con (P(A)=0.4), (P(B)=0.5) e (P(A\cap B)=0.2).  
Calcolare (P(A\mid B)).

A) 0.2  
B) 0.4  
C) 0.5  
D) 0.6  
E) 0.8

✅ Risposta corretta: **B**

---

### Quesito 7 – Distribuzione della media campionaria

Una popolazione ha media (\mu=10) e deviazione standard (\sigma=2).  
Calcolare la **deviazione standard della media campionaria** per (n=16).

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

---

## Nota sullo svolgimento

Per ciascun quesito è richiesto uno svolgimento che renda chiaro:

- il modello utilizzato,
    
- le formule applicate,
    
- i passaggi di calcolo essenziali.
    

La sola risposta numerica **non è sufficiente**.

---

### Chiusura franca

Con questo materiale:

- gli studenti **sanno esattamente** cosa li aspetta;
    
- l’80% è percepito come standard, non come arbitrarietà;
    
- sei **coperto didatticamente e istituzionalmente**.
    

Se vuoi, al prossimo passo posso:

- aiutarti a **trasformare questo esempio in una banca di quiz Moodle**,
    
- oppure calibrare le **prove in itinere** in modo coerente con questo livello iniziale.