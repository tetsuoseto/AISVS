# C7 Comportamento del modello, Controllo dell'uscita e Garanzia di sicurezza.

## Obiettivo di controllo

Gli output del modello devono essere strutturati, affidabili, sicuri, spiegabili e costantemente monitorati in produzione. Ciò riduce allucinazioni, violazioni della privacy, contenuti dannosi e azioni fuori controllo, aumentando al contempo la fiducia degli utenti e la conformità normativa.

---

## C7.1 Applicazione del formato di output

Schemi rigorosi, decodifica vincolata e validazione a valle interrompono contenuti malformati o malevoli prima che si propaghino.

|   #   | Descrizione                                                                                                                                                                                                    | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 7.1.1 | Verifica che gli schemi di risposta (ad es. JSON Schema) siano forniti nel prompt di sistema e che ogni output sia automaticamente convalidato; gli output non conformi innescano una correzione o un rifiuto. |    1    |  D/V  |
| 7.1.2 | Verificare che la decodifica vincolata (token di arresto, espressioni regolari, max-tokens) sia abilitata per prevenire overflow o canali laterali di prompt-injection.                                        |    1    |  D/V  |
| 7.1.3 | Verifica che i componenti a valle trattino gli output come non attendibili e li validino rispetto a schemi o deserializzatori sicuri contro l'iniezione.                                                       |    2    |  D/V  |
| 7.1.4 | Verifica che gli eventi di improper-output siano registrati, limitati per tasso e esposti al monitoraggio.                                                                                                     |    3    |   V   |

---

## C7.2 Rilevazione e Mitigazione delle Allucinazioni

La stima dell'incertezza e le strategie di fallback limitano le risposte inventate.

|   #   | Descrizione                                                                                                                                                                                     | Livello | Ruolo |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 7.2.1 | Verifica che le probabilità logaritmiche a livello di token, la coerenza dell’insieme o i rilevatori di allucinazioni finemente tarati assegnino un punteggio di fiducia a ogni risposta.       |    1    |  D/V  |
| 7.2.2 | Verifica che le risposte al di sotto di una soglia di confidenza configurabile attivino flussi di fallback (ad es., generazione potenziata dal recupero, modello secondario o revisione umana). |    1    |  D/V  |
| 7.2.3 | Verifica che gli incidenti di allucinazione siano etichettati con metadati della causa radice e inviati alle pipeline di post-mortem e di fine-tuning.                                          |    2    |  D/V  |
| 7.2.4 | Verificare che soglie e rilevatori siano ricalibrati dopo aggiornamenti significativi del modello o della base di conoscenza.                                                                   |    3    |  D/V  |
| 7.2.5 | Verifica che le visualizzazioni della dashboard monitorino i tassi di allucinazione.                                                                                                            |    3    |   V   |

---

## C7.3 Filtraggio di Sicurezza e Privacy dell'Uscita

I filtri di policy e la copertura del red-team proteggono gli utenti e i dati riservati.

|   #   | Descrizione                                                                                                                                                                                               | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 7.3.1 | Verifichi che i classificatori pre-generazione e post-generazione blocchino contenuti d'odio, molestie, autolesionismo, contenuti estremisti e contenuti sessualmente espliciti in linea con la politica. |    1    |  D/V  |
| 7.3.2 | Verifica che il rilevamento PII/PCI e la redazione automatica siano eseguiti su ogni risposta; le violazioni generano un incidente di privacy.                                                            |    1    |  D/V  |
| 7.3.3 | Verificare che le etichette di riservatezza (ad es. segreti commerciali) si propaghino attraverso le diverse modalità per prevenire la fuga di dati nel testo, nelle immagini o nel codice.               |    2    |   D   |
| 7.3.4 | Verificare che i tentativi di bypass dei filtri o le classificazioni ad alto rischio richiedano un'approvazione secondaria o una ri-autenticazione dell'utente.                                           |    3    |  D/V  |
| 7.3.5 | Verifica che le soglie di filtraggio riflettano le giurisdizioni legali e il contesto di età/ruolo dell'utente.                                                                                           |    3    |  D/V  |

---

## C7.4 Limitazione di Output e Azione

I limiti di frequenza e i meccanismi di approvazione prevengono abusi e un'autonomia eccessiva.

|   #   | Descrizione                                                                                                                                                                            | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 7.4.1 | Verificare che i limiti per utente e per chiave API limitino le richieste, i token e i costi con back-off esponenziale sugli errori 429.                                               |    1    |   D   |
| 7.4.2 | Verifica che le azioni privilegiate (scritture su file, esecuzione di codice, chiamate di rete) richiedano approvazione basata su politiche o intervento umano nel loop.               |    1    |  D/V  |
| 7.4.3 | Verifica che i controlli di coerenza multimodale garantiscano che immagini, codice e testo generati per la stessa richiesta non possano essere usati per introdurre contenuti dannosi. |    2    |  D/V  |
| 7.4.4 | Verifichi che la profondità di delega dell'agente, i limiti di ricorsione e le liste di strumenti consentiti siano configurati esplicitamente.                                         |    2    |   D   |
| 7.4.5 | Verifica che la violazione dei limiti emetta eventi di sicurezza strutturati per l'ingestione SIEM.                                                                                    |    3    |   V   |

---

## C7.5 Spiegabilità dell'output

Segnali trasparenti aumentano la fiducia degli utenti e semplificano il debugging interno.

|   #   | Descrizione                                                                                                                                                           | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 7.5.1 | Verifica che i punteggi di confidenza visibili all'utente o i brevi riepiloghi del ragionamento siano esposti quando la valutazione del rischio lo ritenga opportuno. |    2    |  D/V  |
| 7.5.2 | Verifica che le spiegazioni generate non rivelino prompt di sistema sensibili o dati proprietari.                                                                     |    2    |  D/V  |
| 7.5.3 | Verifica che il sistema catturi le probabilità logaritmiche a livello di token o le mappe di attenzione e le memorizzi per ispezione autorizzata.                     |    3    |   D   |
| 7.5.4 | Verifica che gli artefatti di spiegabilità siano versionati insieme ai rilasci dei modelli per l'auditabilità.                                                        |    3    |   V   |

---

## C7.6 Integrazione del monitoraggio

L'osservabilità in tempo reale chiude il ciclo tra sviluppo e produzione.

|   #   | Descrizione                                                                                                                                                                                                                     | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 7.6.1 | Verifica che le metriche (violazioni dello schema, tasso di allucinazioni, tossicità, perdite di informazioni personalmente identificabili (PII), latenza, costo) vengano trasmesse a una piattaforma di monitoraggio centrale. |    1    |   D   |
| 7.6.2 | Verifica che le soglie di allerta siano definite per ogni metrica di sicurezza, con percorsi di escalation disponibili in reperibilità.                                                                                         |    1    |   V   |
| 7.6.3 | Verifica che i cruscotti correlino le anomalie di output con modello/versione, flag delle funzionalità e modifiche ai dati a monte.                                                                                             |    2    |   V   |
| 7.6.4 | Verifica che i dati di monitoraggio alimentino il riaddestramento, il fine-tuning o gli aggiornamenti delle regole all'interno di un flusso di lavoro MLOps documentato.                                                        |    2    |  D/V  |
| 7.6.5 | Verifica che le pipeline di monitoraggio siano sottoposte a test di penetrazione e protette da controlli di accesso per evitare la perdita di log sensibili.                                                                    |    3    |   V   |

---

## 7.7 Salvaguardie dei media generativi

Garantire che i sistemi di IA non generino contenuti multimediali illegali, dannosi o non autorizzati, applicando vincoli di policy, validazione degli output e tracciabilità.

|   #   | Descrizione                                                                                                                                                                                                                    | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 7.7.1 | Verifica che i prompt di sistema e le istruzioni dell'utente vietino esplicitamente la generazione di deepfake illegali, dannosi o non consensuali (ad es. immagini, video, audio).                                            |    1    |  D/V  |
| 7.7.2 | Verificare che i prompt siano filtrati per tentativi di generare impersonamenti, deepfake sessualmente espliciti o contenuti che ritraggono persone reali senza consenso.                                                      |    2    |  D/V  |
| 7.7.3 | Verifica che il sistema utilizzi l'hash percettivo, il rilevamento della filigrana o l'impronta digitale per impedire la riproduzione non autorizzata di contenuti protetti da copyright.                                      |    2    |   V   |
| 7.7.4 | Verifica che tutti i media generati siano firmati digitalmente, contrassegnati con una filigrana digitale o incorporati con metadati di provenienza resistenti a manomissioni per la tracciabilità a valle.                    |    3    |  D/V  |
| 7.7.5 | Verifica che i tentativi di elusione (ad es. offuscamento del prompt, gergo, formulazioni avversarie) siano rilevati, registrati e limitati per tasso di richieste; abusi ripetuti siano segnalati ai sistemi di monitoraggio. |    3    |   V   |

## Riferimenti

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [ISO/IEC 42001:2023 – AI Management System](https://www.iso.org/obp/ui/en/)
* [OWASP Top-10 for Large Language Model Applications (2025)](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Improper Output Handling – OWASP LLM05:2025](https://genai.owasp.org/llmrisk/llm052025-improper-output-handling/)
* [Practical Techniques to Constrain LLM Output](https://mychen76.medium.com/practical-techniques-to-constraint-llm-output-in-json-format-e3e72396c670)
* [Dataiku – Structured Text Generation Guide](https://blog.dataiku.com/your-guide-to-structured-text-generation)
* [VL-Uncertainty: Detecting Hallucinations](https://arxiv.org/abs/2411.11919)
* [HaDeMiF: Hallucination Detection & Mitigation](https://openreview.net/forum?id=VwOYxPScxB)
* [Building Confidence in LLM Outputs](https://www.alkymi.io/data-science-room/building-confidence-in-llm-outputs)
* [Explainable AI & LLMs](https://duncsand.medium.com/explainable-ai-140912d31b3b)
* [LLM Red-Teaming Guide](https://www.confident-ai.com/blog/red-teaming-llms-a-step-by-step-guide)
* [Sensitive Information Disclosure in LLMs](https://virtualcyberlabs.com/llm-sensitive-information-disclosure/)
* [LangChain – Chat Model Rate Limiting](https://python.langchain.com/docs/how_to/chat_model_rate_limiting/)
* [OpenAI Rate-Limit & Exponential Back-off](https://hackernoon.com/openais-rate-limit-a-guide-to-exponential-backoff-for-llm-evaluation)
* [Arize AI – LLM Observability Platform](https://arize.com/)

