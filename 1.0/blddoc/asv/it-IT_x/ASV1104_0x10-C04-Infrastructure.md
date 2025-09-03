# C4 Sicurezza dell'infrastruttura, configurazione e dispiegamento

## Obiettivo di controllo

L'infrastruttura di IA deve essere messa in sicurezza contro l'elevazione dei privilegi, la manomissione della catena di fornitura e i movimenti laterali, tramite una configurazione sicura, isolamento in tempo di esecuzione, pipeline di distribuzione affidabili e monitoraggio esaustivo.

Solo componenti e configurazioni di infrastruttura autorizzati e convalidate raggiungono la produzione tramite processi controllati che mantengono la sicurezza, l'integrità e l'auditabilità.

Obiettivo di sicurezza principale: Solo componenti infrastrutturali firmati digitalmente e sottoposti a scansione delle vulnerabilità raggiungono l'ambiente di produzione attraverso pipeline di convalida automatizzate che fanno rispettare le politiche di sicurezza e mantengono tracce di audit immutabili.

---

## C4.1 Isolamento dell'ambiente di esecuzione

Prevenire l'evasione dai contenitori e l'aumento dei privilegi mediante meccanismi di isolamento a livello del kernel e controlli di accesso obbligatori.

|   #   | Descrizione                                                                                                                                                                                                                                                     | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.1.1 | Verifica che tutti i contenitori di IA rimuovano tutte le capacità Linux, ad eccezione di CAP_SETUID, CAP_SETGID e delle capacità esplicitamente richieste documentate nelle baseline di sicurezza.                                                             |    1    |  D/V  |
| 4.1.2 | Verifica che i profili seccomp blocchino tutte le chiamate di sistema, ad eccezione di quelle presenti nelle liste bianche già approvate, con violazioni che terminano il contenitore e generano avvisi di sicurezza.                                           |    1    |  D/V  |
| 4.1.3 | Verifica che i carichi di lavoro di IA funzionino con root del filesystem in sola lettura, tmpfs per dati temporanei e volumi nominati per dati persistenti, con opzioni di montaggio noexec imposte.                                                           |    2    |  D/V  |
| 4.1.4 | Verificare che il monitoraggio in tempo di esecuzione basato su eBPF (Falco, Tetragon o equivalente) rilevi tentativi di elevazione dei privilegi e termini automaticamente i processi non autorizzati entro i tempi di risposta stabiliti dall'organizzazione. |    2    |  D/V  |
| 4.1.5 | Verificare che i carichi di lavoro IA ad alto rischio vengano eseguiti in ambienti hardware-isolati (Intel TXT, AMD SVM o nodi bare-metal dedicati) con verifica di attestazione.                                                                               |    3    |  D/V  |

---

## C4.2 Pipelines di build e deployment sicure

Garantire l'integrità crittografica e la sicurezza della catena di fornitura attraverso build riproducibili e artefatti firmati.

|   #   | Descrizione                                                                                                                                                                                                              | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 4.2.1 | Verifica che l'infrastruttura come codice (IaC) venga scansionata con strumenti (tfsec, Checkov o Terrascan) ad ogni commit, bloccando le fusioni con riscontri di gravità CRITICAL o HIGH.                              |    1    |  D/V  |
| 4.2.2 | Verifica che i build dei contenitori siano riproducibili con hash SHA256 identici tra i build e genera attestazioni di provenienza SLSA Livello 3 firmate con Sigstore.                                                  |    1    |  D/V  |
| 4.2.3 | Verifica che le immagini container includano SBOM CycloneDX o SPDX e siano firmate con Cosign prima del push nel registro, e che le immagini non firmate vengano rifiutate al deployment.                                |    2    |  D/V  |
| 4.2.4 | Verifica che le pipeline CI/CD utilizzino token OIDC provenienti da HashiCorp Vault, AWS IAM Roles o Azure Managed Identity, con durate non superiori ai limiti della politica di sicurezza dell'organizzazione.         |    2    |  D/V  |
| 4.2.5 | Verificare che le firme Cosign e la provenienza SLSA siano verificate durante il processo di distribuzione prima dell'esecuzione del contenitore e che gli errori di verifica causino il fallimento della distribuzione. |    2    |  D/V  |
| 4.2.6 | Verifica che gli ambienti di build funzionino in contenitori effimeri o in macchine virtuali senza archiviazione persistente e con isolamento di rete dalle VPC di produzione.                                           |    2    |  D/V  |

---

## C4.3 Sicurezza di rete e controllo degli accessi

Implementa una rete zero-trust con politiche di negazione predefinite e comunicazioni criptate.

|   #   | Descrizione                                                                                                                                                                                          | Livello | Ruolo |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.3.1 | Verifica che Kubernetes NetworkPolicies o equivalenti implementino un rifiuto predefinito per ingresso e uscita, con regole esplicite di permesso per le porte richieste (443, 8080, ecc.).          |    1    |  D/V  |
| 4.3.2 | Verifichi che SSH (porta 22), RDP (porta 3389) e gli endpoint di metadati nel cloud (169.254.169.254) siano bloccati o richiedano un'autenticazione basata su certificato.                           |    1    |  D/V  |
| 4.3.3 | Verificare che il traffico in uscita sia filtrato tramite proxy HTTP/HTTPS (Squid, Istio o gateway NAT nel cloud) con liste bianche dei domini e che le richieste bloccate vengano registrate.       |    2    |  D/V  |
| 4.3.4 | Verifica che la comunicazione tra i servizi utilizzi TLS mutuo con certificati ruotati secondo la politica organizzativa e che la validazione dei certificati sia attiva (nessuna flag skip-verify). |    2    |  D/V  |
| 4.3.5 | Verifica che l'infrastruttura di IA operi in VPCs e VNets dedicati, con nessun accesso diretto a Internet, e comunichi esclusivamente tramite gateway NAT o host bastione.                           |    2    |  D/V  |

---

## C4.4 Segreti e Gestione delle Chiavi Crittografiche

Proteggi le credenziali tramite archiviazione basata su hardware e rotazione automatizzata delle credenziali con accesso zero-trust.

|   #   | Descrizione                                                                                                                                                                                                                   | Livello | Ruolo |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.4.1 | Verifica che i segreti siano archiviati in HashiCorp Vault, AWS Secrets Manager, Azure Key Vault o Google Secret Manager con cifratura a riposo tramite AES-256.                                                              |    1    |  D/V  |
| 4.4.2 | Verificare che le chiavi crittografiche siano generate in HSM FIPS 140-2 Livello 2 (AWS CloudHSM, Azure Dedicated HSM) con rotazione delle chiavi secondo la politica crittografica aziendale.                                |    1    |  D/V  |
| 4.4.3 | Verifica che la rotazione dei segreti sia automatizzata con distribuzione senza tempi di inattività e che la rotazione sia immediata, attivata da cambiamenti del personale o incidenti di sicurezza.                         |    2    |  D/V  |
| 4.4.4 | Verifica che le immagini dei contenitori siano sottoposte a scansione con strumenti (GitLeaks, TruffleHog o detect-secrets) che blocchino le build contenenti chiavi API, password o certificati.                             |    2    |  D/V  |
| 4.4.5 | Verificare che l'accesso ai segreti di produzione richieda MFA con token hardware (YubiKey, FIDO2) e sia registrato in log di audit immutabili che includano l'identità dell'utente e la data e ora.                          |    2    |  D/V  |
| 4.4.6 | Verifichi che i segreti siano iniettati tramite i segreti di Kubernetes, volumi montati o contenitori di inizializzazione, e si assicuri che i segreti non siano mai incorporati nelle variabili d'ambiente o nelle immagini. |    2    |  D/V  |

---

## C4.5 IA sandboxing dei carichi di lavoro e validazione

Isolare i modelli di IA non affidabili in sandbox sicuri con un'analisi comportamentale completa.

|   #   | Descrizione                                                                                                                                                                                                         | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.5.1 | Verifica che i modelli AI esterni vengano eseguiti in gVisor, microVM (come Firecracker, CrossVM) o contenitori Docker con le opzioni --security-opt=no-new-privileges e --read-only.                               |    1    |  D/V  |
| 4.5.2 | Verifica che gli ambienti sandbox non abbiano alcuna connettività di rete (--network=none) o abbiano solo l'accesso a localhost, con tutte le richieste esterne bloccate dalle regole iptables.                     |    1    |  D/V  |
| 4.5.3 | Verificare che la validazione del modello di IA includa test automatizzati del Red Team con copertura di test definita dall'organizzazione e analisi comportamentale per la rilevazione di backdoor.                |    2    |  D/V  |
| 4.5.4 | Verifica che prima che un modello di IA venga promosso in produzione, i suoi risultati della sandbox siano firmati digitalmente da personale di sicurezza autorizzato e registrati in registri di audit immutabili. |    2    |  D/V  |
| 4.5.5 | Verifica che gli ambienti sandbox siano distrutti e ricreati da immagini golden tra le valutazioni, con una pulizia completa del filesystem e della memoria.                                                        |    2    |  D/V  |

---

## C4.6 Monitoraggio della sicurezza dell'infrastruttura

Scansiona e monitora continuamente l'infrastruttura con rimedi automatizzati e avvisi in tempo reale.

|   #   | Descrizione                                                                                                                                                                                                                    | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 4.6.1 | Verificare che le immagini del container vengano scansionate secondo i programmi organizzativi, con vulnerabilità CRITICHE che blocchino la distribuzione in base alle soglie di rischio organizzative.                        |    1    |  D/V  |
| 4.6.2 | Verificare che l'infrastruttura rispetti CIS Benchmarks o i controlli NIST 800-53, con soglie di conformità definite dall'organizzazione e rimedi automatizzati per le verifiche fallite.                                      |    1    |  D/V  |
| 4.6.3 | Verificare che le vulnerabilità ad alta gravità siano patchate secondo le tempistiche della gestione del rischio organizzativo, con procedure di emergenza per CVE attivamente sfruttate.                                      |    2    |  D/V  |
| 4.6.4 | Verifica che gli avvisi di sicurezza si integrino con le piattaforme SIEM (Splunk, Elastic o Sentinel) utilizzando formati CEF o STIX/TAXII con arricchimento automatico.                                                      |    2    |   V   |
| 4.6.5 | Verifica che le metriche dell'infrastruttura siano esportate nei sistemi di monitoraggio (Prometheus, DataDog) con cruscotti SLA e reporting esecutivo.                                                                        |    3    |   V   |
| 4.6.6 | Verificare che la deviazione di configurazione venga rilevata utilizzando strumenti (Chef InSpec, AWS Config) in base ai requisiti di monitoraggio dell'organizzazione, con rollback automatico per modifiche non autorizzate. |    2    |  D/V  |

---

## C4.7 Gestione delle risorse dell'infrastruttura di IA

Prevenire gli attacchi di esaurimento delle risorse e garantire una ripartizione equa delle risorse tramite quote e monitoraggio.

|   #   | Descrizione                                                                                                                                                                                                                                                               | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.7.1 | Verifica che l'utilizzo di GPU/TPU sia monitorato con allarmi attivati a soglie definite dall'organizzazione e che il ridimensionamento automatico o il bilanciamento del carico siano attivati in base alle politiche di gestione della capacità.                        |    1    |  D/V  |
| 4.7.2 | Verifica che le metriche dei carichi di lavoro IA (latenza di inferenza, throughput, tassi di errore) siano raccolte in conformità ai requisiti di monitoraggio dell'organizzazione e siano correlate all'utilizzo dell'infrastruttura.                                   |    1    |  D/V  |
| 4.7.3 | Verificare che le ResourceQuotas di Kubernetes o equivalenti limitino i carichi di lavoro individuali in base alle politiche di allocazione delle risorse dell'organizzazione, con limiti rigidi applicati.                                                               |    2    |  D/V  |
| 4.7.4 | Verificare che il monitoraggio dei costi tracci la spesa per carico di lavoro/tenant con avvisi basati sulle soglie di budget organizzativo e controlli automatizzati per i superamenti del budget.                                                                       |    2    |   V   |
| 4.7.5 | Verifica che la pianificazione della capacità utilizzi dati storici con periodi di previsione definiti dall'organizzazione e che l'allocazione automatizzata delle risorse sia basata sui modelli di domanda.                                                             |    3    |   V   |
| 4.7.6 | Verificare che l'esaurimento delle risorse faccia scattare gli interruttori di protezione del circuito in conformità ai requisiti di risposta dell'organizzazione, tra cui la limitazione del tasso basata su politiche di capacità e l'isolamento dei carichi di lavoro. |    2    |  D/V  |

---

## C4.8 Separazione degli ambienti e controlli di promozione

Imporre confini rigorosi tra gli ambienti con cancelli di promozione automatizzati e validazione della sicurezza.

|   #   | Descrizione                                                                                                                                                                                                        | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 4.8.1 | Verificare che gli ambienti di sviluppo, test e produzione operino in VPCs/VNets separati, senza alcuna condivisione di ruoli IAM, gruppi di sicurezza o connettività di rete.                                     |    1    |  D/V  |
| 4.8.2 | Verificare che la promozione dell'ambiente richieda l'approvazione da parte del personale autorizzato definito dall'organizzazione, con firme crittografiche e tracce di audit immutabili.                         |    1    |  D/V  |
| 4.8.3 | Verifica che gli ambienti di produzione blocchino l'accesso SSH, disabilitino gli endpoint di debug e richiedano richieste di modifica con requisiti di preavviso organizzativo, salvo le emergenze.               |    2    |  D/V  |
| 4.8.4 | Verificare che le modifiche all'infrastruttura come codice (IaC) richiedano una revisione tra pari con test automatici e scansione di sicurezza prima della fusione nel ramo principale.                           |    2    |  D/V  |
| 4.8.5 | Verificare che i dati non di produzione siano anonimizzati secondo i requisiti di privacy organizzativi, la generazione di dati sintetici o il mascheramento completo dei dati con la rimozione di PII verificata. |    2    |  D/V  |
| 4.8.6 | Verificare che i gate di promozione includano test di sicurezza automatizzati (SAST, DAST, scansione dei container) con la condizione che non vi siano vulnerabilità critiche per l'approvazione.                  |    2    |  D/V  |

---

## C4.9 Infrastruttura Backup e Ripristino

Garantire la resilienza dell'infrastruttura mediante backup automatizzati, procedure di ripristino testate e capacità di disaster recovery.

|   #   | Descrizione                                                                                                                                                                                                         | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.9.1 | Verificare che le configurazioni dell'infrastruttura siano sottoposte a backup secondo i piani di backup organizzativi, in regioni geograficamente separate, con l'implementazione della strategia di backup 3-2-1. |    1    |  D/V  |
| 4.9.2 | Verificare che i sistemi di backup operino in reti isolate con credenziali separate e archiviazione offline isolata per la protezione contro il ransomware.                                                         |    2    |  D/V  |
| 4.9.3 | Verificare che le procedure di ripristino siano testate e validate tramite test automatizzati secondo i programmi organizzativi, con obiettivi RTO e RPO che soddisfino i requisiti dell'organizzazione.            |    2    |   V   |
| 4.9.4 | Verifica che il ripristino di emergenza includa runbook specifici per IA con il ripristino dei pesi del modello, la ricostruzione del cluster GPU e la mappatura delle dipendenze dei servizi.                      |    3    |   V   |

---

## C4.10 Conformità e governance dell'infrastruttura

Mantenere la conformità normativa attraverso valutazioni continue, documentazione e controlli automatizzati.

|   #    | Descrizione                                                                                                                                                                                          | Livello | Ruolo |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.10.1 | Verificare che la conformità dell'infrastruttura sia valutata in base ai piani organizzativi rispetto ai controlli SOC 2, ISO 27001 o FedRAMP, con raccolta automatizzata delle evidenze.            |    2    |  D/V  |
| 4.10.2 | Verifica che la documentazione infrastrutturale includa diagrammi di rete, mappe di flusso dei dati e modelli di minaccia aggiornati in base ai requisiti di gestione del cambiamento organizzativo. |    2    |   V   |
| 4.10.3 | Verificare che le modifiche all'infrastruttura siano sottoposte a una valutazione automatica dell'impatto sulla conformità, con flussi di approvazione regolamentare per modifiche ad alto rischio.  |    3    |  D/V  |

---

## C4.11 Sicurezza dell'hardware dell'IA

Garantire la sicurezza dei componenti hardware specifici per l'IA, inclusi GPU, TPU e acceleratori di intelligenza artificiale specializzati.

|   #    | Descrizione                                                                                                                                                                                                     | Livello | Ruolo |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.11.1 | Verificare che il firmware dell'acceleratore AI (BIOS della GPU, firmware TPU) sia verificato con firme crittografiche e aggiornato in conformità alle tempistiche di gestione delle patch dell'organizzazione. |    2    |  D/V  |
| 4.11.2 | Verificare che, prima dell'esecuzione del carico di lavoro, l'integrità dell'acceleratore AI sia convalidata tramite attestazione hardware utilizzando TPM 2.0, Intel TXT o AMD SVM.                            |    2    |  D/V  |
| 4.11.3 | Verifica che la memoria GPU sia isolata tra i carichi di lavoro utilizzando SR-IOV, MIG (Multi-Instance GPU) o partizionamento hardware equivalente con sanificazione della memoria tra i lavori.               |    2    |  D/V  |
| 4.11.4 | Verifica che la catena di fornitura dell'hardware per l'IA includa la verifica della provenienza con certificati del produttore e la convalida dell'imballaggio a prova di manomissione.                        |    3    |   V   |
| 4.11.5 | Verifichi che i moduli di sicurezza hardware (HSM) proteggano i pesi del modello di IA e le chiavi crittografiche con certificazione FIPS 140-2 livello 3 o Common Criteria EAL4+.                              |    3    |  D/V  |

---

## C4.12 Edge & Infrastruttura IA Distribuita

Implementazioni sicure di IA distribuita, includendo edge computing, apprendimento federato e architetture multi-sito.

|   #    | Descrizione                                                                                                                                                                                                                   | Livello | Ruolo |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.12.1 | Verifica che i dispositivi edge AI si autentichino presso l'infrastruttura centrale utilizzando TLS mutuo (mTLS) con certificati dei dispositivi ruotati secondo la politica di gestione dei certificati dell'organizzazione. |    2    |  D/V  |
| 4.12.2 | Verificare che i dispositivi edge implementino l'avvio sicuro con firme verificate e protezione contro il rollback che prevenga gli attacchi di downgrade del firmware.                                                       |    2    |  D/V  |
| 4.12.3 | Verifica che il coordinamento distribuito dell'IA utilizzi algoritmi di consenso tolleranti ai fallimenti bizantini con validazione dei partecipanti e rilevamento di nodi malevoli.                                          |    3    |  D/V  |
| 4.12.4 | Verifichi che la comunicazione edge-to-cloud includa la limitazione della larghezza di banda, la compressione dei dati e le capacità di operare offline con archiviazione locale sicura.                                      |    3    |  D/V  |

---

## C4.13 Sicurezza dell'infrastruttura multi-cloud e ibrida

Proteggere i carichi di lavoro di IA tra più fornitori di cloud e implementazioni ibride cloud-on-premises.

|   #    | Descrizione                                                                                                                                                                                                 | Livello | Ruolo |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.13.1 | Verificare che le implementazioni di IA multi-cloud utilizzino una federazione di identità indipendente dal cloud (OIDC, SAML) con gestione centralizzata delle politiche tra i fornitori.                  |    2    |  D/V  |
| 4.13.2 | Verificare che il trasferimento di dati tra cloud utilizzi la crittografia end-to-end con chiavi gestite dal cliente e controlli di residenza dei dati applicati per giurisdizione.                         |    2    |  D/V  |
| 4.13.3 | Verificare che i carichi di lavoro IA nel cloud ibrido implementino politiche di sicurezza coerenti tra ambienti in locale e cloud, con monitoraggio e allerta unificati.                                   |    2    |  D/V  |
| 4.13.4 | Verifichi che la prevenzione del lock-in del fornitore cloud includa infrastruttura come codice portatile, API standardizzate e capacità di esportazione dei dati con strumenti di conversione dei formati. |    3    |   V   |
| 4.13.5 | Verifica che l'ottimizzazione dei costi multi-cloud includa controlli di sicurezza che prevengano lo spreco di risorse, nonché i costi di trasferimento dati tra i cloud non autorizzati.                   |    3    |   V   |

---

## C4.14 Automazione dell'infrastruttura e sicurezza GitOps

Pipeline di automazione dell'infrastruttura sicura e flussi di lavoro GitOps per la gestione dell'infrastruttura AI.

|   #    | Descrizione                                                                                                                                                                                                                                          | Livello | Ruolo |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.14.1 | Verifica che i repository GitOps richiedano commit firmati con chiavi GPG e regole di protezione dei rami che impediscono push diretti ai rami principali.                                                                                           |    2    |  D/V  |
| 4.14.2 | Verificare che l'automazione dell'infrastruttura includa il rilevamento delle deviazioni con intervento correttivo automatico e le capacità di rollback attivate in base ai requisiti di risposta dell'organizzazione per modifiche non autorizzate. |    2    |  D/V  |
| 4.14.3 | Verifica che l'automazione dell'approvvigionamento dell'infrastruttura includa la validazione delle policy di sicurezza con blocco della distribuzione per configurazioni non conformi.                                                              |    2    |  D/V  |
| 4.14.4 | Verifica che i segreti dell'automazione dell'infrastruttura siano gestiti tramite operatori di segreti esterni (External Secrets Operator, Bank-Vaults) con rotazione automatica.                                                                    |    2    |  D/V  |
| 4.14.5 | Verifica che l'infrastruttura auto-rigenerante includa la correlazione degli eventi di sicurezza con la risposta automatizzata agli incidenti e i flussi di lavoro di notifica ai portatori di interesse.                                            |    3    |   V   |

---

## C4.15 Sicurezza delle infrastrutture resistenti ai computer quantistici

Prepara l'infrastruttura di IA per le minacce legate al calcolo quantistico mediante crittografia post-quantum e protocolli sicuri quantistici.

|   #    | Descrizione                                                                                                                                                                                                                                       | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.15.1 | Verificare che l'infrastruttura IA implementi gli algoritmi crittografici post-quantistici approvati da NIST (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) per lo scambio di chiavi e le firme digitali.                                         |    3    |  D/V  |
| 4.15.2 | Verifica che i sistemi di distribuzione di chiavi quantistiche (QKD) siano implementati per comunicazioni ad alta sicurezza basate sull'Intelligenza Artificiale, con protocolli di gestione delle chiavi sicuri contro gli attacchi quantistici. |    3    |  D/V  |
| 4.15.3 | Verificare che i framework di agilità crittografica consentano una migrazione rapida verso nuovi algoritmi post-quantistici con rotazione automatizzata di certificati e chiavi.                                                                  |    3    |  D/V  |
| 4.15.4 | Verificare che la modellazione delle minacce quantistiche valuti la vulnerabilità dell'infrastruttura IA agli attacchi quantistici, con cronologie di migrazione documentate e valutazioni dei rischi.                                            |    3    |   V   |
| 4.15.5 | Verifica che i sistemi crittografici ibridi classico-quantistici forniscano difesa-in-profondità durante il periodo di transizione quantistica con monitoraggio delle prestazioni.                                                                |    3    |  D/V  |

---

## C4.16 Calcolo confidenziale & ambienti sicuri

Proteggere i carichi di lavoro dell'IA e i pesi del modello usando ambienti di esecuzione fidati basati su hardware e tecnologie di calcolo confidenziale.

|   #    | Descrizione                                                                                                                                                                            | Livello | Ruolo |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.16.1 | Verifichi che i modelli di IA sensibili vengano eseguiti all'interno di enclave Intel SGX, AMD SEV-SNP o ARM TrustZone, con memoria cifrata e verifica dell'attestazione.              |    3    |  D/V  |
| 4.16.2 | Verifica che i contenitori confidenziali (Kata Containers, gVisor con calcolo confidenziale) isolino i carichi di lavoro dell'IA con cifratura della memoria supportata dall'hardware. |    3    |  D/V  |
| 4.16.3 | Verifica l'integrità dell'enclave tramite attestazione remota prima di caricare i modelli di IA, fornendo una prova crittografica dell'autenticità dell'ambiente di esecuzione.        |    3    |  D/V  |
| 4.16.4 | Verifica che i servizi di inferenza AI confidenziali impediscano l'estrazione del modello mediante calcolo crittografato con pesi del modello sigillati ed esecuzione protetta.        |    3    |  D/V  |
| 4.16.5 | Verifica che l'orchestrazione dell'ambiente di esecuzione affidabile gestisca il ciclo di vita dell'enclave sicura con attestazione remota e canali di comunicazione cifrati.          |    3    |  D/V  |
| 4.16.6 | Verifica che il calcolo sicuro multiparte (SMPC) consenta un addestramento collaborativo dell'IA senza esporre i set di dati individuali o i parametri del modello.                    |    3    |  D/V  |

---

## C4.17 Infrastruttura Zero-Knowledge

Implementa sistemi di prove a conoscenza zero per la verifica e l'autenticazione dell'IA che preservano la privacy, senza rivelare informazioni sensibili.

|   #    | Descrizione                                                                                                                                                                                               | Livello | Ruolo |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.17.1 | Verifica che le prove a conoscenza nulla (ZK-SNARKs, ZK-STARKs) verifichino l'integrità del modello di IA e la provenienza dell'addestramento senza esporre i pesi del modello o i dati di addestramento. |    3    |  D/V  |
| 4.17.2 | Verifica che i sistemi di autenticazione basati su ZK consentano una verifica dell'utente che preservi la privacy nei servizi di IA senza rivelare informazioni relative all'identità.                    |    3    |  D/V  |
| 4.17.3 | Verifica che i protocolli di intersezione di insiemi privata (PSI) consentano l'abbinamento sicuro dei dati per l'IA federata senza esporre set di dati individuali.                                      |    3    |  D/V  |
| 4.17.4 | Verifica che i sistemi di apprendimento automatico a conoscenza nulla (ZKML) consentano inferenze AI verificabili con una prova crittografica della correttezza del calcolo.                              |    3    |  D/V  |
| 4.17.5 | Verifica che i rollup ZK offrano un'elaborazione scalabile delle transazioni di IA che preservi la privacy, con verifica in batch e ridotto carico computazionale.                                        |    3    |  D/V  |

---

## C4.18 Prevenzione degli attacchi a canali laterali

Proteggere l'infrastruttura IA dagli attacchi a canale laterale basati su temporizzazione, consumo di energia, elettromagnetici e cache che potrebbero rivelare informazioni sensibili.

|   #    | Descrizione                                                                                                                                                                                            | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 4.18.1 | Verifica che il tempo di inferenza dell'IA sia normalizzato utilizzando algoritmi a tempo costante e padding per prevenire attacchi di estrazione del modello basati sul tempo.                        |    3    |  D/V  |
| 4.18.2 | Verifica che la protezione contro l’analisi del consumo di potenza includa l’iniezione di rumore, il filtraggio della linea di alimentazione e schemi di esecuzione casualizzati per l’hardware di IA. |    3    |  D/V  |
| 4.18.3 | Verifica che la mitigazione basata sulla cache dei canali laterali utilizzi la partizione della cache, la randomizzazione e le istruzioni di flush per prevenire la perdita di informazioni.           |    3    |  D/V  |
| 4.18.4 | Verifica che la protezione dalle emanazioni elettromagnetiche includa schermatura elettromagnetica, filtraggio del segnale e elaborazione casualizzata per prevenire attacchi di tipo TEMPEST.         |    3    |  D/V  |
| 4.18.5 | Verifica che le difese contro i canali laterali microarchitetturali includano controlli sull'esecuzione speculativa e offuscamento dei pattern di accesso alla memoria.                                |    3    |  D/V  |

---

## C4.19 Sicurezza dell'hardware neuromorfico e specializzato per l'IA

Garantire la sicurezza delle architetture hardware emergenti per l'IA, tra cui chip neuromorfici, FPGA, ASIC personalizzati e sistemi di calcolo ottico.

|   #    | Descrizione                                                                                                                                                                                          | Livello | Ruolo |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.19.1 | Verificare che la sicurezza del chip neuromorfico includa crittografia delle sequenze di spike, protezione dei pesi sinaptici e validazione delle regole di apprendimento basate su hardware.        |    3    |  D/V  |
| 4.19.2 | Verifica che gli acceleratori di IA basati su FPGA implementino la crittografia del bitstream, meccanismi anti-manomissione e caricamento sicuro della configurazione con aggiornamenti autenticati. |    3    |  D/V  |
| 4.19.3 | Verificare che la sicurezza di un ASIC personalizzato includa processori di sicurezza on-chip, radice di fiducia hardware e memorizzazione sicura delle chiavi con rilevamento di manomissione.      |    3    |  D/V  |
| 4.19.4 | Verifica che i sistemi di calcolo ottico implementino cifratura ottica resistente ai computer quantistici, commutazione fotonica sicura e elaborazione sicura del segnale ottico.                    |    3    |  D/V  |
| 4.19.5 | Verificare che i chip AI ibridi analogico-digitali includano calcolo analogico sicuro, archiviazione protetta dei pesi e conversione analogico-digitale autenticata.                                 |    3    |  D/V  |

---

## C4.20 Infrastruttura di calcolo che preserva la privacy

Implementare controlli infrastrutturali per la computazione a tutela della privacy al fine di proteggere i dati sensibili durante l'elaborazione e l'analisi basate sull'IA.

|   #    | Descrizione                                                                                                                                                                                                                           | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.20.1 | Verificare che l'infrastruttura di crittografia omomorfica permetta l'elaborazione crittografata su carichi di lavoro sensibili di IA, con verifica dell'integrità crittografica e monitoraggio delle prestazioni.                    |    3    |  D/V  |
| 4.20.2 | Verifichi che i sistemi di recupero privato delle informazioni consentano interrogazioni al database senza rivelare gli schemi delle query mediante protezione crittografica degli schemi di accesso.                                 |    3    |  D/V  |
| 4.20.3 | Verifica che i protocolli di calcolo multiparte sicuro consentano inferenze IA che preservano la privacy senza esporre input individuali o calcoli intermedi.                                                                         |    3    |  D/V  |
| 4.20.4 | Verifica che la gestione delle chiavi orientata alla privacy includa la generazione di chiavi distribuita, la crittografia a soglia e la rotazione sicura delle chiavi con protezione basata su hardware.                             |    3    |  D/V  |
| 4.20.5 | Verifica che le prestazioni computazionali che preservano la privacy siano ottimizzate tramite l'elaborazione in batch, la memorizzazione nella cache e l'accelerazione hardware, mantenendo le garanzie di sicurezza crittografiche. |    3    |  D/V  |

---

## C4.15 Framework dell'agente Integrazione Cloud, Sicurezza e Distribuzione Ibrida

Controlli di sicurezza per framework di agenti integrati nel cloud con architetture ibride on-premises/cloud.

|   #    | Descrizione                                                                                                                                                          | Livello | Ruolo |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.15.1 | Verifica che l'integrazione dello storage cloud utilizzi la crittografia end-to-end con gestione delle chiavi controllata dall'agente.                               |    1    |  D/V  |
| 4.15.2 | Verifica che i limiti di sicurezza della distribuzione ibrida siano chiaramente definiti con canali di comunicazione criptati.                                       |    2    |  D/V  |
| 4.15.3 | Verifica che l'accesso alle risorse cloud includa una verifica Zero-Trust con autenticazione continua.                                                               |    2    |  D/V  |
| 4.15.4 | Verifica che i requisiti di localizzazione dei dati siano applicati mediante attestazione crittografica delle sedi di archiviazione.                                 |    3    |  D/V  |
| 4.15.5 | Verifica che le valutazioni di sicurezza del fornitore di servizi cloud includano la modellazione delle minacce specifica per l'agente e la valutazione del rischio. |    3    |  D/V  |

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

