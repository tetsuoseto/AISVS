# C1 Governance dei dati di addestramento e gestione dei bias

## Obiettivo di controllo

I dati di addestramento devono essere reperiti, gestiti e mantenuti in modo da preservarne la provenienza, la sicurezza, la qualità e l'equità. Ciò adempie agli obblighi legali e riduce i rischi di pregiudizio, avvelenamento dei dati o violazioni della privacy che emergono durante l'addestramento e che potrebbero influire sull'intero ciclo di vita dell'IA.

---

## C1.1 Provenienza dei dati di addestramento

Mantenere un inventario verificabile di tutti i dataset, accettare solo fonti affidabili e registrare ogni modifica per l'auditabilità.

|   #   | Descrizione                                                                                                                                                                                                                       | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 1.1.1 | Verificare che sia mantenuto un inventario aggiornato di ogni fonte di dati di addestramento (origine, custode/proprietario, licenza, metodo di raccolta, vincoli d'uso previsti e storia del trattamento).                       |    1    |  D/V  |
| 1.1.2 | Verificare che i processi sui dati di addestramento escludano caratteristiche, attributi o campi non necessari (ad esempio metadati inutilizzati, informazioni personali identificabili (PII) sensibili, dati di test trapelati). |    1    |  D/V  |
| 1.1.3 | Verifica che tutte le modifiche al set di dati siano soggette a un flusso di approvazione registrato.                                                                                                                             |    2    |  D/V  |
| 1.1.4 | Verificare che i dataset o i sottoinsiemi siano contrassegnati con filigrana o impronta digitale, ove possibile.                                                                                                                  |    3    |  D/V  |

---

## C1.2 Sicurezza e integrità dei dati di addestramento

Limitare l'accesso ai dati di addestramento, crittografare i dati a riposo e in transito, e verificarne l'integrità per prevenire manomissioni, furti o avvelenamento dei dati.

|   #   | Descrizione                                                                                                                                                                                  | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 1.2.1 | Verifica che i controlli di accesso proteggano l'archiviazione dei dati di addestramento e le pipeline.                                                                                      |    1    |  D/V  |
| 1.2.2 | Verifica che tutti gli accessi ai dati di addestramento siano registrati, inclusi l'utente, l'ora e l'azione.                                                                                |    2    |  D/V  |
| 1.2.3 | Verificare che i set di dati di addestramento siano cifrati sia in transito che a riposo, utilizzando algoritmi crittografici standard di settore e pratiche di gestione delle chiavi.       |    2    |  D/V  |
| 1.2.4 | Verifica che vengano utilizzati hash crittografici o firme digitali per garantire l'integrità dei dati durante l'archiviazione e il trasferimento dei dati di addestramento.                 |    2    |  D/V  |
| 1.2.5 | Verificare che le tecniche di rilevamento automatico siano applicate per prevenire modifiche non autorizzate o la corruzione dei dati di addestramento.                                      |    2    |  D/V  |
| 1.2.6 | Verificare che i dati di addestramento obsoleti siano eliminati in modo sicuro o anonimizzati.                                                                                               |    2    |  D/V  |
| 1.2.7 | Verificare che tutte le versioni del dataset di addestramento siano identificate in modo univoco, archiviate in modo immutabile e auditabili per supportare il rollback e l’analisi forense. |    3    |  D/V  |

---

## C1.3 Qualità, integrità e sicurezza dell'etichettatura dei dati di addestramento

Proteggere le etichette e richiedere una revisione tecnica per i dati critici.

|   #   | Descrizione                                                                                                                                                                                                                                  | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 1.3.1 | Verificare che gli hash crittografici o le firme digitali siano applicati agli artefatti di etichettatura per garantire la loro integrità e autenticità.                                                                                     |    2    |  D/V  |
| 1.3.2 | Verifichi che le interfacce di etichettatura e le piattaforme applichino controlli di accesso robusti, mantengano registri di audit a prova di manomissione di tutte le attività di etichettatura e proteggano da modifiche non autorizzate. |    2    |  D/V  |
| 1.3.3 | Verifica che le informazioni sensibili presenti nelle etichette siano oscurate, anonimizzate o criptate a livello di campo dati a riposo e in transito.                                                                                      |    3    |  D/V  |

---

## C1.4 Garanzia della qualità e della sicurezza dei dati di addestramento

Combinare la validazione automatica, controlli manuali a campione e interventi correttivi registrati per garantire l'affidabilità del set di dati.

|   #   | Descrizione                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 1.4.1 | Verifica che i test automatizzati catturino errori di formato e valori nulli in ogni ingestione o trasformazione significativa dei dati.                                                                                                                                                                                                                                                                                                                                                |    1    |   D   |
| 1.4.2 | Verifica che le pipeline di addestramento e di fine-tuning degli LLM implementino il rilevamento dell'avvelenamento e la validazione dell'integrità dei dati (ad es. metodi statistici, rilevamento di outlier, analisi degli embedding) per identificare potenziali attacchi di avvelenamento (ad es. ribaltamento delle etichette, inserimento di trigger di backdoor, comandi di cambio di ruolo, attacchi a istanze influenti) o corruzione involontaria dei dati di addestramento. |    2    |  D/V  |
| 1.4.3 | Verifica che siano implementate e tarate difese adeguate, come l'addestramento avversario (utilizzando esempi avversari generati), l'aumento dei dati con input perturbati o tecniche di ottimizzazione robuste, in base alla valutazione del rischio.                                                                                                                                                                                                                                  |    3    |  D/V  |
| 1.4.4 | Verificare che le etichette generate automaticamente (ad es. tramite modelli linguistici di grandi dimensioni (LLMs) o supervisione debole) siano soggette a soglie di confidenza e controlli di coerenza per rilevare etichette allucinatorie, fuorvianti o con bassa confidenza.                                                                                                                                                                                                      |    2    |  D/V  |
| 1.4.5 | Verifica che i test automatizzati rilevino gli sbilanciamenti delle etichette in ogni ingestione o trasformazione significativa dei dati.                                                                                                                                                                                                                                                                                                                                               |    3    |   D   |

---

## C1.5 Provenienza e tracciabilità dei dati

Traccia l'intero percorso di ogni dato dall'origine all'input del modello per auditabilità e gestione degli incidenti.

|   #   | Descrizione                                                                                                                                                                                                                                                                             | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 1.5.1 | Verificare che la tracciabilità di ogni punto dati, comprese tutte le trasformazioni, le augmentazioni e le fusioni, sia registrata e possa essere ricostruita.                                                                                                                         |    2    |  D/V  |
| 1.5.2 | Verificare che i registri di provenienza dei dati siano immutabili, conservati in modo sicuro e accessibili per gli audit.                                                                                                                                                              |    2    |  D/V  |
| 1.5.3 | Verificare che il tracciamento della provenienza dei dati comprenda i dati sintetici generati tramite tecniche di tutela della privacy o tecniche generative e che tutti i dati sintetici siano chiaramente etichettati e distinguibili dai dati reali lungo l'intero flusso di lavoro. |    2    |  D/V  |

---

## Riferimenti

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [EU AI Act – Article 10: Data & Data Governance](https://artificialintelligenceact.eu/article/10/)
* [MITRE ATLAS: Adversary Tactics for AI](https://atlas.mitre.org/)
* [Survey of ML Bias Mitigation Techniques – MDPI](https://www.mdpi.com/2673-6470/4/1/1)
* [Data Provenance & Lineage Best Practices – Nightfall AI](https://www.nightfall.ai/ai-security-101/data-provenance-and-lineage)
* [Data Labeling Quality Standards – LabelYourData](https://labelyourdata.com/articles/data-labeling-quality-and-how-to-measure-it)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [CISA Advisory: Securing Data for AI Systems](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [ISO/IEC 23053: AI Management Systems Framework](https://www.iso.org/sectors/it-technologies/ai)
* [IBM: What is AI Governance?](https://www.ibm.com/think/topics/ai-governance)
* [Google AI Principles](https://ai.google/principles/)
* [GDPR & AI Training Data – DataProtectionReport](https://www.dataprotectionreport.com/2024/08/recent-regulatory-developments-in-training-artificial-intelligence-ai-models-under-the-gdpr/)
* [Supply-Chain Security for AI Data – AppSOC](https://www.appsoc.com/blog/ai-is-the-new-frontier-of-supply-chain-security)
* [OpenAI Privacy Center – Data Deletion Controls](https://privacy.openai.com/policies?modal=take-control)
* [Adversarial ML Dataset – Kaggle](https://www.kaggle.com/datasets/cnrieiit/adversarial-machine-learning-dataset)

