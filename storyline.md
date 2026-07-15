# Storyline e Filo Narrativo della Tesi

Questo documento descrive lo stato di avanzamento, le scelte metodologiche, i collegamenti concettuali e il filo narrativo che lega i capitoli della tesi incentrata sulla risoluzione dell'High School Timetabling Problem (HSTP) per l'Istituto Tecnico Saffi-Alberti di Forlì.

---

## Introduzione
* **Sintesi**: Inquadra lo School Timetabling come problema di ottimizzazione combinatoria in contesti logistici ed organizzativi reali. Introduce gli obiettivi specifici dello studio sul caso dell'Istituto Saffi-Alberti di Forlì.
* **Filo Narrativo**: Pone le basi motivazionali e definisce il perimetro applicativo. Si collega al Capitolo 1 introducendo la necessità di una modellazione matematica formale.

---

## Capitolo 1: Il Problema dell’HSTP e la sua Modellazione Matematica
* **Sintesi**: Definisce formalmente gli insiemi ($D, C, A, T$) e le variabili decisionali booleane $x_{d,c,a,t}$. Dimostra la natura NP-hard del problema e l'esplosione combinatoria degli stati. Introduce la riduzione classica al Graph Coloring Problem (GCP) tramite il grafo di conflitto $G=(V,E)$ e discute le estensioni List Coloring e ipergrafi. Classifica i vincoli in Hard (ammissibilità fisica) e Soft (qualità didattica), definendo la funzione obiettivo a costi pesati: $\min z = \sum w_i P_i(x)$.
* **Filo Narrativo**: Traduce l'esigenza organizzativa reale dell'introduzione in un modello matematico astratto standard. Evidenzia che la risoluzione diretta del modello è computazionalmente impraticabile, introducendo la necessità di esplorare gli algoritmi dello stato dell'arte trattati nel Capitolo 2.
* **Scelte Tecniche e Vincoli**: Definizione univoca della notazione matematica e delle variabili decisionali che rimarranno costanti in tutta la tesi.

---

## Capitolo 2: Stato dell'Arte degli Algoritmi di Risoluzione
* **Sintesi**: Esplora e confronta gli approcci esatti (ILP, SAT-solving, Constraint Programming) con gli approcci euristici. Analizza in dettaglio le metaeuristiche a traiettoria (Tabu Search, Simulated Annealing) e di popolazione (Algoritmi Genetici), citando il lavoro di Colorni, Dorigo e Maniezzo (1998) per misurarne l'efficacia relativa. Introduce il paradigma ibrido delle Matheuristics (Maniezzo, Boschetti e Stützle 2021) analizzando euristiche da decomposizione (Dantzig-Wolfe, Lagrangiana, Benders), Corridor Method e Kernel Search.
* **Filo Narrativo**: Fornisce la rassegna critica degli strumenti risolutivi disponibili in letteratura per superare l'esplosione combinatoria introdotta nel Capitolo 1. Si collega al Capitolo 3 poiché questi algoritmi dovranno essere valutati e adattati per rispondere ai vincoli specifici del caso reale di studio.
* **Scelte Tecniche e Vincoli**: Formalizzazione teorica delle tecniche di ricerca locale e dei metodi esatti.

---

## Capitolo 3: Analisi Applicativa: I Vincoli dell'Istituto Tecnico e Scelta del Modello
* **Sintesi**: Cala la teoria sul caso reale dell'Istituto Saffi-Alberti di Forlì per l'A.S. 2026/2027. Matematizza i vincoli rigidi (unicità docente/classe, capacità aule, compresenze) e morbidi (max 5 ore consecutive, max 3 ore buche settimanali, divieto duplicazione giornaliera). Introduce la logistica multi-plesso e la mobilità dei docenti su più scuole adottando i modelli Class Teacher Assignment Problem (CTAP) e Teacher Profile Problem (TPP) di Claudio Crobu (2024). Propone un'architettura risolutiva ibrida a 2 fasi: Constraint Programming / FET solver per la generazione dell'orario iniziale ammissibile + Tabu Search per l'ottimizzazione fine dei vincoli soft.
* **Filo Narrativo**: Sintetizza la teoria modellistica del Capitolo 1 ed i metodi risolutivi del Capitolo 2 applicandoli alla complessità della scuola reale. Risolve le specificità del multi-plesso e propone la soluzione ingegneristica finale da implementare.
* **Scelte Tecniche e Vincoli**: Formulazione matematica esatta dei vincoli locali e definizione dell'architettura ibrida CP + TS.

---

## Conclusioni
* **Sintesi**: Riassume i risultati ottenuti, l'efficacia dell'approccio ibrido proposto e discute le prospettive future di implementazione software o integrazione di machine learning per la gestione delle supplenze.
* **Filo Narrativo**: Chiude il percorso logico della tesi tirando le somme dell'analisi compilativo-progettuale svolta.
