# Appendice B: Controlli Strategici

## C4.15 Sicurezza dell'Infrastruttura Resistente alla Quantum

Preparare l'infrastruttura AI per le minacce del calcolo quantistico tramite crittografia post-quantistica e protocolli quantisticamente sicuri.

|   #    | Descrizione                                                                                                                                                                                            | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 4.15.1 | Verificare che l'infrastruttura AI implementi algoritmi crittografici post-quantistici approvati dal NIST (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) per lo scambio di chiavi e le firme digitali. |    3    |  D/V  |
| 4.15.2 | Verificare che i sistemi di distribuzione di chiavi quantistiche (QKD) siano implementati per comunicazioni AI ad alta sicurezza con protocolli di gestione chiavi quantum-safe.                       |    3    |  D/V  |
| 4.15.3 | Verificare che i framework di agilità crittografica permettano una migrazione rapida verso i nuovi algoritmi post-quantistici con rotazione automatica di certificati e chiavi.                        |    3    |  D/V  |
| 4.15.4 | Verificare che la modellazione delle minacce quantistiche valuti la vulnerabilità dell'infrastruttura AI ad attacchi quantistici con tempi di migrazione documentati e valutazioni del rischio.        |    3    |   V   |
| 4.15.5 | Verificare che i sistemi crittografici ibridi classico-quantistici forniscano una difesa stratificata durante il periodo di transizione quantistica con monitoraggio delle prestazioni.                |    3    |  D/V  |

---

## C4.17 Infrastruttura a Conoscenza Zero

Implementare sistemi di zero-knowledge proof per la verifica e l'autenticazione di AI che preservano la privacy senza rivelare informazioni sensibili.

|   #    | Descrizione                                                                                                                                                                                            | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 4.17.1 | Verificare che le prove a conoscenza zero (ZK-SNARKs, ZK-STARKs) confermino l'integrità del modello AI e la provenienza dell'addestramento senza esporre i pesi del modello o i dati di addestramento. |    3    |  D/V  |
| 4.17.2 | Verificare che i sistemi di autenticazione basati su ZK consentano la verifica degli utenti preservando la privacy per i servizi AI senza rivelare informazioni correlate all'identità.                |    3    |  D/V  |
| 4.17.3 | Verificare che i protocolli di intersezione di insiemi privati (PSI) consentano un confronto sicuro dei dati per l’IA federata senza esporre i singoli set di dati.                                    |    3    |  D/V  |
| 4.17.4 | Verificare che i sistemi di machine learning a conoscenza zero (ZKML) permettano inferenze AI verificabili con prova crittografica del calcolo corretto.                                               |    3    |  D/V  |
| 4.17.5 | Verificare che gli ZK-rollup forniscano un'elaborazione delle transazioni AI scalabile e preservante la privacy con verifica batch e ridotto overhead computazionale.                                  |    3    |  D/V  |

---

## C4.18 Prevenzione degli Attacchi Side-Channel

Proteggi l'infrastruttura AI dagli attacchi side-channel basati su tempistiche, potenza, elettromagnetismo e cache che potrebbero divulgare informazioni sensibili.

|   #    | Descrizione                                                                                                                                                                                        | Livello | Ruolo |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.18.1 | Verificare che il tempo di inferenza dell’IA sia normalizzato utilizzando algoritmi a tempo costante e padding per prevenire attacchi di estrazione del modello basati sul tempo.                  |    3    |  D/V  |
| 4.18.2 | Verifica che la protezione contro l'analisi della potenza includa l'iniezione di rumore, il filtraggio della linea di alimentazione e modelli di esecuzione randomizzati per l'hardware AI.        |    3    |  D/V  |
| 4.18.3 | Verificare che la mitigazione dei canali laterali basati sulla cache utilizzi la partizione della cache, la randomizzazione e le istruzioni di flush per prevenire la fuoriuscita di informazioni. |    3    |  D/V  |
| 4.18.4 | Verificare che la protezione dalle emanazioni elettromagnetiche includa schermatura, filtraggio del segnale e elaborazione casuale per prevenire attacchi di tipo TEMPEST.                         |    3    |  D/V  |
| 4.18.5 | Verificare che le difese contro i canali laterali microarchitetturali includano controlli sull'esecuzione speculativa e l'oscuramento dei modelli di accesso alla memoria.                         |    3    |  D/V  |

---

## C4.19 Sicurezza dell'hardware neuromorfico e specializzato per l'IA

Proteggere le architetture hardware emergenti per l'IA, inclusi chip neuromorfici, FPGA, ASIC personalizzati e sistemi di calcolo ottico.

|   #    | Descrizione                                                                                                                                                                                            | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 4.19.1 | Verificare che la sicurezza del chip neuromorfico includa la crittografia dei modelli di spike, la protezione dei pesi sinaptici e la convalida basata sull'hardware delle regole di apprendimento.    |    3    |  D/V  |
| 4.19.2 | Verificare che gli acceleratori AI basati su FPGA implementino la crittografia del bitstream, meccanismi anti-manomissione e il caricamento sicuro della configurazione con aggiornamenti autenticati. |    3    |  D/V  |
| 4.19.3 | Verificare che la sicurezza ASIC personalizzata includa processori di sicurezza on-chip, root di fiducia hardware e memorizzazione sicura delle chiavi con rilevamento delle manomissioni.             |    3    |  D/V  |
| 4.19.4 | Verificare che i sistemi di calcolo ottico implementino crittografia ottica quantisticamente sicura, commutazione fotonica sicura e elaborazione del segnale ottico protetta.                          |    3    |  D/V  |
| 4.19.5 | Verificare che i chip AI ibridi analogico-digitali includano calcolo analogico sicuro, archiviazione protetta dei pesi e conversione analogico-digitale autenticata.                                   |    3    |  D/V  |

---

## C4.20 Infrastruttura di Calcolo per la Privacy

Implementare controlli infrastrutturali per il calcolo che preserva la privacy al fine di proteggere i dati sensibili durante l'elaborazione e l'analisi dell'IA.

|   #    | Descrizione                                                                                                                                                                                                     | Livello | Ruolo |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.20.1 | Verificare che l'infrastruttura di crittografia omomorfica consenta il calcolo crittografato su carichi di lavoro AI sensibili con verifica dell'integrità crittografica e monitoraggio delle prestazioni.      |    3    |  D/V  |
| 4.20.2 | Verificare che i sistemi di recupero privato delle informazioni consentano interrogazioni al database senza rivelare i modelli di query, proteggendo crittograficamente i modelli di accesso.                   |    3    |  D/V  |
| 4.20.3 | Verificare che i protocolli di calcolo multipartito sicuro consentano l'inferenza AI preservando la privacy senza esporre input individuali o calcoli intermedi.                                                |    3    |  D/V  |
| 4.20.4 | Verificare che la gestione delle chiavi preservi la privacy includa la generazione distribuita delle chiavi, la crittografia a soglia e la rotazione sicura delle chiavi con protezione supportata da hardware. |    3    |  D/V  |
| 4.20.5 | Verificare che le prestazioni del calcolo a tutela della privacy siano ottimizzate tramite batching, caching e accelerazione hardware, mantenendo al contempo le garanzie di sicurezza crittografica.           |    3    |  D/V  |

| 4.9.1 | Verificare che tutti gli ambienti cloud siano integrati in sistemi di identità centralizzati per garantire un'autenticazione coerente. | 1 | D/V |
| 4.9.2 | Verificare che le distribuzioni multi-cloud utilizzino standard di identità federata (ad es., OIDC, SAML) con applicazione centralizzata delle policy tra i provider. | 2 | D/V |
| 4.9.3 | Verificare che i trasferimenti di dati cross-cloud e ibridi utilizzino la crittografia end-to-end con chiavi gestite dal cliente e rispettino i requisiti di residenza dei dati giurisdizionale. | 2 | D/V |
| 4.9.1 | Verificare che l'integrazione dello storage cloud utilizzi la crittografia end-to-end con la gestione delle chiavi controllata dall'agente. | 1 | D/V |
| 4.9.2 | Verificare che i confini di sicurezza del deployment ibrido siano chiaramente definiti con canali di comunicazione crittografati. | 2 | D/V |

