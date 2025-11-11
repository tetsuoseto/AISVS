# C12 Monitoraggio, Registrazione e Rilevamento delle Anomalie

## Obiettivo di Controllo

Questa sezione fornisce requisiti per offrire una visibilità in tempo reale e forense su ciò che il modello e altri componenti AI vedono, fanno e restituiscono, in modo che le minacce possano essere rilevate, gestite e analizzate per apprendimento.

## C12.1 Registrazione delle Richieste e delle Risposte

|   #    | Descrizione                                                                                                                                                                                                                                                         | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 12.1.1 | Verificare che tutti i prompt utente e le risposte del modello siano registrati con i metadati appropriati (ad esempio timestamp, ID utente, ID sessione, versione del modello).                                                                                    |    1    |  D/V  |
| 12.1.2 | Verificare che i log siano archiviati in repository sicuri, con accesso controllato, dotati di politiche di conservazione appropriate e procedure di backup.                                                                                                        |    1    |  D/V  |
| 12.1.3 | Verificare che i sistemi di archiviazione dei log implementino la crittografia a riposo e in transito per proteggere le informazioni sensibili contenute nei log.                                                                                                   |    1    |  D/V  |
| 12.1.4 | Verificare che i dati sensibili nei prompt e nei risultati siano automaticamente oscurati o mascherati prima della registrazione, con regole di oscuramento configurabili per informazioni personali identificabili (PII), credenziali e informazioni proprietarie. |    1    |  D/V  |
| 12.1.5 | Verificare che le decisioni politiche e le azioni di filtraggio di sicurezza siano registrate con dettagli sufficienti per consentire la revisione e il debug dei sistemi di moderazione dei contenuti.                                                             |    2    |  D/V  |
| 12.1.6 | Verificare che l'integrità dei log sia protetta tramite, ad esempio, firme crittografiche o archiviazione in sola scrittura.                                                                                                                                        |    2    |  D/V  |

---

## C12.2 Rilevamento e Allerta degli Abusi

|   #    | Descrizione                                                                                                                                                                                                         | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 12.2.1 | Verificare che il sistema rilevi e avvisi sulle pattern di jailbreak conosciuti, sui tentativi di iniezione di prompt e sugli input avversari utilizzando il rilevamento basato su firme.                           |    1    |  D/V  |
| 12.2.2 | Verificare che il sistema si integri con le piattaforme di Security Information and Event Management (SIEM) esistenti utilizzando formati di log e protocolli standard.                                             |    1    |  D/V  |
| 12.2.3 | Verificare che gli eventi di sicurezza arricchiti includano il contesto specifico dell'IA come gli identificatori del modello, i punteggi di confidenza e le decisioni del filtro di sicurezza.                     |    2    |  D/V  |
| 12.2.4 | Verificare che il rilevamento delle anomalie comportamentali identifichi modelli di conversazione insoliti, tentativi di ripetizione eccessivi o comportamenti di sondaggio sistematici.                            |    2    |  D/V  |
| 12.2.5 | Verificare che i meccanismi di allerta in tempo reale notificano i team di sicurezza quando vengono rilevate potenziali violazioni delle policy o tentativi di attacco.                                             |    2    |  D/V  |
| 12.2.6 | Verifica che siano incluse regole personalizzate per rilevare schemi di minacce specifici dell’IA, inclusi tentativi coordinati di jailbreak, campagne di iniezione di prompt e attacchi di estrazione del modello. |    2    |  D/V  |
| 12.2.7 | Verificare che i workflow automatizzati di risposta agli incidenti possano isolare i modelli compromessi, bloccare gli utenti malintenzionati e segnalare gli eventi di sicurezza critici.                          |    3    |  D/V  |

---

## C12.3 Rilevamento del Drift del Modello

|   #    | Descrizione                                                                                                                                                                                      | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 12.3.1 | Verificare che il sistema monitori metriche di prestazione di base come accuratezza, punteggi di confidenza, latenza e tassi di errore attraverso le versioni del modello e i periodi temporali. |    1    |  D/V  |
| 12.3.2 | Verificare che gli avvisi automatici vengano attivati quando i metriche di prestazione superano le soglie di degrado predefinite o si discostano significativamente dalle linee di base.         |    2    |  D/V  |
| 12.3.3 | Verificare che i sistemi di rilevamento delle allucinazioni identifichino e segnalino i casi in cui le risposte del modello contengano informazioni fattualmente errate, incoerenti o inventate. |    2    |  D/V  |

---

## C12.4 Telemetria delle Prestazioni e del Comportamento

|   #    | Descrizione                                                                                                                                                                                 | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 12.4.1 | Verificare che le metriche operative, inclusi la latenza delle richieste, il consumo di token, l'uso della memoria e la produttività, siano continuamente raccolte e monitorate.            |    1    |  D/V  |
| 12.4.2 | Verificare che i tassi di successo e di fallimento siano monitorati con la categorizzazione dei tipi di errore e delle loro cause principali.                                               |    1    |  D/V  |
| 12.4.3 | Verificare che il monitoraggio dell'utilizzo delle risorse includa l'uso di GPU/CPU, il consumo di memoria e i requisiti di archiviazione, con allerta in caso di superamento delle soglie. |    2    |  D/V  |

---

## C12.5 Pianificazione ed Esecuzione della Risposta agli Incidenti di AI

|   #    | Descrizione                                                                                                                                                                                                               | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 12.5.1 | Verificare che i piani di risposta agli incidenti affrontino specificamente gli eventi di sicurezza legati all'intelligenza artificiale, inclusi compromissioni del modello, avvelenamento dei dati e attacchi avversari. |    1    |  D/V  |
| 12.5.2 | Verificare che i team di risposta agli incidenti abbiano accesso a strumenti forensi specifici per l'IA e a competenze per investigare il comportamento dei modelli e i vettori di attacco.                               |    2    |  D/V  |
| 12.5.3 | Verificare che l'analisi post-incidente includa considerazioni sul retraining del modello, aggiornamenti dei filtri di sicurezza e l'integrazione delle lezioni apprese nei controlli di sicurezza.                       |    3    |  D/V  |

---

## C12.6 Rilevamento del Deterioramento delle Prestazioni dell'AI

Monitorare e rilevare il degrado delle prestazioni e della qualità del modello di IA nel tempo.

|   #    | Descrizione                                                                                                                                                    | Livello | Ruolo |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 12.6.1 | Verificare che accuratezza, precisione, richiamo e punteggi F1 del modello siano monitorati continuamente e confrontati con le soglie di base.                 |    1    |  D/V  |
| 12.6.2 | Verificare che il rilevamento del drift dei dati monitori le variazioni nella distribuzione degli input che potrebbero influire sulle prestazioni del modello. |    1    |  D/V  |
| 12.6.3 | Verificare che il rilevamento del concept drift individui cambiamenti nella relazione tra input e output attesi.                                               |    2    |  D/V  |
| 12.6.4 | Verificare che il degrado delle prestazioni attivi automaticamente gli avvisi e avvii i flussi di lavoro per il riaddestramento o la sostituzione del modello. |    2    |  D/V  |
| 12.6.5 | Verificare che l'analisi delle cause primarie del degrado correli i cali di prestazioni con modifiche dei dati, problemi infrastrutturali o fattori esterni.   |    3    |   V   |

---

## C12.7 Visualizzazione DAG e Sicurezza del Flusso di Lavoro

Proteggere i sistemi di visualizzazione del flusso di lavoro da perdite di informazioni e attacchi di manipolazione.

|   #    | Descrizione                                                                                                                                                                                                        | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 12.7.1 | Verificare che i dati di visualizzazione DAG siano puliti per rimuovere informazioni sensibili prima della memorizzazione o della trasmissione.                                                                    |    1    |  D/V  |
| 12.7.2 | Verificare che i controlli di accesso alla visualizzazione del flusso di lavoro garantiscano che solo gli utenti autorizzati possano visualizzare i percorsi decisionali degli agenti e le tracce di ragionamento. |    1    |  D/V  |
| 12.7.3 | Verificare che l'integrità dei dati DAG sia protetta tramite firme crittografiche e meccanismi di archiviazione a prova di manomissione.                                                                           |    2    |  D/V  |
| 12.7.4 | Verificare che i sistemi di visualizzazione del flusso di lavoro implementino la convalida degli input per prevenire attacchi di injection tramite dati manipolati di nodi o archi.                                |    2    |  D/V  |
| 12.7.5 | Verificare che gli aggiornamenti DAG in tempo reale siano limitati nella frequenza e convalidati per prevenire attacchi di negazione del servizio sui sistemi di visualizzazione.                                  |    3    |  D/V  |

---

## C12.8 Monitoraggio Proattivo del Comportamento di Sicurezza

Rilevamento e prevenzione delle minacce alla sicurezza attraverso l'analisi proattiva del comportamento degli agenti.

|   #    | Descrizione                                                                                                                                                     | Livello | Ruolo |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 12.8.1 | Verificare che i comportamenti proattivi degli agenti siano convalidati in termini di sicurezza prima dell'esecuzione, integrando una valutazione del rischio.  |    1    |  D/V  |
| 12.8.2 | Verificare che le iniziative autonome includano la valutazione del contesto di sicurezza e l’analisi del panorama delle minacce.                                |    2    |  D/V  |
| 12.8.3 | Verificare che i modelli di comportamento proattivo siano analizzati per potenziali implicazioni di sicurezza e conseguenze non intenzionali.                   |    2    |  D/V  |
| 12.8.4 | Verificare che le azioni proattive critiche per la sicurezza richiedano catene di approvazione esplicite con tracciamenti di audit.                             |    3    |  D/V  |
| 12.8.5 | Verificare che il rilevamento di anomalie comportamentali identifichi deviazioni nei modelli degli agenti proattivi che potrebbero indicare una compromissione. |    3    |  D/V  |

---

## Riferimenti

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)

