# C2 Validazione dell'input dell'utente

## Obiettivo di controllo

Una validazione robusta dell'input dell'utente è una prima linea di difesa contro alcuni degli attacchi più dannosi rivolti ai sistemi di IA. Gli attacchi di iniezione di prompt possono sovrascrivere le istruzioni di sistema, rivelare dati sensibili o guidare il modello verso comportamenti non consentiti. A meno che non siano presenti filtri dedicati e gerarchie di istruzioni, la ricerca mostra che "multi-shot" jailbreaks che sfruttano finestre di contesto molto lunghe saranno efficaci. Inoltre, attacchi di perturbazione avversaria sottili--come scambi di omografi o leetspeak—possono modificare silenziosamente le decisioni del modello.

---

## C2.1 Difesa contro l'iniezione di prompt

L'iniezione di prompt è uno dei principali rischi per i sistemi di IA. Le difese contro questa tattica impiegano una combinazione di filtri di pattern statici, classificatori dinamici e l'applicazione della gerarchia delle istruzioni.

|   #   | Descrizione                                                                                                                                                                                                                                     | Livello | Ruolo |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 2.1.1 | Verifichi che gli input degli utenti siano filtrati rispetto a una libreria costantemente aggiornata di schemi noti di prompt injection (parole chiave di jailbreak, "ignore previous", catene di gioco di ruolo, attacchi indiretti HTML/URL). |    1    |  D/V  |
| 2.1.2 | Verifica che il sistema faccia rispettare una gerarchia di istruzioni in cui i messaggi di sistema o di sviluppatore hanno la precedenza sulle istruzioni dell'utente, anche dopo l'espansione della finestra di contesto.                      |    1    |  D/V  |
| 2.1.3 | Verifica che i test di valutazione avversaria (ad es. i prompt della Red Team 'many-shot') siano eseguiti prima di ogni rilascio di modello o di template di prompt, con soglie di tasso di successo e blocchi automatici per le regressioni.   |    2    |  D/V  |
| 2.1.4 | Verifica che i prompt originati da contenuti di terze parti (pagine Web, PDF, email) siano sanificati in un contesto di parsing isolato prima di essere concatenati nel prompt principale.                                                      |    2    |   D   |
| 2.1.5 | Verifica che tutti gli aggiornamenti delle regole del prompt-filter, le versioni dei modelli classificatori e le modifiche al block-list siano sotto controllo di versione e auditabili.                                                        |    3    |  D/V  |

---

## C2.2 Resistenza agli esempi avversi

I modelli di Elaborazione del Linguaggio Naturale (NLP) sono ancora vulnerabili a perturbazioni sottili a livello di caratteri o di parole che gli esseri umani spesso non notano, ma i modelli tendono a classificare erroneamente.

|   #   | Descrizione                                                                                                                                                                                                                                        | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 2.2.1 | Verifica che i passaggi di base di normalizzazione dell'input (normalizzazione Unicode NFC, mappatura degli omografi, rimozione degli spazi bianchi) vengano eseguiti prima della tokenizzazione.                                                  |    1    |   D   |
| 2.2.2 | Verifica che il rilevamento statistico delle anomalie contrassegni gli input caratterizzati da una distanza di Levenshtein notevolmente superiore alle norme linguistiche, da token ripetuti in modo eccessivo o da distanze di embedding anomale. |    2    |  D/V  |
| 2.2.3 | Verificare che la pipeline di inferenza supporti varianti di modelli opzionali potenziati dall'addestramento avversariale–rafforzato o strati di difesa (ad es., randomizzazione, distillazione difensiva) per endpoint ad alto rischio.           |    2    |   D   |
| 2.2.4 | Verifica che gli input avversari sospetti siano messi in quarantena e che siano registrati con payload completi (dopo l'anonimizzazione delle informazioni PII).                                                                                   |    2    |   V   |
| 2.2.5 | Verifica che le metriche di robustezza (tasso di successo delle suite di attacchi note) vengano tracciate nel tempo e che le regressioni attivino un blocco di rilascio.                                                                           |    3    |  D/V  |

---

## C2.3 Validazione dello schema, del tipo e della lunghezza

Attacchi basati sull'IA che presentano input malformati o troppo grandi possono causare errori di parsing, propagazione del prompt tra i campi e esaurimento delle risorse.  L'applicazione rigorosa dello schema è anche un prerequisito quando si eseguono chiamate deterministiche agli strumenti.

|   #   | Descrizione                                                                                                                                                                                                          | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 2.3.1 | Verifica che ogni endpoint API o chiamata di funzione definisca uno schema di input esplicito (JSON Schema, Protobuf o equivalente multimodale) e che gli input vengano validati prima dell'assemblaggio del prompt. |    1    |   D   |
| 2.3.2 | Verifica che gli input che superano i limiti massimi di token o di byte vengano rifiutati con un errore sicuro e non vengano mai troncati silenziosamente.                                                           |    1    |  D/V  |
| 2.3.3 | Verifica che i controlli di tipo (ad es. intervalli numerici, valori enum, tipi MIME per immagini/audio) siano applicati sul lato server, non solo nel codice lato client.                                           |    2    |  D/V  |
| 2.3.4 | Verifica che i validatori semantici (ad es. JSON Schema) operino in tempo costante per prevenire attacchi DoS algoritmici.                                                                                           |    2    |   D   |
| 2.3.5 | Verifica che i fallimenti di validazione siano registrati con frammenti di payload oscurati e codici di errore univoci per agevolare il triage di sicurezza.                                                         |    3    |   V   |

---

## C2.4 Verifica dei contenuti e delle politiche

Gli sviluppatori dovrebbero essere in grado di rilevare prompt sintatticamente validi che richiedono contenuti vietati (come istruzioni illecite, discorsi d'odio e testi protetti da copyright) e impedire che vengano propagati.

|   #   | Descrizione                                                                                                                                                                                                   | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 2.4.1 | Verifica che un classificatore di contenuti (zero-shot o finetunato) assegni un punteggio a ogni input per violenza, autolesionismo, odio, contenuti sessuali e richieste illegali, con soglie configurabili. |    1    |   D   |
| 2.4.2 | Verificare che gli input che violano le politiche ricevano rifiuti standardizzati o completamenti sicuri, in modo che non si propaghino alle chiamate LLM a valle.                                            |    1    |  D/V  |
| 2.4.3 | Verificare che il modello di screening o l'insieme di regole venga riaddestrato o aggiornato almeno ogni trimestre, integrando i pattern di jailbreak o di elusione delle policy recentemente osservati.      |    2    |   D   |
| 2.4.4 | Verifica che il filtraggio rispetti le politiche specifiche dell'utente (età, vincoli legali regionali) tramite regole basate su attributi risolte al momento della richiesta.                                |    2    |   D   |
| 2.4.5 | Verifica che i log di screening includano punteggi di confidenza del classificatore e tag di categoria delle politiche per la correlazione SOC e la riproduzione futura da parte del red-team.                |    3    |   V   |

---

## C2.5 Limitazione della velocità di input e prevenzione degli abusi

Gli sviluppatori dovrebbero prevenire abusi, esaurimento delle risorse e attacchi automatizzati contro i sistemi di IA limitando i tassi di input e rilevando schemi di utilizzo anomali.

|   #   | Descrizione                                                                                                                           | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 2.5.1 | Verificare che i limiti di velocità per utente, per IP e per chiave API siano applicati a tutti gli endpoint di input.                |    1    |  D/V  |
| 2.5.2 | Verifica che i limiti di picco e sostenuti della frequenza delle richieste siano tarati per prevenire DoS e attacchi di forza bruta.  |    2    |  D/V  |
| 2.5.3 | Verifica che schemi di utilizzo anomali (ad es. richieste a raffica, inondazione di input) scatenino blocchi automatici o escalation. |    2    |  D/V  |
| 2.5.4 | Verificare che i log di prevenzione degli abusi siano conservati e revisionati per individuare schemi di attacco emergenti.           |    3    |   V   |

---

## C2.6 Validazione multimodale degli input

I sistemi di IA dovrebbero includere una validazione robusta per input non testuali (immagini, audio, file) per prevenire l'iniezione, l'evasione o l'abuso delle risorse.

|   #   | Descrizione                                                                                                                               | Livello | Ruolo |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 2.6.1 | Verifica che tutti gli input non testuali (immagini, audio e file) siano validati per tipo, dimensione e formato prima dell'elaborazione. |    1    |   D   |
| 2.6.2 | Verifica che i file vengano scansionati per malware e payload steganografici prima dell'ingestione.                                       |    2    |  D/V  |
| 2.6.3 | Verifica che gli input di immagini e audio siano controllati per perturbazioni avversariali o schemi di attacco noti.                     |    2    |  D/V  |
| 2.6.4 | Verifica che i fallimenti della convalida degli input multimodali siano registrati e che vengano attivati avvisi per l’indagine.          |    3    |   V   |

---

## C2.7 Provenienza degli input e attribuzione

I sistemi di IA dovrebbero supportare la verifica, il tracciamento degli abusi e la conformità monitorando e etichettando l'origine di tutti gli input degli utenti.

|   #   | Descrizione                                                                                                                                                         | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 2.7.1 | Verifica che tutti gli input degli utenti siano contrassegnati con metadati (ID utente, sessione, fonte, marca temporale, indirizzo IP) al momento dell’ingestione. |    1    |  D/V  |
| 2.7.2 | Verificare che i metadati di provenienza siano mantenuti e auditabili per tutti gli input elaborati.                                                                |    2    |  D/V  |
| 2.7.3 | Verifica che le fonti di input anomale o non affidabili siano contrassegnate e soggette a un controllo potenziato o al blocco.                                      |    2    |  D/V  |

---

## C2.8 Rilevamento adattivo delle minacce in tempo reale

Gli sviluppatori dovrebbero utilizzare sistemi avanzati di rilevamento delle minacce per l'IA che si adattano a nuovi schemi di attacco e forniscono protezione in tempo reale con corrispondenza di schemi compilata.

|   #   | Descrizione                                                                                                                                                                                                                                 | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 2.8.1 | Verifica che i pattern di rilevamento delle minacce siano compilati in motori di espressioni regolari ottimizzati per un filtraggio in tempo reale ad alte prestazioni, con un impatto minimo sulla latenza.                                |    1    |  D/V  |
| 2.8.2 | Verifica che i sistemi di rilevamento delle minacce mantengano librerie di pattern separate per diverse categorie di minaccia (iniezione di prompt, contenuto dannoso, dati sensibili, comandi di sistema).                                 |    1    |  D/V  |
| 2.8.3 | Verifica che il rilevamento adattivo delle minacce integri modelli di apprendimento automatico che aggiornano la sensibilità alle minacce in base alla frequenza degli attacchi e ai tassi di successo.                                     |    2    |  D/V  |
| 2.8.4 | Verifica che i flussi di threat intelligence in tempo reale aggiornino automaticamente le librerie di pattern con nuove firme di attacco e IoCs (Indicatori di compromissione).                                                             |    2    |  D/V  |
| 2.8.5 | Verifica che i tassi di falsi positivi nel rilevamento delle minacce siano monitorati costantemente e che la specificità dei modelli di rilevamento sia regolata automaticamente per minimizzare l'interferenza con i casi d'uso legittimi. |    3    |  D/V  |
| 2.8.6 | Verifica che l’analisi contestuale delle minacce prenda in considerazione la fonte di input, i modelli di comportamento dell’utente e la cronologia della sessione per migliorare l’accuratezza del rilevamento.                            |    3    |  D/V  |
| 2.8.7 | Verifichi che le metriche delle prestazioni del rilevamento delle minacce siano monitorate e ottimizzate in tempo reale.                                                                                                                    |    3    |  D/V  |

---

## C2.9 Multi-Modal Pipeline di Validazione della Sicurezza Multimodale

Gli sviluppatori dovrebbero fornire una validazione della sicurezza per testo, immagine, audio e altre modalità di input dell'IA, con tipologie specifiche di rilevamento delle minacce e di isolamento delle risorse.

|   #   | Descrizione                                                                                                                                                                                                                                                                        | Livello | Ruolo |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 2.9.1 | Verifica che ogni modalità di input abbia validatori di sicurezza dedicati con schemi di minaccia documentati (testo: iniezione di prompt, immagini: steganografia, audio: attacchi allo spettrogramma) e soglie di rilevamento.                                                   |    1    |  D/V  |
| 2.9.2 | Verifica che gli input multimodali siano elaborati in sandbox isolati con limiti di risorse definiti (memoria, CPU, tempo di elaborazione) specifici per ciascun tipo di modalità e documentati nelle politiche di sicurezza.                                                      |    2    |  D/V  |
| 2.9.3 | Verifica che il rilevamento cross-modale degli attacchi identifichi attacchi coordinati che si estendono su più tipi di input (ad es., payload steganografici in immagini combinati con l'iniezione di prompt nel testo) mediante regole di correlazione e generazione di allarmi. |    2    |  D/V  |
| 2.9.4 | Verificare che i fallimenti della validazione multimodale attivino una registrazione dettagliata che includa tutte le modalità di input, i risultati della validazione, i punteggi di minaccia e l'analisi di correlazione con formati di log strutturati per l'integrazione SIEM. |    3    |  D/V  |
| 2.9.5 | Verifica che i classificatori di contenuto specifici per modalità siano aggiornati secondo i programmi documentati (almeno ogni trimestre) con nuovi schemi di minaccia, esempi avversariali e benchmark delle prestazioni mantenuti al di sopra delle soglie di base.             |    3    |  D/V  |

---

## Riferimenti

* [LLM01:2025 Prompt Injection – OWASP Top 10 for LLM & Generative AI Security](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)
* [Generative AI's Biggest Security Flaw Is Not Easy to Fix](https://www.wired.com/story/generative-ai-prompt-injection-hacking)
* [Many-shot jailbreaking \ Anthropic](https://www.anthropic.com/research/many-shot-jailbreaking)
* [$PDF$ OpenAI GPT-4.5 System Card](https://cdn.openai.com/gpt-4-5-system-card-2272025.pdf)
* [Notebook for the CheckThat Lab at CLEF 2024](https://ceur-ws.org/Vol-3740/paper-53.pdf)
* [Mitigate jailbreaks and prompt injections – Anthropic](https://docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/mitigate-jailbreaks)
* [Chapter 3 MITRE ATT\&CK – Adversarial Model Analysis](https://ama.drwhy.ai/mitre-attck.html)
* [OWASP Top 10 for LLM Applications 2025 – WorldTech IT](https://wtit.com/blog/2025/04/17/owasp-top-10-for-llm-applications-2025/)
* [OWASP Machine Learning Security Top Ten](https://owasp.org/www-project-machine-learning-security-top-10/)
* [Few words about AI Security – Jussi Metso](https://www.jussimetso.com/index.php/2024/09/28/few-words-about-ai-security/)
* [How To Ensure LLM Output Adheres to a JSON Schema | Modelmetry](https://modelmetry.com/blog/how-to-ensure-llm-output-adheres-to-a-json-schema)
* [Easily enforcing valid JSON schema following – API](https://community.openai.com/t/feature-request-function-calling-easily-enforcing-valid-json-schema-following/263515?utm_source)
* [AI Safety + Cybersecurity R\&D Tracker – Fairly AI](https://www.fairly.ai/blog/ai-cybersecurity-tracker)
* [Anthropic makes 'jailbreak' advance to stop AI models producing harmful results](https://www.ft.com/content/cf11ebd8-aa0b-4ed4-945b-a5d4401d186e)
* [Pattern matching filter rules - IBM](https://www.ibm.com/docs/ssw_aix_71/security/intrusion_pattern_matching_filter_rules.html)
* [Real-time Threat Detection](https://www.darktrace.com/cyber-ai-glossary/real-time-threat-detection)

