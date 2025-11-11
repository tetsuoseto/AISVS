# Controllo Accessi C5 e Identità per Componenti e Utenti AI

## Obiettivo di Controllo

Un controllo degli accessi efficace per i sistemi di intelligenza artificiale richiede una gestione robusta delle identità, un'autorizzazione contestuale e un'applicazione in tempo reale secondo i principi zero-trust. Questi controlli garantiscono che umani, servizi e agenti autonomi interagiscano solo con modelli, dati e risorse computazionali all'interno di ambiti esplicitamente concessi, con capacità di verifica continua e audit.

---

## C5.1 Gestione dell'Identità e Autenticazione

Stabilire identità supportate da crittografia per tutte le entità con autenticazione a più fattori.

|   #   | Descrizione                                                                                                                                                                                                                                                                         | Livello | Ruolo |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 5.1.1 | Verificare che tutti gli utenti umani e i service principal si autentichino tramite un provider di identità aziendale centralizzato (IdP) utilizzando i protocolli OIDC e/o SAML.                                                                                                   |    1    |  D/V  |
| 5.1.2 | Verificare che le operazioni ad alto rischio (deploy del modello, esportazione dei pesi, accesso ai dati di addestramento, modifiche alla configurazione di produzione) richiedano l'autenticazione multi-fattore o un'autenticazione step-up con la ri-validazione della sessione. |    1    |  D/V  |
| 5.1.3 | Verificare che gli agenti AI federati si autentichino tramite asserzioni JWT firmate che abbiano una durata massima di 24 ore e includano una prova crittografica di origine.                                                                                                       |    3    |  D/V  |

---

## C5.2 Autorizzazione e Politica

Implementare controlli di accesso per tutte le risorse AI con modelli di autorizzazione espliciti e tracce di audit.

|   #   | Descrizione                                                                                                                                                                                                                                        | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 5.2.1 | Verificare che ogni risorsa AI (dataset, modelli, endpoint, collezioni di vettori, indici di embedding, istanze di calcolo) applichi controlli di accesso basati sui ruoli con liste di consentiti esplicite e politiche di negazione predefinite. |    1    |  D/V  |
| 5.2.2 | Verificare che tutte le modifiche al controllo degli accessi siano registrate in modo immutabile con timestamp, identità degli attori, identificatori delle risorse e modifiche alle autorizzazioni.                                               |    1    |   V   |
| 5.2.3 | Verificare che le etichette di classificazione dei dati (PII, PHI, proprietarie, ecc.) si propaghino automaticamente alle risorse derivate (embedding, cache dei prompt, output del modello).                                                      |    2    |   D   |
| 5.2.4 | Verificare che i tentativi di accesso non autorizzati e gli eventi di escalation dei privilegi attivino avvisi in tempo reale con metadati contestuali.                                                                                            |    2    |  D/V  |
| 5.2.5 | Verificare che le decisioni di autorizzazione siano esternalizzate a un motore di policy dedicato (OPA, Cedar o equivalente).                                                                                                                      |    1    |  D/V  |
| 5.2.6 | Verificare che le policy valutino gli attributi dinamici in fase di esecuzione, inclusi ruolo o gruppo dell'utente, classificazione della risorsa, contesto della richiesta, isolamento del tenant e vincoli temporali.                            |    1    |  D/V  |
| 5.2.7 | Verificare che i valori di time-to-live (TTL) della cache delle policy non superino i 5 minuti per le risorse ad alta sensibilità e 1 ora per le risorse standard con capacità di invalidamento della cache.                                       |    3    |  D/V  |

---

## C5.3 Applicazione della sicurezza in fase di interrogazione

Implementare controlli di sicurezza a livello di database con filtri obbligatori e politiche di sicurezza a livello di riga.

|   #   | Descrizione                                                                                                                                                                                                                             | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 5.3.1 | Verificare che tutte le query sui database vettoriali e SQL includano filtri di sicurezza obbligatori (ID del tenant, etichette di sensibilità, ambito utente) applicati a livello del motore di database.                              |    1    |  D/V  |
| 5.3.2 | Verificare che le politiche di sicurezza a livello di riga e la mascheratura a livello di campo siano abilitate con l’ereditarietà delle politiche per tutti i database vettoriali, gli indici di ricerca e i dataset di addestramento. |    1    |  D/V  |
| 5.3.3 | Verificare che le valutazioni di autorizzazione fallite interrompano immediatamente le query e restituiscano codici di errore di autorizzazione espliciti.                                                                              |    2    |   D   |
| 5.3.4 | Verificare che i meccanismi di ritentativo delle query rivalutino le politiche di autorizzazione per tenere conto delle modifiche dinamiche delle autorizzazioni nelle sessioni utente attive.                                          |    3    |  D/V  |

---

## C5.4 Filtraggio dell'Output e Prevenzione della Perdita di Dati

Implementare controlli di post-elaborazione per prevenire l'esposizione non autorizzata di dati nei contenuti generati dall'IA.

|   #   | Descrizione                                                                                                                                                                                                                    | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 5.4.1 | Verificare che i meccanismi di filtraggio post-inferenza scansionino e oscurino le informazioni personali non autorizzate, le informazioni classificate e i dati proprietari prima di consegnare il contenuto ai richiedenti.  |    1    |  D/V  |
| 5.4.2 | Verificare che citazioni, riferimenti e attribuzioni di fonte nei risultati del modello siano convalidati rispetto ai diritti del chiamante e rimossi se viene rilevato un accesso non autorizzato.                            |    1    |  D/V  |
| 5.4.3 | Verificare che le restrizioni sul formato di output (PDF sanitizzati, immagini con metadati rimossi, tipi di file approvati) siano applicate in base ai livelli di autorizzazione dell'utente e alle classificazioni dei dati. |    2    |   D   |

---

## C5.5 Isolamento Multi-Tenant

Garantire l'isolamento crittografico e logico tra i tenant in un'infrastruttura AI condivisa.

|   #   | Descrizione                                                                                                                                                                                                                                          | Livello | Ruolo |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 5.5.1 | Verificare che gli spazi di memoria, gli archivi di embedding, le voci della cache e i file temporanei siano segregati per namespace per ogni tenant, con una cancellazione sicura in caso di eliminazione del tenant o terminazione della sessione. |    1    |  D/V  |
| 5.5.2 | Verificare che ogni richiesta API includa un identificatore tenant autenticato, convalidato crittograficamente rispetto al contesto della sessione e alle autorizzazioni dell'utente.                                                                |    1    |  D/V  |
| 5.5.3 | Verificare che le policy di rete implementino regole di default-deny per la comunicazione cross-tenant all'interno delle service mesh e delle piattaforme di orchestrazione dei container.                                                           |    2    |   D   |
| 5.5.4 | Verificare che le chiavi di crittografia siano uniche per ogni tenant con supporto per chiavi gestite dal cliente (CMK) e isolamento crittografico tra gli archivi dati dei tenant.                                                                  |    3    |   D   |

---

## C5.6 Autorizzazione dell'Agente Autonomo

Controlla le autorizzazioni per agenti di IA e sistemi autonomi tramite token di capacità con ambito definito e autorizzazione continua.

|   #   | Descrizione                                                                                                                                                                                                      | Livello | Ruolo |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 5.6.1 | Verificare che gli agenti autonomi ricevano token di capacità delimitati che enumerano esplicitamente le azioni consentite, le risorse accessibili, i limiti temporali e i vincoli operativi.                    |    1    |  D/V  |
| 5.6.2 | Verificare che le capacità ad alto rischio (accesso al file system, esecuzione di codice, chiamate API esterne, transazioni finanziarie) siano disabilitate di default e richiedano un'autorizzazione esplicita. |    1    |  D/V  |
| 5.6.3 | Verificare che i token di capacità siano legati alle sessioni utente, includano una protezione di integrità crittografica e garantire che non possano essere memorizzati o riutilizzati in scenari offline.      |    2    |   D   |
| 5.6.4 | Verificare che le azioni avviate dall'agente siano soggette ad autorizzazione tramite un motore di policy ABAC.                                                                                                  |    2    |   V   |

---

## Riferimenti

* [NIST SP 800-162: Guide to Attribute Based Access Control (ABAC)](https://csrc.nist.gov/pubs/sp/800/162/final)
* [NIST SP 800-207: Zero Trust Architecture](https://csrc.nist.gov/pubs/sp/800/207/final)
* [NIST SP 800-63-3: Digital Identity Guidelines](https://csrc.nist.gov/pubs/sp/800/63/3/final)
* [NIST IR 8360: Machine Learning for Access Control Policy Verification](https://csrc.nist.gov/pubs/ir/8360/final)

