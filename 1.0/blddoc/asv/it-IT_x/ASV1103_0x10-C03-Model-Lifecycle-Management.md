# C3 Gestione del ciclo di vita dei modelli e controllo delle modifiche

## Obiettivo di controllo

I sistemi di IA devono implementare processi di controllo delle modifiche che impediscano modifiche del modello non autorizzate o non sicure dal raggiungere l'ambiente di produzione. Questo controllo garantisce l'integrità del modello per l'intero ciclo di vita--dallo sviluppo all'implementazione fino al dismissione--il che consente una risposta rapida agli incidenti e mantiene la responsabilità per tutte le modifiche.

Obiettivo di sicurezza principale: solo i modelli autorizzati e validati raggiungono la produzione impiegando processi controllati che mantengono l'integrità, la tracciabilità e la recuperabilità.

---

## C3.1 Autorizzazione e integrità del modello

Solo modelli autorizzati con integrità verificata raggiungono gli ambienti di produzione.

|   #   | Descrizione                                                                                                                                                                                                                           | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 3.1.1 | Verifichi che tutti gli artefatti del modello (pesi, configurazioni, tokenizzatori) siano firmati crittograficamente da enti autorizzati prima della messa in produzione.                                                             |    1    |  D/V  |
| 3.1.2 | Verifica che l'integrità del modello sia convalidata in fase di distribuzione e che i fallimenti della verifica della firma impediscano il caricamento del modello.                                                                   |    1    |  D/V  |
| 3.1.3 | Verifica che i registri di provenienza del modello includano l'identità dell'entità autorizzante, gli checksum dei dati di addestramento, i risultati dei test di validazione con esito pass/fail e una marca temporale di creazione. |    2    |  D/V  |
| 3.1.4 | Verifica che tutti gli artefatti del modello utilizzino il versionamento semantico (MAJOR.MINOR.PATCH) con criteri documentati che specificano quando ciascun componente della versione aumenta.                                      |    2    |  D/V  |
| 3.1.5 | Verifica che il tracciamento delle dipendenze mantenga un inventario in tempo reale che consenta l'identificazione rapida di tutti i sistemi che ne fanno uso.                                                                        |    2    |   V   |

---

## C3.2 Validazione del modello e test

I modelli devono superare le validazioni di sicurezza e di affidabilità definite prima della messa in produzione.

|   #   | Descrizione                                                                                                                                                                                                                                                                                      | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 3.2.1 | Verificare che i modelli vengano sottoposti a test di sicurezza automatizzati che includano la convalida degli input, la sanitizzazione degli output e valutazioni di sicurezza, con soglie di accettazione/rifiuto concordate in anticipo dall'organizzazione, prima della messa in produzione. |    1    |  D/V  |
| 3.2.2 | Verificare che i fallimenti della validazione blocchino automaticamente la messa in produzione del modello dopo l'approvazione esplicita al bypass da parte del personale autorizzato designato in anticipo, con giustificazioni aziendali documentate.                                          |    1    |  D/V  |
| 3.2.3 | Verifica che i risultati dei test siano firmati crittograficamente e legati in modo immutabile all'hash della versione del modello specifico che viene validata.                                                                                                                                 |    2    |   V   |
| 3.2.4 | Verificare che i dispiegamenti di emergenza richiedano una valutazione documentata dei rischi per la sicurezza e l'approvazione da parte di un'autorità di sicurezza pre-designata entro i tempi concordati.                                                                                     |    2    |  D/V  |

---

## C3.3 Distribuzione controllata e rollback

Le implementazioni dei modelli devono essere controllate, monitorate e reversibili.

|   #   | Descrizione                                                                                                                                                                                                                                                                    | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 3.3.1 | Verifica che le distribuzioni in produzione implementino meccanismi di rollout graduale (canary deployments, blue-green deployments) con trigger di rollback automatici basati su tassi di errore concordati in anticipo, soglie di latenza o criteri di allerta di sicurezza. |    1    |   D   |
| 3.3.2 | Verifica che le funzionalità di rollback ripristinino in modo atomico lo stato completo del modello (pesi, configurazioni, dipendenze) entro le finestre temporali predefinite dall'organizzazione.                                                                            |    1    |  D/V  |
| 3.3.3 | Verifica che i processi di distribuzione convalidino le firme crittografiche e calcolino i checksum di integrità prima dell'attivazione del modello, facendo fallire la distribuzione in caso di qualsiasi incongruenza.                                                       |    2    |  D/V  |
| 3.3.4 | Verifica che le capacità di spegnimento di emergenza del modello possano disabilitare gli endpoint del modello entro i tempi di risposta predefiniti tramite interruttori automatici o interruttori manuali di spegnimento.                                                    |    2    |  D/V  |
| 3.3.5 | Verificare che gli artefatti di rollback (versioni precedenti del modello, configurazioni, dipendenze) siano conservati in conformità alle politiche organizzative, con archiviazione immutabile per la gestione degli incidenti.                                              |    2    |   V   |

---

## C3.4 Responsabilità delle modifiche e verifica

Tutte le modifiche al ciclo di vita del modello devono essere tracciabili e auditabili.

|   #   | Descrizione                                                                                                                                                                                                                                                                       | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 3.4.1 | Verifica che tutte le modifiche al modello (dispiegamento, configurazione, ritiro) generino registri di audit immutabili che includano una marca temporale, l'identità dell'attore autenticata, il tipo di modifica e gli stati prima/dopo.                                       |    1    |   V   |
| 3.4.2 | Verifica che l'accesso al registro di audit richieda l'autorizzazione appropriata e che tutti i tentativi di accesso siano registrati con l'identità dell'utente e con una marca temporale.                                                                                       |    2    |  D/V  |
| 3.4.3 | Verificare che i modelli di prompt e i messaggi di sistema siano sottoposti a controllo di versione nei repository Git, con revisione del codice obbligatoria e approvazione da parte dei revisori designati prima della messa in produzione.                                     |    2    |  D/V  |
| 3.4.4 | Verificare che i registri di audit contengano dettagli sufficienti (hash del modello, istantanee di configurazione, versioni delle dipendenze) per consentire una ricostruzione completa dello stato del modello per qualsiasi marca temporale entro il periodo di conservazione. |    2    |   V   |

---

## C3.5 Pratiche di sviluppo sicuro

I processi di sviluppo e addestramento del modello devono seguire pratiche sicure per prevenire la compromissione.

|   #   | Descrizione                                                                                                                                                                                                                                                 | Livello | Ruolo |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 3.5.1 | Verificare che gli ambienti di sviluppo, test e produzione dei modelli siano separati fisicamente o logicamente. Non hanno infrastrutture condivise, controlli di accesso distinti e archivi di dati isolati.                                               |    1    |   D   |
| 3.5.2 | Verificare che l'addestramento del modello e la messa a punto avvengano in ambienti isolati con accesso di rete controllato.                                                                                                                                |    1    |   D   |
| 3.5.3 | Verificare che le fonti dei dati di addestramento siano verificate tramite controlli di integrità e provengano da fonti affidabili con una catena di custodia documentata prima dell'uso nello sviluppo del modello.                                        |    1    |  D/V  |
| 3.5.4 | Verifica che gli artefatti di sviluppo del modello (iperparametri, script di addestramento, file di configurazione) siano archiviati nel controllo delle versioni e richiedano l'approvazione tramite revisione tra pari prima dell'uso nell'addestramento. |    2    |   D   |

---

## C3.6 Ritiro del modello e messa fuori servizio

I modelli devono essere ritirati in modo sicuro quando non sono più necessari o quando si identificano problemi di sicurezza.

|   #   | Descrizione                                                                                                                                                                                                                                                              | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 3.6.1 | Verificare che i processi di messa fuori servizio del modello eseguano automaticamente la scansione dei grafi di dipendenza, identifichino tutti i sistemi che ne fanno uso e forniscano i periodi di preavviso concordati in anticipo prima della messa fuori servizio. |    1    |   D   |
| 3.6.2 | Verificare che gli artefatti dei modelli ritirati siano cancellati in modo sicuro mediante cancellazione crittografica o sovrascrittura a più passaggi, in conformità alle politiche di conservazione dei dati documentate, con certificati di distruzione verificati.   |    1    |  D/V  |
| 3.6.3 | Verificare che gli eventi di ritiro del modello siano registrati con marca temporale e identità dell'attore, e che le firme del modello siano revocate per impedirne il riutilizzo.                                                                                      |    2    |   V   |
| 3.6.4 | Verificare che la messa fuori servizio d'emergenza del modello possa disabilitare l'accesso al modello entro i tempi di risposta di emergenza prestabiliti tramite interruttori di spegnimento automatici se vengono rilevate vulnerabilità di sicurezza critiche.       |    2    |  D/V  |

---

## Riferimenti

* [MLOps Principles](https://ml-ops.org/content/mlops-principles)
* [Securing AI/ML Ops – Cisco.com](https://sec.cloudapps.cisco.com/security/center/resources/SecuringAIMLOps)
* [Audit logs security: cryptographically signed tamper-proof logs](https://www.cossacklabs.com/blog/audit-logs-security/)
* [Machine Learning Model Versioning: Top Tools & Best Practices](https://lakefs.io/blog/model-versioning/)
* [AI Hygiene Starts with Models and Data Loaders – SEI Blog](https://insights.sei.cmu.edu/documents/6190/AI-Hygiene-Starts-with-Models-and-Data-Loaders_1G0KTRh.pdf)
* [How to handle versioning and rollback of a deployed ML model?](https://learn.microsoft.com/en-au/answers/questions/1845378/how-to-handle-versioning-and-rollback-of-a-deploye)
* [Reinforcement fine-tuning – OpenAI API](https://platform.openai.com/docs/guides/reinforcement-fine-tuning)
* [Auditing Machine Learning models: Governance, Data Security and …](https://www.linkedin.com/pulse/auditing-machine-learning-models-governance-data-security-negrete-yn81f)
* [Adversarial Training to Improve Model Robustness](https://medium.com/%40amit25173/adversarial-training-to-improve-model-robustness-5e285b516713)
* [What is AI adversarial robustness? – IBM Research](https://research.ibm.com/blog/securing-ai-workflows-with-adversarial-robustness)
* [Exploring Data Provenance: Ensuring Data Integrity and Authenticity](https://www.astera.com/type/blog/data-provenance/)
* [MITRE ATLAS](https://atlas.mitre.org/)
* [AWS Prescriptive Guidance – Best practices for retiring applications …](https://docs.aws.amazon.com/pdfs/prescriptive-guidance/latest/migration-app-retirement-best-practices/migration-app-retirement-best-practices.pdf)

