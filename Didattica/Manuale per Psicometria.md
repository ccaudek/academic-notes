---
type: Zettel
title: Manuale per Psicometria
description: null
modificationDate: 2025-05-26 07:58
tags: [teaching, bayes, R]
coverImage: null
---

Devo scrivere un manuale didattico introduttivo sull'analisi dei dati psicologici. Un tema è la crisi della replicabilità in psicologia e i limiti dell'approccio frequentista. Ne segue che l'approccio proposto è quello bayesiano all'inferenza. Un problema che devo risolvere è che il libro (di non più di 400 pagine) dovrà essere self-contained (quindi fornire tutte le informazioni necessarie sulla teoria della probabilità, R, statistica descrittiva e inferenziale). Ho già tutto il materiale qui [https://ccaudek.github.io/psicometria-r/](https://ccaudek.github.io/psicometria-r/) ma è troppo lungo. Per renderlo più omogeneo e breve, pensavo di sottolineare che l'aspetto centrale dei fenomeni psicologici è la **variabilità**: le differenze individuali e il cambiamento all'interno del singolo soggetto. Come fil rouge del libro, utilizzerei questa idea in ogni capitolo, collegando questo tema alla descrizione bayesiana dell'incertezza. Proporrei il punto di vista secondo cui l'approccio bayesiano è il metodo naturale per descrivere variabilità e incertezza. Per le spiegazioni, presenterei la distribuzione a posteriori con il metodo basato su griglia, con le famiglie coniugate (caso beta-binomiale) e spiegherei l'algoritmo di Metropolis. Poi utilizzerei brms per l'inferenza su regressione bivariata, una media, due medie, una proporzione e due proporzioni. Gli equivalenti frequentasti sono facili da implementare in R, ma la spiegazione di tutta la teoria della probabilità soggiacente è troppo lunga per un testo di questo tipo, per cui pensavo di aggiungere tutte le spiegazioni dei concetti richiesti di teoria della probabilità e le dimostrazioni dei teoremi frequentisti nel materiale supplementare fornito su un sito web separato dal libro. Se voglio rendere centrale l'approccio idiografico nell'analisi dei dati psicologici, dovrò anche spiegare i modelli multilivello, che collegano il singolo caso ad una distribuzione di casi. Userei medie e proporzioni come il primo passo idiografico→nomotetico e la palestra per i concetti bayesiani. Il libro deve restare accessibile, coerente con la prospettiva idiografica e prontamente collegato ai dibattiti contemporanei sulla replicabilità (crisi frequentista) e sulla modellazione bayesiana.

![index](../Files/Media/index.docx)
[index](../Files/index.md)

![psicometria_manuale](../Files/Media/psicometria_manuale.docx)
[psicometria_manuale](../Files/psicometria_manuale.md)
