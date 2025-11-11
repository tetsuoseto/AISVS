# Appendice D: Governance e Verifica del Coding Sicuro Assistito da AI

## Obiettivo

Questo capitolo definisce i controlli organizzativi di base per l'uso sicuro ed efficace degli strumenti di codifica assistita da AI durante lo sviluppo software, garantendo sicurezza e tracciabilità lungo tutto il SDLC.

---

## AD.1 Flusso di lavoro di codifica sicura assistita dall'IA

Integrare gli strumenti di AI nel ciclo di vita dello sviluppo software sicuro (SSDLC) dell'organizzazione senza indebolire le barriere di sicurezza esistenti.

|   #    | Descrizione                                                                                                                                                                                                 | Livello | Ruolo |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AD.1.1 | Verificare che un flusso di lavoro documentato descriva quando e come gli strumenti di IA possono generare, rifattorizzare o revisionare il codice.                                                         |    1    |  D/V  |
| AD.1.2 | Verificare che il flusso di lavoro corrisponda a ciascuna fase dell'SSDLC (progettazione, implementazione, revisione del codice, testing, distribuzione).                                                   |    2    |   D   |
| AD.1.3 | Verificare che le metriche (ad esempio, densità di vulnerabilità, tempo medio di rilevamento) siano raccolte sul codice prodotto dall’IA e confrontate con i parametri di riferimento esclusivamente umani. |    3    |  D/V  |

---

## AD.2 Qualificazione degli Strumenti di AI e Modellazione delle Minacce

Assicurarsi che gli strumenti di codifica AI vengano valutati in base alle capacità di sicurezza, ai rischi e all'impatto sulla catena di approvvigionamento prima dell'adozione.

|   #    | Descrizione                                                                                                                                                                                           | Livello | Ruolo |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AD.2.1 | Verificare che un modello di minaccia per ogni strumento di intelligenza artificiale identifichi gli abusi, l'inversione del modello, la fuoriuscita di dati e i rischi della catena di dipendenza.   |    1    |  D/V  |
| AD.2.2 | Verificare che le valutazioni degli strumenti includano l'analisi statica/dinamica di qualsiasi componente locale e la valutazione degli endpoint SaaS (TLS, autenticazione/autorizzazione, logging). |    2    |   D   |
| AD.2.3 | Verificare che le valutazioni seguano un quadro riconosciuto e vengano rieseguite dopo cambiamenti di versione importanti.                                                                            |    3    |  D/V  |

---

## AD.3 Gestione Sicura di Prompt e Contesto

Prevenire la fuoriuscita di segreti, codice proprietario e dati personali durante la costruzione di prompt o contesti per modelli di intelligenza artificiale.

|   #    | Descrizione                                                                                                                                                                                  | Livello | Ruolo |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AD.3.1 | Verificare che le linee guida scritte proibiscano l'invio di segreti, credenziali o dati classificati nei prompt.                                                                            |    1    |  D/V  |
| AD.3.2 | Verificare che i controlli tecnici (redazione lato client, filtri di contesto approvati) rimuovano automaticamente gli elementi sensibili.                                                   |    2    |   D   |
| AD.3.3 | Verificare che i prompt e le risposte siano tokenizzati, criptati durante il transito e a riposo, e che i periodi di conservazione siano conformi alla politica di classificazione dei dati. |    3    |  D/V  |

---

## AD.4 Validazione del codice generato dall’IA

Individuare e correggere le vulnerabilità introdotte dall'output dell'IA prima che il codice venga unito o distribuito.

|   #    | Descrizione                                                                                                                                                                                          | Livello | Ruolo |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AD.4.1 | Verificare che il codice generato dall'IA sia sempre soggetto a revisione umana del codice.                                                                                                          |    1    |  D/V  |
| AD.4.2 | Verificare che gli scanner automatizzati (SAST/IAST/DAST) vengano eseguiti su ogni pull request contenente codice generato da AI e bloccare le fusioni in presenza di riscontri critici.             |    2    |   D   |
| AD.4.3 | Verificare che il differential fuzz testing o i test basati sulle proprietà dimostrino comportamenti critici per la sicurezza (ad esempio, la validazione degli input, la logica di autorizzazione). |    3    |  D/V  |

---

## AD.5 Spiegabilità e Tracciabilità delle Suggerimenti di Codice

Fornire a revisori e sviluppatori una comprensione del motivo per cui è stata fatta una proposta e di come si è evoluta.

|   #    | Descrizione                                                                                                                                                                                                      | Livello | Ruolo |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AD.5.1 | Verificare che le coppie prompt/risposta siano registrate con gli ID di commit.                                                                                                                                  |    1    |  D/V  |
| AD.5.2 | Verificare che gli sviluppatori possano visualizzare le citazioni del modello (estratti di addestramento, documentazione) a supporto di un suggerimento.                                                         |    2    |   D   |
| AD.5.3 | Verificare che i report di spiegabilità siano archiviati con gli artefatti di progettazione e referenziati nelle revisioni di sicurezza, soddisfacendo i principi di tracciabilità dello standard ISO/IEC 42001. |    3    |  D/V  |

---

## AD.6 Feedback Continuo e Messa a Punto del Modello

Migliorare le prestazioni di sicurezza del modello nel tempo prevenendo deriva negativa.

|   #    | Descrizione                                                                                                                                                                                                       | Livello | Ruolo |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AD.6.1 | Verificare che gli sviluppatori possano segnalare suggerimenti non sicuri o non conformi e che le segnalazioni siano tracciate.                                                                                   |    1    |  D/V  |
| AD.6.2 | Verificare che il feedback aggregato informi la messa a punto periodica o la generazione aumentata da recupero con corpora di codifica sicura verificati (ad esempio, OWASP Cheat Sheets).                        |    2    |   D   |
| AD.6.3 | Verificare che un sistema di valutazione a ciclo chiuso esegua test di regressione dopo ogni fine-tuning; le metriche di sicurezza devono soddisfare o superare le baseline precedenti prima della distribuzione. |    3    |  D/V  |

---

### Riferimenti

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

