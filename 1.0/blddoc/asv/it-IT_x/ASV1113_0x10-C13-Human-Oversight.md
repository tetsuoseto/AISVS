# C13 Supervisione Umana, Responsabilità e Governance

## Obiettivo di Controllo

Questo capitolo fornisce requisiti per mantenere la supervisione umana e catene di responsabilità chiare nei sistemi di intelligenza artificiale, garantendo spiegabilità, trasparenza e gestione etica lungo tutto il ciclo di vita dell’IA.

---

## C13.1 Meccanismi di Kill-Switch e Override

Fornire percorsi di spegnimento o rollback quando viene osservato un comportamento non sicuro del sistema di IA.

|   #    | Descrizione                                                                                                                          | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 13.1.1 | Verificare che esista un meccanismo manuale di interruzione per fermare immediatamente l'inferenza e gli output del modello AI.      |    1    |  D/V  |
| 13.1.2 | Verificare che i controlli di override siano accessibili solo al personale autorizzato.                                              |    1    |   D   |
| 13.1.3 | Verificare che le procedure di rollback possano riportare alle versioni precedenti del modello o alle operazioni in modalità sicura. |    3    |  D/V  |
| 13.1.4 | Verificare che i meccanismi di override siano testati regolarmente.                                                                  |    3    |   V   |

---

## C13.2 Punti di Controllo delle Decisioni con Coinvolgimento Umano

Richiedere approvazioni umane quando le poste in gioco superano le soglie di rischio predefinite.

|   #    | Descrizione                                                                                                                                                               | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 13.2.1 | Verificare che le decisioni AI ad alto rischio richiedano un'esplicita approvazione umana prima dell'esecuzione.                                                          |    1    |  D/V  |
| 13.2.2 | Verificare che le soglie di rischio siano chiaramente definite e attivino automaticamente i flussi di lavoro di revisione umana.                                          |    1    |   D   |
| 13.2.3 | Verificare che le decisioni sensibili al tempo dispongano di procedure di riserva nel caso in cui l'approvazione umana non possa essere ottenuta entro i tempi richiesti. |    2    |   D   |
| 13.2.4 | Verificare che le procedure di escalation definiscano livelli di autorità chiari per i diversi tipi di decisione o categorie di rischio, se applicabile.                  |    3    |  D/V  |

---

## C13.3 Catena di Responsabilità e Auditabilità

Registra le azioni dell'operatore e le decisioni del modello.

|   #    | Descrizione                                                                                                                                                  | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 13.3.1 | Verificare che tutte le decisioni del sistema AI e gli interventi umani siano registrati con marca temporale, identità utente e motivazione della decisione. |    1    |  D/V  |
| 13.3.2 | Verificare che i log di audit non possano essere manomessi e includano meccanismi di verifica dell'integrità.                                                |    2    |   D   |

---

## C13.4 Tecniche di Explainable AI

Importanza delle caratteristiche superficiali, controfattuali e spiegazioni locali.

|   #    | Descrizione                                                                                                                                                            | Livello | Ruolo |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 13.4.1 | Verificare che i sistemi di intelligenza artificiale forniscano spiegazioni di base per le loro decisioni in un formato comprensibile all’essere umano.                |    1    |  D/V  |
| 13.4.2 | Verificare che la qualità della spiegazione sia validata attraverso studi di valutazione umana e metriche.                                                             |    2    |   V   |
| 13.4.3 | Verificare che i punteggi di importanza delle caratteristiche o i metodi di attribuzione (SHAP, LIME, ecc.) siano disponibili per le decisioni critiche.               |    3    |  D/V  |
| 13.4.4 | Verificare che le spiegazioni controfattuali mostrino come gli input potrebbero essere modificati per cambiare i risultati, se applicabile al caso d'uso e al dominio. |    3    |   V   |

---

## C13.5 Schede Modello e Dichiarazioni di Utilizzo

Mantenere schede modello per l'uso previsto, le metriche di prestazione e le considerazioni etiche.

|   #    | Descrizione                                                                                                                                                                                                                                   | Livello | Ruolo |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 13.5.1 | Verificare che le schede del modello documentino i casi d'uso previsti, le limitazioni e i modi di guasto noti.                                                                                                                               |    1    |   D   |
| 13.5.2 | Verificare che le metriche di prestazione relative ai diversi casi d'uso applicabili siano comunicate.                                                                                                                                        |    1    |  D/V  |
| 13.5.3 | Verificare che le considerazioni etiche, le valutazioni dei bias, le valutazioni dell'equità, le caratteristiche dei dati di addestramento e le limitazioni conosciute dei dati di addestramento siano documentate e aggiornate regolarmente. |    2    |   D   |
| 13.5.4 | Verificare che le schede del modello siano soggette a controllo delle versioni e mantenute durante l'intero ciclo di vita del modello con monitoraggio delle modifiche.                                                                       |    2    |  D/V  |

---

## C13.6 Quantificazione dell’Incertezza

Propagare i punteggi di confidenza o le misure di entropia nelle risposte.

|   #    | Descrizione                                                                                                            | Livello | Ruolo |
| :----: | ---------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 13.6.1 | Verificare che i sistemi di AI forniscano punteggi di confidenza o misure di incertezza con i loro output.             |    1    |   D   |
| 13.6.2 | Verificare che le soglie di incertezza attivino una revisione umana aggiuntiva o percorsi decisionali alternativi.     |    2    |  D/V  |
| 13.6.3 | Verificare che i metodi di quantificazione dell'incertezza siano calibrati e validati rispetto ai dati di riferimento. |    2    |   V   |
| 13.6.4 | Verificare che la propagazione dell'incertezza sia mantenuta attraverso flussi di lavoro AI multi-fase.                |    3    |  D/V  |

---

## C13.7 Rapporti di trasparenza rivolti agli utenti

Fornire divulgazioni periodiche sugli incidenti, le derive e l'uso dei dati.

|   #    | Descrizione                                                                                                                                               | Livello | Ruolo |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 13.7.1 | Verificare che le politiche di utilizzo dei dati e le pratiche di gestione del consenso degli utenti siano chiaramente comunicate alle parti interessate. |    1    |  D/V  |
| 13.7.2 | Verificare che le valutazioni dell'impatto dell'IA siano condotte e che i risultati siano inclusi nei rapporti.                                           |    2    |  D/V  |
| 13.7.3 | Verificare che i rapporti di trasparenza pubblicati regolarmente divulghino incidenti di AI e metriche operative con un livello di dettaglio ragionevole. |    2    |  D/V  |

### Riferimenti

* [EU Artificial Intelligence Act — Regulation (EU) 2024/1689 (Official Journal, 12 July 2024)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj)
* [ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management](https://www.iso.org/standard/77304.html)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [NIST SP 800-53 Revision 5 — Security and Privacy Controls](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r5.pdf)
* [A Unified Approach to Interpreting Model Predictions (SHAP, ICML 2017)](https://arxiv.org/abs/1705.07874)
* [Model Cards for Model Reporting (Mitchell et al., 2018)](https://arxiv.org/abs/1810.03993)
* [Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning (Gal & Ghahramani, 2016)](https://arxiv.org/abs/1506.02142)
* [ISO/IEC 24029-2:2023 — Robustness of Neural Networks — Methodology for Formal Methods](https://www.iso.org/standard/79804.html)
* [IEEE 7001-2021 — Transparency of Autonomous Systems](https://standards.ieee.org/ieee/7001/6929/)
* [Human Oversight under Article 14 of the EU AI Act (Fink, 2025)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5147196)

