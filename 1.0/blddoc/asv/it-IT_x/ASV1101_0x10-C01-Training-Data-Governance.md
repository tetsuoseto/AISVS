# C1 Governance dei Dati di Addestramento e Gestione dei Bias

## Obiettivo di Controllo

I dati di addestramento devono essere reperiti, gestiti e mantenuti in modo da preservarne la provenienza, la sicurezza, la qualità e l’equità. Farlo soddisfa i doveri legali e riduce i rischi di bias, avvelenamento o violazioni della privacy che si manifestano durante l’addestramento e che potrebbero influenzare l’intero ciclo di vita dell’IA.

---

## C1.1 Provenienza dei dati di addestramento

Mantieni un inventario verificabile di tutti i set di dati, accetta solo fonti affidabili e registra ogni modifica per garantire la tracciabilità.

|   #   | Descrizione                                                                                                                                                                                                        | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 1.1.1 | Verificare che venga mantenuto un inventario aggiornato di ogni fonte di dati di addestramento (origine, responsabile/proprietario, licenza, metodo di raccolta, vincoli d'uso previsti e storia di elaborazione). |    1    |  D/V  |
| 1.1.2 | Verificare che i processi di training dei dati escludano caratteristiche, attributi o campi non necessari (ad esempio, metadati non utilizzati, dati PII sensibili, dati di test trapelati).                       |    1    |  D/V  |
| 1.1.3 | Verificare che tutte le modifiche al dataset siano soggette a un flusso di lavoro di approvazione registrato.                                                                                                      |    2    |  D/V  |
| 1.1.4 | Verificare che i dataset o i sottoinsiemi siano marcati con filigrana o tramite impronta digitale dove possibile.                                                                                                  |    3    |  D/V  |

---

## C1.2 Sicurezza e Integrità dei Dati di Addestramento

Limitare l'accesso ai dati di addestramento, crittografarli sia a riposo che in transito e convalidarne l'integrità per prevenire manomissioni, furti o avvelenamento dei dati.

|   #   | Descrizione                                                                                                                                                                                     | Livello | Ruolo |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 1.2.1 | Verificare che i controlli di accesso proteggano l’archiviazione dei dati di addestramento e le pipeline.                                                                                       |    1    |  D/V  |
| 1.2.2 | Verificare che tutti gli accessi ai dati di addestramento siano registrati, inclusi utente, ora e azione.                                                                                       |    2    |  D/V  |
| 1.2.3 | Verificare che i dataset di addestramento siano crittografati durante la trasmissione e a riposo, utilizzando algoritmi crittografici standard del settore e pratiche di gestione delle chiavi. |    2    |  D/V  |
| 1.2.4 | Verificare che vengano utilizzati hash crittografici o firme digitali per garantire l'integrità dei dati durante l'archiviazione e il trasferimento dei dati di addestramento.                  |    2    |  D/V  |
| 1.2.5 | Verificare che vengano applicate tecniche di rilevamento automatizzato per prevenire modifiche non autorizzate o la corruzione dei dati di addestramento.                                       |    2    |  D/V  |
| 1.2.6 | Verificare che i dati di addestramento obsoleti siano eliminati in modo sicuro o anonimizzati.                                                                                                  |    2    |  D/V  |
| 1.2.7 | Verificare che tutte le versioni del dataset di addestramento siano identificate univocamente, archiviate in modo immutabile e verificabili per supportare il rollback e l'analisi forense.     |    3    |  D/V  |

---

## C1.3 Qualità, Integrità e Sicurezza dell'Etichettatura dei Dati di Addestramento

Proteggi le etichette e richiedi una revisione tecnica per i dati critici.

|   #   | Descrizione                                                                                                                                                                                                                                        | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 1.3.1 | Verificare che gli hash crittografici o le firme digitali siano applicati agli artefatti delle etichette per garantirne l'integrità e l'autenticità.                                                                                               |    2    |  D/V  |
| 1.3.2 | Verificare che le interfacce e le piattaforme di etichettatura applichino controlli di accesso rigorosi, mantengano registri di audit a prova di manomissione di tutte le attività di etichettatura e proteggano contro modifiche non autorizzate. |    2    |  D/V  |
| 1.3.3 | Verificare che le informazioni sensibili nelle etichette siano oscurate, anonimizzate o criptate a livello di campo dati sia a riposo che in transito.                                                                                             |    3    |  D/V  |

---

## C1.4 Qualità dei Dati di Addestramento e Garanzia di Sicurezza

Combina la validazione automatica, i controlli manuali a campione e la correzione registrata per garantire l'affidabilità del dataset.

|   #   | Descrizione                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 1.4.1 | Verificare che i test automatici rilevino errori di formato e valori nulli ad ogni ingresso o trasformazione significativa dei dati.                                                                                                                                                                                                                                                                                                                                             |    1    |   D   |
| 1.4.2 | Verificare che le pipeline di addestramento e fine-tuning dei LLM implementino il rilevamento di avvelenamento e la validazione dell'integrità dei dati (ad esempio, metodi statistici, rilevamento di outlier, analisi degli embedding) per identificare potenziali attacchi di avvelenamento (ad esempio, cambio di etichetta, inserimento di trigger backdoor, comandi di cambio ruolo, attacchi di istanze influenti) o la corruzione accidentale dei dati di addestramento. |    2    |  D/V  |
| 1.4.3 | Verificare che le etichette generate automaticamente (ad esempio, tramite LLM o supervisione debole) siano soggette a soglie di confidabilità e controlli di coerenza per rilevare etichette allucinatorie, fuorvianti o a bassa affidabilità.                                                                                                                                                                                                                                   |    2    |  D/V  |
| 1.4.4 | Verificare che siano implementate e ottimizzate difese adeguate, come l’addestramento avversario (utilizzando esempi avversari generati), l’augmentazione dei dati con input perturbati o tecniche di ottimizzazione robusta, per i modelli rilevanti basati sulla valutazione del rischio.                                                                                                                                                                                      |    3    |  D/V  |
| 1.4.5 | Verificare che i test automatizzati rilevino gli sfasamenti delle etichette ad ogni ingresso o significativa trasformazione dei dati.                                                                                                                                                                                                                                                                                                                                            |    3    |   D   |

---

## C1.5 Tracciabilità e Lineage dei Dati

Traccia l'intero percorso di ogni punto dati dalla fonte all'input del modello per garantire auditabilità e risposta agli incidenti.

|   #   | Descrizione                                                                                                                                                                                                                                                              | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 1.5.1 | Verificare che la provenienza di ogni punto dati, comprese tutte le trasformazioni, aumenti e fusioni, sia registrata e possa essere ricostruita.                                                                                                                        |    2    |  D/V  |
| 1.5.2 | Verificare che i record di tracciabilità siano immutabili, archiviati in modo sicuro e accessibili per le revisioni.                                                                                                                                                     |    2    |  D/V  |
| 1.5.3 | Verificare che il tracciamento della provenienza copra i dati sintetici generati tramite tecniche di preservazione della privacy o generative e che tutti i dati sintetici siano chiaramente etichettati e distinguibili dai dati reali lungo tutto il flusso di lavoro. |    2    |  D/V  |

---

## Riferimenti

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [EU AI Act – Article 10: Data & Data Governance](https://artificialintelligenceact.eu/article/10/)
* [CISA Advisory: Securing Data for AI Systems](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [OpenAI Privacy Center – Data Deletion Controls](https://privacy.openai.com/policies?modal=take-control)

