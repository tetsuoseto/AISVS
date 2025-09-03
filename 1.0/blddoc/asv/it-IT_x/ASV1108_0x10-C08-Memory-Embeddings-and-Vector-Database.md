# C8 Memory, Embeddings e Sicurezza del Database Vettoriale

## Obiettivo di controllo

Rappresentazioni vettoriali e archivi vettoriali fungono da "memoria attiva" dei sistemi IA contemporanei, accettando continuamente dati forniti dagli utenti e riportandoli nei contesti del modello tramite Generazione potenziata dal recupero (RAG). Se non governata, questa memoria può esporre PII (Informazioni di identificazione personale), violare il consenso o essere invertita per ricostruire il testo originale. L'obiettivo di questa famiglia di controlli è rafforzare le pipeline di memoria e i database vettoriali in modo che l'accesso sia conforme al principio del minimo privilegio, le rappresentazioni vettoriali preservino la privacy, i vettori memorizzati scadano o possano essere revocati su richiesta, e la memoria per utente non contamini mai le richieste o i completamenti di un altro utente.

---

## C8.1 Controlli di accesso su indici di memoria e RAG

Applica controlli di accesso granulare su ogni collezione di vettori.

|   #   | Descrizione                                                                                                                                                                                    | Livello | Ruolo |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 8.1.1 | Verifica che le regole di controllo degli accessi a livello di riga/namespace limitino le operazioni di inserimento, eliminazione e interrogazione per tenant, collezione o tag del documento. |    1    |  D/V  |
| 8.1.2 | Verifica che le chiavi API o i JWT contengano claim con ambito definito (ad es. ID delle collezioni, verbi di azione) e che siano ruotate almeno ogni trimestre.                               |    1    |  D/V  |
| 8.1.3 | Verifica che i tentativi di elevazione dei privilegi (ad es., query di similarità tra namespace) siano rilevati e registrati in un SIEM entro 5 minuti.                                        |    2    |  D/V  |
| 8.1.4 | Verifica che il log di auditing del DB vettoriale registri identificatore del soggetto, operazione, ID del vettore/spazio dei nomi, soglia di similarità e conteggio dei risultati.            |    2    |  D/V  |
| 8.1.5 | Verificare che le decisioni di accesso siano testate per vulnerabilità di bypass ogni volta che i motori sono aggiornati o cambiano le regole di sharding degli indici.                        |    3    |   V   |

---

## C8.2 Sanitizzazione e Validazione degli embedding

Eseguire uno screening preliminare del testo per informazioni di identificazione personale (PII), oscurare o pseudonimizzare prima della vettorializzazione, e, facoltativamente, post-elaborare le rappresentazioni vettoriali per eliminare segnali residui.

|   #   | Descrizione                                                                                                                                                                                                         | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 8.2.1 | Verificare che PII e dati regolamentati siano rilevati tramite classificatori automatizzati e mascherati, tokenizzati o scartati prima dell'embedding.                                                              |    1    |  D/V  |
| 8.2.2 | Verifichi che le pipeline di embedding rifiutino o mettano in quarantena gli input contenenti codice eseguibile o artefatti non UTF-8 che potrebbero compromettere l'indice.                                        |    1    |   D   |
| 8.2.3 | Verifichi che sia applicata la sanitizzazione della privacy differenziale locale o basata su metriche agli embedding di frasi la cui distanza da qualsiasi token PII noto sia inferiore a una soglia configurabile. |    2    |  D/V  |
| 8.2.4 | Verificare che l'efficacia della sanitizzazione (ad es. richiamo del mascheramento di PII, deriva semantica) sia validata almeno semestralmente su corpora di riferimento.                                          |    2    |   V   |
| 8.2.5 | Verifica che le configurazioni di sanificazione siano versionate e che le modifiche siano sottoposte a revisione tra pari.                                                                                          |    3    |  D/V  |

---

## C8.3 Scadenza della memoria, Revoca e Cancellazione

GDPR e leggi simili sul diritto all'oblio richiedono una cancellazione tempestiva; gli archivi vettoriali devono quindi supportare TTLs, cancellazioni definitive e tomb-stoning affinché i vettori revocati non possano essere recuperati o indicizzati di nuovo.

|   #   | Descrizione                                                                                                                                                                                         | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 8.3.1 | Verifica che ogni vettore e ogni record di metadati contengano un TTL o un'etichetta esplicita di conservazione che sia rispettata dai lavori di pulizia automatizzata.                             |    1    |  D/V  |
| 8.3.2 | Verificare che le richieste di eliminazione avviate dall'utente cancellino vettori, metadati, copie nella cache e indici derivati entro 30 giorni.                                                  |    1    |  D/V  |
| 8.3.3 | Verifica che le cancellazioni logiche siano seguite dalla cancellazione crittografica dei blocchi di archiviazione, se l'hardware lo supporta, oppure dalla distruzione delle chiavi nel Key Vault. |    2    |   D   |
| 8.3.4 | Verifica che i vettori scaduti siano esclusi dai risultati della ricerca del vicino più prossimo entro < 500 ms dalla scadenza.                                                                     |    3    |  D/V  |

---

## C8.4 Prevenire l'inversione dell'embedding e la fuga di dati

Difese recenti—superposizione del rumore, reti di proiezione, perturbazione dei neuroni per la privacy e crittografia a livello di applicazione—possono ridurre i tassi di inversione a livello di token al di sotto del 5%.

|   #   | Descrizione                                                                                                                                                                                                  | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 8.4.1 | Verifica che esista un modello di minaccia formale che copra gli attacchi di inversione, di appartenenza e di inferenza degli attributi, e che venga revisionato annualmente.                                |    1    |   V   |
| 8.4.2 | Verifica che la crittografia a livello di applicazione o la crittografia ricercabile proteggano i vettori dalle letture dirette da parte degli amministratori dell'infrastruttura o del personale del cloud. |    2    |  D/V  |
| 8.4.3 | Verifica che i parametri di difesa (ε per DP, rumore σ, rango di proiezione k) bilancino la privacy differenziale ≥ 99 % protezione dei token e l'utilità ≤ 3 % perdita di accuratezza.                      |    3    |   V   |
| 8.4.4 | Verifica che le metriche di resilienza all'inversione siano parte dei gate di rilascio per gli aggiornamenti dei modelli, con budget di regressione definiti.                                                |    3    |  D/V  |

---

## C8.5 Applicazione dell'ambito per la memoria specifica dell'utente

La fuga tra tenant rimane tra i principali rischi della RAG: query di similarità filtrate in modo improprio possono esporre documenti privati di un altro cliente.

|   #   | Descrizione                                                                                                                                                                               | Livello | Ruolo |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 8.5.1 | Verifica che ogni query di recupero sia post-filtrata per l'ID del tenant e dell'utente prima di essere inviata al prompt LLM.                                                            |    1    |  D/V  |
| 8.5.2 | Verifica che i nomi delle collezioni o gli ID con namespace siano salati per utente o tenant, in modo che i vettori non possano collidere tra gli ambiti.                                 |    1    |   D   |
| 8.5.3 | Verificare che i risultati di similarità superiori a una soglia di distanza configurabile ma al di fuori dell'ambito del richiedente vengano scartati e che scattino avvisi di sicurezza. |    2    |  D/V  |
| 8.5.4 | Verifica che i test di stress multi-tenant simulino richieste avversarie volte a recuperare documenti fuori dal perimetro e dimostrino l'assenza di fuga di dati.                         |    2    |   V   |
| 8.5.5 | Verifichi che le chiavi di cifratura siano separate per ogni tenant, garantendo l'isolamento crittografico anche se l'archiviazione fisica è condivisa.                                   |    3    |  D/V  |

---

## C8.6 Sicurezza avanzata del sistema di memoria

Controlli di sicurezza per architetture di memoria sofisticate che includono memoria episodica, semantica e memoria di lavoro, con requisiti specifici di isolamento e validazione.

|   #   | Descrizione                                                                                                                                                                                                                                                                                                          | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 8.6.1 | Verifica che i diversi tipi di memoria (episodica, semantica e di lavoro) abbiano contesti di sicurezza isolati con controlli di accesso basati sui ruoli, chiavi di cifratura separate e schemi di accesso documentati per ciascun tipo di memoria.                                                                 |    1    |  D/V  |
| 8.6.2 | Verifica che i processi di consolidamento della memoria includano la validazione di sicurezza per prevenire l'iniezione di memorie dannose tramite la sanitizzazione dei contenuti, la verifica della fonte e i controlli di integrità prima della memorizzazione.                                                   |    2    |  D/V  |
| 8.6.3 | Verifica che le query di recupero della memoria siano valide e sanificate per impedire l'estrazione di informazioni non autorizzate mediante analisi dei pattern di query, l'applicazione del controllo degli accessi e il filtraggio dei risultati.                                                                 |    2    |  D/V  |
| 8.6.4 | Verificare che i meccanismi di cancellazione della memoria eliminino in modo sicuro le informazioni sensibili con garanzie di cancellazione crittografica, utilizzando l'eliminazione della chiave, la sovrascrittura a più passaggi o la cancellazione sicura basata su hardware-based con certificati di verifica. |    3    |  D/V  |
| 8.6.5 | Verifica che l'integrità del sistema di memoria sia costantemente monitorata per modifiche non autorizzate o corruzione tramite somme di controllo, registri di audit e avvisi automatici quando il contenuto della memoria cambia al di fuori delle operazioni normali.                                             |    3    |  D/V  |

---

## Riferimenti

* [Vector database security: Pinecone – IronCore Labs](https://ironcorelabs.com/vectordbs/pinecone-security/)
* [Securing the Backbone of AI: Safeguarding Vector Databases and Embeddings – Privacera](https://privacera.com/blog/securing-the-backbone-of-ai-safeguarding-vector-databases-and-embeddings/)
* [Enhancing Data Security with RBAC of Qdrant Vector Database – AI Advances](https://ai.gopubby.com/enhancing-data-security-with-role-based-access-control-of-qdrant-vector-database-3878769bec83)
* [Mitigating Privacy Risks in LLM Embeddings from Embedding Inversion – arXiv](https://arxiv.org/html/2411.05034v1)
* [DPPN: Detecting and Perturbing Privacy-Sensitive Neurons – OpenReview](https://openreview.net/forum?id=DF5TVzpTW0)
* [Art. 17 GDPR – Right to Erasure](https://gdpr-info.eu/art-17-gdpr/)
* [Sensitive Data in Text Embeddings Is Recoverable – Tonic.ai](https://www.tonic.ai/blog/sensitive-data-in-text-embeddings-is-recoverable)
* [PII Identification and Removal – NVIDIA NeMo Docs](https://docs.nvidia.com/nemo-framework/user-guide/latest/datacuration/personalidentifiableinformationidentificationandremoval.html)
* [De-identifying Sensitive Data – Google Cloud DLP](https://cloud.google.com/sensitive-data-protection/docs/deidentify-sensitive-data)
* [Remove PII from Conversations Using Sensitive Information Filters – AWS Bedrock Guardrails](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails-sensitive-filters.html)
* [Think Your RAG Is Secure? Think Again – Medium](https://medium.com/%40vijay.poudel1/think-your-rag-is-secure-think-again-heres-how-to-actually-lock-it-down-c4c30e3864e7)
* [Design a Secure Multitenant RAG Inferencing Solution – Microsoft Learn](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/guide/secure-multitenant-rag)
* [Best Practices for Multi-Tenancy RAG with Milvus – Milvus Blog](https://milvus.io/blog/build-multi-tenancy-rag-with-milvus-best-practices-part-one.md)

