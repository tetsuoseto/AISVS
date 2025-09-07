# Comportamento del Modello C7, Controllo dell'Uscita e Garanzia di Sicurezza

## Obiettivo di Controllo

I risultati del modello devono essere strutturati, affidabili, sicuri, spiegabili e costantemente monitorati in produzione. Questo riduce le allucinazioni, le fughe di dati personali, i contenuti dannosi e le azioni incontrollate, aumentando al contempo la fiducia degli utenti e la conformità normativa.

---

## C7.1 Applicazione del formato di output

Schemi rigorosi, decodifica vincolata e validazione downstream fermano contenuti malformati o dannosi prima che si propaghino.

|   #   | Descrizione                                                                                                                                                                                                            | Livello | Ruolo |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 7.1.1 | Verificare che gli schemi di risposta (ad esempio, JSON Schema) siano forniti nel prompt di sistema e che ogni output venga automaticamente convalidato; gli output non conformi attivano la riparazione o il rifiuto. |    1    |  D/V  |
| 7.1.2 | Verificare che la decodifica vincolata (token di stop, regex, max-token) sia abilitata per prevenire overflow o canali laterali di iniezione nel prompt.                                                               |    1    |  D/V  |
| 7.1.3 | Verificare che i componenti a valle considerino gli output come non attendibili e li convalidino rispetto agli schemi o utilizzino de-serializzatori sicuri contro le injection.                                       |    2    |  D/V  |
| 7.1.4 | Verificare che gli eventi di output improprio siano registrati, soggetti a limitazione della frequenza e resi visibili al monitoraggio.                                                                                |    3    |   V   |

---

## C7.2 Rilevamento e Mitigazione delle Allucinazioni

La stima dell'incertezza e le strategie di fallback limitano le risposte inventate.

|   #   | Descrizione                                                                                                                                                                                                    | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 7.2.1 | Verificare che le log-probabilità a livello di token, la coerenza autonoma dell'ensemble o i rilevatori di allucinazioni messa a punto assegnino un punteggio di confidenza a ogni risposta.                   |    1    |  D/V  |
| 7.2.2 | Verificare che le risposte al di sotto di una soglia di confidenza configurabile attivino flussi di lavoro di fallback (ad esempio, generazione aumentata dal recupero, modello secondario o revisione umana). |    1    |  D/V  |
| 7.2.3 | Verificare che gli incidenti di allucinazione siano etichettati con metadati sulla causa principale e inseriti nelle pipeline di post-mortem e di fine-tuning.                                                 |    2    |  D/V  |
| 7.2.4 | Verificare che le soglie e i rilevatori vengano ricalibrati dopo aggiornamenti importanti del modello o della base di conoscenza.                                                                              |    3    |  D/V  |
| 7.2.5 | Verificare che le visualizzazioni della dashboard traccino i tassi di allucinazione.                                                                                                                           |    3    |   V   |

---

## C7.3 Filtraggio di Sicurezza e Privacy in Output

I filtri di policy e la copertura del red team proteggono gli utenti e i dati riservati.

|   #   | Descrizione                                                                                                                                                                              | Livello | Ruolo |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 7.3.1 | Verificare che i classificatori pre e post-generazione blocchino contenuti di odio, molestie, autolesionismo, estremismo e contenuti sessualmente espliciti in conformità con la policy. |    1    |  D/V  |
| 7.3.2 | Verificare che il rilevamento di PII/PCI e la redazione automatica vengano eseguiti su ogni risposta; le violazioni comportano la segnalazione di un incidente sulla privacy.            |    1    |  D/V  |
| 7.3.3 | Verificare che i tag di riservatezza (ad esempio, segreti commerciali) si propaghino attraverso le modalità per prevenire la fuga di informazioni in testi, immagini o codice.           |    2    |   D   |
| 7.3.4 | Verificare che i tentativi di bypassare il filtro o le classificazioni ad alto rischio richiedano un'approvazione secondaria o una ri-autenticazione dell'utente.                        |    3    |  D/V  |
| 7.3.5 | Verificare che le soglie di filtraggio riflettano le giurisdizioni legali e il contesto di età/ruolo dell'utente.                                                                        |    3    |  D/V  |

---

## C7.4 Limitazione dell'Output e delle Azioni

I limiti di velocità e i gate di approvazione prevengono abusi e autonomia eccessiva.

|   #   | Descrizione                                                                                                                                                                                  | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 7.4.1 | Verificare che le quote per utente e per chiave API limitino le richieste, i token e i costi con un back-off esponenziale sugli errori 429.                                                  |    1    |   D   |
| 7.4.2 | Verificare che le azioni privilegiate (scritture di file, esecuzione di codice, chiamate di rete) richiedano l'approvazione basata su policy o l'intervento umano.                           |    1    |  D/V  |
| 7.4.3 | Verifica che i controlli di coerenza cross-modale garantiscano che immagini, codice e testo generati per la stessa richiesta non possano essere utilizzati per introdurre contenuti dannosi. |    2    |  D/V  |
| 7.4.4 | Verificare che la profondità di delega degli agenti, i limiti di ricorsione e le liste degli strumenti consentiti siano configurati esplicitamente.                                          |    2    |   D   |
| 7.4.5 | Verificare che la violazione dei limiti generi eventi di sicurezza strutturati per l'ingestione nel SIEM.                                                                                    |    3    |   V   |

---

## C7.5 Spiegabilità dell'Output

I segnali trasparenti migliorano la fiducia degli utenti e il debug interno.

|   #   | Descrizione                                                                                                                                                              | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 7.5.1 | Verificare che i punteggi di confidenza rivolti all’utente o i brevi riassunti delle motivazioni siano esposti quando la valutazione del rischio lo ritiene appropriato. |    2    |  D/V  |
| 7.5.2 | Verificare che le spiegazioni generate evitino di rivelare prompt di sistema sensibili o dati proprietari.                                                               |    2    |  D/V  |
| 7.5.3 | Verificare che il sistema acquisisca le log-probabilità a livello di token o le mappe di attenzione e le memorizzi per ispezioni autorizzate.                            |    3    |   D   |
| 7.5.4 | Verificare che gli artefatti di spiegabilità siano sottoposti a controllo delle versioni insieme alle release dei modelli per garantire la tracciabilità.                |    3    |   V   |

---

## C7.6 Integrazione del Monitoraggio

L'osservabilità in tempo reale chiude il ciclo tra sviluppo e produzione.

|   #   | Descrizione                                                                                                                                                                              | Livello | Ruolo |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 7.6.1 | Verificare che le metriche (violazioni dello schema, tasso di allucinazioni, tossicità, fughe di dati PII, latenza, costo) vengano trasmesse a una piattaforma centrale di monitoraggio. |    1    |   D   |
| 7.6.2 | Verificare che le soglie di allerta siano definite per ogni metrica di sicurezza, con percorsi di escalation per il personale di reperibilità.                                           |    1    |   V   |
| 7.6.3 | Verificare che i cruscotti mettano in relazione le anomalie di output con il modello/versione, il flag delle funzionalità e le modifiche ai dati upstream.                               |    2    |   V   |
| 7.6.4 | Verificare che i dati di monitoraggio vengano reinseriti nel processo di retraining, fine-tuning o aggiornamento delle regole all'interno di un flusso di lavoro MLOps documentato.      |    2    |  D/V  |
| 7.6.5 | Verificare che le pipeline di monitoraggio siano sottoposte a penetration test e controllate negli accessi per evitare la fuoriuscita di log sensibili.                                  |    3    |   V   |

---

## 7.7 Salvaguardie per i Media Generativi

Garantire che i sistemi di IA non generino contenuti multimediali illegali, dannosi o non autorizzati, applicando vincoli di policy, convalida dell'output e tracciabilità.

|   #   | Descrizione                                                                                                                                                                                                                                         | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 7.7.1 | Verificare che i prompt di sistema e le istruzioni per l'utente proibiscano esplicitamente la generazione di contenuti deepfake illegali, dannosi o non consensuali (ad esempio, immagini, video, audio).                                           |    1    |  D/V  |
| 7.7.2 | Verificare che i prompt siano filtrati per tentativi di generare imitazioni, deepfake sessualmente espliciti o media che ritraggono persone reali senza consenso.                                                                                   |    2    |  D/V  |
| 7.7.3 | Verifica che il sistema utilizzi hashing percettivo, rilevamento di watermark o fingerprinting per prevenire la riproduzione non autorizzata di contenuti protetti da copyright.                                                                    |    2    |   V   |
| 7.7.4 | Verificare che tutti i media generati siano firmati crittograficamente, watermarkati o incorporati con metadati di provenienza resistenti alla manomissione per la tracciabilità a valle.                                                           |    3    |  D/V  |
| 7.7.5 | Verificare che i tentativi di bypass (ad esempio, offuscamento del prompt, gergo, formulazioni avversarie) siano rilevati, registrati e soggetti a limitazione di frequenza; gli abusi ripetuti devono essere segnalati ai sistemi di monitoraggio. |    3    |   V   |

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

