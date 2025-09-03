# Monitoraggio, registrazione e rilevamento di anomalie per C12

## Obiettivo di controllo

Questa sezione definisce i requisiti per fornire visibilità in tempo reale e forense su ciò che il modello e gli altri componenti di IA vedono, fanno e restituiscono, affinché le minacce possano essere rilevate, priorizzate nel triage e da cui apprendere.

## C12.1 Registrazione di richieste e risposte

|   #    | Descrizione                                                                                                                                                                                                                        | Livello | Ruolo |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 12.1.1 | Verifica che tutti i prompt dell'utente e le risposte del modello siano registrati con metadati appropriati (ad es. marcatempo, ID utente, ID sessione, versione del modello).                                                     |    1    |  D/V  |
| 12.1.2 | Verifica che i log siano archiviati in repository sicuri e protetti con controlli di accesso, politiche di conservazione adeguate e procedure di backup.                                                                           |    1    |  D/V  |
| 12.1.3 | Verifica che i sistemi di archiviazione dei log implementino la crittografia a riposo e in transito per proteggere le informazioni sensibili contenute nei log.                                                                    |    1    |  D/V  |
| 12.1.4 | Verifica che i dati sensibili presenti in prompt e output vengano automaticamente redatti o mascherati prima di essere registrati nei log, con regole di redazione configurabili per PII, credenziali e informazioni proprietarie. |    1    |  D/V  |
| 12.1.5 | Verificare che le decisioni di policy e le azioni di filtraggio di sicurezza siano registrate con dettagli sufficienti per consentire l'audit e il debugging dei sistemi di moderazione dei contenuti.                             |    2    |  D/V  |
| 12.1.6 | Verifica che l'integrità del registro sia protetta, ad es. mediante firme crittografiche o archiviazione in scrittura sola.                                                                                                        |    2    |  D/V  |

---

## C12.2 Rilevamento degli abusi e allerta

|   #    | Descrizione                                                                                                                                                                                                          | Livello | Ruolo |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 12.2.1 | Verifica che il sistema rilevi e segnali i noti schemi di jailbreak, i tentativi di iniezione di prompt e gli input ostili utilizzando il rilevamento basato su firme.                                               |    1    |  D/V  |
| 12.2.2 | Verificare che il sistema si integri con le piattaforme SIEM esistenti utilizzando formati di log standard e protocolli.                                                                                             |    1    |  D/V  |
| 12.2.3 | Verifica che gli eventi di sicurezza arricchiti includano contesto specifico dell'IA, come identificatori del modello, punteggi di confidenza e decisioni del filtro di sicurezza.                                   |    2    |  D/V  |
| 12.2.4 | Verifica che il rilevamento delle anomalie comportamentali identifichi modelli di conversazione insoliti, un numero eccessivo di tentativi di riprova o comportamenti di sondaggio sistematici.                      |    2    |  D/V  |
| 12.2.5 | Verifica che i meccanismi di allerta in tempo reale notifichino ai team di sicurezza quando vengano rilevate potenziali violazioni delle politiche o tentativi di attacco.                                           |    2    |  D/V  |
| 12.2.6 | Verifica che siano incluse regole personalizzate per rilevare schemi di minaccia specifici dell'IA, inclusi tentativi di jailbreak coordinati, campagne di iniezione di prompt e attacchi di estrazione del modello. |    2    |  D/V  |
| 12.2.7 | Verifica che i flussi di lavoro di risposta automatizzata agli incidenti possano isolare modelli compromessi, bloccare utenti malevoli e gestire l'escalation di eventi di sicurezza critici.                        |    3    |  D/V  |

---

## C12.3 Rilevamento della deriva del modello

|   #    | Descrizione                                                                                                                                                                                                       | Livello | Ruolo |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 12.3.1 | Verifica che il sistema tenga traccia di metriche di performance di base quali accuratezza, punteggi di confidenza, latenza e tassi di errore tra le versioni del modello e i periodi di tempo.                   |    1    |  D/V  |
| 12.3.2 | Verificare che gli avvisi automatici si attivino quando le metriche di prestazione superano le soglie di degrado predefinite o si discostano significativamente dalle linee di base.                              |    2    |  D/V  |
| 12.3.3 | Verifica che i monitor di rilevamento delle allucinazioni identifichino e segnalino gli esempi in cui gli output del modello contengono informazioni errate dal punto di vista fattuale, incoerenti o fabbricate. |    2    |  D/V  |

---

## C12.4 Telemetria delle Prestazioni e del Comportamento

|   #    | Descrizione                                                                                                                                                                                     | Livello | Ruolo |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 12.4.1 | Verifichi che le metriche operative, tra cui la latenza delle richieste, il consumo di token, l'uso della memoria e il throughput, siano raccolte e monitorate continuamente.                   |    1    |  D/V  |
| 12.4.2 | Verifica che i tassi di successo e di fallimento siano tracciati con la categorizzazione dei tipi di errore e delle loro cause principali.                                                      |    1    |  D/V  |
| 12.4.3 | Verificare che il monitoraggio dell'utilizzo delle risorse includa l'utilizzo di GPU/CPU, il consumo di memoria e i requisiti di archiviazione, con avvisi in caso di superamento delle soglie. |    2    |  D/V  |

---

## C12.5 Pianificazione e Esecuzione della Risposta agli Incidenti di IA

|   #    | Descrizione                                                                                                                                                                                                         | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 12.5.1 | Verifica che i piani di risposta agli incidenti affrontino in modo specifico gli eventi di sicurezza correlati all'IA, tra cui la compromissione del modello, l'avvelenamento dei dati e gli attacchi avversariali. |    1    |  D/V  |
| 12.5.2 | Verifica che i team di risposta agli incidenti abbiano accesso a strumenti forensi specifici per l'IA e competenze per indagare sul comportamento dei modelli e sui vettori di attacco.                             |    2    |  D/V  |
| 12.5.3 | Verificare che l'analisi post-incidente includa considerazioni sul riaddestramento del modello, aggiornamenti dei filtri di sicurezza e l'integrazione delle lezioni apprese nei controlli di sicurezza.            |    3    |  D/V  |

---

## C12.5 Rilevamento della degradazione delle prestazioni dell'Intelligenza Artificiale

Monitora e rileva la degradazione delle prestazioni e della qualità del modello di IA nel tempo.

|   #    | Descrizione                                                                                                                                                               | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 12.5.1 | Verificare che l'accuratezza del modello, la precisione, il richiamo e i punteggi F1 siano monitorati costantemente e confrontati con soglie di riferimento.              |    1    |  D/V  |
| 12.5.2 | Verifica che il rilevamento della deriva dei dati monitori i cambiamenti della distribuzione degli input che potrebbero influire sulle prestazioni del modello.           |    1    |  D/V  |
| 12.5.3 | Verifica che il rilevamento del drift concettuale identifichi i cambiamenti nella relazione tra input e output attesi.                                                    |    2    |  D/V  |
| 12.5.4 | Verifica che il degrado delle prestazioni inneschi avvisi automatici e avvii flussi di lavoro di riaddestramento o sostituzione del modello.                              |    2    |  D/V  |
| 12.5.5 | Verificare che l'analisi della causa principale del degrado possa correlare i cali delle prestazioni con modifiche ai dati, problemi di infrastruttura o fattori esterni. |    3    |   V   |

---

## C12.6 Visualizzazione DAG e Sicurezza del Flusso di Lavoro

Proteggere i sistemi di visualizzazione del flusso di lavoro dalle fughe di informazioni e dagli attacchi di manomissione.

|   #    | Descrizione                                                                                                                                                                                                      | Livello | Ruolo |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 12.6.1 | Verificare che i dati di visualizzazione del DAG siano sanificati per rimuovere informazioni sensibili prima dell'archiviazione o della trasmissione.                                                            |    1    |  D/V  |
| 12.6.2 | Verificare che i controlli di accesso alla visualizzazione del flusso di lavoro assicurino che solo gli utenti autorizzati possano visualizzare i percorsi decisionali degli agenti e le tracce di ragionamento. |    1    |  D/V  |
| 12.6.3 | Verifica che l'integrità dei dati DAG sia protetta mediante firme criptografiche e meccanismi di archiviazione a prova di manomissione.                                                                          |    2    |  D/V  |
| 12.6.4 | Verificare che i sistemi di visualizzazione dei flussi di lavoro implementino la validazione dell'input per prevenire attacchi di iniezione attraverso dati di nodi o archi appositamente costruiti.             |    2    |  D/V  |
| 12.6.5 | Verificare che gli aggiornamenti in tempo reale dei DAG siano limitati in frequenza e validati per prevenire attacchi DoS sui sistemi di visualizzazione.                                                        |    3    |  D/V  |

---

## C12.7 Monitoraggio proattivo del comportamento di sicurezza

Rilevazione e prevenzione delle minacce alla sicurezza attraverso l'analisi proattiva del comportamento degli agenti.

|   #    | Descrizione                                                                                                                                                                       | Livello | Ruolo |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 12.7.1 | Verifica che i comportamenti degli agenti proattivi siano validati per la sicurezza prima dell'esecuzione, con integrazione della valutazione del rischio.                        |    1    |  D/V  |
| 12.7.2 | Verifica che gli inneschi di iniziativa autonoma includano la valutazione del contesto di sicurezza e la valutazione del panorama delle minacce.                                  |    2    |  D/V  |
| 12.7.3 | Verifica che i modelli di comportamento proattivo siano analizzati per potenziali implicazioni di sicurezza e conseguenze non intenzionali.                                       |    2    |  D/V  |
| 12.7.4 | Verificare che le azioni proattive critiche per la sicurezza richiedano catene di approvazione esplicite con registri di audit.                                                   |    3    |  D/V  |
| 12.7.5 | Verifica che il rilevamento delle anomalie comportamentali identifichi deviazioni nei modelli di comportamento degli agenti proattivi che potrebbero indicare una compromissione. |    3    |  D/V  |

---

## Riferimenti

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)
* [EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R1689)

