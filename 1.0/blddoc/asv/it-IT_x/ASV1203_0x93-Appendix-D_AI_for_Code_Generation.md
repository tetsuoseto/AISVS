# Appendice D: Governance e Verifica della Scrittura Sicura Assistita da AI

## Obiettivo

Questo capitolo definisce i controlli organizzativi di base per l'uso sicuro ed efficace degli strumenti di codifica assistita dall'IA durante lo sviluppo software, garantendo sicurezza e tracciabilità lungo l'intero ciclo di vita del software (SDLC).

---

## AD.1 Flusso di lavoro per la programmazione sicura assistita da AI

Integrare gli strumenti di intelligenza artificiale nel ciclo di vita dello sviluppo software sicuro (SSDLC) dell'organizzazione senza indebolire i controlli di sicurezza esistenti.

|   #    | Descrizione                                                                                                                                                                                                    | Livello | Ruolo |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AD.1.1 | Verifica che un flusso di lavoro documentato descriva quando e come gli strumenti di intelligenza artificiale possono generare, rifattorizzare o revisionare il codice.                                        |    1    |  D/V  |
| AD.1.2 | Verificare che il flusso di lavoro corrisponda a ciascuna fase del SSDLC (progettazione, implementazione, revisione del codice, test, distribuzione).                                                          |    2    |   D   |
| AD.1.3 | Verificare che le metriche (ad esempio, densità delle vulnerabilità, tempo medio di rilevamento) siano raccolte sul codice prodotto dall'IA e confrontate con i parametri di riferimento esclusivamente umani. |    3    |  D/V  |

---

## AD.2 Qualificazione dello Strumento AI e Modellazione delle Minacce

Assicurarsi che gli strumenti di codifica AI vengano valutati per le capacità di sicurezza, il rischio e l'impatto sulla catena di approvvigionamento prima dell'adozione.

|   #    | Descrizione                                                                                                                                                                                                 | Livello | Ruolo |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AD.2.1 | Verificare che un modello di minaccia per ogni strumento di IA identifichi abusi, inversione del modello, perdita di dati e rischi nella catena di dipendenza.                                              |    1    |  D/V  |
| AD.2.2 | Verificare che le valutazioni degli strumenti includano l’analisi statica/dinamica di eventuali componenti locali e la valutazione degli endpoint SaaS (TLS, autenticazione/autorizzazione, registrazione). |    2    |   D   |
| AD.2.3 | Verificare che le valutazioni seguano un quadro riconosciuto e siano ripetute dopo cambiamenti significativi di versione.                                                                                   |    3    |  D/V  |

---

## AD.3 Gestione sicura di prompt e contesto

Impedire la fuoriuscita di segreti, codice proprietario e dati personali durante la costruzione di prompt o contesti per modelli di IA.

|   #    | Descrizione                                                                                                                                                                                           | Livello | Ruolo |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AD.3.1 | Verificare che le linee guida scritte vietino l'invio di segreti, credenziali o dati riservati nelle richieste.                                                                                       |    1    |  D/V  |
| AD.3.2 | Verificare che i controlli tecnici (redazione lato client, filtri di contesto approvati) rimuovano automaticamente gli elementi sensibili.                                                            |    2    |   D   |
| AD.3.3 | Verificare che i prompt e le risposte siano tokenizzati, crittografati durante la trasmissione e a riposo, e che i periodi di conservazione siano conformi alla politica di classificazione dei dati. |    3    |  D/V  |

---

## AD.4 Validazione del codice generato da AI

Rilevare e correggere le vulnerabilità introdotte dall'output dell'IA prima che il codice venga integrato o distribuito.

|   #    | Descrizione                                                                                                                                                                              | Livello | Ruolo |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AD.4.1 | Verificare che il codice generato dall'IA sia sempre sottoposto a revisione umana.                                                                                                       |    1    |  D/V  |
| AD.4.2 | Verificare che gli scanner automatizzati (SAST/IAST/DAST) vengano eseguiti su ogni pull request contenente codice generato dall'IA e bloccare le fusioni in caso di riscontri critici.   |    2    |   D   |
| AD.4.3 | Verificare che i test di fuzzing differenziale o i test basati su proprietà dimostrino comportamenti critici per la sicurezza (ad es., convalida degli input, logica di autorizzazione). |    3    |  D/V  |

---

## AD.5 Spiegabilità e Tracciabilità dei Suggerimenti di Codice

Fornire agli auditor e agli sviluppatori una panoramica sul motivo per cui è stato fatto un suggerimento e su come è evoluto.

|   #    | Descrizione                                                                                                                                                                                        | Livello | Ruolo |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AD.5.1 | Verificare che le coppie prompt/risposta siano registrate con gli ID di commit.                                                                                                                    |    1    |  D/V  |
| AD.5.2 | Verificare che gli sviluppatori possano mostrare le citazioni del modello (estratti di addestramento, documentazione) a supporto di un suggerimento.                                               |    2    |   D   |
| AD.5.3 | Verificare che i rapporti di spiegabilità siano archiviati insieme agli artefatti di progettazione e citati nelle revisioni di sicurezza, soddisfacendo i principi di tracciabilità ISO/IEC 42001. |    3    |  D/V  |

---

## AD.6 Feedback Continuo e Messa a Punto del Modello

Migliorare le prestazioni di sicurezza del modello nel tempo prevenendo la deriva negativa.

|   #    | Descrizione                                                                                                                                                                                                   | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AD.6.1 | Verificare che gli sviluppatori possano segnalare suggerimenti non sicuri o non conformi, e che le segnalazioni vengano monitorate.                                                                           |    1    |  D/V  |
| AD.6.2 | Verificare che il feedback aggregato informi il fine-tuning periodico o la generazione aumentata da recupero con corpora di codifica sicura verificati (ad esempio, OWASP Cheat Sheets).                      |    2    |   D   |
| AD.6.3 | Verificare che un sistema di valutazione a circuito chiuso esegua test di regressione dopo ogni fine-tuning; le metriche di sicurezza devono soddisfare o superare le baseline precedenti prima del rilascio. |    3    |  D/V  |

---

### Riferimenti

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

