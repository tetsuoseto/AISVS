# C13 Supervisione Umana, Responsabilità e Governance

## Obiettivo di controllo

Questo capitolo fornisce requisiti per mantenere la supervisione umana e chiare catene di responsabilità nei sistemi di IA, garantendo spiegabilità, trasparenza e una gestione etica durante l'intero ciclo di vita dell'IA.

---

## C13.1 Interruttore di spegnimento e meccanismi di sovrascrittura

Fornire percorsi di spegnimento o di rollback quando si osserva un comportamento non sicuro del sistema di intelligenza artificiale.

|   #    | Descrizione                                                                                                                              | Livello | Ruolo |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 13.1.1 | Verifica che esista un meccanismo di arresto manuale in grado di interrompere immediatamente l'inferenza e gli output del modello di IA. |    1    |  D/V  |
| 13.1.2 | Verifica che i controlli di override siano accessibili solo al personale autorizzato.                                                    |    1    |   D   |
| 13.1.3 | Verificare che le procedure di rollback possano ripristinare le versioni precedenti del modello o operazioni in modalità sicura.         |    3    |  D/V  |
| 13.1.4 | Verificare che i meccanismi di override siano testati regolarmente.                                                                      |    3    |   V   |

---

## C13.2 Punti di controllo decisionali con coinvolgimento umano

Richiedere approvazioni umane quando gli importi in gioco superano soglie di rischio predefinite.

|   #    | Descrizione                                                                                                                                               | Livello | Ruolo |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 13.2.1 | Verificare che le decisioni dell'IA ad alto rischio richiedano l'approvazione esplicita da parte di un essere umano prima dell'esecuzione.                |    1    |  D/V  |
| 13.2.2 | Verifica che le soglie di rischio siano chiaramente definite e attivino automaticamente i flussi di lavoro di revisione umana.                            |    1    |   D   |
| 13.2.3 | Verifichi che le decisioni sensibili al tempo abbiano procedure di fallback quando l'approvazione umana non possa essere ottenuta entro i tempi previsti. |    2    |   D   |
| 13.2.4 | Verifica che le procedure di escalation definiscano livelli di autorità chiari per diversi tipi di decisione o categorie di rischio, se applicabili.      |    3    |  D/V  |

---

## C13.3 Catena di responsabilità e auditabilità

Registrare le azioni dell'operatore e le decisioni del modello.

|   #    | Descrizione                                                                                                                                                             | Livello | Ruolo |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 13.3.1 | Verifica che tutte le decisioni del sistema di IA e gli interventi umani siano registrati con marcature temporali, identità degli utenti e motivazione della decisione. |    1    |  D/V  |
| 13.3.2 | Verifica che i registri di audit non possano essere manomessi e includano meccanismi di verifica dell'integrità.                                                        |    2    |   D   |

---

## C13.4 Tecniche di Explainable-AI

Importanza delle caratteristiche superficiali, spiegazioni controfattuali e spiegazioni locali.

|   #    | Descrizione                                                                                                                                                          | Livello | Ruolo |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 13.4.1 | Verifica che i sistemi di IA forniscano spiegazioni di base per le loro decisioni in formato leggibile dall'uomo.                                                    |    1    |  D/V  |
| 13.4.2 | Verificare che la qualità delle spiegazioni sia validata tramite studi di valutazione umana e metriche.                                                              |    2    |   V   |
| 13.4.3 | Verifica che siano disponibili i punteggi di importanza delle caratteristiche o i metodi di attribuzione (SHAP, LIME, ecc.) per decisioni critiche.                  |    3    |  D/V  |
| 13.4.4 | Verificare che le spiegazioni contrafattuali mostrino come gli input potrebbero essere modificati per cambiare gli esiti, se applicabile al caso d'uso e al dominio. |    3    |   V   |

---

## C13.5 Schede dei modelli e divulgazioni sull'uso

Mantenere le schede del modello per l'uso previsto, le metriche delle prestazioni e le considerazioni etiche.

|   #    | Descrizione                                                                                                                                                                                                                         | Livello | Ruolo |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 13.5.1 | Verifica che le schede del modello documentino i casi d'uso previsti, le limitazioni e le modalità di guasto note.                                                                                                                  |    1    |   D   |
| 13.5.2 | Verificare che le metriche di prestazione relative ai diversi casi d'uso applicabili siano rese note.                                                                                                                               |    1    |  D/V  |
| 13.5.3 | Verifica che le considerazioni etiche, le valutazioni dei bias, le valutazioni di equità, le caratteristiche dei dati di addestramento e le limitazioni note dei dati di addestramento siano documentate e aggiornate regolarmente. |    2    |   D   |
| 13.5.4 | Verifica che le schede del modello siano versionate e mantenute durante l'intero ciclo di vita del modello, con tracciamento delle modifiche.                                                                                       |    2    |  D/V  |

---

## C13.6 Quantificazione dell'incertezza

Propaga i punteggi di confidenza o le misure di entropia nelle risposte.

|   #    | Descrizione                                                                                                               | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 13.6.1 | Verifica che i sistemi di IA forniscano punteggi di confidenza o misure di incertezza insieme ai loro output.             |    1    |   D   |
| 13.6.2 | Verifica che le soglie di incertezza attivino una revisione umana aggiuntiva o percorsi decisionali alternativi.          |    2    |  D/V  |
| 13.6.3 | Verificare che i metodi di quantificazione dell'incertezza siano calibrati e validati rispetto ai dati di verità a terra. |    2    |   V   |
| 13.6.4 | Verifica che la propagazione dell'incertezza sia mantenuta attraverso flussi di lavoro di IA a più passaggi.              |    3    |  D/V  |

---

## C13.7 Rapporti di trasparenza rivolti agli utenti

Fornire aggiornamenti periodici su incidenti, deriva e utilizzo dei dati.

|   #    | Descrizione                                                                                                                                                           | Livello | Ruolo |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 13.7.1 | Verifica che le politiche sull'utilizzo dei dati e le pratiche di gestione del consenso degli utenti siano comunicate chiaramente alle parti interessate.             |    1    |  D/V  |
| 13.7.2 | Verifica che siano condotte valutazioni sull'impatto dell'IA e che i risultati siano inclusi nel reporting.                                                           |    2    |  D/V  |
| 13.7.3 | Verifica che i rapporti di trasparenza pubblicati regolarmente riportino gli incidenti legati all'IA e le metriche operative con un livello di dettaglio ragionevole. |    2    |  D/V  |

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
* [GDPR — Article 5 "Transparency Principle" (Regulation (EU) 2016/679)](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX%3A32016R0679)
* [Human Oversight under Article 14 of the EU AI Act (Fink, 2025)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5147196)

