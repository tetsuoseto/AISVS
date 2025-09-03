# Appendice D: Governance e Verifica della Programmazione Sicura Assistita dall'IA

## Obiettivo

Questo capitolo definisce controlli organizzativi di base per l'uso sicuro ed efficace degli strumenti di programmazione assistiti dall'IA durante lo sviluppo del software, garantendo sicurezza e tracciabilità lungo il ciclo di vita dello sviluppo del software (SDLC).

---

## AD.1 Flusso di lavoro per la programmazione sicura assistita dall'IA

Integra strumenti di IA nel ciclo di vita dello sviluppo software sicuro dell'organizzazione (SSDLC) senza indebolire i cancelli di sicurezza esistenti.

|   #    | Descrizione                                                                                                                                                                                     | Livello | Ruolo |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AD.1.1 | Verifica che un flusso di lavoro documentato descriva quando e come gli strumenti di IA possono generare, rifattorizzare o rivedere il codice.                                                  |    1    |  D/V  |
| AD.1.2 | Verifica che il flusso di lavoroMappi ciascuna fase del SSDLC (progettazione, implementazione, revisione del codice, test, messa in produzione).                                                |    2    |   D   |
| AD.1.3 | Verifica che le metriche (ad es. densità delle vulnerabilità, tempo medio di rilevamento) siano raccolte sul codice prodotto dall'IA e confrontate con linee di base basate solo su dati umani. |    3    |  D/V  |

---

## AD.2 Qualificazione degli strumenti di IA e Modellazione delle minacce

Garantire che gli strumenti di codifica basati sull'IA siano valutati in termini di capacità di sicurezza, rischio e impatto della supply‑chain prima dell'adozione.

|   #    | Descrizione                                                                                                                                                                                                 | Livello | Ruolo |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AD.2.1 | Verifica che un modello di minaccia per ogni strumento di IA identifichi l'uso improprio, l'inversione del modello, la fuga di dati e i rischi della catena di dipendenze.                                  |    1    |  D/V  |
| AD.2.2 | Verifica che le valutazioni degli strumenti includano l'analisi statica/dinamica di eventuali componenti locali e la valutazione dei punti finali SaaS (TLS, autenticazione/autorizzazione, registrazione). |    2    |   D   |
| AD.2.3 | Verificare che le valutazioni seguano un quadro di riferimento riconosciuto e che vengano rieseguite dopo cambiamenti di versione principali.                                                               |    3    |  D/V  |

---

## AD.3 Prompt Sicuro e Gestione del Contesto

Previeni la fuga di segreti, codice proprietario e dati personali durante la creazione di prompt o contesti per modelli di IA.

|   #    | Descrizione                                                                                                                                                                                    | Livello | Ruolo |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AD.3.1 | Verifichi che le linee guida scritte vietino l'invio di segreti, credenziali o dati classificati nei prompt.                                                                                   |    1    |  D/V  |
| AD.3.2 | Verifica che i controlli tecnici (redazione client-side, filtri di contesto approvati) rimuovano automaticamente artefatti sensibili.                                                          |    2    |   D   |
| AD.3.3 | Verifica che i prompt e le risposte siano tokenizzati, crittografati in transito e a riposo, e che i periodi di conservazione dei dati siano conformi alla policy di classificazione dei dati. |    3    |  D/V  |

---

## AD.4 Validazione del codice generato dall'IA

Rileva e correggi le vulnerabilità introdotte dall'output dell'IA prima che il codice venga unito o distribuito.

|   #    | Descrizione                                                                                                                                                                      | Livello | Ruolo |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AD.4.1 | Verifica che il codice generato dall'IA sia sempre soggetto a revisione da parte di un essere umano.                                                                             |    1    |  D/V  |
| AD.4.2 | Verifica che gli scanner automatizzati (SAST/IAST/DAST) vengano eseguiti su ogni pull request contenente codice AI‑generato e blocchino le fusioni in caso di scoperte critiche. |    2    |   D   |
| AD.4.3 | Verifica che fuzzing differenziale o property‑based tests dimostrino comportamenti critici per la sicurezza (ad es. validazione degli input, logica di autorizzazione).          |    3    |  D/V  |

---

## AD.5 Esplicabilità e tracciabilità dei suggerimenti di codice

Fornite ai revisori e agli sviluppatori una visione approfondita del motivo per cui è stata fatta una proposta e di come sia evoluta.

|   #    | Descrizione                                                                                                                                                                                        | Livello | Ruolo |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AD.5.1 | Verifica che le coppie prompt/risposta siano registrate con gli ID di commit.                                                                                                                      |    1    |  D/V  |
| AD.5.2 | Verificare che gli sviluppatori possano rendere disponibili citazioni del modello (frammenti di addestramento, documentazione) a supporto di un suggerimento.                                      |    2    |   D   |
| AD.5.3 | Verificare che i rapporti di spiegabilità siano archiviati insieme agli artefatti di progettazione e citati nelle revisioni di sicurezza, soddisfacendo i principi di tracciabilità ISO/IEC 42001. |    3    |  D/V  |

---

## AD.6 Feedback continuo e Fine‑Tuning del modello

Migliorare nel tempo le prestazioni di sicurezza del modello, evitando la deriva negativa.

|   #    | Descrizione                                                                                                                                                                                                                            | Livello | Ruolo |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AD.6.1 | Verificare che gli sviluppatori possano contrassegnare suggerimenti non sicuri o non conformi e che le segnalazioni siano tracciate.                                                                                                   |    1    |  D/V  |
| AD.6.2 | Verifica che il feedback aggregato informi un fine‑tuning periodico o retrieval‑augmented generation con corpora di codifica‑sicura verificati (ad es. OWASP Cheat Sheets).                                                            |    2    |   D   |
| AD.6.3 | Verifica che un sistema di valutazione a ciclo chiuso esegua test di regressione dopo ogni messa a punto; le metriche di sicurezza devono soddisfare o superare i parametri di riferimento precedenti prima della messa in produzione. |    3    |  D/V  |

---

### Riferimenti

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

