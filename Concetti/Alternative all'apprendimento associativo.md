---
type: Zettel
title: Alternative all'apprendimento associativo
description: null
modificationDate: 2025-04-25 08:34
tags: [research]
coverImage: null
---

Oltre all'approccio tradizionale basato su ricompense e punizioni, possiamo considerare modelli complessi come l'apprendimento basato su probabilità (Bayes), il coding predittivo, il principio dell'energia libera, e l'apprendimento osservativo. Ognuno di questi approcci non si limita alla semplice associazione, ma propone forme di adattamento attraverso l'errore, la previsione e la minimizzazione delle sorprese, esplorando così diverse prospettive psicologiche e metodi di reinforcement learning.

**Esplorando modelli alternativi di apprendimento**

Sto pensando a diversi approcci alternativi all'apprendimento associativo, tra cui l'inferenza attiva, che si basa sulla previsione piuttosto che sul semplice premio. Altri modelli includono l'apprendimento informativo (ricerca di novità e guadagno informativo), la plasticità e il potenziale per apprendere in modo non supervisionato. Voglio anche esplorare l'influenza sociale e osservazionale, e i modelli ecologici dinamici. Penso che dovrei consultare articoli recenti su argomenti come il coding predittivo e la teoria dell'energia libera per approfondire ulteriormente.

Di seguito trovi una “mappa” concettuale—organizzata per grandi filoni teorici—di modi alternativi (o complementari) di concepire l’adattamento senza ridurre tutto a «scelta → ricompensa/punizione» come nel classico Rescorla-Wagner.

---

## 1. Modelli probabilistici e inferenza bayesiana

L’idea centrale è che l’organismo mantenga e aggiorni **credenze** sulle cause del mondo, invece di pesare soltanto rinforzi. L’apprendimento avviene tramite la **regola di Bayes**:

p(θ∣D)∝p(D∣θ) p(θ)

dove D è la nuova evidenza sensoriale. Il “prediction-error” qui è la discrepanza fra dati osservati e quelli previsti dal modello generativo, non una differenza tra ricompensa attesa e ottenuta. Questi modelli spiegano con eleganza fenomeni come **blocking** e **overshadowing** senza evocare rinforzi esterni. citeturn0search6

---

## 2. Predictive Coding & Free-Energy Principle

Secondo la cornice di Friston, il cervello si comporta come un sistema bayesiano che minimizza la **free energy** (una misura del surprisal atteso). A livello percettivo, minimizzare l’errore di previsione allineando le rappresentazioni interne; a livello motorio, compiere azioni che rendano vere le proprie predizioni.

F=Eq[ln⁡q(s)]⏟accuracy−Eq[ln⁡p(s,o)]⏟complexity

Qui l’adattamento è guidato dall’**epistemic value** (riduzione di incertezza) più che dal valore di ricompensa. citeturn0search0turn0search5turn0search10

---

## 3. Active Inference

Estende il punto precedente: l’agente seleziona azioni che minimizzano l’**expected free energy**

G=Risk⏟discrepanza tra preferenze e predizioni+Ambiguity⏟incertezza sensoriale

ottenendo un principio unificato di esplorazione-sfruttamento senza un esplicito segnale di rinforzo. È quindi possibile modellare curiosità, homeostasis o stigma-avoidance come particolari prior preferences, non come “ricompense”. citeturn0search0turn0search5

---

## 4. Intrinsic Motivation e Information-Theoretic RL

Nell’AI contemporanea si usano **ricompense intrinseche** basate su novità, sorpresa o guadagno d’informazione (p. es. entropia delle predizioni, variational information gain). Queste grandezze misurano direttamente la qualità dell’adattamento (esplora ciò che riduce l’incertezza del modello). Framework recenti come **Curiosity-Driven RLHF**combinano feedback umano con ricompense interne che premiano stati mai visti, mostrando che l’agente impara politiche flessibili anche in ambienti privi di rinforzi esterni densi. citeturn0search2turn0search7turn0search12

---

## 5. Latent Learning e Cognitive Maps

Già Tolman mostrò che i ratti possono apprendere la struttura di un labirinto **senza** rinforzo—concetto di *latent learning*. Oggi questa idea è formalizzata nei modelli **model-based**: l’agente costruisce una rappresentazione dello spazio delle transizioni (“cognitive map”) e pianifica su di essa. Tali modelli spiegano flessibilità, generalizzazione composizionale e “replanning” quando l’ambiente cambia. Evidenze neurofisiologiche recenti (ippocampo, corteccia entorinale) corroborano la presenza di mappe latenti. citeturn0search3turn0search8turn0search13

---

## 6. Ecological-Dynamical Approach

Qui l’adattamento è concepito come **auto-organizzazione** in un campo dinamico di **affordances**—opportunità d’azione offerte dall’ambiente. Le leggi che guidano il comportamento derivano dalla dinamica congiunta agente-ambiente (attractor landscapes, synergies), non da un segnale di premio. Plasticità e apprendimento emergono dall’esposizione continua a vincoli e perturbazioni, con meccanismi di selezione naturale, procedurale e percettiva che ri-parametrizzano il sistema. citeturn0search4turn0search9turn0search14

---

## 7. Plasticità sinaptica non-rinforzata

- **Hebbian/anti-Hebbian learning**: “fire together, wire together” → utilissimo per l’estrazione di feature statistiche, cioè *unsupervised representation learning*.

- **Spike-Timing-Dependent Plasticity**: regola temporale che può formare sequenze predittive. Queste forme di plasticità supportano l’organizzazione dei circuiti senza bisogno di premio esterno, ma possono diventare la base su cui sistemi più lenti (dopamine-driven) operano selezioni.

---

## 8. Meta-Learning (“Learning to Learn”)

Gli agenti possono adattare **la propria stessa dinamica di aggiornamento**. In psicologia si vedono fenomeni analoghi nel trasferimento di set mentali o nella modulazione del tasso di apprendimento (α) in funzione della volatilità ambientale.

---

### Confronto sintetico

| Approccio                    | Meccanismo di guida               | Rappresentazione interna          | Flessibilità             |
| :--------------------------- | :-------------------------------- | :-------------------------------- | :----------------------- |
| Rescorla-Wagner              | Errore di prediction sul rinforzo | Peso stimolo-rinforzo             | Limitata                 |
| Bayesian / Predictive coding | Errore di previsione sensoriale   | Modello generativo probabilistico | Alta                     |
| Active inference             | Expected free energy              | Modello gerarchico + preferenze   | Altissima                |
| Intrinsic RL                 | Information gain / novelty        | Embedding latente                 | Alta                     |
| Ecological-dynamics          | Affordances & dinamica sistema    | Coupling percezione-azione        | Contingente all'ambiente |

---

## Implicazioni pratiche

1. **Ricerca di base**: per studiare l’adattamento animale/umano in ambienti complessi, conviene integrare paradigmi di rinforzo classico con misure di incertezza (pupilometry, surprise-locked ERPs).

2. **AI e Robotics**: incorporare free-energy o curiosity rewards consente a robot di esplorare senza scripting di “goal states”.

3. **Psicologia applicata**: nei contesti clinici, il framing di “punizione e ricompensa” può essere sostituito da interventi su aspettative (terapia predittivo-cognitiva) o ristrutturazione di affordances ambientali.

---

### Conclusione

Sì, esistono (e sono sempre più adottate) teorie in cui l’apprendimento non è guidato primariamente da ricompense e punizioni. Dalla prospettiva bayesiana-predictive all’ecological-dynamics, l’enfasi si sposta su **informazione, incertezza e auto-organizzazione**. Ciò offre modelli più generali e biologicamente plausibili per spiegare come gli organismi—e le AI—si adattano a un mondo che cambia.

# **Sviluppando il punto delle aspettative e dell'ambiente**

Per uno studio sui cambiamenti nelle aspettative e sulle modifiche ambientali, propongo due esperimenti. Il primo potrebbe manipolare le aspettative predittive mediante simulazioni di scenari legati alle decisioni, modificando aspettative su ricompense o rischi. Il secondo esplorerebbe il "framing" ambientale modificato, cambiando la disposizione fisica per influenzare il comportamento. Sia le misure psicometriche che l'analisi delle differenze individuali, come la personalità e il comportamento di apprendimento, potrebbero essere fondamentali per raccogliere i dati.

**Cercando interventi basati su aspettative**

Voglio aggiornare il mio riferimento su temi come la terapia basata su elaborazione predittiva, manipolazione delle aspettative nel placebo/nocebo e interventi legati all'ambiente. Posso cercare articoli per temi specifici come "terapia basata su elaborazione predittiva e depressione universitaria nel 2024" e "intervento basato sugli affordance nella progettazione ambientale per la salute mentale." Un altro approccio potrebbe essere esplorare la rilevanza dell'aspettativa nei compiti priming o l'analgesia placebo.

**Progetti per esperimenti sulle aspettative**

Abbiamo già alcune fonti sull'applicazione delle aspettative, dell'energia libera e degli affordances. Voglio includere articoli pertinenti a temi come l'aspettativa e la sensibilità ai premi, l'influenza dei video sulla depressione, ed esperimenti sullo spazio ambientale. Propongo due esperimenti: uno con l'intervento predittivo su aspettative attraverso la terapia predittiva, confrontato con un gruppo di controllo, e l'altro manipolando aspettative placebo/nocebo in cupping e compiti di stress. I partecipanti saranno studenti, e studieremo le differenze individuali.

### Come passare da “ricompensa / punizione” a **“aspettative e affordances”** in laboratorio

Di seguito propongo **due paradigmi sperimentali** fattibili con campioni universitari (N≈80–120) che permettono di:

1. manipolare *aspettative* o *affordances* senza usare rinforzi esterni,

2. stimare **parametri individuali** (computazionali e psicometrici) collegabili a vulnerabilità cliniche.

---

## Paradigma A – “Prediction-Update Lab”

**Obiettivo.** Misurare come le persone aggiornano le proprie previsioni emotive e se questo processo spiega la variabilità nei sintomi ansioso-depressivi.

| Fase                         | Procedura                                                                                                                                                                      | Output chiave                                                       |
| :--------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------ |
| **Induzione di aspettative** | Video di testimonianze (“questa attività rilassa moltissimo” vs “è stressante”) – tecnica usata per modulare l’esito di interventi depressivi citeturn0search0turn0search5 | Variazione di *outcome‐expectancy* (scala CEQ o analogica da 0–100) |
| **Task di previsione**       | In scanner EEG o in laboratorio: presentate immagini neutre→positive con probabilità variabile. Il soggetto predice il valence futuro e valuta lo stimolo reale.               | Trial-by-trial **prediction error**                                 |
| **Fase di confutazione**     | Informate i partecipanti che la fonte del video era inaffidabile (condizione *violazione di aspettativa*) oppure no (controllo).                                               | Δ di learning-rate post-violazione                                  |

### Analisi

- **Modello gerarchico bayesiano** (p. es. *Hierarchical Gaussian Filter*) per estrarre parametri:

    - *μ0* (bias iniziale),

    - *α* (tasso di apprendimento),

    - *ω* (volatilità percepita).

- Regressioni e *latent-profile analysis* per vedere quali parametri predicono:

    - BDI-II, STAI, Intolerance-of-Uncertainty (IU-12).

- I lavori recenti mostrano che l’instabilità del prediction-error è collegata ad anedonia e reward-sensitivity citeturn0search10turn0search3.

### Implicazioni cliniche

Chi mostra *α* troppo basso (scarso updating) tende a mantenere convinzioni depressive; in terapia “predittivo-cognitiva”​ si interverrebbe aumentando evidenza contro tali priors—non distribuendo premi o punizioni.

---

## Paradigma B – “Affordance-Reshape Studio”

**Obiettivo.** Verificare se la ristrutturazione di affordances ambientali riduce stress e migliora agency, e se l’effetto dipende da differenze individuali (p. es. Sensory Processing Sensitivity).

| Condizione          | Setting (3 settimane di studio quotidiano)                                                                                                                                                                                 |
| :------------------ | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Standard**        | Aula tradizionale, sedute fisse, luci a LED fredde.                                                                                                                                                                        |
| **Affordance-Plus** | Verde biofilico + posti mobili, zone di micro-pausa, bacheca “take-action” per pianificare attività autonome; elementi ispirati agli studi su affordances e salute mentale citeturn0search1turn0search6turn0search11. |

### Misure

1. **EMA** via smartphone (mood, percezione di controllo, stress fisiologico stimato da HRV wrist-band).

2. **Compiti di navigazione** in realtà aumentata dentro l’aula (numero di percorsi esplorativi come proxy di “exploratory agency”).

3. Questionari pre-post: PSS-10, Basic Psychological Need Satisfaction (autonomia), Highly Sensitive Person Scale.

### Analisi

- **Mixed-effects** (tempo × condizione × moderatore-tratto).

- *Network analysis* sugli item EMA per valutare come cambiano le connessioni fra “controllo” e “umore”.

- Cluster di soggetti che traggono maggiore beneficio (p. es. elevata sensibilità sensoriale + bassa autonomia di base).

### Traduzione clinica

I cluster “rispondenti” potrebbero corrispondere a pazienti che, in clinica, giovano più di interventi *environment-focused*(p.es. occupational therapy, terapia forestale) rispetto a quelli basati su rinforzo comportamentale.

---

## Aspetti metodologici comuni

| Tema                          | Suggerimenti operativi                                                                                                                                                                                                                                   |
| :---------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Potenza statistica**        | Simulazioni a priori con parametri dal meta-analisi delle aspettative (ES≈0.30) ⇒ N=100 per 0.80 power.                                                                                                                                                  |
| **Etica**                     | Protocollo Ateneo + preregistrazione (OSF); *debriefing approfondito* per l’inganno nel Paradigma A.                                                                                                                                                     |
| **Open Science**              | Condividere codice (PyMC/HDDM) e dati anonimi; utilizzare standard *BIDS* per fisiologia.                                                                                                                                                                |
| **Misure cliniche indirette** | Aggiungere compiti web-based (p. es. Effort-Expenditure for Rewards) e clusterare partecipanti con l’approccio di **computational psychiatry**—ma verificare l’affidabilità dei parametri, dato che molti hanno scarsa test-retest citeturn0search13. |

---

### Perché questi paradigmi parlano di clinica

- **Expectation-focused interventions** stanno emergendo come fattori chiave nel risultato psicoterapeutico (placebo/nocebo, open-label placebo) citeturn0search2turn0search7.

- **Affordance redesign** agisce sulla possibilità di compiere azioni autogestite, concetto centrale in approcci transdiagnostici (p. es. RIP — Restricted and Interrupted Participation).

- Collegare **parametri individuali** a benefici immediati in studenti offre biomarcatori di *chi* potrebbe trarre vantaggio, anticipando test clinici su popolazioni con disturbi internalizzanti.

---

## Conclusione

Con questi due schemi sperimentali puoi:

1. Abbandonare la logica stimolo-rinforzo, testando invece come **predizioni** e **opportunità di azione** guidano l’adattamento;

2. Quantificare **differenze individuali** con strumenti computazionali robusti;

3. Gettare basi empiriche per interventi clinici personalizzati centrati su aspettative o affordances, piuttosto che su premi e punizioni.

# Disegno di ricerca dettagliato

**Rewriting Paradigm A**

I’ll update Paradigm A to focus solely on behavioral data like reaction times (RTs) and choices, removing EEG and physiological elements. We’ll adjust the tasks to include reaction time measures, and possibly confidence ratings or forced choices. The design will follow a simple structure: clear bullet points and lists without tables. Also, I’ll add details on stimuli (images), tasks (prediction, valuation), and output measures like prediction errors and RT. Analysis will involve RL modeling of RTs and choices, with a mention of model-based diffusion techniques for decision parameters.

Thought for 5 seconds

# Paradigma A — “Prediction-Update Lab” (solo **misure comportamentali**)

### Obiettivo

Stimare, usando soltanto scelte e tempi di risposta (RT), come gli individui aggiornano le proprie previsioni emotive e collegare questi parametri a sintomi ansioso-depressivi.

---

## 1. Timeline sintetica

- **T0 – Screening (≈ 20 min)**

    - Consenso informato.

    - Questionari base: BDI-II, STAI-Y, IU-12.

- **T1 – Sessione di laboratorio (≈ 50-60 min)**

    1. Induzione di aspettative (7 min).

    2. Task di previsione (30-35 min).

    3. Confutazione aspettative (3 min).

    4. Questionari post-task (5 min).

- **T2 – Follow-up online (a 7 giorni, 10 min)**

    - BDI-II breve + CEQ per la stabilità degli effetti.

---

## 2. Materiali

- Due video-testimonianze (3 min l’uno) che descrivono il compito come **rilassante** oppure **stressante**.

- 120 immagini IAPS (valence neutro-positivo).

- Software di presentazione (PsychoPy, jsPsych o equivalente).

- Postazione PC o tablet: tastiera numerica o slider touch per le risposte.

---

## 3. Fase 1 — Induzione di aspettative

1. Visione di **uno** dei due video (assegnazione casuale).

2. Compilazione del **Credibility/Expectancy Questionnaire (CEQ)**: quattro item 0-100.

*Output*: punteggio di *outcome expectancy*.

---

## 4. Fase 2 — Task di previsione (learning)

**Struttura di un singolo trial**

1. Fixation croce (0.5 s).

2. **Predizione** (max 2 s)

    - Schermata: «Quanto pensi che la prossima immagine sarà piacevole?»

    - Risposta tramite slider 1-9 → *RT-predizione* registrato.

3. ISI (intervallo casuale 0.3-0.6 s).

4. **Outcome** (1 s)

    - Visualizzazione immagine IAPS.

5. **Valutazione** (max 2 s)

    - «Quanto *è* piacevole?» (slider 1-9)

    - *RT-valutazione* registrato.

6. ITI (0.8-1.2 s).

*Dettagli stimoli*

- Blocchi: probabilità 70 % neutre / 30 % positive (o viceversa).

- Ordine blocchi controbilanciato tra partecipanti.

*Dati che ottieni per ogni trial*

- Rating previsto.

- Rating reale.

- Prediction Error = rating previsto – rating reale.

- RT-predizione.

- RT-valutazione.

---

## 5. Fase 3 — Confutazione aspettative

- **Gruppo “Violazione”**: messaggio «Le testimonianze viste all’inizio non erano affidabili».

- **Gruppo “Controllo”**: nessuna informazione aggiuntiva.

Entrambi ricompilano il CEQ.

*Output*: variazione di *outcome expectancy* e cambiamento del learning-rate (Δα) prima-dopo la violazione.

---

## 6. Parametri computazionali

1. **Hierarchical Gaussian Filter (HGF)** sui rating previsti →

    - μ₀ (bias iniziale)

    - α (learning-rate)

    - ω (volatilità percepita)

    - Δα (cambio dopo la confutazione)

2. **Drift-Diffusion Model (DDM)** sui RT di predizione

    - Drift rate modellato come funzione di incertezza (|prediction error atteso|).

    - Boundary separazione = cautela decisionale.

---

## 7. Analisi principali

- Mixed-effects: prediction-error e RT in funzione di (valence × blocco × gruppo) + (1 | soggetto).

- Regressioni: α, ω, Δα, drift rate → sintomi (BDI-II, STAI, IU-12).

- Latent Profile Analysis sui parametri computazionali per identificare sottogruppi (es. “slow-updaters”, “volatility-sensitive”).

---

## 8. Interpretazione clinica

- **α basso** → rigidità nel modificare aspettative negative → rischio di ruminazione.

- **ω alto** → ipersensibilità alla volatilità → ansia anticipatoria.

- **Drift rate basso** → difficoltà a trasformare l’incertezza in decisione rapida → anedonia/apatia.

Nella *terapia predittivo-cognitiva* si propone di creare **violazioni di aspettative controllate** (feedback positivi inattesi, revisione prove) per incrementare α e stabilizzare ω, invece di usare premi/punizioni esterni.

---

## 9. Checklist operativa

- Randomizza il video iniziale con funzione built-in del software.

- Registra con precisione le timestamp degli eventi per i calcoli RT.

- Implementa il fitting HGF e DDM in PyMC o HDDM (preregistrazione OSF).

- Debriefing completo (spiega l’inganno) e offri contatti di supporto psicologico.

