# 9 Orchestrazione Autonoma e Sicurezza dell'Azione Agente

## Obiettivo di Controllo

Garantire che i sistemi di intelligenza artificiale autonomi o multi-agente possano eseguire solo azioni che sono esplicitamente intenzionate, autenticate, verificabili e all’interno di limiti prestabiliti di costi e rischi. Questo protegge da minacce come il Compromesso del Sistema Autonomo, l’uso improprio degli Strumenti, il Rilevamento di Loop dell’Agente, il Dirottamento delle Comunicazioni, la Contraffazione dell’Identità, la Manipolazione dello Sciame e la Manipolazione delle Intenzioni.

---

## 9.1 Pianificazione dei compiti dell'agente e budget di ricorsione

Limitare i piani ricorsivi e imporre checkpoint umani per azioni privilegiate.

|   #   | Descrizione                                                                                                                                                                                                              | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 9.1.1 | Verificare che la profondità massima della ricorsione, la larghezza, il tempo di clock effettivo, i token e il costo monetario per esecuzione agente siano configurati centralmente e controllati tramite versionamento. |    1    |  D/V  |
| 9.1.2 | Verificare che le azioni privilegiate o irreversibili (ad esempio, commit di codice, trasferimenti finanziari) richiedano un'approvazione umana esplicita tramite un canale verificabile prima dell'esecuzione.          |    1    |  D/V  |
| 9.1.3 | Verificare che i monitor delle risorse in tempo reale attivino l'interruzione del circuito di sicurezza quando viene superata qualsiasi soglia del budget, interrompendo l'espansione ulteriore delle attività.          |    2    |   D   |
| 9.1.4 | Verificare che gli eventi del circuito di interruzione siano registrati con l'ID dell'agente, la condizione di attivazione e lo stato del piano acquisito per la revisione forense.                                      |    2    |  D/V  |
| 9.1.5 | Verificare che i test di sicurezza coprano gli scenari di esaurimento del budget e di esecuzione incontrollata del piano, confermando l'arresto sicuro senza perdita di dati.                                            |    3    |   V   |
| 9.1.6 | Verificare che le politiche di budget siano espresse come policy-as-code e applicate nel CI/CD per bloccare la deriva della configurazione.                                                                              |    3    |   D   |

---

## 9.2 Sandbox dei Plugin degli Strumenti

Isolare le interazioni con gli strumenti per prevenire l'accesso non autorizzato al sistema o l'esecuzione di codice.

|   #   | Descrizione                                                                                                                                                                                          | Livello | Ruolo |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.2.1 | Verifica che ogni tool/plugin venga eseguito all'interno di un sistema operativo, container o sandbox a livello WASM con politiche di minimo privilegio per file system, rete e chiamate di sistema. |    1    |  D/V  |
| 9.2.2 | Verificare che le quote delle risorse della sandbox (CPU, memoria, disco, uscita rete) e i timeout di esecuzione siano applicati e registrati.                                                       |    1    |  D/V  |
| 9.2.3 | Verificare che i file binari o i descrittori degli strumenti siano firmati digitalmente; le firme devono essere convalidate prima del caricamento.                                                   |    2    |  D/V  |
| 9.2.4 | Verificare che la telemetria della sandbox venga trasmessa a un SIEM; le anomalie (ad esempio, tentativi di connessioni in uscita) generano allarmi.                                                 |    2    |   V   |
| 9.2.5 | Verificare che i plugin ad alto rischio vengano sottoposti a revisione della sicurezza e test di penetrazione prima della distribuzione in produzione.                                               |    3    |   V   |
| 9.2.6 | Verificare che i tentativi di fuga dalla sandbox siano bloccati automaticamente e che il plugin offensivo venga messo in quarantena in attesa di indagine.                                           |    3    |  D/V  |

---

## 9.3 Ciclo Autonomo e Limite dei Costi

Rilevare e fermare la ricorsione incontrollata tra agenti e le esplosioni di costi.

|   #   | Descrizione                                                                                                                                                               | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.3.1 | Verificare che le chiamate tra agenti includano un limite di salto o TTL che il runtime decrementa e applica.                                                             |    1    |  D/V  |
| 9.3.2 | Verificare che gli agenti mantengano un ID unico per il grafo di invocazione per individuare auto-invocazioni o schemi ciclici.                                           |    2    |   D   |
| 9.3.3 | Verificare che i contatori cumulativi di unità di calcolo e spesa siano tracciati per catena di richiesta; il superamento del limite provoca l'interruzione della catena. |    2    |  D/V  |
| 9.3.4 | Verificare che l'analisi formale o il model checking dimostrino l'assenza di ricorsione non limitata nei protocolli degli agenti.                                         |    3    |   V   |
| 9.3.5 | Verificare che gli eventi di interruzione del ciclo generino avvisi e alimentino le metriche di miglioramento continuo.                                                   |    3    |   D   |

---

## 9.4 Protezione contro l'uso improprio a livello di protocollo

Canali di comunicazione sicuri tra agenti e sistemi esterni per prevenire dirottamenti o manipolazioni.

|   #   | Descrizione                                                                                                                                                     | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.4.1 | Verificare che tutti i messaggi da agente a strumento e da agente a agente siano autenticati (ad esempio, mutual TLS o JWT) e criptati end-to-end.              |    1    |  D/V  |
| 9.4.2 | Verificare che gli schemi siano strettamente validati; i campi sconosciuti o i messaggi malformati devono essere respinti.                                      |    1    |   D   |
| 9.4.3 | Verificare che i controlli di integrità (MAC o firme digitali) coprano l'intero payload del messaggio, inclusi i parametri degli strumenti.                     |    2    |  D/V  |
| 9.4.4 | Verificare che la protezione contro la ripetizione (nonce o finestre temporali) sia applicata a livello di protocollo.                                          |    2    |   D   |
| 9.4.5 | Verificare che le implementazioni del protocollo vengano sottoposte a fuzzing e analisi statica per individuare vulnerabilità di injection o deserializzazione. |    3    |   V   |

---

## 9.5 Identità dell'Agente e Prova di Manomissione

Garantire che le azioni siano attribuibili e le modifiche rilevabili.

|   #   | Descrizione                                                                                                                           | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.5.1 | Verificare che ogni istanza di agente possieda un’identità crittografica unica (coppia di chiavi o credenziale radicata in hardware). |    1    |  D/V  |
| 9.5.2 | Verificare che tutte le azioni degli agenti siano firmate e datate; i registri includono la firma per la non ripudiabilità.           |    2    |  D/V  |
| 9.5.3 | Verificare che i log a prova di manomissione siano archiviati in un supporto solo per aggiunte o scrittura unica.                     |    2    |   V   |
| 9.5.4 | Verificare che le chiavi di identità ruotino secondo un programma definito e in presenza di indicatori di compromissione.             |    3    |   D   |
| 9.5.5 | Verificare che i tentativi di spoofing o conflitto di chiavi attivino immediatamente la quarantena dell'agente interessato.           |    3    |  D/V  |

---

## 9.6 Riduzione del rischio con sciame multi-agente

Mitigare i rischi legati al comportamento collettivo attraverso l'isolamento e la modellazione formale della sicurezza.

|   #   | Descrizione                                                                                                                                         | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.6.1 | Verificare che gli agenti operanti in differenti domini di sicurezza vengano eseguiti in sandbox di runtime isolati o in segmenti di rete separati. |    1    |  D/V  |
| 9.6.2 | Verificare che i comportamenti dello sciame siano modellati e formalmente verificati per la vivacità e la sicurezza prima del dispiegamento.        |    3    |   V   |
| 9.6.3 | Verificare che i monitor di runtime rilevino schemi di pericolo emergenti (ad esempio, oscillazioni, deadlock) e avviino azioni correttive.         |    3    |   D   |

---

## 9.7 Autenticazione / Autorizzazione Utente e Strumento

Implementare controlli di accesso robusti per ogni azione attivata dall'agente.

|   #   | Descrizione                                                                                                                                                | Livello | Ruolo |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.7.1 | Verificare che gli agenti si autentichino come principali di prima classe ai sistemi downstream, senza mai riutilizzare le credenziali dell'utente finale. |    1    |  D/V  |
| 9.7.2 | Verificare che le politiche di autorizzazione a grana fine limitino quali strumenti un agente può invocare e quali parametri può fornire.                  |    2    |   D   |
| 9.7.3 | Verificare che i controlli di privilegio vengano rivalutati ad ogni chiamata (autorizzazione continua), non solo all'inizio della sessione.                |    2    |   V   |
| 9.7.4 | Verificare che i privilegi delegati scadano automaticamente e richiedano un nuovo consenso dopo il timeout o la modifica dell'ambito.                      |    3    |   D   |

---

## 9.8 Sicurezza della comunicazione agent-to-agent

Criptare e proteggere l'integrità di tutti i messaggi inter-agente per impedire intercettazioni e manomissioni.

|   #   | Descrizione                                                                                                                                              | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.8.1 | Verificare che l'autenticazione mutua e la crittografia a segreto perfetto in avanti (ad esempio TLS 1.3) siano obbligatorie per i canali agent.         |    1    |  D/V  |
| 9.8.2 | Verificare che l'integrità e l'origine del messaggio siano convalidate prima dell'elaborazione; i fallimenti generano avvisi e scartano il messaggio.    |    1    |   D   |
| 9.8.3 | Verificare che i metadati della comunicazione (timestamp, numeri di sequenza) siano registrati per supportare la ricostruzione forense.                  |    2    |  D/V  |
| 9.8.4 | Verificare che la verifica formale o il model checking confermino che le macchine a stati del protocollo non possano essere portate in stati non sicuri. |    3    |   V   |

---

## 9.9 Verifica dell'Intento e Applicazione dei Vincoli

Verifica che le azioni dell'agente siano in linea con l'intento dichiarato dall'utente e con i vincoli del sistema.

|   #   | Descrizione                                                                                                                                                                                        | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.9.1 | Verificare che i solver di vincoli pre-esecuzione controllino le azioni proposte rispetto alle regole di sicurezza e di policy codificate rigidamente.                                             |    1    |   D   |
| 9.9.2 | Verificare che le azioni ad alto impatto (finanziarie, distruttive, sensibili alla privacy) richiedano una conferma esplicita dell'intento da parte dell'utente che le avvia.                      |    2    |  D/V  |
| 9.9.3 | Verificare che i controlli delle post-condizioni confermino che le azioni completate abbiano raggiunto gli effetti previsti senza effetti collaterali; eventuali discrepanze attivano il rollback. |    2    |   V   |
| 9.9.4 | Verificare che i metodi formali (ad esempio, model checking, dimostrazione di teoremi) o i test basati su proprietà dimostrino che i piani degli agenti soddisfano tutti i vincoli dichiarati.     |    3    |   V   |
| 9.9.5 | Verificare che gli incidenti di disallineamento dell’intento o di violazione dei vincoli alimentino cicli di miglioramento continuo e condivisione delle informazioni sulle minacce.               |    3    |   D   |

---

## 9.10 Sicurezza della Strategia di Ragionamento dell'Agente

Selezione ed esecuzione sicura di diverse strategie di ragionamento, inclusi gli approcci ReAct, Chain-of-Thought e Tree-of-Thoughts.

|   #    | Descrizione                                                                                                                                                                                                                                                                  | Livello | Ruolo |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.10.1 | Verificare che la selezione della strategia di ragionamento utilizzi criteri deterministici (complessità dell’input, tipo di compito, contesto di sicurezza) e che input identici producano selezioni di strategia identiche all’interno dello stesso contesto di sicurezza. |    1    |  D/V  |
| 9.10.2 | Verifica che ogni strategia di ragionamento (ReAct, Chain-of-Thought, Tree-of-Thoughts) disponga di una validazione degli input dedicata, una sanificazione degli output e limiti di tempo di esecuzione specifici per il rispettivo approccio cognitivo.                    |    1    |  D/V  |
| 9.10.3 | Verificare che le transizioni della strategia di ragionamento siano registrate con contesto completo, inclusi le caratteristiche dell'input, i valori dei criteri di selezione e i metadati di esecuzione, per la ricostruzione della traccia di controllo.                  |    2    |  D/V  |
| 9.10.4 | Verificare che il ragionamento Tree-of-Thoughts includa meccanismi di potatura dei rami che interrompono l’esplorazione quando vengono rilevate violazioni di policy, limiti di risorse o confini di sicurezza.                                                              |    2    |  D/V  |
| 9.10.5 | Verificare che i cicli ReAct (Reason-Act-Observe) includano punti di controllo di convalida in ogni fase: verifica del passaggio di ragionamento, autorizzazione dell’azione e sanificazione dell’osservazione prima di procedere.                                           |    2    |  D/V  |
| 9.10.6 | Verificare che le metriche di prestazione della strategia di ragionamento (tempo di esecuzione, utilizzo delle risorse, qualità dell'output) siano monitorate con avvisi automatici quando le metriche si discostano oltre le soglie configurate.                            |    3    |  D/V  |
| 9.10.7 | Verificare che gli approcci di ragionamento ibrido che combinano più strategie mantengano la validazione dell'input e i vincoli di output di tutte le strategie costituenti senza bypassare alcun controllo di sicurezza.                                                    |    3    |  D/V  |
| 9.10.8 | Verificare che il testing di sicurezza della strategia di ragionamento includa il fuzzing con input malformati, prompt avversari progettati per forzare il cambio di strategia e il testing delle condizioni limite per ogni approccio cognitivo.                            |    3    |  D/V  |

---

## 9.11 Gestione dello Stato del Ciclo di Vita dell'Agente e Sicurezza

Inizializzazione sicura dell'agente, transizioni di stato e terminazione con tracciature di audit crittografiche e procedure di recupero definite.

|   #    | Descrizione                                                                                                                                                                                                                                                                                                               | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.11.1 | Verificare che l'inizializzazione dell'agente includa l'istituzione dell'identità crittografica con credenziali supportate da hardware e registri di audit di avvio immutabili contenenti ID agente, timestamp, hash di configurazione e parametri di inizializzazione.                                                   |    1    |  D/V  |
| 9.11.2 | Verificare che le transizioni di stato dell’agente siano firmate crittograficamente, con marcatura temporale e registrate con contesto completo, inclusi gli eventi scatenanti, l’hash dello stato precedente, l’hash del nuovo stato e le convalide di sicurezza eseguite.                                               |    2    |  D/V  |
| 9.11.3 | Verificare che le procedure di arresto dell'agente includano la cancellazione sicura della memoria mediante cancellazione crittografica o sovrascrittura a più passaggi, la revoca delle credenziali con notifica all'autorità di certificazione e la generazione di certificati di terminazione a prova di manomissione. |    2    |  D/V  |
| 9.11.4 | Verificare che i meccanismi di recupero dell'agente convalidino l'integrità dello stato utilizzando checksum crittografici (minimo SHA-256) e ripristinino stati noti come corretti quando viene rilevata una corruzione, con avvisi automatizzati e requisiti di approvazione manuale.                                   |    3    |  D/V  |
| 9.11.5 | Verificare che i meccanismi di persistenza dell'agente cifrino i dati di stato sensibili con chiavi AES-256 per singolo agente e implementino una rotazione sicura delle chiavi secondo programmi configurabili (massimo 90 giorni) con distribuzione a zero tempi di inattività.                                         |    3    |  D/V  |

---

## 9.12 Framework di Sicurezza per l'Integrazione degli Strumenti

Controlli di sicurezza per il caricamento dinamico degli strumenti, l'esecuzione e la convalida dei risultati con processi definiti di valutazione del rischio e approvazione.

|   #    | Descrizione                                                                                                                                                                                                                                                                                                   | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.12.1 | Verificare che i descrittori degli strumenti includano metadati di sicurezza specificando i privilegi richiesti (lettura/scrittura/esecuzione), i livelli di rischio (basso/medio/alto), i limiti delle risorse (CPU, memoria, rete) e i requisiti di convalida documentati nei manifest degli strumenti.     |    1    |  D/V  |
| 9.12.2 | Verificare che i risultati dell'esecuzione degli strumenti siano convalidati rispetto agli schemi previsti (JSON Schema, XML Schema) e alle politiche di sicurezza (sanificazione dell'output, classificazione dei dati) prima dell'integrazione, con limiti di timeout e procedure di gestione degli errori. |    1    |  D/V  |
| 9.12.3 | Verificare che i log delle interazioni degli strumenti includano un contesto di sicurezza dettagliato, compreso l'uso dei privilegi, i modelli di accesso ai dati, i tempi di esecuzione, il consumo delle risorse e i codici di ritorno, con una registrazione strutturata per l'integrazione con SIEM.      |    2    |  D/V  |
| 9.12.4 | Verificare che i meccanismi di caricamento dinamico degli strumenti convalidino le firme digitali utilizzando l'infrastruttura PKI e implementino protocolli di caricamento sicuri con isolamento in sandbox e verifica delle autorizzazioni prima dell'esecuzione.                                           |    2    |  D/V  |
| 9.12.5 | Verificare che le valutazioni di sicurezza degli strumenti vengano attivate automaticamente per le nuove versioni con passaggi di approvazione obbligatori che includano analisi statica, test dinamici e revisione del team di sicurezza con criteri di approvazione documentati e requisiti di SLA.         |    3    |  D/V  |

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

