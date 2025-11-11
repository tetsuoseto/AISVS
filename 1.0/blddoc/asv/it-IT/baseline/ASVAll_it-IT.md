## Frontespizio

### Informazioni sullo Standard

Lo Standard di Verifica della Sicurezza dell'Intelligenza Artificiale (AISVS) è un catalogo guidato dalla comunità di requisiti di sicurezza che data scientist, ingegneri MLOps, architetti software, sviluppatori, tester, professionisti della sicurezza, fornitori di strumenti, regolatori e consumatori possono utilizzare per progettare, costruire, testare e verificare sistemi e applicazioni AI affidabili. Fornisce un linguaggio comune per specificare i controlli di sicurezza lungo l'intero ciclo di vita dell'IA—dalla raccolta dei dati e lo sviluppo del modello fino al deployment e al monitoraggio continuo—così le organizzazioni possono misurare e migliorare la resilienza, la privacy e la sicurezza delle loro soluzioni AI.

### Copyright e Licenza

Versione 0.1 (Prima Bozza Pubblica - Lavori in Corso), 2025  

![license](images/license.png)
Copyright © 2025 Il Progetto AISVS.  

Rilasciato sotto laCreative Commons Attribution‑ShareAlike 4.0 International License.
Per qualsiasi riutilizzo o distribuzione, è necessario comunicare chiaramente agli altri i termini della licenza di questo lavoro.

### Responsabili di Progetto

Jim Manico
Aras “Russ” Memisyazici

### Collaboratori e Revisori

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


────────────────────────────────────────

AISVS è un nuovo standard creato specificamente per affrontare le sfide uniche di sicurezza dei sistemi di intelligenza artificiale. Pur traendo ispirazione dalle migliori pratiche di sicurezza più ampie, ogni requisito di AISVS è stato sviluppato da zero per riflettere il panorama delle minacce dell’IA e per aiutare le organizzazioni a costruire soluzioni di IA più sicure e resilienti.

## Prefazione

Benvenuti allo Standard di Verifica della Sicurezza dell'Intelligenza Artificiale (AISVS) versione 1.0!

### Introduzione

Fondata nel 2025 attraverso uno sforzo collaborativo della comunità, AISVS definisce i requisiti di sicurezza da considerare nella progettazione, nello sviluppo, nel dispiegamento e nel funzionamento di modelli di intelligenza artificiale moderni, pipeline e servizi abilitati dall'AI.

AISVS v1.0 rappresenta il lavoro combinato dei suoi responsabili di progetto, del gruppo di lavoro e dei contributori della comunità più ampia per produrre una baseline pragmatica e testabile per la sicurezza dei sistemi di intelligenza artificiale.

Il nostro obiettivo con questa versione è rendere AISVS semplice da adottare mantenendo al contempo un focus preciso sul suo ambito definito e affrontando il panorama dei rischi in rapida evoluzione unico dell'IA.

### Obiettivi Chiave per AISVS Versione 1.0

La versione 1.0 sarà creata con diversi principi guida.

#### Ambito Ben Definito

Ogni requisito deve essere allineato con il nome e la missione di AISVS:

Intelligenza Artificiale – I controlli operano al livello AI/ML (dati, modello, pipeline o inferenza) e sono responsabilità dei professionisti dell'intelligenza artificiale.
Sicurezza – I requisiti mitigano direttamente i rischi identificati per la sicurezza, la privacy o la sicurezza.
Verifica – Il linguaggio è scritto in modo che la conformità possa essere convalidata oggettivamente.
Lo standard – Le sezioni seguono una struttura e una terminologia coerenti per formare un riferimento omogeneo.
​
────────────────────────────────────────

Seguendo AISVS, le organizzazioni possono valutare sistematicamente e rafforzare la postura di sicurezza delle loro soluzioni di intelligenza artificiale, promuovendo una cultura di ingegneria dell'IA sicura.

## Utilizzando l'AISVS

Lo Standard di Verifica della Sicurezza dell'Intelligenza Artificiale (AISVS) definisce i requisiti di sicurezza per le applicazioni e i servizi di intelligenza artificiale moderni, concentrandosi sugli aspetti sotto il controllo degli sviluppatori di applicazioni.

L'AISVS è destinato a chiunque sviluppi o valuti la sicurezza delle applicazioni di intelligenza artificiale, inclusi sviluppatori, architetti, ingegneri della sicurezza e auditor. Questo capitolo introduce la struttura e l'uso dell'AISVS, inclusi i suoi livelli di verifica e i casi d'uso previsti.

### Livelli di Verifica della Sicurezza dell'Intelligenza Artificiale

L'AISVS definisce tre livelli crescenti di verifica della sicurezza. Ogni livello aggiunge profondità e complessità, permettendo alle organizzazioni di adattare la loro postura di sicurezza al livello di rischio dei loro sistemi di IA.

Le organizzazioni possono iniziare al Livello 1 e adottare progressivamente livelli più elevati man mano che la maturità della sicurezza e l'esposizione alle minacce aumentano.

#### Definizione dei Livelli

Ogni requisito in AISVS v1.0 è assegnato a uno dei seguenti livelli:

 Requisiti di livello 1

Il Livello 1 include i requisiti di sicurezza più critici e fondamentali. Questi si concentrano sulla prevenzione degli attacchi comuni che non si basano su altre precondizioni o vulnerabilità. La maggior parte dei controlli del Livello 1 è o semplice da implementare o sufficientemente essenziale da giustificare lo sforzo.

 Requisiti di livello 2

Il Livello 2 affronta attacchi più avanzati o meno comuni, nonché difese stratificate contro minacce diffuse. Questi requisiti possono comportare una logica più complessa o mirare a specifici prerequisiti dell'attacco.

 Requisiti di livello 3

Il Livello 3 include controlli che sono tipicamente più difficili da implementare o situazionali nella loro applicabilità. Questi rappresentano spesso meccanismi di difesa in profondità o mitigazioni contro attacchi di nicchia, mirati o ad alta complessità.

#### Ruolo (D/V)

Ogni requisito AISVS è contrassegnato in base al pubblico principale:

D – Requisiti focalizzati sullo sviluppatore
V – Requisiti focalizzati sul verificatore/auditor
D/V – Rilevante sia per sviluppatori che per verificatori

## C1 Governance dei Dati di Addestramento e Gestione dei Bias

### Obiettivo di Controllo

I dati di addestramento devono essere reperiti, gestiti e mantenuti in modo da preservarne la provenienza, la sicurezza, la qualità e l’equità. Farlo soddisfa i doveri legali e riduce i rischi di bias, avvelenamento o violazioni della privacy che si manifestano durante l’addestramento e che potrebbero influenzare l’intero ciclo di vita dell’IA.

────────────────────────────────────────

### C1.1 Provenienza dei dati di addestramento

Mantieni un inventario verificabile di tutti i set di dati, accetta solo fonti affidabili e registra ogni modifica per garantire la tracciabilità.

 #1.1.1    Livello: 1    Ruolo: D/V
 Verificare che venga mantenuto un inventario aggiornato di ogni fonte di dati di addestramento (origine, responsabile/proprietario, licenza, metodo di raccolta, vincoli d'uso previsti e storia di elaborazione).
 #1.1.2    Livello: 1    Ruolo: D/V
 Verificare che i processi di training dei dati escludano caratteristiche, attributi o campi non necessari (ad esempio, metadati non utilizzati, dati PII sensibili, dati di test trapelati).
 #1.1.3    Livello: 2    Ruolo: D/V
 Verificare che tutte le modifiche al dataset siano soggette a un flusso di lavoro di approvazione registrato.
 #1.1.4    Livello: 3    Ruolo: D/V
 Verificare che i dataset o i sottoinsiemi siano marcati con filigrana o tramite impronta digitale dove possibile.

────────────────────────────────────────

### C1.2 Sicurezza e Integrità dei Dati di Addestramento

Limitare l'accesso ai dati di addestramento, crittografarli sia a riposo che in transito e convalidarne l'integrità per prevenire manomissioni, furti o avvelenamento dei dati.

 #1.2.1    Livello: 1    Ruolo: D/V
 Verificare che i controlli di accesso proteggano l’archiviazione dei dati di addestramento e le pipeline.
 #1.2.2    Livello: 2    Ruolo: D/V
 Verificare che tutti gli accessi ai dati di addestramento siano registrati, inclusi utente, ora e azione.
 #1.2.3    Livello: 2    Ruolo: D/V
 Verificare che i dataset di addestramento siano crittografati durante la trasmissione e a riposo, utilizzando algoritmi crittografici standard del settore e pratiche di gestione delle chiavi.
 #1.2.4    Livello: 2    Ruolo: D/V
 Verificare che vengano utilizzati hash crittografici o firme digitali per garantire l'integrità dei dati durante l'archiviazione e il trasferimento dei dati di addestramento.
 #1.2.5    Livello: 2    Ruolo: D/V
 Verificare che vengano applicate tecniche di rilevamento automatizzato per prevenire modifiche non autorizzate o la corruzione dei dati di addestramento.
 #1.2.6    Livello: 2    Ruolo: D/V
 Verificare che i dati di addestramento obsoleti siano eliminati in modo sicuro o anonimizzati.
 #1.2.7    Livello: 3    Ruolo: D/V
 Verificare che tutte le versioni del dataset di addestramento siano identificate univocamente, archiviate in modo immutabile e verificabili per supportare il rollback e l'analisi forense.

────────────────────────────────────────

### C1.3 Qualità, Integrità e Sicurezza dell'Etichettatura dei Dati di Addestramento

Proteggi le etichette e richiedi una revisione tecnica per i dati critici.

 #1.3.1    Livello: 2    Ruolo: D/V
 Verificare che gli hash crittografici o le firme digitali siano applicati agli artefatti delle etichette per garantirne l'integrità e l'autenticità.
 #1.3.2    Livello: 2    Ruolo: D/V
 Verificare che le interfacce e le piattaforme di etichettatura applichino controlli di accesso rigorosi, mantengano registri di audit a prova di manomissione di tutte le attività di etichettatura e proteggano contro modifiche non autorizzate.
 #1.3.3    Livello: 3    Ruolo: D/V
 Verificare che le informazioni sensibili nelle etichette siano oscurate, anonimizzate o criptate a livello di campo dati sia a riposo che in transito.

────────────────────────────────────────

### C1.4 Qualità dei Dati di Addestramento e Garanzia di Sicurezza

Combina la validazione automatica, i controlli manuali a campione e la correzione registrata per garantire l'affidabilità del dataset.

 #1.4.1    Livello: 1    Ruolo: D
 Verificare che i test automatici rilevino errori di formato e valori nulli ad ogni ingresso o trasformazione significativa dei dati.
 #1.4.2    Livello: 2    Ruolo: D/V
 Verificare che le pipeline di addestramento e fine-tuning dei LLM implementino il rilevamento di avvelenamento e la validazione dell'integrità dei dati (ad esempio, metodi statistici, rilevamento di outlier, analisi degli embedding) per identificare potenziali attacchi di avvelenamento (ad esempio, cambio di etichetta, inserimento di trigger backdoor, comandi di cambio ruolo, attacchi di istanze influenti) o la corruzione accidentale dei dati di addestramento.
 #1.4.3    Livello: 2    Ruolo: D/V
 Verificare che le etichette generate automaticamente (ad esempio, tramite LLM o supervisione debole) siano soggette a soglie di confidabilità e controlli di coerenza per rilevare etichette allucinatorie, fuorvianti o a bassa affidabilità.
 #1.4.4    Livello: 3    Ruolo: D/V
 Verificare che siano implementate e ottimizzate difese adeguate, come l’addestramento avversario (utilizzando esempi avversari generati), l’augmentazione dei dati con input perturbati o tecniche di ottimizzazione robusta, per i modelli rilevanti basati sulla valutazione del rischio.
 #1.4.5    Livello: 3    Ruolo: D
 Verificare che i test automatizzati rilevino gli sfasamenti delle etichette ad ogni ingresso o significativa trasformazione dei dati.

────────────────────────────────────────

### C1.5 Tracciabilità e Lineage dei Dati

Traccia l'intero percorso di ogni punto dati dalla fonte all'input del modello per garantire auditabilità e risposta agli incidenti.

 #1.5.1    Livello: 2    Ruolo: D/V
 Verificare che la provenienza di ogni punto dati, comprese tutte le trasformazioni, aumenti e fusioni, sia registrata e possa essere ricostruita.
 #1.5.2    Livello: 2    Ruolo: D/V
 Verificare che i record di tracciabilità siano immutabili, archiviati in modo sicuro e accessibili per le revisioni.
 #1.5.3    Livello: 2    Ruolo: D/V
 Verificare che il tracciamento della provenienza copra i dati sintetici generati tramite tecniche di preservazione della privacy o generative e che tutti i dati sintetici siano chiaramente etichettati e distinguibili dai dati reali lungo tutto il flusso di lavoro.

────────────────────────────────────────

### Riferimenti

NIST AI Risk Management Framework
EU AI Act – Article 10: Data & Data Governance
CISA Advisory: Securing Data for AI Systems
OpenAI Privacy Center – Data Deletion Controls

## Validazione dell'input utente C2

### Obiettivo di Controllo

La validazione robusta dell'input utente è una difesa di prima linea contro alcuni degli attacchi più dannosi ai sistemi di intelligenza artificiale. Gli attacchi di prompt injection possono sovrascrivere le istruzioni di sistema, divulgare dati sensibili o indirizzare il modello verso comportamenti non consentiti. A meno che non siano implementati filtri dedicati e altre forme di validazione, la ricerca mostra che i jailbreak che sfruttano le finestre di contesto continueranno a essere efficaci.

────────────────────────────────────────

### C2.1 Difesa contro l'iniezione di prompt

L'iniezione di prompt è uno dei principali rischi per i sistemi di IA. Le difese contro questa tattica utilizzano una combinazione di filtri di pattern, classificatori di dati e applicazione della gerarchia delle istruzioni.

 #2.1.1    Livello: 1    Ruolo: D/V
 Verificare che qualsiasi input esterno o derivato che possa influenzare il comportamento, inclusi prompt dell’utente, risultati RAG, output di plugin o MCP, messaggi agente-agente, risposte API o webhook, file di configurazione o policy, letture e scritture di memoria, sia trattato come non attendibile, reso inerte tramite citazione o etichettatura e rimozione di contenuti attivi, e controllato tramite un set di regole o un servizio mantenuto per il rilevamento di iniezioni di prompt, prima della loro concatenazione nei prompt o dell’esecuzione di azioni.
 #2.1.2    Livello: 1    Ruolo: D/V
 Verificare che il sistema applichi una gerarchia di istruzioni in cui i messaggi di sistema e dello sviluppatore sovrascrivano le istruzioni dell'utente e altri input non attendibili, anche dopo l'elaborazione delle istruzioni dell'utente.
 #2.1.4    Livello: 2    Ruolo: D
 Verificare che i prompt provenienti da contenuti di terze parti (pagine web, PDF, email) vengano sanitizzati in isolamento (ad esempio, rimuovendo direttive simili a istruzioni e neutralizzando contenuti HTML, Markdown e script) prima di essere concatenati nel prompt principale.

────────────────────────────────────────

### C2.2 Resistenza agli Esempi Avversari

I modelli di Elaborazione del Linguaggio Naturale (NLP) sono ancora vulnerabili a lievi perturbazioni a livello di caratteri o parole che gli esseri umani spesso non notano, ma che i modelli tendono a classificare erroneamente.

 #2.2.1    Livello: 1    Ruolo: D
 Verificare che i passaggi di normalizzazione di input di base (Unicode NFC, mappatura degli omoglifi, rimozione degli spazi bianchi superflui, eliminazione dei caratteri di controllo e invisibili Unicode) vengano eseguiti prima della tokenizzazione o dell'embedding e prima dell'analisi negli argomenti degli strumenti o MCP.
 #2.2.2    Livello: 2    Ruolo: D/V
 Verificare che il rilevamento di anomalie statistiche segnali gli input con una distanza di modifica insolitamente elevata rispetto alle norme linguistiche o distanze di embedding anomale e che gli input segnalati vengano bloccati prima della concatenazione nei prompt o dell'esecuzione delle azioni.
 #2.2.3    Livello: 2    Ruolo: D
 Verificare che la pipeline di inferenza supporti varianti di modelli rinforzati tramite addestramento adversariale o livelli di difesa (ad esempio, randomizzazione, distillazione difensiva, controlli di allineamento) per endpoint ad alto rischio.
 #2.2.4    Livello: 2    Ruolo: V
 Verificare che gli input sospetti di tipo avversario siano messi in quarantena e registrati con i payload completi e i metadati di tracciamento (origine, strumento o server MCP, ID agente, sessione).
 #2.2.5    Livello: 2    Ruolo: D/V
 Verificare che il travisamento di codifica e rappresentazione sia rilevato e mitigato sia negli input che negli output (ad esempio, caratteri Unicode/control invisibili, sostituzioni di omoglifi o testo a direzione mista). Le mitigazioni approvate includono la canonicalizzazione, la validazione rigorosa dello schema, il rifiuto basato su politiche o la marcatura esplicita.

────────────────────────────────────────

### C2.3 Set di caratteri per il prompt

Limitare il set di caratteri degli input degli utenti per consentire solamente i caratteri necessari ai requisiti aziendali può aiutare a prevenire vari tipi di attacchi.

 #2.3.1    Livello: 1    Ruolo: D
 Verificare che il sistema implementi una limitazione del set di caratteri per gli input degli utenti, consentendo solo i caratteri espressamente richiesti per scopi aziendali.
 #2.3.2    Livello: 1    Ruolo: D
 Verificare che venga utilizzato un approccio basato su una lista di consentiti per definire il set di caratteri permessi.
 #2.3.3    Livello: 1    Ruolo: D/V
 Verificare che gli input contenenti caratteri al di fuori del set consentito vengano rifiutati e registrati con metadati di tracciamento (origine, strumento o server MCP, ID agente, sessione).

────────────────────────────────────────

### C2.4 Validazione di Schema, Tipo e Lunghezza

Gli attacchi di intelligenza artificiale che utilizzano input malformati o sovradimensionati possono causare errori di parsing, fuoriuscite di prompt tra i campi e esaurimento delle risorse. Un'applicazione rigorosa dello schema è inoltre un prerequisito quando si eseguono chiamate deterministicte agli strumenti.

 #2.4.1    Livello: 1    Ruolo: D
 Verificare che ogni API, strumento o endpoint MCP definisca uno schema di input esplicito (JSON Schema, Protobuf o equivalente multimodale), rifiuti campi extra o sconosciuti e la coercizione implicita dei tipi, e convalidi gli input lato server prima dell’assemblaggio del prompt o dell’esecuzione dello strumento.
 #2.4.2    Livello: 1    Ruolo: D/V
 Verificare che gli input che superano i limiti massimi di token o byte vengano rifiutati con un errore sicuro e mai troncati silenziosamente.
 #2.4.3    Livello: 2    Ruolo: D/V
 Verificare che i controlli di tipo (ad esempio, intervalli numerici, valori enum, tipi MIME per immagini/audio) siano applicati lato server, inclusi gli argomenti di strumenti o MCP.
 #2.4.4    Livello: 2    Ruolo: D
 Verificare che i validatori semantici, che comprendono l’input NLP, operino in tempo costante ed evitino chiamate di rete esterne per prevenire DoS algoritmici.
 #2.4.5    Livello: 3    Ruolo: V
 Verificare che i fallimenti di convalida vengano registrati con estratti del payload oscurati e codici di errore univoci e includano i metadati di tracciamento (origine, strumento o server MCP, ID agente, sessione) per facilitare la gestione della sicurezza.

────────────────────────────────────────

### C2.5 Controllo dei Contenuti e delle Politiche

Gli sviluppatori dovrebbero essere in grado di rilevare prompt sintatticamente validi che richiedono contenuti non consentiti (come istruzioni illecite, discorsi d'odio e/o testi protetti da copyright) e impedirne la diffusione.

 #2.5.1    Livello: 1    Ruolo: D
 Verificare che un classificatore di contenuti (zero shot o fine-tuned) valuti ogni input e output per violenza, autolesionismo, odio, contenuti sessuali e richieste illegali, con soglie configurabili.
 #2.5.2    Livello: 1    Ruolo: D/V
 Verificare che gli input che violano le politiche vengano rifiutati in modo che non si propaghino a chiamate successive verso LLM o strumenti/MCP.
 #2.5.3    Livello: 2    Ruolo: D
 Verificare che il filtraggio rispetti le politiche specifiche dell'utente (età, vincoli legali regionali) tramite regole basate su attributi risolte al momento della richiesta, inclusi gli attributi di ruolo dell'agente.
 #2.5.4    Livello: 3    Ruolo: V
 Verificare che i log di screening includano i punteggi di confidenza del classificatore e le etichette delle categorie di policy con lo stadio applicato (pre-prompt o post-risposta) e i metadati di tracciamento (origine, strumento o server MCP, ID agente, sessione) per la correlazione SOC e la successiva riproduzione red-team.

────────────────────────────────────────

### C2.6 Limitazione della velocità di input e prevenzione degli abusi

Gli sviluppatori dovrebbero prevenire abusi, esaurimento delle risorse e attacchi automatizzati contro i sistemi di intelligenza artificiale limitando i tassi di input e rilevando modelli di utilizzo anomali.

 #2.6.1    Livello: 1    Ruolo: D/V
 Verificare che i limiti di velocità per utente, per IP, per chiave API, per agente e per sessione/compito siano applicati per tutti gli endpoint di input e degli strumenti/MCP.
 #2.6.2    Livello: 2    Ruolo: D/V
 Verificare che i limiti di velocità burst e sostenuti siano regolati per prevenire attacchi DoS e di forza bruta, e che i budget per attività (ad esempio token, chiamate a strumenti/MCP e costi) siano applicati per i cicli di pianificazione degli agenti.
 #2.6.3    Livello: 2    Ruolo: D/V
 Verificare che i modelli di utilizzo anomali (ad esempio, richieste rapide consecutive, inondazione di input, chiamate ripetitive a strumenti/MCP che falliscono o loop ricorsivi dell’agente) attivino blocchi o escalation automatiche.
 #2.6.4    Livello: 3    Ruolo: V
 Verificare che i log di prevenzione degli abusi vengano conservati e controllati per individuare schemi di attacco emergenti, con metadati di tracciamento (origine, strumento o server MCP, ID agente, sessione).

────────────────────────────────────────

### C2.7 Validazione di Input Multi-Modale

I sistemi di intelligenza artificiale dovrebbero includere una validazione robusta per input non testuali (immagini, audio, file) per prevenire iniezioni, evasione o abuso delle risorse.

 #2.7.1    Livello: 1    Ruolo: D
 Verificare che tutti gli input non testuali (immagini, audio, file) siano validati per tipo, dimensione e formato prima dell'elaborazione, e che eventuali testi estratti (da immagine a testo o da voce a testo) e qualsiasi istruzione nascosta o incorporata (metadata, livelli, testo alternativo, commenti) siano trattati come non affidabili secondo il punto 2.1.1.
 #2.7.2    Livello: 2    Ruolo: D/V
 Verificare che i file vengano analizzati per malware e payload steganografici prima dell'ingestione e che qualsiasi contenuto attivo (come script o macro) venga rimosso o che il file venga messo in quarantena.
 #2.7.3    Livello: 2    Ruolo: D/V
 Verificare che gli input immagine/audio vengano controllati per perturbazioni avversarie o schemi di attacco noti, e che le rilevazioni attivino un sistema di controllo (bloccare o degradare le capacità) prima dell'uso del modello.
 #2.7.4    Livello: 3    Ruolo: V
 Verificare che i fallimenti nella validazione degli input multi-modali vengano registrati e attivino avvisi per le indagini, con metadata di tracciamento (origine, strumento o server MCP, ID agente, sessione).
 #2.7.5    Livello: 2    Ruolo: D/V
 Verificare che il rilevamento degli attacchi cross-modali identifichi attacchi coordinati che coinvolgono più tipi di input (ad esempio, payload steganografici nelle immagini combinati con iniezione di prompt nel testo) mediante regole di correlazione e generazione di allarmi, e che le rilevazioni confermate vengano bloccate o richiedano l'approvazione HITL (human-in-the-loop).
 #2.7.6    Livello: 3    Ruolo: D/V
 Verificare che i fallimenti di validazione multi-modale attivino una registrazione dettagliata che includa tutte le modalità di input, i risultati della validazione, i punteggi delle minacce e i metadati di traccia (fonte, strumento o server MCP, ID agente, sessione).
────────────────────────────────────────

### C2.8 Rilevamento Adattativo delle Minacce in Tempo Reale

Gli sviluppatori dovrebbero utilizzare sistemi avanzati di rilevamento delle minacce per l'IA che si adattano a nuovi modelli di attacco e forniscono protezione in tempo reale con il matching di pattern compilati.

 #2.8.1    Livello: 1    Ruolo: D/V
 Verificare che il pattern matching (ad esempio, espressioni regolari compilate) venga eseguito su tutti gli input e output (inclusi superfici di tool/MCP) con un impatto minimo sulla latenza.
 #2.8.3    Livello: 2    Ruolo: D/V
 Verificare che i modelli di rilevamento adattativi regolino la sensibilità in base all'attività recente di attacco e vengano aggiornati con nuovi modelli in tempo reale, attivando risposte adattive al rischio (ad esempio disabilitare strumenti, ridurre il contesto o richiedere l'approvazione HITL).
 #2.8.4    Livello: 3    Ruolo: D/V
 Verificare che la precisione del rilevamento venga migliorata tramite l’analisi contestuale della cronologia utente, della fonte e del comportamento della sessione, inclusi i metadati di traccia (fonte, strumento o server MCP, ID agente, sessione).
 #2.8.5    Livello: 3    Ruolo: D/V
 Verificare che le metriche di prestazione della rilevazione (tasso di rilevamento, tasso di falsi positivi, latenza di elaborazione) siano monitorate e ottimizzate continuamente, includendo il tempo di blocco e la fase (pre-prompt/post-risposta).

### Riferimenti

OWASP LLM01:2025 Prompt Injection
LLM Prompt Injection Prevention Cheat Sheet
MITRE ATLAS : Adversarial Input Detection
Mitigate jailbreaks and prompt injections

## Gestione del Ciclo di Vita del Modello C3 e Controllo delle Modifiche

### Obiettivo di Controllo

I sistemi di intelligenza artificiale devono implementare processi di controllo delle modifiche che impediscano modifiche non autorizzate o non sicure del modello di raggiungere la produzione. Questo controllo garantisce l'integrità del modello durante l'intero ciclo di vita--dallo sviluppo al dispiegamento fino alla disattivazione--consentendo una risposta rapida agli incidenti e mantenendo la responsabilità per tutte le modifiche.

Obiettivo principale di sicurezza: Solo modelli autorizzati e convalidati raggiungono la produzione impiegando processi controllati che mantengono integrità, tracciabilità e recuperabilità.

────────────────────────────────────────

### C3.1 Autorizzazione e Integrità del Modello

Solo i modelli autorizzati con integrità verificata raggiungono gli ambienti di produzione.

 #3.1.1    Livello: 1    Ruolo: D/V
 Verificare che tutti gli artefatti del modello (pesi, configurazioni, tokenizer) siano firmati crittograficamente da entità autorizzate prima della distribuzione.
 #3.1.2    Livello: 2    Ruolo: V
 Verificare che il tracciamento delle dipendenze mantenga un inventario in tempo reale che consenta l’identificazione di tutti i sistemi consumatori.
 #3.1.3    Livello: 3    Ruolo: D/V
 Verificare che i record di provenienza del modello includano l'identità dell'entità autorizzante, i checksum dei dati di addestramento, i risultati dei test di validazione con stato di superamento/insuccesso e un timestamp di creazione.

────────────────────────────────────────

### C3.2 Validazione e Test del Modello

I modelli devono superare le convalide di sicurezza e protezione definite prima della distribuzione.

 #3.2.1    Livello: 1    Ruolo: D/V
 Verificare che i modelli vengano sottoposti a test di sicurezza automatizzati che includano la convalida degli input, la sanificazione degli output e valutazioni di sicurezza con soglie di superamento/fallimento predefinite dall'organizzazione prima della distribuzione.
 #3.2.2    Livello: 1    Ruolo: V
 Verificare che tutte le modifiche al modello (deployment, configurazione, pensionamento) generino registri di audit immutabili che includano un timestamp, un'identità dell'attore autenticata, un tipo di modifica e gli stati precedente/dopo.
 #3.2.3    Livello: 2    Ruolo: D/V
 Verificare che i fallimenti di validazione blocchino automaticamente il deployment del modello dopo l'approvazione esplicita di una deroga da parte del personale autorizzato pre-designato con giustificazioni aziendali documentate.

────────────────────────────────────────

### C3.3 Distribuzione Controllata e Ripristino

Le distribuzioni dei modelli devono essere controllate, monitorate e reversibili.

 #3.3.1    Livello: 1    Ruolo: D/V
 Verificare che i processi di distribuzione convalidino le firme crittografiche e calcolino checksum di integrità prima dell'attivazione del modello, interrompendo la distribuzione in caso di discrepanze.
 #3.3.2    Livello: 1    Ruolo: D
 Verificare che le distribuzioni in produzione implementino meccanismi di rollout graduale (deployment canary, deployment blue-green) con trigger di rollback automatici basati su tassi di errore, soglie di latenza o criteri di allerta di sicurezza predefiniti.
 #3.3.3    Livello: 2    Ruolo: D/V
 Verificare che le funzionalità di rollback ripristinino lo stato completo del modello (pesi, configurazioni, dipendenze) in modo atomico.
 #3.3.4    Livello: 3    Ruolo: D/V
 Verificare che le capacità di spegnimento di emergenza del modello possano disabilitare gli endpoint del modello entro una risposta predefinita.

────────────────────────────────────────

### C3.4 Pratiche di Sviluppo Sicuro

I processi di sviluppo e addestramento del modello devono seguire pratiche sicure per prevenire compromissioni.

 #3.4.1    Livello: 1    Ruolo: D/V
 Verificare che gli ambienti di sviluppo, test e produzione del modello siano separati fisicamente o logicamente. Essi non devono condividere infrastrutture, devono avere controlli di accesso distinti e archivi di dati isolati.
 #3.4.2    Livello: 1    Ruolo: D
 Verificare che gli artefatti di sviluppo del modello (iperparametri, script di addestramento, file di configurazione, modelli di prompt, ecc.) siano archiviati nel controllo delle versioni e richiedano l'approvazione della revisione tra pari prima dell'uso nell'addestramento.
 #3.4.3    Livello: 2    Ruolo: D/V
 Verificare che l'addestramento e il fine-tuning del modello avvengano in ambienti isolati con accesso di rete controllato.
 #3.4.4    Livello: 2    Ruolo: D
 Verificare che le fonti dei dati di addestramento siano validate tramite controlli di integrità e autenticate tramite fonti affidabili con una documentata catena di custodia prima dell’utilizzo nello sviluppo del modello.

────────────────────────────────────────

### Ritiro e dismissione del modello C3.5

I modelli devono essere dismessi in modo sicuro quando non sono più necessari o quando vengono identificati problemi di sicurezza.

 #3.5.1    Livello: 1    Ruolo: D/V
 Verificare che gli artefatti del modello dismesso siano cancellati in modo sicuro utilizzando la cancellazione crittografica sicura.
 #3.5.2    Livello: 2    Ruolo: V
 Verificare che gli eventi di dismissione del modello siano registrati con data e ora e identità dell'attore, e che le firme del modello siano revocate per prevenire il riutilizzo.

────────────────────────────────────────

### Riferimenti

MITRE ATLAS
MLOps Principles
Reinforcement fine-tuning
What is AI adversarial robustness? – IBM Research

## Sicurezza dell'infrastruttura, della configurazione e del deployment di C4

### Obiettivo di Controllo

L'infrastruttura AI deve essere rafforzata contro l'escalation dei privilegi, la manomissione della catena di approvvigionamento e i movimenti laterali tramite una configurazione sicura, l'isolamento in fase di esecuzione, pipeline di distribuzione affidabili e monitoraggio completo. Solo i componenti dell'infrastruttura validati e autorizzati raggiungono la produzione attraverso processi controllati che garantiscono sicurezza, integrità e tracciabilità.

Obiettivo Principale di Sicurezza: Solo i componenti dell'infrastruttura firmati criptograficamente e sottoposti a scansione delle vulnerabilità raggiungono la produzione attraverso pipeline di validazione automatizzate che applicano le politiche di sicurezza e mantengono registri di controllo immutabili.

────────────────────────────────────────

### C4.1 Isolamento dell'Ambiente di Esecuzione

Prevenire le fughe dai container e l'escalation dei privilegi tramite primitive di isolamento a livello di sistema operativo.

 #4.1.1    Livello: 1    Ruolo: D/V
 Verificare che tutti i carichi di lavoro AI vengano eseguiti con i permessi minimi necessari sul sistema operativo, ad esempio rimuovendo le capacità Linux non necessarie nel caso di un container.
 #4.1.2    Livello: 1    Ruolo: D/V
 Verificare che i carichi di lavoro siano protetti da tecnologie che limitano lo sfruttamento come sandboxing, profili seccomp, AppArmor, SELinux o simili, e che la configurazione sia appropriata.
 #4.1.3    Livello: 2    Ruolo: D/V
 Verificare che i carichi di lavoro vengano eseguiti con un filesystem root di sola lettura e che tutte le mount scrivibili siano definite esplicitamente e protette con opzioni restrittive (ad esempio, noexec, nosuid, nodev).
 #4.1.4    Livello: 2    Ruolo: D/V
 Verificare che il monitoraggio in tempo reale rilevi i comportamenti di escalation dei privilegi e di fuga dal container e che termini automaticamente i processi responsabili.
 #4.1.5    Livello: 3    Ruolo: D/V
 Verificare che i carichi di lavoro AI ad alto rischio vengano eseguiti in ambienti isolati a livello hardware (ad esempio, TEEs, hypervisor affidabili o nodi bare-metal) solo dopo un'attestazione remota riuscita.

────────────────────────────────────────

### C4.2 Pipeline di Build e Deployment Sicuri

Garantire l'integrità crittografica e la sicurezza della catena di approvvigionamento attraverso build riproducibili e artefatti firmati.

 #4.2.1    Livello: 1    Ruolo: D/V
 Verificare che le build siano riproducibili e producano metadati di provenienza firmati, come appropriato per gli artefatti della build, che possano essere verificati in modo indipendente.
 #4.2.2    Livello: 2    Ruolo: D/V
 Verificare che le build producano una bill of materials (SBOM) del software e siano firmate prima di essere accettate per il deployment.
 #4.2.3    Livello: 2    Ruolo: D/V
 Verificare che le firme degli artifact di build (ad esempio, le immagini container) e i metadati di provenienza siano convalidati al momento del deployment, e che gli artifact non verificati vengano rifiutati.

────────────────────────────────────────

### C4.3 Sicurezza di Rete e Controllo degli Accessi

Implementare una rete a fiducia zero con politiche di negazione predefinite e comunicazioni crittografate.

 #4.3.1    Livello: 1    Ruolo: D/V
 Verificare che le policy di rete applichino il rifiuto predefinito per l’ingresso e l’uscita, consentendo esplicitamente solo i servizi necessari.
 #4.3.2    Livello: 1    Ruolo: D/V
 Verificare che i protocolli di accesso amministrativo (ad es., SSH, RDP) e l'accesso ai servizi di metadata cloud siano limitati e richiedano un’autenticazione forte.
 #4.3.3    Livello: 2    Ruolo: D/V
 Verificare che il traffico in uscita sia limitato a destinazioni approvate e che tutte le richieste siano registrate.
 #4.3.4    Livello: 2    Ruolo: D/V
 Verificare che la comunicazione tra servizi utilizzi mutual TLS con validazione del certificato e rotazione automatica regolare.
 #4.3.5    Livello: 2    Ruolo: D/V
 Verificare che i carichi di lavoro e gli ambienti AI (sviluppo, test, produzione) operino in segmenti di rete isolati (VPC/VNet) senza accesso diretto a Internet e senza ruoli IAM condivisi, gruppi di sicurezza o connettività tra ambienti.

### C4.4 Gestione dei Segreti e delle Chiavi Criptografiche

Proteggi i segreti e le chiavi crittografiche con uno storage sicuro, rotazione automatica e solidi controlli di accesso.

 #4.4.1    Livello: 1    Ruolo: D/V
 Verificare che i segreti siano archiviati in un sistema dedicato di gestione dei segreti con crittografia a riposo e isolati dai carichi di lavoro delle applicazioni.
 #4.4.2    Livello: 1    Ruolo: D/V
 Verificare che le chiavi crittografiche siano generate e archiviate in moduli supportati da hardware (ad esempio, HSM, KMS cloud).
 #4.4.3    Livello: 1    Ruolo: D/V
 Verificare che l'accesso ai segreti di produzione richieda un'autenticazione forte.
 #4.4.4    Livello: 1    Ruolo: D/V
 Verificare che i segreti vengano distribuiti alle applicazioni durante l'esecuzione tramite un sistema dedicato di gestione dei segreti. I segreti non devono mai essere incorporati nel codice sorgente, nei file di configurazione, negli artefatti di build, nelle immagini dei container o nelle variabili d'ambiente.
 #4.4.5    Livello: 2    Ruolo: D/V
 Verificare che la rotazione dei segreti sia automatizzata.

────────────────────────────────────────

### C4.5 Isolamento e Validazione del Carico di Lavoro AI

Isola i modelli di IA non affidabili in sandbox sicure e proteggi i carichi di lavoro sensibili di IA utilizzando ambienti di esecuzione affidabili (TEE) e tecnologie di calcolo confidenziale.

 #4.5.1    Livello: 1    Ruolo: D/V
 Verificare che i modelli di AI esterni o non affidabili vengano eseguiti in sandbox isolate.
 #4.5.2    Livello: 1    Ruolo: D/V
 Verificare che i carichi di lavoro in sandbox non abbiano connettività di rete in uscita per impostazione predefinita, con qualsiasi accesso necessario definito esplicitamente.
 #4.5.3    Livello: 2    Ruolo: D/V
 Verificare che l'attestazione del carico di lavoro venga eseguita prima del caricamento del modello o del carico di lavoro, garantendo una prova crittografica di un ambiente di esecuzione attendibile.
 #4.5.4    Livello: 3    Ruolo: D/V
 Verificare che i carichi di lavoro confidenziali vengano eseguiti all'interno di un ambiente di esecuzione affidabile (TEE) che fornisce isolamento garantito dall'hardware, crittografia della memoria e protezione dell'integrità.
 #4.5.5    Livello: 3    Ruolo: D/V
 Verificare che i servizi di inferenza riservati prevengano l'estrazione del modello tramite calcolo crittografato con pesi del modello sigillati ed esecuzione protetta.
 #4.5.6    Livello: 3    Ruolo: D/V
 Verificare che l'orchestrazione degli ambienti di esecuzione attendibili includa la gestione del ciclo di vita, l'attestazione remota e i canali di comunicazione crittografati.
 #4.5.7    Livello: 3    Ruolo: D/V
 Verificare che il calcolo multipartito sicuro (SMPC) consenta l’addestramento collaborativo dell’IA senza esporre set di dati individuali o parametri del modello.

────────────────────────────────────────

### C4.6 Gestione delle risorse dell'infrastruttura AI, backup e ripristino

Prevenire attacchi di esaurimento delle risorse e garantire una distribuzione equa delle risorse tramite quote e monitoraggio. Mantenere la resilienza dell'infrastruttura attraverso backup sicuri, procedure di recupero testate e capacità di disaster recovery.

 #4.6.1    Livello: 2    Ruolo: D/V
 Verificare che il consumo di risorse del carico di lavoro sia limitato in modo appropriato con, ad esempio, ResourceQuota di Kubernetes o strumenti simili per mitigare gli attacchi di Denial of Service.
 #4.6.2    Livello: 2    Ruolo: D/V
 Verificare che l'esaurimento delle risorse attivi le protezioni automatiche (ad esempio, limitazione della velocità o isolamento del carico di lavoro) una volta superate le soglie definite di CPU, memoria o richieste.
 #4.6.3    Livello: 2    Ruolo: D/V
 Verificare che i sistemi di backup operino in reti isolate con credenziali separate e che il sistema di archiviazione sia gestito in una rete air-gapped oppure implementi la protezione WORM (write-once-read-many) contro modifiche non autorizzate.

────────────────────────────────────────

### C4.7 Sicurezza dell'hardware AI

Proteggi i componenti hardware specifici per l'IA, inclusi GPU, TPU e acceleratori AI specializzati.

 #4.7.1    Livello: 2    Ruolo: D/V
 Verificare che prima dell'esecuzione del carico di lavoro, l'integrità dell'acceleratore AI sia convalidata utilizzando meccanismi di attestazione basati su hardware (ad esempio, TPM, DRTM o equivalenti).
 #4.7.2    Livello: 2    Ruolo: D/V
 Verificare che la memoria dell'acceleratore (GPU) sia isolata tra i carichi di lavoro tramite meccanismi di partizionamento con la sanificazione della memoria tra i processi.
 #4.7.3    Livello: 3    Ruolo: D/V
 Verificare che i moduli di sicurezza hardware (HSM) proteggano i pesi del modello AI e le chiavi crittografiche con certificazione FIPS 140-3 Livello 3 o Common Criteria EAL4+.
 #4.7.4    Livello: 2    Ruolo: D/V
 Verificare che il firmware dell'acceleratore (GPU/TPU/NPUs) sia bloccato a una versione specifica, firmato e attestato all'avvio; i firmware non firmati o di debug devono essere bloccati.
 #4.7.5    Livello: 2    Ruolo: D/V
 Verificare che la VRAM e la memoria on-package siano azzerate tra i lavori/tenant e che le politiche di reset del dispositivo prevengano la persistenza dei dati tra tenant.
 #4.7.6    Livello: 2    Ruolo: D/V
 Verificare che le funzionalità di partizionamento/isolation (ad esempio, partizionamento MIG/VM) siano applicate per ogni tenant e impediscano l'accesso alla memoria peer-to-peer tra le partizioni.
 #4.7.7    Livello: 3    Ruolo: D/V
 Verificare che le interconnessioni degli accelerator (NVLink/PCIe/InfiniBand/RDMA/NCCL) siano limitate a topologie approvate e a endpoint autenticati; i collegamenti in chiaro tra tenant diversi non sono consentiti.
 #4.7.8    Livello: 3    Ruolo: D
 Verificare che la telemetria dell'acceleratore (potenza, temperature, ECC, contatori di prestazioni) venga esportata a SIEM/OTel e che vengano generati avvisi su anomalie indicative di canali laterali o canali occulti.

────────────────────────────────────────

### C4.8 Sicurezza dell'AI Edge e Distribuita

Distribuzioni AI sicure distribuite, inclusi edge computing, apprendimento federato e architetture multisito.

 #4.8.1    Livello: 2    Ruolo: D/V
 Verificare che i dispositivi edge AI si autentichino all'infrastruttura centrale utilizzando mutual TLS.
 #4.8.2    Livello: 2    Ruolo: D/V
 Verificare che i dispositivi edge implementino il secure boot con firme verificate e protezione rollback per prevenire attacchi di downgrade del firmware.
 #4.8.3    Livello: 3    Ruolo: D/V
 Verificare che il coordinamento dell'IA distribuita utilizzi meccanismi di consenso tolleranti ai guasti bizantini con validazione dei partecipanti e rilevamento di nodi malevoli.
 #4.8.4    Livello: 3    Ruolo: D/V
 Verificare che la comunicazione edge-to-cloud supporti la limitazione della larghezza di banda, la compressione dei dati e il funzionamento sicuro offline con archiviazione locale crittografata.

────────────────────────────────────────

### Riferimenti

NIST Cybersecurity Framework 2.0
CIS Controls v8
Kubernetes Security Best Practices
Cloud Security Alliance: Cloud Controls Matrix
ENISA: Secure Infrastructure Design
ISO 27001:2022 Information Security Management
NIST AI Risk Management Framework

## Controllo Accessi C5 e Identità per Componenti e Utenti AI

### Obiettivo di Controllo

Un controllo degli accessi efficace per i sistemi di intelligenza artificiale richiede una gestione robusta delle identità, un'autorizzazione contestuale e un'applicazione in tempo reale secondo i principi zero-trust. Questi controlli garantiscono che umani, servizi e agenti autonomi interagiscano solo con modelli, dati e risorse computazionali all'interno di ambiti esplicitamente concessi, con capacità di verifica continua e audit.

────────────────────────────────────────

### C5.1 Gestione dell'Identità e Autenticazione

Stabilire identità supportate da crittografia per tutte le entità con autenticazione a più fattori.

 #5.1.1    Livello: 1    Ruolo: D/V
 Verificare che tutti gli utenti umani e i service principal si autentichino tramite un provider di identità aziendale centralizzato (IdP) utilizzando i protocolli OIDC e/o SAML.
 #5.1.2    Livello: 1    Ruolo: D/V
 Verificare che le operazioni ad alto rischio (deploy del modello, esportazione dei pesi, accesso ai dati di addestramento, modifiche alla configurazione di produzione) richiedano l'autenticazione multi-fattore o un'autenticazione step-up con la ri-validazione della sessione.
 #5.1.3    Livello: 3    Ruolo: D/V
 Verificare che gli agenti AI federati si autentichino tramite asserzioni JWT firmate che abbiano una durata massima di 24 ore e includano una prova crittografica di origine.

────────────────────────────────────────

### C5.2 Autorizzazione e Politica

Implementare controlli di accesso per tutte le risorse AI con modelli di autorizzazione espliciti e tracce di audit.

 #5.2.1    Livello: 1    Ruolo: D/V
 Verificare che ogni risorsa AI (dataset, modelli, endpoint, collezioni di vettori, indici di embedding, istanze di calcolo) applichi controlli di accesso basati sui ruoli con liste di consentiti esplicite e politiche di negazione predefinite.
 #5.2.2    Livello: 1    Ruolo: V
 Verificare che tutte le modifiche al controllo degli accessi siano registrate in modo immutabile con timestamp, identità degli attori, identificatori delle risorse e modifiche alle autorizzazioni.
 #5.2.3    Livello: 2    Ruolo: D
 Verificare che le etichette di classificazione dei dati (PII, PHI, proprietarie, ecc.) si propaghino automaticamente alle risorse derivate (embedding, cache dei prompt, output del modello).
 #5.2.4    Livello: 2    Ruolo: D/V
 Verificare che i tentativi di accesso non autorizzati e gli eventi di escalation dei privilegi attivino avvisi in tempo reale con metadati contestuali.
 #5.2.5    Livello: 1    Ruolo: D/V
 Verificare che le decisioni di autorizzazione siano esternalizzate a un motore di policy dedicato (OPA, Cedar o equivalente).
 #5.2.6    Livello: 1    Ruolo: D/V
 Verificare che le policy valutino gli attributi dinamici in fase di esecuzione, inclusi ruolo o gruppo dell'utente, classificazione della risorsa, contesto della richiesta, isolamento del tenant e vincoli temporali.
 #5.2.7    Livello: 3    Ruolo: D/V
 Verificare che i valori di time-to-live (TTL) della cache delle policy non superino i 5 minuti per le risorse ad alta sensibilità e 1 ora per le risorse standard con capacità di invalidamento della cache.

────────────────────────────────────────

### C5.3 Applicazione della sicurezza in fase di interrogazione

Implementare controlli di sicurezza a livello di database con filtri obbligatori e politiche di sicurezza a livello di riga.

 #5.3.1    Livello: 1    Ruolo: D/V
 Verificare che tutte le query sui database vettoriali e SQL includano filtri di sicurezza obbligatori (ID del tenant, etichette di sensibilità, ambito utente) applicati a livello del motore di database.
 #5.3.2    Livello: 1    Ruolo: D/V
 Verificare che le politiche di sicurezza a livello di riga e la mascheratura a livello di campo siano abilitate con l’ereditarietà delle politiche per tutti i database vettoriali, gli indici di ricerca e i dataset di addestramento.
 #5.3.3    Livello: 2    Ruolo: D
 Verificare che le valutazioni di autorizzazione fallite interrompano immediatamente le query e restituiscano codici di errore di autorizzazione espliciti.
 #5.3.4    Livello: 3    Ruolo: D/V
 Verificare che i meccanismi di ritentativo delle query rivalutino le politiche di autorizzazione per tenere conto delle modifiche dinamiche delle autorizzazioni nelle sessioni utente attive.

────────────────────────────────────────

### C5.4 Filtraggio dell'Output e Prevenzione della Perdita di Dati

Implementare controlli di post-elaborazione per prevenire l'esposizione non autorizzata di dati nei contenuti generati dall'IA.

 #5.4.1    Livello: 1    Ruolo: D/V
 Verificare che i meccanismi di filtraggio post-inferenza scansionino e oscurino le informazioni personali non autorizzate, le informazioni classificate e i dati proprietari prima di consegnare il contenuto ai richiedenti.
 #5.4.2    Livello: 1    Ruolo: D/V
 Verificare che citazioni, riferimenti e attribuzioni di fonte nei risultati del modello siano convalidati rispetto ai diritti del chiamante e rimossi se viene rilevato un accesso non autorizzato.
 #5.4.3    Livello: 2    Ruolo: D
 Verificare che le restrizioni sul formato di output (PDF sanitizzati, immagini con metadati rimossi, tipi di file approvati) siano applicate in base ai livelli di autorizzazione dell'utente e alle classificazioni dei dati.

────────────────────────────────────────

### C5.5 Isolamento Multi-Tenant

Garantire l'isolamento crittografico e logico tra i tenant in un'infrastruttura AI condivisa.

 #5.5.1    Livello: 1    Ruolo: D/V
 Verificare che gli spazi di memoria, gli archivi di embedding, le voci della cache e i file temporanei siano segregati per namespace per ogni tenant, con una cancellazione sicura in caso di eliminazione del tenant o terminazione della sessione.
 #5.5.2    Livello: 1    Ruolo: D/V
 Verificare che ogni richiesta API includa un identificatore tenant autenticato, convalidato crittograficamente rispetto al contesto della sessione e alle autorizzazioni dell'utente.
 #5.5.3    Livello: 2    Ruolo: D
 Verificare che le policy di rete implementino regole di default-deny per la comunicazione cross-tenant all'interno delle service mesh e delle piattaforme di orchestrazione dei container.
 #5.5.4    Livello: 3    Ruolo: D
 Verificare che le chiavi di crittografia siano uniche per ogni tenant con supporto per chiavi gestite dal cliente (CMK) e isolamento crittografico tra gli archivi dati dei tenant.

────────────────────────────────────────

### C5.6 Autorizzazione dell'Agente Autonomo

Controlla le autorizzazioni per agenti di IA e sistemi autonomi tramite token di capacità con ambito definito e autorizzazione continua.

 #5.6.1    Livello: 1    Ruolo: D/V
 Verificare che gli agenti autonomi ricevano token di capacità delimitati che enumerano esplicitamente le azioni consentite, le risorse accessibili, i limiti temporali e i vincoli operativi.
 #5.6.2    Livello: 1    Ruolo: D/V
 Verificare che le capacità ad alto rischio (accesso al file system, esecuzione di codice, chiamate API esterne, transazioni finanziarie) siano disabilitate di default e richiedano un'autorizzazione esplicita.
 #5.6.3    Livello: 2    Ruolo: D
 Verificare che i token di capacità siano legati alle sessioni utente, includano una protezione di integrità crittografica e garantire che non possano essere memorizzati o riutilizzati in scenari offline.
 #5.6.4    Livello: 2    Ruolo: V
 Verificare che le azioni avviate dall'agente siano soggette ad autorizzazione tramite un motore di policy ABAC.

────────────────────────────────────────

### Riferimenti

NIST SP 800-162: Guide to Attribute Based Access Control (ABAC)
NIST SP 800-207: Zero Trust Architecture
NIST SP 800-63-3: Digital Identity Guidelines
NIST IR 8360: Machine Learning for Access Control Policy Verification

## C6 Sicurezza della catena di approvvigionamento per modelli, framework e dati

### Obiettivo di Controllo

Gli attacchi alla supply chain dell'AI sfruttano modelli, framework o dataset di terze parti per inserire backdoor, bias o codice sfruttabile. Questi controlli forniscono una provenienza end-to-end, gestione delle vulnerabilità e monitoraggio per proteggere l'intero ciclo di vita del modello.

────────────────────────────────────────

### C6.1 Verifica e Provenienza del Modello Preaddestrato

Valutare e autenticare l'origine dei modelli di terze parti, le licenze e i comportamenti nascosti prima di qualsiasi messa a punto o distribuzione.

 #6.1.1    Livello: 1    Ruolo: D/V
 Verificare che ogni artefatto di modello di terze parti includa un record di provenienza firmato che identifichi il repository di origine e l'hash del commit.
 #6.1.2    Livello: 1    Ruolo: D/V
 Verificare che i modelli siano analizzati per rilevare livelli dannosi o trigger Trojan mediante strumenti automatizzati prima dell'importazione.
 #6.1.3    Livello: 2    Ruolo: D
 Verificare che il fine-tuning tramite transfer learning superi la valutazione avversaria per rilevare comportamenti nascosti.
 #6.1.4    Livello: 2    Ruolo: V
 Verificare che le licenze del modello, i tag di controllo delle esportazioni e le dichiarazioni sull'origine dei dati siano registrati in una voce ML-BOM.
 #6.1.5    Livello: 3    Ruolo: D/V
 Verificare che i modelli ad alto rischio (pesi caricati pubblicamente, creatori non verificati) rimangano isolati fino alla revisione e approvazione da parte di un essere umano.

────────────────────────────────────────

### C6.2 Scansione del Framework e delle Librerie

Scansionare continuamente i framework e le librerie di ML per CVE e codice dannoso per mantenere sicuro lo stack di runtime.

 #6.2.1    Livello: 1    Ruolo: D/V
 Verificare che le pipeline CI eseguano scanner di dipendenze su framework di intelligenza artificiale e librerie critiche.
 #6.2.2    Livello: 1    Ruolo: D/V
 Verificare che le vulnerabilità critiche (CVSS ≥ 7.0) impediscano la promozione alle immagini di produzione.
 #6.2.3    Livello: 2    Ruolo: D
 Verificare che l'analisi statica del codice venga eseguita sulle librerie ML forkate o fornite.
 #6.2.4    Livello: 2    Ruolo: V
 Verificare che le proposte di aggiornamento del framework includano una valutazione dell'impatto sulla sicurezza che faccia riferimento ai feed pubblici CVE.
 #6.2.5    Livello: 3    Ruolo: V
 Verificare che i sensori runtime segnalino i caricamenti di librerie dinamiche imprevisti che deviano dal SBOM firmato.

────────────────────────────────────────

### C6.3 Blocco e Verifica delle Dipendenze

Blocca ogni dipendenza su digest immutabili e riproduci le build per garantire artefatti identici e privi di manomissioni.

 #6.3.1    Livello: 1    Ruolo: D/V
 Verificare che tutti i gestori di pacchetti applicano il version pinning tramite i file di blocco.
 #6.3.2    Livello: 1    Ruolo: D/V
 Verificare che vengano utilizzati digest immutabili invece di tag modificabili nei riferimenti ai container.
 #6.3.3    Livello: 2    Ruolo: D
 Verificare che i controlli di build riproducibili confrontino gli hash tra le esecuzioni CI per garantire output identici.
 #6.3.4    Livello: 2    Ruolo: V
 Verificare che le attestazioni di build siano archiviate per 18 mesi per la tracciabilità dell'audit.
 #6.3.5    Livello: 3    Ruolo: D
 Verificare che le dipendenze scadute attivino PR automatiche per aggiornare o forkare le versioni bloccate.

────────────────────────────────────────

### C6.4 Applicazione di Fonte Affidabile

Consentire il download degli artefatti solo da fonti approvate dall'organizzazione e verificati criptograficamente e bloccare tutto il resto.

 #6.4.1    Livello: 1    Ruolo: D/V
 Verificare che i pesi del modello, i set di dati e i container vengano scaricati solo da domini approvati o registri interni.
 #6.4.2    Livello: 1    Ruolo: D/V
 Verificare che le firme Sigstore/Cosign convalidino l'identità dell'editore prima che gli artefatti vengano memorizzati nella cache locale.
 #6.4.3    Livello: 2    Ruolo: D
 Verificare che i proxy di uscita blocchino i download di artifact non autenticati per applicare la politica della fonte attendibile.
 #6.4.4    Livello: 2    Ruolo: V
 Verificare che le liste di autorizzazione del repository siano riviste trimestralmente con evidenza della giustificazione commerciale per ogni voce.
 #6.4.5    Livello: 3    Ruolo: V
 Verificare che le violazioni della policy attivino la messa in quarantena degli artifact e il rollback delle esecuzioni di pipeline dipendenti.

────────────────────────────────────────

### C6.5 Valutazione del rischio dei dataset di terze parti

Valutare i dataset esterni per avvelenamento, bias e conformità legale, e monitorarli durante tutto il loro ciclo di vita.

 #6.5.1    Livello: 1    Ruolo: D/V
 Verificare che i dataset esterni siano sottoposti a una valutazione del rischio di avvelenamento (ad esempio, impronta digitale dei dati, rilevamento di valori anomali).
 #6.5.2    Livello: 1    Ruolo: D
 Verificare che le metriche di bias (parità demografica, pari opportunità) siano calcolate prima dell'approvazione del dataset.
 #6.5.3    Livello: 2    Ruolo: V
 Verificare che la provenienza e i termini di licenza per i set di dati siano registrati nelle voci ML‑BOM.
 #6.5.4    Livello: 2    Ruolo: V
 Verificare che il monitoraggio periodico rilevi il drift o la corruzione nei dataset ospitati.
 #6.5.5    Livello: 3    Ruolo: D
 Verificare che i contenuti non consentiti (copyright, dati personali identificabili) siano rimossi tramite cancellazione automatica prima dell'addestramento.

────────────────────────────────────────

### C6.6 Monitoraggio degli Attacchi alla Catena di Fornitura

Rileva precocemente le minacce alla catena di approvvigionamento tramite feed CVE, analisi dei log di audit e simulazioni red-team.

 #6.6.1    Livello: 1    Ruolo: V
 Verificare che i log di audit CI/CD vengano inviati allo SIEM per il rilevamento di pull di pacchetti anomali o passaggi di build manomessi.
 #6.6.2    Livello: 2    Ruolo: D
 Verificare che i playbook di risposta agli incidenti includano procedure di rollback per modelli o librerie compromessi.
 #6.6.3    Livello: 3    Ruolo: V
 Verificare che i tag di arricchimento di threat‑intel identifichino indicatori specifici per ML (ad esempio, IoC di avvelenamento del modello) nella gestione delle segnalazioni.

────────────────────────────────────────

### C6.7 ML‑BOM per gli Artefatti del Modello

Genera e firma SBOM dettagliati specifici per ML (ML-BOM) in modo che i consumatori a valle possano verificare l'integrità dei componenti al momento del deploy.

 #6.7.1    Livello: 1    Ruolo: D/V
 Verificare che ogni artefatto del modello pubblichi un ML‑BOM che elenchi dataset, pesi, iperparametri e licenze.
 #6.7.2    Livello: 1    Ruolo: D/V
 Verificare che la generazione di ML‑BOM e la firma Cosign siano automatizzate nel CI e obbligatorie per la fusione.
 #6.7.3    Livello: 2    Ruolo: D
 Verificare che i controlli di completezza ML‑BOM facciano fallire la build se manca qualsiasi metadato del componente (hash, licenza).
 #6.7.4    Livello: 2    Ruolo: V
 Verificare che i consumatori downstream possano interrogare gli ML-BOM tramite API per convalidare i modelli importati al momento del deploy.
 #6.7.5    Livello: 3    Ruolo: V
 Verificare che le ML-BOM siano sotto controllo versione e confrontate per rilevare modifiche non autorizzate.

────────────────────────────────────────

### Riferimenti

OWASP LLM03:2025 Supply Chain
MITRE ATLAS : Supply Chain Compromise
SBOM Overview – CISA
CycloneDX – Machine Learning Bill of Materials

## Comportamento del Modello C7, Controllo dell'Uscita e Garanzia di Sicurezza

### Obiettivo di Controllo

I risultati del modello devono essere strutturati, affidabili, sicuri, spiegabili e continuamente monitorati in produzione. Questo riduce le allucinazioni, le perdite di privacy, i contenuti dannosi e le azioni incontrollate, aumentando al contempo la fiducia degli utenti e la conformità normativa.

────────────────────────────────────────

### C7.1 Applicazione del formato di output

Gli schemi rigorosi, la decodifica vincolata e la convalida a valle impediscono che contenuti malformati o dannosi si propaghino.

 #7.1.1    Livello: 1    Ruolo: D/V
 Verificare che gli schemi di risposta (ad esempio, JSON Schema) siano forniti nel prompt del sistema e che ogni output venga automaticamente convalidato; gli output non conformi attivano la riparazione o il rifiuto.
 #7.1.2    Livello: 1    Ruolo: D/V
 Verificare che la decodifica vincolata (token di arresto, espressioni regolari, token massimi) sia abilitata per prevenire overflow o side-channel di iniezione del prompt.
 #7.1.3    Livello: 2    Ruolo: D/V
 Verificare che i componenti a valle considerino gli output come non attendibili e li convalidino rispetto a schemi o de-serializzatori sicuri contro le iniezioni.
 #7.1.4    Livello: 3    Ruolo: V
 Verificare che gli eventi di output improprio siano registrati, limitati in frequenza e visualizzati nel sistema di monitoraggio.

────────────────────────────────────────

### C7.2 Rilevamento e Mitigazione delle Allucinazioni

La stima dell'incertezza e le strategie di fallback limitano le risposte inventate.

 #7.2.1    Livello: 1    Ruolo: D/V
 Verificare che le probabilità logaritmiche a livello di token, l’auto-consistenza dell’ensemble o i rilevatori di allucinazioni ottimizzati assegnino un punteggio di confidenza a ogni risposta.
 #7.2.2    Livello: 1    Ruolo: D/V
 Verificare che le risposte al di sotto di una soglia di confidenza configurabile attivino flussi di lavoro di fallback (ad esempio, generazione aumentata da recupero, modello secondario o revisione umana).
 #7.2.3    Livello: 2    Ruolo: D/V
 Verificare che gli incidenti di allucinazione siano contrassegnati con metadati della causa principale e inviati alle pipeline di post-mortem e di affinamento.
 #7.2.4    Livello: 3    Ruolo: D/V
 Verificare che le soglie e i rilevatori siano ricalibrati dopo aggiornamenti importanti del modello o della base di conoscenza.
 #7.2.5    Livello: 3    Ruolo: V
 Verificare che le visualizzazioni della dashboard monitorino i tassi di allucinazione.

────────────────────────────────────────

### C7.3 Filtraggio della Sicurezza e della Privacy in Output

I filtri di policy e la copertura del red-team proteggono gli utenti e i dati riservati.

 #7.3.1    Livello: 1    Ruolo: D/V
 Verificare che i classificatori pre e post-generazione blocchino contenuti di odio, molestie, autolesionismo, estremismo e contenuti sessualmente espliciti conformi alla politica.
 #7.3.2    Livello: 1    Ruolo: D/V
 Verificare che il rilevamento di PII/PCI e la redazione automatica vengano eseguiti su ogni risposta; le violazioni comportano l'apertura di un incidente di privacy.
 #7.3.3    Livello: 2    Ruolo: D
 Verificare che i tag di riservatezza (ad esempio, segreti commerciali) si propaghino attraverso le modalità per impedire perdite in testo, immagini o codice.
 #7.3.4    Livello: 3    Ruolo: D/V
 Verificare che i tentativi di bypass del filtro o le classificazioni ad alto rischio richiedano un'approvazione secondaria o una riautenticazione dell'utente.
 #7.3.5    Livello: 3    Ruolo: D/V
 Verificare che le soglie di filtraggio riflettano le giurisdizioni legali e il contesto di età/ruolo dell'utente.

────────────────────────────────────────

### C7.4 Limitazione di Output e Azione

I limiti di velocità e le barriere di approvazione prevengono abusi e autonomia eccessiva.

 #7.4.1    Livello: 1    Ruolo: D
 Verificare che le quote per utente e per chiave API limitino le richieste, i token e i costi con back-off esponenziale sugli errori 429.
 #7.4.2    Livello: 1    Ruolo: D/V
 Verificare che le azioni privilegiate (scrittura di file, esecuzione di codice, chiamate di rete) richiedano l'approvazione basata su policy o l'intervento umano.
 #7.4.3    Livello: 2    Ruolo: D/V
 Verificare che i controlli di coerenza cross-modale garantiscano che immagini, codice e testo generati per la stessa richiesta non possano essere utilizzati per introdurre contenuti dannosi.
 #7.4.4    Livello: 2    Ruolo: D
 Verificare che la profondità di delega degli agenti, i limiti di ricorsione e le liste degli strumenti consentiti siano configurati esplicitamente.
 #7.4.5    Livello: 3    Ruolo: V
 Verificare che la violazione dei limiti generi eventi di sicurezza strutturati per l'ingestione da parte del SIEM.

────────────────────────────────────────

### C7.5 Spiegabilità dell'Output

I segnali trasparenti migliorano la fiducia degli utenti e il debug interno.

 #7.5.1    Livello: 2    Ruolo: D/V
 Verificare che i punteggi di fiducia rivolti all’utente o i riassunti brevi delle motivazioni siano esposti quando la valutazione del rischio lo ritiene opportuno.
 #7.5.2    Livello: 2    Ruolo: D/V
 Verificare che le spiegazioni generate evitino di rivelare prompt di sistema sensibili o dati proprietari.
 #7.5.3    Livello: 3    Ruolo: D
 Verificare che il sistema acquisisca le log-probabilità a livello di token o le mappe di attenzione e le memorizzi per un'ispezione autorizzata.
 #7.5.4    Livello: 3    Ruolo: V
 Verificare che gli artefatti di spiegabilità siano versionati insieme alle release del modello per garantirne la tracciabilità.

────────────────────────────────────────

### C7.6 Integrazione del Monitoraggio

L'osservabilità in tempo reale chiude il ciclo tra sviluppo e produzione.

 #7.6.1    Livello: 1    Ruolo: D
 Verificare che le metriche (violazioni dello schema, tasso di allucinazioni, tossicità, perdite di PII, latenza, costo) vengano trasmesse a una piattaforma di monitoraggio centrale.
 #7.6.2    Livello: 1    Ruolo: V
 Verificare che siano definiti soglie di allerta per ogni metrica di sicurezza, con percorsi di escalation per il personale di guardia.
 #7.6.3    Livello: 2    Ruolo: V
 Verificare che i cruscotti correlino le anomalie di output con modello/versione, flag di funzionalità e modifiche ai dati a monte.
 #7.6.4    Livello: 2    Ruolo: D/V
 Verificare che i dati di monitoraggio vengano reinseriti nel processo di retraining, fine-tuning o aggiornamento delle regole all'interno di un flusso di lavoro MLOps documentato.
 #7.6.5    Livello: 3    Ruolo: V
 Verificare che le pipeline di monitoraggio siano sottoposte a test di penetrazione e che l'accesso sia controllato per evitare la fuoriuscita di log sensibili.

────────────────────────────────────────

### 7.7 Salvaguardie dei Media Generativi

Garantire che i sistemi di intelligenza artificiale non generino contenuti multimediali illegali, dannosi o non autorizzati applicando vincoli di politica, validazione dell'output e tracciabilità.

 #7.7.1    Livello: 1    Ruolo: D/V
 Verificare che i prompt di sistema e le istruzioni per l'utente proibiscano esplicitamente la generazione di contenuti deepfake illegali, dannosi o non consensuali (ad esempio, immagini, video, audio).
 #7.7.2    Livello: 2    Ruolo: D/V
 Verificare che i prompt vengano filtrati per tentativi di generare impersonificazioni, deepfake sessualmente espliciti o media che ritraggono persone reali senza consenso.
 #7.7.3    Livello: 2    Ruolo: V
 Verificare che il sistema utilizzi hashing percettivo, rilevamento di watermark o fingerprinting per prevenire la riproduzione non autorizzata di contenuti protetti da copyright.
 #7.7.4    Livello: 3    Ruolo: D/V
 Verificare che tutti i media generati siano firmati crittograficamente, marcati con watermark o incorporati con metadati di provenienza resistenti alla manomissione per la tracciabilità a valle.
 #7.7.5    Livello: 3    Ruolo: V
 Verificare che i tentativi di bypass (ad esempio, offuscamento del prompt, gergo, formulazioni avversarie) vengano rilevati, registrati e sottoposti a limitazione della frequenza; gli abusi ripetuti devono essere segnalati ai sistemi di monitoraggio.

### Riferimenti

NIST AI Risk Management Framework
ISO/IEC 42001:2023 – AI Management System
OWASP Top-10 for Large Language Model Applications (2025)
Practical Techniques to Constrain LLM Output
Dataiku – Structured Text Generation Guide
VL-Uncertainty: Detecting Hallucinations
HaDeMiF: Hallucination Detection & Mitigation
Building Confidence in LLM Outputs
Explainable AI & LLMs
Sensitive Information Disclosure in LLMs
OpenAI Rate-Limit & Exponential Back-off
Arize AI – LLM Observability Platform

## Sicurezza della Memoria C8, degli Embeddings e del Database Vettoriale

### Obiettivo di Controllo

Le embeddings e i vettori di archiviazione fungono da "memoria attiva" dei sistemi di IA contemporanei, accettando continuamente dati forniti dagli utenti e riportandoli nei contesti del modello tramite la Generazione Arricchita da Recupero (RAG). Se lasciata senza controllo, questa memoria può divulgare informazioni personali identificabili (PII), violare il consenso o essere invertita per ricostruire il testo originale. L'obiettivo di questa famiglia di controlli è rafforzare le pipeline di memoria e i database vettoriali affinché l'accesso sia a privilegi minimi, le embeddings siano conformi alla privacy, i vettori memorizzati scadano o possano essere revocati su richiesta, e la memoria per utente non contamini mai i prompt o i completamenti di un altro utente.

────────────────────────────────────────

### C8.1 Controlli di accesso sulla memoria e sugli indici RAG

Applicare controlli di accesso dettagliati su ogni raccolta vettoriale.

 #8.1.1    Livello: 1    Ruolo: D/V
 Verificare che le regole di controllo degli accessi a livello di riga/namespace limitino le operazioni di inserimento, eliminazione e query per tenant, collezione o tag del documento.
 #8.1.2    Livello: 1    Ruolo: D/V
 Verificare che le chiavi API o i JWT contengano claims con ambito specifico (es. ID collezione, verbi di azione) e vengano ruotati almeno trimestralmente.
 #8.1.3    Livello: 2    Ruolo: D/V
 Verificare che i tentativi di escalation dei privilegi (ad esempio, query di similarità tra namespace diversi) siano rilevati e registrati in un SIEM entro 5 minuti.
 #8.1.4    Livello: 2    Ruolo: D/V
 Verificare che il database vettoriale registri il soggetto identificatore del log, l'operazione, l'ID vettore/namespace, la soglia di similarità e il conteggio dei risultati.
 #8.1.5    Livello: 3    Ruolo: V
 Verificare che le decisioni di accesso siano testate per individuare vulnerabilità di bypass ogni volta che i motori vengono aggiornati o le regole di sharding degli indici cambiano.

────────────────────────────────────────

### C8.2 Sanificazione e Validazione degli Embedding

Pre-selezionare il testo per le informazioni personali identificabili (PII), oscurare o pseudonomizzare prima della vettorizzazione, e opzionalmente post-elaborare gli embedding per eliminare segnali residui.

 #8.2.1    Livello: 1    Ruolo: D/V
 Verificare che i dati PII e regolamentati siano rilevati tramite classificatori automatici e mascherati, tokenizzati o eliminati prima dell'embedding.
 #8.2.2    Livello: 1    Ruolo: D
 Verificare che le pipeline di embedding respingano o mettano in quarantena gli input contenenti codice eseguibile o artefatti non UTF-8 che potrebbero contaminare l'indice.
 #8.2.3    Livello: 2    Ruolo: D/V
 Verificare che venga applicata una sanificazione con privacy differenziale locale o metrico agli embedding delle frasi la cui distanza da qualsiasi token PII noto scende al di sotto di una soglia configurabile.
 #8.2.4    Livello: 2    Ruolo: V
 Verificare che l'efficacia della sanificazione (ad esempio, il richiamo della redazione dei dati personali identificabili, la deriva semantica) venga convalidata almeno ogni sei mesi utilizzando corpora di riferimento.
 #8.2.5    Livello: 3    Ruolo: D/V
 Verificare che le configurazioni di sanificazione siano controllate da versioni e che le modifiche vengano sottoposte a revisione tra pari.

────────────────────────────────────────

### C8.3 Scadenza, Revoca e Cancellazione della Memoria

Il GDPR "diritto all'oblio" e leggi simili richiedono la cancellazione tempestiva; pertanto, gli archivi vettoriali devono supportare TTL, cancellazioni definitive e tomb-stoning affinché i vettori revocati non possano essere recuperati o reindicizzati.

 #8.3.1    Livello: 1    Ruolo: D/V
 Verificare che ogni vettore e record di metadata abbia un TTL o un'etichetta di conservazione esplicita rispettata dai processi di pulizia automatica.
 #8.3.2    Livello: 1    Ruolo: D/V
 Verificare che le richieste di cancellazione avviate dall’utente eliminino vettori, metadati, copie di cache e indici derivati entro 30 giorni.
 #8.3.3    Livello: 2    Ruolo: D
 Verificare che le cancellazioni logiche siano seguite da una distruzione crittografica dei blocchi di archiviazione se l'hardware lo supporta, oppure dalla distruzione della chiave del key-vault.
 #8.3.4    Livello: 3    Ruolo: D/V
 Verificare che i vettori scaduti siano esclusi dai risultati della ricerca del vicino più prossimo in meno di 500 ms dopo la scadenza.

────────────────────────────────────────

### C8.4 Prevenire l'inversione e la perdita di embedding

Le difese recenti—sovrapposizione di rumore, reti di proiezione, perturbazione del neurone della privacy e crittografia a livello di applicazione—possono ridurre i tassi di inversione a livello di token sotto il 5%.

 #8.4.1    Livello: 1    Ruolo: V
 Verificare che esista un modello di minaccia formale che copra attacchi di inversione, appartenenza e inferenza di attributi e che venga revisionato annualmente.
 #8.4.2    Livello: 2    Ruolo: D/V
 Verificare che la crittografia a livello applicativo o la crittografia ricercabile proteggano i vettori da letture dirette da parte degli amministratori dell'infrastruttura o del personale cloud.
 #8.4.3    Livello: 3    Ruolo: V
 Verificare che i parametri di difesa (ε per DP, rumore σ, rango di proiezione k) bilancino la privacy ≥ 99% di protezione dei token e l’utilità ≤ 3% di perdita di accuratezza.
 #8.4.4    Livello: 3    Ruolo: D/V
 Verificare che le metriche di resilienza all’inversione facciano parte delle soglie di rilascio per gli aggiornamenti del modello, con budget di regressione definiti.

────────────────────────────────────────

### C8.5 Applicazione dell'Ambito per la Memoria Specifica dell'Utente

La fuga di dati tra tenant rimane un rischio principale per RAG: query di similarità filtrate in modo improprio possono far emergere i documenti privati di un altro cliente.

 #8.5.1    Livello: 1    Ruolo: D/V
 Verificare che ogni query di recupero venga filtrata successivamente in base all'ID del tenant/utente prima di essere passata al prompt LLM.
 #8.5.2    Livello: 1    Ruolo: D
 Verificare che i nomi delle collezioni o gli ID con namespace siano salati per utente o tenant in modo che i vettori non possano collidere tra gli ambiti.
 #8.5.3    Livello: 2    Ruolo: D/V
 Verificare che i risultati di similarità superiori a una soglia di distanza configurabile ma al di fuori dell'ambito del chiamante vengano scartati e attivino allarmi di sicurezza.
 #8.5.4    Livello: 2    Ruolo: V
 Verificare che i test di stress multi-tenant simulino query avversarie che tentano di recuperare documenti fuori ambito e dimostrino l’assenza totale di fuoriuscite.
 #8.5.5    Livello: 3    Ruolo: D/V
 Verificare che le chiavi di crittografia siano segregate per tenant, garantendo l'isolamento crittografico anche se lo storage fisico è condiviso.

────────────────────────────────────────

### C8.6 Sicurezza Avanzata del Sistema di Memoria

Controlli di sicurezza per architetture di memoria sofisticate, inclusi memoria episodica, semantica e di lavoro, con requisiti specifici di isolamento e validazione.

 #8.6.1    Livello: 1    Ruolo: D/V
 Verificare che i diversi tipi di memoria (episodica, semantica, di lavoro) abbiano contesti di sicurezza isolati con controlli di accesso basati sui ruoli, chiavi di crittografia separate e modelli di accesso documentati per ciascun tipo di memoria.
 #8.6.2    Livello: 2    Ruolo: D/V
 Verificare che i processi di consolidamento della memoria includano la validazione della sicurezza per prevenire l'iniezione di memorie dannose attraverso la sanificazione dei contenuti, la verifica delle fonti e i controlli di integrità prima della memorizzazione.
 #8.6.3    Livello: 2    Ruolo: D/V
 Verificare che le interrogazioni di recupero della memoria siano convalidate e sanificate per prevenire l'estrazione di informazioni non autorizzate tramite l'analisi dei modelli di interrogazione, l'applicazione del controllo degli accessi e il filtraggio dei risultati.
 #8.6.4    Livello: 3    Ruolo: D/V
 Verificare che i meccanismi di cancellazione della memoria eliminino in modo sicuro le informazioni sensibili con garanzie di cancellazione crittografica utilizzando la cancellazione delle chiavi, la sovrascrittura multipla o la cancellazione sicura basata su hardware con certificati di verifica.
 #8.6.5    Livello: 3    Ruolo: D/V
 Verificare che l'integrità del sistema di memoria venga monitorata continuamente per modifiche non autorizzate o corruzioni tramite checksum, registri di controllo e avvisi automatizzati quando il contenuto della memoria cambia fuori dalle operazioni normali.

────────────────────────────────────────

### Riferimenti

Vector database security: Pinecone – IronCore Labs
Securing the Backbone of AI: Safeguarding Vector Databases and Embeddings – Privacera
Enhancing Data Security with RBAC of Qdrant Vector Database – AI Advances
Mitigating Privacy Risks in LLM Embeddings from Embedding Inversion – arXiv
DPPN: Detecting and Perturbing Privacy-Sensitive Neurons – OpenReview
Art. 17 GDPR – Right to Erasure
Sensitive Data in Text Embeddings Is Recoverable – Tonic.ai
PII Identification and Removal – NVIDIA NeMo Docs
De-identifying Sensitive Data – Google Cloud DLP
Remove PII from Conversations Using Sensitive Information Filters – AWS Bedrock Guardrails
Think Your RAG Is Secure? Think Again – Medium
Design a Secure Multitenant RAG Inferencing Solution – Microsoft Learn
Best Practices for Multi-Tenancy RAG with Milvus – Milvus Blog

## 9 Orchestrazione Autonoma e Sicurezza dell'Azione Agente

### Obiettivo di Controllo

Garantire che i sistemi di intelligenza artificiale autonomi o multi-agente possano eseguire solo azioni che sono esplicitamente intenzionate, autenticate, verificabili e all’interno di limiti prestabiliti di costi e rischi. Questo protegge da minacce come il Compromesso del Sistema Autonomo, l’uso improprio degli Strumenti, il Rilevamento di Loop dell’Agente, il Dirottamento delle Comunicazioni, la Contraffazione dell’Identità, la Manipolazione dello Sciame e la Manipolazione delle Intenzioni.

────────────────────────────────────────

### 9.1 Pianificazione dei compiti dell'agente e budget di ricorsione

Limitare i piani ricorsivi e imporre checkpoint umani per azioni privilegiate.

 #9.1.1    Livello: 1    Ruolo: D/V
 Verificare che la profondità massima della ricorsione, la larghezza, il tempo di clock effettivo, i token e il costo monetario per esecuzione agente siano configurati centralmente e controllati tramite versionamento.
 #9.1.2    Livello: 1    Ruolo: D/V
 Verificare che le azioni privilegiate o irreversibili (ad esempio, commit di codice, trasferimenti finanziari) richiedano un'approvazione umana esplicita tramite un canale verificabile prima dell'esecuzione.
 #9.1.3    Livello: 2    Ruolo: D
 Verificare che i monitor delle risorse in tempo reale attivino l'interruzione del circuito di sicurezza quando viene superata qualsiasi soglia del budget, interrompendo l'espansione ulteriore delle attività.
 #9.1.4    Livello: 2    Ruolo: D/V
 Verificare che gli eventi del circuito di interruzione siano registrati con l'ID dell'agente, la condizione di attivazione e lo stato del piano acquisito per la revisione forense.
 #9.1.5    Livello: 3    Ruolo: V
 Verificare che i test di sicurezza coprano gli scenari di esaurimento del budget e di esecuzione incontrollata del piano, confermando l'arresto sicuro senza perdita di dati.
 #9.1.6    Livello: 3    Ruolo: D
 Verificare che le politiche di budget siano espresse come policy-as-code e applicate nel CI/CD per bloccare la deriva della configurazione.

────────────────────────────────────────

### 9.2 Sandbox dei Plugin degli Strumenti

Isolare le interazioni con gli strumenti per prevenire l'accesso non autorizzato al sistema o l'esecuzione di codice.

 #9.2.1    Livello: 1    Ruolo: D/V
 Verifica che ogni tool/plugin venga eseguito all'interno di un sistema operativo, container o sandbox a livello WASM con politiche di minimo privilegio per file system, rete e chiamate di sistema.
 #9.2.2    Livello: 1    Ruolo: D/V
 Verificare che le quote delle risorse della sandbox (CPU, memoria, disco, uscita rete) e i timeout di esecuzione siano applicati e registrati.
 #9.2.3    Livello: 2    Ruolo: D/V
 Verificare che i file binari o i descrittori degli strumenti siano firmati digitalmente; le firme devono essere convalidate prima del caricamento.
 #9.2.4    Livello: 2    Ruolo: V
 Verificare che la telemetria della sandbox venga trasmessa a un SIEM; le anomalie (ad esempio, tentativi di connessioni in uscita) generano allarmi.
 #9.2.5    Livello: 3    Ruolo: V
 Verificare che i plugin ad alto rischio vengano sottoposti a revisione della sicurezza e test di penetrazione prima della distribuzione in produzione.
 #9.2.6    Livello: 3    Ruolo: D/V
 Verificare che i tentativi di fuga dalla sandbox siano bloccati automaticamente e che il plugin offensivo venga messo in quarantena in attesa di indagine.

────────────────────────────────────────

### 9.3 Ciclo Autonomo e Limite dei Costi

Rilevare e fermare la ricorsione incontrollata tra agenti e le esplosioni di costi.

 #9.3.1    Livello: 1    Ruolo: D/V
 Verificare che le chiamate tra agenti includano un limite di salto o TTL che il runtime decrementa e applica.
 #9.3.2    Livello: 2    Ruolo: D
 Verificare che gli agenti mantengano un ID unico per il grafo di invocazione per individuare auto-invocazioni o schemi ciclici.
 #9.3.3    Livello: 2    Ruolo: D/V
 Verificare che i contatori cumulativi di unità di calcolo e spesa siano tracciati per catena di richiesta; il superamento del limite provoca l'interruzione della catena.
 #9.3.4    Livello: 3    Ruolo: V
 Verificare che l'analisi formale o il model checking dimostrino l'assenza di ricorsione non limitata nei protocolli degli agenti.
 #9.3.5    Livello: 3    Ruolo: D
 Verificare che gli eventi di interruzione del ciclo generino avvisi e alimentino le metriche di miglioramento continuo.

────────────────────────────────────────

### 9.4 Protezione contro l'uso improprio a livello di protocollo

Canali di comunicazione sicuri tra agenti e sistemi esterni per prevenire dirottamenti o manipolazioni.

 #9.4.1    Livello: 1    Ruolo: D/V
 Verificare che tutti i messaggi da agente a strumento e da agente a agente siano autenticati (ad esempio, mutual TLS o JWT) e criptati end-to-end.
 #9.4.2    Livello: 1    Ruolo: D
 Verificare che gli schemi siano strettamente validati; i campi sconosciuti o i messaggi malformati devono essere respinti.
 #9.4.3    Livello: 2    Ruolo: D/V
 Verificare che i controlli di integrità (MAC o firme digitali) coprano l'intero payload del messaggio, inclusi i parametri degli strumenti.
 #9.4.4    Livello: 2    Ruolo: D
 Verificare che la protezione contro la ripetizione (nonce o finestre temporali) sia applicata a livello di protocollo.
 #9.4.5    Livello: 3    Ruolo: V
 Verificare che le implementazioni del protocollo vengano sottoposte a fuzzing e analisi statica per individuare vulnerabilità di injection o deserializzazione.

────────────────────────────────────────

### 9.5 Identità dell'Agente e Prova di Manomissione

Garantire che le azioni siano attribuibili e le modifiche rilevabili.

 #9.5.1    Livello: 1    Ruolo: D/V
 Verificare che ogni istanza di agente possieda un’identità crittografica unica (coppia di chiavi o credenziale radicata in hardware).
 #9.5.2    Livello: 2    Ruolo: D/V
 Verificare che tutte le azioni degli agenti siano firmate e datate; i registri includono la firma per la non ripudiabilità.
 #9.5.3    Livello: 2    Ruolo: V
 Verificare che i log a prova di manomissione siano archiviati in un supporto solo per aggiunte o scrittura unica.
 #9.5.4    Livello: 3    Ruolo: D
 Verificare che le chiavi di identità ruotino secondo un programma definito e in presenza di indicatori di compromissione.
 #9.5.5    Livello: 3    Ruolo: D/V
 Verificare che i tentativi di spoofing o conflitto di chiavi attivino immediatamente la quarantena dell'agente interessato.

────────────────────────────────────────

### 9.6 Riduzione del rischio con sciame multi-agente

Mitigare i rischi legati al comportamento collettivo attraverso l'isolamento e la modellazione formale della sicurezza.

 #9.6.1    Livello: 1    Ruolo: D/V
 Verificare che gli agenti operanti in differenti domini di sicurezza vengano eseguiti in sandbox di runtime isolati o in segmenti di rete separati.
 #9.6.2    Livello: 3    Ruolo: V
 Verificare che i comportamenti dello sciame siano modellati e formalmente verificati per la vivacità e la sicurezza prima del dispiegamento.
 #9.6.3    Livello: 3    Ruolo: D
 Verificare che i monitor di runtime rilevino schemi di pericolo emergenti (ad esempio, oscillazioni, deadlock) e avviino azioni correttive.

────────────────────────────────────────

### 9.7 Autenticazione / Autorizzazione Utente e Strumento

Implementare controlli di accesso robusti per ogni azione attivata dall'agente.

 #9.7.1    Livello: 1    Ruolo: D/V
 Verificare che gli agenti si autentichino come principali di prima classe ai sistemi downstream, senza mai riutilizzare le credenziali dell'utente finale.
 #9.7.2    Livello: 2    Ruolo: D
 Verificare che le politiche di autorizzazione a grana fine limitino quali strumenti un agente può invocare e quali parametri può fornire.
 #9.7.3    Livello: 2    Ruolo: V
 Verificare che i controlli di privilegio vengano rivalutati ad ogni chiamata (autorizzazione continua), non solo all'inizio della sessione.
 #9.7.4    Livello: 3    Ruolo: D
 Verificare che i privilegi delegati scadano automaticamente e richiedano un nuovo consenso dopo il timeout o la modifica dell'ambito.

────────────────────────────────────────

### 9.8 Sicurezza della comunicazione agent-to-agent

Criptare e proteggere l'integrità di tutti i messaggi inter-agente per impedire intercettazioni e manomissioni.

 #9.8.1    Livello: 1    Ruolo: D/V
 Verificare che l'autenticazione mutua e la crittografia a segreto perfetto in avanti (ad esempio TLS 1.3) siano obbligatorie per i canali agent.
 #9.8.2    Livello: 1    Ruolo: D
 Verificare che l'integrità e l'origine del messaggio siano convalidate prima dell'elaborazione; i fallimenti generano avvisi e scartano il messaggio.
 #9.8.3    Livello: 2    Ruolo: D/V
 Verificare che i metadati della comunicazione (timestamp, numeri di sequenza) siano registrati per supportare la ricostruzione forense.
 #9.8.4    Livello: 3    Ruolo: V
 Verificare che la verifica formale o il model checking confermino che le macchine a stati del protocollo non possano essere portate in stati non sicuri.

────────────────────────────────────────

### 9.9 Verifica dell'Intento e Applicazione dei Vincoli

Verifica che le azioni dell'agente siano in linea con l'intento dichiarato dall'utente e con i vincoli del sistema.

 #9.9.1    Livello: 1    Ruolo: D
 Verificare che i solver di vincoli pre-esecuzione controllino le azioni proposte rispetto alle regole di sicurezza e di policy codificate rigidamente.
 #9.9.2    Livello: 2    Ruolo: D/V
 Verificare che le azioni ad alto impatto (finanziarie, distruttive, sensibili alla privacy) richiedano una conferma esplicita dell'intento da parte dell'utente che le avvia.
 #9.9.3    Livello: 2    Ruolo: V
 Verificare che i controlli delle post-condizioni confermino che le azioni completate abbiano raggiunto gli effetti previsti senza effetti collaterali; eventuali discrepanze attivano il rollback.
 #9.9.4    Livello: 3    Ruolo: V
 Verificare che i metodi formali (ad esempio, model checking, dimostrazione di teoremi) o i test basati su proprietà dimostrino che i piani degli agenti soddisfano tutti i vincoli dichiarati.
 #9.9.5    Livello: 3    Ruolo: D
 Verificare che gli incidenti di disallineamento dell’intento o di violazione dei vincoli alimentino cicli di miglioramento continuo e condivisione delle informazioni sulle minacce.

────────────────────────────────────────

### 9.10 Sicurezza della Strategia di Ragionamento dell'Agente

Selezione ed esecuzione sicura di diverse strategie di ragionamento, inclusi gli approcci ReAct, Chain-of-Thought e Tree-of-Thoughts.

 #9.10.1    Livello: 1    Ruolo: D/V
 Verificare che la selezione della strategia di ragionamento utilizzi criteri deterministici (complessità dell’input, tipo di compito, contesto di sicurezza) e che input identici producano selezioni di strategia identiche all’interno dello stesso contesto di sicurezza.
 #9.10.2    Livello: 1    Ruolo: D/V
 Verifica che ogni strategia di ragionamento (ReAct, Chain-of-Thought, Tree-of-Thoughts) disponga di una validazione degli input dedicata, una sanificazione degli output e limiti di tempo di esecuzione specifici per il rispettivo approccio cognitivo.
 #9.10.3    Livello: 2    Ruolo: D/V
 Verificare che le transizioni della strategia di ragionamento siano registrate con contesto completo, inclusi le caratteristiche dell'input, i valori dei criteri di selezione e i metadati di esecuzione, per la ricostruzione della traccia di controllo.
 #9.10.4    Livello: 2    Ruolo: D/V
 Verificare che il ragionamento Tree-of-Thoughts includa meccanismi di potatura dei rami che interrompono l’esplorazione quando vengono rilevate violazioni di policy, limiti di risorse o confini di sicurezza.
 #9.10.5    Livello: 2    Ruolo: D/V
 Verificare che i cicli ReAct (Reason-Act-Observe) includano punti di controllo di convalida in ogni fase: verifica del passaggio di ragionamento, autorizzazione dell’azione e sanificazione dell’osservazione prima di procedere.
 #9.10.6    Livello: 3    Ruolo: D/V
 Verificare che le metriche di prestazione della strategia di ragionamento (tempo di esecuzione, utilizzo delle risorse, qualità dell'output) siano monitorate con avvisi automatici quando le metriche si discostano oltre le soglie configurate.
 #9.10.7    Livello: 3    Ruolo: D/V
 Verificare che gli approcci di ragionamento ibrido che combinano più strategie mantengano la validazione dell'input e i vincoli di output di tutte le strategie costituenti senza bypassare alcun controllo di sicurezza.
 #9.10.8    Livello: 3    Ruolo: D/V
 Verificare che il testing di sicurezza della strategia di ragionamento includa il fuzzing con input malformati, prompt avversari progettati per forzare il cambio di strategia e il testing delle condizioni limite per ogni approccio cognitivo.

────────────────────────────────────────

### 9.11 Gestione dello Stato del Ciclo di Vita dell'Agente e Sicurezza

Inizializzazione sicura dell'agente, transizioni di stato e terminazione con tracciature di audit crittografiche e procedure di recupero definite.

 #9.11.1    Livello: 1    Ruolo: D/V
 Verificare che l'inizializzazione dell'agente includa l'istituzione dell'identità crittografica con credenziali supportate da hardware e registri di audit di avvio immutabili contenenti ID agente, timestamp, hash di configurazione e parametri di inizializzazione.
 #9.11.2    Livello: 2    Ruolo: D/V
 Verificare che le transizioni di stato dell’agente siano firmate crittograficamente, con marcatura temporale e registrate con contesto completo, inclusi gli eventi scatenanti, l’hash dello stato precedente, l’hash del nuovo stato e le convalide di sicurezza eseguite.
 #9.11.3    Livello: 2    Ruolo: D/V
 Verificare che le procedure di arresto dell'agente includano la cancellazione sicura della memoria mediante cancellazione crittografica o sovrascrittura a più passaggi, la revoca delle credenziali con notifica all'autorità di certificazione e la generazione di certificati di terminazione a prova di manomissione.
 #9.11.4    Livello: 3    Ruolo: D/V
 Verificare che i meccanismi di recupero dell'agente convalidino l'integrità dello stato utilizzando checksum crittografici (minimo SHA-256) e ripristinino stati noti come corretti quando viene rilevata una corruzione, con avvisi automatizzati e requisiti di approvazione manuale.
 #9.11.5    Livello: 3    Ruolo: D/V
 Verificare che i meccanismi di persistenza dell'agente cifrino i dati di stato sensibili con chiavi AES-256 per singolo agente e implementino una rotazione sicura delle chiavi secondo programmi configurabili (massimo 90 giorni) con distribuzione a zero tempi di inattività.

────────────────────────────────────────

### 9.12 Framework di Sicurezza per l'Integrazione degli Strumenti

Controlli di sicurezza per il caricamento dinamico degli strumenti, l'esecuzione e la convalida dei risultati con processi definiti di valutazione del rischio e approvazione.

 #9.12.1    Livello: 1    Ruolo: D/V
 Verificare che i descrittori degli strumenti includano metadati di sicurezza specificando i privilegi richiesti (lettura/scrittura/esecuzione), i livelli di rischio (basso/medio/alto), i limiti delle risorse (CPU, memoria, rete) e i requisiti di convalida documentati nei manifest degli strumenti.
 #9.12.2    Livello: 1    Ruolo: D/V
 Verificare che i risultati dell'esecuzione degli strumenti siano convalidati rispetto agli schemi previsti (JSON Schema, XML Schema) e alle politiche di sicurezza (sanificazione dell'output, classificazione dei dati) prima dell'integrazione, con limiti di timeout e procedure di gestione degli errori.
 #9.12.3    Livello: 2    Ruolo: D/V
 Verificare che i log delle interazioni degli strumenti includano un contesto di sicurezza dettagliato, compreso l'uso dei privilegi, i modelli di accesso ai dati, i tempi di esecuzione, il consumo delle risorse e i codici di ritorno, con una registrazione strutturata per l'integrazione con SIEM.
 #9.12.4    Livello: 2    Ruolo: D/V
 Verificare che i meccanismi di caricamento dinamico degli strumenti convalidino le firme digitali utilizzando l'infrastruttura PKI e implementino protocolli di caricamento sicuri con isolamento in sandbox e verifica delle autorizzazioni prima dell'esecuzione.
 #9.12.5    Livello: 3    Ruolo: D/V
 Verificare che le valutazioni di sicurezza degli strumenti vengano attivate automaticamente per le nuove versioni con passaggi di approvazione obbligatori che includano analisi statica, test dinamici e revisione del team di sicurezza con criteri di approvazione documentati e requisiti di SLA.

────────────────────────────────────────

#### Riferimenti

MITRE ATLAS tactics ML09
Circuit-breaker research for AI agents — Zou et al., 2024
Trend Micro analysis of sandbox escapes in AI agents — Park, 2025
Auth0 guidance on human-in-the-loop authorization for agents — Martinez, 2025
Medium deep-dive on MCP & A2A protocol hijacking — ForAISec, 2025
Rapid7 fundamentals on spoofing attack prevention — 2024
Imperial College verification of swarm systems — Lomuscio et al.
NIST AI Risk Management Framework 1.0, 2023
WIRED security briefing on encryption best practices, 2024
OWASP Top 10 for LLM Applications, 2025
Comprehensive Vulnerability Analysis is Necessary for Trustworthy LLM-MAS
[How Is LLM Reasoning Distracted by Irrelevant Context?
An Analysis Using a Controlled Benchmark](https://www.arxiv.org/pdf/2505.18761)
Large Language Model Sentinel: LLM Agent for Adversarial Purification
Securing Agentic AI: A Comprehensive Threat Model and Mitigation Framework for Generative AI Agents

## 10 Robustezza Avversaria e Difesa della Privacy

### Obiettivo di Controllo

Garantire che i modelli di AI rimangano affidabili, rispettosi della privacy e resistenti agli abusi quando affrontano attacchi di evasione, inferenza, estrazione o avvelenamento.

────────────────────────────────────────

### 10.1 Allineamento e Sicurezza del Modello

Proteggere contro output dannosi o che violano le politiche.

 #10.1.1    Livello: 1    Ruolo: D/V
 Verificare che un test-suite di allineamento (prompt red-team, sonde per jailbreak, contenuti non consentiti) sia gestito con controllo di versione e venga eseguito ad ogni rilascio del modello.
 #10.1.2    Livello: 1    Ruolo: D
 Verificare che siano applicate le barriere di sicurezza per il rifiuto e il completamento sicuro.
 #10.1.3    Livello: 2    Ruolo: D/V
 Verificare che un valutatore automatico misuri il tasso di contenuti dannosi e segnali le regressioni oltre una soglia prestabilita.
 #10.1.4    Livello: 2    Ruolo: D
 Verificare che l’addestramento contro il jailbreak sia documentato e riproducibile.
 #10.1.5    Livello: 3    Ruolo: V
 Verificare che le prove formali di conformità alle politiche o il monitoraggio certificato coprano i domini critici.

────────────────────────────────────────

### 10.2 Indurimento contro esempi avversari

Aumentare la resilienza agli input manipolati. L'addestramento avversariale robusto e la valutazione tramite benchmark sono le migliori pratiche attuali.

 #10.2.1    Livello: 1    Ruolo: D
 Verificare che i repository del progetto includano configurazioni di addestramento adversariale con semi riproducibili.
 #10.2.2    Livello: 2    Ruolo: D/V
 Verificare che il rilevamento degli esempi avversari generi avvisi di blocco nelle pipeline di produzione.
 #10.2.4    Livello: 3    Ruolo: V
 Verificare che le prove di robustezza certificata o i certificati a intervallo coprano almeno le principali classi critiche.
 #10.2.5    Livello: 3    Ruolo: V
 Verificare che i test di regressione utilizzino attacchi adattativi per confermare l'assenza di perdita misurabile di robustezza.

────────────────────────────────────────

### 10.3 Mitigazione delle inferenze sulla appartenenza

Limitare la capacità di decidere se un record faceva parte dei dati di addestramento. La privacy differenziale e la mascheratura del punteggio di confidenza rimangono le difese note più efficaci.

 #10.3.1    Livello: 1    Ruolo: D
 Verifica che la regolarizzazione dell'entropia per query o la scalatura della temperatura riducono le predizioni troppo sicure.
 #10.3.2    Livello: 2    Ruolo: D
 Verificare che l'addestramento utilizzi un’ottimizzazione a privacy differenziale vincolata da ε per dataset sensibili.
 #10.3.3    Livello: 2    Ruolo: V
 Verificare che le simulazioni di attacco (modello-ombra o black-box) mostrino un AUC dell'attacco ≤ 0,60 sui dati di test.

────────────────────────────────────────

### 10.4 Resistenza all'inversione del modello

Impedire la ricostruzione degli attributi privati. Recenti indagini sottolineano la troncatura dell'output e le garanzie DP come difese pratiche.

 #10.4.1    Livello: 1    Ruolo: D
 Verificare che gli attributi sensibili non vengano mai riportati direttamente; dove necessario, utilizzare bucket o trasformazioni unidirezionali.
 #10.4.2    Livello: 1    Ruolo: D/V
 Verificare che i limiti di frequenza delle query limitino le query adattive ripetute dallo stesso principale.
 #10.4.3    Livello: 2    Ruolo: D
 Verificare che il modello sia addestrato con rumore a tutela della privacy.

────────────────────────────────────────

### 10.5 Difesa contro l'Estrazione del Modello

Rilevare e dissuadere la clonazione non autorizzata. Si raccomandano la marcatura digitale (watermarking) e l'analisi dei modelli di query.

 #10.5.1    Livello: 1    Ruolo: D
 Verificare che i gateway di inferenza applichino limiti di frequenza globali e per chiave API regolati in base alla soglia di memorizzazione del modello.
 #10.5.2    Livello: 2    Ruolo: D/V
 Verificare che le statistiche di query-entropy e input-plurality alimentino un rilevatore di estrazione automatica.
 #10.5.3    Livello: 2    Ruolo: V
 Verificare che i watermark fragili o probabilistici possano essere dimostrati con p < 0,01 in ≤ 1 000 query contro un clone sospetto.
 #10.5.4    Livello: 3    Ruolo: D
 Verificare che le chiavi di watermark e i set di trigger siano memorizzati in un modulo di sicurezza hardware e ruotati annualmente.
 #10.5.5    Livello: 3    Ruolo: V
 Verificare che gli eventi di extraction-alert includano le query responsabili e siano integrati con i playbook di risposta agli incidenti.

────────────────────────────────────────

### 10.6 Rilevamento di Dati Avvelenati in Fase di Inferenza

Identificare e neutralizzare input con backdoor o avvelenati.

 #10.6.1    Livello: 1    Ruolo: D
 Verificare che gli input passino attraverso un rilevatore di anomalie (ad esempio, STRIP, scoring di coerenza) prima dell'inferenza del modello.
 #10.6.2    Livello: 1    Ruolo: V
 Verificare che le soglie del rilevatore siano regolate su set di validazione puliti/avvelenati per ottenere meno del 5% di falsi positivi.
 #10.6.3    Livello: 2    Ruolo: D
 Verificare che gli input identificati come contaminati attivino il soft-blocking e i flussi di lavoro per la revisione umana.
 #10.6.4    Livello: 2    Ruolo: V
 Verificare che i rilevatori siano sottoposti a stress test con attacchi backdoor adattivi e senza trigger.
 #10.6.5    Livello: 3    Ruolo: D
 Verificare che le metriche di efficacia del rilevamento siano registrate e riesaminate periodicamente con nuove informazioni sulle minacce.

────────────────────────────────────────

### 10.7 Adattamento dinamico della politica di sicurezza

Aggiornamenti in tempo reale delle politiche di sicurezza basati sull'intelligence delle minacce e sull'analisi comportamentale.

 #10.7.1    Livello: 1    Ruolo: D/V
 Verificare che le politiche di sicurezza possano essere aggiornate dinamicamente senza riavviare l’agente mantenendo l’integrità della versione della politica.
 #10.7.2    Livello: 2    Ruolo: D/V
 Verificare che gli aggiornamenti delle policy siano firmati crittograficamente dal personale di sicurezza autorizzato e convalidati prima dell'applicazione.
 #10.7.3    Livello: 2    Ruolo: D/V
 Verificare che le modifiche dinamiche alle policy siano registrate con tracce di audit complete, includendo giustificazioni, catene di approvazione e procedure di rollback.
 #10.7.4    Livello: 3    Ruolo: D/V
 Verificare che i meccanismi di sicurezza adattivi regolino la sensibilità del rilevamento delle minacce in base al contesto di rischio e ai modelli comportamentali.
 #10.7.5    Livello: 3    Ruolo: D/V
 Verificare che le decisioni di adattamento della policy siano spiegabili e includano tracce di evidenza per la revisione del team di sicurezza.

────────────────────────────────────────

### 10.8 Analisi della Sicurezza Basata sulla Riflessività

Validazione della sicurezza attraverso l'auto-riflessione dell'agente e l'analisi meta-cognitiva.

 #10.8.1    Livello: 1    Ruolo: D/V
 Verificare che i meccanismi di riflessione dell'agente includano un'autovalutazione delle decisioni e delle azioni focalizzata sulla sicurezza.
 #10.8.2    Livello: 2    Ruolo: D/V
 Verificare che i risultati della riflessione siano convalidati per prevenire la manipolazione dei meccanismi di autovalutazione da parte di input avversari.
 #10.8.3    Livello: 2    Ruolo: D/V
 Verificare che l'analisi di sicurezza meta-cognitiva identifichi potenziali bias, manipolazioni o compromissioni nei processi di ragionamento degli agenti.
 #10.8.4    Livello: 3    Ruolo: D/V
 Verificare che gli avvisi di sicurezza basati sulla riflessione attivino il monitoraggio avanzato e i potenziali flussi di lavoro di intervento umano.
 #10.8.5    Livello: 3    Ruolo: D/V
 Verificare che l'apprendimento continuo dalle riflessioni sulla sicurezza migliori il rilevamento delle minacce senza compromettere la funzionalità legittima.

────────────────────────────────────────

### 10.9 Sicurezza per l'Evoluzione e l'Auto-Miglioramento

Controlli di sicurezza per sistemi agenti capaci di auto-modificazione ed evoluzione.

 #10.9.1    Livello: 1    Ruolo: D/V
 Verificare che le capacità di auto-modifica siano limitate ad aree designate sicure con confini di verifica formale.
 #10.9.2    Livello: 2    Ruolo: D/V
 Verificare che le proposte di evoluzione vengano sottoposte a una valutazione dell'impatto sulla sicurezza prima dell'implementazione.
 #10.9.3    Livello: 2    Ruolo: D/V
 Verificare che i meccanismi di auto-miglioramento includano capacità di rollback con verifica dell'integrità.
 #10.9.4    Livello: 3    Ruolo: D/V
 Verificare che la sicurezza del meta-learning impedisca la manipolazione avversaria degli algoritmi di miglioramento.
 #10.9.5    Livello: 3    Ruolo: D/V
 Verificare che il miglioramento ricorsivo di sé stesso sia limitato da vincoli formali di sicurezza con dimostrazioni matematiche di convergenza.

────────────────────────────────────────

#### Riferimenti

MITRE ATLAS adversary tactics for ML
NIST AI Risk Management Framework 1.0, 2023
OWASP Top 10 for LLM Applications, 2025
Adversarial Training: A Survey — Zhao et al., 2024
RobustBench adversarial-robustness benchmark
Membership-Inference & Model-Inversion Risk Survey, 2025
PURIFIER: Confidence-Score Defense against MI Attacks — AAAI 2023
Model-Inversion Attacks & Defenses Survey — AI Review, 2025
Comprehensive Defense Framework Against Model Extraction — IEEE TDSC 2024
Fragile Model Watermarking Survey — 2025
Data Poisoning in Deep Learning: A Survey — Zhao et al., 2025
BDetCLIP: Multimodal Prompting Backdoor Detection — Niu et al., 2024

## 11 Protezione della privacy e gestione dei dati personali

### Obiettivo di Controllo

Mantenere rigorose garanzie di privacy lungo l'intero ciclo di vita dell'IA—raccolta, addestramento, inferenza e risposta agli incidenti—affinché i dati personali siano processati solo con consenso esplicito, ambito minimo necessario, cancellazione dimostrabile e garanzie formali di privacy.

────────────────────────────────────────

### 11.1 Anonimizzazione e Minimizzazione dei Dati

 #11.1.1    Livello: 1    Ruolo: D/V
 Verificare che gli identificatori diretti e quasi-identificatori siano rimossi o sottoposti a hashing.
 #11.1.2    Livello: 2    Ruolo: D/V
 Verificare che le verifiche automatizzate misurino k-anonimato/l-diversità e segnalino quando le soglie scendono al di sotto della politica.
 #11.1.3    Livello: 2    Ruolo: V
 Verificare che i rapporti di importanza delle caratteristiche del modello dimostrino nessuna fuga di identificatori oltre ε = 0,01 di informazione mutua.
 #11.1.4    Livello: 3    Ruolo: V
 Verificare che le dimostrazioni formali o la certificazione con dati sintetici mostrino un rischio di re-identificazione ≤ 0,05 anche in caso di attacchi di linkage.

────────────────────────────────────────

### 11.2 Diritto all'Oblio e Applicazione della Cancellazione

 #11.2.1    Livello: 1    Ruolo: D/V
 Verificare che le richieste di cancellazione dei dati del soggetto si propaghino ai set di dati grezzi, ai checkpoint, agli embeddings, ai registri e ai backup entro accordi sul livello di servizio inferiori a 30 giorni.
 #11.2.2    Livello: 2    Ruolo: D
 Verificare che le routine di "machine-unlearning" ri-addestrino fisicamente o approssimino la rimozione utilizzando algoritmi di unlearning certificati.
 #11.2.3    Livello: 2    Ruolo: V
 Verificare che la valutazione del modello ombra dimostri che i record dimenticati influenzano meno dell'1% dei risultati dopo il processo di unlearning.
 #11.2.4    Livello: 3    Ruolo: V
 Verificare che gli eventi di cancellazione siano registrati in modo immutabile e siano verificabili per i regolatori.

────────────────────────────────────────

### 11.3 Misure di protezione basate sulla privacy differenziale

 #11.3.1    Livello: 2    Ruolo: D/V
 Verificare che i cruscotti di contabilizzazione della perdita della privacy segnalino quando ε cumulativo supera le soglie delle politiche.
 #11.3.2    Livello: 2    Ruolo: V
 Verificare che le verifiche di privacy black-box stimino ε̂ entro il 10% del valore dichiarato.
 #11.3.3    Livello: 3    Ruolo: V
 Verificare che le dimostrazioni formali coprano tutte le rifiniture post-addestramento e gli embeddings.

────────────────────────────────────────

### 11.4 Limitazione dello scopo e protezione contro l'espansione incontrollata del campo di applicazione

 #11.4.1    Livello: 1    Ruolo: D
 Verificare che ogni dataset e checkpoint del modello riporti un tag di scopo leggibile da macchina allineato al consenso originale.
 #11.4.2    Livello: 1    Ruolo: D/V
 Verificare che i monitor di runtime rilevino query incoerenti con lo scopo dichiarato e attivino un rifiuto soft.
 #11.4.3    Livello: 3    Ruolo: D
 Verificare che i gate di policy-as-code blocchino la ridistribuzione dei modelli su nuovi domini senza la revisione DPIA.
 #11.4.4    Livello: 3    Ruolo: V
 Verificare che le prove formali di tracciabilità dimostrino che ogni ciclo di vita dei dati personali rimanga all'interno dell'ambito consentito.

────────────────────────────────────────

### 11.5 Gestione del Consenso e Tracciamento della Base Legale

 #11.5.1    Livello: 1    Ruolo: D/V
 Verificare che una Piattaforma di Gestione del Consenso (CMP) registri lo stato di opt-in, lo scopo e il periodo di conservazione per ciascun soggetto dei dati.
 #11.5.2    Livello: 2    Ruolo: D
 Verificare che le API espongano i token di consenso; i modelli devono convalidare l'ambito del token prima dell'inferenza.
 #11.5.3    Livello: 2    Ruolo: D/V
 Verificare che il consenso negato o ritirato interrompa le pipeline di elaborazione entro 24 ore.

────────────────────────────────────────

### 11.6 Apprendimento Federato con Controlli sulla Privacy

 #11.6.1    Livello: 1    Ruolo: D
 Verificare che gli aggiornamenti del client impieghino l’aggiunta di rumore tramite privacy differenziale locale prima dell’aggregazione.
 #11.6.2    Livello: 2    Ruolo: D/V
 Verificare che le metriche di addestramento siano differenzialmente private e non rivelino mai la perdita di un singolo cliente.
 #11.6.3    Livello: 2    Ruolo: V
 Verificare che l'aggregazione resistente al poisoning (ad esempio, Krum/Trimmed-Mean) sia abilitata.
 #11.6.4    Livello: 3    Ruolo: V
 Verificare che le dimostrazioni formali dimostrino un budget complessivo di ε con una perdita di utilità inferiore a 5.

────────────────────────────────────────

#### Riferimenti

GDPR & AI Compliance Best Practices
EU Parliament Study on GDPR & AI, 2020
ISO 31700-1:2023 — Privacy by Design for Consumer Products
NIST Privacy Framework 1.1 (2025 Draft)
Machine Unlearning: Right-to-Be-Forgotten Techniques
A Survey of Machine Unlearning, 2024
Auditing DP-SGD — ArXiv 2024
DP-SGD Explained — PyTorch Blog
Purpose-Limitation for AI — IJLIT 2025
Data-Protection Considerations for AI — URM Consulting
Top Consent-Management Platforms, 2025
Secure Aggregation in DP Federated Learning — ArXiv 2024

## C12 Monitoraggio, Registrazione e Rilevamento delle Anomalie

### Obiettivo di Controllo

Questa sezione fornisce requisiti per offrire una visibilità in tempo reale e forense su ciò che il modello e altri componenti AI vedono, fanno e restituiscono, in modo che le minacce possano essere rilevate, gestite e analizzate per apprendimento.

### C12.1 Registrazione delle Richieste e delle Risposte

 #12.1.1    Livello: 1    Ruolo: D/V
 Verificare che tutti i prompt utente e le risposte del modello siano registrati con i metadati appropriati (ad esempio timestamp, ID utente, ID sessione, versione del modello).
 #12.1.2    Livello: 1    Ruolo: D/V
 Verificare che i log siano archiviati in repository sicuri, con accesso controllato, dotati di politiche di conservazione appropriate e procedure di backup.
 #12.1.3    Livello: 1    Ruolo: D/V
 Verificare che i sistemi di archiviazione dei log implementino la crittografia a riposo e in transito per proteggere le informazioni sensibili contenute nei log.
 #12.1.4    Livello: 1    Ruolo: D/V
 Verificare che i dati sensibili nei prompt e nei risultati siano automaticamente oscurati o mascherati prima della registrazione, con regole di oscuramento configurabili per informazioni personali identificabili (PII), credenziali e informazioni proprietarie.
 #12.1.5    Livello: 2    Ruolo: D/V
 Verificare che le decisioni politiche e le azioni di filtraggio di sicurezza siano registrate con dettagli sufficienti per consentire la revisione e il debug dei sistemi di moderazione dei contenuti.
 #12.1.6    Livello: 2    Ruolo: D/V
 Verificare che l'integrità dei log sia protetta tramite, ad esempio, firme crittografiche o archiviazione in sola scrittura.

────────────────────────────────────────

### C12.2 Rilevamento e Allerta degli Abusi

 #12.2.1    Livello: 1    Ruolo: D/V
 Verificare che il sistema rilevi e avvisi sulle pattern di jailbreak conosciuti, sui tentativi di iniezione di prompt e sugli input avversari utilizzando il rilevamento basato su firme.
 #12.2.2    Livello: 1    Ruolo: D/V
 Verificare che il sistema si integri con le piattaforme di Security Information and Event Management (SIEM) esistenti utilizzando formati di log e protocolli standard.
 #12.2.3    Livello: 2    Ruolo: D/V
 Verificare che gli eventi di sicurezza arricchiti includano il contesto specifico dell'IA come gli identificatori del modello, i punteggi di confidenza e le decisioni del filtro di sicurezza.
 #12.2.4    Livello: 2    Ruolo: D/V
 Verificare che il rilevamento delle anomalie comportamentali identifichi modelli di conversazione insoliti, tentativi di ripetizione eccessivi o comportamenti di sondaggio sistematici.
 #12.2.5    Livello: 2    Ruolo: D/V
 Verificare che i meccanismi di allerta in tempo reale notificano i team di sicurezza quando vengono rilevate potenziali violazioni delle policy o tentativi di attacco.
 #12.2.6    Livello: 2    Ruolo: D/V
 Verifica che siano incluse regole personalizzate per rilevare schemi di minacce specifici dell’IA, inclusi tentativi coordinati di jailbreak, campagne di iniezione di prompt e attacchi di estrazione del modello.
 #12.2.7    Livello: 3    Ruolo: D/V
 Verificare che i workflow automatizzati di risposta agli incidenti possano isolare i modelli compromessi, bloccare gli utenti malintenzionati e segnalare gli eventi di sicurezza critici.

────────────────────────────────────────

### C12.3 Rilevamento del Drift del Modello

 #12.3.1    Livello: 1    Ruolo: D/V
 Verificare che il sistema monitori metriche di prestazione di base come accuratezza, punteggi di confidenza, latenza e tassi di errore attraverso le versioni del modello e i periodi temporali.
 #12.3.2    Livello: 2    Ruolo: D/V
 Verificare che gli avvisi automatici vengano attivati quando i metriche di prestazione superano le soglie di degrado predefinite o si discostano significativamente dalle linee di base.
 #12.3.3    Livello: 2    Ruolo: D/V
 Verificare che i sistemi di rilevamento delle allucinazioni identifichino e segnalino i casi in cui le risposte del modello contengano informazioni fattualmente errate, incoerenti o inventate.

────────────────────────────────────────

### C12.4 Telemetria delle Prestazioni e del Comportamento

 #12.4.1    Livello: 1    Ruolo: D/V
 Verificare che le metriche operative, inclusi la latenza delle richieste, il consumo di token, l'uso della memoria e la produttività, siano continuamente raccolte e monitorate.
 #12.4.2    Livello: 1    Ruolo: D/V
 Verificare che i tassi di successo e di fallimento siano monitorati con la categorizzazione dei tipi di errore e delle loro cause principali.
 #12.4.3    Livello: 2    Ruolo: D/V
 Verificare che il monitoraggio dell'utilizzo delle risorse includa l'uso di GPU/CPU, il consumo di memoria e i requisiti di archiviazione, con allerta in caso di superamento delle soglie.

────────────────────────────────────────

### C12.5 Pianificazione ed Esecuzione della Risposta agli Incidenti di AI

 #12.5.1    Livello: 1    Ruolo: D/V
 Verificare che i piani di risposta agli incidenti affrontino specificamente gli eventi di sicurezza legati all'intelligenza artificiale, inclusi compromissioni del modello, avvelenamento dei dati e attacchi avversari.
 #12.5.2    Livello: 2    Ruolo: D/V
 Verificare che i team di risposta agli incidenti abbiano accesso a strumenti forensi specifici per l'IA e a competenze per investigare il comportamento dei modelli e i vettori di attacco.
 #12.5.3    Livello: 3    Ruolo: D/V
 Verificare che l'analisi post-incidente includa considerazioni sul retraining del modello, aggiornamenti dei filtri di sicurezza e l'integrazione delle lezioni apprese nei controlli di sicurezza.

────────────────────────────────────────

### C12.6 Rilevamento del Deterioramento delle Prestazioni dell'AI

Monitorare e rilevare il degrado delle prestazioni e della qualità del modello di IA nel tempo.

 #12.6.1    Livello: 1    Ruolo: D/V
 Verificare che accuratezza, precisione, richiamo e punteggi F1 del modello siano monitorati continuamente e confrontati con le soglie di base.
 #12.6.2    Livello: 1    Ruolo: D/V
 Verificare che il rilevamento del drift dei dati monitori le variazioni nella distribuzione degli input che potrebbero influire sulle prestazioni del modello.
 #12.6.3    Livello: 2    Ruolo: D/V
 Verificare che il rilevamento del concept drift individui cambiamenti nella relazione tra input e output attesi.
 #12.6.4    Livello: 2    Ruolo: D/V
 Verificare che il degrado delle prestazioni attivi automaticamente gli avvisi e avvii i flussi di lavoro per il riaddestramento o la sostituzione del modello.
 #12.6.5    Livello: 3    Ruolo: V
 Verificare che l'analisi delle cause primarie del degrado correli i cali di prestazioni con modifiche dei dati, problemi infrastrutturali o fattori esterni.

────────────────────────────────────────

### C12.7 Visualizzazione DAG e Sicurezza del Flusso di Lavoro

Proteggere i sistemi di visualizzazione del flusso di lavoro da perdite di informazioni e attacchi di manipolazione.

 #12.7.1    Livello: 1    Ruolo: D/V
 Verificare che i dati di visualizzazione DAG siano puliti per rimuovere informazioni sensibili prima della memorizzazione o della trasmissione.
 #12.7.2    Livello: 1    Ruolo: D/V
 Verificare che i controlli di accesso alla visualizzazione del flusso di lavoro garantiscano che solo gli utenti autorizzati possano visualizzare i percorsi decisionali degli agenti e le tracce di ragionamento.
 #12.7.3    Livello: 2    Ruolo: D/V
 Verificare che l'integrità dei dati DAG sia protetta tramite firme crittografiche e meccanismi di archiviazione a prova di manomissione.
 #12.7.4    Livello: 2    Ruolo: D/V
 Verificare che i sistemi di visualizzazione del flusso di lavoro implementino la convalida degli input per prevenire attacchi di injection tramite dati manipolati di nodi o archi.
 #12.7.5    Livello: 3    Ruolo: D/V
 Verificare che gli aggiornamenti DAG in tempo reale siano limitati nella frequenza e convalidati per prevenire attacchi di negazione del servizio sui sistemi di visualizzazione.

────────────────────────────────────────

### C12.8 Monitoraggio Proattivo del Comportamento di Sicurezza

Rilevamento e prevenzione delle minacce alla sicurezza attraverso l'analisi proattiva del comportamento degli agenti.

 #12.8.1    Livello: 1    Ruolo: D/V
 Verificare che i comportamenti proattivi degli agenti siano convalidati in termini di sicurezza prima dell'esecuzione, integrando una valutazione del rischio.
 #12.8.2    Livello: 2    Ruolo: D/V
 Verificare che le iniziative autonome includano la valutazione del contesto di sicurezza e l’analisi del panorama delle minacce.
 #12.8.3    Livello: 2    Ruolo: D/V
 Verificare che i modelli di comportamento proattivo siano analizzati per potenziali implicazioni di sicurezza e conseguenze non intenzionali.
 #12.8.4    Livello: 3    Ruolo: D/V
 Verificare che le azioni proattive critiche per la sicurezza richiedano catene di approvazione esplicite con tracciamenti di audit.
 #12.8.5    Livello: 3    Ruolo: D/V
 Verificare che il rilevamento di anomalie comportamentali identifichi deviazioni nei modelli degli agenti proattivi che potrebbero indicare una compromissione.

────────────────────────────────────────

### Riferimenti

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6

## C13 Supervisione Umana, Responsabilità e Governance

### Obiettivo di Controllo

Questo capitolo fornisce requisiti per mantenere la supervisione umana e catene di responsabilità chiare nei sistemi di intelligenza artificiale, garantendo spiegabilità, trasparenza e gestione etica lungo tutto il ciclo di vita dell’IA.

────────────────────────────────────────

### C13.1 Meccanismi di Kill-Switch e Override

Fornire percorsi di spegnimento o rollback quando viene osservato un comportamento non sicuro del sistema di IA.

 #13.1.1    Livello: 1    Ruolo: D/V
 Verificare che esista un meccanismo manuale di interruzione per fermare immediatamente l'inferenza e gli output del modello AI.
 #13.1.2    Livello: 1    Ruolo: D
 Verificare che i controlli di override siano accessibili solo al personale autorizzato.
 #13.1.3    Livello: 3    Ruolo: D/V
 Verificare che le procedure di rollback possano riportare alle versioni precedenti del modello o alle operazioni in modalità sicura.
 #13.1.4    Livello: 3    Ruolo: V
 Verificare che i meccanismi di override siano testati regolarmente.

────────────────────────────────────────

### C13.2 Punti di Controllo delle Decisioni con Coinvolgimento Umano

Richiedere approvazioni umane quando le poste in gioco superano le soglie di rischio predefinite.

 #13.2.1    Livello: 1    Ruolo: D/V
 Verificare che le decisioni AI ad alto rischio richiedano un'esplicita approvazione umana prima dell'esecuzione.
 #13.2.2    Livello: 1    Ruolo: D
 Verificare che le soglie di rischio siano chiaramente definite e attivino automaticamente i flussi di lavoro di revisione umana.
 #13.2.3    Livello: 2    Ruolo: D
 Verificare che le decisioni sensibili al tempo dispongano di procedure di riserva nel caso in cui l'approvazione umana non possa essere ottenuta entro i tempi richiesti.
 #13.2.4    Livello: 3    Ruolo: D/V
 Verificare che le procedure di escalation definiscano livelli di autorità chiari per i diversi tipi di decisione o categorie di rischio, se applicabile.

────────────────────────────────────────

### C13.3 Catena di Responsabilità e Auditabilità

Registra le azioni dell'operatore e le decisioni del modello.

 #13.3.1    Livello: 1    Ruolo: D/V
 Verificare che tutte le decisioni del sistema AI e gli interventi umani siano registrati con marca temporale, identità utente e motivazione della decisione.
 #13.3.2    Livello: 2    Ruolo: D
 Verificare che i log di audit non possano essere manomessi e includano meccanismi di verifica dell'integrità.

────────────────────────────────────────

### C13.4 Tecniche di Explainable AI

Importanza delle caratteristiche superficiali, controfattuali e spiegazioni locali.

 #13.4.1    Livello: 1    Ruolo: D/V
 Verificare che i sistemi di intelligenza artificiale forniscano spiegazioni di base per le loro decisioni in un formato comprensibile all’essere umano.
 #13.4.2    Livello: 2    Ruolo: V
 Verificare che la qualità della spiegazione sia validata attraverso studi di valutazione umana e metriche.
 #13.4.3    Livello: 3    Ruolo: D/V
 Verificare che i punteggi di importanza delle caratteristiche o i metodi di attribuzione (SHAP, LIME, ecc.) siano disponibili per le decisioni critiche.
 #13.4.4    Livello: 3    Ruolo: V
 Verificare che le spiegazioni controfattuali mostrino come gli input potrebbero essere modificati per cambiare i risultati, se applicabile al caso d'uso e al dominio.

────────────────────────────────────────

### C13.5 Schede Modello e Dichiarazioni di Utilizzo

Mantenere schede modello per l'uso previsto, le metriche di prestazione e le considerazioni etiche.

 #13.5.1    Livello: 1    Ruolo: D
 Verificare che le schede del modello documentino i casi d'uso previsti, le limitazioni e i modi di guasto noti.
 #13.5.2    Livello: 1    Ruolo: D/V
 Verificare che le metriche di prestazione relative ai diversi casi d'uso applicabili siano comunicate.
 #13.5.3    Livello: 2    Ruolo: D
 Verificare che le considerazioni etiche, le valutazioni dei bias, le valutazioni dell'equità, le caratteristiche dei dati di addestramento e le limitazioni conosciute dei dati di addestramento siano documentate e aggiornate regolarmente.
 #13.5.4    Livello: 2    Ruolo: D/V
 Verificare che le schede del modello siano soggette a controllo delle versioni e mantenute durante l'intero ciclo di vita del modello con monitoraggio delle modifiche.

────────────────────────────────────────

### C13.6 Quantificazione dell’Incertezza

Propagare i punteggi di confidenza o le misure di entropia nelle risposte.

 #13.6.1    Livello: 1    Ruolo: D
 Verificare che i sistemi di AI forniscano punteggi di confidenza o misure di incertezza con i loro output.
 #13.6.2    Livello: 2    Ruolo: D/V
 Verificare che le soglie di incertezza attivino una revisione umana aggiuntiva o percorsi decisionali alternativi.
 #13.6.3    Livello: 2    Ruolo: V
 Verificare che i metodi di quantificazione dell'incertezza siano calibrati e validati rispetto ai dati di riferimento.
 #13.6.4    Livello: 3    Ruolo: D/V
 Verificare che la propagazione dell'incertezza sia mantenuta attraverso flussi di lavoro AI multi-fase.

────────────────────────────────────────

### C13.7 Rapporti di trasparenza rivolti agli utenti

Fornire divulgazioni periodiche sugli incidenti, le derive e l'uso dei dati.

 #13.7.1    Livello: 1    Ruolo: D/V
 Verificare che le politiche di utilizzo dei dati e le pratiche di gestione del consenso degli utenti siano chiaramente comunicate alle parti interessate.
 #13.7.2    Livello: 2    Ruolo: D/V
 Verificare che le valutazioni dell'impatto dell'IA siano condotte e che i risultati siano inclusi nei rapporti.
 #13.7.3    Livello: 2    Ruolo: D/V
 Verificare che i rapporti di trasparenza pubblicati regolarmente divulghino incidenti di AI e metriche operative con un livello di dettaglio ragionevole.

#### Riferimenti

EU Artificial Intelligence Act — Regulation (EU) 2024/1689 (Official Journal, 12 July 2024)
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
ISO/IEC 42001:2023 — AI Management Systems Requirements
NIST AI Risk Management Framework 1.0
NIST SP 800-53 Revision 5 — Security and Privacy Controls
A Unified Approach to Interpreting Model Predictions (SHAP, ICML 2017)
Model Cards for Model Reporting (Mitchell et al., 2018)
Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning (Gal & Ghahramani, 2016)
ISO/IEC 24029-2:2023 — Robustness of Neural Networks — Methodology for Formal Methods
IEEE 7001-2021 — Transparency of Autonomous Systems
Human Oversight under Article 14 of the EU AI Act (Fink, 2025)

## Appendice A: Glossario

Questo glossario completo fornisce definizioni dei termini chiave di AI, ML e sicurezza utilizzati in tutto l'AISVS per garantire chiarezza e comprensione comune.

Esempio avversario: un input deliberatamente creato per far commettere un errore a un modello di IA, spesso aggiungendo sottili perturbazioni impercettibili agli esseri umani.
​
Robustezza Avversaria – La robustezza avversaria nell'AI si riferisce alla capacità di un modello di mantenere le proprie prestazioni e resistere a essere ingannato o manipolato da input intenzionalmente creati e dannosi, progettati per causare errori.
​
Agente – Gli agenti AI sono sistemi software che utilizzano l'intelligenza artificiale per perseguire obiettivi e completare compiti per conto degli utenti. Mostrano capacità di ragionamento, pianificazione e memoria e possiedono un livello di autonomia per prendere decisioni, apprendere e adattarsi.
​
Agentic AI: Sistemi di intelligenza artificiale che possono operare con un certo grado di autonomia per raggiungere obiettivi, spesso prendendo decisioni e compiendo azioni senza intervento umano diretto.
​
Controllo di Accesso Basato su Attributi (ABAC): un paradigma di controllo degli accessi in cui le decisioni di autorizzazione si basano sugli attributi dell'utente, della risorsa, dell'azione e dell'ambiente, valutati al momento della richiesta.
​
Attacco Backdoor: Un tipo di attacco di avvelenamento dei dati in cui il modello viene addestrato a rispondere in un modo specifico a determinati trigger mentre si comporta normalmente altrimenti.
​
Bias: Errori sistematici nei risultati dei modelli di IA che possono portare a risultati ingiusti o discriminatori per determinati gruppi o in contesti specifici.
​
Sfruttamento dei Bias: Una tecnica di attacco che sfrutta i bias noti nei modelli di AI per manipolare risultati o esiti.
​
Cedar: il linguaggio e il motore di policy di Amazon per permessi dettagliati utilizzati nell'implementazione di ABAC per sistemi di intelligenza artificiale.
​
Catena di pensiero: una tecnica per migliorare il ragionamento nei modelli linguistici generando passaggi intermedi di ragionamento prima di produrre una risposta finale.
​
Interruttori automatici: Meccanismi che interrompono automaticamente le operazioni del sistema AI quando vengono superate specifiche soglie di rischio.
​
Servizio di Inferenza Confidenziale: un servizio di inferenza che esegue modelli di intelligenza artificiale all'interno di un ambiente di esecuzione attendibile (TEE) o di un meccanismo equivalente di calcolo confidenziale, garantendo che i pesi del modello e i dati di inferenza rimangano criptati, sigillati e protetti da accessi non autorizzati o manomissioni.
​
Carico di lavoro confidenziale: un carico di lavoro AI (ad esempio, training, inferenza, preprocessing) eseguito all'interno di un ambiente di esecuzione affidabile (TEE) con isolamento hardware, crittografia della memoria e attestazione remota per proteggere codice, dati e modelli dall'accesso da parte dell'host o di co-tenant.
​
Perdita di dati: esposizione involontaria di informazioni sensibili tramite output o comportamento del modello AI.
​
Avvelenamento dei dati: la corruzione deliberata dei dati di addestramento per compromettere l'integrità del modello, spesso per installare backdoor o degradare le prestazioni.
​
Privacy differenziale – La privacy differenziale è un quadro matematicamente rigoroso per la divulgazione di informazioni statistiche su insiemi di dati proteggendo al contempo la privacy dei singoli soggetti dei dati. Consente a chi detiene i dati di condividere modelli aggregati del gruppo limitando le informazioni che vengono rivelate su individui specifici.
​
Embedding: Rappresentazioni vettoriali dense di dati (testo, immagini, ecc.) che catturano il significato semantico in uno spazio ad alta dimensione.
​
Spiegabilità – La spiegabilità nell'IA è la capacità di un sistema di intelligenza artificiale di fornire motivazioni comprensibili all’essere umano per le proprie decisioni e previsioni, offrendo approfondimenti sul suo funzionamento interno.
​
Intelligenza Artificiale Spiegabile (XAI): sistemi di intelligenza artificiale progettati per fornire spiegazioni comprensibili agli esseri umani riguardo alle loro decisioni e comportamenti attraverso diverse tecniche e framework.
​
Apprendimento Federato: un approccio di machine learning in cui i modelli vengono addestrati su più dispositivi decentralizzati che possiedono campioni di dati locali, senza scambiare i dati stessi.
​
Formulazione: La ricetta o il metodo utilizzato per produrre un artefatto o un dataset, come gli iperparametri, la configurazione dell'addestramento, i passaggi di preprocessamento o gli script di compilazione.
​
Limitazioni: Vincoli implementati per prevenire che i sistemi di IA producano risultati dannosi, parziali o altrimenti indesiderati.
​
Allucinazione – Un'allucinazione dell'IA si riferisce a un fenomeno in cui un modello di IA genera informazioni errate o fuorvianti che non si basano sui suoi dati di addestramento o sulla realtà fattuale.
​
Human-in-the-Loop (HITL): Sistemi progettati per richiedere supervisione, verifica o intervento umano in punti decisionali cruciali.
​
Infrastructure as Code (IaC): Gestione e provisioning dell'infrastruttura tramite codice anziché processi manuali, consentendo la scansione della sicurezza e distribuzioni coerenti.
​
Jailbreak: Tecniche utilizzate per eludere i vincoli di sicurezza nei sistemi di intelligenza artificiale, in particolare nei grandi modelli linguistici, per produrre contenuti proibiti.
​
Minimo privilegio: Il principio di sicurezza che concede solo i diritti di accesso minimi necessari per utenti e processi.
​
LIME (Local Interpretable Model-agnostic Explanations): Una tecnica per spiegare le predizioni di qualsiasi classificatore di machine learning approssimandolo localmente con un modello interpretabile.
​
Attacco di Inferenza di Membri: Un attacco che mira a determinare se un dato specifico è stato utilizzato per addestrare un modello di machine learning.
​
MITRE ATLAS: Paesaggio delle minacce avversarie per i sistemi di intelligenza artificiale; una base di conoscenza delle tattiche e tecniche avversarie contro i sistemi di IA.
​
Scheda Modello – Una scheda modello è un documento che fornisce informazioni standardizzate sulle prestazioni di un modello di intelligenza artificiale, sui limiti, sugli utilizzi previsti e sulle considerazioni etiche per promuovere la trasparenza e lo sviluppo responsabile dell’intelligenza artificiale.
​
Estrazione del modello: Un attacco in cui un avversario interroga ripetutamente un modello di destinazione per creare una copia funzionalmente simile senza autorizzazione.
​
Inversione del modello: un attacco che tenta di ricostruire i dati di addestramento analizzando gli output del modello.
​
Gestione del Ciclo di Vita del Modello – La gestione del ciclo di vita del modello AI è il processo di supervisione di tutte le fasi dell'esistenza di un modello AI, inclusi progettazione, sviluppo, distribuzione, monitoraggio, manutenzione e eventuale dismissione, per garantire che rimanga efficace e allineato agli obiettivi.
​
Avvelenamento del modello: introdurre vulnerabilità o backdoor direttamente in un modello durante il processo di addestramento.
​
Furto/Rubare un Modello: Estrarre una copia o un'approssimazione di un modello proprietario tramite ripetute interrogazioni.
​
Sistema multi-agente: un sistema composto da più agenti di IA interagenti, ciascuno con potenzialmente capacità e obiettivi differenti.
​
OPA (Open Policy Agent): Un motore di policy open-source che consente l'applicazione unificata delle policy a tutti i livelli della stack.
​
Provenienza: La genealogia e la catena di custodia di un artefatto o un dataset, compresi la sua origine, i responsabili, il percorso di trasferimento e le prove di integrità (ad esempio, checksum, firme).
​
Apprendimento Automatico Preservante la Privacy (PPML): Tecniche e metodi per addestrare e distribuire modelli di ML proteggendo la privacy dei dati di addestramento.
​
Iniezione di prompt: un attacco in cui istruzioni dannose sono inserite negli input per sovrascrivere il comportamento previsto di un modello.
​
RAG (Generazione Incrementata dal Recupero): Una tecnica che migliora i grandi modelli linguistici recuperando informazioni rilevanti da fonti di conoscenza esterne prima di generare una risposta.
​
Red-Teaming: La pratica di testare attivamente i sistemi di IA simulando attacchi avversari per identificare le vulnerabilità.
​
Provenienza SLSA: Metadati definiti dal framework SLSA che registrano dove, quando e come è stato prodotto un artefatto (ad esempio, repository sorgente, hash del commit, sistema di build e parametri).
​
SBOM (Elenco dei Materiali Software): Un registro formale contenente i dettagli e le relazioni della catena di fornitura di vari componenti utilizzati nella creazione di software o modelli di AI.
​
SHAP (SHapley Additive exPlanations): un approccio basato sulla teoria dei giochi per spiegare l’output di qualsiasi modello di machine learning calcolando il contributo di ciascuna caratteristica alla previsione.
​
Autenticazione Forte: Autenticazione che resiste al furto di credenziali e al replay richiedendo almeno due fattori (conoscenza, possesso, inherenza) e meccanismi resistenti al phishing come FIDO2/WebAuthn, autenticazione di servizio basata su certificato o token a breve durata.
​
Attacco alla catena di approvvigionamento: compromettere un sistema prendendo di mira elementi meno sicuri nella sua catena di approvvigionamento, come librerie di terze parti, set di dati o modelli pre-addestrati.
​
Apprendimento di trasferimento: una tecnica in cui un modello sviluppato per un compito viene riutilizzato come punto di partenza per un modello su un secondo compito.
​
Database vettoriale: un database specializzato progettato per memorizzare vettori ad alta dimensionalità (embedding) ed eseguire ricerche di similarità in modo efficiente.
​
Scansione delle vulnerabilità: Strumenti automatizzati che identificano le vulnerabilità di sicurezza note nei componenti software, inclusi i framework AI e le dipendenze.
​
Watermarking: Tecniche per incorporare marcatori impercettibili nei contenuti generati dall'IA per tracciare la loro origine o rilevare la generazione da parte dell'IA.
​
Vulnerabilità Zero-Day: Una vulnerabilità precedentemente sconosciuta che gli attaccanti possono sfruttare prima che gli sviluppatori creino e distribuiscano una patch.

## Appendice B: Riferimenti

### DA FARE

## Appendice C: Governance della Sicurezza AI e Documentazione (Riorganizzata)

### Obiettivo

Questo appendice fornisce i requisiti fondamentali per stabilire strutture organizzative, politiche, documentazione e processi per governare la sicurezza dell'IA durante tutto il ciclo di vita del sistema.

────────────────────────────────────────

### AC.1 Adozione del Framework di Gestione del Rischio AI

 #AC.1.1    Livello: 1    Ruolo: D/V
 Verificare che una metodologia di valutazione del rischio specifica per l’AI sia documentata e implementata.
 #AC.1.2    Livello: 2    Ruolo: D
 Verificare che le valutazioni del rischio siano condotte nei punti chiave del ciclo di vita dell'IA e prima di cambiamenti significativi.
 #AC.1.3    Livello: 3    Ruolo: D/V
 Verificare che il quadro di gestione del rischio sia allineato agli standard stabiliti (ad esempio, NIST AI RMF).

────────────────────────────────────────

### AC.2 Politiche e Procedure di Sicurezza per l'IA

 #AC.2.1    Livello: 1    Ruolo: D/V
 Verificare che esistano politiche di sicurezza AI documentate.
 #AC.2.2    Livello: 2    Ruolo: D
 Verificare che le politiche siano revisionate e aggiornate almeno annualmente e dopo cambiamenti significativi nel panorama delle minacce.
 #AC.2.3    Livello: 3    Ruolo: D/V
 Verificare che le politiche coprano tutte le categorie AISVS e i requisiti normativi applicabili.

────────────────────────────────────────

### AC.3 Ruoli e Responsabilità per la Sicurezza dell'IA

 #AC.3.1    Livello: 1    Ruolo: D/V
 Verificare che i ruoli e le responsabilità della sicurezza AI siano documentati.
 #AC.3.2    Livello: 2    Ruolo: D
 Verificare che le persone responsabili possiedano un'adeguata competenza in materia di sicurezza.
 #AC.3.3    Livello: 3    Ruolo: D/V
 Verificare che sia stato istituito un comitato di etica dell'IA o un consiglio di governance per i sistemi di IA ad alto rischio.

────────────────────────────────────────

### AC.4 Applicazione delle linee guida etiche per l'IA

 #AC.4.1    Livello: 1    Ruolo: D/V
 Verificare che esistano linee guida etiche per lo sviluppo e l'implementazione dell'IA.
 #AC.4.2    Livello: 2    Ruolo: D
 Verificare che siano in atto meccanismi per rilevare e segnalare violazioni etiche.
 #AC.4.3    Livello: 3    Ruolo: D/V
 Verificare che vengano effettuate revisioni etiche regolari dei sistemi di IA dispiegati.

────────────────────────────────────────

### AC.5 Monitoraggio della conformità normativa dell'IA

 #AC.5.1    Livello: 1    Ruolo: D/V
 Verificare che esistano processi per identificare le normative sull’AI applicabili.
 #AC.5.2    Livello: 2    Ruolo: D
 Verificare che la conformità a tutti i requisiti normativi sia valutata.
 #AC.5.3    Livello: 3    Ruolo: D/V
 Verificare che le modifiche normative provochino revisioni e aggiornamenti tempestivi ai sistemi di intelligenza artificiale.

────────────────────────────────────────

### AC.6 Governance, documentazione e processo dei dati di addestramento

#### AC.6.1 Acquisizione dei dati e due diligence

 #AC.6.1.1    Livello: 1    Ruolo: D/V
 Verificare che vengano consentiti solo i dataset valutati per qualità, rappresentatività, approvvigionamento etico e conformità alle licenze, riducendo i rischi di avvelenamento, bias incorporati e violazione della proprietà intellettuale.
 #AC.6.1.2    Livello: 2    Ruolo: D/V
 Verificare che i fornitori di dati di terze parti, inclusi i fornitori di modelli pre-addestrati e set di dati esterni, siano sottoposti a controlli di due diligence riguardanti sicurezza, privacy, approvvigionamento etico e qualità dei dati prima che i loro dati o modelli vengano integrati.
 #AC.6.1.3    Livello: 1    Ruolo: D
 Verificare che i trasferimenti esterni utilizzino TLS/autenticazione e controlli di integrità.
 #AC.6.1.4    Livello: 2    Ruolo: D/V
 Verificare che le fonti di dati ad alto rischio (ad esempio, set di dati open-source con provenienza sconosciuta, fornitori non verificati) ricevano una valutazione approfondita, come l’analisi in sandbox, controlli estesi sulla qualità e sui bias, e il rilevamento mirato di avvelenamento, prima del loro utilizzo in applicazioni sensibili.
 #AC.6.1.5    Livello: 3    Ruolo: D/V
 Verificare che i modelli pre-addestrati ottenuti da terze parti siano valutati per bias incorporati, potenziali backdoor, integrità della loro architettura e provenienza dei dati di addestramento originali prima della messa a punto o del dispiegamento.

#### AC.6.2 Gestione di Bias e Equità

 #AC.6.2.1    Livello: 1    Ruolo: D/V
 Verificare che i dataset siano profilati per squilibri rappresentativi e potenziali bias riguardanti attributi legalmente protetti (ad esempio, razza, genere, età) e altre caratteristiche eticamente sensibili rilevanti per il dominio di applicazione del modello (ad esempio, status socio-economico, ubicazione).
 #AC.6.2.2    Livello: 2    Ruolo: D/V
 Verificare che i bias identificati siano mitigati tramite strategie documentate come il riequilibrio, l'aumento mirato dei dati, gli aggiustamenti algoritmici (ad esempio, tecniche di pre-processing, in-processing, post-processing) o la ripesatura, e che l'impatto della mitigazione sia valutato sia sulla equità che sulle prestazioni complessive del modello.
 #AC.6.2.3    Livello: 2    Ruolo: D/V
 Verificare che le metriche di equità post-addestramento siano valutate e documentate.
 #AC.6.2.4    Livello: 3    Ruolo: D/V
 Verificare che una politica di gestione del bias nel ciclo di vita assegni i responsabili e la cadenza delle revisioni.

#### AC.6.3 Governance dell'Etichettatura e dell'Annotazione

 #AC.6.3.1    Livello: 2    Ruolo: D/V
 Verificare che la qualità della etichettatura/annotazione sia garantita tramite controlli incrociati da parte dei revisori o consenso.
 #AC.6.3.2    Livello: 2    Ruolo: D/V
 Verificare che le schede dei dati vengano mantenute per i set di dati di addestramento significativi, dettagliando caratteristiche, motivazioni, composizione, processi di raccolta, preprocessing, licenze e usi raccomandati/sconsigliati.
 #AC.6.3.3    Livello: 2    Ruolo: D/V
 Verificare che le schede dei dati documentino i rischi di bias, le distorsioni demografiche e le considerazioni etiche rilevanti per il dataset.
 #AC.6.3.4    Livello: 2    Ruolo: D/V
 Verificare che le schede dei dati siano versionate insieme ai dataset e aggiornate ogni volta che il dataset viene modificato.
 #AC.6.3.5    Livello: 2    Ruolo: D/V
 Verificare che le schede dati siano riviste e approvate sia dagli stakeholder tecnici che non tecnici (ad esempio, conformità, etica, esperti del settore).
 #AC.6.3.6    Livello: 2    Ruolo: D/V
 Verificare che la qualità delle etichettature/annotazioni sia garantita tramite linee guida chiare, revisioni incrociate da parte dei valutatori, meccanismi di consenso (ad es., monitoraggio dell'accordo tra annotatori) e processi definiti per la risoluzione delle discrepanze.
 #AC.6.3.7    Livello: 3    Ruolo: D/V
 Verificare che le etichette critiche per la sicurezza, la protezione o l'equità (ad esempio, l'identificazione di contenuti tossici, risultati medici critici) ricevano una revisione duale indipendente obbligatoria o una verifica robusta equivalente.
 #AC.6.3.8    Livello: 2    Ruolo: D/V
 Verificare che le linee guida e le istruzioni per l'etichettatura siano complete, controllate nelle versioni e revisionate dai pari.
 #AC.6.3.9    Livello: 2    Ruolo: D/V
 Verificare che gli schemi dei dati per le etichette siano chiaramente definiti e controllati nella versione.
 #AC.6.3.10    Livello: 2    Ruolo: D/V
 Verificare che i flussi di lavoro di etichettatura esternalizzati o basati sul crowd includano salvaguardie tecniche/procedurali per garantire la riservatezza dei dati, l'integrità, la qualità delle etichette e prevenire la perdita di dati.
 #AC.6.3.11    Livello: 2    Ruolo: D/V
 Verificare che tutto il personale coinvolto nell'annotazione dei dati sia stato sottoposto a controlli di background e formato sulla sicurezza e la privacy dei dati.
 #AC.6.3.12    Livello: 2    Ruolo: D/V
 Verificare che tutto il personale di annotazione firmi accordi di riservatezza e non divulgazione.
 #AC.6.3.13    Livello: 2    Ruolo: D/V
 Verificare che le piattaforme di annotazione applichino controlli di accesso e monitorino le minacce interne.

#### AC.6.4 Gate di Qualità del Dataset e Messa in Quarantena

 #AC.6.4.1    Livello: 2    Ruolo: D/V
 Verificare che i dataset non riusciti siano messi in quarantena con tracce di audit.
 #AC.6.4.2    Livello: 2    Ruolo: D/V
 Verificare che le soglie di qualità blocchino i dataset di qualità inferiore a meno che non siano approvate eccezioni.
 #AC.6.4.3    Livello: 2    Ruolo: V
 Verificare che i controlli manuali a campione eseguiti da esperti del dominio coprano un campione statisticamente significativo (ad esempio, ≥1% o 1.000 campioni, a seconda di quale sia maggiore, o come determinato dalla valutazione del rischio) per identificare problemi di qualità sottili non rilevati dall’automazione.

#### AC.6.5 Rilevamento di minacce/avvelenamento e deriva

 #AC.6.5.1    Livello: 2    Ruolo: D/V
 Verificare che i campioni segnalati attivino una revisione manuale prima dell'addestramento.
 #AC.6.5.2    Livello: 2    Ruolo: V
 Verificare che i risultati alimentino il dossier di sicurezza del modello e informino l'intelligence sulle minacce in corso.
 #AC.6.5.3    Livello: 3    Ruolo: D/V
 Verificare che la logica di rilevamento sia aggiornata con nuove informazioni sulle minacce.
 #AC.6.5.4    Livello: 3    Ruolo: D/V
 Verificare che le pipeline di apprendimento online monitorino il drift di distribuzione.

#### AC.6.6 Cancellazione, Consenso, Diritti, Conservazione e Conformità

 #AC.6.6.1    Livello: 1    Ruolo: D/V
 Verificare che i flussi di lavoro per la cancellazione dei dati di addestramento eliminino sia i dati primari che quelli derivati e valutare l’impatto sul modello, assicurandosi che l'effetto sui modelli interessati venga valutato e, se necessario, affrontato (ad esempio mediante riaddestramento o riallineamento).
 #AC.6.6.2    Livello: 2    Ruolo: D
 Verificare che siano in atto meccanismi per monitorare e rispettare l'ambito e lo stato del consenso dell'utente (e dei suoi eventuali ritiri) per i dati utilizzati nell'addestramento, e che il consenso venga validato prima che i dati siano incorporati in nuovi processi di addestramento o aggiornamenti significativi del modello.
 #AC.6.6.3    Livello: 2    Ruolo: V
 Verificare che i workflow siano testati annualmente e registrati.
 #AC.6.6.4    Livello: 1    Ruolo: D/V
 Verificare che siano definiti periodi di conservazione espliciti per tutti i dataset di addestramento.
 #AC.6.6.5    Livello: 2    Ruolo: D/V
 Verificare che i set di dati vengano automaticamente scaduti, eliminati o esaminati per l'eliminazione alla fine del loro ciclo di vita.
 #AC.6.6.6    Livello: 2    Ruolo: D/V
 Verificare che le azioni di conservazione e cancellazione siano registrate e verificabili.
 #AC.6.6.7    Livello: 2    Ruolo: D/V
 Verificare che i requisiti di residenza dei dati e di trasferimento transfrontaliero siano identificati e applicati per tutti i set di dati.
 #AC.6.6.8    Livello: 2    Ruolo: D/V
 Verificare che le normative specifiche del settore (ad esempio, sanità, finanza) siano identificate e affrontate nella gestione dei dati.
 #AC.6.6.9    Livello: 2    Ruolo: D/V
 Verificare che la conformità alle leggi sulla privacy rilevanti (ad esempio, GDPR, CCPA) sia documentata e revisionata regolarmente.
 #AC.6.6.10    Livello: 2    Ruolo: D/V
 Verificare che esistano meccanismi per rispondere alle richieste dei soggetti dei dati riguardo all'accesso, alla rettifica, alla limitazione o all'opposizione.
 #AC.6.6.11    Livello: 2    Ruolo: D/V
 Verificare che le richieste siano registrate, tracciate e soddisfatte entro i tempi stabiliti dalla legge.
 #AC.6.6.12    Livello: 2    Ruolo: D/V
 Verificare che i processi relativi ai diritti dei soggetti dei dati siano testati e revisionati regolarmente per garantirne l'efficacia.

#### AC.6.7 Versioning e Gestione delle Modifiche

 #AC.6.7.1    Livello: 2    Ruolo: D/V
 Verificare che venga eseguita un'analisi d'impatto prima di aggiornare o sostituire una versione del dataset, includendo prestazioni del modello, equità e conformità.
 #AC.6.7.2    Livello: 2    Ruolo: D/V
 Verificare che i risultati dell'analisi d'impatto siano documentati e revisionati dalle parti interessate rilevanti.
 #AC.6.7.3    Livello: 2    Ruolo: D/V
 Verificare che esistano piani di rollback nel caso in cui le nuove versioni introducano rischi inaccettabili o regressioni.

#### AC.6.8 Governance dei Dati Sintetici

 #AC.6.8.1    Livello: 2    Ruolo: D/V
 Verifica che il processo di generazione, i parametri e l'uso previsto dei dati sintetici siano documentati.
 #AC.6.8.2    Livello: 2    Ruolo: D/V
 Verificare che i dati sintetici siano valutati in termini di rischio per bias, perdita di privacy e problemi di rappresentazione prima dell’uso nell’addestramento.

#### AC.6.9 Monitoraggio degli accessi

 #AC.6.9.1    Livello: 2    Ruolo: D/V
 Verificare che i log di accesso vengano regolarmente esaminati per individuare modelli insoliti, come esportazioni di grandi dimensioni o accessi da nuove località.
 #AC.6.9.2    Livello: 2    Ruolo: D/V
 Verificare che vengano generate allerte per eventi di accesso sospetti e che vengano indagate tempestivamente.

#### AC.6.10 Governance dell'addestramento avversariale

 #AC.6.10.1    Livello: 2    Ruolo: D/V
 Verificare che, se viene utilizzato l'addestramento avversario, la generazione, la gestione e la versione dei dataset avversari siano documentate e controllate.
 #AC.6.10.2    Livello: 3    Ruolo: D/V
 Verificare che l'impatto dell'addestramento alla robustezza adversaria sulle prestazioni del modello (sia contro input puliti che adversari) e sulle metriche di equità sia valutato, documentato e monitorato.
 #AC.6.10.3    Livello: 3    Ruolo: D/V
 Verificare che le strategie per l'addestramento avversariale e la robustezza siano periodicamente riviste e aggiornate per contrastare le tecniche di attacco avversario in evoluzione.

────────────────────────────────────────

### AC.7 Governance e Documentazione del Ciclo di Vita del Modello

 #AC.7.1    Livello: 2    Ruolo: D/V
 Verificare che tutti gli artefatti del modello utilizzino il versionamento semantico (MAJOR.MINOR.PATCH) con criteri documentati che specifichino quando incrementare ciascuna componente della versione.
 #AC.7.2    Livello: 2    Ruolo: D/V
 Verificare che le distribuzioni di emergenza richiedano una valutazione documentata del rischio di sicurezza e l'approvazione da parte di un'autorità di sicurezza predesignata entro i tempi concordati in anticipo.
 #AC.7.3    Livello: 2    Ruolo: V
 Verificare che gli artefatti di rollback (versioni precedenti del modello, configurazioni, dipendenze) siano conservati secondo le politiche organizzative.
 #AC.7.4    Livello: 2    Ruolo: D/V
 Verificare che l'accesso al registro di controllo richieda un'autorizzazione appropriata e che tutti i tentativi di accesso siano registrati con l'identità dell'utente e un timestamp.
 #AC.7.5    Livello: 1    Ruolo: D/V
 Verificare che gli artefatti del modello ritirato siano conservati in conformità alle politiche di conservazione dei dati.

────────────────────────────────────────

### Governance della sicurezza di prompt, input e output di AC.8

#### Difesa contro l'iniezione di prompt AC.8.1

 #AC.8.1.1    Livello: 2    Ruolo: D/V
 Verificare che i test di valutazione avversaria (ad esempio, i prompt "many-shot" del Red Team) vengano eseguiti prima di ogni rilascio di modello o template di prompt, con soglie di tasso di successo e blocchi automatizzati per regressioni.
 #AC.8.1.2    Livello: 3    Ruolo: D/V
 Verificare che tutti gli aggiornamenti delle regole del filtro dei prompt, le versioni del modello classificatore e le modifiche alla lista di blocco siano controllati nella versione e verificabili.

#### AC.8.2 Resistenza agli Esempi Avversari

 #AC.8.2.1    Livello: 3    Ruolo: D/V
 Verificare che le metriche di robustezza (tasso di successo delle suite di attacchi conosciuti) siano monitorate nel tempo tramite automazione e che le regressioni attivino un avviso.

#### AC.8.3 Screening dei Contenuti e delle Politiche

 #AC.8.3.1    Livello: 2    Ruolo: D
 Verificare che il modello di screening o il set di regole venga riaddestrato/aggiornato almeno ogni trimestre, incorporando i nuovi schemi di jailbreak o di superamento delle politiche osservati.

#### AC.8.4 Limitazione della velocità di input e prevenzione degli abusi

 #AC.8.4.1    Livello: 3    Ruolo: V
 Verificare che i log di prevenzione degli abusi siano conservati e riesaminati per individuare modelli di attacco emergenti.

#### AC.8.5 Provenienza e attribuzione dell'input

 #AC.8.5.1    Livello: 1    Ruolo: D/V
 Verificare che tutti gli input degli utenti siano contrassegnati con metadati (ID utente, sessione, fonte, timestamp, indirizzo IP) al momento dell’acquisizione.
 #AC.8.5.2    Livello: 2    Ruolo: D/V
 Verificare che i metadati di provenienza siano mantenuti e verificabili per tutti gli input elaborati.
 #AC.8.5.3    Livello: 2    Ruolo: D/V
 Verificare che le fonti di input anomale o non attendibili vengano segnalate e sottoposte a un controllo più rigoroso o al blocco.

────────────────────────────────────────

### AC.9 Validazione multimodale, MLOps e governance dell'infrastruttura

#### AC.9.1 Pipeline di convalida della sicurezza multimodale

 #AC.9.1.1    Livello: 3    Ruolo: D/V
 Verificare che i classificatori di contenuti specifici per modalità siano aggiornati secondo i programmi documentati (almeno trimestralmente) con nuovi schemi di minacce, esempi avversari e che i parametri di prestazione siano mantenuti al di sopra delle soglie di base.

#### AC.9.2 Sicurezza CI/CD & Build

 #AC.9.2.1    Livello: 1    Ruolo: D/V
 Verificare che l'infrastruttura come codice venga sottoposta a scansione ad ogni commit, e che le fusioni siano bloccate in presenza di risultati critici o ad alta gravità.
 #AC.9.2.2    Livello: 2    Ruolo: D/V
 Verificare che le pipeline CI/CD utilizzino identità a breve termine e con ambito definito per l'accesso a segreti e infrastrutture.
 #AC.9.2.3    Livello: 2    Ruolo: D/V
 Verificare che gli ambienti di build siano isolati dalle reti e dai dati di produzione.

#### AC.9.3 Sicurezza di Container e Immagini

 #AC.9.3.1    Livello: 2    Ruolo: D/V
 Verificare che le immagini dei container siano sottoposte a scansione per bloccare segreti hardcoded (ad esempio, chiavi API, credenziali, certificati).
 #AC.9.3.2    Livello: 1    Ruolo: D/V
 Verificare che le immagini dei container siano scansionate secondo i programmi organizzativi, con le vulnerabilità CRITICHE che bloccano il deployment in base alle soglie di rischio organizzative.

#### AC.9.4 Monitoraggio, Allerta e SIEM

 #AC.9.4.1    Livello: 2    Ruolo: V
 Verificare che gli avvisi di sicurezza si integrino con le piattaforme SIEM (Splunk, Elastic o Sentinel) utilizzando formati CEF o STIX/TAXII con arricchimento automatizzato.

#### AC.9.5 Gestione delle vulnerabilità

 #AC.9.5.1    Livello: 2    Ruolo: D/V
 Verificare che le vulnerabilità di gravità ALTA siano corrette secondo le tempistiche di gestione del rischio organizzativo, con procedure di emergenza per le CVE attivamente sfruttate.

#### AC.9.6 Configurazione e Controllo della Deriva

 #AC.9.6.1    Livello: 2    Ruolo: D/V
 Verificare che la deriva di configurazione venga rilevata utilizzando strumenti (Chef InSpec, AWS Config) secondo i requisiti di monitoraggio dell'organizzazione con rollback automatico per le modifiche non autorizzate.

#### AC.9.7 Indurimento dell'Ambiente di Produzione

 #AC.9.7.1    Livello: 2    Ruolo: D/V
 Verificare che gli ambienti di produzione blocchino l'accesso SSH, disabilitino gli endpoint di debug e richiedano richieste di modifica con requisiti di preavviso organizzativo, eccetto in caso di emergenze.

#### AC.9.8 Porte di promozione del rilascio

 #AC.9.8.1    Livello: 2    Ruolo: D/V
 Verificare che le fasi di promozione includano test di sicurezza automatizzati (SAST, DAST, scansione dei container) con nessuna rilevazione CRITICA richiesta per l’approvazione.

#### AC.9.9 Monitoraggio del carico di lavoro, della capacità e dei costi

 #AC.9.9.1    Livello: 1    Ruolo: D/V
 Verificare che l'utilizzo di GPU/TPU sia monitorato con avvisi attivati a soglie definite dall'organizzazione e che venga attivata la scalabilità automatica o il bilanciamento del carico basato sulle politiche di gestione della capacità.
 #AC.9.9.2    Livello: 1    Ruolo: D/V
 Verificare che le metriche del carico di lavoro AI (latenza di inferenza, throughput, tassi di errore) siano raccolte secondo i requisiti di monitoraggio organizzativo e correlate con l'utilizzo dell'infrastruttura.
 #AC.9.9.3    Livello: 2    Ruolo: V
 Verificare che il monitoraggio dei costi segua la spesa per carico di lavoro/tenant con avvisi basati sulle soglie di budget organizzativo e controlli automatizzati per superamenti del budget.
 #AC.9.9.4    Livello: 3    Ruolo: V
 Verificare che la pianificazione della capacità utilizzi dati storici con periodi di previsione definiti dall'organizzazione e un provisioning delle risorse automatizzato basato sui modelli di domanda.

#### AC.9.10 Approvazioni e Tracce di Audit

 #AC.9.10.1    Livello: 1    Ruolo: D/V
 Verificare che la promozione dell'ambiente richieda l'approvazione da parte del personale autorizzato definito a livello organizzativo con firme crittografiche e trilogie di audit immutabili.

#### AC.9.11 Governance IaC

 #AC.9.11.1    Livello: 2    Ruolo: D/V
 Verificare che le modifiche all'infrastructure-as-code richiedano una revisione tra pari con testing automatico e scansione di sicurezza prima della fusione nel ramo principale.

#### AC.9.12 Gestione dei dati in ambienti non di produzione

 #AC.9.12.1    Livello: 2    Ruolo: D/V
 Verificare che i dati non di produzione siano anonimizzati secondo i requisiti organizzativi sulla privacy, con generazione di dati sintetici o mascheramento completo dei dati con rimozione delle PII verificata.

#### AC.9.13 Backup e Recupero di Emergenza

 #AC.9.13.1    Livello: 1    Ruolo: D/V
 Verificare che le configurazioni dell'infrastruttura siano sottoposte a backup secondo i programmi di backup organizzativi verso regioni geograficamente separate con l'implementazione della strategia di backup 3-2-1.
 #AC.9.13.2    Livello: 2    Ruolo: V
 Verificare che le procedure di recupero siano testate e validate tramite test automatizzati secondo i programmi organizzativi, con obiettivi di RTO e RPO conformi ai requisiti dell'organizzazione.
 #AC.9.13.3    Livello: 3    Ruolo: V
 Verificare che il disaster recovery includa runbook specifici per l'AI con il ripristino dei pesi del modello, la ricostruzione del cluster GPU e la mappatura delle dipendenze dei servizi.

#### AC.9.14 Conformità e Documentazione

 #AC.9.14.1    Livello: 2    Ruolo: D/V
 Verificare che la conformità dell'infrastruttura venga valutata secondo i programmi organizzativi rispetto ai controlli SOC 2, ISO 27001 o FedRAMP con raccolta automatizzata delle evidenze.
 #AC.9.14.2    Livello: 2    Ruolo: V
 Verificare che la documentazione dell'infrastruttura includa diagrammi di rete, mappe del flusso dei dati e modelli di minaccia aggiornati secondo i requisiti della gestione del cambiamento organizzativo.
 #AC.9.14.3    Livello: 3    Ruolo: D/V
 Verificare che le modifiche all'infrastruttura siano sottoposte a una valutazione automatizzata dell'impatto sulla conformità con flussi di lavoro di approvazione normativa per le modifiche ad alto rischio.

#### AC.9.15 Hardware e Catena di Fornitura

 #AC.9.15.1    Livello: 2    Ruolo: D/V
 Verificare che il firmware dell'acceleratore AI (BIOS GPU, firmware TPU) sia verificato con firme crittografiche e aggiornato secondo le tempistiche di gestione delle patch dell'organizzazione.
 #AC.9.15.2    Livello: 3    Ruolo: V
 Verificare che la catena di approvvigionamento dell'hardware AI includa la verifica della provenienza con certificati del produttore e la convalida dell'imballaggio a prova di manomissione.

#### AC.9.16 Strategia Cloud e Portabilità

 #AC.9.16.1    Livello: 3    Ruolo: V
 Verificare che la prevenzione del vendor lock-in nel cloud includa infrastruttura-as-code portabile, API standardizzate e capacità di esportazione dei dati con strumenti di conversione del formato.
 #AC.9.16.2    Livello: 3    Ruolo: V
 Verificare che l'ottimizzazione dei costi multi-cloud includa controlli di sicurezza che prevengano la dispersione delle risorse e addebiti non autorizzati per il trasferimento dati cross-cloud.

#### AC.9.17 GitOps e Auto-Riparazione

 #AC.9.17.1    Livello: 2    Ruolo: D/V
 Verifica che i repository GitOps richiedano commit firmati con chiavi GPG e regole di protezione dei branch che impediscano push diretti ai branch principali.
 #AC.9.17.2    Livello: 3    Ruolo: V
 Verificare che l'infrastruttura autoprotettiva includa la correlazione degli eventi di sicurezza con la risposta automatizzata agli incidenti e i flussi di lavoro per la notifica agli stakeholder.

#### AC.9.18 Zero-Trust, Agenti, Provisioning e Attestazione di Residenza

 #AC.9.18.1    Livello: 2    Ruolo: D/V
 Verificare che l'accesso alle risorse cloud includa la verifica zero-trust con autenticazione continua.
 #AC.9.18.2    Livello: 2    Ruolo: D/V
 Verificare che il provisioning automatizzato dell'infrastruttura includa la convalida delle policy di sicurezza con il blocco del deployment per configurazioni non conformi.
 #AC.9.18.3    Livello: 2    Ruolo: D/V
 Verificare che il provisioning automatico dell'infrastruttura convalidi le politiche di sicurezza durante il CI/CD, bloccando le configurazioni non conformi al momento del deployment.
 #AC.9.18.4    Livello: 3    Ruolo: D/V
 Verificare che i requisiti di residenza dei dati siano applicati tramite attestazione crittografica delle ubicazioni di archiviazione.
 #AC.9.18.5    Livello: 3    Ruolo: D/V
 Verificare che le valutazioni di sicurezza del provider cloud includano la modellizzazione delle minacce specifica per l'agente e la valutazione del rischio.

#### AC.9.19 Controllo degli Accessi e Identità

 #5.1.3    Livello: 2    Ruolo: D
 Verificare che i nuovi responsabili siano sottoposti a un processo di verifica dell'identità conforme a NIST 800-63-3 IAL-2 o a standard equivalenti prima di ricevere l'accesso ai sistemi di produzione.
 #5.1.4    Livello: 2    Ruolo: V
 Verificare che le revisioni degli accessi vengano eseguite trimestralmente con rilevamento automatico degli account inattivi, applicazione della rotazione delle credenziali e flussi di lavoro di de-provisioning.
 #5.2.2    Livello: 1    Ruolo: D/V
 Verificare che i principi di minimo privilegio siano applicati di default agli account di servizio, iniziando con permessi in sola lettura e richiedendo una giustificazione aziendale documentata per l'accesso in scrittura.
 #5.3.3    Livello: 2    Ruolo: D
 Verificare che le definizioni delle policy siano controllate nelle versioni, revisionate dai pari e validate tramite test automatizzati nelle pipeline CI/CD prima del rilascio in produzione.
 #5.3.4    Livello: 2    Ruolo: V
 Verificare che i risultati della valutazione delle policy includano le motivazioni delle decisioni e siano trasmessi ai sistemi SIEM per l'analisi di correlazione e la generazione di report di conformità.
 #5.4.4    Livello: 2    Ruolo: V
 Verificare che la latenza nella valutazione delle policy sia continuamente monitorata con avvisi automatizzati per condizioni di timeout che potrebbero consentire il bypass dell'autorizzazione.
 #5.5.4    Livello: 2    Ruolo: V
 Verificare che gli algoritmi di redazione siano deterministici, controllati nelle versioni e mantengano registri di audit per supportare le indagini di conformità e l'analisi forense.
 #5.5.5    Livello: 3    Ruolo: V
 Verificare che gli eventi di redazione ad alto rischio generino log adattivi che includano hash crittografici del contenuto originale per il recupero forense senza esposizione dei dati.
 #5.7.5    Livello: 3    Ruolo: V
 Verificare che le condizioni di errore dell'agente e la gestione delle eccezioni includano informazioni sull'ambito delle capacità per supportare l'analisi degli incidenti e le indagini forensi.
 #5.4.2    Livello: 1    Ruolo: D/V
 Verificare che le citazioni, le referenze e le attribuzioni delle fonti nei risultati del modello siano convalidate in base ai diritti del chiamante e rimosse se viene rilevato un accesso non autorizzato.

#### Nuovi elementi da integrare sopra

 #2.3.3    Livello: 2    Ruolo: D/V
 Verificare che l'insieme di caratteri consentiti venga regolarmente esaminato e aggiornato per garantire che rimanga allineato ai requisiti aziendali.

## Appendice D: Governance e Verifica del Coding Sicuro Assistito da AI

### Obiettivo

Questo capitolo definisce i controlli organizzativi di base per l'uso sicuro ed efficace degli strumenti di codifica assistita da AI durante lo sviluppo software, garantendo sicurezza e tracciabilità lungo tutto il SDLC.

────────────────────────────────────────

### AD.1 Flusso di lavoro di codifica sicura assistita dall'IA

Integrare gli strumenti di AI nel ciclo di vita dello sviluppo software sicuro (SSDLC) dell'organizzazione senza indebolire le barriere di sicurezza esistenti.

 #AD.1.1    Livello: 1    Ruolo: D/V
 Verificare che un flusso di lavoro documentato descriva quando e come gli strumenti di IA possono generare, rifattorizzare o revisionare il codice.
 #AD.1.2    Livello: 2    Ruolo: D
 Verificare che il flusso di lavoro corrisponda a ciascuna fase dell'SSDLC (progettazione, implementazione, revisione del codice, testing, distribuzione).
 #AD.1.3    Livello: 3    Ruolo: D/V
 Verificare che le metriche (ad esempio, densità di vulnerabilità, tempo medio di rilevamento) siano raccolte sul codice prodotto dall’IA e confrontate con i parametri di riferimento esclusivamente umani.

────────────────────────────────────────

### AD.2 Qualificazione degli Strumenti di AI e Modellazione delle Minacce

Assicurarsi che gli strumenti di codifica AI vengano valutati in base alle capacità di sicurezza, ai rischi e all'impatto sulla catena di approvvigionamento prima dell'adozione.

 #AD.2.1    Livello: 1    Ruolo: D/V
 Verificare che un modello di minaccia per ogni strumento di intelligenza artificiale identifichi gli abusi, l'inversione del modello, la fuoriuscita di dati e i rischi della catena di dipendenza.
 #AD.2.2    Livello: 2    Ruolo: D
 Verificare che le valutazioni degli strumenti includano l'analisi statica/dinamica di qualsiasi componente locale e la valutazione degli endpoint SaaS (TLS, autenticazione/autorizzazione, logging).
 #AD.2.3    Livello: 3    Ruolo: D/V
 Verificare che le valutazioni seguano un quadro riconosciuto e vengano rieseguite dopo cambiamenti di versione importanti.

────────────────────────────────────────

### AD.3 Gestione Sicura di Prompt e Contesto

Prevenire la fuoriuscita di segreti, codice proprietario e dati personali durante la costruzione di prompt o contesti per modelli di intelligenza artificiale.

 #AD.3.1    Livello: 1    Ruolo: D/V
 Verificare che le linee guida scritte proibiscano l'invio di segreti, credenziali o dati classificati nei prompt.
 #AD.3.2    Livello: 2    Ruolo: D
 Verificare che i controlli tecnici (redazione lato client, filtri di contesto approvati) rimuovano automaticamente gli elementi sensibili.
 #AD.3.3    Livello: 3    Ruolo: D/V
 Verificare che i prompt e le risposte siano tokenizzati, criptati durante il transito e a riposo, e che i periodi di conservazione siano conformi alla politica di classificazione dei dati.

────────────────────────────────────────

### AD.4 Validazione del codice generato dall’IA

Individuare e correggere le vulnerabilità introdotte dall'output dell'IA prima che il codice venga unito o distribuito.

 #AD.4.1    Livello: 1    Ruolo: D/V
 Verificare che il codice generato dall'IA sia sempre soggetto a revisione umana del codice.
 #AD.4.2    Livello: 2    Ruolo: D
 Verificare che gli scanner automatizzati (SAST/IAST/DAST) vengano eseguiti su ogni pull request contenente codice generato da AI e bloccare le fusioni in presenza di riscontri critici.
 #AD.4.3    Livello: 3    Ruolo: D/V
 Verificare che il differential fuzz testing o i test basati sulle proprietà dimostrino comportamenti critici per la sicurezza (ad esempio, la validazione degli input, la logica di autorizzazione).

────────────────────────────────────────

### AD.5 Spiegabilità e Tracciabilità delle Suggerimenti di Codice

Fornire a revisori e sviluppatori una comprensione del motivo per cui è stata fatta una proposta e di come si è evoluta.

 #AD.5.1    Livello: 1    Ruolo: D/V
 Verificare che le coppie prompt/risposta siano registrate con gli ID di commit.
 #AD.5.2    Livello: 2    Ruolo: D
 Verificare che gli sviluppatori possano visualizzare le citazioni del modello (estratti di addestramento, documentazione) a supporto di un suggerimento.
 #AD.5.3    Livello: 3    Ruolo: D/V
 Verificare che i report di spiegabilità siano archiviati con gli artefatti di progettazione e referenziati nelle revisioni di sicurezza, soddisfacendo i principi di tracciabilità dello standard ISO/IEC 42001.

────────────────────────────────────────

### AD.6 Feedback Continuo e Messa a Punto del Modello

Migliorare le prestazioni di sicurezza del modello nel tempo prevenendo deriva negativa.

 #AD.6.1    Livello: 1    Ruolo: D/V
 Verificare che gli sviluppatori possano segnalare suggerimenti non sicuri o non conformi e che le segnalazioni siano tracciate.
 #AD.6.2    Livello: 2    Ruolo: D
 Verificare che il feedback aggregato informi la messa a punto periodica o la generazione aumentata da recupero con corpora di codifica sicura verificati (ad esempio, OWASP Cheat Sheets).
 #AD.6.3    Livello: 3    Ruolo: D/V
 Verificare che un sistema di valutazione a ciclo chiuso esegua test di regressione dopo ogni fine-tuning; le metriche di sicurezza devono soddisfare o superare le baseline precedenti prima della distribuzione.

────────────────────────────────────────

#### Riferimenti

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Appendice E: Esempi di Strumenti e Framework

### Obiettivo

Questo capitolo fornisce esempi di strumenti e framework che possono supportare l'implementazione o il soddisfacimento di un determinato requisito AISVS. Questi non devono essere considerati come raccomandazioni o approvazioni da parte del team AISVS o del Progetto di Sicurezza OWASP GenAI.

────────────────────────────────────────

### AE.1 Governance dei Dati di Addestramento e Gestione del Bias

Strumenti utilizzati per l'analisi dei dati, la governance e la gestione dei bias.

 #AE.1.1    Sezione: 1.1
 Strumenti per l'inventario dei dati: Strumenti per la gestione dell'inventario dei dati come...
 #AE.1.2    Sezione: 1.2
 Crittografia in transito Usa TLS per applicazioni basate su HTTPS, con strumenti come openSSL e python's`ssl` libreria.

────────────────────────────────────────

### AE.2 Validazione dell'Input Utente

Strumenti per gestire e convalidare gli input degli utenti.

 #AE.2.1    Sezione: 2.1
 Strumenti di Difesa contro l'Iniezione di Prompt: Utilizzare strumenti di protezione come NeMo di NVIDIA o Guardrails AI.

────────────────────────────────────────

## Appendice B: Controlli Strategici

### C4.15 Sicurezza dell'Infrastruttura Resistente alla Quantum

Preparare l'infrastruttura AI per le minacce del calcolo quantistico tramite crittografia post-quantistica e protocolli quantisticamente sicuri.

 #4.15.1    Livello: 3    Ruolo: D/V
 Verificare che l'infrastruttura AI implementi algoritmi crittografici post-quantistici approvati dal NIST (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) per lo scambio di chiavi e le firme digitali.
 #4.15.2    Livello: 3    Ruolo: D/V
 Verificare che i sistemi di distribuzione di chiavi quantistiche (QKD) siano implementati per comunicazioni AI ad alta sicurezza con protocolli di gestione chiavi quantum-safe.
 #4.15.3    Livello: 3    Ruolo: D/V
 Verificare che i framework di agilità crittografica permettano una migrazione rapida verso i nuovi algoritmi post-quantistici con rotazione automatica di certificati e chiavi.
 #4.15.4    Livello: 3    Ruolo: V
 Verificare che la modellazione delle minacce quantistiche valuti la vulnerabilità dell'infrastruttura AI ad attacchi quantistici con tempi di migrazione documentati e valutazioni del rischio.
 #4.15.5    Livello: 3    Ruolo: D/V
 Verificare che i sistemi crittografici ibridi classico-quantistici forniscano una difesa stratificata durante il periodo di transizione quantistica con monitoraggio delle prestazioni.

────────────────────────────────────────

### C4.17 Infrastruttura a Conoscenza Zero

Implementare sistemi di zero-knowledge proof per la verifica e l'autenticazione di AI che preservano la privacy senza rivelare informazioni sensibili.

 #4.17.1    Livello: 3    Ruolo: D/V
 Verificare che le prove a conoscenza zero (ZK-SNARKs, ZK-STARKs) confermino l'integrità del modello AI e la provenienza dell'addestramento senza esporre i pesi del modello o i dati di addestramento.
 #4.17.2    Livello: 3    Ruolo: D/V
 Verificare che i sistemi di autenticazione basati su ZK consentano la verifica degli utenti preservando la privacy per i servizi AI senza rivelare informazioni correlate all'identità.
 #4.17.3    Livello: 3    Ruolo: D/V
 Verificare che i protocolli di intersezione di insiemi privati (PSI) consentano un confronto sicuro dei dati per l’IA federata senza esporre i singoli set di dati.
 #4.17.4    Livello: 3    Ruolo: D/V
 Verificare che i sistemi di machine learning a conoscenza zero (ZKML) permettano inferenze AI verificabili con prova crittografica del calcolo corretto.
 #4.17.5    Livello: 3    Ruolo: D/V
 Verificare che gli ZK-rollup forniscano un'elaborazione delle transazioni AI scalabile e preservante la privacy con verifica batch e ridotto overhead computazionale.

────────────────────────────────────────

### C4.18 Prevenzione degli Attacchi Side-Channel

Proteggi l'infrastruttura AI dagli attacchi side-channel basati su tempistiche, potenza, elettromagnetismo e cache che potrebbero divulgare informazioni sensibili.

 #4.18.1    Livello: 3    Ruolo: D/V
 Verificare che il tempo di inferenza dell’IA sia normalizzato utilizzando algoritmi a tempo costante e padding per prevenire attacchi di estrazione del modello basati sul tempo.
 #4.18.2    Livello: 3    Ruolo: D/V
 Verifica che la protezione contro l'analisi della potenza includa l'iniezione di rumore, il filtraggio della linea di alimentazione e modelli di esecuzione randomizzati per l'hardware AI.
 #4.18.3    Livello: 3    Ruolo: D/V
 Verificare che la mitigazione dei canali laterali basati sulla cache utilizzi la partizione della cache, la randomizzazione e le istruzioni di flush per prevenire la fuoriuscita di informazioni.
 #4.18.4    Livello: 3    Ruolo: D/V
 Verificare che la protezione dalle emanazioni elettromagnetiche includa schermatura, filtraggio del segnale e elaborazione casuale per prevenire attacchi di tipo TEMPEST.
 #4.18.5    Livello: 3    Ruolo: D/V
 Verificare che le difese contro i canali laterali microarchitetturali includano controlli sull'esecuzione speculativa e l'oscuramento dei modelli di accesso alla memoria.

────────────────────────────────────────

### C4.19 Sicurezza dell'hardware neuromorfico e specializzato per l'IA

Proteggere le architetture hardware emergenti per l'IA, inclusi chip neuromorfici, FPGA, ASIC personalizzati e sistemi di calcolo ottico.

 #4.19.1    Livello: 3    Ruolo: D/V
 Verificare che la sicurezza del chip neuromorfico includa la crittografia dei modelli di spike, la protezione dei pesi sinaptici e la convalida basata sull'hardware delle regole di apprendimento.
 #4.19.2    Livello: 3    Ruolo: D/V
 Verificare che gli acceleratori AI basati su FPGA implementino la crittografia del bitstream, meccanismi anti-manomissione e il caricamento sicuro della configurazione con aggiornamenti autenticati.
 #4.19.3    Livello: 3    Ruolo: D/V
 Verificare che la sicurezza ASIC personalizzata includa processori di sicurezza on-chip, root di fiducia hardware e memorizzazione sicura delle chiavi con rilevamento delle manomissioni.
 #4.19.4    Livello: 3    Ruolo: D/V
 Verificare che i sistemi di calcolo ottico implementino crittografia ottica quantisticamente sicura, commutazione fotonica sicura e elaborazione del segnale ottico protetta.
 #4.19.5    Livello: 3    Ruolo: D/V
 Verificare che i chip AI ibridi analogico-digitali includano calcolo analogico sicuro, archiviazione protetta dei pesi e conversione analogico-digitale autenticata.

────────────────────────────────────────

### C4.20 Infrastruttura di Calcolo per la Privacy

Implementare controlli infrastrutturali per il calcolo che preserva la privacy al fine di proteggere i dati sensibili durante l'elaborazione e l'analisi dell'IA.

 #4.20.1    Livello: 3    Ruolo: D/V
 Verificare che l'infrastruttura di crittografia omomorfica consenta il calcolo crittografato su carichi di lavoro AI sensibili con verifica dell'integrità crittografica e monitoraggio delle prestazioni.
 #4.20.2    Livello: 3    Ruolo: D/V
 Verificare che i sistemi di recupero privato delle informazioni consentano interrogazioni al database senza rivelare i modelli di query, proteggendo crittograficamente i modelli di accesso.
 #4.20.3    Livello: 3    Ruolo: D/V
 Verificare che i protocolli di calcolo multipartito sicuro consentano l'inferenza AI preservando la privacy senza esporre input individuali o calcoli intermedi.
 #4.20.4    Livello: 3    Ruolo: D/V
 Verificare che la gestione delle chiavi preservi la privacy includa la generazione distribuita delle chiavi, la crittografia a soglia e la rotazione sicura delle chiavi con protezione supportata da hardware.
 #4.20.5    Livello: 3    Ruolo: D/V
 Verificare che le prestazioni del calcolo a tutela della privacy siano ottimizzate tramite batching, caching e accelerazione hardware, mantenendo al contempo le garanzie di sicurezza crittografica.

 4.9.14.9.2    1: 2    D/V: D/V
 Verificare che le distribuzioni multi-cloud utilizzino standard di identità federata (ad es., OIDC, SAML) con applicazione centralizzata delle policy tra i provider.
 4.9.14.9.3    1: 2    D/V: D/V
 Verificare che i trasferimenti di dati cross-cloud e ibridi utilizzino la crittografia end-to-end con chiavi gestite dal cliente e rispettino i requisiti di residenza dei dati giurisdizionale.
 4.9.14.9.1    1: 1    D/V: D/V
 Verificare che l'integrazione dello storage cloud utilizzi la crittografia end-to-end con la gestione delle chiavi controllata dall'agente.
 4.9.14.9.2    1: 2    D/V: D/V
 Verificare che i confini di sicurezza del deployment ibrido siano chiaramente definiti con canali di comunicazione crittografati.

