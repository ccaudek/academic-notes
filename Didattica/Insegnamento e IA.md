
# **PROCEDURA DETTAGLIATA: "EXPLAIN-TO-AI" NEL CORSO DI ANALISI BAYESIANA**

## **TIMELINE DEI 4 COMPITI**

|Compito|Concetto|Timing|Capitoli di riferimento|
|---|---|---|---|
|**1**|Aggiornamento bayesiano|Settimana 4-5|Cap. 8 (Quantificare e aggiornare l'incertezza)|
|**2**|Prior predictive distributions|Settimana 7-8|Cap. 12 (Controllo predittivo a priori)|
|**3**|Posterior predictive distributions|Settimana 10-11|Cap. 13 (Distribuzione predittiva a posteriori)|
|**4**|ELPD e confronto tra modelli|Settimana 14-15|Cap. 44-45 (KL divergence, Model comparison)|

**Razionale**: Questi 4 momenti scandiscono le fasi critiche dell'inferenza bayesiana: _come aggiorniamo_, _come scegliamo le prior_, _come valutiamo il modello_, _come confrontiamo modelli alternativi_.

---

## **STRUTTURA OPERATIVA DI OGNI COMPITO**

Ogni compito segue il ciclo: **Explain → Peer Review → Meta-Analysis → Intervento → Consolidamento**

---

# **COMPITO 1: AGGIORNAMENTO BAYESIANO**

**Timing**: Dopo Cap. 8 | **Durata totale**: 10 giorni

## **FASE 1: Explain-to-AI (giorni 1-3)**

### **Prompt strutturato per gli studenti**

```
CONTESTO: Hai appena finito di studiare il Cap. 8 sul teorema di Bayes.

COMPITO: Spiega all'IA il concetto di "aggiornamento bayesiano" come 
se stessi preparando una micro-lezione per un compagno che era assente.

La tua spiegazione deve includere:
1. Cosa significa "aggiornare" una credenza con nuova evidenza
2. Perché si chiama "bayesiano" (riferimento al teorema di Bayes)
3. Un esempio concreto dalla ricerca psicologica
4. Cosa succederebbe se ricevessimo più evidenza contraddittoria

FORMATO: Dialoga con l'IA. L'IA ti farà domande per chiarire. 
Rispondi con parole tue, non citare il libro.

CONSEGNA: Esporta la trascrizione completa (max 1500 parole) 
e il micro-summary finale dell'IA.
```

### **Prompt per l'IA (inserito nel sistema)**

```
Assumi il ruolo di un tutor socratico per studenti di psicologia 
che stanno imparando statistica bayesiana.

OBIETTIVI:
- Elicitare la comprensione dello studente tramite domande
- Identificare fraintendimenti comuni (es. confondere prior con ipotesi, pensare che Bayes sia "soggettivo arbitrario")
- Non dare soluzioni dirette, ma guidare il ragionamento

DOMANDE CHIAVE DA PORRE:
1. "Cosa distingue l'aggiornamento bayesiano dal test di ipotesi classico?"
2. "Se la prior è molto forte e i dati deboli, cosa succede alla posterior?"
3. "Puoi darmi un esempio numerico semplice (anche inventato) che mostri prior → dati → posterior?"
4. "Cosa significa che la posterior di oggi diventa la prior di domani?"

ALLA FINE: Genera un micro-summary (max 150 parole) che identifica:
- Cosa lo studente ha capito bene
- Dove c'è ancora incertezza
- Eventuali fraintendimenti emersi
```

**Output atteso**:

- Trascrizione con dialogo studente-IA
- Box finale con micro-summary

---

## **FASE 2: Peer Review (giorni 4-6)**

### **Rubrica strutturata per la peer review**

Ogni studente riceve **2 trascrizioni anonime** di compagni e compila:

```
PEER REVIEW - AGGIORNAMENTO BAYESIANO

TRASCRIZIONE #__

1. ACCURATEZZA CONCETTUALE (1-3 frasi)
   Identifica UN'affermazione corretta nella spiegazione del compagno. Spiega perché questa affermazione è accurata.
   
   Esempio di cosa cercare: 
   - Distinzione tra prior e likelihood
   - Ruolo dei dati nell'aggiornamento
   - Sequenzialità dell'apprendimento bayesiano

1. FRAINTENDIMENTO IDENTIFICATO (1-3 frasi)
   C'è un'affermazione che ti sembra imprecisa o confusa?
   Quale? Come la correggeresti?
   
   Fraintendimenti comuni da cercare:
   - "La prior è arbitraria/soggettiva e quindi inaffidabile"
   - "Bayes ci dice quale ipotesi è vera"
   - Confusione tra P(dati|ipotesi) e P(ipotesi|dati)

3. SPIEGAZIONE PIÙ EFFICACE (1-2 frasi)
   Quale metafora/esempio/analogia del compagno ti ha fatto capire 
   meglio il concetto? Perché?

4. DOMANDA ANCORA APERTA (1 frase)
   Dopo aver letto questa spiegazione, quale aspetto dell'aggiornamento bayesiano non ti è ancora chiaro del tutto?
```

**Strumento**: Form Google/Moodle con le 4 sezioni

**Output atteso**:

- Documento di peer review per ogni trascrizione
- Database anonimizzato di tutte le peer review

---

## **FASE 3: Meta-Analisi IA (giorni 7-8)**

### **Prompt per l'IA (analisi batch)**

```
TASK: Analizza le seguenti trascrizioni di studenti che spiegano 
"aggiornamento bayesiano" e le relative peer review.

INPUT:
- 60 trascrizioni studente-IA
- 120 peer review

ANALIZZA IN MODO STRATIFICATO:

A) DALLE TRASCRIZIONI:
   - Identifica misconcezioni ricorrenti (con % di frequenza)
   - Pattern linguistici associati a comprensione solida vs fragile
   - Esempi/analogie più efficaci usati spontaneamente dagli studenti
   
B) DALLE PEER REVIEW:
   - Cosa gli studenti riconoscono come corretto/scorretto (meta-comprensione)
   - Gap tra cosa sanno identificare e cosa sanno spiegare
   
C) DALLE DOMANDE APERTE:
   - Aree di incertezza residua comune
   - Cluster tematici di confusione

OUTPUT RICHIESTO:
Report strutturato (max 2 pagine) con:

1. LIVELLO DI COMPRENSIONE CLASSE
   [Solida >70% | Parziale 40-70% | Fragile <40%]
   
   Concetti compresi:
   - ...
   
   Concetti parziali:
   - ...
   
   Concetti fragili:
   - ...

2. TOP 5 MISCONCEZIONI (con frequenza %)
   3. [Misconcetto] - XX%
      Origine probabile: ...
      Correzione suggerita: ...
   
4. PATTERN LINGUISTICI OSSERVATI
   - Studenti con comprensione solida tendono a...
   - Studenti con difficoltà tendono a...
   
4. ESEMPI/ANALOGIE PIÙ EFFICACI EMERSI
   - "..." (usato da N studenti, riconosciuto come chiaro da M peer reviewers)
   
5. DOMANDE APERTE RICORRENTI
   - [Domanda] - riportata da N studenti
   
6. SUGGERIMENTI DIDATTICI
   - Dedicare tempo a...
   - Esercizio pratico su...
   - Chiarire differenza tra...
   
7. STUDENTI A RISCHIO
   Identificare (in modo anonimo) studenti con:
   - Molteplici misconcezioni sovrapposte
   - Difficoltà a generare esempi concreti
   - Linguaggio vago/evasivo
```

**Output atteso**:

- Report di 2 pagine
- (Opzionale) Dashboard visiva con heatmap concetti solidi/fragili

---

## **FASE 4: Intervento Didattico (giorno 9)**

### **Struttura della lezione correttiva**

**Durata**: 90 minuti

**PARTE 1 (30 min): Fraintendimenti comuni**

- Presento il report meta-analitico (versione anonimizzata)
- "Ecco le 3 misconcezioni più frequenti emerse dalle vostre spiegazioni"
- Per ciascuna:
    - Mostro un esempio reale (anonimo) dalla trascrizione
    - Chiedo alla classe: "Dove sta il problema qui?"
    - Chiarisco con simulazione in R live

**PARTE 2 (30 min): Simulazione interattiva**

```r
# Aggiornamento sequenziale con dati contrastanti
# Simulo situazione emersa nelle domande aperte:
# "Cosa succede se i primi dati supportano un'ipotesi e i successivi la contraddicono?"

library(tidyverse)

# Prior: P(efficacia_farmaco) ~ Beta(2, 2) [debolmente informativa]
# Primi 10 pazienti: 8 guarigioni → posterior1
# Altri 20 pazienti: 6 guarigioni → posterior2

# Mostro graficamente come la posterior si aggiorna
# e perché "pesa" la quantità di evidenza
```

**PARTE 3 (30 min): Co-costruzione esempi**

- In piccoli gruppi (4 persone): progettate un esempio psicologico dove l'aggiornamento bayesiano è rilevante
- Condivisione plenaria: "Peer teaching inverso"

**Materiali condivisi**:

- Slide con i 3 fraintendimenti + correzioni
- Script R commentato della simulazione
- Lista degli esempi/analogie più efficaci emersi dalle trascrizioni

---

## **FASE 5: Consolidamento (giorno 10)**

### **Seconda spiegazione (breve)**

```
COMPITO: Rispiega all'IA il concetto di "aggiornamento bayesiano"
in MASSIMO 300 parole.

Questa volta:
- Sii più preciso sui punti critici emersi in classe
- Usa almeno UN esempio concreto (anche quello discusso in aula)
- Evita le 3 misconcezioni principali che abbiamo identificato

L'IA confronterà automaticamente questa spiegazione con la tua prima.
```

### **Prompt per l'IA (valutazione comparativa)**

```
Confronta la spiegazione 1 (pre-intervento) e spiegazione 2 (post-intervento) dello stesso studente.

VALUTA:
1. Miglioramento concettuale (scala 1-5)
2. Precisione linguistica (scala 1-5)
3. Capacità di generare esempi concreti (sì/no)
4. Persistenza di misconcezioni precedenti (elenco)
5. Emergenza di nuove difficoltà (se presenti)

OUTPUT: Feedback personalizzato (max 150 parole) che evidenzia:
- Cosa è migliorato significativamente
- Cosa è ancora da consolidare
- Suggerimento per approfondire (es. "Prova a simulare in R un caso con prior molto informativa vs poco informativa")
```

**Output finale**:

- Feedback individuale generato dall'IA
- Report aggregato per il docente: % di miglioramento medio post-intervento

---

# **PORTFOLIO INDIVIDUALE**

Al termine dei 4 compiti, ogni studente ha:

```
PORTFOLIO_STUDENTE/
│
├── COMPITO_1_Aggiornamento/
│   ├── trascrizione_1_pre
│   ├── peer_review_su_compagno_A
│   ├── peer_review_su_compagno_B
│   ├── trascrizione_2_post
│   └── feedback_IA_confronto
│
├── COMPITO_2_Prior_Predictive/
│   └── [stessa struttura]
│
├── COMPITO_3_Posterior_Predictive/
│   └── [stessa struttura]
│
└── COMPITO_4_ELPD_ModelComparison/
    └── [stessa struttura]
```

---

# **COMPITO 2: PRIOR PREDICTIVE DISTRIBUTIONS**

**Timing**: Dopo Cap. 12 | **Durata**: 10 giorni

## **FASE 1: Explain-to-AI**

### **Prompt strutturato**

```
CONTESTO: Hai studiato il Cap. 12 sul controllo predittivo a priori.

COMPITO: Spiega all'IA cosa sono le "prior predictive distributions" 
e perché sono utili nel workflow bayesiano.

La tua spiegazione deve includere:
1. Differenza tra prior parametrica e prior predictive distribution
2. Cosa significa "simulare dati prima di osservare dati reali"
3. Un esempio concreto: come useresti una prior predictive per 
   verificare se la tua prior è ragionevole
4. Cosa succederebbe se la prior predictive generasse dati assurdi

LINK CON CODICE R: 
Se hai fatto l'esercizio del Cap. 12 in R, allega uno screenshot 
del tuo codice e del grafico prior predictive. L'IA ti farà domande sul codice.
```

### **Domande chiave IA**

```
1. "Qual è la differenza tra P(θ) [prior] e P(y_pred) [prior predictive]?"
2. "Perché generiamo dati finti PRIMA di vedere i dati reali?"
3. "Se la tua prior predictive genera 95% di valori tra 0 e 1, ma sai che nella realtà i valori vanno da -10 a 10, cosa significa?"
4. "Mostrami il tuo codice: cosa fa la funzione rnorm() nel contesto 
   della prior predictive?"
```

---

## **FASE 2: Peer Review**

### **Rubrica con focus su codice**

```
1. ACCURATEZZA CONCETTUALE
   Il compagno ha distinto chiaramente tra:
   - Prior parametrica vs prior predictive?
   - Simulazione vs osservazione?

2. MISCONCETTO IDENTIFICATO
   Misconcezioni comuni da cercare:
   - "Prior predictive è uguale alla prior"
   - "Serve solo per fare grafici carini"
   - Confusione tra prior predictive e posterior predictive

3. COMPRENSIONE DEL CODICE (se allegato)
   Il codice del compagno:
   - Genera effettivamente una prior predictive? (sì/no)
   - È commentato in modo chiaro? (1-5)
   - Quale parte del codice ti sembra più/meno chiara?

4. DOMANDA APERTA
   Quale aspetto delle prior predictive ti è ancora oscuro?
```

---

## **FASE 3: Meta-Analisi IA**

**Focus specifico**:

- Quanti studenti confondono prior predictive con posterior predictive?
- Pattern negli errori di codice (es. "dimenticano di campionare dai parametri prima di simulare dati")
- Difficoltà nel collegare simulazioni R con teoria

**Output aggiuntivo**:

- "Top 3 errori di codice" da mostrare in aula con correzione live

---

## **FASE 4: Intervento Didattico**

**Live coding session (60 min)**:

```r
# Caso studio: prior predictive per test psicologico

# SCENARIO: Stiamo progettando uno studio su punteggi di ansia (scala 1-10)
# DOMANDA: La nostra prior è ragionevole?

# Prior parametrica (per la media del punteggio)
mu_prior <- rnorm(10000, mean = 5, sd = 2)

# Prior predictive (dati che ci aspettiamo di vedere)
y_pred <- rnorm(10000, mean = mu_prior, sd = 1.5)

# Controlliamo
hist(y_pred)
quantile(y_pred, c(0.025, 0.975))

# PROBLEMA: 5% dei valori simulati sono >10 o <1 (impossibile!)
# SOLUZIONE: Aggiustiamo la prior o usiamo distribuzione troncata
```

**Discussione**: "Quali prior predictive avete generato voi? Cosa avete scoperto?"

---

# **COMPITO 3: POSTERIOR PREDICTIVE DISTRIBUTIONS**

**Timing**: Dopo Cap. 13 | **Durata**: 10 giorni

## **Differenze chiave rispetto al Compito 2**

### **Prompt Explain-to-AI**

```
COMPITO: Spiega la differenza tra PRIOR predictive e POSTERIOR predictive.

Focus particolare su:
1. Perché la posterior predictive usa sia θ_posteriori che likelihood
2. Come si usa per "model checking" (controllo se il modello è adeguato)
3. Esempio: hai fittato un modello, la posterior predictive genera dati molto diversi da quelli osservati. Cosa significa?

LINK CON CODICE:
Allega uno screenshot del tuo posterior predictive check (PPC) da Stan/brms.
L'IA ti chiederà di interpretare il grafico.
```

### **Domande chiave IA**

```
1. "Nel tuo grafico PPC, la linea dei dati osservati cade dentro le bande 
   delle simulazioni posterior? Cosa significa se NON cade dentro?"
2. "Se posterior predictive e prior predictive sono molto simili, 
   cosa significa sui dati che hai osservato?"
3. "Spiega questa formula: P(y_pred | y_obs) = ∫ P(y_pred | θ) P(θ | y_obs) dθ"
```

---

## **FASE 2: Peer Review**

**Aggiunta specifica**:

```
5. INTERPRETAZIONE GRAFICA
   Il compagno ha allegato un PPC plot.
   - I dati osservati sembrano compatibili con le simulazioni? (sì/no/incerto)
   - Se NO, il compagno ha identificato il problema nel modello? (sì/no)
   - Cosa miglioreresti nel grafico per renderlo più chiaro?
```

---

## **FASE 3: Meta-Analisi**

**Focus**:

- % studenti che interpretano correttamente discrepanze nei PPC plots
- Misconcezioni su "cosa fare quando il modello non fitta bene"
- Confusione residua tra prior e posterior predictive

---

## **FASE 4: Intervento**

**Caso studio con modello mal specificato**:

```r
# Dati: Tempo di reazione (RT) in ms
# Problema: abbiamo usato una Normale, ma RT sono sempre positivi e asimmetrici

# Posterior predictive genera valori negativi!
# → Discussione: come migliorare il modello? (es. log-normale, gamma)
```

---

# **COMPITO 4: ELPD E CONFRONTO TRA MODELLI**

**Timing**: Dopo Cap. 44-45 | **Durata**: 10 giorni

## **FASE 1: Explain-to-AI**

### **Prompt**

```
CONTESTO: Hai studiato ELPD, LOO-CV, divergenza KL e confronto tra modelli.

COMPITO: Spiega come si confrontano due modelli bayesiani in modo rigoroso.

Include:
1. Cosa misura ELPD (Expected Log Predictive Density)
2. Perché usiamo validazione incrociata (LOO) invece di likelihood sul training set
3. Esempio: Modello A ha ELPD=-450, Modello B ha ELPD=-430. 
   Quale scegli? Perché? Quando l'SE è importante?
4. Differenza tra "fit ai dati" e "capacità predittiva"

LINK CON OUTPUT STAN:
Allega output di loo_compare() da uno dei tuoi esercizi.
```

### **Domande IA**

```
1. "Perché ELPD più alto (meno negativo) è meglio? Cosa rappresenta quel numero?"
2. "Nel tuo output loo_compare, c'è una colonna 'elpd_diff' e 'se_diff'. Come interpreti il rapporto elpd_diff/se_diff?"
3. "Se un modello ha 20 parametri e ELPD=-400, e un altro ha 3 parametri e ELPD=-405, quale scegli? Quando la parsimonia conta?"
4. "Cosa significa 'overfitting' in ottica bayesiana?"
```

---

## **FASE 2: Peer Review**

```
1. ACCURATEZZA CONCETTUALE
   Il compagno ha chiarito:
   - Differenza tra fit e predizione?
   - Ruolo della cross-validation?

2. MISCONCETTO IDENTIFICATO
   Misconcetti comuni:
   - "Il modello con più parametri è sempre migliore"
   - "ELPD è come p-value (soglia fissa)"
   - "LOO è solo un test statistico"

3. INTERPRETAZIONE OUTPUT
   Se il compagno ha allegato loo_compare:
   - Ha interpretato correttamente elpd_diff?
   - Ha considerato l'incertezza (SE)?

4. DOMANDA APERTA
   Quale aspetto del confronto tra modelli trovi più difficile da applicare in pratica?
```

---

## **FASE 3: Meta-Analisi**

**Focus specifico**:

- Confusione tra WAIC, LOO, ELPD (sovrapposizione terminologica)
- Difficoltà nell'interpretare output numerici di Stan
- Tendenza a sovra-interpretare piccole differenze in ELPD

**Output**:

- Flowchart decisionale per confronto modelli (generato dall'IA, raffinato da me)

---

## **FASE 4: Intervento**

**Workshop pratico (90 min)**:

```r
# CASO STUDIO: Predire sintomi depressivi

# Modello 1: solo età
# Modello 2: età + genere
# Modello 3: età + genere + stress + supporto sociale

# Fitto tutti e 3 in Stan
# Confronto con loo_compare()

# DISCUSSIONE:
# - Modello 3 ha ELPD migliore, ma di solo 2 punti (SE=1.8)
# - Modello 2 ha 2 parametri in meno
# - Come decidiamo?

# ESERCIZIO: Aggiungete un predittore "noise" (random)
# Cosa succede all'ELPD? Perché LOO "penalizza" il rumore?
```

---

# **VALUTAZIONE E RICONOSCIMENTO**

## **Peso nella valutazione finale**

- **Partecipazione ai 4 compiti**: 15% del voto finale
    
    - Trascrizioni complete e peer review = 10%
    - Miglioramento pre/post nelle spiegazioni 2 = 5%
- **Portfolio riflessivo**: 5% (opzionale, bonus)
    
    - Documento finale (2-3 pagine) dove lo studente:
        - Confronta le proprie spiegazioni 1 vs 2 dei 4 compiti
        - Identifica i 3 cambiamenti più importanti nella propria comprensione
        - Riflette su quali misconcezioni aveva e come le ha superate

## **Riconoscimenti**

- **"Most insightful peer review"**: Studente che ha fatto la peer review più precisa e costruttiva (votazione anonima della classe)
- **"Clarity award"**: Miglior analogia/esempio emerso dalle trascrizioni (scelto dalla classe dopo aver visto tutti gli esempi anonimi)

---

# **INNOVAZIONI SPECIFICHE DI QUESTO APPROCCIO**

1. **IA come co-valutatore progressivo**: Non solo risponde, ma traccia l'evoluzione concettuale dello studente
    
2. **Peer learning strutturato ma flessibile**: Non semplice "correggi l'errore", ma "identifica pattern di pensiero"
    
3. **Meta-analisi come strumento didattico trasparente**: Gli studenti VEDONO come la classe pensa collettivamente
    
4. **Collegamento teoria-codice**: Ogni compito richiede di spiegare ANCHE il codice R/Stan
    
5. **Feedback loop chiuso**: Meta-analisi → Intervento → Miglioramento misurato
    

---

**Alternative che potresti preferire**:

Se pensi che 4 compiti siano troppi, potremmo ridurre a:

- **Compito 1**: Aggiornamento bayesiano (fondamento epistemologico)
- **Compito 2**: Prior + Posterior predictive (workflow completo)
- **Compito 3**: ELPD e model comparison (valutazione finale)

Oppure, se preferisci enfatizzare aspetti diversi, potrei sviluppare compiti su:

- Prior elicitation e sensitivity analysis
- Modelli gerarchici e pooling parziale
- Workflow diagnostico (convergenza, divergenze)

----------------

Il progetto introduce l'intelligenza artificiale come strumento di apprendimento attivo in un corso di statistica bayesiana per studenti senza competenze pregresse. Oltre al tutoring individualizzato, l'IA viene integrata in un ciclo didattico articolato in tre fasi:

1. **Explain-to-AI**: gli studenti spiegano concetti chiave (es. aggiornamento bayesiano, distribuzioni predittive) dialogando con l'IA, che pone domande socratiche per elicitare comprensione profonda. Le trascrizioni documentano il processo cognitivo.
    
2. **Peer Review strutturata**: gli studenti valutano spiegazioni anonime dei compagni usando rubriche focalizzate, identificando accuratezze, fraintendimenti comuni ed esempi efficaci.
    
3. **Meta-analisi IA**: il docente utilizza l'IA per analizzare in forma aggregata trascrizioni e peer review, generando report diagnostici che mappano fraintendimenti ricorrenti, pattern linguistici e lacune concettuali della classe.
    
Questo approccio rende visibile il "pensare collettivo" degli studenti, consente interventi didattici mirati basati su evidenza empirica e traccia l'evoluzione dell'apprendimento individuale attraverso confronti pre/post intervento. L'innovazione risiede nel duplice ruolo dell'IA: come supporto allo studente e come strumento diagnostico per il docente, creando un ciclo di feedback che personalizza l'insegnamento in modo trasparente.
