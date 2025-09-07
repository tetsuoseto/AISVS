# Governance dei dati di training C1 e gestione dei bias

## Obiettivo di Controllo

I dati di addestramento devono essere ottenuti, gestiti e mantenuti in modo da preservare la provenienza, la sicurezza, la qualità e l'equità. Farlo soddisfa gli obblighi legali e riduce i rischi di bias, avvelenamento o violazioni della privacy che si manifestano durante l'addestramento e che potrebbero influenzare l'intero ciclo di vita dell'IA.

---

## C1.1 Provenienza dei dati di addestramento

Mantenere un inventario verificabile di tutti i dataset, accettare solo fonti affidabili e registrare ogni modifica per garantire l'auditabilità.

|   #   | Descrizione                                                                                                                                                                                                          | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 1.1.1 | Verificare che sia mantenuto un inventario aggiornato di ogni fonte di dati di addestramento (origine, responsabile/proprietario, licenza, metodo di raccolta, vincoli d’uso previsti e cronologia di elaborazione). |    1    |  D/V  |
| 1.1.2 | Verificare che i processi di formazione dei dati escludano funzionalità, attributi o campi non necessari (ad esempio, metadati inutilizzati, PII sensibili, dati di test trapelati).                                 |    1    |  D/V  |
| 1.1.3 | Verificare che tutte le modifiche al dataset siano soggette a un flusso di approvazione registrato.                                                                                                                  |    2    |  D/V  |
| 1.1.4 | Verificare che i dataset o i sottoinsiemi siano watermarkati o fingerprintati ove possibile.                                                                                                                         |    3    |  D/V  |

---

## C1.2 Sicurezza e Integrità dei Dati di Addestramento

Limitare l'accesso ai dati di addestramento, crittografarli sia a riposo che in transito, e convalidarne l'integrità per prevenire manomissioni, furti o avvelenamento dei dati.

|   #   | Descrizione                                                                                                                                                                                         | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 1.2.1 | Verificare che i controlli di accesso proteggano l'archiviazione dei dati di addestramento e le pipeline.                                                                                           |    1    |  D/V  |
| 1.2.2 | Verificare che tutti gli accessi ai dati di addestramento siano registrati, includendo utente, ora e azione.                                                                                        |    2    |  D/V  |
| 1.2.3 | Verificare che i dataset di addestramento siano crittografati durante il trasferimento e in archivio, utilizzando algoritmi crittografici standard del settore e pratiche di gestione delle chiavi. |    2    |  D/V  |
| 1.2.4 | Verificare che vengano utilizzati hash crittografici o firme digitali per garantire l'integrità dei dati durante l'archiviazione e il trasferimento dei dati di addestramento.                      |    2    |  D/V  |
| 1.2.5 | Verificare che vengano applicate tecniche di rilevamento automatico per proteggere contro modifiche non autorizzate o la corruzione dei dati di addestramento.                                      |    2    |  D/V  |
| 1.2.6 | Verificare che i dati di addestramento obsoleti siano eliminati in modo sicuro o anonimizzati.                                                                                                      |    2    |  D/V  |
| 1.2.7 | Verificare che tutte le versioni del dataset di addestramento siano identificate in modo univoco, archiviate in modo immutabile e verificabili per supportare il rollback e l'analisi forense.      |    3    |  D/V  |

---

## C1.3 Qualità, Integrità e Sicurezza dell'Etichettatura dei Dati di Addestramento

Proteggi le etichette e richiedi una revisione tecnica per i dati critici.

|   #   | Descrizione                                                                                                                                                                                                                                        | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 1.3.1 | Verificare che gli hash crittografici o le firme digitali siano applicati agli artefatti di etichettatura per garantirne l'integrità e l'autenticità.                                                                                              |    2    |  D/V  |
| 1.3.2 | Verificare che le interfacce e le piattaforme di etichettatura applichino controlli di accesso rigorosi, mantengano registri di audit a prova di manomissione di tutte le attività di etichettatura e proteggano contro modifiche non autorizzate. |    2    |  D/V  |
| 1.3.3 | Verificare che le informazioni sensibili nelle etichette siano occultate, anonimizzate o crittografate a livello di campo dati sia a riposo che in transito.                                                                                       |    3    |  D/V  |

---

## C1.4 Qualità dei Dati di Addestramento e Garanzia di Sicurezza

Combina la convalida automatica, i controlli manuali a campione e la correzione registrata per garantire l'affidabilità del dataset.

|   #   | Descrizione                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 1.4.1 | Verifica che i test automatizzati rilevino errori di formato e valori nulli ad ogni ingestione o significativa trasformazione dei dati.                                                                                                                                                                                                                                                                                                                                           |    1    |   D   |
| 1.4.2 | Verificare che le pipeline di addestramento e fine-tuning di LLM implementino la rilevazione del poisoning e la validazione dell'integrità dei dati (ad esempio, metodi statistici, rilevamento di outlier, analisi degli embedding) per identificare potenziali attacchi di poisoning (ad esempio, inversione delle etichette, inserimento di trigger backdoor, comandi di cambio ruolo, attacchi tramite istanze influenti) o corruzione accidentale dei dati di addestramento. |    2    |  D/V  |
| 1.4.3 | Verificare che siano implementate e tarate difese appropriate, come l'addestramento avversariale (utilizzando esempi avversariali generati), l'aumento dei dati con input perturbati o tecniche di ottimizzazione robusta, per i modelli rilevanti in base alla valutazione del rischio.                                                                                                                                                                                          |    3    |  D/V  |
| 1.4.4 | Verificare che le etichette generate automaticamente (ad esempio, tramite LLM o supervisione debole) siano soggette a soglie di confidenza e controlli di coerenza per rilevare etichette allucinatorie, fuorvianti o di bassa confidenza.                                                                                                                                                                                                                                        |    2    |  D/V  |
| 1.4.5 | Verificare che i test automatizzati rilevino gli scostamenti delle etichette a ogni acquisizione o trasformazione significativa dei dati.                                                                                                                                                                                                                                                                                                                                         |    3    |   D   |

---

## C1.5 Traccia e Provenienza dei Dati

Traccia l’intero percorso di ogni punto dati dalla fonte all’input del modello per garantire la tracciabilità e la risposta agli incidenti.

|   #   | Descrizione                                                                                                                                                                                                                                                   | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 1.5.1 | Verificare che la provenienza di ogni punto dati, comprese tutte le trasformazioni, le aumentazioni e le fusioni, sia registrata e possa essere ricostruita.                                                                                                  |    2    |  D/V  |
| 1.5.2 | Verificare che i record di provenienza siano immutabili, archiviati in modo sicuro e accessibili per le verifiche.                                                                                                                                            |    2    |  D/V  |
| 1.5.3 | Verificare che il tracciamento della provenienza copra i dati sintetici generati tramite tecniche di protezione della privacy o generative e che tutti i dati sintetici siano chiaramente etichettati e distinguibili dai dati reali lungo tutto il processo. |    2    |  D/V  |

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

