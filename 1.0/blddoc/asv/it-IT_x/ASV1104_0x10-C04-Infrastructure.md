# Sicurezza dell'infrastruttura, della configurazione e del deployment di C4

## Obiettivo di Controllo

L'infrastruttura AI deve essere rafforzata contro l'escalation dei privilegi, la manomissione della catena di approvvigionamento e i movimenti laterali tramite una configurazione sicura, l'isolamento in fase di esecuzione, pipeline di distribuzione affidabili e monitoraggio completo. Solo i componenti dell'infrastruttura validati e autorizzati raggiungono la produzione attraverso processi controllati che garantiscono sicurezza, integrità e tracciabilità.

Obiettivo Principale di Sicurezza: Solo i componenti dell'infrastruttura firmati criptograficamente e sottoposti a scansione delle vulnerabilità raggiungono la produzione attraverso pipeline di validazione automatizzate che applicano le politiche di sicurezza e mantengono registri di controllo immutabili.

---

## C4.1 Isolamento dell'Ambiente di Esecuzione

Prevenire le fughe dai container e l'escalation dei privilegi tramite primitive di isolamento a livello di sistema operativo.

|   #   | Descrizione                                                                                                                                                                                                                      | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.1.1 | Verificare che tutti i carichi di lavoro AI vengano eseguiti con i permessi minimi necessari sul sistema operativo, ad esempio rimuovendo le capacità Linux non necessarie nel caso di un container.                             |    1    |  D/V  |
| 4.1.2 | Verificare che i carichi di lavoro siano protetti da tecnologie che limitano lo sfruttamento come sandboxing, profili seccomp, AppArmor, SELinux o simili, e che la configurazione sia appropriata.                              |    1    |  D/V  |
| 4.1.3 | Verificare che i carichi di lavoro vengano eseguiti con un filesystem root di sola lettura e che tutte le mount scrivibili siano definite esplicitamente e protette con opzioni restrittive (ad esempio, noexec, nosuid, nodev). |    2    |  D/V  |
| 4.1.4 | Verificare che il monitoraggio in tempo reale rilevi i comportamenti di escalation dei privilegi e di fuga dal container e che termini automaticamente i processi responsabili.                                                  |    2    |  D/V  |
| 4.1.5 | Verificare che i carichi di lavoro AI ad alto rischio vengano eseguiti in ambienti isolati a livello hardware (ad esempio, TEEs, hypervisor affidabili o nodi bare-metal) solo dopo un'attestazione remota riuscita.             |    3    |  D/V  |

---

## C4.2 Pipeline di Build e Deployment Sicuri

Garantire l'integrità crittografica e la sicurezza della catena di approvvigionamento attraverso build riproducibili e artefatti firmati.

|   #   | Descrizione                                                                                                                                                                                                       | Livello | Ruolo |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.2.1 | Verificare che le build siano riproducibili e producano metadati di provenienza firmati, come appropriato per gli artefatti della build, che possano essere verificati in modo indipendente.                      |    1    |  D/V  |
| 4.2.2 | Verificare che le build producano una bill of materials (SBOM) del software e siano firmate prima di essere accettate per il deployment.                                                                          |    2    |  D/V  |
| 4.2.3 | Verificare che le firme degli artifact di build (ad esempio, le immagini container) e i metadati di provenienza siano convalidati al momento del deployment, e che gli artifact non verificati vengano rifiutati. |    2    |  D/V  |

---

## C4.3 Sicurezza di Rete e Controllo degli Accessi

Implementare una rete a fiducia zero con politiche di negazione predefinite e comunicazioni crittografate.

|   #   | Descrizione                                                                                                                                                                                                                                     | Livello | Ruolo |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.3.1 | Verificare che le policy di rete applichino il rifiuto predefinito per l’ingresso e l’uscita, consentendo esplicitamente solo i servizi necessari.                                                                                              |    1    |  D/V  |
| 4.3.2 | Verificare che i protocolli di accesso amministrativo (ad es., SSH, RDP) e l'accesso ai servizi di metadata cloud siano limitati e richiedano un’autenticazione forte.                                                                          |    1    |  D/V  |
| 4.3.3 | Verificare che il traffico in uscita sia limitato a destinazioni approvate e che tutte le richieste siano registrate.                                                                                                                           |    2    |  D/V  |
| 4.3.4 | Verificare che la comunicazione tra servizi utilizzi mutual TLS con validazione del certificato e rotazione automatica regolare.                                                                                                                |    2    |  D/V  |
| 4.3.5 | Verificare che i carichi di lavoro e gli ambienti AI (sviluppo, test, produzione) operino in segmenti di rete isolati (VPC/VNet) senza accesso diretto a Internet e senza ruoli IAM condivisi, gruppi di sicurezza o connettività tra ambienti. |    2    |  D/V  |

## C4.4 Gestione dei Segreti e delle Chiavi Criptografiche

Proteggi i segreti e le chiavi crittografiche con uno storage sicuro, rotazione automatica e solidi controlli di accesso.

|   #   | Descrizione                                                                                                                                                                                                                                                                                                                | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.4.1 | Verificare che i segreti siano archiviati in un sistema dedicato di gestione dei segreti con crittografia a riposo e isolati dai carichi di lavoro delle applicazioni.                                                                                                                                                     |    1    |  D/V  |
| 4.4.2 | Verificare che le chiavi crittografiche siano generate e archiviate in moduli supportati da hardware (ad esempio, HSM, KMS cloud).                                                                                                                                                                                         |    1    |  D/V  |
| 4.4.3 | Verificare che l'accesso ai segreti di produzione richieda un'autenticazione forte.                                                                                                                                                                                                                                        |    1    |  D/V  |
| 4.4.4 | Verificare che i segreti vengano distribuiti alle applicazioni durante l'esecuzione tramite un sistema dedicato di gestione dei segreti. I segreti non devono mai essere incorporati nel codice sorgente, nei file di configurazione, negli artefatti di build, nelle immagini dei container o nelle variabili d'ambiente. |    1    |  D/V  |
| 4.4.5 | Verificare che la rotazione dei segreti sia automatizzata.                                                                                                                                                                                                                                                                 |    2    |  D/V  |

---

## C4.5 Isolamento e Validazione del Carico di Lavoro AI

Isola i modelli di IA non affidabili in sandbox sicure e proteggi i carichi di lavoro sensibili di IA utilizzando ambienti di esecuzione affidabili (TEE) e tecnologie di calcolo confidenziale.

|   #   | Descrizione                                                                                                                                                                                                                          | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 4.5.1 | Verificare che i modelli di AI esterni o non affidabili vengano eseguiti in sandbox isolate.                                                                                                                                         |    1    |  D/V  |
| 4.5.2 | Verificare che i carichi di lavoro in sandbox non abbiano connettività di rete in uscita per impostazione predefinita, con qualsiasi accesso necessario definito esplicitamente.                                                     |    1    |  D/V  |
| 4.5.3 | Verificare che l'attestazione del carico di lavoro venga eseguita prima del caricamento del modello o del carico di lavoro, garantendo una prova crittografica di un ambiente di esecuzione attendibile.                             |    2    |  D/V  |
| 4.5.4 | Verificare che i carichi di lavoro confidenziali vengano eseguiti all'interno di un ambiente di esecuzione affidabile (TEE) che fornisce isolamento garantito dall'hardware, crittografia della memoria e protezione dell'integrità. |    3    |  D/V  |
| 4.5.5 | Verificare che i servizi di inferenza riservati prevengano l'estrazione del modello tramite calcolo crittografato con pesi del modello sigillati ed esecuzione protetta.                                                             |    3    |  D/V  |
| 4.5.6 | Verificare che l'orchestrazione degli ambienti di esecuzione attendibili includa la gestione del ciclo di vita, l'attestazione remota e i canali di comunicazione crittografati.                                                     |    3    |  D/V  |
| 4.5.7 | Verificare che il calcolo multipartito sicuro (SMPC) consenta l’addestramento collaborativo dell’IA senza esporre set di dati individuali o parametri del modello.                                                                   |    3    |  D/V  |

---

## C4.6 Gestione delle risorse dell'infrastruttura AI, backup e ripristino

Prevenire attacchi di esaurimento delle risorse e garantire una distribuzione equa delle risorse tramite quote e monitoraggio. Mantenere la resilienza dell'infrastruttura attraverso backup sicuri, procedure di recupero testate e capacità di disaster recovery.

|   #   | Descrizione                                                                                                                                                                                                                                            | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 4.6.1 | Verificare che il consumo di risorse del carico di lavoro sia limitato in modo appropriato con, ad esempio, ResourceQuota di Kubernetes o strumenti simili per mitigare gli attacchi di Denial of Service.                                             |    2    |  D/V  |
| 4.6.2 | Verificare che l'esaurimento delle risorse attivi le protezioni automatiche (ad esempio, limitazione della velocità o isolamento del carico di lavoro) una volta superate le soglie definite di CPU, memoria o richieste.                              |    2    |  D/V  |
| 4.6.3 | Verificare che i sistemi di backup operino in reti isolate con credenziali separate e che il sistema di archiviazione sia gestito in una rete air-gapped oppure implementi la protezione WORM (write-once-read-many) contro modifiche non autorizzate. |    2    |  D/V  |

---

## C4.7 Sicurezza dell'hardware AI

Proteggi i componenti hardware specifici per l'IA, inclusi GPU, TPU e acceleratori AI specializzati.

|   #   | Descrizione                                                                                                                                                                                                                | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.7.1 | Verificare che prima dell'esecuzione del carico di lavoro, l'integrità dell'acceleratore AI sia convalidata utilizzando meccanismi di attestazione basati su hardware (ad esempio, TPM, DRTM o equivalenti).               |    2    |  D/V  |
| 4.7.2 | Verificare che la memoria dell'acceleratore (GPU) sia isolata tra i carichi di lavoro tramite meccanismi di partizionamento con la sanificazione della memoria tra i processi.                                             |    2    |  D/V  |
| 4.7.3 | Verificare che i moduli di sicurezza hardware (HSM) proteggano i pesi del modello AI e le chiavi crittografiche con certificazione FIPS 140-3 Livello 3 o Common Criteria EAL4+.                                           |    3    |  D/V  |
| 4.7.4 | Verificare che il firmware dell'acceleratore (GPU/TPU/NPUs) sia bloccato a una versione specifica, firmato e attestato all'avvio; i firmware non firmati o di debug devono essere bloccati.                                |    2    |  D/V  |
| 4.7.5 | Verificare che la VRAM e la memoria on-package siano azzerate tra i lavori/tenant e che le politiche di reset del dispositivo prevengano la persistenza dei dati tra tenant.                                               |    2    |  D/V  |
| 4.7.6 | Verificare che le funzionalità di partizionamento/isolation (ad esempio, partizionamento MIG/VM) siano applicate per ogni tenant e impediscano l'accesso alla memoria peer-to-peer tra le partizioni.                      |    2    |  D/V  |
| 4.7.7 | Verificare che le interconnessioni degli accelerator (NVLink/PCIe/InfiniBand/RDMA/NCCL) siano limitate a topologie approvate e a endpoint autenticati; i collegamenti in chiaro tra tenant diversi non sono consentiti.    |    3    |  D/V  |
| 4.7.8 | Verificare che la telemetria dell'acceleratore (potenza, temperature, ECC, contatori di prestazioni) venga esportata a SIEM/OTel e che vengano generati avvisi su anomalie indicative di canali laterali o canali occulti. |    3    |   D   |

---

## C4.8 Sicurezza dell'AI Edge e Distribuita

Distribuzioni AI sicure distribuite, inclusi edge computing, apprendimento federato e architetture multisito.

|   #   | Descrizione                                                                                                                                                                                        | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 4.8.1 | Verificare che i dispositivi edge AI si autentichino all'infrastruttura centrale utilizzando mutual TLS.                                                                                           |    2    |  D/V  |
| 4.8.2 | Verificare che i dispositivi edge implementino il secure boot con firme verificate e protezione rollback per prevenire attacchi di downgrade del firmware.                                         |    2    |  D/V  |
| 4.8.3 | Verificare che il coordinamento dell'IA distribuita utilizzi meccanismi di consenso tolleranti ai guasti bizantini con validazione dei partecipanti e rilevamento di nodi malevoli.                |    3    |  D/V  |
| 4.8.4 | Verificare che la comunicazione edge-to-cloud supporti la limitazione della larghezza di banda, la compressione dei dati e il funzionamento sicuro offline con archiviazione locale crittografata. |    3    |  D/V  |

---

## Riferimenti

* [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework)
* [CIS Controls v8](https://www.cisecurity.org/controls/v8)
* [Kubernetes Security Best Practices](https://kubernetes.io/docs/concepts/security/)
* [Cloud Security Alliance: Cloud Controls Matrix](https://cloudsecurityalliance.org/research/cloud-controls-matrix/)
* [ENISA: Secure Infrastructure Design](https://www.enisa.europa.eu/topics/critical-information-infrastructures-and-services)
* [ISO 27001:2022 Information Security Management](https://www.iso.org/standard/27001)
* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)

