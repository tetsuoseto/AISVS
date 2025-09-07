# C12 Monitoraggio, Registrazione e Rilevamento Anomalie

## Obiettivo di Controllo

Questa sezione fornisce i requisiti per offrire una visibilità in tempo reale e forense su ciò che il modello e gli altri componenti di AI vedono, fanno e restituiscono, affinché le minacce possano essere rilevate, classificate e analizzate.

## C12.1 Registrazione delle richieste e delle risposte

|   #    | Descrizione                                                                                                                                                                                                                 | Livello | Ruolo |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 12.1.1 | Verificare che tutti i prompt degli utenti e le risposte del modello siano registrati con metadati appropriati (ad esempio, timestamp, ID utente, ID sessione, versione del modello).                                       |    1    |  D/V  |
| 12.1.2 | Verificare che i log siano archiviati in repository sicuri, con controllo degli accessi, politiche di conservazione appropriate e procedure di backup.                                                                      |    1    |  D/V  |
| 12.1.3 | Verificare che i sistemi di archiviazione dei log implementino la crittografia a riposo e in transito per proteggere le informazioni sensibili contenute nei log.                                                           |    1    |  D/V  |
| 12.1.4 | Verificare che i dati sensibili nei prompt e nei risultati siano automaticamente oscurati o mascherati prima della registrazione, con regole di oscuramento configurabili per PII, credenziali e informazioni proprietarie. |    1    |  D/V  |
| 12.1.5 | Verificare che le decisioni politiche e le azioni di filtraggio della sicurezza siano registrate con dettagli sufficienti per consentire l'audit e il debug dei sistemi di moderazione dei contenuti.                       |    2    |  D/V  |
| 12.1.6 | Verificare che l'integrità dei log sia protetta tramite, ad esempio, firme crittografiche o memorizzazione in sola scrittura.                                                                                               |    2    |  D/V  |

---

## C12.2 Rilevamento e Allerta per Abusi

|   #    | Descrizione                                                                                                                                                                                                                        | Livello | Ruolo |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 12.2.1 | Verificare che il sistema rilevi e avvisi in merito a pattern di jailbreak noti, tentativi di iniezione di prompt e input avversari utilizzando la rilevazione basata su firme.                                                    |    1    |  D/V  |
| 12.2.2 | Verificare che il sistema si integri con le piattaforme esistenti di Security Information and Event Management (SIEM) utilizzando formati di log e protocolli standard.                                                            |    1    |  D/V  |
| 12.2.3 | Verificare che gli eventi di sicurezza arricchiti includano contesti specifici dell'IA come identificatori di modelli, punteggi di confidenza e decisioni del filtro di sicurezza.                                                 |    2    |  D/V  |
| 12.2.4 | Verificare che il rilevamento delle anomalie comportamentali identifichi modelli di conversazione insoliti, tentativi di ripetizione eccessivi o comportamenti di sondaggio sistematici.                                           |    2    |  D/V  |
| 12.2.5 | Verificare che i meccanismi di allerta in tempo reale notifichino i team di sicurezza quando vengono rilevate potenziali violazioni di policy o tentativi di attacco.                                                              |    2    |  D/V  |
| 12.2.6 | Verificare che siano incluse regole personalizzate per rilevare modelli di minacce specifici per l'IA, comprese le tentativi coordinati di jailbreak, le campagne di iniezione di prompt e gli attacchi di estrazione del modello. |    2    |  D/V  |
| 12.2.7 | Verificare che i flussi di lavoro automatizzati di risposta agli incidenti possano isolare i modelli compromessi, bloccare gli utenti malevoli e segnalare gli eventi di sicurezza critici.                                        |    3    |  D/V  |

---

## C12.3 Rilevamento della deriva del modello

|   #    | Descrizione                                                                                                                                                                                      | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 12.3.1 | Verificare che il sistema monitori metriche di prestazione di base come accuratezza, punteggi di fiducia, latenza e tassi di errore attraverso le versioni del modello e i periodi di tempo.     |    1    |  D/V  |
| 12.3.2 | Verificare che l'allerta automatica venga attivata quando le metriche di prestazione superano le soglie di degrado predefinite o si discostano significativamente dai valori basali.             |    2    |  D/V  |
| 12.3.3 | Verificare che i monitor di rilevamento delle allucinazioni identifichino e segnalino i casi in cui le risposte del modello contengano informazioni fattualmente errate, incoerenti o inventate. |    2    |  D/V  |

---

## C12.4 Telemetria delle Prestazioni e del Comportamento

|   #    | Descrizione                                                                                                                                                                                   | Livello | Ruolo |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 12.4.1 | Verificare che le metriche operative, inclusi la latenza delle richieste, il consumo di token, l’utilizzo della memoria e la larghezza di banda, siano continuamente raccolte e monitorate.   |    1    |  D/V  |
| 12.4.2 | Verificare che i tassi di successo e di fallimento siano monitorati con la categorizzazione dei tipi di errore e delle loro cause principali.                                                 |    1    |  D/V  |
| 12.4.3 | Verificare che il monitoraggio dell'utilizzo delle risorse includa l'uso della GPU/CPU, il consumo di memoria e i requisiti di archiviazione con allerta in caso di superamento delle soglie. |    2    |  D/V  |

---

## C12.5 Pianificazione ed esecuzione della risposta agli incidenti di IA

|   #    | Descrizione                                                                                                                                                                                              | Livello | Ruolo |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 12.5.1 | Verificare che i piani di risposta agli incidenti affrontino specificamente eventi di sicurezza legati all'IA, inclusi il compromesso del modello, l'avvelenamento dei dati e gli attacchi adversariali. |    1    |  D/V  |
| 12.5.2 | Verificare che i team di risposta agli incidenti abbiano accesso a strumenti forensi specifici per l'IA e competenze per indagare il comportamento dei modelli e i vettori di attacco.                   |    2    |  D/V  |
| 12.5.3 | Verificare che l'analisi post-incidente includa considerazioni sul retraining del modello, aggiornamenti dei filtri di sicurezza e l'integrazione delle lezioni apprese nei controlli di sicurezza.      |    3    |  D/V  |

---

## C12.5 Rilevamento del Deterioramento delle Prestazioni dell'IA

Monitorare e rilevare il degrado delle prestazioni e della qualità del modello di intelligenza artificiale nel tempo.

|   #    | Descrizione                                                                                                                                                              | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 12.5.1 | Verificare che l'accuratezza del modello, la precisione, il richiamo e i punteggi F1 siano continuamente monitorati e confrontati con le soglie di riferimento.          |    1    |  D/V  |
| 12.5.2 | Verificare che il rilevamento del drift dei dati monitori le variazioni nella distribuzione degli input che potrebbero influire sulle prestazioni del modello.           |    1    |  D/V  |
| 12.5.3 | Verificare che il rilevamento del concetto di drift identifichi i cambiamenti nella relazione tra input e output previsti.                                               |    2    |  D/V  |
| 12.5.4 | Verificare che il degrado delle prestazioni attivi avvisi automatici e avvii workflow di riqualificazione o sostituzione del modello.                                    |    2    |  D/V  |
| 12.5.5 | Verificare che l’analisi della causa principale della degradazione correli i cali di prestazioni con cambiamenti nei dati, problemi di infrastruttura o fattori esterni. |    3    |   V   |

---

## C12.6 Visualizzazione DAG e Sicurezza del Flusso di Lavoro

Proteggere i sistemi di visualizzazione del flusso di lavoro da fughe di informazioni e attacchi di manipolazione.

|   #    | Descrizione                                                                                                                                                                                          | Livello | Ruolo |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 12.6.1 | Verificare che i dati di visualizzazione del DAG siano sanificati per rimuovere informazioni sensibili prima della memorizzazione o della trasmissione.                                              |    1    |  D/V  |
| 12.6.2 | Verificare che i controlli di accesso alla visualizzazione del workflow garantiscano che solo gli utenti autorizzati possano vedere i percorsi decisionali dell'agente e le tracce del ragionamento. |    1    |  D/V  |
| 12.6.3 | Verificare che l'integrità dei dati del DAG sia protetta tramite firme crittografiche e meccanismi di memorizzazione a prova di manomissione.                                                        |    2    |  D/V  |
| 12.6.4 | Verificare che i sistemi di visualizzazione dei workflow implementino la convalida dell'input per prevenire attacchi di injection tramite dati manipolati di nodi o archi.                           |    2    |  D/V  |
| 12.6.5 | Verificare che gli aggiornamenti in tempo reale del DAG siano limitati in frequenza e convalidati per prevenire attacchi di denial-of-service sui sistemi di visualizzazione.                        |    3    |  D/V  |

---

## C12.7 Monitoraggio Proattivo del Comportamento di Sicurezza

Rilevamento e prevenzione delle minacce alla sicurezza attraverso l'analisi proattiva del comportamento degli agenti.

|   #    | Descrizione                                                                                                                                                     | Livello | Ruolo |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 12.7.1 | Verificare che i comportamenti proattivi dell'agente siano convalidati per la sicurezza prima dell'esecuzione con l'integrazione della valutazione del rischio. |    1    |  D/V  |
| 12.7.2 | Verificare che le iniziative autonome includano la valutazione del contesto di sicurezza e la valutazione del panorama delle minacce.                           |    2    |  D/V  |
| 12.7.3 | Verificare che i modelli di comportamento proattivo siano analizzati per potenziali implicazioni di sicurezza e conseguenze non intenzionali.                   |    2    |  D/V  |
| 12.7.4 | Verificare che le azioni proattive critiche per la sicurezza richiedano catene di approvazione esplicite con registrazioni di audit.                            |    3    |  D/V  |
| 12.7.5 | Verificare che il rilevamento di anomalie comportamentali identifichi deviazioni nei modelli degli agenti proattivi che potrebbero indicare un compromesso.     |    3    |  D/V  |

---

## Riferimenti

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)
* [EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R1689)

