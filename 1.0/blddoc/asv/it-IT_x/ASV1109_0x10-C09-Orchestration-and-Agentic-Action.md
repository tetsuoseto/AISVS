# 9 Orchestrazione Autonoma & Azione Agentica Sicurezza

## Obiettivo di controllo

Garantire che i sistemi IA autonomi o multiagente possano eseguire azioni solo se espressamente destinate, autenticabili, auditabili e entro soglie di costo e rischio definite. Questo protegge contro minacce quali compromissione di un sistema autonomo, uso improprio degli strumenti, rilevamento del ciclo dell’agente, dirottamento delle comunicazioni, falsificazione dell’identità, manipolazione di sciami e manipolazione delle intenzioni.

---

## 9.1 Pianificazione dei compiti dell'agente e budget di ricorsione

Limitare i piani ricorsivi e imporre punti di controllo umani per azioni privilegiate.

|   #   | Descrizione                                                                                                                                                                                                                    | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 9.1.1 | Verifichi che la profondità massima di ricorsione, l'ampiezza della ricerca, il tempo reale di esecuzione, i token e il costo monetario per l'esecuzione dell'agente siano configurati centralmente e versionati.              |    1    |  D/V  |
| 9.1.2 | Verifichi che le azioni privilegiate o irreversibili (ad es., commit di codice, trasferimenti finanziari) richiedano un'approvazione esplicita da parte di un essere umano tramite un canale auditabile prima dell'esecuzione. |    1    |  D/V  |
| 9.1.3 | Verifica che i monitor delle risorse in tempo reale attivino l'interruzione del circuit breaker non appena viene superata una qualsiasi soglia di budget, interrompendo ulteriori espansioni delle attività.                   |    2    |   D   |
| 9.1.4 | Verificare che gli eventi del circuit-breaker siano registrati con l'ID dell'agente, la condizione di attivazione e lo stato del piano acquisito per la revisione forense.                                                     |    2    |  D/V  |
| 9.1.5 | Verificare che i test di sicurezza includano scenari di esaurimento del budget e di esecuzione incontrollata del piano, confermando una fermata sicura senza perdita di dati.                                                  |    3    |   V   |
| 9.1.6 | Verifica che le politiche di budget siano espresse come policy-as-code e applicate in CI/CD per bloccare la deriva di configurazione.                                                                                          |    3    |   D   |

---

## 9.2 Sandbox dei plugin degli strumenti

Isolare le interazioni tra gli strumenti per prevenire l'accesso non autorizzato al sistema o l'esecuzione di codice.

|   #   | Descrizione                                                                                                                                                                                                                      | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.2.1 | Verifica che ogni strumento o plug-in venga eseguito all'interno di una sandbox a livello di sistema operativo, contenitore o WASM, con politiche di privilegio minimo per il sistema di file, la rete e le chiamate di sistema. |    1    |  D/V  |
| 9.2.2 | Verificare che i limiti delle risorse della sandbox (CPU, memoria, disco, uscita di rete) e i timeout di esecuzione siano applicati e registrati.                                                                                |    1    |  D/V  |
| 9.2.3 | Verificare che i binari degli strumenti o i descrittori siano firmati digitalmente; le firme vengano verificate prima del caricamento.                                                                                           |    2    |  D/V  |
| 9.2.4 | Verifica che la telemetria della sandbox venga inviata a un SIEM; anomalie (ad es., tentativi di connessioni in uscita) generino allarmi.                                                                                        |    2    |   V   |
| 9.2.5 | Verificare che i plugin ad alto rischio siano sottoposti a una revisione della sicurezza e a test di penetrazione prima della messa in produzione.                                                                               |    3    |   V   |
| 9.2.6 | Verifica che i tentativi di fuga dalla sandbox siano bloccati automaticamente e che il plugin incriminato sia messo in quarantena in attesa di un'indagine.                                                                      |    3    |  D/V  |

---

## 9.3 Loop Autonomo & Vincolo sui Costi

Rileva e interrompi la ricorsione non controllata tra agenti e le esplosioni di costo.

|   #   | Descrizione                                                                                                                                               | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.3.1 | Verifica che le chiamate tra agenti includano un limite di hop o TTL che il runtime decrementa e impone.                                                  |    1    |  D/V  |
| 9.3.2 | Verifica che gli agenti mantengano un identificatore univoco del grafo di invocazione per individuare auto-invocazione o schemi ciclici.                  |    2    |   D   |
| 9.3.3 | Verifica che i contatori cumulativi di unità di calcolo e di spesa siano tracciati per ogni catena di richieste; superare il limite interrompe la catena. |    2    |  D/V  |
| 9.3.4 | Verificare che l’analisi formale o il model checking dimostri l’assenza di ricorsione non vincolata nei protocolli degli agenti.                          |    3    |   V   |
| 9.3.5 | Verificare che gli eventi di terminazione del ciclo generino avvisi e alimentino metriche di miglioramento continuo.                                      |    3    |   D   |

---

## 9.4 Protezione a livello di protocollo contro l'uso improprio

Canali di comunicazione sicuri tra agenti e sistemi esterni per prevenire il dirottamento o la manomissione.

|   #   | Descrizione                                                                                                                                   | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.4.1 | Verifica che tutti i messaggi agente-a-strumento e agente-a-agente siano autenticati (ad es. TLS reciproco o JWT) e crittografati end-to-end. |    1    |  D/V  |
| 9.4.2 | Verifica che gli schemi siano validati in modo rigoroso e che i campi sconosciuti o i messaggi malformati vengano rifiutati.                  |    1    |   D   |
| 9.4.3 | Verifica che i controlli di integrità (MAC o firme digitali) coprano l'intero payload del messaggio, inclusi i parametri dello strumento.     |    2    |  D/V  |
| 9.4.4 | Verifica che la protezione contro il replay (nonce o finestre temporali) sia applicata a livello di protocollo.                               |    2    |   D   |
| 9.4.5 | Verificare che le implementazioni dei protocolli subiscano fuzzing e analisi statica per vulnerabilità di iniezione o deserializzazione.      |    3    |   V   |

---

## 9.5 Identità dell'agente e prova di manomissione

Assicurarsi che le azioni siano attribuibili e che le modifiche siano rilevabili.

|   #   | Descrizione                                                                                                                             | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.5.1 | Verifica che ogni istanza dell'agente possegga un'identità crittografica unica (coppia di chiavi o credenziale radicata nell'hardware). |    1    |  D/V  |
| 9.5.2 | Verifica che tutte le azioni dell'agente siano firmate e datate; i registri includono la firma per non ripudio.                         |    2    |  D/V  |
| 9.5.3 | Verificare che i log antimanomissione siano archiviati su un supporto append-only o write-once.                                         |    2    |   V   |
| 9.5.4 | Verificare che le chiavi di identità ruotino secondo una pianificazione definita e in presenza di indicatori di compromissione.         |    3    |   D   |
| 9.5.5 | Verifica che i tentativi di spoofing o di conflitto di chiavi attivino immediatamente la quarantena dell'agente interessato.            |    3    |  D/V  |

---

## 9.6 Riduzione del rischio dello sciame di agenti multipli

Ridurre i rischi associati al comportamento collettivo tramite isolamento e modellazione formale della sicurezza.

|   #   | Descrizione                                                                                                                                        | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.6.1 | Verifica che gli agenti operanti in diversi domini di sicurezza vengano eseguiti in sandbox di runtime isolati o segmenti di rete isolati.         |    1    |  D/V  |
| 9.6.2 | Verifica che i comportamenti dello sciame siano modellati e verificati formalmente per la vivacità e la sicurezza prima della messa in produzione. |    3    |   V   |
| 9.6.3 | Verificare che i monitor di esecuzione rilevino modelli pericolosi emergenti (ad es. oscillazioni, interblocchi) e avviino azioni correttive.      |    3    |   D   |

---

## 9.7 Autenticazione / Autorizzazione di utenti e strumenti

Implementa controlli di accesso robusti per ogni azione attivata dall'agente.

|   #   | Descrizione                                                                                                                                                  | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 9.7.1 | Verificare che gli agenti si autentichino come principali di prima classe verso i sistemi a valle, senza riutilizzare mai le credenziali dell'utente finale. |    1    |  D/V  |
| 9.7.2 | Verifica che le politiche di autorizzazione a granularità fine limitino quali strumenti un agente può invocare e quali parametri può fornire.                |    2    |   D   |
| 9.7.3 | Verificare che i controlli sui privilegi vengano rivalutati ad ogni chiamata (autorizzazione continua), non solo all'avvio della sessione.                   |    2    |   V   |
| 9.7.4 | Verificare che i privilegi delegati scadano automaticamente e richiedano nuovamente il consenso dopo la scadenza o una modifica dell'ambito.                 |    3    |   D   |

---

## 9.8 Sicurezza delle comunicazioni tra agenti

Crittografa e proteggi l'integrità di tutti i messaggi tra agenti per contrastare intercettazioni e manomissioni.

|   #   | Descrizione                                                                                                                                                                | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.8.1 | Verificare che l'autenticazione reciproca e la cifratura con segretezza perfetta in avanti (ad es. TLS 1.3) siano obbligatorie per i canali dell'agente.                   |    1    |  D/V  |
| 9.8.2 | Verifica che l'integrità del messaggio e l'origine siano verificate prima dell'elaborazione; in caso di fallimento, vengano generati avvisi e il messaggio venga scartato. |    1    |   D   |
| 9.8.3 | Verifica che i metadati di comunicazione (marcatori temporali, numeri di sequenza) siano registrati per supportare la ricostruzione forense.                               |    2    |  D/V  |
| 9.8.4 | Verificare che la verifica formale o il model checking confermino che le macchine a stati del protocollo non possano essere portate in stati non sicuri.                   |    3    |   V   |

---

## 9.9 Verifica dell'intento e applicazione dei vincoli

Verifica che le azioni dell'agente siano allineate all'intento dichiarato dall'utente e ai vincoli di sistema.

|   #   | Descrizione                                                                                                                                                                                | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 9.9.1 | Verifica che i risolutori di vincoli pre-esecuzione controllino le azioni proposte rispetto alle regole di sicurezza e alle policy codificate.                                             |    1    |   D   |
| 9.9.2 | Verifica che le azioni ad alto impatto (finanziarie, distruttive, sensibili alla privacy) richiedano una conferma esplicita dell'intento da parte dell'utente che ha avviato l'azione.     |    2    |  D/V  |
| 9.9.3 | Verificare che i controlli post-condizione confermino che le azioni completate hanno raggiunto gli effetti previsti senza effetti collaterali; in caso di discrepanze, scatta il rollback. |    2    |   V   |
| 9.9.4 | Verifichi che i metodi formali (ad es. model checking, dimostrazione di teoremi) o i test basati sulle proprietà dimostrino che i piani dell'agente soddisfino tutti i vincoli dichiarati. |    3    |   V   |
| 9.9.5 | Verifica che gli incidenti di intent-mismatch o di constraint-violation alimentino cicli di continuous-improvement e condivisione di threat-intel.                                         |    3    |   D   |

---

## 9.10 Strategia di ragionamento degli agenti: sicurezza

Selezione e esecuzione sicure di diverse strategie di ragionamento, tra cui ReAct, Chain-of-Thought e Tree-of-Thoughts.

|   #    | Descrizione                                                                                                                                                                                                                                                                  | Livello | Ruolo |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.10.1 | Verifica che la selezione della strategia di ragionamento si basi su criteri deterministici (complessità dell'input, tipo di compito, contesto di sicurezza) e che input identici producano selezioni di strategia identiche all'interno dello stesso contesto di sicurezza. |    1    |  D/V  |
| 9.10.2 | Verifica che ogni strategia di ragionamento (ReAct, Chain-of-Thought, Tree-of-Thoughts) abbia una validazione dedicata dell'input, una sanitizzazione dell'output e limiti di tempo di esecuzione specifici al suo approccio cognitivo.                                      |    1    |  D/V  |
| 9.10.3 | Verifica che le transizioni della strategia di ragionamento siano registrate con contesto completo, incluse le caratteristiche dell'input, i valori dei criteri di selezione e i metadati di esecuzione, per la ricostruzione della traccia di audit.                        |    2    |  D/V  |
| 9.10.4 | Verifica che il ragionamento ad albero dei pensieri includa meccanismi di potatura dei rami che terminano l'esplorazione quando vengono rilevate violazioni delle politiche, limiti delle risorse o confini di sicurezza.                                                    |    2    |  D/V  |
| 9.10.5 | Verifica che i cicli ReAct (Reason-Act-Observe) includano punti di controllo di validazione in ogni fase: verifica dei passaggi di ragionamento, autorizzazione delle azioni e sanitizzazione delle osservazioni prima di procedere.                                         |    2    |  D/V  |
| 9.10.6 | Verifica che le metriche delle prestazioni della strategia di ragionamento (tempo di esecuzione, utilizzo delle risorse, qualità dell'output) siano monitorate con avvisi automatici quando le metriche si discostano dai limiti configurati.                                |    3    |  D/V  |
| 9.10.7 | Verifica che gli approcci di ragionamento ibridi che combinano diverse strategie mantengano la validazione degli input e i vincoli di output di tutte le strategie costituenti, senza aggirare alcun controllo di sicurezza.                                                 |    3    |  D/V  |
| 9.10.8 | Verifica che i test di sicurezza della strategia di ragionamento includano fuzzing con input malformati, prompt avversari progettati per costringere un cambio di strategia e test delle condizioni al contorno per ciascun approccio cognitivo.                             |    3    |  D/V  |

---

## 9.11 Gestione dello stato del ciclo di vita dell'agente e della sicurezza

Inizializzazione sicura dell'agente, transizioni di stato e terminazione con tracce di audit crittografiche e procedure di recupero definite.

|   #    | Descrizione                                                                                                                                                                                                                                                                                                          | Livello | Ruolo |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.11.1 | Verifica che l'inizializzazione dell'agente includa la creazione dell'identità crittografica con credenziali protette dall'hardware e registri di audit all'avvio immutabili contenenti l'ID dell'agente, marca temporale, hash della configurazione e parametri di inizializzazione.                                |    1    |  D/V  |
| 9.11.2 | Verificare che le transizioni di stato dell'agente siano firmate crittograficamente, marcate temporalmente e registrate con contesto completo, inclusi gli eventi scatenanti, l'hash dello stato precedente, l'hash dello stato nuovo e le verifiche di sicurezza eseguite.                                          |    2    |  D/V  |
| 9.11.3 | Verificare che le procedure di spegnimento dell'agente includano la cancellazione sicura della memoria mediante cancellazione crittografica o sovrascrittura multipassi, la revoca delle credenziali con notifica all'autorità certificante e la generazione di certificati di terminazione a prova di manomissione. |    2    |  D/V  |
| 9.11.4 | Verificare che i meccanismi di recupero degli agenti convalidino l'integrità dello stato utilizzando checksum crittografici (SHA-256 minimo) e tornino a stati noti e affidabili quando venga rilevata la corruzione, con avvisi automatizzati e requisiti di approvazione manuale.                                  |    3    |  D/V  |
| 9.11.5 | Verifica che i meccanismi di persistenza degli agenti cifrino i dati di stato sensibili con chiavi AES-256 per agente e implementino la rotazione sicura delle chiavi su intervalli configurabili (massimo 90 giorni) con distribuzione senza tempi di inattività.                                                   |    3    |  D/V  |

---

## 9.12 Quadro di Sicurezza per l'Integrazione degli Strumenti

Controlli di sicurezza per il caricamento dinamico degli strumenti, l'esecuzione e la convalida dei risultati, con processi di valutazione del rischio e di approvazione definiti.

|   #    | Descrizione                                                                                                                                                                                                                                                                                               | Livello | Ruolo |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.12.1 | Verifica che i descrittori degli strumenti includano metadati di sicurezza che specificano privilegi richiesti (lettura/scrittura/esecuzione), livelli di rischio (basso/medio/alto), limiti delle risorse (CPU, memoria, rete) e requisiti di validazione documentati nei manifest degli strumenti.      |    1    |  D/V  |
| 9.12.2 | Verifica che i risultati dell'esecuzione degli strumenti siano validati rispetto agli schemi attesi (JSON Schema, XML Schema) e alle politiche di sicurezza (sanitizzazione dell'output, classificazione dei dati) prima dell'integrazione con limiti di timeout e procedure di gestione degli errori.    |    1    |  D/V  |
| 9.12.3 | Verifica che i log di interazione degli strumenti includano un contesto di sicurezza dettagliato, tra cui l'uso dei privilegi, i modelli di accesso ai dati, il tempo di esecuzione, il consumo di risorse e i codici di ritorno, con logging strutturato per l'integrazione SIEM.                        |    2    |  D/V  |
| 9.12.4 | Verifichi che i meccanismi di caricamento dinamico degli strumenti validino le firme digitali utilizzando l'infrastruttura PKI e implementino protocolli di caricamento sicuri con isolamento sandbox e verifica delle autorizzazioni prima dell'esecuzione.                                              |    2    |  D/V  |
| 9.12.5 | Verificare che le valutazioni di sicurezza dello strumento vengano attivate automaticamente per le nuove versioni, con gate di approvazione obbligatori che includano analisi statica, test dinamici e revisione da parte del team di sicurezza, con criteri di approvazione documentati e requisiti SLA. |    3    |  D/V  |

---

### Riferimenti

* [MITRE ATLAS tactics ML09](https://atlas.mitre.org/)
* [Circuit-breaker research for AI agents — Zou et al., 2024](https://arxiv.org/abs/2406.04313)
* [Trend Micro analysis of sandbox escapes in AI agents — Park, 2025](https://www.trendmicro.com/vinfo/us/security/news/cybercrime-and-digital-threats/unveiling-ai-agent-vulnerabilities-code-execution)
* [Auth0 guidance on human-in-the-loop authorization for agents — Martinez, 2025](https://auth0.com/blog/secure-human-in-the-loop-interactions-for-ai-agents/)
* [Medium deep-dive on MCP & A2A protocol hijacking — ForAISec, 2025](https://medium.com/%40foraisec/security-analysis-potential-ai-agent-hijacking-via-mcp-and-a2a-protocol-insights-cd1ec5e6045f)
* [Rapid7 fundamentals on spoofing attack prevention — 2024](https://www.rapid7.com/fundamentals/spoofing-attacks/)
* [Imperial College verification of swarm systems — Lomuscio et al.](https://sail.doc.ic.ac.uk/projects/swarms/)
* [NIST AI Risk Management Framework 1.0, 2023](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [WIRED security briefing on encryption best practices, 2024](https://www.wired.com/story/encryption-apps-chinese-telecom-hacking-hydra-russia-exxon)
* [OWASP Top 10 for LLM Applications, 2025](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Comprehensive Vulnerability Analysis is Necessary for Trustworthy LLM-MAS](https://arxiv.org/html/2506.01245v1)
* [How Is LLM Reasoning Distracted by Irrelevant Context?
  An Analysis Using a Controlled Benchmark](https://www.arxiv.org/pdf/2505.18761)
* [Large Language Model Sentinel: LLM Agent for Adversarial Purification](https://arxiv.org/pdf/2405.20770)
* [Securing Agentic AI: A Comprehensive Threat Model and Mitigation Framework for Generative AI Agents](https://arxiv.org/html/2504.19956v2)

