# 9 Sicurezza dell'Orchestrazione Autonoma e dell'Azione Agentica

## Obiettivo di Controllo

Garantire che i sistemi di IA autonomi o multi-agente possano eseguire solo azioni esplicitamente intenzionate, autenticate, verificabili e all’interno di soglie limitate di costo e rischio. Questo protegge contro minacce quali Compromissione del Sistema Autonomo, Uso Improprio degli Strumenti, Rilevamento di Cicli degli Agenti, Dirottamento della Comunicazione, Falsificazione dell’Identità, Manipolazione degli Sciami e Manipolazione dell’Intento.

---

## 9.1 Pianificazione dei compiti dell'agente e budget di ricorsione

Limitare i piani ricorsivi e imporre checkpoint umani per azioni privilegiate.

|   #   | Descrizione                                                                                                                                                                                                                | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.1.1 | Verificare che la profondità massima della ricorsione, la larghezza, il tempo di orologio a parete, i token e il costo monetario per l'esecuzione di ogni agente siano configurati centralmente e versionati.              |    1    |  D/V  |
| 9.1.2 | Verificare che azioni privilegiate o irreversibili (ad esempio, commit di codice, trasferimenti finanziari) richiedano l'approvazione esplicita da parte di un umano tramite un canale verificabile prima dell'esecuzione. |    1    |  D/V  |
| 9.1.3 | Verificare che i monitor delle risorse in tempo reale attivino l'interruzione del circuito di sicurezza quando viene superata qualsiasi soglia di budget, interrompendo l'espansione ulteriore delle attività.             |    2    |   D   |
| 9.1.4 | Verificare che gli eventi del circuito di interruzione vengano registrati con l'ID dell'agente, la condizione di attivazione e lo stato del piano acquisito per la revisione forense.                                      |    2    |  D/V  |
| 9.1.5 | Verificare che i test di sicurezza coprano scenari di esaurimento del budget e di piano fuori controllo, confermando l'arresto sicuro senza perdita di dati.                                                               |    3    |   V   |
| 9.1.6 | Verificare che le politiche di budget siano espresse come policy-as-code e applicate nel CI/CD per bloccare la deriva delle configurazioni.                                                                                |    3    |   D   |

---

## 9.2 Sandboxing dei Plugin degli Strumenti

Isolare le interazioni degli strumenti per prevenire accessi non autorizzati al sistema o l'esecuzione di codice.

|   #   | Descrizione                                                                                                                                                                                                          | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.2.1 | Verificare che ogni strumento/plugin venga eseguito all'interno di un sistema operativo, container o sandbox a livello WASM con politiche di minimo privilegio per il file-system, la rete e le chiamate di sistema. |    1    |  D/V  |
| 9.2.2 | Verificare che le quote delle risorse del sandbox (CPU, memoria, disco, uscita di rete) e i timeout di esecuzione siano applicati e registrati.                                                                      |    1    |  D/V  |
| 9.2.3 | Verificare che i binari o i descrittori degli strumenti siano firmati digitalmente; le firme devono essere convalidate prima del caricamento.                                                                        |    2    |  D/V  |
| 9.2.4 | Verificare che la telemetria del sandbox fluisca verso un SIEM; le anomalie (ad esempio, tentativi di connessioni in uscita) generano allarmi.                                                                       |    2    |   V   |
| 9.2.5 | Verificare che i plugin ad alto rischio siano sottoposti a revisione della sicurezza e test di penetrazione prima del rilascio in produzione.                                                                        |    3    |   V   |
| 9.2.6 | Verificare che i tentativi di fuga dalla sandbox vengano bloccati automaticamente e che il plugin responsabile venga messo in quarantena in attesa di indagini.                                                      |    3    |  D/V  |

---

## 9.3 Ciclo Autonomo e Limite dei Costi

Rilevare e fermare la ricorsione incontrollata da agente ad agente e le esplosioni di costi.

|   #   | Descrizione                                                                                                                                                              | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 9.3.1 | Verificare che le chiamate tra agenti includano un hop-limit o TTL che il runtime decrementa e applica.                                                                  |    1    |  D/V  |
| 9.3.2 | Verificare che gli agenti mantengano un ID univoco del grafo di invocazione per individuare l'auto-invocazione o schemi ciclici.                                         |    2    |   D   |
| 9.3.3 | Verificare che i contatori cumulativi delle unità di calcolo e della spesa siano tracciati per ogni catena di richieste; il superamento del limite interrompe la catena. |    2    |  D/V  |
| 9.3.4 | Verificare che l'analisi formale o il model checking dimostrino l'assenza di ricorsione non limitata nei protocolli degli agenti.                                        |    3    |   V   |
| 9.3.5 | Verificare che gli eventi di interruzione del ciclo generino avvisi e alimentino metriche di miglioramento continuo.                                                     |    3    |   D   |

---

## 9.4 Protezione contro l'abuso a livello di protocollo

Canali di comunicazione sicuri tra agenti e sistemi esterni per prevenire il dirottamento o la manipolazione.

|   #   | Descrizione                                                                                                                                               | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.4.1 | Verificare che tutti i messaggi agent-to-tool e agent-to-agent siano autenticati (ad esempio, mutual TLS o JWT) e criptati end-to-end.                    |    1    |  D/V  |
| 9.4.2 | Verificare che gli schemi siano rigorosamente convalidati; i campi sconosciuti o i messaggi malformati devono essere respinti.                            |    1    |   D   |
| 9.4.3 | Verificare che i controlli di integrità (MAC o firme digitali) coprano l'intero payload del messaggio, compresi i parametri dello strumento.              |    2    |  D/V  |
| 9.4.4 | Verificare che la protezione contro la ripetizione (nonce o finestre temporali) sia applicata a livello di protocollo.                                    |    2    |   D   |
| 9.4.5 | Verificare che le implementazioni dei protocolli vengano sottoposte a fuzzing e analisi statica per individuare difetti di injection o deserializzazione. |    3    |   V   |

---

## 9.5 Identità dell'Agente e Prova di Manomissione

Garantire che le azioni siano attribuibili e le modifiche rilevabili.

|   #   | Descrizione                                                                                                                                             | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.5.1 | Verificare che ogni istanza dell'agente possieda un'identità crittografica unica (coppia di chiavi o credenziale basata su hardware).                   |    1    |  D/V  |
| 9.5.2 | Verificare che tutte le azioni dell'agente siano firmate e corredate da marca temporale; i registri devono includere la firma per la non ripudiabilità. |    2    |  D/V  |
| 9.5.3 | Verificare che i log a prova di manomissione siano memorizzati in un supporto solo in append o scrittura unica.                                         |    2    |   V   |
| 9.5.4 | Verificare che le chiavi di identità ruotino secondo un programma definito e in presenza di indicatori di compromissione.                               |    3    |   D   |
| 9.5.5 | Verificare che i tentativi di spoofing o di conflitto di chiavi attivino l'immediata quarantena dell'agente interessato.                                |    3    |  D/V  |

---

## 9.6 Riduzione del Rischio tramite Sciame Multi-Agente

Mitigare i rischi legati al comportamento collettivo tramite isolamento e modellazione formale della sicurezza.

|   #   | Descrizione                                                                                                                                         | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.6.1 | Verificare che gli agenti che operano in diversi domini di sicurezza vengano eseguiti in sandbox di runtime isolati o in segmenti di rete separati. |    1    |  D/V  |
| 9.6.2 | Verificare che i comportamenti dello sciame siano modellati e formalmente verificati per la vivacità e la sicurezza prima della distribuzione.      |    3    |   V   |
| 9.6.3 | Verificare che i monitor di runtime rilevino pattern emergenti di insicurezza (ad esempio, oscillazioni, deadlock) e avviino azioni correttive.     |    3    |   D   |

---

## 9.7 Autenticazione / Autorizzazione Utente e Strumento

Implementare controlli di accesso robusti per ogni azione attivata dall'agente.

|   #   | Descrizione                                                                                                                                             | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.7.1 | Verificare che gli agenti si autentichino come principali di prima classe ai sistemi a valle, senza mai riutilizzare le credenziali dell'utente finale. |    1    |  D/V  |
| 9.7.2 | Verificare che le politiche di autorizzazione dettagliate limitino quali strumenti un agente può invocare e quali parametri può fornire.                |    2    |   D   |
| 9.7.3 | Verificare che i controlli dei privilegi vengano rivalutati ad ogni chiamata (autorizzazione continua), non solo all'inizio della sessione.             |    2    |   V   |
| 9.7.4 | Verificare che i privilegi delegati scadano automaticamente e richiedano un nuovo consenso dopo il timeout o una modifica dell’ambito.                  |    3    |   D   |

---

## 9.8 Sicurezza della comunicazione agente-agente

Cripta e proteggi l'integrità di tutti i messaggi tra agenti per prevenire l'intercettazione e la manomissione.

|   #   | Descrizione                                                                                                                                                   | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.8.1 | Verificare che l'autenticazione reciproca e la cifratura con segretezza perfetta in avanti (ad esempio TLS 1.3) siano obbligatorie per i canali degli agenti. |    1    |  D/V  |
| 9.8.2 | Verificare che l'integrità e l'origine del messaggio siano convalidate prima dell'elaborazione; i fallimenti generano avvisi e scartano il messaggio.         |    1    |   D   |
| 9.8.3 | Verificare che i metadati di comunicazione (timestamp, numeri di sequenza) vengano registrati per supportare la ricostruzione forense.                        |    2    |  D/V  |
| 9.8.4 | Verificare che la verifica formale o il model checking confermino che le macchine a stati del protocollo non possano essere portate in stati non sicuri.      |    3    |   V   |

---

## 9.9 Verifica dell'intento e applicazione dei vincoli

Convalidare che le azioni dell'agente siano in linea con l'intento dichiarato dall'utente e i vincoli del sistema.

|   #   | Descrizione                                                                                                                                                                                       | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.9.1 | Verificare che i risolutori di vincoli pre-esecuzione controllino le azioni proposte rispetto a regole di sicurezza e politiche codificate rigidamente.                                           |    1    |   D   |
| 9.9.2 | Verificare che le azioni ad alto impatto (finanziarie, distruttive, sensibili alla privacy) richiedano una conferma esplicita dell'intento da parte dell'utente che le avvia.                     |    2    |  D/V  |
| 9.9.3 | Verificare che i controlli post-condizione confermino che le azioni completate abbiano raggiunto gli effetti previsti senza effetti collaterali; eventuali discrepanze attivano il rollback.      |    2    |   V   |
| 9.9.4 | Verificare che i metodi formali (ad esempio, model checking, dimostrazione di teoremi) o i test basati sulle proprietà dimostrino che i piani degli agenti soddisfano tutti i vincoli dichiarati. |    3    |   V   |
| 9.9.5 | Verificare che gli incidenti di discrepanza di intento o violazione di vincoli alimentino cicli di miglioramento continuo e la condivisione di informazioni sulle minacce.                        |    3    |   D   |

---

## 9.10 Strategia di Ragionamento dell'Agente Sicurezza

Selezione ed esecuzione sicura di diverse strategie di ragionamento, inclusi gli approcci ReAct, Chain-of-Thought e Tree-of-Thoughts.

|   #    | Descrizione                                                                                                                                                                                                                                                                  | Livello | Ruolo |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.10.1 | Verificare che la selezione della strategia di ragionamento utilizzi criteri deterministici (complessità dell'input, tipo di compito, contesto di sicurezza) e che input identici producano selezioni di strategia identiche all'interno dello stesso contesto di sicurezza. |    1    |  D/V  |
| 9.10.2 | Verificare che ogni strategia di ragionamento (ReAct, Catena di Pensieri, Albero dei Pensieri) abbia una convalida degli input dedicata, una sanitizzazione degli output e limiti di tempo di esecuzione specifici per il suo approccio cognitivo.                           |    1    |  D/V  |
| 9.10.3 | Verificare che le transizioni della strategia di ragionamento siano registrate con il contesto completo, incluse le caratteristiche dell'input, i valori dei criteri di selezione e i metadati di esecuzione per la ricostruzione della traccia di controllo.                |    2    |  D/V  |
| 9.10.4 | Verificare che il ragionamento Tree-of-Thoughts includa meccanismi di potatura dei rami che terminano l’esplorazione quando vengono rilevate violazioni di policy, limiti di risorse o confini di sicurezza.                                                                 |    2    |  D/V  |
| 9.10.5 | Verificare che i cicli ReAct (Reason-Act-Observe) includano punti di controllo di convalida in ogni fase: verifica del passo di ragionamento, autorizzazione dell’azione e sanificazione dell’osservazione prima di procedere.                                               |    2    |  D/V  |
| 9.10.6 | Verificare che le metriche di prestazione della strategia di ragionamento (tempo di esecuzione, utilizzo delle risorse, qualità dell'output) siano monitorate con avvisi automatici quando le metriche deviano oltre le soglie configurate.                                  |    3    |  D/V  |
| 9.10.7 | Verificare che gli approcci di ragionamento ibrido che combinano più strategie mantengano la convalida degli input e i vincoli di output di tutte le strategie costituenti senza aggirare alcun controllo di sicurezza.                                                      |    3    |  D/V  |
| 9.10.8 | Verifica che il testing della sicurezza della strategia di ragionamento includa il fuzzing con input malformati, prompt avversari progettati per forzare il cambio di strategia e il testing delle condizioni al limite per ogni approccio cognitivo.                        |    3    |  D/V  |

---

## 9.11 Gestione dello Stato del Ciclo di Vita dell'Agente e Sicurezza

Inizializzazione sicura dell'agente, transizioni di stato e terminazione con tracciamenti di audit crittografici e procedure di recupero definite.

|   #    | Descrizione                                                                                                                                                                                                                                                                                                             | Livello | Ruolo |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.11.1 | Verifica che l'inizializzazione dell'agente includa l'istituzione dell'identità crittografica con credenziali supportate da hardware e registri di audit di avvio immutabili contenenti l'ID dell'agente, il timestamp, l'hash della configurazione e i parametri di inizializzazione.                                  |    1    |  D/V  |
| 9.11.2 | Verificare che le transizioni di stato dell'agente siano firmate criptograficamente, contrassegnate con data e ora e registrate con il contesto completo, inclusi gli eventi scatenanti, l'hash dello stato precedente, l'hash del nuovo stato e le convalide di sicurezza eseguite.                                    |    2    |  D/V  |
| 9.11.3 | Verificare che le procedure di spegnimento dell'agente includano la cancellazione sicura della memoria mediante cancellazione crittografica o sovrascrittura multipla, la revoca delle credenziali con notifica all'autorità di certificazione e la generazione di certificati di terminazione a prova di manomissione. |    2    |  D/V  |
| 9.11.4 | Verificare che i meccanismi di recupero degli agenti convalidino l'integrità dello stato utilizzando checksum crittografici (SHA-256 minimo) e tornino a stati noti funzionanti quando viene rilevata una corruzione, con avvisi automatici e requisiti di approvazione manuale.                                        |    3    |  D/V  |
| 9.11.5 | Verificare che i meccanismi di persistenza degli agenti cifrino i dati di stato sensibili con chiavi AES-256 univoche per ogni agente e implementino la rotazione sicura delle chiavi secondo programmi configurabili (massimo 90 giorni) con deployment a tempo zero senza interruzioni.                               |    3    |  D/V  |

---

## 9.12 Framework di Sicurezza per l'Integrazione degli Strumenti

Controlli di sicurezza per il caricamento dinamico degli strumenti, l'esecuzione e la convalida dei risultati con processi definiti di valutazione del rischio e approvazione.

|   #    | Descrizione                                                                                                                                                                                                                                                                                                   | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 9.12.1 | Verificare che i descrittori degli strumenti includano metadati di sicurezza che specificano i privilegi richiesti (lettura/scrittura/esecuzione), i livelli di rischio (basso/medio/alto), i limiti delle risorse (CPU, memoria, rete) e i requisiti di convalida documentati nei manifest degli strumenti.  |    1    |  D/V  |
| 9.12.2 | Verificare che i risultati dell'esecuzione degli strumenti siano convalidati rispetto agli schemi previsti (Schema JSON, Schema XML) e alle politiche di sicurezza (sanificazione dell'output, classificazione dei dati) prima dell'integrazione, con limiti di timeout e procedure di gestione degli errori. |    1    |  D/V  |
| 9.12.3 | Verificare che i log di interazione degli strumenti includano un contesto di sicurezza dettagliato che comprenda l'uso dei privilegi, i modelli di accesso ai dati, il tempo di esecuzione, il consumo di risorse e i codici di ritorno, con una registrazione strutturata per l'integrazione SIEM.           |    2    |  D/V  |
| 9.12.4 | Verificare che i meccanismi di caricamento dinamico degli strumenti convalidino le firme digitali utilizzando l'infrastruttura PKI e implementino protocolli di caricamento sicuri con isolamento sandbox e verifica dei permessi prima dell'esecuzione.                                                      |    2    |  D/V  |
| 9.12.5 | Verificare che le valutazioni di sicurezza degli strumenti vengano attivate automaticamente per le nuove versioni con gate di approvazione obbligatori che includano analisi statica, test dinamici e revisione da parte del team di sicurezza, con criteri di approvazione documentati e requisiti di SLA.   |    3    |  D/V  |

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

