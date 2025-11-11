# Appendice C: Governance della Sicurezza AI e Documentazione (Riorganizzata)

## Obiettivo

Questo appendice fornisce i requisiti fondamentali per stabilire strutture organizzative, politiche, documentazione e processi per governare la sicurezza dell'IA durante tutto il ciclo di vita del sistema.

---

## AC.1 Adozione del Framework di Gestione del Rischio AI

|   #    | Descrizione                                                                                                                               | Livello | Ruolo |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.1.1 | Verificare che una metodologia di valutazione del rischio specifica per l’AI sia documentata e implementata.                              |    1    |  D/V  |
| AC.1.2 | Verificare che le valutazioni del rischio siano condotte nei punti chiave del ciclo di vita dell'IA e prima di cambiamenti significativi. |    2    |   D   |
| AC.1.3 | Verificare che il quadro di gestione del rischio sia allineato agli standard stabiliti (ad esempio, NIST AI RMF).                         |    3    |  D/V  |

---

## AC.2 Politiche e Procedure di Sicurezza per l'IA

|   #    | Descrizione                                                                                                                                | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| AC.2.1 | Verificare che esistano politiche di sicurezza AI documentate.                                                                             |    1    |  D/V  |
| AC.2.2 | Verificare che le politiche siano revisionate e aggiornate almeno annualmente e dopo cambiamenti significativi nel panorama delle minacce. |    2    |   D   |
| AC.2.3 | Verificare che le politiche coprano tutte le categorie AISVS e i requisiti normativi applicabili.                                          |    3    |  D/V  |

---

## AC.3 Ruoli e Responsabilità per la Sicurezza dell'IA

|   #    | Descrizione                                                                                                                       | Livello | Ruolo |
| :----: | --------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.3.1 | Verificare che i ruoli e le responsabilità della sicurezza AI siano documentati.                                                  |    1    |  D/V  |
| AC.3.2 | Verificare che le persone responsabili possiedano un'adeguata competenza in materia di sicurezza.                                 |    2    |   D   |
| AC.3.3 | Verificare che sia stato istituito un comitato di etica dell'IA o un consiglio di governance per i sistemi di IA ad alto rischio. |    3    |  D/V  |

---

## AC.4 Applicazione delle linee guida etiche per l'IA

|   #    | Descrizione                                                                               | Livello | Ruolo |
| :----: | ----------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.4.1 | Verificare che esistano linee guida etiche per lo sviluppo e l'implementazione dell'IA.   |    1    |  D/V  |
| AC.4.2 | Verificare che siano in atto meccanismi per rilevare e segnalare violazioni etiche.       |    2    |   D   |
| AC.4.3 | Verificare che vengano effettuate revisioni etiche regolari dei sistemi di IA dispiegati. |    3    |  D/V  |

---

## AC.5 Monitoraggio della conformità normativa dell'IA

|   #    | Descrizione                                                                                                                   | Livello | Ruolo |
| :----: | ----------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.5.1 | Verificare che esistano processi per identificare le normative sull’AI applicabili.                                           |    1    |  D/V  |
| AC.5.2 | Verificare che la conformità a tutti i requisiti normativi sia valutata.                                                      |    2    |   D   |
| AC.5.3 | Verificare che le modifiche normative provochino revisioni e aggiornamenti tempestivi ai sistemi di intelligenza artificiale. |    3    |  D/V  |

---

## AC.6 Governance, documentazione e processo dei dati di addestramento

### AC.6.1 Acquisizione dei dati e due diligence

|    #     | Descrizione                                                                                                                                                                                                                                                                                                                                           | Livello | Ruolo |
| :------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.6.1.1 | Verificare che vengano consentiti solo i dataset valutati per qualità, rappresentatività, approvvigionamento etico e conformità alle licenze, riducendo i rischi di avvelenamento, bias incorporati e violazione della proprietà intellettuale.                                                                                                       |    1    |  D/V  |
| AC.6.1.2 | Verificare che i fornitori di dati di terze parti, inclusi i fornitori di modelli pre-addestrati e set di dati esterni, siano sottoposti a controlli di due diligence riguardanti sicurezza, privacy, approvvigionamento etico e qualità dei dati prima che i loro dati o modelli vengano integrati.                                                  |    2    |  D/V  |
| AC.6.1.3 | Verificare che i trasferimenti esterni utilizzino TLS/autenticazione e controlli di integrità.                                                                                                                                                                                                                                                        |    1    |   D   |
| AC.6.1.4 | Verificare che le fonti di dati ad alto rischio (ad esempio, set di dati open-source con provenienza sconosciuta, fornitori non verificati) ricevano una valutazione approfondita, come l’analisi in sandbox, controlli estesi sulla qualità e sui bias, e il rilevamento mirato di avvelenamento, prima del loro utilizzo in applicazioni sensibili. |    2    |  D/V  |
| AC.6.1.5 | Verificare che i modelli pre-addestrati ottenuti da terze parti siano valutati per bias incorporati, potenziali backdoor, integrità della loro architettura e provenienza dei dati di addestramento originali prima della messa a punto o del dispiegamento.                                                                                          |    3    |  D/V  |

### AC.6.2 Gestione di Bias e Equità

|    #     | Descrizione                                                                                                                                                                                                                                                                                                                                                             | Livello | Ruolo |
| :------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.6.2.1 | Verificare che i dataset siano profilati per squilibri rappresentativi e potenziali bias riguardanti attributi legalmente protetti (ad esempio, razza, genere, età) e altre caratteristiche eticamente sensibili rilevanti per il dominio di applicazione del modello (ad esempio, status socio-economico, ubicazione).                                                 |    1    |  D/V  |
| AC.6.2.2 | Verificare che i bias identificati siano mitigati tramite strategie documentate come il riequilibrio, l'aumento mirato dei dati, gli aggiustamenti algoritmici (ad esempio, tecniche di pre-processing, in-processing, post-processing) o la ripesatura, e che l'impatto della mitigazione sia valutato sia sulla equità che sulle prestazioni complessive del modello. |    2    |  D/V  |
| AC.6.2.3 | Verificare che le metriche di equità post-addestramento siano valutate e documentate.                                                                                                                                                                                                                                                                                   |    2    |  D/V  |
| AC.6.2.4 | Verificare che una politica di gestione del bias nel ciclo di vita assegni i responsabili e la cadenza delle revisioni.                                                                                                                                                                                                                                                 |    3    |  D/V  |

### AC.6.3 Governance dell'Etichettatura e dell'Annotazione

|     #     | Descrizione                                                                                                                                                                                                                                                                           | Livello | Ruolo |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.6.3.1  | Verificare che la qualità della etichettatura/annotazione sia garantita tramite controlli incrociati da parte dei revisori o consenso.                                                                                                                                                |    2    |  D/V  |
| AC.6.3.2  | Verificare che le schede dei dati vengano mantenute per i set di dati di addestramento significativi, dettagliando caratteristiche, motivazioni, composizione, processi di raccolta, preprocessing, licenze e usi raccomandati/sconsigliati.                                          |    2    |  D/V  |
| AC.6.3.3  | Verificare che le schede dei dati documentino i rischi di bias, le distorsioni demografiche e le considerazioni etiche rilevanti per il dataset.                                                                                                                                      |    2    |  D/V  |
| AC.6.3.4  | Verificare che le schede dei dati siano versionate insieme ai dataset e aggiornate ogni volta che il dataset viene modificato.                                                                                                                                                        |    2    |  D/V  |
| AC.6.3.5  | Verificare che le schede dati siano riviste e approvate sia dagli stakeholder tecnici che non tecnici (ad esempio, conformità, etica, esperti del settore).                                                                                                                           |    2    |  D/V  |
| AC.6.3.6  | Verificare che la qualità delle etichettature/annotazioni sia garantita tramite linee guida chiare, revisioni incrociate da parte dei valutatori, meccanismi di consenso (ad es., monitoraggio dell'accordo tra annotatori) e processi definiti per la risoluzione delle discrepanze. |    2    |  D/V  |
| AC.6.3.7  | Verificare che le etichette critiche per la sicurezza, la protezione o l'equità (ad esempio, l'identificazione di contenuti tossici, risultati medici critici) ricevano una revisione duale indipendente obbligatoria o una verifica robusta equivalente.                             |    3    |  D/V  |
| AC.6.3.8  | Verificare che le linee guida e le istruzioni per l'etichettatura siano complete, controllate nelle versioni e revisionate dai pari.                                                                                                                                                  |    2    |  D/V  |
| AC.6.3.9  | Verificare che gli schemi dei dati per le etichette siano chiaramente definiti e controllati nella versione.                                                                                                                                                                          |    2    |  D/V  |
| AC.6.3.10 | Verificare che i flussi di lavoro di etichettatura esternalizzati o basati sul crowd includano salvaguardie tecniche/procedurali per garantire la riservatezza dei dati, l'integrità, la qualità delle etichette e prevenire la perdita di dati.                                      |    2    |  D/V  |
| AC.6.3.11 | Verificare che tutto il personale coinvolto nell'annotazione dei dati sia stato sottoposto a controlli di background e formato sulla sicurezza e la privacy dei dati.                                                                                                                 |    2    |  D/V  |
| AC.6.3.12 | Verificare che tutto il personale di annotazione firmi accordi di riservatezza e non divulgazione.                                                                                                                                                                                    |    2    |  D/V  |
| AC.6.3.13 | Verificare che le piattaforme di annotazione applichino controlli di accesso e monitorino le minacce interne.                                                                                                                                                                         |    2    |  D/V  |

### AC.6.4 Gate di Qualità del Dataset e Messa in Quarantena

|    #     | Descrizione                                                                                                                                                                                                                                                                                                                       | Livello | Ruolo |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.6.4.1 | Verificare che i dataset non riusciti siano messi in quarantena con tracce di audit.                                                                                                                                                                                                                                              |    2    |  D/V  |
| AC.6.4.2 | Verificare che le soglie di qualità blocchino i dataset di qualità inferiore a meno che non siano approvate eccezioni.                                                                                                                                                                                                            |    2    |  D/V  |
| AC.6.4.3 | Verificare che i controlli manuali a campione eseguiti da esperti del dominio coprano un campione statisticamente significativo (ad esempio, ≥1% o 1.000 campioni, a seconda di quale sia maggiore, o come determinato dalla valutazione del rischio) per identificare problemi di qualità sottili non rilevati dall’automazione. |    2    |   V   |

### AC.6.5 Rilevamento di minacce/avvelenamento e deriva

|    #     | Descrizione                                                                                                                  | Livello | Ruolo |
| :------: | ---------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.6.5.1 | Verificare che i campioni segnalati attivino una revisione manuale prima dell'addestramento.                                 |    2    |  D/V  |
| AC.6.5.2 | Verificare che i risultati alimentino il dossier di sicurezza del modello e informino l'intelligence sulle minacce in corso. |    2    |   V   |
| AC.6.5.3 | Verificare che la logica di rilevamento sia aggiornata con nuove informazioni sulle minacce.                                 |    3    |  D/V  |
| AC.6.5.4 | Verificare che le pipeline di apprendimento online monitorino il drift di distribuzione.                                     |    3    |  D/V  |

### AC.6.6 Cancellazione, Consenso, Diritti, Conservazione e Conformità

|     #     | Descrizione                                                                                                                                                                                                                                                                                                                                | Livello | Ruolo |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| AC.6.6.1  | Verificare che i flussi di lavoro per la cancellazione dei dati di addestramento eliminino sia i dati primari che quelli derivati e valutare l’impatto sul modello, assicurandosi che l'effetto sui modelli interessati venga valutato e, se necessario, affrontato (ad esempio mediante riaddestramento o riallineamento).                |    1    |  D/V  |
| AC.6.6.2  | Verificare che siano in atto meccanismi per monitorare e rispettare l'ambito e lo stato del consenso dell'utente (e dei suoi eventuali ritiri) per i dati utilizzati nell'addestramento, e che il consenso venga validato prima che i dati siano incorporati in nuovi processi di addestramento o aggiornamenti significativi del modello. |    2    |   D   |
| AC.6.6.3  | Verificare che i workflow siano testati annualmente e registrati.                                                                                                                                                                                                                                                                          |    2    |   V   |
| AC.6.6.4  | Verificare che siano definiti periodi di conservazione espliciti per tutti i dataset di addestramento.                                                                                                                                                                                                                                     |    1    |  D/V  |
| AC.6.6.5  | Verificare che i set di dati vengano automaticamente scaduti, eliminati o esaminati per l'eliminazione alla fine del loro ciclo di vita.                                                                                                                                                                                                   |    2    |  D/V  |
| AC.6.6.6  | Verificare che le azioni di conservazione e cancellazione siano registrate e verificabili.                                                                                                                                                                                                                                                 |    2    |  D/V  |
| AC.6.6.7  | Verificare che i requisiti di residenza dei dati e di trasferimento transfrontaliero siano identificati e applicati per tutti i set di dati.                                                                                                                                                                                               |    2    |  D/V  |
| AC.6.6.8  | Verificare che le normative specifiche del settore (ad esempio, sanità, finanza) siano identificate e affrontate nella gestione dei dati.                                                                                                                                                                                                  |    2    |  D/V  |
| AC.6.6.9  | Verificare che la conformità alle leggi sulla privacy rilevanti (ad esempio, GDPR, CCPA) sia documentata e revisionata regolarmente.                                                                                                                                                                                                       |    2    |  D/V  |
| AC.6.6.10 | Verificare che esistano meccanismi per rispondere alle richieste dei soggetti dei dati riguardo all'accesso, alla rettifica, alla limitazione o all'opposizione.                                                                                                                                                                           |    2    |  D/V  |
| AC.6.6.11 | Verificare che le richieste siano registrate, tracciate e soddisfatte entro i tempi stabiliti dalla legge.                                                                                                                                                                                                                                 |    2    |  D/V  |
| AC.6.6.12 | Verificare che i processi relativi ai diritti dei soggetti dei dati siano testati e revisionati regolarmente per garantirne l'efficacia.                                                                                                                                                                                                   |    2    |  D/V  |

### AC.6.7 Versioning e Gestione delle Modifiche

|    #     | Descrizione                                                                                                                                                            | Livello | Ruolo |
| :------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.6.7.1 | Verificare che venga eseguita un'analisi d'impatto prima di aggiornare o sostituire una versione del dataset, includendo prestazioni del modello, equità e conformità. |    2    |  D/V  |
| AC.6.7.2 | Verificare che i risultati dell'analisi d'impatto siano documentati e revisionati dalle parti interessate rilevanti.                                                   |    2    |  D/V  |
| AC.6.7.3 | Verificare che esistano piani di rollback nel caso in cui le nuove versioni introducano rischi inaccettabili o regressioni.                                            |    2    |  D/V  |

### AC.6.8 Governance dei Dati Sintetici

|    #     | Descrizione                                                                                                                                                         | Livello | Ruolo |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.6.8.1 | Verifica che il processo di generazione, i parametri e l'uso previsto dei dati sintetici siano documentati.                                                         |    2    |  D/V  |
| AC.6.8.2 | Verificare che i dati sintetici siano valutati in termini di rischio per bias, perdita di privacy e problemi di rappresentazione prima dell’uso nell’addestramento. |    2    |  D/V  |

### AC.6.9 Monitoraggio degli accessi

|    #     | Descrizione                                                                                                                                                          | Livello | Ruolo |
| :------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.6.9.1 | Verificare che i log di accesso vengano regolarmente esaminati per individuare modelli insoliti, come esportazioni di grandi dimensioni o accessi da nuove località. |    2    |  D/V  |
| AC.6.9.2 | Verificare che vengano generate allerte per eventi di accesso sospetti e che vengano indagate tempestivamente.                                                       |    2    |  D/V  |

### AC.6.10 Governance dell'addestramento avversariale

|     #     | Descrizione                                                                                                                                                                                                     | Livello | Ruolo |
| :-------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.6.10.1 | Verificare che, se viene utilizzato l'addestramento avversario, la generazione, la gestione e la versione dei dataset avversari siano documentate e controllate.                                                |    2    |  D/V  |
| AC.6.10.2 | Verificare che l'impatto dell'addestramento alla robustezza adversaria sulle prestazioni del modello (sia contro input puliti che adversari) e sulle metriche di equità sia valutato, documentato e monitorato. |    3    |  D/V  |
| AC.6.10.3 | Verificare che le strategie per l'addestramento avversariale e la robustezza siano periodicamente riviste e aggiornate per contrastare le tecniche di attacco avversario in evoluzione.                         |    3    |  D/V  |

---

## AC.7 Governance e Documentazione del Ciclo di Vita del Modello

|   #    | Descrizione                                                                                                                                                                                                           | Livello | Ruolo |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.7.1 | Verificare che tutti gli artefatti del modello utilizzino il versionamento semantico (MAJOR.MINOR.PATCH) con criteri documentati che specifichino quando incrementare ciascuna componente della versione.             |    2    |  D/V  |
| AC.7.2 | Verificare che le distribuzioni di emergenza richiedano una valutazione documentata del rischio di sicurezza e l'approvazione da parte di un'autorità di sicurezza predesignata entro i tempi concordati in anticipo. |    2    |  D/V  |
| AC.7.3 | Verificare che gli artefatti di rollback (versioni precedenti del modello, configurazioni, dipendenze) siano conservati secondo le politiche organizzative.                                                           |    2    |   V   |
| AC.7.4 | Verificare che l'accesso al registro di controllo richieda un'autorizzazione appropriata e che tutti i tentativi di accesso siano registrati con l'identità dell'utente e un timestamp.                               |    2    |  D/V  |
| AC.7.5 | Verificare che gli artefatti del modello ritirato siano conservati in conformità alle politiche di conservazione dei dati.                                                                                            |    1    |  D/V  |

---

## Governance della sicurezza di prompt, input e output di AC.8

### Difesa contro l'iniezione di prompt AC.8.1

|    #     | Descrizione                                                                                                                                                                                                                                       | Livello | Ruolo |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.8.1.1 | Verificare che i test di valutazione avversaria (ad esempio, i prompt "many-shot" del Red Team) vengano eseguiti prima di ogni rilascio di modello o template di prompt, con soglie di tasso di successo e blocchi automatizzati per regressioni. |    2    |  D/V  |
| AC.8.1.2 | Verificare che tutti gli aggiornamenti delle regole del filtro dei prompt, le versioni del modello classificatore e le modifiche alla lista di blocco siano controllati nella versione e verificabili.                                            |    3    |  D/V  |

### AC.8.2 Resistenza agli Esempi Avversari

|    #     | Descrizione                                                                                                                                                                             | Livello | Ruolo |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.8.2.1 | Verificare che le metriche di robustezza (tasso di successo delle suite di attacchi conosciuti) siano monitorate nel tempo tramite automazione e che le regressioni attivino un avviso. |    3    |  D/V  |

### AC.8.3 Screening dei Contenuti e delle Politiche

|    #     | Descrizione                                                                                                                                                                                         | Livello | Ruolo |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.8.3.1 | Verificare che il modello di screening o il set di regole venga riaddestrato/aggiornato almeno ogni trimestre, incorporando i nuovi schemi di jailbreak o di superamento delle politiche osservati. |    2    |   D   |

### AC.8.4 Limitazione della velocità di input e prevenzione degli abusi

|    #     | Descrizione                                                                                                                  | Livello | Ruolo |
| :------: | ---------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.8.4.1 | Verificare che i log di prevenzione degli abusi siano conservati e riesaminati per individuare modelli di attacco emergenti. |    3    |   V   |

### AC.8.5 Provenienza e attribuzione dell'input

|    #     | Descrizione                                                                                                                                                       | Livello | Ruolo |
| :------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.8.5.1 | Verificare che tutti gli input degli utenti siano contrassegnati con metadati (ID utente, sessione, fonte, timestamp, indirizzo IP) al momento dell’acquisizione. |    1    |  D/V  |
| AC.8.5.2 | Verificare che i metadati di provenienza siano mantenuti e verificabili per tutti gli input elaborati.                                                            |    2    |  D/V  |
| AC.8.5.3 | Verificare che le fonti di input anomale o non attendibili vengano segnalate e sottoposte a un controllo più rigoroso o al blocco.                                |    2    |  D/V  |

---

## AC.9 Validazione multimodale, MLOps e governance dell'infrastruttura

### AC.9.1 Pipeline di convalida della sicurezza multimodale

|    #     | Descrizione                                                                                                                                                                                                                                                                    | Livello | Ruolo |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| AC.9.1.1 | Verificare che i classificatori di contenuti specifici per modalità siano aggiornati secondo i programmi documentati (almeno trimestralmente) con nuovi schemi di minacce, esempi avversari e che i parametri di prestazione siano mantenuti al di sopra delle soglie di base. |    3    |  D/V  |

### AC.9.2 Sicurezza CI/CD & Build

|    #     | Descrizione                                                                                                                                                                  | Livello | Ruolo |
| :------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.9.2.1 | Verificare che l'infrastruttura come codice venga sottoposta a scansione ad ogni commit, e che le fusioni siano bloccate in presenza di risultati critici o ad alta gravità. |    1    |  D/V  |
| AC.9.2.2 | Verificare che le pipeline CI/CD utilizzino identità a breve termine e con ambito definito per l'accesso a segreti e infrastrutture.                                         |    2    |  D/V  |
| AC.9.2.3 | Verificare che gli ambienti di build siano isolati dalle reti e dai dati di produzione.                                                                                      |    2    |  D/V  |

### AC.9.3 Sicurezza di Container e Immagini

|    #     | Descrizione                                                                                                                                                                                          | Livello | Ruolo |
| :------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.9.3.1 | Verificare che le immagini dei container siano sottoposte a scansione per bloccare segreti hardcoded (ad esempio, chiavi API, credenziali, certificati).                                             |    2    |  D/V  |
| AC.9.3.2 | Verificare che le immagini dei container siano scansionate secondo i programmi organizzativi, con le vulnerabilità CRITICHE che bloccano il deployment in base alle soglie di rischio organizzative. |    1    |  D/V  |

### AC.9.4 Monitoraggio, Allerta e SIEM

|    #     | Descrizione                                                                                                                                                                    | Livello | Ruolo |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| AC.9.4.1 | Verificare che gli avvisi di sicurezza si integrino con le piattaforme SIEM (Splunk, Elastic o Sentinel) utilizzando formati CEF o STIX/TAXII con arricchimento automatizzato. |    2    |   V   |

### AC.9.5 Gestione delle vulnerabilità

|    #     | Descrizione                                                                                                                                                                               | Livello | Ruolo |
| :------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.9.5.1 | Verificare che le vulnerabilità di gravità ALTA siano corrette secondo le tempistiche di gestione del rischio organizzativo, con procedure di emergenza per le CVE attivamente sfruttate. |    2    |  D/V  |

### AC.9.6 Configurazione e Controllo della Deriva

|    #     | Descrizione                                                                                                                                                                                                                 | Livello | Ruolo |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.9.6.1 | Verificare che la deriva di configurazione venga rilevata utilizzando strumenti (Chef InSpec, AWS Config) secondo i requisiti di monitoraggio dell'organizzazione con rollback automatico per le modifiche non autorizzate. |    2    |  D/V  |

### AC.9.7 Indurimento dell'Ambiente di Produzione

|    #     | Descrizione                                                                                                                                                                                                      | Livello | Ruolo |
| :------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.9.7.1 | Verificare che gli ambienti di produzione blocchino l'accesso SSH, disabilitino gli endpoint di debug e richiedano richieste di modifica con requisiti di preavviso organizzativo, eccetto in caso di emergenze. |    2    |  D/V  |

### AC.9.8 Porte di promozione del rilascio

|    #     | Descrizione                                                                                                                                                                        | Livello | Ruolo |
| :------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.9.8.1 | Verificare che le fasi di promozione includano test di sicurezza automatizzati (SAST, DAST, scansione dei container) con nessuna rilevazione CRITICA richiesta per l’approvazione. |    2    |  D/V  |

### AC.9.9 Monitoraggio del carico di lavoro, della capacità e dei costi

|    #     | Descrizione                                                                                                                                                                                                                                   | Livello | Ruolo |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.9.9.1 | Verificare che l'utilizzo di GPU/TPU sia monitorato con avvisi attivati a soglie definite dall'organizzazione e che venga attivata la scalabilità automatica o il bilanciamento del carico basato sulle politiche di gestione della capacità. |    1    |  D/V  |
| AC.9.9.2 | Verificare che le metriche del carico di lavoro AI (latenza di inferenza, throughput, tassi di errore) siano raccolte secondo i requisiti di monitoraggio organizzativo e correlate con l'utilizzo dell'infrastruttura.                       |    1    |  D/V  |
| AC.9.9.3 | Verificare che il monitoraggio dei costi segua la spesa per carico di lavoro/tenant con avvisi basati sulle soglie di budget organizzativo e controlli automatizzati per superamenti del budget.                                              |    2    |   V   |
| AC.9.9.4 | Verificare che la pianificazione della capacità utilizzi dati storici con periodi di previsione definiti dall'organizzazione e un provisioning delle risorse automatizzato basato sui modelli di domanda.                                     |    3    |   V   |

### AC.9.10 Approvazioni e Tracce di Audit

|     #     | Descrizione                                                                                                                                                                                     | Livello | Ruolo |
| :-------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.9.10.1 | Verificare che la promozione dell'ambiente richieda l'approvazione da parte del personale autorizzato definito a livello organizzativo con firme crittografiche e trilogie di audit immutabili. |    1    |  D/V  |

### AC.9.11 Governance IaC

|     #     | Descrizione                                                                                                                                                                       | Livello | Ruolo |
| :-------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.9.11.1 | Verificare che le modifiche all'infrastructure-as-code richiedano una revisione tra pari con testing automatico e scansione di sicurezza prima della fusione nel ramo principale. |    2    |  D/V  |

### AC.9.12 Gestione dei dati in ambienti non di produzione

|     #     | Descrizione                                                                                                                                                                                                         | Livello | Ruolo |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.9.12.1 | Verificare che i dati non di produzione siano anonimizzati secondo i requisiti organizzativi sulla privacy, con generazione di dati sintetici o mascheramento completo dei dati con rimozione delle PII verificata. |    2    |  D/V  |

### AC.9.13 Backup e Recupero di Emergenza

|     #     | Descrizione                                                                                                                                                                                                              | Livello | Ruolo |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| AC.9.13.1 | Verificare che le configurazioni dell'infrastruttura siano sottoposte a backup secondo i programmi di backup organizzativi verso regioni geograficamente separate con l'implementazione della strategia di backup 3-2-1. |    1    |  D/V  |
| AC.9.13.2 | Verificare che le procedure di recupero siano testate e validate tramite test automatizzati secondo i programmi organizzativi, con obiettivi di RTO e RPO conformi ai requisiti dell'organizzazione.                     |    2    |   V   |
| AC.9.13.3 | Verificare che il disaster recovery includa runbook specifici per l'AI con il ripristino dei pesi del modello, la ricostruzione del cluster GPU e la mappatura delle dipendenze dei servizi.                             |    3    |   V   |

### AC.9.14 Conformità e Documentazione

|     #     | Descrizione                                                                                                                                                                                                    | Livello | Ruolo |
| :-------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.9.14.1 | Verificare che la conformità dell'infrastruttura venga valutata secondo i programmi organizzativi rispetto ai controlli SOC 2, ISO 27001 o FedRAMP con raccolta automatizzata delle evidenze.                  |    2    |  D/V  |
| AC.9.14.2 | Verificare che la documentazione dell'infrastruttura includa diagrammi di rete, mappe del flusso dei dati e modelli di minaccia aggiornati secondo i requisiti della gestione del cambiamento organizzativo.   |    2    |   V   |
| AC.9.14.3 | Verificare che le modifiche all'infrastruttura siano sottoposte a una valutazione automatizzata dell'impatto sulla conformità con flussi di lavoro di approvazione normativa per le modifiche ad alto rischio. |    3    |  D/V  |

### AC.9.15 Hardware e Catena di Fornitura

|     #     | Descrizione                                                                                                                                                                                       | Livello | Ruolo |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.9.15.1 | Verificare che il firmware dell'acceleratore AI (BIOS GPU, firmware TPU) sia verificato con firme crittografiche e aggiornato secondo le tempistiche di gestione delle patch dell'organizzazione. |    2    |  D/V  |
| AC.9.15.2 | Verificare che la catena di approvvigionamento dell'hardware AI includa la verifica della provenienza con certificati del produttore e la convalida dell'imballaggio a prova di manomissione.     |    3    |   V   |

### AC.9.16 Strategia Cloud e Portabilità

|     #     | Descrizione                                                                                                                                                                                           | Livello | Ruolo |
| :-------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.9.16.1 | Verificare che la prevenzione del vendor lock-in nel cloud includa infrastruttura-as-code portabile, API standardizzate e capacità di esportazione dei dati con strumenti di conversione del formato. |    3    |   V   |
| AC.9.16.2 | Verificare che l'ottimizzazione dei costi multi-cloud includa controlli di sicurezza che prevengano la dispersione delle risorse e addebiti non autorizzati per il trasferimento dati cross-cloud.    |    3    |   V   |

### AC.9.17 GitOps e Auto-Riparazione

|     #     | Descrizione                                                                                                                                                                                          | Livello | Ruolo |
| :-------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.9.17.1 | Verifica che i repository GitOps richiedano commit firmati con chiavi GPG e regole di protezione dei branch che impediscano push diretti ai branch principali.                                       |    2    |  D/V  |
| AC.9.17.2 | Verificare che l'infrastruttura autoprotettiva includa la correlazione degli eventi di sicurezza con la risposta automatizzata agli incidenti e i flussi di lavoro per la notifica agli stakeholder. |    3    |   V   |

### AC.9.18 Zero-Trust, Agenti, Provisioning e Attestazione di Residenza

|     #     | Descrizione                                                                                                                                                                             | Livello | Ruolo |
| :-------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| AC.9.18.1 | Verificare che l'accesso alle risorse cloud includa la verifica zero-trust con autenticazione continua.                                                                                 |    2    |  D/V  |
| AC.9.18.2 | Verificare che il provisioning automatizzato dell'infrastruttura includa la convalida delle policy di sicurezza con il blocco del deployment per configurazioni non conformi.           |    2    |  D/V  |
| AC.9.18.3 | Verificare che il provisioning automatico dell'infrastruttura convalidi le politiche di sicurezza durante il CI/CD, bloccando le configurazioni non conformi al momento del deployment. |    2    |  D/V  |
| AC.9.18.4 | Verificare che i requisiti di residenza dei dati siano applicati tramite attestazione crittografica delle ubicazioni di archiviazione.                                                  |    3    |  D/V  |
| AC.9.18.5 | Verificare che le valutazioni di sicurezza del provider cloud includano la modellizzazione delle minacce specifica per l'agente e la valutazione del rischio.                           |    3    |  D/V  |

### AC.9.19 Controllo degli Accessi e Identità

|   #   | Descrizione                                                                                                                                                                                                                    | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 5.1.3 | Verificare che i nuovi responsabili siano sottoposti a un processo di verifica dell'identità conforme a NIST 800-63-3 IAL-2 o a standard equivalenti prima di ricevere l'accesso ai sistemi di produzione.                     |    2    |   D   |
| 5.1.4 | Verificare che le revisioni degli accessi vengano eseguite trimestralmente con rilevamento automatico degli account inattivi, applicazione della rotazione delle credenziali e flussi di lavoro di de-provisioning.            |    2    |   V   |
| 5.2.2 | Verificare che i principi di minimo privilegio siano applicati di default agli account di servizio, iniziando con permessi in sola lettura e richiedendo una giustificazione aziendale documentata per l'accesso in scrittura. |    1    |  D/V  |
| 5.3.3 | Verificare che le definizioni delle policy siano controllate nelle versioni, revisionate dai pari e validate tramite test automatizzati nelle pipeline CI/CD prima del rilascio in produzione.                                 |    2    |   D   |
| 5.3.4 | Verificare che i risultati della valutazione delle policy includano le motivazioni delle decisioni e siano trasmessi ai sistemi SIEM per l'analisi di correlazione e la generazione di report di conformità.                   |    2    |   V   |
| 5.4.4 | Verificare che la latenza nella valutazione delle policy sia continuamente monitorata con avvisi automatizzati per condizioni di timeout che potrebbero consentire il bypass dell'autorizzazione.                              |    2    |   V   |
| 5.5.4 | Verificare che gli algoritmi di redazione siano deterministici, controllati nelle versioni e mantengano registri di audit per supportare le indagini di conformità e l'analisi forense.                                        |    2    |   V   |
| 5.5.5 | Verificare che gli eventi di redazione ad alto rischio generino log adattivi che includano hash crittografici del contenuto originale per il recupero forense senza esposizione dei dati.                                      |    3    |   V   |
| 5.7.5 | Verificare che le condizioni di errore dell'agente e la gestione delle eccezioni includano informazioni sull'ambito delle capacità per supportare l'analisi degli incidenti e le indagini forensi.                             |    3    |   V   |
| 5.4.2 | Verificare che le citazioni, le referenze e le attribuzioni delle fonti nei risultati del modello siano convalidate in base ai diritti del chiamante e rimosse se viene rilevato un accesso non autorizzato.                   |    1    |  D/V  |

### Nuovi elementi da integrare sopra

|   #   | Descrizione                                                                                                                                            | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 2.3.3 | Verificare che l'insieme di caratteri consentiti venga regolarmente esaminato e aggiornato per garantire che rimanga allineato ai requisiti aziendali. |    2    |  D/V  |

