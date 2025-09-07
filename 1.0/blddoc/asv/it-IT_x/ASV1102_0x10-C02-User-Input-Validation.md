# Validazione dell'input utente C2

## Obiettivo di Controllo

La convalida robusta dell'input dell'utente è una difesa di prima linea contro alcuni degli attacchi più dannosi ai sistemi di intelligenza artificiale. Gli attacchi di iniezione di prompt possono sovrascrivere le istruzioni di sistema, divulgare dati sensibili o indirizzare il modello verso comportamenti non consentiti. A meno che non siano presenti filtri dedicati e gerarchie di istruzioni, la ricerca dimostra che i jailbreak "multi-shot" che sfruttano finestre di contesto molto lunghe saranno efficaci. Inoltre, attacchi sottili di perturbazione adversariale—come sostituzioni di omoglifi o leetspeak—possono silenziosamente modificare le decisioni di un modello.

---

## C2.1 Difesa contro l'iniezione di prompt

L'iniezione di prompt è uno dei principali rischi per i sistemi di intelligenza artificiale. Le difese contro questa tattica utilizzano una combinazione di filtri statici basati su pattern, classificatori dinamici e l'applicazione gerarchica delle istruzioni.

|   #   | Descrizione                                                                                                                                                                                                                                                     | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 2.1.1 | Verificare che gli input dell'utente vengano filtrati confrontandoli con una libreria continuamente aggiornata di modelli noti di iniezione di prompt (parole chiave di jailbreak, "ignora precedente", catene di gioco di ruolo, attacchi indiretti HTML/URL). |    1    |  D/V  |
| 2.1.2 | Verificare che il sistema imponga una gerarchia di istruzioni in cui i messaggi di sistema o dello sviluppatore sovrascrivono le istruzioni dell'utente, anche dopo l'espansione della finestra di contesto.                                                    |    1    |  D/V  |
| 2.1.3 | Verificare che i test di valutazione adversariale (ad esempio, prompt "many-shot" del Red Team) siano eseguiti prima di ogni rilascio del modello o del template di prompt, con soglie di successo e blocchi automatici per regressioni.                        |    2    |  D/V  |
| 2.1.4 | Verificare che i prompt provenienti da contenuti di terze parti (pagine web, PDF, email) siano sanificati in un contesto di analisi isolato prima di essere concatenati nel prompt principale.                                                                  |    2    |   D   |
| 2.1.5 | Verificare che tutti gli aggiornamenti delle regole di filtro del prompt, le versioni dei modelli di classificazione e le modifiche alla lista di blocco siano controllati tramite versionamento e verificabili.                                                |    3    |  D/V  |

---

## C2.2 Resistenza agli esempi avversari

I modelli di Elaborazione del Linguaggio Naturale (NLP) sono ancora vulnerabili a perturbazioni sottili a livello di caratteri o parole che gli esseri umani spesso non percepiscono, ma che i modelli tendono a classificare in modo errato.

|   #   | Descrizione                                                                                                                                                                                                                     | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 2.2.1 | Verificare che le operazioni di normalizzazione di base dell'input (Unicode NFC, mappatura degli omoglifici, rimozione degli spazi bianchi) vengano eseguite prima della tokenizzazione.                                        |    1    |   D   |
| 2.2.2 | Verificare che il rilevamento statistico delle anomalie segnali input con distanza di modifica insolitamente alta rispetto alle norme linguistiche, token ripetuti eccessivi o distanze di embedding anomale.                   |    2    |  D/V  |
| 2.2.3 | Verificare che la pipeline di inferenza supporti varianti di modelli rinforzati con addestramento avversario opzionale o livelli di difesa (ad esempio, randomizzazione, distillazione difensiva) per endpoint ad alto rischio. |    2    |   D   |
| 2.2.4 | Verificare che gli input sospetti di tipo adversariale siano messi in quarantena e registrati con il payload completo (dopo la rimozione delle informazioni personali identificabili - PII).                                    |    2    |   V   |
| 2.2.5 | Verificare che le metriche di robustezza (tasso di successo delle suite di attacchi conosciuti) vengano monitorate nel tempo e che le regressioni attivino un blocco per il rilascio.                                           |    3    |  D/V  |

---

## C2.3 Validazione di Schema, Tipo e Lunghezza

Gli attacchi di intelligenza artificiale che utilizzano input malformati o sovradimensionati possono causare errori di parsing, fuoriuscita di prompt tra i campi e esaurimento delle risorse. L'applicazione rigorosa dello schema è inoltre un prerequisito quando si eseguono chiamate a strumenti deterministici.

|   #   | Descrizione                                                                                                                                                                                                               | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 2.3.1 | Verificare che ogni endpoint di chiamata API o funzione definisca uno schema di input esplicito (JSON Schema, Protobuf o equivalente multimodale) e che gli input vengano convalidati prima dell'assemblaggio del prompt. |    1    |   D   |
| 2.3.2 | Verificare che gli input che superano i limiti massimi di token o byte vengano rifiutati con un errore sicuro e mai troncati silenziosamente.                                                                             |    1    |  D/V  |
| 2.3.3 | Verificare che i controlli di tipo (es. intervalli numerici, valori enum, tipi MIME per immagini/audio) siano applicati lato server, non solo nel codice client.                                                          |    2    |  D/V  |
| 2.3.4 | Verificare che i validatori semantici (ad esempio, JSON Schema) vengano eseguiti in tempo costante per prevenire attacchi DoS algoritmici.                                                                                |    2    |   D   |
| 2.3.5 | Verificare che i fallimenti di convalida vengano registrati con frammenti di payload oscurati e codici di errore inequivocabili per facilitare la gestione della sicurezza.                                               |    3    |   V   |

---

## C2.4 Controllo dei Contenuti e delle Politiche

Gli sviluppatori dovrebbero essere in grado di rilevare prompt sintatticamente validi che richiedono contenuti non consentiti (come istruzioni illecite, discorsi di odio e testi protetti da copyright) e poi impedire la loro diffusione.

|   #   | Descrizione                                                                                                                                                                                       | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 2.4.1 | Verificare che un classificatore di contenuti (zero shot o fine-tuned) valuti ogni input per violenza, autolesionismo, odio, contenuti sessuali e richieste illegali, con soglie configurabili.   |    1    |   D   |
| 2.4.2 | Verificare che gli input che violano le politiche ricevano rifiuti standardizzati o completamenti sicuri in modo che non vengano propagati a chiamate LLM successive.                             |    1    |  D/V  |
| 2.4.3 | Verificare che il modello di screening o il set di regole venga riqualificato/aggiornato almeno ogni trimestre, incorporando i nuovi schemi di jailbreak o di elusione delle policy osservati.    |    2    |   D   |
| 2.4.4 | Verificare che il filtro rispetti le politiche specifiche per l'utente (età, vincoli legali regionali) tramite regole basate su attributi risolte al momento della richiesta.                     |    2    |   D   |
| 2.4.5 | Verificare che i registri di screening includano i punteggi di fiducia del classificatore e le etichette della categoria di policy per la correlazione SOC e la riproduzione futura del red-team. |    3    |   V   |

---

## C2.5 Limitazione della velocità di input e prevenzione degli abusi

Gli sviluppatori dovrebbero prevenire abusi, esaurimento delle risorse e attacchi automatizzati contro i sistemi AI limitando i tassi di input e rilevando pattern di utilizzo anomali.

|   #   | Descrizione                                                                                                                                           | Livello | Ruolo |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 2.5.1 | Verificare che i limiti di velocità per utente, per IP e per chiave API siano applicati a tutti gli endpoint di input.                                |    1    |  D/V  |
| 2.5.2 | Verificare che i limiti di velocità burst e sostenuti siano regolati per prevenire attacchi DoS e di forza bruta.                                     |    2    |  D/V  |
| 2.5.3 | Verificare che modelli di utilizzo anomali (ad esempio, richieste rapide consecutive, flooding di input) attivino blocchi automatizzati o escalation. |    2    |  D/V  |
| 2.5.4 | Verificare che i registri di prevenzione degli abusi siano conservati e revisionati per individuare modelli emergenti di attacco.                     |    3    |   V   |

---

## C2.6 Validazione dell'Input Multi-Modale

I sistemi di intelligenza artificiale dovrebbero includere una convalida robusta per input non testuali (immagini, audio, file) per prevenire iniezioni, elusioni o abusi di risorse.

|   #   | Descrizione                                                                                                                                    | Livello | Ruolo |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 2.6.1 | Verificare che tutti gli input non testuali (immagini, audio, file) siano convalidati per tipo, dimensione e formato prima della elaborazione. |    1    |   D   |
| 2.6.2 | Verificare che i file siano sottoposti a scansione per malware e payload steganografici prima dell'ingestione.                                 |    2    |  D/V  |
| 2.6.3 | Verificare che gli input immagine/audio siano controllati per perturbazioni avversarie o modelli di attacco noti.                              |    2    |  D/V  |
| 2.6.4 | Verificare che i fallimenti di validazione dell'input multimodale vengano registrati e attivino allarmi per l'indagine.                        |    3    |   V   |

---

## C2.7 Origine e attribuzione dell'input

I sistemi di intelligenza artificiale dovrebbero supportare la verifica, il tracciamento degli abusi e la conformità monitorando e etichettando l’origine di tutti gli input degli utenti.

|   #   | Descrizione                                                                                                                                                  | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 2.7.1 | Verificare che tutti gli input degli utenti siano etichettati con metadati (ID utente, sessione, fonte, timestamp, indirizzo IP) al momento dell'ingestione. |    1    |  D/V  |
| 2.7.2 | Verificare che i metadati di provenienza siano conservati e verificabili per tutti gli input elaborati.                                                      |    2    |  D/V  |
| 2.7.3 | Verificare che le fonti di input anomale o non affidabili siano segnalate e soggette a un controllo più rigoroso o al blocco.                                |    2    |  D/V  |

---

## C2.8 Rilevamento Adattivo delle Minacce in Tempo Reale

Gli sviluppatori dovrebbero utilizzare sistemi avanzati di rilevamento delle minacce per l'IA che si adattino ai nuovi schemi di attacco e forniscano protezione in tempo reale mediante il confronto di pattern compilati.

|   #   | Descrizione                                                                                                                                                                                                                               | Livello | Ruolo |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 2.8.1 | Verificare che i modelli di rilevamento delle minacce siano compilati in motori regex ottimizzati per un filtraggio in tempo reale ad alte prestazioni con un impatto minimo sulla latenza.                                               |    1    |  D/V  |
| 2.8.2 | Verificare che i sistemi di rilevamento delle minacce mantengano librerie di pattern separate per diverse categorie di minacce (iniezione di prompt, contenuti dannosi, dati sensibili, comandi di sistema).                              |    1    |  D/V  |
| 2.8.3 | Verificare che il rilevamento delle minacce adattivo incorpori modelli di machine learning che aggiornano la sensibilità alle minacce in base alla frequenza e ai tassi di successo degli attacchi.                                       |    2    |  D/V  |
| 2.8.4 | Verificare che i feed di intelligence sulle minacce in tempo reale aggiornino automaticamente le librerie di pattern con nuove firme di attacco e IOC (Indicatori di Compromissione).                                                     |    2    |  D/V  |
| 2.8.5 | Verificare che i tassi di falsi positivi nella rilevazione delle minacce siano monitorati continuamente e che la specificità dei modelli venga automaticamente regolata per ridurre al minimo le interferenze con i casi d'uso legittimi. |    3    |  D/V  |
| 2.8.6 | Verifica che l'analisi contestuale delle minacce consideri la fonte dell'input, i modelli di comportamento degli utenti e la cronologia delle sessioni per migliorare la precisione del rilevamento.                                      |    3    |  D/V  |
| 2.8.7 | Verificare che le metriche di prestazione del rilevamento delle minacce (tasso di rilevamento, latenza di elaborazione, utilizzo delle risorse) siano monitorate e ottimizzate in tempo reale.                                            |    3    |  D/V  |

---

## C2.9 Pipeline di Validazione della Sicurezza Multi-Modale

Gli sviluppatori dovrebbero fornire la convalida della sicurezza per testo, immagini, audio e altre modalità di input AI con tipi specifici di rilevamento delle minacce e isolamento delle risorse.

|   #   | Descrizione                                                                                                                                                                                                                                                                          | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 2.9.1 | Verificare che ogni modalità di input abbia validatori di sicurezza dedicati con modelli di minaccia documentati (testo: iniezione di prompt, immagini: steganografia, audio: attacchi allo spettrogramma) e soglie di rilevamento.                                                  |    1    |  D/V  |
| 2.9.2 | Verificare che gli input multi-modali siano elaborati in sandbox isolate con limiti di risorse definiti (memoria, CPU, tempo di elaborazione) specifici per ogni tipo di modalità e documentati nelle politiche di sicurezza.                                                        |    2    |  D/V  |
| 2.9.3 | Verificare che il rilevamento degli attacchi cross-modali identifichi attacchi coordinati che coinvolgono più tipi di input (ad esempio, payload steganografici nelle immagini combinati con iniezioni di prompt nel testo) tramite regole di correlazione e generazione di allarmi. |    2    |  D/V  |
| 2.9.4 | Verificare che i fallimenti di convalida multimodale attivino una registrazione dettagliata, includendo tutte le modalità di input, i risultati della convalida, i punteggi di minaccia e l'analisi di correlazione con formati di log strutturati per l'integrazione SIEM.          |    3    |  D/V  |
| 2.9.5 | Verificare che i classificatori di contenuti specifici per modalità siano aggiornati secondo i programmi documentati (almeno ogni trimestre) con nuovi modelli di minacce, esempi avversari e che i benchmark di prestazione siano mantenuti al di sopra delle soglie di base.       |    3    |  D/V  |

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

