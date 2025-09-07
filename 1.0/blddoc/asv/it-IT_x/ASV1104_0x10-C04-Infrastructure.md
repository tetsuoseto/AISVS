# Sicurezza dell'Infrastruttura, della Configurazione e del Deployment C4

## Obiettivo di Controllo

L'infrastruttura di intelligenza artificiale deve essere rafforzata contro l'escalation dei privilegi, la manomissione della catena di fornitura e i movimenti laterali tramite configurazioni sicure, isolamento durante l'esecuzione, pipeline di distribuzione affidabili e monitoraggio completo. Solo componenti e configurazioni di infrastruttura autorizzati e validati raggiungono la produzione attraverso processi controllati che mantengono sicurezza, integrità e tracciabilità.

Obiettivo principale di sicurezza: solo i componenti infrastrutturali firmati crittograficamente e sottoposti a scansione delle vulnerabilità raggiungono la produzione tramite pipeline di convalida automatizzate che applicano le politiche di sicurezza e mantengono tracce di controllo immutabili.

---

## C4.1 Isolamento dell'Ambiente di Esecuzione

Impedire fughe dal container e escalation di privilegi attraverso primitive di isolamento a livello kernel e controlli di accesso obbligatori.

|   #   | Descrizione                                                                                                                                                                                                                                       | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.1.1 | Verificare che tutti i container AI eliminino TUTTE le capacità Linux eccetto CAP_SETUID, CAP_SETGID e le capacità esplicitamente richieste documentate nelle baseline di sicurezza.                                                              |    1    |  D/V  |
| 4.1.2 | Verificare che i profili seccomp blocchino tutte le chiamate di sistema tranne quelle presenti nelle whitelist pre-approvate, con le violazioni che terminano il container e generano avvisi di sicurezza.                                        |    1    |  D/V  |
| 4.1.3 | Verificare che i carichi di lavoro AI vengano eseguiti con filesystem root di sola lettura, tmpfs per i dati temporanei e volumi nominati per i dati persistenti con opzioni di mount noexec applicate.                                           |    2    |  D/V  |
| 4.1.4 | Verificare che il monitoraggio in runtime basato su eBPF (Falco, Tetragon o equivalente) rilevi i tentativi di escalation dei privilegi e termini automaticamente i processi responsabili entro i tempi di risposta previsti dall'organizzazione. |    2    |  D/V  |
| 4.1.5 | Verificare che i carichi di lavoro AI ad alto rischio vengano eseguiti in ambienti isolati dall'hardware (Intel TXT, AMD SVM o nodi bare-metal dedicati) con verifica di attestazione.                                                            |    3    |  D/V  |

---

## C4.2 Pipeline Sicure di Build e Deployment

Garantire l'integrità crittografica e la sicurezza della catena di approvvigionamento tramite build riproducibili e artefatti firmati.

|   #   | Descrizione                                                                                                                                                                                                          | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.2.1 | Verificare che l'infrastruttura come codice venga scansionata con strumenti (tfsec, Checkov o Terrascan) ad ogni commit, bloccando le fusioni in presenza di rilevamenti con severità CRITICA o ALTA.                |    1    |  D/V  |
| 4.2.2 | Verificare che le compilazioni dei container siano riproducibili con hash SHA256 identici tra le compilazioni e generare attestazioni di provenienza SLSA Livello 3 firmate con Sigstore.                            |    1    |  D/V  |
| 4.2.3 | Verificare che le immagini dei container incorporino SBOM CycloneDX o SPDX e siano firmate con Cosign prima del push al registro, con il rifiuto delle immagini non firmate durante la distribuzione.                |    2    |  D/V  |
| 4.2.4 | Verificare che le pipeline CI/CD utilizzino token OIDC da HashiCorp Vault, ruoli IAM AWS o identità gestite Azure con durate che non superano i limiti stabiliti dalla politica di sicurezza organizzativa.          |    2    |  D/V  |
| 4.2.5 | Verificare che le firme Cosign e la provenienza SLSA siano validate durante il processo di distribuzione prima dell'esecuzione del container e che gli errori di verifica causino il fallimento della distribuzione. |    2    |  D/V  |
| 4.2.6 | Verificare che gli ambienti di build vengano eseguiti in container effimeri o VM senza storage persistente e con isolamento di rete rispetto alle VPC di produzione.                                                 |    2    |  D/V  |

---

## C4.3 Sicurezza di Rete e Controllo degli Accessi

Implementare il networking a zero-trust con politiche di default-deny e comunicazioni criptate.

|   #   | Descrizione                                                                                                                                                                                              | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.3.1 | Verificare che le NetworkPolicy di Kubernetes o qualsiasi equivalente implementino il default-deny per ingressi/uscite con regole esplicite di autorizzazione per le porte necessarie (443, 8080, ecc.). |    1    |  D/V  |
| 4.3.2 | Verificare che SSH (porta 22), RDP (porta 3389) e gli endpoint dei metadata cloud (169.254.169.254) siano bloccati o richiedano l’autenticazione basata su certificato.                                  |    1    |  D/V  |
| 4.3.3 | Verificare che il traffico in uscita venga filtrato tramite proxy HTTP/HTTPS (Squid, Istio o gateway NAT cloud) con liste di domini consentiti e che le richieste bloccate vengano registrate.           |    2    |  D/V  |
| 4.3.4 | Verificare che la comunicazione tra servizi utilizzi mutual TLS con certificati ruotati secondo la politica organizzativa e che la validazione dei certificati sia applicata (nessun flag skip-verify).  |    2    |  D/V  |
| 4.3.5 | Verificare che l'infrastruttura AI funzioni in VPC/VNet dedicati senza accesso diretto a internet e comunichi esclusivamente attraverso gateway NAT o host bastione.                                     |    2    |  D/V  |

---

## C4.4 Gestione dei Segreti e delle Chiavi Criptografiche

Proteggi le credenziali tramite archiviazione supportata da hardware e rotazione automatizzata con accesso a fiducia zero.

|   #   | Descrizione                                                                                                                                                                                                                 | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.4.1 | Verificare che i segreti siano archiviati in HashiCorp Vault, AWS Secrets Manager, Azure Key Vault o Google Secret Manager con crittografia a riposo utilizzando AES-256.                                                   |    1    |  D/V  |
| 4.4.2 | Verificare che le chiavi crittografiche siano generate in HSM conformi a FIPS 140-2 Livello 2 (AWS CloudHSM, Azure Dedicated HSM) con rotazione delle chiavi secondo la politica crittografica organizzativa.               |    1    |  D/V  |
| 4.4.3 | Verificare che la rotazione dei segreti sia automatizzata con un deployment senza tempi di inattività e una rotazione immediata attivata da cambiamenti del personale o incidenti di sicurezza.                             |    2    |  D/V  |
| 4.4.4 | Verificare che le immagini dei container siano scansionate con strumenti (GitLeaks, TruffleHog o detect-secrets) che bloccano le build contenenti chiavi API, password o certificati.                                       |    2    |  D/V  |
| 4.4.5 | Verificare che l'accesso ai segreti di produzione richieda l'MFA con token hardware (YubiKey, FIDO2) e sia registrato da log di audit immutabili con identità utente e timestamp.                                           |    2    |  D/V  |
| 4.4.6 | Verificare che i segreti vengano iniettati tramite segreti di Kubernetes, volumi montati o container di inizializzazione e assicurarsi che i segreti non siano mai incorporati nelle variabili d'ambiente o nelle immagini. |    2    |  D/V  |

---

## C4.5 Sandboxing e Validazione del Carico di Lavoro AI

Isolare i modelli di intelligenza artificiale non fidati in sandbox sicure con un'analisi comportamentale completa.

|   #   | Descrizione                                                                                                                                                                                                       | Livello | Ruolo |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.5.1 | Verificare che i modelli di AI esterni vengano eseguiti in gVisor, microVM (come Firecracker, CrossVM) o container Docker con le opzioni --security-opt=no-new-privileges e --read-only.                          |    1    |  D/V  |
| 4.5.2 | Verificare che gli ambienti sandbox non abbiano connettività di rete (--network=none) oppure che abbiano accesso solo a localhost con tutte le richieste esterne bloccate dalle regole iptables.                  |    1    |  D/V  |
| 4.5.3 | Verificare che la convalida del modello AI includa test di red-team automatizzati con copertura di test definita dall'organizzazione e analisi comportamentale per il rilevamento di backdoor.                    |    2    |  D/V  |
| 4.5.4 | Verificare che, prima che un modello di IA venga promosso in produzione, i risultati nel sandbox siano firmati crittograficamente dal personale di sicurezza autorizzato e archiviati in log di audit immutabili. |    2    |  D/V  |
| 4.5.5 | Verificare che gli ambienti sandbox vengano distrutti e ricreati dalle immagini di riferimento tra le valutazioni con una completa pulizia del filesystem e della memoria.                                        |    2    |  D/V  |

---

## C4.6 Monitoraggio della Sicurezza dell'Infrastruttura

Scansiona e monitora continuamente l'infrastruttura con risoluzione automatica e allerta in tempo reale.

|   #   | Descrizione                                                                                                                                                                                                           | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.6.1 | Verificare che le immagini dei container siano scansionate secondo i programmi organizzativi, con le vulnerabilità CRITICHE che bloccano la distribuzione in base alle soglie di rischio organizzative.               |    1    |  D/V  |
| 4.6.2 | Verificare che l'infrastruttura rispetti i CIS Benchmarks o i controlli NIST 800-53 con soglie di conformità definite dall'organizzazione e con la rimedio automatico per i controlli non superati.                   |    1    |  D/V  |
| 4.6.3 | Verificare che le vulnerabilità di gravità ALTA siano corrette secondo le tempistiche di gestione del rischio organizzativo con procedure di emergenza per le CVE attivamente sfruttate.                              |    2    |  D/V  |
| 4.6.4 | Verificare che gli avvisi di sicurezza si integrino con le piattaforme SIEM (Splunk, Elastic o Sentinel) utilizzando i formati CEF o STIX/TAXII con arricchimento automatizzato.                                      |    2    |   V   |
| 4.6.5 | Verificare che le metriche dell'infrastruttura siano esportate ai sistemi di monitoraggio (Prometheus, DataDog) con dashboard SLA e reportistica esecutiva.                                                           |    3    |   V   |
| 4.6.6 | Verificare che la deriva della configurazione venga rilevata utilizzando strumenti (Chef InSpec, AWS Config) secondo i requisiti di monitoraggio organizzativo con rollback automatico per modifiche non autorizzate. |    2    |  D/V  |

---

## Gestione delle Risorse dell'Infrastruttura AI C4.7

Prevenire gli attacchi di esaurimento delle risorse e garantire un'allocazione equa delle risorse tramite quote e monitoraggio.

|   #   | Descrizione                                                                                                                                                                                                                                                         | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.7.1 | Verificare che l'utilizzo di GPU/TPU sia monitorato con avvisi attivati a soglie definite dall'organizzazione e che venga attivato il ridimensionamento automatico o il bilanciamento del carico in base alle politiche di gestione della capacità.                 |    1    |  D/V  |
| 4.7.2 | Verificare che le metriche del carico di lavoro AI (latenza di inferenza, throughput, tassi di errore) siano raccolte in conformità ai requisiti di monitoraggio dell’organizzazione e correlate con l’utilizzo dell’infrastruttura.                                |    1    |  D/V  |
| 4.7.3 | Verificare che i ResourceQuota di Kubernetes o equivalenti limitino i singoli carichi di lavoro secondo le politiche di allocazione delle risorse dell'organizzazione con limiti rigidi applicati.                                                                  |    2    |  D/V  |
| 4.7.4 | Verificare che il monitoraggio dei costi tenga traccia della spesa per carico di lavoro/tenant con avvisi basati sulle soglie di budget organizzativo e controlli automatizzati per il superamento del budget.                                                      |    2    |   V   |
| 4.7.5 | Verificare che la pianificazione della capacità utilizzi dati storici con periodi di previsione definiti dall'organizzazione e provisioning automatico delle risorse basato sui modelli di domanda.                                                                 |    3    |   V   |
| 4.7.6 | Verificare che l'esaurimento delle risorse attivi gli interruttori automatici (circuit breakers) secondo i requisiti di risposta dell'organizzazione, inclusi il limitazione della velocità basata sulle politiche di capacità e l'isolamento del carico di lavoro. |    2    |  D/V  |

---

## C4.8 Controlli per la Separazione degli Ambienti e la Promozione

Imporre rigidi confini ambientali con cancelli di promozione automatizzati e validazione della sicurezza.

|   #   | Descrizione                                                                                                                                                                                                            | Livello | Ruolo |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.8.1 | Verificare che gli ambienti dev/test/prod operino in VPC/VNet separati senza ruoli IAM, gruppi di sicurezza o connettività di rete condivisi.                                                                          |    1    |  D/V  |
| 4.8.2 | Verificare che la promozione dell’ambiente richieda l’approvazione da parte del personale autorizzato definito a livello organizzativo, con firme crittografiche e registri di controllo immutabili.                   |    1    |  D/V  |
| 4.8.3 | Verificare che gli ambienti di produzione blocchino l'accesso SSH, disabilitino gli endpoint di debug e richiedano richieste di modifica con requisiti di preavviso organizzativo, ad eccezione delle emergenze.       |    2    |  D/V  |
| 4.8.4 | Verificare che le modifiche all'infrastruttura come codice richiedano una revisione tra pari con test automatizzati e scansione di sicurezza prima della fusione nel ramo principale.                                  |    2    |  D/V  |
| 4.8.5 | Verificare che i dati non di produzione siano anonimizzati secondo i requisiti di privacy dell'organizzazione, con generazione di dati sintetici o mascheramento completo dei dati con rimozione delle PII verificata. |    2    |  D/V  |
| 4.8.6 | Verificare che i gate di promozione includano test di sicurezza automatizzati (SAST, DAST, scansione dei container) con zero risultati CRITICI richiesti per l'approvazione.                                           |    2    |  D/V  |

---

## Backup e ripristino dell'infrastruttura C4.9

Garantire la resilienza dell'infrastruttura tramite backup automatizzati, procedure di recupero testate e capacità di ripristino in caso di disastro.

|   #   | Descrizione                                                                                                                                                                                                              | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 4.9.1 | Verificare che le configurazioni dell'infrastruttura siano sottoposte a backup secondo i programmi di backup organizzativi verso regioni geograficamente separate con l'implementazione della strategia di backup 3-2-1. |    1    |  D/V  |
| 4.9.2 | Verificare che i sistemi di backup funzionino in reti isolate con credenziali separate e archiviazione air-gapped per la protezione contro il ransomware.                                                                |    2    |  D/V  |
| 4.9.3 | Verificare che le procedure di ripristino siano testate e validate tramite test automatizzati secondo i programmi organizzativi, con obiettivi di RTO e RPO che soddisfano i requisiti dell'organizzazione.              |    2    |   V   |
| 4.9.4 | Verificare che il disaster recovery includa runbook specifici per l’IA con il ripristino dei pesi del modello, la ricostruzione del cluster GPU e la mappatura delle dipendenze di servizio.                             |    3    |   V   |

---

## C4.10 Conformità e Governance dell'Infrastruttura

Garantire la conformità normativa attraverso una valutazione continua, la documentazione e controlli automatizzati.

|   #    | Descrizione                                                                                                                                                                                                   | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.10.1 | Verificare che la conformità dell'infrastruttura sia valutata secondo i programmi organizzativi rispetto ai controlli SOC 2, ISO 27001 o FedRAMP con la raccolta automatizzata delle evidenze.                |    2    |  D/V  |
| 4.10.2 | Verificare che la documentazione dell'infrastruttura includa diagrammi di rete, mappe di flusso dei dati e modelli di minacce aggiornati secondo i requisiti della gestione del cambiamento organizzativo.    |    2    |   V   |
| 4.10.3 | Verificare che le modifiche all'infrastruttura vengano sottoposte a una valutazione automatizzata dell'impatto sulla conformità con flussi di lavoro di approvazione normativa per modifiche ad alto rischio. |    3    |  D/V  |

---

## C4.11 Sicurezza dell'Hardware per l'IA

Proteggere i componenti hardware specifici per l'IA, inclusi GPU, TPU e acceleratori AI specializzati.

|   #    | Descrizione                                                                                                                                                                                              | Livello | Ruolo |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.11.1 | Verificare che il firmware dell'acceleratore AI (BIOS GPU, firmware TPU) sia verificato con firme crittografiche e aggiornato secondo le tempistiche di gestione delle patch dell'organizzazione.        |    2    |  D/V  |
| 4.11.2 | Verificare che, prima dell'esecuzione del carico di lavoro, l'integrità dell'acceleratore AI sia validata mediante attestazione hardware utilizzando TPM 2.0, Intel TXT o AMD SVM.                       |    2    |  D/V  |
| 4.11.3 | Verificare che la memoria GPU sia isolata tra i carichi di lavoro utilizzando SR-IOV, MIG (Multi-Instance GPU) o un partizionamento hardware equivalente con sanificazione della memoria tra i processi. |    2    |  D/V  |
| 4.11.4 | Verificare che la catena di fornitura dell'hardware AI includa la verifica della provenienza con certificati del produttore e la convalida dell'imballaggio a prova di manomissione.                     |    3    |   V   |
| 4.11.5 | Verificare che i moduli di sicurezza hardware (HSM) proteggano i pesi del modello AI e le chiavi crittografiche con certificazione FIPS 140-2 Livello 3 o Common Criteria EAL4+.                         |    3    |  D/V  |

---

## C4.12 Infrastruttura AI Edge e Distribuita

Distribuzioni AI distribuite sicure, inclusi edge computing, apprendimento federato e architetture multi-sito.

|   #    | Descrizione                                                                                                                                                                                                   | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.12.1 | Verificare che i dispositivi edge AI si autentichino all'infrastruttura centrale utilizzando mutual TLS con certificati di dispositivo ruotati secondo la politica organizzativa di gestione dei certificati. |    2    |  D/V  |
| 4.12.2 | Verificare che i dispositivi edge implementino il secure boot con firme verificate e protezione rollback per prevenire attacchi di downgrade del firmware.                                                    |    2    |  D/V  |
| 4.12.3 | Verificare che il coordinamento dell'intelligenza artificiale distribuita utilizzi algoritmi di consenso tolleranti ai guasti bizantini con validazione dei partecipanti e rilevamento di nodi malevoli.      |    3    |  D/V  |
| 4.12.4 | Verificare che la comunicazione edge-to-cloud includa il controllo della larghezza di banda, la compressione dei dati e le capacità di funzionamento offline con archiviazione locale sicura.                 |    3    |  D/V  |

---

## C4.13 Sicurezza dell'Infrastruttura Multi-Cloud e Ibrida

Proteggi i carichi di lavoro AI in modo sicuro attraverso più provider cloud e implementazioni ibride cloud-on-premises.

|   #    | Descrizione                                                                                                                                                                                                 | Livello | Ruolo |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.13.1 | Verificare che le distribuzioni AI multi-cloud utilizzino la federazione di identità cloud-agnostica (OIDC, SAML) con una gestione centralizzata delle policy tra i provider.                               |    2    |  D/V  |
| 4.13.2 | Verificare che il trasferimento di dati tra cloud utilizzi la crittografia end-to-end con chiavi gestite dal cliente e che i controlli sulla residenza dei dati siano applicati in base alla giurisdizione. |    2    |  D/V  |
| 4.13.3 | Verificare che i workload di AI in cloud ibrido implementino politiche di sicurezza consistenti tra ambienti on-premise e cloud con monitoraggio e allerta unificati.                                       |    2    |  D/V  |
| 4.13.4 | Verificare che la prevenzione del lock-in del fornitore cloud includa un'infrastruttura-as-code portatile, API standardizzate e capacità di esportazione dei dati con strumenti di conversione dei formati. |    3    |   V   |
| 4.13.5 | Verificare che l'ottimizzazione dei costi multi-cloud includa controlli di sicurezza per prevenire la proliferazione delle risorse e le spese non autorizzate per il trasferimento di dati tra cloud.       |    3    |   V   |

---

## C4.14 Automazione dell'Infrastruttura e Sicurezza GitOps

Automatizzare in modo sicuro le pipeline di infrastruttura e i flussi di lavoro GitOps per la gestione dell'infrastruttura AI.

|   #    | Descrizione                                                                                                                                                                                                                 | Livello | Ruolo |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.14.1 | Verificare che i repository GitOps richiedano commit firmati con chiavi GPG e regole di protezione dei rami che impediscano push diretti ai rami principali.                                                                |    2    |  D/V  |
| 4.14.2 | Verificare che l'automazione dell'infrastruttura includa il rilevamento delle derivate con capacità di rimedio automatico e rollback attivate in base ai requisiti di risposta organizzativa per modifiche non autorizzate. |    2    |  D/V  |
| 4.14.3 | Verificare che la fornitura automatizzata dell'infrastruttura includa la convalida della politica di sicurezza con il blocco della distribuzione per configurazioni non conformi.                                           |    2    |  D/V  |
| 4.14.4 | Verificare che i segreti dell'automazione dell'infrastruttura siano gestiti tramite operatori di segreti esterni (External Secrets Operator, Bank-Vaults) con rotazione automatica.                                         |    2    |  D/V  |
| 4.14.5 | Verificare che l'infrastruttura self-healing includa la correlazione degli eventi di sicurezza con la risposta automatizzata agli incidenti e i flussi di lavoro per la notifica agli stakeholder.                          |    3    |   V   |

---

## C4.15 Sicurezza dell'Infrastruttura Resistente alla Quantum

Preparare l'infrastruttura di intelligenza artificiale per le minacce del calcolo quantistico tramite crittografia post-quantistica e protocolli sicuri contro il quantum.

|   #    | Descrizione                                                                                                                                                                                             | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.15.1 | Verificare che l'infrastruttura AI implementi algoritmi crittografici post-quantistici approvati dal NIST (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) per lo scambio di chiavi e le firme digitali.  |    3    |  D/V  |
| 4.15.2 | Verificare che i sistemi di distribuzione di chiavi quantistiche (QKD) siano implementati per comunicazioni AI ad alta sicurezza con protocolli di gestione delle chiavi quantisticamente sicuri.       |    3    |  D/V  |
| 4.15.3 | Verificare che i framework di agilità crittografica consentano una migrazione rapida a nuovi algoritmi post-quantistici con la rotazione automatica di certificati e chiavi.                            |    3    |  D/V  |
| 4.15.4 | Verificare che la modellazione delle minacce quantistiche valuti la vulnerabilità dell'infrastruttura AI agli attacchi quantistici con tempistiche di migrazione documentate e valutazioni del rischio. |    3    |   V   |
| 4.15.5 | Verificare che i sistemi crittografici ibridi classico-quantistici offrano una difesa approfondita durante il periodo di transizione quantistica con il monitoraggio delle prestazioni.                 |    3    |  D/V  |

---

## C4.16 Calcolo Confidenziale e Enclavi Sicure

Proteggi i carichi di lavoro AI e i pesi del modello utilizzando ambienti di esecuzione attendibili basati su hardware e tecnologie di calcolo confidenziale.

|   #    | Descrizione                                                                                                                                                                                         | Livello | Ruolo |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.16.1 | Verificare che i modelli di intelligenza artificiale sensibili vengano eseguiti all'interno di enclave Intel SGX, AMD SEV-SNP o ARM TrustZone con memoria crittografata e verifica di attestazione. |    3    |  D/V  |
| 4.16.2 | Verificare che i container riservati (Kata Containers, gVisor con computing riservato) isolino i carichi di lavoro AI con crittografia della memoria applicata a livello hardware.                  |    3    |  D/V  |
| 4.16.3 | Verificare che l'attestazione remota convalidi l'integrità dell'enclave prima di caricare i modelli di IA con una prova crittografica dell'autenticità dell'ambiente di esecuzione.                 |    3    |  D/V  |
| 4.16.4 | Verificare che i servizi di inferenza AI riservati prevengano l'estrazione del modello tramite calcolo crittografato con pesi del modello sigillati ed esecuzione protetta.                         |    3    |  D/V  |
| 4.16.5 | Verificare che l'orchestrazione dell'ambiente di esecuzione attendibile gestisca il ciclo di vita dell'enclave sicura con attestazione remota e canali di comunicazione crittografati.              |    3    |  D/V  |
| 4.16.6 | Verificare che il calcolo sicuro multi-parte (SMPC) consenta l'addestramento collaborativo dell'IA senza esporre i singoli set di dati o i parametri del modello.                                   |    3    |  D/V  |

---

## C4.17 Infrastruttura a Conoscenza Zero

Implementare sistemi di prova a conoscenza zero per la verifica e l'autenticazione dell'IA preservando la privacy senza rivelare informazioni sensibili.

|   #    | Descrizione                                                                                                                                                                                                  | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 4.17.1 | Verificare che le zero-knowledge proofs (ZK-SNARKs, ZK-STARKs) confermino l'integrità del modello AI e la provenienza dell'addestramento senza esporre i pesi del modello o i dati di addestramento.         |    3    |  D/V  |
| 4.17.2 | Verificare che i sistemi di autenticazione basati su ZK consentano la verifica dell'utente preservando la privacy per i servizi di intelligenza artificiale senza rivelare informazioni legate all'identità. |    3    |  D/V  |
| 4.17.3 | Verificare che i protocolli di intersezione di insiemi privati (PSI) consentano un confronto sicuro dei dati per l'AI federata senza esporre i dataset individuali.                                          |    3    |  D/V  |
| 4.17.4 | Verificare che i sistemi di machine learning a conoscenza zero (ZKML) consentano inferenze AI verificabili con una prova crittografica della correttezza del calcolo.                                        |    3    |  D/V  |
| 4.17.5 | Verificare che gli ZK-rollup offrano un'elaborazione delle transazioni AI scalabile e rispettosa della privacy con verifica batch e riduzione del carico computazionale.                                     |    3    |  D/V  |

---

## C4.18 Prevenzione degli attacchi di canalizzazione laterale

Proteggi l'infrastruttura AI da attacchi side-channel basati su temporizzazione, potenza, elettromagnetismo e cache che potrebbero divulgare informazioni sensibili.

|   #    | Descrizione                                                                                                                                                                                        | Livello | Ruolo |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.18.1 | Verificare che il tempo di inferenza dell'IA sia normalizzato utilizzando algoritmi a tempo costante e padding per prevenire attacchi di estrazione del modello basati sul tempo.                  |    3    |  D/V  |
| 4.18.2 | Verificare che la protezione contro l'analisi della potenza includa l'iniezione di rumore, il filtraggio della linea di alimentazione e schemi di esecuzione randomizzati per l'hardware AI.       |    3    |  D/V  |
| 4.18.3 | Verificare che la mitigazione dei canali laterali basati sulla cache utilizzi la partizione della cache, la randomizzazione e le istruzioni di flush per prevenire la fuoriuscita di informazioni. |    3    |  D/V  |
| 4.18.4 | Verificare che la protezione contro le emanazioni elettromagnetiche includa schermatura, filtraggio del segnale e elaborazione casualizzata per prevenire attacchi di tipo TEMPEST.                |    3    |  D/V  |
| 4.18.5 | Verificare che le difese contro i canali laterali microarchitetturali includano controlli sull'esecuzione speculativa e l'offuscamento dei modelli di accesso alla memoria.                        |    3    |  D/V  |

---

## C4.19 Sicurezza dell'Hardware Neuromorfico e AI Specializzato

Proteggere le architetture hardware emergenti dell'IA, inclusi chip neuromorfici, FPGA, ASIC personalizzati e sistemi di calcolo ottico.

|   #    | Descrizione                                                                                                                                                                                         | Livello | Ruolo |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.19.1 | Verificare che la sicurezza del chip neuromorfico includa la crittografia dei modelli di spike, la protezione del peso sinaptico e la convalida basata sull'hardware delle regole di apprendimento. |    3    |  D/V  |
| 4.19.2 | Verificare che gli accelerator AI basati su FPGA implementino la crittografia del bitstream, meccanismi anti-manomissione e caricamento sicuro della configurazione con aggiornamenti autenticati.  |    3    |  D/V  |
| 4.19.3 | Verificare che la sicurezza ASIC personalizzata includa processori di sicurezza on-chip, root of trust hardware e archiviazione sicura delle chiavi con rilevamento delle manomissioni.             |    3    |  D/V  |
| 4.19.4 | Verificare che i sistemi di calcolo ottico implementino crittografia ottica quantisticamente sicura, commutazione fotonica sicura e elaborazione dei segnali ottici protetta.                       |    3    |  D/V  |
| 4.19.5 | Verificare che i chip AI ibridi analogico-digitali includano computazione analogica sicura, memorizzazione protetta dei pesi e conversione da analogico a digitale autenticata.                     |    3    |  D/V  |

---

## C4.20 Infrastruttura di Calcolo per la Privacy

Implementare controlli infrastrutturali per il calcolo che preserva la privacy al fine di proteggere i dati sensibili durante l'elaborazione e l'analisi AI.

|   #    | Descrizione                                                                                                                                                                                                         | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.20.1 | Verificare che l'infrastruttura di crittografia omomorfica consenta il calcolo crittografato su carichi di lavoro AI sensibili con verifica dell'integrità crittografica e monitoraggio delle prestazioni.          |    3    |  D/V  |
| 4.20.2 | Verificare che i sistemi di recupero di informazioni private permettano interrogazioni al database senza rivelare i modelli di query tramite la protezione crittografica dei modelli di accesso.                    |    3    |  D/V  |
| 4.20.3 | Verificare che i protocolli di computazione multipartita sicura consentano inferenze AI preservanti la privacy senza esporre input individuali o computazioni intermedie.                                           |    3    |  D/V  |
| 4.20.4 | Verificare che la gestione delle chiavi che preserva la privacy includa la generazione distribuita delle chiavi, la crittografia a soglia e la rotazione sicura delle chiavi con protezione supportata da hardware. |    3    |  D/V  |
| 4.20.5 | Verificare che le prestazioni del calcolo in modalità privacy-preserving siano ottimizzate tramite batching, caching e accelerazione hardware, mantenendo al contempo le garanzie di sicurezza crittografica.       |    3    |  D/V  |

---

## C4.15 Sicurezza dell'integrazione cloud e distribuzione ibrida del framework agenti

Controlli di sicurezza per framework agenti integrati nel cloud con architetture ibride on-premises/cloud.

|   #    | Descrizione                                                                                                                                                | Livello | Ruolo |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.15.1 | Verificare che l'integrazione dello storage cloud utilizzi la crittografia end-to-end con gestione delle chiavi controllata dall'agente.                   |    1    |  D/V  |
| 4.15.2 | Verificare che i confini di sicurezza del deployment ibrido siano chiaramente definiti con canali di comunicazione criptati.                               |    2    |  D/V  |
| 4.15.3 | Verificare che l'accesso alle risorse cloud includa la verifica zero-trust con autenticazione continua.                                                    |    2    |  D/V  |
| 4.15.4 | Verificare che i requisiti di residenza dei dati siano applicati mediante attestazione crittografica delle posizioni di archiviazione.                     |    3    |  D/V  |
| 4.15.5 | Verificare che le valutazioni di sicurezza del provider cloud includano la modellazione delle minacce specifica per l’agente e la valutazione del rischio. |    3    |  D/V  |

---

## Riferimenti

* [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework)
* [CIS Controls v8](https://www.cisecurity.org/controls/v8)
* [OWASP Container Security Verification Standard](https://github.com/OWASP/Container-Security-Verification-Standard)
* [Kubernetes Security Best Practices](https://kubernetes.io/docs/concepts/security/)
* [SLSA Supply Chain Security Framework](https://slsa.dev/)
* [NIST SP 800-190: Application Container Security Guide](https://csrc.nist.gov/publications/detail/sp/800-190/final)
* [Cloud Security Alliance: Cloud Controls Matrix](https://cloudsecurityalliance.org/research/cloud-controls-matrix/)
* [ENISA: Secure Infrastructure Design](https://www.enisa.europa.eu/topics/critical-information-infrastructures-and-services)
* [NIST SP 800-53: Security Controls for Federal Information Systems](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final)
* [ISO 27001:2022 Information Security Management](https://www.iso.org/standard/27001)
* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [CIS Kubernetes Benchmark](https://www.cisecurity.org/benchmark/kubernetes)
* [FIPS 140-2 Security Requirements](https://csrc.nist.gov/publications/detail/fips/140/2/final)
* [NIST SP 800-207: Zero Trust Architecture](https://csrc.nist.gov/publications/detail/sp/800-207/final)
* [IEEE 2857: Privacy Engineering for AI Systems](https://standards.ieee.org/ieee/2857/7273/)
* [NIST SP 800-161: Cybersecurity Supply Chain Risk Management](https://csrc.nist.gov/publications/detail/sp/800-161/rev-1/final)
* [NIST Post-Quantum Cryptography Standards](https://csrc.nist.gov/Projects/post-quantum-cryptography)
* [Intel SGX Developer Guide](https://www.intel.com/content/www/us/en/developer/tools/software-guard-extensions/overview.html)
* [AMD SEV-SNP White Paper](https://www.amd.com/system/files/TechDocs/SEV-SNP-strengthening-vm-isolation-with-integrity-protection-and-more.pdf)
* [ARM TrustZone Technology](https://developer.arm.com/ip-products/security-ip/trustzone)
* [ZK-SNARKs: A Gentle Introduction](https://blog.ethereum.org/2016/12/05/zksnarks-in-a-nutshell/)
* [NIST SP 800-57: Cryptographic Key Management](https://csrc.nist.gov/publications/detail/sp/800-57-part-1/rev-5/final)
* [Side-Channel Attack Countermeasures](https://link.springer.com/book/10.1007/978-3-319-75268-6)
* [Neuromorphic Computing Security Challenges](https://ieeexplore.ieee.org/document/9458103)
* [FPGA Security: Fundamentals, Evaluation, and Countermeasures](https://link.springer.com/book/10.1007/978-3-319-90385-9)
* [Microsoft SEAL: Homomorphic Encryption Library](https://github.com/Microsoft/SEAL)
* [HElib: Homomorphic Encryption Library](https://github.com/homenc/HElib)
* [PALISADE Lattice Cryptography Library](https://palisade-crypto.org/)
* [Differential Privacy: A Survey of Results](https://link.springer.com/chapter/10.1007/978-3-540-79228-4_1)
* [Secure Aggregation for Federated Learning](https://eprint.iacr.org/2017/281.pdf)
* [Private Information Retrieval: Concepts and Constructions](https://link.springer.com/book/10.1007/978-3-030-16234-8)

