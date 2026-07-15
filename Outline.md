# Proposta di Indice e Struttura Dettagliata (Outline)

Questo documento delinea la struttura di ciascun capitolo per la nuova configurazione a 3 capitoli della tesi.

---

## Introduzione (circa 2-3 pagine)
* **Contenuto**:
  * Inquadramento generale sul problema dello scheduling e dell'allocazione di risorse in organizzazioni complesse.
  * Definizione del dominio specifico dello *School Timetabling*.
  * Obiettivi del lavoro di tesi: modellazione e analisi per l'Istituto Tecnico Saffi-Alberti di Forlì.
  * Descrizione della struttura dei capitoli successivi.

---

## Capitolo 1: Il Problema dell’HSTP e la sua Modellazione Matematica (circa 8-9 pagine)
* **1.1 Definizione formale dell'High School Timetabling Problem (HSTP) e complessità**
  * Formalizzazione degli insiemi fondamentali: Docenti ($D$), Classi ($C$), Aule ($A$), Slot Temporali ($T$).
  * Variabili decisionali booleane $x_{d,c,a,t} \in \{0, 1\}$.
  * Discussione della complessità computazionale del problema (NP-hard) ed esplosione combinatoria.
* **1.2 Astrazione del problema: il modello standard e la riduzione al Graph Coloring Problem (GCP)**
  * Costruzione del grafo di conflitto $G=(V,E)$ in cui i nodi $V$ sono gli eventi (lezioni) e gli archi $E$ sono le incompatibilità.
  * Associazione dei colori ai time-slot disponibili.
  * Limiti del GCP classico ed estensioni (es. *List Coloring*, ipergrafi per vincoli multi-risorsa).
* **1.3 Tassonomia dei vincoli nell'HSTP: Hard Constraints vs Soft Constraints**
  * Classificazione teorica:
    * *Hard Constraints* (vincoli strutturali o di ammissibilità): essenziali per l'esistenza di un orario valido (es. contemporaneità, limiti fisici delle aule).
    * *Soft Constraints* (vincoli di qualità o preferenze): descrivono la qualità didattica e organizzativa (es. ore buche, consecutività).
  * Formulazione della funzione obiettivo a costi/penalità pesate: $\min z = \sum w_i P_i(x)$.

---

## Capitolo 2: Stato dell'Arte degli Algoritmi di Risoluzione (circa 10-12 pagine)
* **2.1 Approcci esatti vs. Approcci euristici**
  * Metodi esatti: Programmazione Lineare Intera (ILP), SAT-solving, Constraint Programming (CP).
  * Limiti di scalabilità e impraticabilità dei metodi esatti su istanze scolastiche reali di grandi dimensioni.
* **2.2 Il ruolo delle Meta-euristiche**
  * Ricerca Locale e algoritmi basati su traiettoria:
    * **Tabu Search**: uso della memoria a breve termine (Tabu List), funzioni di aspirazione, mosse di intorno.
    * **Simulated Annealing**: approccio termodinamico stocastico, accettazione di soluzioni peggiorative per sfuggire a ottimi locali.
  * Meta-euristiche evolutive:
    * **Algoritmi Genetici**: codifica cromosomica, funzioni di fitness, operatori di crossover e mutazione dedicati allo scheduling.
  * Riferimento fondamentale: *Colorni, Dorigo e Maniezzo (1998)* per illustrare l'efficacia comparata di queste meta-euristiche.
* **2.3 Modelli ibridi: l'approccio delle Matheuristics**
  * Definizione di *Matheuristics*: combinazione di programmazione matematica (es. MIP/ILP) e metaeuristiche.
  * Vantaggi: sfruttare l'efficacia dei solver matematici su sotto-problemi e l'esplorazione globale delle metaeuristiche.
  * Riferimento fondamentale: *Maniezzo, Boschetti e Stützle ( EURO Advanced Tutorials )*.

---

## Capitolo 3: Analisi Applicativa: I Vincoli dell'Istituto Tecnico e Scelta del Modello (circa 8-10 pagine)
* **3.1 Analisi dei vincoli strutturali e didattici dell'A.S. 2026/2027**
  * Descrizione dei vincoli dell'Istituto Saffi-Alberti di Forlì e loro formulazione matematica:
    * *Hard*: Unicità docente/classe, capacità laboratori e palestre, compresenze (*co-teachers*), finestre di indisponibilità strutturale.
    * *Soft*: Massimo 5 ore consecutive giornaliere, massimo 3 ore buche settimanali, divieto di duplicazione giornaliera di materie da 2 ore (escluso Scienze Motorie), equità del carico orario docenti.
* **3.2 Il problema dei docenti su più plessi (Multi-school Timetabling)**
  * Modellazione logico-matematica basata sulla tesi di dottorato di *Claudio Crobu (2024)*.
  * Introduzione del Class Teacher Assignment Problem (CTAP) e del Teacher Profile Problem (TPP).
  * Formulazione del problema multi-plesso come partizionamento di grafi bipartiti e coordinamento temporale dei docenti condivisi.
* **3.3 Valutazione degli algoritmi rispetto al caso reale e proposta della soluzione ottimale**
  * Presentazione della tabella comparativa tra paradigmi (ILP, CP, TS, SA, GA) basata sulla densità dei vincoli del Saffi-Alberti.
  * Proposta di una soluzione ottimale ibrida:
    * Fase 1: Constraint Programming (CP) o euristica costruttiva (es. l'algoritmo ricorsivo del solutore open-source *FET*) per generare rapidamente un orario iniziale ammissibile (soddisfacimento degli hard constraints).
    * Fase 2: Tabu Search o Ricerca Locale per ottimizzare e minimizzare le violazioni dei soft constraints (ore buche, ore consecutive, preferenze).

---

## Conclusioni (circa 2 pagine)
* Sintesi dei risultati ottenuti con la modellazione ibrida proposta.
* Sviluppi futuri (es. implementazione software o uso di moduli predittivi/ML per supplenze e variazioni).
