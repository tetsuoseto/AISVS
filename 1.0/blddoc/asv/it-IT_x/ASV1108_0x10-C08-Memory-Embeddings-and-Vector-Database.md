# Sicurezza della Memoria C8, degli Embedding e dei Database Vettoriali

## Obiettivo di Controllo

Gli embeddings e gli store vettoriali agiscono come la "memoria attiva" dei sistemi di AI contemporanei, accettando continuamente dati forniti dagli utenti e riportandoli nei contesti del modello tramite la Generazione Aumentata da Recupero (RAG). Se lasciata senza controllo, questa memoria può divulgare informazioni personali identificabili (PII), violare il consenso o essere invertita per ricostruire il testo originale. L'obiettivo di questa famiglia di controlli è rafforzare le pipeline di memoria e i database vettoriali affinché l'accesso sia a privilegio minimo, gli embeddings siano rispettosi della privacy, i vettori memorizzati scadano o possano essere revocati su richiesta, e la memoria per utente non contamini mai le richieste o le risposte di un altro utente.

---

## C8.1 Controlli di Accesso su Memoria e Indici RAG

Applicare controlli di accesso granulari su ogni collezione vettoriale.

|   #   | Descrizione                                                                                                                                                                                            | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 8.1.1 | Verificare che le regole di controllo accesso a livello di riga/namespace limitino le operazioni di inserimento, eliminazione e interrogazione per tenant, collezione o tag del documento.             |    1    |  D/V  |
| 8.1.2 | Verificare che le chiavi API o i JWT contengano richieste con ambito definito (ad esempio, ID delle collezioni, verbi di azione) e che vengano ruotati almeno trimestralmente.                         |    1    |  D/V  |
| 8.1.3 | Verificare che i tentativi di escalation dei privilegi (ad esempio, query di similarità tra namespace diversi) vengano rilevati e registrati in un SIEM entro 5 minuti.                                |    2    |  D/V  |
| 8.1.4 | Verificare che il database vettoriale registri nel diario di controllo l'identificatore del soggetto, l'operazione, l'ID/namespace del vettore, la soglia di somiglianza e il conteggio dei risultati. |    2    |  D/V  |
| 8.1.5 | Verificare che le decisioni di accesso vengano testate per individuare eventuali falle di bypass ogni volta che i motori vengono aggiornati o le regole di suddivisione dell'indice cambiano.          |    3    |   V   |

---

## C8.2 Sanitizzazione e Validazione dell'Embedding

Pre-selezionare il testo per dati personali identificabili (PII), oscurare o pseudonimizzare prima della vettorializzazione, e opzionalmente post-elaborare gli embedding per rimuovere segnali residui.

|   #   | Descrizione                                                                                                                                                                                                          | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 8.2.1 | Verificare che i dati PII e i dati regolamentati siano rilevati tramite classificatori automatici e mascherati, tokenizzati o eliminati prima dell'embedding.                                                        |    1    |  D/V  |
| 8.2.2 | Verificare che le pipeline di embedding rifiutino o mettano in quarantena gli input contenenti codice eseguibile o artefatti non UTF-8 che potrebbero compromettere l'indice.                                        |    1    |   D   |
| 8.2.3 | Verificare che venga applicata la sanificazione della privacy differenziale locale o metrica agli embeddings delle frasi la cui distanza da qualsiasi token PII noto scende al di sotto di una soglia configurabile. |    2    |  D/V  |
| 8.2.4 | Verificare che l'efficacia della sanitizzazione (ad esempio, il richiamo della redazione delle PII, la deriva semantica) venga convalidata almeno ogni sei mesi rispetto a corpus di riferimento.                    |    2    |   V   |
| 8.2.5 | Verifica che le configurazioni di sanitizzazione siano controllate tramite versionamento e che le modifiche vengano sottoposte a revisione tra pari.                                                                 |    3    |  D/V  |

---

## C8.3 Scadenza, Revoca e Cancellazione della Memoria

Il GDPR "diritto all'oblio" e leggi simili richiedono la cancellazione tempestiva; pertanto, gli archivi vettoriali devono supportare TTL, eliminazioni definitive e tomb-stoning affinché i vettori revocati non possano essere recuperati o reindicizzati.

|   #   | Descrizione                                                                                                                                                                                         | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 8.3.1 | Verificare che ogni vettore e record di metadata possieda un TTL o un’etichetta di conservazione esplicita rispettata dai processi automatici di pulizia.                                           |    1    |  D/V  |
| 8.3.2 | Verificare che le richieste di eliminazione avviate dall'utente cancellino vettori, metadati, copie della cache e indici derivati entro 30 giorni.                                                  |    1    |  D/V  |
| 8.3.3 | Verificare che le eliminazioni logiche siano seguite dalla cancellazione crittografica dei blocchi di archiviazione se l'hardware lo supporta, oppure dalla distruzione della chiave del key vault. |    2    |   D   |
| 8.3.4 | Verificare che i vettori scaduti siano esclusi dai risultati della ricerca dei vicini più prossimi in meno di 500 ms dopo la scadenza.                                                              |    3    |  D/V  |

---

## C8.4 Prevenire l'inversione e la fuoriuscita dell'embedding

Le recenti difese—sovrapposizione del rumore, reti di proiezione, perturbazione dei neuroni della privacy e crittografia a livello di applicazione—possono ridurre i tassi di inversione a livello di token sotto il 5%.

|   #   | Descrizione                                                                                                                                                                                         | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 8.4.1 | Verificare che esista un modello di minaccia formale che copra gli attacchi di inversione, di membership e di inferenza degli attributi e che venga revisionato annualmente.                        |    1    |   V   |
| 8.4.2 | Verificare che la crittografia a livello applicativo o la crittografia ricercabile proteggano i vettori da letture dirette da parte degli amministratori dell'infrastruttura o del personale cloud. |    2    |  D/V  |
| 8.4.3 | Verificare che i parametri di difesa (ε per DP, rumore σ, rango di proiezione k) bilancino la privacy ≥ 99 % protezione del token e l’utilità ≤ 3 % perdita di accuratezza.                         |    3    |   V   |
| 8.4.4 | Verificare che le metriche di resilienza all'inversione facciano parte delle soglie di rilascio per gli aggiornamenti del modello, con budget di regressione definiti.                              |    3    |  D/V  |

---

## C8.5 Applicazione del Controllo di Ambito per la Memoria Specifica dell'Utente

La perdita di dati tra tenant rimane un rischio principale per RAG: query di similarità filtrate in modo improprio possono far emergere documenti privati di un altro cliente.

|   #   | Descrizione                                                                                                                                                                         | Livello | Ruolo |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 8.5.1 | Verificare che ogni query di recupero sia filtrata successivamente dall’ID del tenant/utente prima di essere inviata al prompt LLM.                                                 |    1    |  D/V  |
| 8.5.2 | Verificare che i nomi delle collezioni o gli ID con namespace siano salati per utente o tenant in modo che i vettori non possano collidere tra gli ambiti.                          |    1    |   D   |
| 8.5.3 | Verificare che i risultati di similarità superiori a una soglia di distanza configurabile ma al di fuori dell'ambito del chiamante vengano scartati e attivino avvisi di sicurezza. |    2    |  D/V  |
| 8.5.4 | Verificare che i test di stress multi-tenant simulino query avversarie che tentano di recuperare documenti fuori ambito e dimostrino assenza totale di perdite.                     |    2    |   V   |
| 8.5.5 | Verificare che le chiavi di crittografia siano separate per tenant, garantendo l'isolamento crittografico anche se lo storage fisico è condiviso.                                   |    3    |  D/V  |

---

## C8.6 Sicurezza avanzata del sistema di memoria

Controlli di sicurezza per architetture di memoria sofisticate, comprese la memoria episodica, semantica e di lavoro, con requisiti specifici di isolamento e validazione.

|   #   | Descrizione                                                                                                                                                                                                                                                                                       | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 8.6.1 | Verificare che i diversi tipi di memoria (episodica, semantica, di lavoro) abbiano contesti di sicurezza isolati con controlli di accesso basati sui ruoli, chiavi di crittografia separate e modelli di accesso documentati per ciascun tipo di memoria.                                         |    1    |  D/V  |
| 8.6.2 | Verificare che i processi di consolidamento della memoria includano la validazione della sicurezza per prevenire l'iniezione di memorie dannose attraverso la sanificazione dei contenuti, la verifica delle fonti e i controlli di integrità prima dell'archiviazione.                           |    2    |  D/V  |
| 8.6.3 | Verificare che le query di recupero della memoria siano validate e sanificate per prevenire l'estrazione di informazioni non autorizzate tramite l'analisi dei modelli di query, l'applicazione del controllo degli accessi e il filtraggio dei risultati.                                        |    2    |  D/V  |
| 8.6.4 | Verificare che i meccanismi di oblio della memoria eliminino in modo sicuro le informazioni sensibili con garanzie di cancellazione crittografica utilizzando la cancellazione delle chiavi, la sovrascrittura multipla o la cancellazione sicura basata su hardware con certificati di verifica. |    3    |  D/V  |
| 8.6.5 | Verificare che l'integrità del sistema di memoria sia continuamente monitorata per modifiche non autorizzate o corruzioni mediante checksum, registri di controllo e avvisi automatici quando il contenuto della memoria cambia al di fuori delle operazioni normali.                             |    3    |  D/V  |

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

