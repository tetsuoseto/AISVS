# C5 Controllo degli Accessi e Identità per Componenti e Utenti IA

## Obiettivo di controllo

Un controllo di accesso efficace per i sistemi di IA richiede una gestione robusta delle identità, un'autorizzazione basata sul contesto e un'attuazione al runtime conforme ai principi zero-trust. Questi controlli garantiscono che gli esseri umani, i servizi e gli agenti autonomi interagiscano solo con modelli, dati e risorse computazionali all'interno di ambiti concessi esplicitamente, con verifica continua e capacità di audit.

---

## Gestione delle identità e dell'autenticazione

Stabilire identità basate su crittografia per tutte le entità, con autenticazione a più fattori per operazioni privilegiate.

|   #   | Descrizione                                                                                                                                                                                                                                                                           | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 5.1.1 | Verifica che tutti gli utenti umani e i principali di servizio si autentichino tramite un fornitore di identità aziendale centralizzato (IdP) utilizzando i protocolli OIDC/SAML con mappature identità-token uniche (nessun account o credenziale condivisi).                        |    1    |  D/V  |
| 5.1.2 | Verifica che le operazioni ad alto rischio (implementazione del modello, esportazione dei pesi, accesso ai dati di addestramento, modifiche alle configurazioni di produzione) richiedano autenticazione a più fattori o autenticazione step-up con ri-autenticazione della sessione. |    1    |  D/V  |
| 5.1.3 | Verificare che i nuovi soggetti siano sottoposti a una verifica dell'identità in linea con NIST 800-63-3 IAL-2 o standard equivalenti prima di ottenere l'accesso al sistema di produzione.                                                                                           |    2    |   D   |
| 5.1.4 | Verificare che le revisioni degli accessi siano condotte trimestralmente, con rilevamento automatico degli account inattivi, l'applicazione della rotazione delle credenziali e i flussi di de-provisioning.                                                                          |    2    |   V   |
| 5.1.5 | Verifica che gli agenti IA federati si autentichino tramite asserzioni JWT firmate che abbiano una durata massima di 24 ore e includano una prova crittografica di provenienza.                                                                                                       |    3    |  D/V  |

---

## C5.2 Autorizzazione alle risorse e principio del minimo privilegio

Implementare controlli di accesso granulare per tutte le risorse di IA con modelli di autorizzazione espliciti e tracce di audit.

|   #   | Descrizione                                                                                                                                                                                                                                                                         | Livello | Ruolo |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 5.2.1 | Verifica che ogni risorsa IA (set di dati, modelli, endpoint, collezioni di vettori, indici di embedding, istanze di calcolo) applichi controlli di accesso basati sui ruoli con liste di autorizzazione esplicite e politiche di negazione predefinite.                            |    1    |  D/V  |
| 5.2.2 | Verifica che i principi del minimo privilegio siano applicati di default, con gli account di servizio che partono da permessi di sola lettura e che richiedono una giustificazione aziendale documentata per l'accesso in scrittura.                                                |    1    |  D/V  |
| 5.2.3 | Verifica che tutte le modifiche al controllo degli accessi siano collegate a richieste di modifica approvate e registrate in modo immutabile con timestamp, identità degli attori, identificatori delle risorse e variazioni dei permessi.                                          |    1    |   V   |
| 5.2.4 | Verifica che le etichette di classificazione dei dati (PII, PHI, esportazione controllata, dati proprietari) si propagano automaticamente alle risorse derivate (rappresentazioni di embedding, cache dei prompt, uscite del modello) con un'applicazione coerente delle politiche. |    2    |   D   |
| 5.2.5 | Verifica che i tentativi di accesso non autorizzato e gli eventi di escalation dei privilegi attivino avvisi in tempo reale con metadati contestuali ai sistemi SIEM entro 5 minuti.                                                                                                |    2    |  D/V  |

---

## C5.3 Valutazione dinamica della politica

Distribuire motori ABAC per decisioni di autorizzazione contestualizzate con funzionalità di audit.

|   #   | Descrizione                                                                                                                                                                                                                                                   | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 5.3.1 | Verificare che le decisioni di autorizzazione siano esternalizzate a un motore di policy dedicato (OPA, Cedar o equivalente), accessibile tramite API autenticati con protezione dell'integrità crittografica.                                                |    1    |  D/V  |
| 5.3.2 | Verificare che le policy valutino attributi dinamici a tempo di esecuzione, inclusi il livello di autorizzazione dell'utente, la classificazione della sensibilità della risorsa, il contesto della richiesta, l'isolamento tra tenant e i vincoli temporali. |    1    |  D/V  |
| 5.3.3 | Verificare che le definizioni delle policy siano versionate, sottoposte a revisione tra pari e validate tramite test automatizzati nelle pipeline CI/CD prima della messa in produzione.                                                                      |    2    |   D   |
| 5.3.4 | Verifica che i risultati della valutazione delle policy includano giustificazioni decisionali strutturate e siano trasmessi ai sistemi SIEM per l'analisi di correlazione e la reportistica sulla conformità.                                                 |    2    |   V   |
| 5.3.5 | Verifica che i valori TTL della cache delle policy non superino 5 minuti per le risorse ad alta sensibilità e 1 ora per le risorse standard con capacità di invalidazione della cache.                                                                        |    3    |  D/V  |

---

## C5.4 Esecuzione della sicurezza in tempo di query

Implementare controlli di sicurezza a livello di database con filtraggio obbligatorio e politiche di sicurezza a livello di riga.

|   #   | Descrizione                                                                                                                                                                                                                                         | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 5.4.1 | Verifica che tutte le query sui database vettoriali e SQL includano filtri di sicurezza obbligatori (ID tenant, etichette di sensibilità, ambito utente) imposti a livello del motore del database, non nel codice dell'applicazione.               |    1    |  D/V  |
| 5.4.2 | Verifica che le policy di sicurezza a livello di riga (RLS) e il mascheramento a livello di campo siano abilitati con l’ereditarietà delle policy per tutti i database vettoriali, gli indici di ricerca e i set di dati di addestramento.          |    1    |  D/V  |
| 5.4.3 | Verifica che le valutazioni di autorizzazione fallite prevengano gli attacchi del 'confused deputy' interrompendo immediatamente le query e restituendo codici di errore di autorizzazione espliciti anziché restituire insiemi di risultati vuoti. |    2    |   D   |
| 5.4.4 | Verificare che la latenza della valutazione della policy sia monitorata in modo continuo con avvisi automatici per condizioni di timeout che potrebbero consentire il bypass dell'autorizzazione.                                                   |    2    |   V   |
| 5.4.5 | Verifica che i meccanismi di ritentativo delle query rivalutino le politiche di autorizzazione per tenere conto delle modifiche dinamiche ai permessi durante le sessioni utente attive.                                                            |    3    |  D/V  |

---

## C5.5 Filtraggio dell'output & Prevenzione della perdita di dati

Implementa controlli di post-elaborazione per impedire l'esposizione non autorizzata dei dati nei contenuti generati dall'IA.

|   #   | Descrizione                                                                                                                                                                                                                            | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 5.5.1 | Verifica che i meccanismi di filtraggio post-inferenza scansionino e redigano informazioni personalmente identificabili (PII) non autorizzate, informazioni classificate e dati proprietari prima di fornire contenuti ai richiedenti. |    1    |  D/V  |
| 5.5.2 | Verificare che le citazioni, i riferimenti e le attribuzioni delle fonti presenti nei risultati del modello siano validati rispetto alle autorizzazioni del chiamante e rimosse se viene rilevato accesso non autorizzato.             |    1    |  D/V  |
| 5.5.3 | Verifichi che le restrizioni sui formati di output (PDF sanificati, immagini prive di metadati, tipi di file approvati) siano applicate in base ai livelli di permesso degli utenti e alle classificazioni dei dati.                   |    2    |   D   |
| 5.5.4 | Verifica che gli algoritmi di anonimizzazione siano deterministici, versionati e mantengano registri di audit per supportare le indagini di conformità e l'analisi forense.                                                            |    2    |   V   |
| 5.5.5 | Verifica che gli eventi di redazione ad alto rischio generino registri adattivi che includano hash crittografici del contenuto originale per il recupero forense senza esposizione dei dati.                                           |    3    |   V   |

---

## C5.6 Isolamento multi-tenant

Garantire l'isolamento crittografico e logico tra i tenant in un'infrastruttura IA condivisa.

|   #   | Descrizione                                                                                                                                                                                                                                                            | Livello | Ruolo |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 5.6.1 | Verificare che gli spazi di memoria, gli archivi di embedding, le voci della cache e i file temporanei siano separati per spazio dei nomi per ciascun inquilino, con una purga sicura al momento dell'eliminazione dell'inquilino o della terminazione della sessione. |    1    |  D/V  |
| 5.6.2 | Verificare che ogni richiesta API includa un identificatore del tenant autenticato che sia validato crittograficamente rispetto al contesto della sessione e ai diritti dell'utente.                                                                                   |    1    |  D/V  |
| 5.6.3 | Verificare che le policy di rete implementino regole di rifiuto predefinito per la comunicazione tra tenant all'interno delle mesh di servizio e delle piattaforme di orchestrazione dei contenitori.                                                                  |    2    |   D   |
| 5.6.4 | Verificare che le chiavi di cifratura siano uniche per ogni inquilino, con supporto CMK (Chiave gestita dal cliente) e isolamento crittografico tra i data store dei diversi inquilini.                                                                                |    3    |   D   |

---

## C5.7 Autorizzazione dell'agente autonomo

Controlla i permessi per agenti IA e sistemi autonomi tramite token di capacità con ambito definito e autorizzazione continua.

|   #   | Descrizione                                                                                                                                                                                                                                                                      | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 5.7.1 | Verifica che agli agenti autonomi vengano forniti token di capacità con ambito definito e che tali token elenchino esplicitamente le azioni consentite, le risorse accessibili, i limiti temporali e i vincoli operativi.                                                        |    1    |  D/V  |
| 5.7.2 | Verificare che le capacità ad alto rischio (accesso al file system, esecuzione del codice, chiamate API esterne, transazioni finanziarie) siano disabilitate per impostazione predefinita e richiedano autorizzazioni esplicite per l'attivazione con giustificazioni aziendali. |    1    |  D/V  |
| 5.7.3 | Verificare che i token di capacità siano vincolati alle sessioni utente, includano protezione dell'integrità crittografica e non possano essere conservati o riutilizzati in scenari offline.                                                                                    |    2    |   D   |
| 5.7.4 | Verifica che le azioni avviate dall'agente siano soggette a autorizzazione secondaria tramite il motore di policy ABAC, con una valutazione completa del contesto e registrazione di audit.                                                                                      |    2    |   V   |
| 5.7.5 | Verificare che le condizioni di errore dell'agente e la gestione delle eccezioni includano informazioni sull'ambito delle capacità per supportare l'analisi degli incidenti e le indagini forensi.                                                                               |    3    |   V   |

---

## Riferimenti

### Standard e Quadri di riferimento

* [NIST SP 800-63-3: Digital Identity Guidelines](https://pages.nist.gov/800-63-3/)
* [Zero Trust Architecture – NIST SP 800-207](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.800-207.pdf)
* [OWASP Application Security Verification Standard (AISVS)](https://owasp.org/www-project-application-security-verification-standard/)
  ​
### Guide di implementazione

* [Identity and Access Management in the AI Era: 2025 Guide – IDSA](https://www.idsalliance.org/blog/identity-and-access-management-in-the-ai-era-2025-guide/)
* [Attribute-Based Access Control with OPA – Permify](https://medium.com/permify-tech-blog/attribute-based-access-control-abac-implementation-with-open-policy-agent-opa-b47052248f29)
* [How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS](https://aws.amazon.com/blogs/security/how-we-designed-cedar-to-be-intuitive-to-use-fast-and-safe/)
  ​
### Sicurezza specifica per l'IA

* [Row Level Security in Vector DBs for RAG – Bluetuple.ai](https://medium.com/bluetuple-ai/implementing-row-level-security-in-vector-dbs-for-rag-applications-fdbccb63d464)
* [Tenant Isolation in Multi-Tenant Systems – WorkOS](https://workos.com/blog/tenant-isolation-in-multi-tenant-systems)
* [Handling AI Agent Permissions – Stytch](https://stytch.com/blog/handling-ai-agent-permissions/)
* [OWASP Top 10 for Large Language Model Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

