# Validazione dell'input utente C2

## Obiettivo di Controllo

La validazione robusta dell'input utente è una difesa di prima linea contro alcuni degli attacchi più dannosi ai sistemi di intelligenza artificiale. Gli attacchi di prompt injection possono sovrascrivere le istruzioni di sistema, divulgare dati sensibili o indirizzare il modello verso comportamenti non consentiti. A meno che non siano implementati filtri dedicati e altre forme di validazione, la ricerca mostra che i jailbreak che sfruttano le finestre di contesto continueranno a essere efficaci.

---

## C2.1 Difesa contro l'iniezione di prompt

L'iniezione di prompt è uno dei principali rischi per i sistemi di IA. Le difese contro questa tattica utilizzano una combinazione di filtri di pattern, classificatori di dati e applicazione della gerarchia delle istruzioni.

|   #   | Descrizione                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 2.1.1 | Verificare che qualsiasi input esterno o derivato che possa influenzare il comportamento, inclusi prompt dell’utente, risultati RAG, output di plugin o MCP, messaggi agente-agente, risposte API o webhook, file di configurazione o policy, letture e scritture di memoria, sia trattato come non attendibile, reso inerte tramite citazione o etichettatura e rimozione di contenuti attivi, e controllato tramite un set di regole o un servizio mantenuto per il rilevamento di iniezioni di prompt, prima della loro concatenazione nei prompt o dell’esecuzione di azioni. |    1    |  D/V  |
| 2.1.2 | Verificare che il sistema applichi una gerarchia di istruzioni in cui i messaggi di sistema e dello sviluppatore sovrascrivano le istruzioni dell'utente e altri input non attendibili, anche dopo l'elaborazione delle istruzioni dell'utente.                                                                                                                                                                                                                                                                                                                                   |    1    |  D/V  |
| 2.1.4 | Verificare che i prompt provenienti da contenuti di terze parti (pagine web, PDF, email) vengano sanitizzati in isolamento (ad esempio, rimuovendo direttive simili a istruzioni e neutralizzando contenuti HTML, Markdown e script) prima di essere concatenati nel prompt principale.                                                                                                                                                                                                                                                                                           |    2    |   D   |

---

## C2.2 Resistenza agli Esempi Avversari

I modelli di Elaborazione del Linguaggio Naturale (NLP) sono ancora vulnerabili a lievi perturbazioni a livello di caratteri o parole che gli esseri umani spesso non notano, ma che i modelli tendono a classificare erroneamente.

|   #   | Descrizione                                                                                                                                                                                                                                                                                                                                                                             | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 2.2.1 | Verificare che i passaggi di normalizzazione di input di base (Unicode NFC, mappatura degli omoglifi, rimozione degli spazi bianchi superflui, eliminazione dei caratteri di controllo e invisibili Unicode) vengano eseguiti prima della tokenizzazione o dell'embedding e prima dell'analisi negli argomenti degli strumenti o MCP.                                                   |    1    |   D   |
| 2.2.2 | Verificare che il rilevamento di anomalie statistiche segnali gli input con una distanza di modifica insolitamente elevata rispetto alle norme linguistiche o distanze di embedding anomale e che gli input segnalati vengano bloccati prima della concatenazione nei prompt o dell'esecuzione delle azioni.                                                                            |    2    |  D/V  |
| 2.2.3 | Verificare che la pipeline di inferenza supporti varianti di modelli rinforzati tramite addestramento adversariale o livelli di difesa (ad esempio, randomizzazione, distillazione difensiva, controlli di allineamento) per endpoint ad alto rischio.                                                                                                                                  |    2    |   D   |
| 2.2.4 | Verificare che gli input sospetti di tipo avversario siano messi in quarantena e registrati con i payload completi e i metadati di tracciamento (origine, strumento o server MCP, ID agente, sessione).                                                                                                                                                                                 |    2    |   V   |
| 2.2.5 | Verificare che il travisamento di codifica e rappresentazione sia rilevato e mitigato sia negli input che negli output (ad esempio, caratteri Unicode/control invisibili, sostituzioni di omoglifi o testo a direzione mista). Le mitigazioni approvate includono la canonicalizzazione, la validazione rigorosa dello schema, il rifiuto basato su politiche o la marcatura esplicita. |    2    |  D/V  |

---

## C2.3 Set di caratteri per il prompt

Limitare il set di caratteri degli input degli utenti per consentire solamente i caratteri necessari ai requisiti aziendali può aiutare a prevenire vari tipi di attacchi.

|   #   | Descrizione                                                                                                                                                                                      | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 2.3.1 | Verificare che il sistema implementi una limitazione del set di caratteri per gli input degli utenti, consentendo solo i caratteri espressamente richiesti per scopi aziendali.                  |    1    |   D   |
| 2.3.2 | Verificare che venga utilizzato un approccio basato su una lista di consentiti per definire il set di caratteri permessi.                                                                        |    1    |   D   |
| 2.3.3 | Verificare che gli input contenenti caratteri al di fuori del set consentito vengano rifiutati e registrati con metadati di tracciamento (origine, strumento o server MCP, ID agente, sessione). |    1    |  D/V  |

---

## C2.4 Validazione di Schema, Tipo e Lunghezza

Gli attacchi di intelligenza artificiale che utilizzano input malformati o sovradimensionati possono causare errori di parsing, fuoriuscite di prompt tra i campi e esaurimento delle risorse. Un'applicazione rigorosa dello schema è inoltre un prerequisito quando si eseguono chiamate deterministicte agli strumenti.

|   #   | Descrizione                                                                                                                                                                                                                                                                                                                 | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 2.4.1 | Verificare che ogni API, strumento o endpoint MCP definisca uno schema di input esplicito (JSON Schema, Protobuf o equivalente multimodale), rifiuti campi extra o sconosciuti e la coercizione implicita dei tipi, e convalidi gli input lato server prima dell’assemblaggio del prompt o dell’esecuzione dello strumento. |    1    |   D   |
| 2.4.2 | Verificare che gli input che superano i limiti massimi di token o byte vengano rifiutati con un errore sicuro e mai troncati silenziosamente.                                                                                                                                                                               |    1    |  D/V  |
| 2.4.3 | Verificare che i controlli di tipo (ad esempio, intervalli numerici, valori enum, tipi MIME per immagini/audio) siano applicati lato server, inclusi gli argomenti di strumenti o MCP.                                                                                                                                      |    2    |  D/V  |
| 2.4.4 | Verificare che i validatori semantici, che comprendono l’input NLP, operino in tempo costante ed evitino chiamate di rete esterne per prevenire DoS algoritmici.                                                                                                                                                            |    2    |   D   |
| 2.4.5 | Verificare che i fallimenti di convalida vengano registrati con estratti del payload oscurati e codici di errore univoci e includano i metadati di tracciamento (origine, strumento o server MCP, ID agente, sessione) per facilitare la gestione della sicurezza.                                                          |    3    |   V   |

---

## C2.5 Controllo dei Contenuti e delle Politiche

Gli sviluppatori dovrebbero essere in grado di rilevare prompt sintatticamente validi che richiedono contenuti non consentiti (come istruzioni illecite, discorsi d'odio e/o testi protetti da copyright) e impedirne la diffusione.

|   #   | Descrizione                                                                                                                                                                                                                                                                                                                              | Livello | Ruolo |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 2.5.1 | Verificare che un classificatore di contenuti (zero shot o fine-tuned) valuti ogni input e output per violenza, autolesionismo, odio, contenuti sessuali e richieste illegali, con soglie configurabili.                                                                                                                                 |    1    |   D   |
| 2.5.2 | Verificare che gli input che violano le politiche vengano rifiutati in modo che non si propaghino a chiamate successive verso LLM o strumenti/MCP.                                                                                                                                                                                       |    1    |  D/V  |
| 2.5.3 | Verificare che il filtraggio rispetti le politiche specifiche dell'utente (età, vincoli legali regionali) tramite regole basate su attributi risolte al momento della richiesta, inclusi gli attributi di ruolo dell'agente.                                                                                                             |    2    |   D   |
| 2.5.4 | Verificare che i log di screening includano i punteggi di confidenza del classificatore e le etichette delle categorie di policy con lo stadio applicato (pre-prompt o post-risposta) e i metadati di tracciamento (origine, strumento o server MCP, ID agente, sessione) per la correlazione SOC e la successiva riproduzione red-team. |    3    |   V   |

---

## C2.6 Limitazione della velocità di input e prevenzione degli abusi

Gli sviluppatori dovrebbero prevenire abusi, esaurimento delle risorse e attacchi automatizzati contro i sistemi di intelligenza artificiale limitando i tassi di input e rilevando modelli di utilizzo anomali.

|   #   | Descrizione                                                                                                                                                                                                                                                    | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 2.6.1 | Verificare che i limiti di velocità per utente, per IP, per chiave API, per agente e per sessione/compito siano applicati per tutti gli endpoint di input e degli strumenti/MCP.                                                                               |    1    |  D/V  |
| 2.6.2 | Verificare che i limiti di velocità burst e sostenuti siano regolati per prevenire attacchi DoS e di forza bruta, e che i budget per attività (ad esempio token, chiamate a strumenti/MCP e costi) siano applicati per i cicli di pianificazione degli agenti. |    2    |  D/V  |
| 2.6.3 | Verificare che i modelli di utilizzo anomali (ad esempio, richieste rapide consecutive, inondazione di input, chiamate ripetitive a strumenti/MCP che falliscono o loop ricorsivi dell’agente) attivino blocchi o escalation automatiche.                      |    2    |  D/V  |
| 2.6.4 | Verificare che i log di prevenzione degli abusi vengano conservati e controllati per individuare schemi di attacco emergenti, con metadati di tracciamento (origine, strumento o server MCP, ID agente, sessione).                                             |    3    |   V   |

---

## C2.7 Validazione di Input Multi-Modale

I sistemi di intelligenza artificiale dovrebbero includere una validazione robusta per input non testuali (immagini, audio, file) per prevenire iniezioni, evasione o abuso delle risorse.

|   #   | Descrizione                                                                                                                                                                                                                                                                                                                                                                                  | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 2.7.1 | Verificare che tutti gli input non testuali (immagini, audio, file) siano validati per tipo, dimensione e formato prima dell'elaborazione, e che eventuali testi estratti (da immagine a testo o da voce a testo) e qualsiasi istruzione nascosta o incorporata (metadata, livelli, testo alternativo, commenti) siano trattati come non affidabili secondo il punto 2.1.1.                  |    1    |   D   |
| 2.7.2 | Verificare che i file vengano analizzati per malware e payload steganografici prima dell'ingestione e che qualsiasi contenuto attivo (come script o macro) venga rimosso o che il file venga messo in quarantena.                                                                                                                                                                            |    2    |  D/V  |
| 2.7.3 | Verificare che gli input immagine/audio vengano controllati per perturbazioni avversarie o schemi di attacco noti, e che le rilevazioni attivino un sistema di controllo (bloccare o degradare le capacità) prima dell'uso del modello.                                                                                                                                                      |    2    |  D/V  |
| 2.7.4 | Verificare che i fallimenti nella validazione degli input multi-modali vengano registrati e attivino avvisi per le indagini, con metadata di tracciamento (origine, strumento o server MCP, ID agente, sessione).                                                                                                                                                                            |    3    |   V   |
| 2.7.5 | Verificare che il rilevamento degli attacchi cross-modali identifichi attacchi coordinati che coinvolgono più tipi di input (ad esempio, payload steganografici nelle immagini combinati con iniezione di prompt nel testo) mediante regole di correlazione e generazione di allarmi, e che le rilevazioni confermate vengano bloccate o richiedano l'approvazione HITL (human-in-the-loop). |    2    |  D/V  |
| 2.7.6 | Verificare che i fallimenti di validazione multi-modale attivino una registrazione dettagliata che includa tutte le modalità di input, i risultati della validazione, i punteggi delle minacce e i metadati di traccia (fonte, strumento o server MCP, ID agente, sessione).                                                                                                                 |    3    |  D/V  |
---

## C2.8 Rilevamento Adattativo delle Minacce in Tempo Reale

Gli sviluppatori dovrebbero utilizzare sistemi avanzati di rilevamento delle minacce per l'IA che si adattano a nuovi modelli di attacco e forniscono protezione in tempo reale con il matching di pattern compilati.

|   #   | Descrizione                                                                                                                                                                                                                                                                                                 | Livello | Ruolo |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 2.8.1 | Verificare che il pattern matching (ad esempio, espressioni regolari compilate) venga eseguito su tutti gli input e output (inclusi superfici di tool/MCP) con un impatto minimo sulla latenza.                                                                                                             |    1    |  D/V  |
| 2.8.3 | Verificare che i modelli di rilevamento adattativi regolino la sensibilità in base all'attività recente di attacco e vengano aggiornati con nuovi modelli in tempo reale, attivando risposte adattive al rischio (ad esempio disabilitare strumenti, ridurre il contesto o richiedere l'approvazione HITL). |    2    |  D/V  |
| 2.8.4 | Verificare che la precisione del rilevamento venga migliorata tramite l’analisi contestuale della cronologia utente, della fonte e del comportamento della sessione, inclusi i metadati di traccia (fonte, strumento o server MCP, ID agente, sessione).                                                    |    3    |  D/V  |
| 2.8.5 | Verificare che le metriche di prestazione della rilevazione (tasso di rilevamento, tasso di falsi positivi, latenza di elaborazione) siano monitorate e ottimizzate continuamente, includendo il tempo di blocco e la fase (pre-prompt/post-risposta).                                                      |    3    |  D/V  |

## Riferimenti

* [OWASP LLM01:2025 Prompt Injection](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)
* [LLM Prompt Injection Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/LLM_Prompt_Injection_Prevention_Cheat_Sheet.html)
* [MITRE ATLAS : Adversarial Input Detection](https://atlas.mitre.org/mitigations/AML.M00150)
* [Mitigate jailbreaks and prompt injections](https://docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/mitigate-jailbreaks)

