## Frontespizio

### Informazioni sullo standard

Lo Standard di Verifica della Sicurezza dell'Intelligenza Artificiale (AISVS) è un catalogo guidato dalla comunità di requisiti di sicurezza che scienziati dei dati, ingegneri MLOps, architetti del software, sviluppatori, tester, professionisti della sicurezza, fornitori di strumenti, regolatori e consumatori possono utilizzare per progettare, costruire, testare e verificare sistemi e applicazioni abilitati all'IA affidabili. Fornisce un linguaggio comune per specificare i controlli di sicurezza lungo l'intero ciclo di vita dell'IA, dalla raccolta dei dati e dallo sviluppo del modello fino al dispiegamento e al monitoraggio continuo, in modo che le organizzazioni possano misurare e migliorare la resilienza, la privacy e la sicurezza delle loro soluzioni di IA.

### Diritti d'autore e licenza

Versione 0.1 (Prima bozza pubblica - in sviluppo), 2025  

![license](images/license.png)
Diritti d'autore © 2025 The AISVS Project.  

Rilasciato sotto laCreative Commons Attribution‑ShareAlike 4.0 International License.
Per qualsiasi riutilizzo o distribuzione, devi comunicare chiaramente i termini di licenza di questa opera agli altri.

### Responsabili di progetto

Jim Manico
Aras “Russ” Memisyazici

### Contributori e Revisori

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


---

AISVS è uno standard nuovissimo creato appositamente per affrontare le sfide di sicurezza uniche dei sistemi di intelligenza artificiale. Pur prendendo ispirazione dalle migliori pratiche di sicurezza più ampie, ogni requisito di AISVS è stato sviluppato ex novo per riflettere il panorama delle minacce legate all'IA e per aiutare le organizzazioni a costruire soluzioni di IA più sicure e robuste.

## Prefazione

Benvenuto nello Standard di Verifica della Sicurezza dell'Intelligenza Artificiale (AISVS) versione 1.0!

### Introduzione

Fondata nel 2025 attraverso uno sforzo collaborativo della comunità, AISVS definisce i requisiti di sicurezza da considerare durante la progettazione, lo sviluppo, l'implementazione e l'operatività di modelli di IA moderni, pipeline e servizi abilitati dall'IA.

AISVS v1.0 rappresenta il lavoro congiunto dei suoi responsabili di progetto, del gruppo di lavoro e dei contributori della comunità più ampia, al fine di produrre una base di riferimento pragmatica e testabile per mettere in sicurezza i sistemi di IA.

Il nostro obiettivo con questo rilascio è rendere AISVS facile da adottare, mantenendo al contempo una focalizzazione estremamente mirata sul suo ambito definito e affrontando il panorama dei rischi in rapida evoluzione tipico dell'IA.

### Obiettivi chiave per AISVS Versione 1.0

La versione 1.0 sarà creata con diversi principi guida.

#### Ambito ben definito

Ogni requisito deve allinearsi al nome e alla missione di AISVS:

Intelligenza Artificiale – i controlli operano a livello AI/ML (dati, modello, pipeline o inferenza) e sono responsabilità dei professionisti dell'IA.
Sicurezza – I requisiti mitigano direttamente i rischi identificati relativi alla sicurezza, alla privacy o alla tutela della sicurezza.
Verificazione – Il linguaggio è scritto in modo che la conformità possa essere oggettivamente validata.
Standard – Le sezioni seguono una struttura e una terminologia coerenti per formare un riferimento coerente.
​
---

Seguendo AISVS, le organizzazioni possono valutare in modo sistematico e rafforzare il profilo di sicurezza delle loro soluzioni di IA, promuovendo una cultura dell'ingegneria dell'IA sicura.

## Utilizzando l'AISVS

Lo Standard di Verifica della Sicurezza dell'Intelligenza Artificiale (AISVS) definisce i requisiti di sicurezza per le moderne applicazioni e servizi di IA, concentrandosi sugli aspetti entro il controllo degli sviluppatori delle applicazioni.

L'AISVS è destinato a chiunque sviluppi o valuti la sicurezza delle applicazioni di IA, inclusi sviluppatori, architetti, ingegneri della sicurezza e revisori. Questo capitolo presenta la struttura e l'utilizzo dell'AISVS, inclusi i suoi livelli di verifica e i casi d'uso previsti.

### Livelli di verifica della sicurezza dell'intelligenza artificiale

L'AISVS definisce tre livelli crescenti di verifica della sicurezza. Ogni livello aggiunge profondità e complessità, consentendo alle organizzazioni di adeguare la propria postura di sicurezza al livello di rischio dei loro sistemi di IA.

Le organizzazioni possono iniziare dal Livello 1 e adottare progressivamente livelli superiori man mano che aumentano la maturità della sicurezza e l'esposizione alle minacce.

#### Definizione dei livelli

Ogni requisito in AISVS v1.0 viene assegnato a uno dei seguenti livelli:

 Requisiti di livello 1

Livello 1 include i requisiti di sicurezza più critici e fondamentali. Questi si concentrano sulla prevenzione di attacchi comuni che non dipendono da altri prerequisiti o vulnerabilità. La maggior parte dei controlli di Livello 1 è di facile implementazione o è abbastanza essenziale da giustificare l'impegno.

 Requisiti di livello 2

Livello 2 affronta attacchi più avanzati o meno comuni, nonché difese a strati contro minacce diffuse. Questi requisiti possono comportare una logica più complessa o mirare a prerequisiti specifici dell'attacco.

 Requisiti di livello 3

Il livello 3 include controlli che sono tipicamente più difficili da implementare o applicabili solo in determinate situazioni. Questi controlli spesso rappresentano meccanismi di difesa in profondità o mitigazioni contro attacchi di nicchia, mirati o ad alta complessità.

#### Ruolo (D/V)

Ogni requisito AISVS è contrassegnato in base al pubblico primario:

D – Requisiti orientati agli sviluppatori
V – Requisiti incentrati sul verificatore/auditor
D/V – Rilevante sia per gli sviluppatori che per i verificatori

## C1 Governance dei dati di addestramento e gestione dei bias

### Obiettivo di controllo

I dati di addestramento devono essere reperiti, gestiti e mantenuti in modo da preservarne la provenienza, la sicurezza, la qualità e l'equità. Ciò adempie agli obblighi legali e riduce i rischi di pregiudizio, avvelenamento dei dati o violazioni della privacy che emergono durante l'addestramento e che potrebbero influire sull'intero ciclo di vita dell'IA.

---

### C1.1 Provenienza dei dati di addestramento

Mantenere un inventario verificabile di tutti i dataset, accettare solo fonti affidabili e registrare ogni modifica per l'auditabilità.

 #1.1.1    Livello: 1    Ruolo: D/V
 Verificare che sia mantenuto un inventario aggiornato di ogni fonte di dati di addestramento (origine, custode/proprietario, licenza, metodo di raccolta, vincoli d'uso previsti e storia del trattamento).
 #1.1.2    Livello: 1    Ruolo: D/V
 Verificare che i processi sui dati di addestramento escludano caratteristiche, attributi o campi non necessari (ad esempio metadati inutilizzati, informazioni personali identificabili (PII) sensibili, dati di test trapelati).
 #1.1.3    Livello: 2    Ruolo: D/V
 Verifica che tutte le modifiche al set di dati siano soggette a un flusso di approvazione registrato.
 #1.1.4    Livello: 3    Ruolo: D/V
 Verificare che i dataset o i sottoinsiemi siano contrassegnati con filigrana o impronta digitale, ove possibile.

---

### C1.2 Sicurezza e integrità dei dati di addestramento

Limitare l'accesso ai dati di addestramento, crittografare i dati a riposo e in transito, e verificarne l'integrità per prevenire manomissioni, furti o avvelenamento dei dati.

 #1.2.1    Livello: 1    Ruolo: D/V
 Verifica che i controlli di accesso proteggano l'archiviazione dei dati di addestramento e le pipeline.
 #1.2.2    Livello: 2    Ruolo: D/V
 Verifica che tutti gli accessi ai dati di addestramento siano registrati, inclusi l'utente, l'ora e l'azione.
 #1.2.3    Livello: 2    Ruolo: D/V
 Verificare che i set di dati di addestramento siano cifrati sia in transito che a riposo, utilizzando algoritmi crittografici standard di settore e pratiche di gestione delle chiavi.
 #1.2.4    Livello: 2    Ruolo: D/V
 Verifica che vengano utilizzati hash crittografici o firme digitali per garantire l'integrità dei dati durante l'archiviazione e il trasferimento dei dati di addestramento.
 #1.2.5    Livello: 2    Ruolo: D/V
 Verificare che le tecniche di rilevamento automatico siano applicate per prevenire modifiche non autorizzate o la corruzione dei dati di addestramento.
 #1.2.6    Livello: 2    Ruolo: D/V
 Verificare che i dati di addestramento obsoleti siano eliminati in modo sicuro o anonimizzati.
 #1.2.7    Livello: 3    Ruolo: D/V
 Verificare che tutte le versioni del dataset di addestramento siano identificate in modo univoco, archiviate in modo immutabile e auditabili per supportare il rollback e l’analisi forense.

---

### C1.3 Qualità, integrità e sicurezza dell'etichettatura dei dati di addestramento

Proteggere le etichette e richiedere una revisione tecnica per i dati critici.

 #1.3.1    Livello: 2    Ruolo: D/V
 Verificare che gli hash crittografici o le firme digitali siano applicati agli artefatti di etichettatura per garantire la loro integrità e autenticità.
 #1.3.2    Livello: 2    Ruolo: D/V
 Verifichi che le interfacce di etichettatura e le piattaforme applichino controlli di accesso robusti, mantengano registri di audit a prova di manomissione di tutte le attività di etichettatura e proteggano da modifiche non autorizzate.
 #1.3.3    Livello: 3    Ruolo: D/V
 Verifica che le informazioni sensibili presenti nelle etichette siano oscurate, anonimizzate o criptate a livello di campo dati a riposo e in transito.

---

### C1.4 Garanzia della qualità e della sicurezza dei dati di addestramento

Combinare la validazione automatica, controlli manuali a campione e interventi correttivi registrati per garantire l'affidabilità del set di dati.

 #1.4.1    Livello: 1    Ruolo: D
 Verifica che i test automatizzati catturino errori di formato e valori nulli in ogni ingestione o trasformazione significativa dei dati.
 #1.4.2    Livello: 2    Ruolo: D/V
 Verifica che le pipeline di addestramento e di fine-tuning degli LLM implementino il rilevamento dell'avvelenamento e la validazione dell'integrità dei dati (ad es. metodi statistici, rilevamento di outlier, analisi degli embedding) per identificare potenziali attacchi di avvelenamento (ad es. ribaltamento delle etichette, inserimento di trigger di backdoor, comandi di cambio di ruolo, attacchi a istanze influenti) o corruzione involontaria dei dati di addestramento.
 #1.4.3    Livello: 3    Ruolo: D/V
 Verifica che siano implementate e tarate difese adeguate, come l'addestramento avversario (utilizzando esempi avversari generati), l'aumento dei dati con input perturbati o tecniche di ottimizzazione robuste, in base alla valutazione del rischio.
 #1.4.4    Livello: 2    Ruolo: D/V
 Verificare che le etichette generate automaticamente (ad es. tramite modelli linguistici di grandi dimensioni (LLMs) o supervisione debole) siano soggette a soglie di confidenza e controlli di coerenza per rilevare etichette allucinatorie, fuorvianti o con bassa confidenza.
 #1.4.5    Livello: 3    Ruolo: D
 Verifica che i test automatizzati rilevino gli sbilanciamenti delle etichette in ogni ingestione o trasformazione significativa dei dati.

---

### C1.5 Provenienza e tracciabilità dei dati

Traccia l'intero percorso di ogni dato dall'origine all'input del modello per auditabilità e gestione degli incidenti.

 #1.5.1    Livello: 2    Ruolo: D/V
 Verificare che la tracciabilità di ogni punto dati, comprese tutte le trasformazioni, le augmentazioni e le fusioni, sia registrata e possa essere ricostruita.
 #1.5.2    Livello: 2    Ruolo: D/V
 Verificare che i registri di provenienza dei dati siano immutabili, conservati in modo sicuro e accessibili per gli audit.
 #1.5.3    Livello: 2    Ruolo: D/V
 Verificare che il tracciamento della provenienza dei dati comprenda i dati sintetici generati tramite tecniche di tutela della privacy o tecniche generative e che tutti i dati sintetici siano chiaramente etichettati e distinguibili dai dati reali lungo l'intero flusso di lavoro.

---

### Riferimenti

NIST AI Risk Management Framework
EU AI Act – Article 10: Data & Data Governance
MITRE ATLAS: Adversary Tactics for AI
Survey of ML Bias Mitigation Techniques – MDPI
Data Provenance & Lineage Best Practices – Nightfall AI
Data Labeling Quality Standards – LabelYourData
Training Data Poisoning Guide – Lakera.ai
CISA Advisory: Securing Data for AI Systems
ISO/IEC 23053: AI Management Systems Framework
IBM: What is AI Governance?
Google AI Principles
GDPR & AI Training Data – DataProtectionReport
Supply-Chain Security for AI Data – AppSOC
OpenAI Privacy Center – Data Deletion Controls
Adversarial ML Dataset – Kaggle

## C2 Validazione dell'input dell'utente

### Obiettivo di controllo

Una validazione robusta dell'input dell'utente è una prima linea di difesa contro alcuni degli attacchi più dannosi rivolti ai sistemi di IA. Gli attacchi di iniezione di prompt possono sovrascrivere le istruzioni di sistema, rivelare dati sensibili o guidare il modello verso comportamenti non consentiti. A meno che non siano presenti filtri dedicati e gerarchie di istruzioni, la ricerca mostra che "multi-shot" jailbreaks che sfruttano finestre di contesto molto lunghe saranno efficaci. Inoltre, attacchi di perturbazione avversaria sottili--come scambi di omografi o leetspeak—possono modificare silenziosamente le decisioni del modello.

---

### C2.1 Difesa contro l'iniezione di prompt

L'iniezione di prompt è uno dei principali rischi per i sistemi di IA. Le difese contro questa tattica impiegano una combinazione di filtri di pattern statici, classificatori dinamici e l'applicazione della gerarchia delle istruzioni.

 #2.1.1    Livello: 1    Ruolo: D/V
 Verifichi che gli input degli utenti siano filtrati rispetto a una libreria costantemente aggiornata di schemi noti di prompt injection (parole chiave di jailbreak, "ignore previous", catene di gioco di ruolo, attacchi indiretti HTML/URL).
 #2.1.2    Livello: 1    Ruolo: D/V
 Verifica che il sistema faccia rispettare una gerarchia di istruzioni in cui i messaggi di sistema o di sviluppatore hanno la precedenza sulle istruzioni dell'utente, anche dopo l'espansione della finestra di contesto.
 #2.1.3    Livello: 2    Ruolo: D/V
 Verifica che i test di valutazione avversaria (ad es. i prompt della Red Team 'many-shot') siano eseguiti prima di ogni rilascio di modello o di template di prompt, con soglie di tasso di successo e blocchi automatici per le regressioni.
 #2.1.4    Livello: 2    Ruolo: D
 Verifica che i prompt originati da contenuti di terze parti (pagine Web, PDF, email) siano sanificati in un contesto di parsing isolato prima di essere concatenati nel prompt principale.
 #2.1.5    Livello: 3    Ruolo: D/V
 Verifica che tutti gli aggiornamenti delle regole del prompt-filter, le versioni dei modelli classificatori e le modifiche al block-list siano sotto controllo di versione e auditabili.

---

### C2.2 Resistenza agli esempi avversi

I modelli di Elaborazione del Linguaggio Naturale (NLP) sono ancora vulnerabili a perturbazioni sottili a livello di caratteri o di parole che gli esseri umani spesso non notano, ma i modelli tendono a classificare erroneamente.

 #2.2.1    Livello: 1    Ruolo: D
 Verifica che i passaggi di base di normalizzazione dell'input (normalizzazione Unicode NFC, mappatura degli omografi, rimozione degli spazi bianchi) vengano eseguiti prima della tokenizzazione.
 #2.2.2    Livello: 2    Ruolo: D/V
 Verifica che il rilevamento statistico delle anomalie contrassegni gli input caratterizzati da una distanza di Levenshtein notevolmente superiore alle norme linguistiche, da token ripetuti in modo eccessivo o da distanze di embedding anomale.
 #2.2.3    Livello: 2    Ruolo: D
 Verificare che la pipeline di inferenza supporti varianti di modelli opzionali potenziati dall'addestramento avversariale–rafforzato o strati di difesa (ad es., randomizzazione, distillazione difensiva) per endpoint ad alto rischio.
 #2.2.4    Livello: 2    Ruolo: V
 Verifica che gli input avversari sospetti siano messi in quarantena e che siano registrati con payload completi (dopo l'anonimizzazione delle informazioni PII).
 #2.2.5    Livello: 3    Ruolo: D/V
 Verifica che le metriche di robustezza (tasso di successo delle suite di attacchi note) vengano tracciate nel tempo e che le regressioni attivino un blocco di rilascio.

---

### C2.3 Validazione dello schema, del tipo e della lunghezza

Attacchi basati sull'IA che presentano input malformati o troppo grandi possono causare errori di parsing, propagazione del prompt tra i campi e esaurimento delle risorse.  L'applicazione rigorosa dello schema è anche un prerequisito quando si eseguono chiamate deterministiche agli strumenti.

 #2.3.1    Livello: 1    Ruolo: D
 Verifica che ogni endpoint API o chiamata di funzione definisca uno schema di input esplicito (JSON Schema, Protobuf o equivalente multimodale) e che gli input vengano validati prima dell'assemblaggio del prompt.
 #2.3.2    Livello: 1    Ruolo: D/V
 Verifica che gli input che superano i limiti massimi di token o di byte vengano rifiutati con un errore sicuro e non vengano mai troncati silenziosamente.
 #2.3.3    Livello: 2    Ruolo: D/V
 Verifica che i controlli di tipo (ad es. intervalli numerici, valori enum, tipi MIME per immagini/audio) siano applicati sul lato server, non solo nel codice lato client.
 #2.3.4    Livello: 2    Ruolo: D
 Verifica che i validatori semantici (ad es. JSON Schema) operino in tempo costante per prevenire attacchi DoS algoritmici.
 #2.3.5    Livello: 3    Ruolo: V
 Verifica che i fallimenti di validazione siano registrati con frammenti di payload oscurati e codici di errore univoci per agevolare il triage di sicurezza.

---

### C2.4 Verifica dei contenuti e delle politiche

Gli sviluppatori dovrebbero essere in grado di rilevare prompt sintatticamente validi che richiedono contenuti vietati (come istruzioni illecite, discorsi d'odio e testi protetti da copyright) e impedire che vengano propagati.

 #2.4.1    Livello: 1    Ruolo: D
 Verifica che un classificatore di contenuti (zero-shot o finetunato) assegni un punteggio a ogni input per violenza, autolesionismo, odio, contenuti sessuali e richieste illegali, con soglie configurabili.
 #2.4.2    Livello: 1    Ruolo: D/V
 Verificare che gli input che violano le politiche ricevano rifiuti standardizzati o completamenti sicuri, in modo che non si propaghino alle chiamate LLM a valle.
 #2.4.3    Livello: 2    Ruolo: D
 Verificare che il modello di screening o l'insieme di regole venga riaddestrato o aggiornato almeno ogni trimestre, integrando i pattern di jailbreak o di elusione delle policy recentemente osservati.
 #2.4.4    Livello: 2    Ruolo: D
 Verifica che il filtraggio rispetti le politiche specifiche dell'utente (età, vincoli legali regionali) tramite regole basate su attributi risolte al momento della richiesta.
 #2.4.5    Livello: 3    Ruolo: V
 Verifica che i log di screening includano punteggi di confidenza del classificatore e tag di categoria delle politiche per la correlazione SOC e la riproduzione futura da parte del red-team.

---

### C2.5 Limitazione della velocità di input e prevenzione degli abusi

Gli sviluppatori dovrebbero prevenire abusi, esaurimento delle risorse e attacchi automatizzati contro i sistemi di IA limitando i tassi di input e rilevando schemi di utilizzo anomali.

 #2.5.1    Livello: 1    Ruolo: D/V
 Verificare che i limiti di velocità per utente, per IP e per chiave API siano applicati a tutti gli endpoint di input.
 #2.5.2    Livello: 2    Ruolo: D/V
 Verifica che i limiti di picco e sostenuti della frequenza delle richieste siano tarati per prevenire DoS e attacchi di forza bruta.
 #2.5.3    Livello: 2    Ruolo: D/V
 Verifica che schemi di utilizzo anomali (ad es. richieste a raffica, inondazione di input) scatenino blocchi automatici o escalation.
 #2.5.4    Livello: 3    Ruolo: V
 Verificare che i log di prevenzione degli abusi siano conservati e revisionati per individuare schemi di attacco emergenti.

---

### C2.6 Validazione multimodale degli input

I sistemi di IA dovrebbero includere una validazione robusta per input non testuali (immagini, audio, file) per prevenire l'iniezione, l'evasione o l'abuso delle risorse.

 #2.6.1    Livello: 1    Ruolo: D
 Verifica che tutti gli input non testuali (immagini, audio e file) siano validati per tipo, dimensione e formato prima dell'elaborazione.
 #2.6.2    Livello: 2    Ruolo: D/V
 Verifica che i file vengano scansionati per malware e payload steganografici prima dell'ingestione.
 #2.6.3    Livello: 2    Ruolo: D/V
 Verifica che gli input di immagini e audio siano controllati per perturbazioni avversariali o schemi di attacco noti.
 #2.6.4    Livello: 3    Ruolo: V
 Verifica che i fallimenti della convalida degli input multimodali siano registrati e che vengano attivati avvisi per l’indagine.

---

### C2.7 Provenienza degli input e attribuzione

I sistemi di IA dovrebbero supportare la verifica, il tracciamento degli abusi e la conformità monitorando e etichettando l'origine di tutti gli input degli utenti.

 #2.7.1    Livello: 1    Ruolo: D/V
 Verifica che tutti gli input degli utenti siano contrassegnati con metadati (ID utente, sessione, fonte, marca temporale, indirizzo IP) al momento dell’ingestione.
 #2.7.2    Livello: 2    Ruolo: D/V
 Verificare che i metadati di provenienza siano mantenuti e auditabili per tutti gli input elaborati.
 #2.7.3    Livello: 2    Ruolo: D/V
 Verifica che le fonti di input anomale o non affidabili siano contrassegnate e soggette a un controllo potenziato o al blocco.

---

### C2.8 Rilevamento adattivo delle minacce in tempo reale

Gli sviluppatori dovrebbero utilizzare sistemi avanzati di rilevamento delle minacce per l'IA che si adattano a nuovi schemi di attacco e forniscono protezione in tempo reale con corrispondenza di schemi compilata.

 #2.8.1    Livello: 1    Ruolo: D/V
 Verifica che i pattern di rilevamento delle minacce siano compilati in motori di espressioni regolari ottimizzati per un filtraggio in tempo reale ad alte prestazioni, con un impatto minimo sulla latenza.
 #2.8.2    Livello: 1    Ruolo: D/V
 Verifica che i sistemi di rilevamento delle minacce mantengano librerie di pattern separate per diverse categorie di minaccia (iniezione di prompt, contenuto dannoso, dati sensibili, comandi di sistema).
 #2.8.3    Livello: 2    Ruolo: D/V
 Verifica che il rilevamento adattivo delle minacce integri modelli di apprendimento automatico che aggiornano la sensibilità alle minacce in base alla frequenza degli attacchi e ai tassi di successo.
 #2.8.4    Livello: 2    Ruolo: D/V
 Verifica che i flussi di threat intelligence in tempo reale aggiornino automaticamente le librerie di pattern con nuove firme di attacco e IoCs (Indicatori di compromissione).
 #2.8.5    Livello: 3    Ruolo: D/V
 Verifica che i tassi di falsi positivi nel rilevamento delle minacce siano monitorati costantemente e che la specificità dei modelli di rilevamento sia regolata automaticamente per minimizzare l'interferenza con i casi d'uso legittimi.
 #2.8.6    Livello: 3    Ruolo: D/V
 Verifica che l’analisi contestuale delle minacce prenda in considerazione la fonte di input, i modelli di comportamento dell’utente e la cronologia della sessione per migliorare l’accuratezza del rilevamento.
 #2.8.7    Livello: 3    Ruolo: D/V
 Verifichi che le metriche delle prestazioni del rilevamento delle minacce siano monitorate e ottimizzate in tempo reale.

---

### C2.9 Multi-Modal Pipeline di Validazione della Sicurezza Multimodale

Gli sviluppatori dovrebbero fornire una validazione della sicurezza per testo, immagine, audio e altre modalità di input dell'IA, con tipologie specifiche di rilevamento delle minacce e di isolamento delle risorse.

 #2.9.1    Livello: 1    Ruolo: D/V
 Verifica che ogni modalità di input abbia validatori di sicurezza dedicati con schemi di minaccia documentati (testo: iniezione di prompt, immagini: steganografia, audio: attacchi allo spettrogramma) e soglie di rilevamento.
 #2.9.2    Livello: 2    Ruolo: D/V
 Verifica che gli input multimodali siano elaborati in sandbox isolati con limiti di risorse definiti (memoria, CPU, tempo di elaborazione) specifici per ciascun tipo di modalità e documentati nelle politiche di sicurezza.
 #2.9.3    Livello: 2    Ruolo: D/V
 Verifica che il rilevamento cross-modale degli attacchi identifichi attacchi coordinati che si estendono su più tipi di input (ad es., payload steganografici in immagini combinati con l'iniezione di prompt nel testo) mediante regole di correlazione e generazione di allarmi.
 #2.9.4    Livello: 3    Ruolo: D/V
 Verificare che i fallimenti della validazione multimodale attivino una registrazione dettagliata che includa tutte le modalità di input, i risultati della validazione, i punteggi di minaccia e l'analisi di correlazione con formati di log strutturati per l'integrazione SIEM.
 #2.9.5    Livello: 3    Ruolo: D/V
 Verifica che i classificatori di contenuto specifici per modalità siano aggiornati secondo i programmi documentati (almeno ogni trimestre) con nuovi schemi di minaccia, esempi avversariali e benchmark delle prestazioni mantenuti al di sopra delle soglie di base.

---

### Riferimenti

LLM01:2025 Prompt Injection – OWASP Top 10 for LLM & Generative AI Security
Generative AI's Biggest Security Flaw Is Not Easy to Fix
Many-shot jailbreaking \ Anthropic
$PDF$ OpenAI GPT-4.5 System Card
Notebook for the CheckThat Lab at CLEF 2024
Mitigate jailbreaks and prompt injections – Anthropic
Chapter 3 MITRE ATT\&CK – Adversarial Model Analysis
OWASP Top 10 for LLM Applications 2025 – WorldTech IT
OWASP Machine Learning Security Top Ten
Few words about AI Security – Jussi Metso
How To Ensure LLM Output Adheres to a JSON Schema | Modelmetry
Easily enforcing valid JSON schema following – API
AI Safety + Cybersecurity R\&D Tracker – Fairly AI
Anthropic makes 'jailbreak' advance to stop AI models producing harmful results
Pattern matching filter rules - IBM
Real-time Threat Detection

## C3 Gestione del ciclo di vita dei modelli e controllo delle modifiche

### Obiettivo di controllo

I sistemi di IA devono implementare processi di controllo delle modifiche che impediscano modifiche del modello non autorizzate o non sicure dal raggiungere l'ambiente di produzione. Questo controllo garantisce l'integrità del modello per l'intero ciclo di vita--dallo sviluppo all'implementazione fino al dismissione--il che consente una risposta rapida agli incidenti e mantiene la responsabilità per tutte le modifiche.

Obiettivo di sicurezza principale: solo i modelli autorizzati e validati raggiungono la produzione impiegando processi controllati che mantengono l'integrità, la tracciabilità e la recuperabilità.

---

### C3.1 Autorizzazione e integrità del modello

Solo modelli autorizzati con integrità verificata raggiungono gli ambienti di produzione.

 #3.1.1    Livello: 1    Ruolo: D/V
 Verifichi che tutti gli artefatti del modello (pesi, configurazioni, tokenizzatori) siano firmati crittograficamente da enti autorizzati prima della messa in produzione.
 #3.1.2    Livello: 1    Ruolo: D/V
 Verifica che l'integrità del modello sia convalidata in fase di distribuzione e che i fallimenti della verifica della firma impediscano il caricamento del modello.
 #3.1.3    Livello: 2    Ruolo: D/V
 Verifica che i registri di provenienza del modello includano l'identità dell'entità autorizzante, gli checksum dei dati di addestramento, i risultati dei test di validazione con esito pass/fail e una marca temporale di creazione.
 #3.1.4    Livello: 2    Ruolo: D/V
 Verifica che tutti gli artefatti del modello utilizzino il versionamento semantico (MAJOR.MINOR.PATCH) con criteri documentati che specificano quando ciascun componente della versione aumenta.
 #3.1.5    Livello: 2    Ruolo: V
 Verifica che il tracciamento delle dipendenze mantenga un inventario in tempo reale che consenta l'identificazione rapida di tutti i sistemi che ne fanno uso.

---

### C3.2 Validazione del modello e test

I modelli devono superare le validazioni di sicurezza e di affidabilità definite prima della messa in produzione.

 #3.2.1    Livello: 1    Ruolo: D/V
 Verificare che i modelli vengano sottoposti a test di sicurezza automatizzati che includano la convalida degli input, la sanitizzazione degli output e valutazioni di sicurezza, con soglie di accettazione/rifiuto concordate in anticipo dall'organizzazione, prima della messa in produzione.
 #3.2.2    Livello: 1    Ruolo: D/V
 Verificare che i fallimenti della validazione blocchino automaticamente la messa in produzione del modello dopo l'approvazione esplicita al bypass da parte del personale autorizzato designato in anticipo, con giustificazioni aziendali documentate.
 #3.2.3    Livello: 2    Ruolo: V
 Verifica che i risultati dei test siano firmati crittograficamente e legati in modo immutabile all'hash della versione del modello specifico che viene validata.
 #3.2.4    Livello: 2    Ruolo: D/V
 Verificare che i dispiegamenti di emergenza richiedano una valutazione documentata dei rischi per la sicurezza e l'approvazione da parte di un'autorità di sicurezza pre-designata entro i tempi concordati.

---

### C3.3 Distribuzione controllata e rollback

Le implementazioni dei modelli devono essere controllate, monitorate e reversibili.

 #3.3.1    Livello: 1    Ruolo: D
 Verifica che le distribuzioni in produzione implementino meccanismi di rollout graduale (canary deployments, blue-green deployments) con trigger di rollback automatici basati su tassi di errore concordati in anticipo, soglie di latenza o criteri di allerta di sicurezza.
 #3.3.2    Livello: 1    Ruolo: D/V
 Verifica che le funzionalità di rollback ripristinino in modo atomico lo stato completo del modello (pesi, configurazioni, dipendenze) entro le finestre temporali predefinite dall'organizzazione.
 #3.3.3    Livello: 2    Ruolo: D/V
 Verifica che i processi di distribuzione convalidino le firme crittografiche e calcolino i checksum di integrità prima dell'attivazione del modello, facendo fallire la distribuzione in caso di qualsiasi incongruenza.
 #3.3.4    Livello: 2    Ruolo: D/V
 Verifica che le capacità di spegnimento di emergenza del modello possano disabilitare gli endpoint del modello entro i tempi di risposta predefiniti tramite interruttori automatici o interruttori manuali di spegnimento.
 #3.3.5    Livello: 2    Ruolo: V
 Verificare che gli artefatti di rollback (versioni precedenti del modello, configurazioni, dipendenze) siano conservati in conformità alle politiche organizzative, con archiviazione immutabile per la gestione degli incidenti.

---

### C3.4 Responsabilità delle modifiche e verifica

Tutte le modifiche al ciclo di vita del modello devono essere tracciabili e auditabili.

 #3.4.1    Livello: 1    Ruolo: V
 Verifica che tutte le modifiche al modello (dispiegamento, configurazione, ritiro) generino registri di audit immutabili che includano una marca temporale, l'identità dell'attore autenticata, il tipo di modifica e gli stati prima/dopo.
 #3.4.2    Livello: 2    Ruolo: D/V
 Verifica che l'accesso al registro di audit richieda l'autorizzazione appropriata e che tutti i tentativi di accesso siano registrati con l'identità dell'utente e con una marca temporale.
 #3.4.3    Livello: 2    Ruolo: D/V
 Verificare che i modelli di prompt e i messaggi di sistema siano sottoposti a controllo di versione nei repository Git, con revisione del codice obbligatoria e approvazione da parte dei revisori designati prima della messa in produzione.
 #3.4.4    Livello: 2    Ruolo: V
 Verificare che i registri di audit contengano dettagli sufficienti (hash del modello, istantanee di configurazione, versioni delle dipendenze) per consentire una ricostruzione completa dello stato del modello per qualsiasi marca temporale entro il periodo di conservazione.

---

### C3.5 Pratiche di sviluppo sicuro

I processi di sviluppo e addestramento del modello devono seguire pratiche sicure per prevenire la compromissione.

 #3.5.1    Livello: 1    Ruolo: D
 Verificare che gli ambienti di sviluppo, test e produzione dei modelli siano separati fisicamente o logicamente. Non hanno infrastrutture condivise, controlli di accesso distinti e archivi di dati isolati.
 #3.5.2    Livello: 1    Ruolo: D
 Verificare che l'addestramento del modello e la messa a punto avvengano in ambienti isolati con accesso di rete controllato.
 #3.5.3    Livello: 1    Ruolo: D/V
 Verificare che le fonti dei dati di addestramento siano verificate tramite controlli di integrità e provengano da fonti affidabili con una catena di custodia documentata prima dell'uso nello sviluppo del modello.
 #3.5.4    Livello: 2    Ruolo: D
 Verifica che gli artefatti di sviluppo del modello (iperparametri, script di addestramento, file di configurazione) siano archiviati nel controllo delle versioni e richiedano l'approvazione tramite revisione tra pari prima dell'uso nell'addestramento.

---

### C3.6 Ritiro del modello e messa fuori servizio

I modelli devono essere ritirati in modo sicuro quando non sono più necessari o quando si identificano problemi di sicurezza.

 #3.6.1    Livello: 1    Ruolo: D
 Verificare che i processi di messa fuori servizio del modello eseguano automaticamente la scansione dei grafi di dipendenza, identifichino tutti i sistemi che ne fanno uso e forniscano i periodi di preavviso concordati in anticipo prima della messa fuori servizio.
 #3.6.2    Livello: 1    Ruolo: D/V
 Verificare che gli artefatti dei modelli ritirati siano cancellati in modo sicuro mediante cancellazione crittografica o sovrascrittura a più passaggi, in conformità alle politiche di conservazione dei dati documentate, con certificati di distruzione verificati.
 #3.6.3    Livello: 2    Ruolo: V
 Verificare che gli eventi di ritiro del modello siano registrati con marca temporale e identità dell'attore, e che le firme del modello siano revocate per impedirne il riutilizzo.
 #3.6.4    Livello: 2    Ruolo: D/V
 Verificare che la messa fuori servizio d'emergenza del modello possa disabilitare l'accesso al modello entro i tempi di risposta di emergenza prestabiliti tramite interruttori di spegnimento automatici se vengono rilevate vulnerabilità di sicurezza critiche.

---

### Riferimenti

MLOps Principles
Securing AI/ML Ops – Cisco.com
Audit logs security: cryptographically signed tamper-proof logs
Machine Learning Model Versioning: Top Tools & Best Practices
AI Hygiene Starts with Models and Data Loaders – SEI Blog
How to handle versioning and rollback of a deployed ML model?
Reinforcement fine-tuning – OpenAI API
Auditing Machine Learning models: Governance, Data Security and …
Adversarial Training to Improve Model Robustness
What is AI adversarial robustness? – IBM Research
Exploring Data Provenance: Ensuring Data Integrity and Authenticity
MITRE ATLAS
AWS Prescriptive Guidance – Best practices for retiring applications …

## C4 Sicurezza dell'infrastruttura, configurazione e dispiegamento

### Obiettivo di controllo

L'infrastruttura di IA deve essere messa in sicurezza contro l'elevazione dei privilegi, la manomissione della catena di fornitura e i movimenti laterali, tramite una configurazione sicura, isolamento in tempo di esecuzione, pipeline di distribuzione affidabili e monitoraggio esaustivo.

Solo componenti e configurazioni di infrastruttura autorizzati e convalidate raggiungono la produzione tramite processi controllati che mantengono la sicurezza, l'integrità e l'auditabilità.

Obiettivo di sicurezza principale: Solo componenti infrastrutturali firmati digitalmente e sottoposti a scansione delle vulnerabilità raggiungono l'ambiente di produzione attraverso pipeline di convalida automatizzate che fanno rispettare le politiche di sicurezza e mantengono tracce di audit immutabili.

---

### C4.1 Isolamento dell'ambiente di esecuzione

Prevenire l'evasione dai contenitori e l'aumento dei privilegi mediante meccanismi di isolamento a livello del kernel e controlli di accesso obbligatori.

 #4.1.1    Livello: 1    Ruolo: D/V
 Verifica che tutti i contenitori di IA rimuovano tutte le capacità Linux, ad eccezione di CAP_SETUID, CAP_SETGID e delle capacità esplicitamente richieste documentate nelle baseline di sicurezza.
 #4.1.2    Livello: 1    Ruolo: D/V
 Verifica che i profili seccomp blocchino tutte le chiamate di sistema, ad eccezione di quelle presenti nelle liste bianche già approvate, con violazioni che terminano il contenitore e generano avvisi di sicurezza.
 #4.1.3    Livello: 2    Ruolo: D/V
 Verifica che i carichi di lavoro di IA funzionino con root del filesystem in sola lettura, tmpfs per dati temporanei e volumi nominati per dati persistenti, con opzioni di montaggio noexec imposte.
 #4.1.4    Livello: 2    Ruolo: D/V
 Verificare che il monitoraggio in tempo di esecuzione basato su eBPF (Falco, Tetragon o equivalente) rilevi tentativi di elevazione dei privilegi e termini automaticamente i processi non autorizzati entro i tempi di risposta stabiliti dall'organizzazione.
 #4.1.5    Livello: 3    Ruolo: D/V
 Verificare che i carichi di lavoro IA ad alto rischio vengano eseguiti in ambienti hardware-isolati (Intel TXT, AMD SVM o nodi bare-metal dedicati) con verifica di attestazione.

---

### C4.2 Pipelines di build e deployment sicure

Garantire l'integrità crittografica e la sicurezza della catena di fornitura attraverso build riproducibili e artefatti firmati.

 #4.2.1    Livello: 1    Ruolo: D/V
 Verifica che l'infrastruttura come codice (IaC) venga scansionata con strumenti (tfsec, Checkov o Terrascan) ad ogni commit, bloccando le fusioni con riscontri di gravità CRITICAL o HIGH.
 #4.2.2    Livello: 1    Ruolo: D/V
 Verifica che i build dei contenitori siano riproducibili con hash SHA256 identici tra i build e genera attestazioni di provenienza SLSA Livello 3 firmate con Sigstore.
 #4.2.3    Livello: 2    Ruolo: D/V
 Verifica che le immagini container includano SBOM CycloneDX o SPDX e siano firmate con Cosign prima del push nel registro, e che le immagini non firmate vengano rifiutate al deployment.
 #4.2.4    Livello: 2    Ruolo: D/V
 Verifica che le pipeline CI/CD utilizzino token OIDC provenienti da HashiCorp Vault, AWS IAM Roles o Azure Managed Identity, con durate non superiori ai limiti della politica di sicurezza dell'organizzazione.
 #4.2.5    Livello: 2    Ruolo: D/V
 Verificare che le firme Cosign e la provenienza SLSA siano verificate durante il processo di distribuzione prima dell'esecuzione del contenitore e che gli errori di verifica causino il fallimento della distribuzione.
 #4.2.6    Livello: 2    Ruolo: D/V
 Verifica che gli ambienti di build funzionino in contenitori effimeri o in macchine virtuali senza archiviazione persistente e con isolamento di rete dalle VPC di produzione.

---

### C4.3 Sicurezza di rete e controllo degli accessi

Implementa una rete zero-trust con politiche di negazione predefinite e comunicazioni criptate.

 #4.3.1    Livello: 1    Ruolo: D/V
 Verifica che Kubernetes NetworkPolicies o equivalenti implementino un rifiuto predefinito per ingresso e uscita, con regole esplicite di permesso per le porte richieste (443, 8080, ecc.).
 #4.3.2    Livello: 1    Ruolo: D/V
 Verifichi che SSH (porta 22), RDP (porta 3389) e gli endpoint di metadati nel cloud (169.254.169.254) siano bloccati o richiedano un'autenticazione basata su certificato.
 #4.3.3    Livello: 2    Ruolo: D/V
 Verificare che il traffico in uscita sia filtrato tramite proxy HTTP/HTTPS (Squid, Istio o gateway NAT nel cloud) con liste bianche dei domini e che le richieste bloccate vengano registrate.
 #4.3.4    Livello: 2    Ruolo: D/V
 Verifica che la comunicazione tra i servizi utilizzi TLS mutuo con certificati ruotati secondo la politica organizzativa e che la validazione dei certificati sia attiva (nessuna flag skip-verify).
 #4.3.5    Livello: 2    Ruolo: D/V
 Verifica che l'infrastruttura di IA operi in VPCs e VNets dedicati, con nessun accesso diretto a Internet, e comunichi esclusivamente tramite gateway NAT o host bastione.

---

### C4.4 Segreti e Gestione delle Chiavi Crittografiche

Proteggi le credenziali tramite archiviazione basata su hardware e rotazione automatizzata delle credenziali con accesso zero-trust.

 #4.4.1    Livello: 1    Ruolo: D/V
 Verifica che i segreti siano archiviati in HashiCorp Vault, AWS Secrets Manager, Azure Key Vault o Google Secret Manager con cifratura a riposo tramite AES-256.
 #4.4.2    Livello: 1    Ruolo: D/V
 Verificare che le chiavi crittografiche siano generate in HSM FIPS 140-2 Livello 2 (AWS CloudHSM, Azure Dedicated HSM) con rotazione delle chiavi secondo la politica crittografica aziendale.
 #4.4.3    Livello: 2    Ruolo: D/V
 Verifica che la rotazione dei segreti sia automatizzata con distribuzione senza tempi di inattività e che la rotazione sia immediata, attivata da cambiamenti del personale o incidenti di sicurezza.
 #4.4.4    Livello: 2    Ruolo: D/V
 Verifica che le immagini dei contenitori siano sottoposte a scansione con strumenti (GitLeaks, TruffleHog o detect-secrets) che blocchino le build contenenti chiavi API, password o certificati.
 #4.4.5    Livello: 2    Ruolo: D/V
 Verificare che l'accesso ai segreti di produzione richieda MFA con token hardware (YubiKey, FIDO2) e sia registrato in log di audit immutabili che includano l'identità dell'utente e la data e ora.
 #4.4.6    Livello: 2    Ruolo: D/V
 Verifichi che i segreti siano iniettati tramite i segreti di Kubernetes, volumi montati o contenitori di inizializzazione, e si assicuri che i segreti non siano mai incorporati nelle variabili d'ambiente o nelle immagini.

---

### C4.5 IA sandboxing dei carichi di lavoro e validazione

Isolare i modelli di IA non affidabili in sandbox sicuri con un'analisi comportamentale completa.

 #4.5.1    Livello: 1    Ruolo: D/V
 Verifica che i modelli AI esterni vengano eseguiti in gVisor, microVM (come Firecracker, CrossVM) o contenitori Docker con le opzioni --security-opt=no-new-privileges e --read-only.
 #4.5.2    Livello: 1    Ruolo: D/V
 Verifica che gli ambienti sandbox non abbiano alcuna connettività di rete (--network=none) o abbiano solo l'accesso a localhost, con tutte le richieste esterne bloccate dalle regole iptables.
 #4.5.3    Livello: 2    Ruolo: D/V
 Verificare che la validazione del modello di IA includa test automatizzati del Red Team con copertura di test definita dall'organizzazione e analisi comportamentale per la rilevazione di backdoor.
 #4.5.4    Livello: 2    Ruolo: D/V
 Verifica che prima che un modello di IA venga promosso in produzione, i suoi risultati della sandbox siano firmati digitalmente da personale di sicurezza autorizzato e registrati in registri di audit immutabili.
 #4.5.5    Livello: 2    Ruolo: D/V
 Verifica che gli ambienti sandbox siano distrutti e ricreati da immagini golden tra le valutazioni, con una pulizia completa del filesystem e della memoria.

---

### C4.6 Monitoraggio della sicurezza dell'infrastruttura

Scansiona e monitora continuamente l'infrastruttura con rimedi automatizzati e avvisi in tempo reale.

 #4.6.1    Livello: 1    Ruolo: D/V
 Verificare che le immagini del container vengano scansionate secondo i programmi organizzativi, con vulnerabilità CRITICHE che blocchino la distribuzione in base alle soglie di rischio organizzative.
 #4.6.2    Livello: 1    Ruolo: D/V
 Verificare che l'infrastruttura rispetti CIS Benchmarks o i controlli NIST 800-53, con soglie di conformità definite dall'organizzazione e rimedi automatizzati per le verifiche fallite.
 #4.6.3    Livello: 2    Ruolo: D/V
 Verificare che le vulnerabilità ad alta gravità siano patchate secondo le tempistiche della gestione del rischio organizzativo, con procedure di emergenza per CVE attivamente sfruttate.
 #4.6.4    Livello: 2    Ruolo: V
 Verifica che gli avvisi di sicurezza si integrino con le piattaforme SIEM (Splunk, Elastic o Sentinel) utilizzando formati CEF o STIX/TAXII con arricchimento automatico.
 #4.6.5    Livello: 3    Ruolo: V
 Verifica che le metriche dell'infrastruttura siano esportate nei sistemi di monitoraggio (Prometheus, DataDog) con cruscotti SLA e reporting esecutivo.
 #4.6.6    Livello: 2    Ruolo: D/V
 Verificare che la deviazione di configurazione venga rilevata utilizzando strumenti (Chef InSpec, AWS Config) in base ai requisiti di monitoraggio dell'organizzazione, con rollback automatico per modifiche non autorizzate.

---

### C4.7 Gestione delle risorse dell'infrastruttura di IA

Prevenire gli attacchi di esaurimento delle risorse e garantire una ripartizione equa delle risorse tramite quote e monitoraggio.

 #4.7.1    Livello: 1    Ruolo: D/V
 Verifica che l'utilizzo di GPU/TPU sia monitorato con allarmi attivati a soglie definite dall'organizzazione e che il ridimensionamento automatico o il bilanciamento del carico siano attivati in base alle politiche di gestione della capacità.
 #4.7.2    Livello: 1    Ruolo: D/V
 Verifica che le metriche dei carichi di lavoro IA (latenza di inferenza, throughput, tassi di errore) siano raccolte in conformità ai requisiti di monitoraggio dell'organizzazione e siano correlate all'utilizzo dell'infrastruttura.
 #4.7.3    Livello: 2    Ruolo: D/V
 Verificare che le ResourceQuotas di Kubernetes o equivalenti limitino i carichi di lavoro individuali in base alle politiche di allocazione delle risorse dell'organizzazione, con limiti rigidi applicati.
 #4.7.4    Livello: 2    Ruolo: V
 Verificare che il monitoraggio dei costi tracci la spesa per carico di lavoro/tenant con avvisi basati sulle soglie di budget organizzativo e controlli automatizzati per i superamenti del budget.
 #4.7.5    Livello: 3    Ruolo: V
 Verifica che la pianificazione della capacità utilizzi dati storici con periodi di previsione definiti dall'organizzazione e che l'allocazione automatizzata delle risorse sia basata sui modelli di domanda.
 #4.7.6    Livello: 2    Ruolo: D/V
 Verificare che l'esaurimento delle risorse faccia scattare gli interruttori di protezione del circuito in conformità ai requisiti di risposta dell'organizzazione, tra cui la limitazione del tasso basata su politiche di capacità e l'isolamento dei carichi di lavoro.

---

### C4.8 Separazione degli ambienti e controlli di promozione

Imporre confini rigorosi tra gli ambienti con cancelli di promozione automatizzati e validazione della sicurezza.

 #4.8.1    Livello: 1    Ruolo: D/V
 Verificare che gli ambienti di sviluppo, test e produzione operino in VPCs/VNets separati, senza alcuna condivisione di ruoli IAM, gruppi di sicurezza o connettività di rete.
 #4.8.2    Livello: 1    Ruolo: D/V
 Verificare che la promozione dell'ambiente richieda l'approvazione da parte del personale autorizzato definito dall'organizzazione, con firme crittografiche e tracce di audit immutabili.
 #4.8.3    Livello: 2    Ruolo: D/V
 Verifica che gli ambienti di produzione blocchino l'accesso SSH, disabilitino gli endpoint di debug e richiedano richieste di modifica con requisiti di preavviso organizzativo, salvo le emergenze.
 #4.8.4    Livello: 2    Ruolo: D/V
 Verificare che le modifiche all'infrastruttura come codice (IaC) richiedano una revisione tra pari con test automatici e scansione di sicurezza prima della fusione nel ramo principale.
 #4.8.5    Livello: 2    Ruolo: D/V
 Verificare che i dati non di produzione siano anonimizzati secondo i requisiti di privacy organizzativi, la generazione di dati sintetici o il mascheramento completo dei dati con la rimozione di PII verificata.
 #4.8.6    Livello: 2    Ruolo: D/V
 Verificare che i gate di promozione includano test di sicurezza automatizzati (SAST, DAST, scansione dei container) con la condizione che non vi siano vulnerabilità critiche per l'approvazione.

---

### C4.9 Infrastruttura Backup e Ripristino

Garantire la resilienza dell'infrastruttura mediante backup automatizzati, procedure di ripristino testate e capacità di disaster recovery.

 #4.9.1    Livello: 1    Ruolo: D/V
 Verificare che le configurazioni dell'infrastruttura siano sottoposte a backup secondo i piani di backup organizzativi, in regioni geograficamente separate, con l'implementazione della strategia di backup 3-2-1.
 #4.9.2    Livello: 2    Ruolo: D/V
 Verificare che i sistemi di backup operino in reti isolate con credenziali separate e archiviazione offline isolata per la protezione contro il ransomware.
 #4.9.3    Livello: 2    Ruolo: V
 Verificare che le procedure di ripristino siano testate e validate tramite test automatizzati secondo i programmi organizzativi, con obiettivi RTO e RPO che soddisfino i requisiti dell'organizzazione.
 #4.9.4    Livello: 3    Ruolo: V
 Verifica che il ripristino di emergenza includa runbook specifici per IA con il ripristino dei pesi del modello, la ricostruzione del cluster GPU e la mappatura delle dipendenze dei servizi.

---

### C4.10 Conformità e governance dell'infrastruttura

Mantenere la conformità normativa attraverso valutazioni continue, documentazione e controlli automatizzati.

 #4.10.1    Livello: 2    Ruolo: D/V
 Verificare che la conformità dell'infrastruttura sia valutata in base ai piani organizzativi rispetto ai controlli SOC 2, ISO 27001 o FedRAMP, con raccolta automatizzata delle evidenze.
 #4.10.2    Livello: 2    Ruolo: V
 Verifica che la documentazione infrastrutturale includa diagrammi di rete, mappe di flusso dei dati e modelli di minaccia aggiornati in base ai requisiti di gestione del cambiamento organizzativo.
 #4.10.3    Livello: 3    Ruolo: D/V
 Verificare che le modifiche all'infrastruttura siano sottoposte a una valutazione automatica dell'impatto sulla conformità, con flussi di approvazione regolamentare per modifiche ad alto rischio.

---

### C4.11 Sicurezza dell'hardware dell'IA

Garantire la sicurezza dei componenti hardware specifici per l'IA, inclusi GPU, TPU e acceleratori di intelligenza artificiale specializzati.

 #4.11.1    Livello: 2    Ruolo: D/V
 Verificare che il firmware dell'acceleratore AI (BIOS della GPU, firmware TPU) sia verificato con firme crittografiche e aggiornato in conformità alle tempistiche di gestione delle patch dell'organizzazione.
 #4.11.2    Livello: 2    Ruolo: D/V
 Verificare che, prima dell'esecuzione del carico di lavoro, l'integrità dell'acceleratore AI sia convalidata tramite attestazione hardware utilizzando TPM 2.0, Intel TXT o AMD SVM.
 #4.11.3    Livello: 2    Ruolo: D/V
 Verifica che la memoria GPU sia isolata tra i carichi di lavoro utilizzando SR-IOV, MIG (Multi-Instance GPU) o partizionamento hardware equivalente con sanificazione della memoria tra i lavori.
 #4.11.4    Livello: 3    Ruolo: V
 Verifica che la catena di fornitura dell'hardware per l'IA includa la verifica della provenienza con certificati del produttore e la convalida dell'imballaggio a prova di manomissione.
 #4.11.5    Livello: 3    Ruolo: D/V
 Verifichi che i moduli di sicurezza hardware (HSM) proteggano i pesi del modello di IA e le chiavi crittografiche con certificazione FIPS 140-2 livello 3 o Common Criteria EAL4+.

---

### C4.12 Edge & Infrastruttura IA Distribuita

Implementazioni sicure di IA distribuita, includendo edge computing, apprendimento federato e architetture multi-sito.

 #4.12.1    Livello: 2    Ruolo: D/V
 Verifica che i dispositivi edge AI si autentichino presso l'infrastruttura centrale utilizzando TLS mutuo (mTLS) con certificati dei dispositivi ruotati secondo la politica di gestione dei certificati dell'organizzazione.
 #4.12.2    Livello: 2    Ruolo: D/V
 Verificare che i dispositivi edge implementino l'avvio sicuro con firme verificate e protezione contro il rollback che prevenga gli attacchi di downgrade del firmware.
 #4.12.3    Livello: 3    Ruolo: D/V
 Verifica che il coordinamento distribuito dell'IA utilizzi algoritmi di consenso tolleranti ai fallimenti bizantini con validazione dei partecipanti e rilevamento di nodi malevoli.
 #4.12.4    Livello: 3    Ruolo: D/V
 Verifichi che la comunicazione edge-to-cloud includa la limitazione della larghezza di banda, la compressione dei dati e le capacità di operare offline con archiviazione locale sicura.

---

### C4.13 Sicurezza dell'infrastruttura multi-cloud e ibrida

Proteggere i carichi di lavoro di IA tra più fornitori di cloud e implementazioni ibride cloud-on-premises.

 #4.13.1    Livello: 2    Ruolo: D/V
 Verificare che le implementazioni di IA multi-cloud utilizzino una federazione di identità indipendente dal cloud (OIDC, SAML) con gestione centralizzata delle politiche tra i fornitori.
 #4.13.2    Livello: 2    Ruolo: D/V
 Verificare che il trasferimento di dati tra cloud utilizzi la crittografia end-to-end con chiavi gestite dal cliente e controlli di residenza dei dati applicati per giurisdizione.
 #4.13.3    Livello: 2    Ruolo: D/V
 Verificare che i carichi di lavoro IA nel cloud ibrido implementino politiche di sicurezza coerenti tra ambienti in locale e cloud, con monitoraggio e allerta unificati.
 #4.13.4    Livello: 3    Ruolo: V
 Verifichi che la prevenzione del lock-in del fornitore cloud includa infrastruttura come codice portatile, API standardizzate e capacità di esportazione dei dati con strumenti di conversione dei formati.
 #4.13.5    Livello: 3    Ruolo: V
 Verifica che l'ottimizzazione dei costi multi-cloud includa controlli di sicurezza che prevengano lo spreco di risorse, nonché i costi di trasferimento dati tra i cloud non autorizzati.

---

### C4.14 Automazione dell'infrastruttura e sicurezza GitOps

Pipeline di automazione dell'infrastruttura sicura e flussi di lavoro GitOps per la gestione dell'infrastruttura AI.

 #4.14.1    Livello: 2    Ruolo: D/V
 Verifica che i repository GitOps richiedano commit firmati con chiavi GPG e regole di protezione dei rami che impediscono push diretti ai rami principali.
 #4.14.2    Livello: 2    Ruolo: D/V
 Verificare che l'automazione dell'infrastruttura includa il rilevamento delle deviazioni con intervento correttivo automatico e le capacità di rollback attivate in base ai requisiti di risposta dell'organizzazione per modifiche non autorizzate.
 #4.14.3    Livello: 2    Ruolo: D/V
 Verifica che l'automazione dell'approvvigionamento dell'infrastruttura includa la validazione delle policy di sicurezza con blocco della distribuzione per configurazioni non conformi.
 #4.14.4    Livello: 2    Ruolo: D/V
 Verifica che i segreti dell'automazione dell'infrastruttura siano gestiti tramite operatori di segreti esterni (External Secrets Operator, Bank-Vaults) con rotazione automatica.
 #4.14.5    Livello: 3    Ruolo: V
 Verifica che l'infrastruttura auto-rigenerante includa la correlazione degli eventi di sicurezza con la risposta automatizzata agli incidenti e i flussi di lavoro di notifica ai portatori di interesse.

---

### C4.15 Sicurezza delle infrastrutture resistenti ai computer quantistici

Prepara l'infrastruttura di IA per le minacce legate al calcolo quantistico mediante crittografia post-quantum e protocolli sicuri quantistici.

 #4.15.1    Livello: 3    Ruolo: D/V
 Verificare che l'infrastruttura IA implementi gli algoritmi crittografici post-quantistici approvati da NIST (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) per lo scambio di chiavi e le firme digitali.
 #4.15.2    Livello: 3    Ruolo: D/V
 Verifica che i sistemi di distribuzione di chiavi quantistiche (QKD) siano implementati per comunicazioni ad alta sicurezza basate sull'Intelligenza Artificiale, con protocolli di gestione delle chiavi sicuri contro gli attacchi quantistici.
 #4.15.3    Livello: 3    Ruolo: D/V
 Verificare che i framework di agilità crittografica consentano una migrazione rapida verso nuovi algoritmi post-quantistici con rotazione automatizzata di certificati e chiavi.
 #4.15.4    Livello: 3    Ruolo: V
 Verificare che la modellazione delle minacce quantistiche valuti la vulnerabilità dell'infrastruttura IA agli attacchi quantistici, con cronologie di migrazione documentate e valutazioni dei rischi.
 #4.15.5    Livello: 3    Ruolo: D/V
 Verifica che i sistemi crittografici ibridi classico-quantistici forniscano difesa-in-profondità durante il periodo di transizione quantistica con monitoraggio delle prestazioni.

---

### C4.16 Calcolo confidenziale & ambienti sicuri

Proteggere i carichi di lavoro dell'IA e i pesi del modello usando ambienti di esecuzione fidati basati su hardware e tecnologie di calcolo confidenziale.

 #4.16.1    Livello: 3    Ruolo: D/V
 Verifichi che i modelli di IA sensibili vengano eseguiti all'interno di enclave Intel SGX, AMD SEV-SNP o ARM TrustZone, con memoria cifrata e verifica dell'attestazione.
 #4.16.2    Livello: 3    Ruolo: D/V
 Verifica che i contenitori confidenziali (Kata Containers, gVisor con calcolo confidenziale) isolino i carichi di lavoro dell'IA con cifratura della memoria supportata dall'hardware.
 #4.16.3    Livello: 3    Ruolo: D/V
 Verifica l'integrità dell'enclave tramite attestazione remota prima di caricare i modelli di IA, fornendo una prova crittografica dell'autenticità dell'ambiente di esecuzione.
 #4.16.4    Livello: 3    Ruolo: D/V
 Verifica che i servizi di inferenza AI confidenziali impediscano l'estrazione del modello mediante calcolo crittografato con pesi del modello sigillati ed esecuzione protetta.
 #4.16.5    Livello: 3    Ruolo: D/V
 Verifica che l'orchestrazione dell'ambiente di esecuzione affidabile gestisca il ciclo di vita dell'enclave sicura con attestazione remota e canali di comunicazione cifrati.
 #4.16.6    Livello: 3    Ruolo: D/V
 Verifica che il calcolo sicuro multiparte (SMPC) consenta un addestramento collaborativo dell'IA senza esporre i set di dati individuali o i parametri del modello.

---

### C4.17 Infrastruttura Zero-Knowledge

Implementa sistemi di prove a conoscenza zero per la verifica e l'autenticazione dell'IA che preservano la privacy, senza rivelare informazioni sensibili.

 #4.17.1    Livello: 3    Ruolo: D/V
 Verifica che le prove a conoscenza nulla (ZK-SNARKs, ZK-STARKs) verifichino l'integrità del modello di IA e la provenienza dell'addestramento senza esporre i pesi del modello o i dati di addestramento.
 #4.17.2    Livello: 3    Ruolo: D/V
 Verifica che i sistemi di autenticazione basati su ZK consentano una verifica dell'utente che preservi la privacy nei servizi di IA senza rivelare informazioni relative all'identità.
 #4.17.3    Livello: 3    Ruolo: D/V
 Verifica che i protocolli di intersezione di insiemi privata (PSI) consentano l'abbinamento sicuro dei dati per l'IA federata senza esporre set di dati individuali.
 #4.17.4    Livello: 3    Ruolo: D/V
 Verifica che i sistemi di apprendimento automatico a conoscenza nulla (ZKML) consentano inferenze AI verificabili con una prova crittografica della correttezza del calcolo.
 #4.17.5    Livello: 3    Ruolo: D/V
 Verifica che i rollup ZK offrano un'elaborazione scalabile delle transazioni di IA che preservi la privacy, con verifica in batch e ridotto carico computazionale.

---

### C4.18 Prevenzione degli attacchi a canali laterali

Proteggere l'infrastruttura IA dagli attacchi a canale laterale basati su temporizzazione, consumo di energia, elettromagnetici e cache che potrebbero rivelare informazioni sensibili.

 #4.18.1    Livello: 3    Ruolo: D/V
 Verifica che il tempo di inferenza dell'IA sia normalizzato utilizzando algoritmi a tempo costante e padding per prevenire attacchi di estrazione del modello basati sul tempo.
 #4.18.2    Livello: 3    Ruolo: D/V
 Verifica che la protezione contro l’analisi del consumo di potenza includa l’iniezione di rumore, il filtraggio della linea di alimentazione e schemi di esecuzione casualizzati per l’hardware di IA.
 #4.18.3    Livello: 3    Ruolo: D/V
 Verifica che la mitigazione basata sulla cache dei canali laterali utilizzi la partizione della cache, la randomizzazione e le istruzioni di flush per prevenire la perdita di informazioni.
 #4.18.4    Livello: 3    Ruolo: D/V
 Verifica che la protezione dalle emanazioni elettromagnetiche includa schermatura elettromagnetica, filtraggio del segnale e elaborazione casualizzata per prevenire attacchi di tipo TEMPEST.
 #4.18.5    Livello: 3    Ruolo: D/V
 Verifica che le difese contro i canali laterali microarchitetturali includano controlli sull'esecuzione speculativa e offuscamento dei pattern di accesso alla memoria.

---

### C4.19 Sicurezza dell'hardware neuromorfico e specializzato per l'IA

Garantire la sicurezza delle architetture hardware emergenti per l'IA, tra cui chip neuromorfici, FPGA, ASIC personalizzati e sistemi di calcolo ottico.

 #4.19.1    Livello: 3    Ruolo: D/V
 Verificare che la sicurezza del chip neuromorfico includa crittografia delle sequenze di spike, protezione dei pesi sinaptici e validazione delle regole di apprendimento basate su hardware.
 #4.19.2    Livello: 3    Ruolo: D/V
 Verifica che gli acceleratori di IA basati su FPGA implementino la crittografia del bitstream, meccanismi anti-manomissione e caricamento sicuro della configurazione con aggiornamenti autenticati.
 #4.19.3    Livello: 3    Ruolo: D/V
 Verificare che la sicurezza di un ASIC personalizzato includa processori di sicurezza on-chip, radice di fiducia hardware e memorizzazione sicura delle chiavi con rilevamento di manomissione.
 #4.19.4    Livello: 3    Ruolo: D/V
 Verifica che i sistemi di calcolo ottico implementino cifratura ottica resistente ai computer quantistici, commutazione fotonica sicura e elaborazione sicura del segnale ottico.
 #4.19.5    Livello: 3    Ruolo: D/V
 Verificare che i chip AI ibridi analogico-digitali includano calcolo analogico sicuro, archiviazione protetta dei pesi e conversione analogico-digitale autenticata.

---

### C4.20 Infrastruttura di calcolo che preserva la privacy

Implementare controlli infrastrutturali per la computazione a tutela della privacy al fine di proteggere i dati sensibili durante l'elaborazione e l'analisi basate sull'IA.

 #4.20.1    Livello: 3    Ruolo: D/V
 Verificare che l'infrastruttura di crittografia omomorfica permetta l'elaborazione crittografata su carichi di lavoro sensibili di IA, con verifica dell'integrità crittografica e monitoraggio delle prestazioni.
 #4.20.2    Livello: 3    Ruolo: D/V
 Verifichi che i sistemi di recupero privato delle informazioni consentano interrogazioni al database senza rivelare gli schemi delle query mediante protezione crittografica degli schemi di accesso.
 #4.20.3    Livello: 3    Ruolo: D/V
 Verifica che i protocolli di calcolo multiparte sicuro consentano inferenze IA che preservano la privacy senza esporre input individuali o calcoli intermedi.
 #4.20.4    Livello: 3    Ruolo: D/V
 Verifica che la gestione delle chiavi orientata alla privacy includa la generazione di chiavi distribuita, la crittografia a soglia e la rotazione sicura delle chiavi con protezione basata su hardware.
 #4.20.5    Livello: 3    Ruolo: D/V
 Verifica che le prestazioni computazionali che preservano la privacy siano ottimizzate tramite l'elaborazione in batch, la memorizzazione nella cache e l'accelerazione hardware, mantenendo le garanzie di sicurezza crittografiche.

---

### C4.15 Framework dell'agente Integrazione Cloud, Sicurezza e Distribuzione Ibrida

Controlli di sicurezza per framework di agenti integrati nel cloud con architetture ibride on-premises/cloud.

 #4.15.1    Livello: 1    Ruolo: D/V
 Verifica che l'integrazione dello storage cloud utilizzi la crittografia end-to-end con gestione delle chiavi controllata dall'agente.
 #4.15.2    Livello: 2    Ruolo: D/V
 Verifica che i limiti di sicurezza della distribuzione ibrida siano chiaramente definiti con canali di comunicazione criptati.
 #4.15.3    Livello: 2    Ruolo: D/V
 Verifica che l'accesso alle risorse cloud includa una verifica Zero-Trust con autenticazione continua.
 #4.15.4    Livello: 3    Ruolo: D/V
 Verifica che i requisiti di localizzazione dei dati siano applicati mediante attestazione crittografica delle sedi di archiviazione.
 #4.15.5    Livello: 3    Ruolo: D/V
 Verifica che le valutazioni di sicurezza del fornitore di servizi cloud includano la modellazione delle minacce specifica per l'agente e la valutazione del rischio.

---

### Riferimenti

NIST Cybersecurity Framework 2.0
CIS Controls v8
OWASP Container Security Verification Standard
Kubernetes Security Best Practices
SLSA Supply Chain Security Framework
NIST SP 800-190: Application Container Security Guide
Cloud Security Alliance: Cloud Controls Matrix
ENISA: Secure Infrastructure Design
NIST SP 800-53: Security Controls for Federal Information Systems
ISO 27001:2022 Information Security Management
NIST AI Risk Management Framework
CIS Kubernetes Benchmark
FIPS 140-2 Security Requirements
NIST SP 800-207: Zero Trust Architecture
IEEE 2857: Privacy Engineering for AI Systems
NIST SP 800-161: Cybersecurity Supply Chain Risk Management
NIST Post-Quantum Cryptography Standards
Intel SGX Developer Guide
AMD SEV-SNP White Paper
ARM TrustZone Technology
ZK-SNARKs: A Gentle Introduction
NIST SP 800-57: Cryptographic Key Management
Side-Channel Attack Countermeasures
Neuromorphic Computing Security Challenges
FPGA Security: Fundamentals, Evaluation, and Countermeasures
Microsoft SEAL: Homomorphic Encryption Library
HElib: Homomorphic Encryption Library
PALISADE Lattice Cryptography Library
Differential Privacy: A Survey of Results
Secure Aggregation for Federated Learning
Private Information Retrieval: Concepts and Constructions

## C5 Controllo degli Accessi e Identità per Componenti e Utenti IA

### Obiettivo di controllo

Un controllo di accesso efficace per i sistemi di IA richiede una gestione robusta delle identità, un'autorizzazione basata sul contesto e un'attuazione al runtime conforme ai principi zero-trust. Questi controlli garantiscono che gli esseri umani, i servizi e gli agenti autonomi interagiscano solo con modelli, dati e risorse computazionali all'interno di ambiti concessi esplicitamente, con verifica continua e capacità di audit.

---

### Gestione delle identità e dell'autenticazione

Stabilire identità basate su crittografia per tutte le entità, con autenticazione a più fattori per operazioni privilegiate.

 #5.1.1    Livello: 1    Ruolo: D/V
 Verifica che tutti gli utenti umani e i principali di servizio si autentichino tramite un fornitore di identità aziendale centralizzato (IdP) utilizzando i protocolli OIDC/SAML con mappature identità-token uniche (nessun account o credenziale condivisi).
 #5.1.2    Livello: 1    Ruolo: D/V
 Verifica che le operazioni ad alto rischio (implementazione del modello, esportazione dei pesi, accesso ai dati di addestramento, modifiche alle configurazioni di produzione) richiedano autenticazione a più fattori o autenticazione step-up con ri-autenticazione della sessione.
 #5.1.3    Livello: 2    Ruolo: D
 Verificare che i nuovi soggetti siano sottoposti a una verifica dell'identità in linea con NIST 800-63-3 IAL-2 o standard equivalenti prima di ottenere l'accesso al sistema di produzione.
 #5.1.4    Livello: 2    Ruolo: V
 Verificare che le revisioni degli accessi siano condotte trimestralmente, con rilevamento automatico degli account inattivi, l'applicazione della rotazione delle credenziali e i flussi di de-provisioning.
 #5.1.5    Livello: 3    Ruolo: D/V
 Verifica che gli agenti IA federati si autentichino tramite asserzioni JWT firmate che abbiano una durata massima di 24 ore e includano una prova crittografica di provenienza.

---

### C5.2 Autorizzazione alle risorse e principio del minimo privilegio

Implementare controlli di accesso granulare per tutte le risorse di IA con modelli di autorizzazione espliciti e tracce di audit.

 #5.2.1    Livello: 1    Ruolo: D/V
 Verifica che ogni risorsa IA (set di dati, modelli, endpoint, collezioni di vettori, indici di embedding, istanze di calcolo) applichi controlli di accesso basati sui ruoli con liste di autorizzazione esplicite e politiche di negazione predefinite.
 #5.2.2    Livello: 1    Ruolo: D/V
 Verifica che i principi del minimo privilegio siano applicati di default, con gli account di servizio che partono da permessi di sola lettura e che richiedono una giustificazione aziendale documentata per l'accesso in scrittura.
 #5.2.3    Livello: 1    Ruolo: V
 Verifica che tutte le modifiche al controllo degli accessi siano collegate a richieste di modifica approvate e registrate in modo immutabile con timestamp, identità degli attori, identificatori delle risorse e variazioni dei permessi.
 #5.2.4    Livello: 2    Ruolo: D
 Verifica che le etichette di classificazione dei dati (PII, PHI, esportazione controllata, dati proprietari) si propagano automaticamente alle risorse derivate (rappresentazioni di embedding, cache dei prompt, uscite del modello) con un'applicazione coerente delle politiche.
 #5.2.5    Livello: 2    Ruolo: D/V
 Verifica che i tentativi di accesso non autorizzato e gli eventi di escalation dei privilegi attivino avvisi in tempo reale con metadati contestuali ai sistemi SIEM entro 5 minuti.

---

### C5.3 Valutazione dinamica della politica

Distribuire motori ABAC per decisioni di autorizzazione contestualizzate con funzionalità di audit.

 #5.3.1    Livello: 1    Ruolo: D/V
 Verificare che le decisioni di autorizzazione siano esternalizzate a un motore di policy dedicato (OPA, Cedar o equivalente), accessibile tramite API autenticati con protezione dell'integrità crittografica.
 #5.3.2    Livello: 1    Ruolo: D/V
 Verificare che le policy valutino attributi dinamici a tempo di esecuzione, inclusi il livello di autorizzazione dell'utente, la classificazione della sensibilità della risorsa, il contesto della richiesta, l'isolamento tra tenant e i vincoli temporali.
 #5.3.3    Livello: 2    Ruolo: D
 Verificare che le definizioni delle policy siano versionate, sottoposte a revisione tra pari e validate tramite test automatizzati nelle pipeline CI/CD prima della messa in produzione.
 #5.3.4    Livello: 2    Ruolo: V
 Verifica che i risultati della valutazione delle policy includano giustificazioni decisionali strutturate e siano trasmessi ai sistemi SIEM per l'analisi di correlazione e la reportistica sulla conformità.
 #5.3.5    Livello: 3    Ruolo: D/V
 Verifica che i valori TTL della cache delle policy non superino 5 minuti per le risorse ad alta sensibilità e 1 ora per le risorse standard con capacità di invalidazione della cache.

---

### C5.4 Esecuzione della sicurezza in tempo di query

Implementare controlli di sicurezza a livello di database con filtraggio obbligatorio e politiche di sicurezza a livello di riga.

 #5.4.1    Livello: 1    Ruolo: D/V
 Verifica che tutte le query sui database vettoriali e SQL includano filtri di sicurezza obbligatori (ID tenant, etichette di sensibilità, ambito utente) imposti a livello del motore del database, non nel codice dell'applicazione.
 #5.4.2    Livello: 1    Ruolo: D/V
 Verifica che le policy di sicurezza a livello di riga (RLS) e il mascheramento a livello di campo siano abilitati con l’ereditarietà delle policy per tutti i database vettoriali, gli indici di ricerca e i set di dati di addestramento.
 #5.4.3    Livello: 2    Ruolo: D
 Verifica che le valutazioni di autorizzazione fallite prevengano gli attacchi del 'confused deputy' interrompendo immediatamente le query e restituendo codici di errore di autorizzazione espliciti anziché restituire insiemi di risultati vuoti.
 #5.4.4    Livello: 2    Ruolo: V
 Verificare che la latenza della valutazione della policy sia monitorata in modo continuo con avvisi automatici per condizioni di timeout che potrebbero consentire il bypass dell'autorizzazione.
 #5.4.5    Livello: 3    Ruolo: D/V
 Verifica che i meccanismi di ritentativo delle query rivalutino le politiche di autorizzazione per tenere conto delle modifiche dinamiche ai permessi durante le sessioni utente attive.

---

### C5.5 Filtraggio dell'output & Prevenzione della perdita di dati

Implementa controlli di post-elaborazione per impedire l'esposizione non autorizzata dei dati nei contenuti generati dall'IA.

 #5.5.1    Livello: 1    Ruolo: D/V
 Verifica che i meccanismi di filtraggio post-inferenza scansionino e redigano informazioni personalmente identificabili (PII) non autorizzate, informazioni classificate e dati proprietari prima di fornire contenuti ai richiedenti.
 #5.5.2    Livello: 1    Ruolo: D/V
 Verificare che le citazioni, i riferimenti e le attribuzioni delle fonti presenti nei risultati del modello siano validati rispetto alle autorizzazioni del chiamante e rimosse se viene rilevato accesso non autorizzato.
 #5.5.3    Livello: 2    Ruolo: D
 Verifichi che le restrizioni sui formati di output (PDF sanificati, immagini prive di metadati, tipi di file approvati) siano applicate in base ai livelli di permesso degli utenti e alle classificazioni dei dati.
 #5.5.4    Livello: 2    Ruolo: V
 Verifica che gli algoritmi di anonimizzazione siano deterministici, versionati e mantengano registri di audit per supportare le indagini di conformità e l'analisi forense.
 #5.5.5    Livello: 3    Ruolo: V
 Verifica che gli eventi di redazione ad alto rischio generino registri adattivi che includano hash crittografici del contenuto originale per il recupero forense senza esposizione dei dati.

---

### C5.6 Isolamento multi-tenant

Garantire l'isolamento crittografico e logico tra i tenant in un'infrastruttura IA condivisa.

 #5.6.1    Livello: 1    Ruolo: D/V
 Verificare che gli spazi di memoria, gli archivi di embedding, le voci della cache e i file temporanei siano separati per spazio dei nomi per ciascun inquilino, con una purga sicura al momento dell'eliminazione dell'inquilino o della terminazione della sessione.
 #5.6.2    Livello: 1    Ruolo: D/V
 Verificare che ogni richiesta API includa un identificatore del tenant autenticato che sia validato crittograficamente rispetto al contesto della sessione e ai diritti dell'utente.
 #5.6.3    Livello: 2    Ruolo: D
 Verificare che le policy di rete implementino regole di rifiuto predefinito per la comunicazione tra tenant all'interno delle mesh di servizio e delle piattaforme di orchestrazione dei contenitori.
 #5.6.4    Livello: 3    Ruolo: D
 Verificare che le chiavi di cifratura siano uniche per ogni inquilino, con supporto CMK (Chiave gestita dal cliente) e isolamento crittografico tra i data store dei diversi inquilini.

---

### C5.7 Autorizzazione dell'agente autonomo

Controlla i permessi per agenti IA e sistemi autonomi tramite token di capacità con ambito definito e autorizzazione continua.

 #5.7.1    Livello: 1    Ruolo: D/V
 Verifica che agli agenti autonomi vengano forniti token di capacità con ambito definito e che tali token elenchino esplicitamente le azioni consentite, le risorse accessibili, i limiti temporali e i vincoli operativi.
 #5.7.2    Livello: 1    Ruolo: D/V
 Verificare che le capacità ad alto rischio (accesso al file system, esecuzione del codice, chiamate API esterne, transazioni finanziarie) siano disabilitate per impostazione predefinita e richiedano autorizzazioni esplicite per l'attivazione con giustificazioni aziendali.
 #5.7.3    Livello: 2    Ruolo: D
 Verificare che i token di capacità siano vincolati alle sessioni utente, includano protezione dell'integrità crittografica e non possano essere conservati o riutilizzati in scenari offline.
 #5.7.4    Livello: 2    Ruolo: V
 Verifica che le azioni avviate dall'agente siano soggette a autorizzazione secondaria tramite il motore di policy ABAC, con una valutazione completa del contesto e registrazione di audit.
 #5.7.5    Livello: 3    Ruolo: V
 Verificare che le condizioni di errore dell'agente e la gestione delle eccezioni includano informazioni sull'ambito delle capacità per supportare l'analisi degli incidenti e le indagini forensi.

---

### Riferimenti

#### Standard e Quadri di riferimento

NIST SP 800-63-3: Digital Identity Guidelines
Zero Trust Architecture – NIST SP 800-207
OWASP Application Security Verification Standard (AISVS)
​
#### Guide di implementazione

Identity and Access Management in the AI Era: 2025 Guide – IDSA
Attribute-Based Access Control with OPA – Permify
How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS
​
#### Sicurezza specifica per l'IA

Row Level Security in Vector DBs for RAG – Bluetuple.ai
Tenant Isolation in Multi-Tenant Systems – WorkOS
Handling AI Agent Permissions – Stytch
OWASP Top 10 for Large Language Model Applications

## C6 Sicurezza della catena di fornitura per modelli, framework e dati

### Obiettivo di controllo

Attacchi alla catena di fornitura dell'IA sfruttano modelli, framework o set di dati di terze parti per introdurre backdoor, bias o codice sfruttabile. Questi controlli forniscono tracciabilità end‑to‑end, gestione delle vulnerabilità e monitoraggio per proteggere l'intero ciclo di vita del modello.

---

### C6.1 Verifica e Provenienza dei Modelli Preaddestrati

Valuta e autentica le origini dei modelli di terze parti, le licenze e i comportamenti nascosti prima di qualsiasi messa a punto o implementazione in produzione.

 #6.1.1    Livello: 1    Ruolo: D/V
 Verifica che ogni artefatto di modello di terze‑parti includa un record di provenienza firmato che identifichi il repository sorgente e l'hash del commit.
 #6.1.2    Livello: 1    Ruolo: D/V
 Verificare che i modelli vengano scansionati per individuare strati dannosi o trigger Trojan utilizzando strumenti automatizzati prima dell'importazione.
 #6.1.3    Livello: 2    Ruolo: D
 Verifica che il fine-tuning nel transfer‑learning superi una valutazione avversaria per rilevare comportamenti nascosti.
 #6.1.4    Livello: 2    Ruolo: V
 Verifica che le licenze del modello, i tag di controllo export‑control e le dichiarazioni sull'origine dei dati siano registrati in una voce ML‑BOM.
 #6.1.5    Livello: 3    Ruolo: D/V
 Verifica che i modelli ad alto rischio (pesi caricati pubblicamente, creatori non verificati) rimangano in quarantena fino alla revisione e all'approvazione da parte di un essere umano.

---

### C6.2 Scansione di framework e librerie

Scansionare continuamente i framework e le librerie ML alla ricerca di CVEs e codice dannoso per mantenere lo stack di runtime sicuro.

 #6.2.1    Livello: 1    Ruolo: D/V
 Verifica che le pipeline CI eseguano scanner delle dipendenze sui framework di IA e sulle librerie critiche.
 #6.2.2    Livello: 1    Ruolo: D/V
 Verificare che le vulnerabilità critiche (CVSS ≥ 7.0) blocchino la promozione alle immagini di produzione.
 #6.2.3    Livello: 2    Ruolo: D
 Verifica che l'analisi statica del codice venga eseguita su librerie ML forkate o vendorizzate.
 #6.2.4    Livello: 2    Ruolo: V
 Verifica che le proposte di aggiornamento del framework includano una valutazione dell'impatto sulla sicurezza che faccia riferimento ai feed CVE pubblici.
 #6.2.5    Livello: 3    Ruolo: V
 Verificare che i sensori a tempo di esecuzione emettano avvisi quando si verificano caricamenti dinamici di librerie che deviano dallo SBOM firmato.

---

### C6.3 Bloccaggio delle dipendenze e verifica

Vincola ogni dipendenza a hash immutabili e riproduci le build per garantire artefatti identici e non manomissabili.

 #6.3.1    Livello: 1    Ruolo: D/V
 Verifica che tutti i gestori di pacchetti impongano il pinning delle versioni tramite i file di blocco.
 #6.3.2    Livello: 1    Ruolo: D/V
 Verifica che i digest immutabili vengano utilizzati al posto dei tag mutabili nei riferimenti ai contenitori.
 #6.3.3    Livello: 2    Ruolo: D
 Verifica che i controlli di build riproducibili confrontino gli hash tra le esecuzioni CI per garantire output identici.
 #6.3.4    Livello: 2    Ruolo: V
 Verifica che le attestazioni di build siano conservate per 18 mesi per la tracciabilità dell'audit.
 #6.3.5    Livello: 3    Ruolo: D
 Verifica che le dipendenze scadute inneschino pull request automatiche per aggiornare o forkare le versioni fissate.

---

### C6.4 Applicazione delle fonti attendibili

Consenti solo i download di artefatti da fonti verificate crittograficamente e approvate dall'organizzazione e blocca tutto il resto.

 #6.4.1    Livello: 1    Ruolo: D/V
 Verifica che i pesi del modello, i set di dati e i contenitori siano scaricati solo da domini approvati o registri interni.
 #6.4.2    Livello: 1    Ruolo: D/V
 Verifica che le firme Sigstore/Cosign validino l'identità dell'editore prima che gli artefatti vengano memorizzati nella cache locale.
 #6.4.3    Livello: 2    Ruolo: D
 Verifichi che i proxy di uscita blocchino i download di artefatti non autenticati per applicare la politica di origine attendibile.
 #6.4.4    Livello: 2    Ruolo: V
 Verifica che le liste-consentite del repository vengano riviste trimestralmente, con evidenze della giustificazione aziendale per ogni voce.
 #6.4.5    Livello: 3    Ruolo: V
 Verifica che le violazioni delle policy inneschino la quarantena degli artefatti e il rollback delle esecuzioni di pipeline dipendenti.

---

### C6.5 Valutazione del rischio del dataset di terze parti

Valutare set di dati esterni per avvelenamento, bias e conformità legale, e monitorarli durante l'intero ciclo di vita.

 #6.5.1    Livello: 1    Ruolo: D/V
 Verificare che i set di dati esterni subiscano una valutazione del rischio di avvelenamento (ad es. impronta digitale dei dati, rilevamento di outlier).
 #6.5.2    Livello: 1    Ruolo: D
 Verificare che le metriche di bias (parità demografica, parità di opportunità) siano calcolate prima dell'approvazione del set di dati.
 #6.5.3    Livello: 2    Ruolo: V
 Verificare che i termini di provenienza e di licenza per i set di dati siano registrati nelle voci ML‑BOM.
 #6.5.4    Livello: 2    Ruolo: V
 Verifica che il monitoraggio periodico rilevi la deriva o la corruzione dei dataset ospitati.
 #6.5.5    Livello: 3    Ruolo: D
 Verificare che i contenuti vietati (copyright, PII) siano rimossi tramite pulizia automatizzata prima dell'addestramento.

---

### C6.6 Monitoraggio degli attacchi alla catena di fornitura

Rilevare precocemente le minacce della supply‑chain attraverso feed CVE, analisi dei log di audit e simulazioni di red‑team.

 #6.6.1    Livello: 1    Ruolo: V
 Verifica che i log di audit CI/CD vengano trasmessi ai rilevamenti SIEM per identificare prelievi di pacchetti anomali o passaggi di build manomessi.
 #6.6.2    Livello: 2    Ruolo: D
 Verificare che i piani di risposta agli incidenti includano procedure di rollback per modelli o librerie compromessi.
 #6.6.3    Livello: 3    Ruolo: V
 Verifica che le etichette di arricchimento delle informazioni sulle minacce contengano indicatori specifici per ML (ad es. IoCs di avvelenamento del modello) nel triage degli avvisi.

---

### C6.7 ML‑BOM per gli artefatti del modello

Genera e firma digitalmente SBOM dettagliate specifiche per ML (ML‑BOM) affinché i consumatori a valle possano verificare l'integrità dei componenti al momento della messa in produzione.

 #6.7.1    Livello: 1    Ruolo: D/V
 Verifica che ogni artefatto del modello pubblichi un ML‑BOM che elenchi set di dati, pesi, iperparametri e licenze.
 #6.7.2    Livello: 1    Ruolo: D/V
 Verificare che la generazione ML‑BOM e la firma Cosign siano automatizzate nell'integrazione continua (CI) e obbligatorie per il merge.
 #6.7.3    Livello: 2    Ruolo: D
 Verifica che i controlli di completezza ML‑BOM falliscano la build se manca qualsiasi metadato del componente (hash, licenza).
 #6.7.4    Livello: 2    Ruolo: V
 Verificare che i consumatori a valle possano interrogare ML-BOMs tramite API per convalidare i modelli importati in fase di distribuzione.
 #6.7.5    Livello: 3    Ruolo: V
 Verifica che i ML‑BOMs siano sotto controllo di versione e confrontati per rilevare modifiche non autorizzate.

---

### Riferimenti

ML Supply Chain Compromise – MITRE ATLAS
Supply‑chain Levels for Software Artifacts (SLSA)
CycloneDX – Machine Learning Bill of Materials
What is Data Poisoning? – SentinelOne
Transfer Learning Attack – OWASP ML Security Top 10
AI Data Security Best Practices – CISA
Secure CI/CD Supply Chain – Sumo Logic
AI & Transparency: Protect ML Models – ReversingLabs
SBOM Overview – CISA
Training Data Poisoning Guide – Lakera.ai
Dependency Pinning for Reproducible Python – Medium

## C7 Comportamento del modello, Controllo dell'uscita e Garanzia di sicurezza.

### Obiettivo di controllo

Gli output del modello devono essere strutturati, affidabili, sicuri, spiegabili e costantemente monitorati in produzione. Ciò riduce allucinazioni, violazioni della privacy, contenuti dannosi e azioni fuori controllo, aumentando al contempo la fiducia degli utenti e la conformità normativa.

---

### C7.1 Applicazione del formato di output

Schemi rigorosi, decodifica vincolata e validazione a valle interrompono contenuti malformati o malevoli prima che si propaghino.

 #7.1.1    Livello: 1    Ruolo: D/V
 Verifica che gli schemi di risposta (ad es. JSON Schema) siano forniti nel prompt di sistema e che ogni output sia automaticamente convalidato; gli output non conformi innescano una correzione o un rifiuto.
 #7.1.2    Livello: 1    Ruolo: D/V
 Verificare che la decodifica vincolata (token di arresto, espressioni regolari, max-tokens) sia abilitata per prevenire overflow o canali laterali di prompt-injection.
 #7.1.3    Livello: 2    Ruolo: D/V
 Verifica che i componenti a valle trattino gli output come non attendibili e li validino rispetto a schemi o deserializzatori sicuri contro l'iniezione.
 #7.1.4    Livello: 3    Ruolo: V
 Verifica che gli eventi di improper-output siano registrati, limitati per tasso e esposti al monitoraggio.

---

### C7.2 Rilevazione e Mitigazione delle Allucinazioni

La stima dell'incertezza e le strategie di fallback limitano le risposte inventate.

 #7.2.1    Livello: 1    Ruolo: D/V
 Verifica che le probabilità logaritmiche a livello di token, la coerenza dell’insieme o i rilevatori di allucinazioni finemente tarati assegnino un punteggio di fiducia a ogni risposta.
 #7.2.2    Livello: 1    Ruolo: D/V
 Verifica che le risposte al di sotto di una soglia di confidenza configurabile attivino flussi di fallback (ad es., generazione potenziata dal recupero, modello secondario o revisione umana).
 #7.2.3    Livello: 2    Ruolo: D/V
 Verifica che gli incidenti di allucinazione siano etichettati con metadati della causa radice e inviati alle pipeline di post-mortem e di fine-tuning.
 #7.2.4    Livello: 3    Ruolo: D/V
 Verificare che soglie e rilevatori siano ricalibrati dopo aggiornamenti significativi del modello o della base di conoscenza.
 #7.2.5    Livello: 3    Ruolo: V
 Verifica che le visualizzazioni della dashboard monitorino i tassi di allucinazione.

---

### C7.3 Filtraggio di Sicurezza e Privacy dell'Uscita

I filtri di policy e la copertura del red-team proteggono gli utenti e i dati riservati.

 #7.3.1    Livello: 1    Ruolo: D/V
 Verifichi che i classificatori pre-generazione e post-generazione blocchino contenuti d'odio, molestie, autolesionismo, contenuti estremisti e contenuti sessualmente espliciti in linea con la politica.
 #7.3.2    Livello: 1    Ruolo: D/V
 Verifica che il rilevamento PII/PCI e la redazione automatica siano eseguiti su ogni risposta; le violazioni generano un incidente di privacy.
 #7.3.3    Livello: 2    Ruolo: D
 Verificare che le etichette di riservatezza (ad es. segreti commerciali) si propaghino attraverso le diverse modalità per prevenire la fuga di dati nel testo, nelle immagini o nel codice.
 #7.3.4    Livello: 3    Ruolo: D/V
 Verificare che i tentativi di bypass dei filtri o le classificazioni ad alto rischio richiedano un'approvazione secondaria o una ri-autenticazione dell'utente.
 #7.3.5    Livello: 3    Ruolo: D/V
 Verifica che le soglie di filtraggio riflettano le giurisdizioni legali e il contesto di età/ruolo dell'utente.

---

### C7.4 Limitazione di Output e Azione

I limiti di frequenza e i meccanismi di approvazione prevengono abusi e un'autonomia eccessiva.

 #7.4.1    Livello: 1    Ruolo: D
 Verificare che i limiti per utente e per chiave API limitino le richieste, i token e i costi con back-off esponenziale sugli errori 429.
 #7.4.2    Livello: 1    Ruolo: D/V
 Verifica che le azioni privilegiate (scritture su file, esecuzione di codice, chiamate di rete) richiedano approvazione basata su politiche o intervento umano nel loop.
 #7.4.3    Livello: 2    Ruolo: D/V
 Verifica che i controlli di coerenza multimodale garantiscano che immagini, codice e testo generati per la stessa richiesta non possano essere usati per introdurre contenuti dannosi.
 #7.4.4    Livello: 2    Ruolo: D
 Verifichi che la profondità di delega dell'agente, i limiti di ricorsione e le liste di strumenti consentiti siano configurati esplicitamente.
 #7.4.5    Livello: 3    Ruolo: V
 Verifica che la violazione dei limiti emetta eventi di sicurezza strutturati per l'ingestione SIEM.

---

### C7.5 Spiegabilità dell'output

Segnali trasparenti aumentano la fiducia degli utenti e semplificano il debugging interno.

 #7.5.1    Livello: 2    Ruolo: D/V
 Verifica che i punteggi di confidenza visibili all'utente o i brevi riepiloghi del ragionamento siano esposti quando la valutazione del rischio lo ritenga opportuno.
 #7.5.2    Livello: 2    Ruolo: D/V
 Verifica che le spiegazioni generate non rivelino prompt di sistema sensibili o dati proprietari.
 #7.5.3    Livello: 3    Ruolo: D
 Verifica che il sistema catturi le probabilità logaritmiche a livello di token o le mappe di attenzione e le memorizzi per ispezione autorizzata.
 #7.5.4    Livello: 3    Ruolo: V
 Verifica che gli artefatti di spiegabilità siano versionati insieme ai rilasci dei modelli per l'auditabilità.

---

### C7.6 Integrazione del monitoraggio

L'osservabilità in tempo reale chiude il ciclo tra sviluppo e produzione.

 #7.6.1    Livello: 1    Ruolo: D
 Verifica che le metriche (violazioni dello schema, tasso di allucinazioni, tossicità, perdite di informazioni personalmente identificabili (PII), latenza, costo) vengano trasmesse a una piattaforma di monitoraggio centrale.
 #7.6.2    Livello: 1    Ruolo: V
 Verifica che le soglie di allerta siano definite per ogni metrica di sicurezza, con percorsi di escalation disponibili in reperibilità.
 #7.6.3    Livello: 2    Ruolo: V
 Verifica che i cruscotti correlino le anomalie di output con modello/versione, flag delle funzionalità e modifiche ai dati a monte.
 #7.6.4    Livello: 2    Ruolo: D/V
 Verifica che i dati di monitoraggio alimentino il riaddestramento, il fine-tuning o gli aggiornamenti delle regole all'interno di un flusso di lavoro MLOps documentato.
 #7.6.5    Livello: 3    Ruolo: V
 Verifica che le pipeline di monitoraggio siano sottoposte a test di penetrazione e protette da controlli di accesso per evitare la perdita di log sensibili.

---

### 7.7 Salvaguardie dei media generativi

Garantire che i sistemi di IA non generino contenuti multimediali illegali, dannosi o non autorizzati, applicando vincoli di policy, validazione degli output e tracciabilità.

 #7.7.1    Livello: 1    Ruolo: D/V
 Verifica che i prompt di sistema e le istruzioni dell'utente vietino esplicitamente la generazione di deepfake illegali, dannosi o non consensuali (ad es. immagini, video, audio).
 #7.7.2    Livello: 2    Ruolo: D/V
 Verificare che i prompt siano filtrati per tentativi di generare impersonamenti, deepfake sessualmente espliciti o contenuti che ritraggono persone reali senza consenso.
 #7.7.3    Livello: 2    Ruolo: V
 Verifica che il sistema utilizzi l'hash percettivo, il rilevamento della filigrana o l'impronta digitale per impedire la riproduzione non autorizzata di contenuti protetti da copyright.
 #7.7.4    Livello: 3    Ruolo: D/V
 Verifica che tutti i media generati siano firmati digitalmente, contrassegnati con una filigrana digitale o incorporati con metadati di provenienza resistenti a manomissioni per la tracciabilità a valle.
 #7.7.5    Livello: 3    Ruolo: V
 Verifica che i tentativi di elusione (ad es. offuscamento del prompt, gergo, formulazioni avversarie) siano rilevati, registrati e limitati per tasso di richieste; abusi ripetuti siano segnalati ai sistemi di monitoraggio.

### Riferimenti

NIST AI Risk Management Framework
ISO/IEC 42001:2023 – AI Management System
OWASP Top-10 for Large Language Model Applications (2025)
Improper Output Handling – OWASP LLM05:2025
Practical Techniques to Constrain LLM Output
Dataiku – Structured Text Generation Guide
VL-Uncertainty: Detecting Hallucinations
HaDeMiF: Hallucination Detection & Mitigation
Building Confidence in LLM Outputs
Explainable AI & LLMs
LLM Red-Teaming Guide
Sensitive Information Disclosure in LLMs
LangChain – Chat Model Rate Limiting
OpenAI Rate-Limit & Exponential Back-off
Arize AI – LLM Observability Platform

## C8 Memory, Embeddings e Sicurezza del Database Vettoriale

### Obiettivo di controllo

Rappresentazioni vettoriali e archivi vettoriali fungono da "memoria attiva" dei sistemi IA contemporanei, accettando continuamente dati forniti dagli utenti e riportandoli nei contesti del modello tramite Generazione potenziata dal recupero (RAG). Se non governata, questa memoria può esporre PII (Informazioni di identificazione personale), violare il consenso o essere invertita per ricostruire il testo originale. L'obiettivo di questa famiglia di controlli è rafforzare le pipeline di memoria e i database vettoriali in modo che l'accesso sia conforme al principio del minimo privilegio, le rappresentazioni vettoriali preservino la privacy, i vettori memorizzati scadano o possano essere revocati su richiesta, e la memoria per utente non contamini mai le richieste o i completamenti di un altro utente.

---

### C8.1 Controlli di accesso su indici di memoria e RAG

Applica controlli di accesso granulare su ogni collezione di vettori.

 #8.1.1    Livello: 1    Ruolo: D/V
 Verifica che le regole di controllo degli accessi a livello di riga/namespace limitino le operazioni di inserimento, eliminazione e interrogazione per tenant, collezione o tag del documento.
 #8.1.2    Livello: 1    Ruolo: D/V
 Verifica che le chiavi API o i JWT contengano claim con ambito definito (ad es. ID delle collezioni, verbi di azione) e che siano ruotate almeno ogni trimestre.
 #8.1.3    Livello: 2    Ruolo: D/V
 Verifica che i tentativi di elevazione dei privilegi (ad es., query di similarità tra namespace) siano rilevati e registrati in un SIEM entro 5 minuti.
 #8.1.4    Livello: 2    Ruolo: D/V
 Verifica che il log di auditing del DB vettoriale registri identificatore del soggetto, operazione, ID del vettore/spazio dei nomi, soglia di similarità e conteggio dei risultati.
 #8.1.5    Livello: 3    Ruolo: V
 Verificare che le decisioni di accesso siano testate per vulnerabilità di bypass ogni volta che i motori sono aggiornati o cambiano le regole di sharding degli indici.

---

### C8.2 Sanitizzazione e Validazione degli embedding

Eseguire uno screening preliminare del testo per informazioni di identificazione personale (PII), oscurare o pseudonimizzare prima della vettorializzazione, e, facoltativamente, post-elaborare le rappresentazioni vettoriali per eliminare segnali residui.

 #8.2.1    Livello: 1    Ruolo: D/V
 Verificare che PII e dati regolamentati siano rilevati tramite classificatori automatizzati e mascherati, tokenizzati o scartati prima dell'embedding.
 #8.2.2    Livello: 1    Ruolo: D
 Verifichi che le pipeline di embedding rifiutino o mettano in quarantena gli input contenenti codice eseguibile o artefatti non UTF-8 che potrebbero compromettere l'indice.
 #8.2.3    Livello: 2    Ruolo: D/V
 Verifichi che sia applicata la sanitizzazione della privacy differenziale locale o basata su metriche agli embedding di frasi la cui distanza da qualsiasi token PII noto sia inferiore a una soglia configurabile.
 #8.2.4    Livello: 2    Ruolo: V
 Verificare che l'efficacia della sanitizzazione (ad es. richiamo del mascheramento di PII, deriva semantica) sia validata almeno semestralmente su corpora di riferimento.
 #8.2.5    Livello: 3    Ruolo: D/V
 Verifica che le configurazioni di sanificazione siano versionate e che le modifiche siano sottoposte a revisione tra pari.

---

### C8.3 Scadenza della memoria, Revoca e Cancellazione

GDPR e leggi simili sul diritto all'oblio richiedono una cancellazione tempestiva; gli archivi vettoriali devono quindi supportare TTLs, cancellazioni definitive e tomb-stoning affinché i vettori revocati non possano essere recuperati o indicizzati di nuovo.

 #8.3.1    Livello: 1    Ruolo: D/V
 Verifica che ogni vettore e ogni record di metadati contengano un TTL o un'etichetta esplicita di conservazione che sia rispettata dai lavori di pulizia automatizzata.
 #8.3.2    Livello: 1    Ruolo: D/V
 Verificare che le richieste di eliminazione avviate dall'utente cancellino vettori, metadati, copie nella cache e indici derivati entro 30 giorni.
 #8.3.3    Livello: 2    Ruolo: D
 Verifica che le cancellazioni logiche siano seguite dalla cancellazione crittografica dei blocchi di archiviazione, se l'hardware lo supporta, oppure dalla distruzione delle chiavi nel Key Vault.
 #8.3.4    Livello: 3    Ruolo: D/V
 Verifica che i vettori scaduti siano esclusi dai risultati della ricerca del vicino più prossimo entro < 500 ms dalla scadenza.

---

### C8.4 Prevenire l'inversione dell'embedding e la fuga di dati

Difese recenti—superposizione del rumore, reti di proiezione, perturbazione dei neuroni per la privacy e crittografia a livello di applicazione—possono ridurre i tassi di inversione a livello di token al di sotto del 5%.

 #8.4.1    Livello: 1    Ruolo: V
 Verifica che esista un modello di minaccia formale che copra gli attacchi di inversione, di appartenenza e di inferenza degli attributi, e che venga revisionato annualmente.
 #8.4.2    Livello: 2    Ruolo: D/V
 Verifica che la crittografia a livello di applicazione o la crittografia ricercabile proteggano i vettori dalle letture dirette da parte degli amministratori dell'infrastruttura o del personale del cloud.
 #8.4.3    Livello: 3    Ruolo: V
 Verifica che i parametri di difesa (ε per DP, rumore σ, rango di proiezione k) bilancino la privacy differenziale ≥ 99 % protezione dei token e l'utilità ≤ 3 % perdita di accuratezza.
 #8.4.4    Livello: 3    Ruolo: D/V
 Verifica che le metriche di resilienza all'inversione siano parte dei gate di rilascio per gli aggiornamenti dei modelli, con budget di regressione definiti.

---

### C8.5 Applicazione dell'ambito per la memoria specifica dell'utente

La fuga tra tenant rimane tra i principali rischi della RAG: query di similarità filtrate in modo improprio possono esporre documenti privati di un altro cliente.

 #8.5.1    Livello: 1    Ruolo: D/V
 Verifica che ogni query di recupero sia post-filtrata per l'ID del tenant e dell'utente prima di essere inviata al prompt LLM.
 #8.5.2    Livello: 1    Ruolo: D
 Verifica che i nomi delle collezioni o gli ID con namespace siano salati per utente o tenant, in modo che i vettori non possano collidere tra gli ambiti.
 #8.5.3    Livello: 2    Ruolo: D/V
 Verificare che i risultati di similarità superiori a una soglia di distanza configurabile ma al di fuori dell'ambito del richiedente vengano scartati e che scattino avvisi di sicurezza.
 #8.5.4    Livello: 2    Ruolo: V
 Verifica che i test di stress multi-tenant simulino richieste avversarie volte a recuperare documenti fuori dal perimetro e dimostrino l'assenza di fuga di dati.
 #8.5.5    Livello: 3    Ruolo: D/V
 Verifichi che le chiavi di cifratura siano separate per ogni tenant, garantendo l'isolamento crittografico anche se l'archiviazione fisica è condivisa.

---

### C8.6 Sicurezza avanzata del sistema di memoria

Controlli di sicurezza per architetture di memoria sofisticate che includono memoria episodica, semantica e memoria di lavoro, con requisiti specifici di isolamento e validazione.

 #8.6.1    Livello: 1    Ruolo: D/V
 Verifica che i diversi tipi di memoria (episodica, semantica e di lavoro) abbiano contesti di sicurezza isolati con controlli di accesso basati sui ruoli, chiavi di cifratura separate e schemi di accesso documentati per ciascun tipo di memoria.
 #8.6.2    Livello: 2    Ruolo: D/V
 Verifica che i processi di consolidamento della memoria includano la validazione di sicurezza per prevenire l'iniezione di memorie dannose tramite la sanitizzazione dei contenuti, la verifica della fonte e i controlli di integrità prima della memorizzazione.
 #8.6.3    Livello: 2    Ruolo: D/V
 Verifica che le query di recupero della memoria siano valide e sanificate per impedire l'estrazione di informazioni non autorizzate mediante analisi dei pattern di query, l'applicazione del controllo degli accessi e il filtraggio dei risultati.
 #8.6.4    Livello: 3    Ruolo: D/V
 Verificare che i meccanismi di cancellazione della memoria eliminino in modo sicuro le informazioni sensibili con garanzie di cancellazione crittografica, utilizzando l'eliminazione della chiave, la sovrascrittura a più passaggi o la cancellazione sicura basata su hardware-based con certificati di verifica.
 #8.6.5    Livello: 3    Ruolo: D/V
 Verifica che l'integrità del sistema di memoria sia costantemente monitorata per modifiche non autorizzate o corruzione tramite somme di controllo, registri di audit e avvisi automatici quando il contenuto della memoria cambia al di fuori delle operazioni normali.

---

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

## 9 Orchestrazione Autonoma & Azione Agentica Sicurezza

### Obiettivo di controllo

Garantire che i sistemi IA autonomi o multiagente possano eseguire azioni solo se espressamente destinate, autenticabili, auditabili e entro soglie di costo e rischio definite. Questo protegge contro minacce quali compromissione di un sistema autonomo, uso improprio degli strumenti, rilevamento del ciclo dell’agente, dirottamento delle comunicazioni, falsificazione dell’identità, manipolazione di sciami e manipolazione delle intenzioni.

---

### 9.1 Pianificazione dei compiti dell'agente e budget di ricorsione

Limitare i piani ricorsivi e imporre punti di controllo umani per azioni privilegiate.

 #9.1.1    Livello: 1    Ruolo: D/V
 Verifichi che la profondità massima di ricorsione, l'ampiezza della ricerca, il tempo reale di esecuzione, i token e il costo monetario per l'esecuzione dell'agente siano configurati centralmente e versionati.
 #9.1.2    Livello: 1    Ruolo: D/V
 Verifichi che le azioni privilegiate o irreversibili (ad es., commit di codice, trasferimenti finanziari) richiedano un'approvazione esplicita da parte di un essere umano tramite un canale auditabile prima dell'esecuzione.
 #9.1.3    Livello: 2    Ruolo: D
 Verifica che i monitor delle risorse in tempo reale attivino l'interruzione del circuit breaker non appena viene superata una qualsiasi soglia di budget, interrompendo ulteriori espansioni delle attività.
 #9.1.4    Livello: 2    Ruolo: D/V
 Verificare che gli eventi del circuit-breaker siano registrati con l'ID dell'agente, la condizione di attivazione e lo stato del piano acquisito per la revisione forense.
 #9.1.5    Livello: 3    Ruolo: V
 Verificare che i test di sicurezza includano scenari di esaurimento del budget e di esecuzione incontrollata del piano, confermando una fermata sicura senza perdita di dati.
 #9.1.6    Livello: 3    Ruolo: D
 Verifica che le politiche di budget siano espresse come policy-as-code e applicate in CI/CD per bloccare la deriva di configurazione.

---

### 9.2 Sandbox dei plugin degli strumenti

Isolare le interazioni tra gli strumenti per prevenire l'accesso non autorizzato al sistema o l'esecuzione di codice.

 #9.2.1    Livello: 1    Ruolo: D/V
 Verifica che ogni strumento o plug-in venga eseguito all'interno di una sandbox a livello di sistema operativo, contenitore o WASM, con politiche di privilegio minimo per il sistema di file, la rete e le chiamate di sistema.
 #9.2.2    Livello: 1    Ruolo: D/V
 Verificare che i limiti delle risorse della sandbox (CPU, memoria, disco, uscita di rete) e i timeout di esecuzione siano applicati e registrati.
 #9.2.3    Livello: 2    Ruolo: D/V
 Verificare che i binari degli strumenti o i descrittori siano firmati digitalmente; le firme vengano verificate prima del caricamento.
 #9.2.4    Livello: 2    Ruolo: V
 Verifica che la telemetria della sandbox venga inviata a un SIEM; anomalie (ad es., tentativi di connessioni in uscita) generino allarmi.
 #9.2.5    Livello: 3    Ruolo: V
 Verificare che i plugin ad alto rischio siano sottoposti a una revisione della sicurezza e a test di penetrazione prima della messa in produzione.
 #9.2.6    Livello: 3    Ruolo: D/V
 Verifica che i tentativi di fuga dalla sandbox siano bloccati automaticamente e che il plugin incriminato sia messo in quarantena in attesa di un'indagine.

---

### 9.3 Loop Autonomo & Vincolo sui Costi

Rileva e interrompi la ricorsione non controllata tra agenti e le esplosioni di costo.

 #9.3.1    Livello: 1    Ruolo: D/V
 Verifica che le chiamate tra agenti includano un limite di hop o TTL che il runtime decrementa e impone.
 #9.3.2    Livello: 2    Ruolo: D
 Verifica che gli agenti mantengano un identificatore univoco del grafo di invocazione per individuare auto-invocazione o schemi ciclici.
 #9.3.3    Livello: 2    Ruolo: D/V
 Verifica che i contatori cumulativi di unità di calcolo e di spesa siano tracciati per ogni catena di richieste; superare il limite interrompe la catena.
 #9.3.4    Livello: 3    Ruolo: V
 Verificare che l’analisi formale o il model checking dimostri l’assenza di ricorsione non vincolata nei protocolli degli agenti.
 #9.3.5    Livello: 3    Ruolo: D
 Verificare che gli eventi di terminazione del ciclo generino avvisi e alimentino metriche di miglioramento continuo.

---

### 9.4 Protezione a livello di protocollo contro l'uso improprio

Canali di comunicazione sicuri tra agenti e sistemi esterni per prevenire il dirottamento o la manomissione.

 #9.4.1    Livello: 1    Ruolo: D/V
 Verifica che tutti i messaggi agente-a-strumento e agente-a-agente siano autenticati (ad es. TLS reciproco o JWT) e crittografati end-to-end.
 #9.4.2    Livello: 1    Ruolo: D
 Verifica che gli schemi siano validati in modo rigoroso e che i campi sconosciuti o i messaggi malformati vengano rifiutati.
 #9.4.3    Livello: 2    Ruolo: D/V
 Verifica che i controlli di integrità (MAC o firme digitali) coprano l'intero payload del messaggio, inclusi i parametri dello strumento.
 #9.4.4    Livello: 2    Ruolo: D
 Verifica che la protezione contro il replay (nonce o finestre temporali) sia applicata a livello di protocollo.
 #9.4.5    Livello: 3    Ruolo: V
 Verificare che le implementazioni dei protocolli subiscano fuzzing e analisi statica per vulnerabilità di iniezione o deserializzazione.

---

### 9.5 Identità dell'agente e prova di manomissione

Assicurarsi che le azioni siano attribuibili e che le modifiche siano rilevabili.

 #9.5.1    Livello: 1    Ruolo: D/V
 Verifica che ogni istanza dell'agente possegga un'identità crittografica unica (coppia di chiavi o credenziale radicata nell'hardware).
 #9.5.2    Livello: 2    Ruolo: D/V
 Verifica che tutte le azioni dell'agente siano firmate e datate; i registri includono la firma per non ripudio.
 #9.5.3    Livello: 2    Ruolo: V
 Verificare che i log antimanomissione siano archiviati su un supporto append-only o write-once.
 #9.5.4    Livello: 3    Ruolo: D
 Verificare che le chiavi di identità ruotino secondo una pianificazione definita e in presenza di indicatori di compromissione.
 #9.5.5    Livello: 3    Ruolo: D/V
 Verifica che i tentativi di spoofing o di conflitto di chiavi attivino immediatamente la quarantena dell'agente interessato.

---

### 9.6 Riduzione del rischio dello sciame di agenti multipli

Ridurre i rischi associati al comportamento collettivo tramite isolamento e modellazione formale della sicurezza.

 #9.6.1    Livello: 1    Ruolo: D/V
 Verifica che gli agenti operanti in diversi domini di sicurezza vengano eseguiti in sandbox di runtime isolati o segmenti di rete isolati.
 #9.6.2    Livello: 3    Ruolo: V
 Verifica che i comportamenti dello sciame siano modellati e verificati formalmente per la vivacità e la sicurezza prima della messa in produzione.
 #9.6.3    Livello: 3    Ruolo: D
 Verificare che i monitor di esecuzione rilevino modelli pericolosi emergenti (ad es. oscillazioni, interblocchi) e avviino azioni correttive.

---

### 9.7 Autenticazione / Autorizzazione di utenti e strumenti

Implementa controlli di accesso robusti per ogni azione attivata dall'agente.

 #9.7.1    Livello: 1    Ruolo: D/V
 Verificare che gli agenti si autentichino come principali di prima classe verso i sistemi a valle, senza riutilizzare mai le credenziali dell'utente finale.
 #9.7.2    Livello: 2    Ruolo: D
 Verifica che le politiche di autorizzazione a granularità fine limitino quali strumenti un agente può invocare e quali parametri può fornire.
 #9.7.3    Livello: 2    Ruolo: V
 Verificare che i controlli sui privilegi vengano rivalutati ad ogni chiamata (autorizzazione continua), non solo all'avvio della sessione.
 #9.7.4    Livello: 3    Ruolo: D
 Verificare che i privilegi delegati scadano automaticamente e richiedano nuovamente il consenso dopo la scadenza o una modifica dell'ambito.

---

### 9.8 Sicurezza delle comunicazioni tra agenti

Crittografa e proteggi l'integrità di tutti i messaggi tra agenti per contrastare intercettazioni e manomissioni.

 #9.8.1    Livello: 1    Ruolo: D/V
 Verificare che l'autenticazione reciproca e la cifratura con segretezza perfetta in avanti (ad es. TLS 1.3) siano obbligatorie per i canali dell'agente.
 #9.8.2    Livello: 1    Ruolo: D
 Verifica che l'integrità del messaggio e l'origine siano verificate prima dell'elaborazione; in caso di fallimento, vengano generati avvisi e il messaggio venga scartato.
 #9.8.3    Livello: 2    Ruolo: D/V
 Verifica che i metadati di comunicazione (marcatori temporali, numeri di sequenza) siano registrati per supportare la ricostruzione forense.
 #9.8.4    Livello: 3    Ruolo: V
 Verificare che la verifica formale o il model checking confermino che le macchine a stati del protocollo non possano essere portate in stati non sicuri.

---

### 9.9 Verifica dell'intento e applicazione dei vincoli

Verifica che le azioni dell'agente siano allineate all'intento dichiarato dall'utente e ai vincoli di sistema.

 #9.9.1    Livello: 1    Ruolo: D
 Verifica che i risolutori di vincoli pre-esecuzione controllino le azioni proposte rispetto alle regole di sicurezza e alle policy codificate.
 #9.9.2    Livello: 2    Ruolo: D/V
 Verifica che le azioni ad alto impatto (finanziarie, distruttive, sensibili alla privacy) richiedano una conferma esplicita dell'intento da parte dell'utente che ha avviato l'azione.
 #9.9.3    Livello: 2    Ruolo: V
 Verificare che i controlli post-condizione confermino che le azioni completate hanno raggiunto gli effetti previsti senza effetti collaterali; in caso di discrepanze, scatta il rollback.
 #9.9.4    Livello: 3    Ruolo: V
 Verifichi che i metodi formali (ad es. model checking, dimostrazione di teoremi) o i test basati sulle proprietà dimostrino che i piani dell'agente soddisfino tutti i vincoli dichiarati.
 #9.9.5    Livello: 3    Ruolo: D
 Verifica che gli incidenti di intent-mismatch o di constraint-violation alimentino cicli di continuous-improvement e condivisione di threat-intel.

---

### 9.10 Strategia di ragionamento degli agenti: sicurezza

Selezione e esecuzione sicure di diverse strategie di ragionamento, tra cui ReAct, Chain-of-Thought e Tree-of-Thoughts.

 #9.10.1    Livello: 1    Ruolo: D/V
 Verifica che la selezione della strategia di ragionamento si basi su criteri deterministici (complessità dell'input, tipo di compito, contesto di sicurezza) e che input identici producano selezioni di strategia identiche all'interno dello stesso contesto di sicurezza.
 #9.10.2    Livello: 1    Ruolo: D/V
 Verifica che ogni strategia di ragionamento (ReAct, Chain-of-Thought, Tree-of-Thoughts) abbia una validazione dedicata dell'input, una sanitizzazione dell'output e limiti di tempo di esecuzione specifici al suo approccio cognitivo.
 #9.10.3    Livello: 2    Ruolo: D/V
 Verifica che le transizioni della strategia di ragionamento siano registrate con contesto completo, incluse le caratteristiche dell'input, i valori dei criteri di selezione e i metadati di esecuzione, per la ricostruzione della traccia di audit.
 #9.10.4    Livello: 2    Ruolo: D/V
 Verifica che il ragionamento ad albero dei pensieri includa meccanismi di potatura dei rami che terminano l'esplorazione quando vengono rilevate violazioni delle politiche, limiti delle risorse o confini di sicurezza.
 #9.10.5    Livello: 2    Ruolo: D/V
 Verifica che i cicli ReAct (Reason-Act-Observe) includano punti di controllo di validazione in ogni fase: verifica dei passaggi di ragionamento, autorizzazione delle azioni e sanitizzazione delle osservazioni prima di procedere.
 #9.10.6    Livello: 3    Ruolo: D/V
 Verifica che le metriche delle prestazioni della strategia di ragionamento (tempo di esecuzione, utilizzo delle risorse, qualità dell'output) siano monitorate con avvisi automatici quando le metriche si discostano dai limiti configurati.
 #9.10.7    Livello: 3    Ruolo: D/V
 Verifica che gli approcci di ragionamento ibridi che combinano diverse strategie mantengano la validazione degli input e i vincoli di output di tutte le strategie costituenti, senza aggirare alcun controllo di sicurezza.
 #9.10.8    Livello: 3    Ruolo: D/V
 Verifica che i test di sicurezza della strategia di ragionamento includano fuzzing con input malformati, prompt avversari progettati per costringere un cambio di strategia e test delle condizioni al contorno per ciascun approccio cognitivo.

---

### 9.11 Gestione dello stato del ciclo di vita dell'agente e della sicurezza

Inizializzazione sicura dell'agente, transizioni di stato e terminazione con tracce di audit crittografiche e procedure di recupero definite.

 #9.11.1    Livello: 1    Ruolo: D/V
 Verifica che l'inizializzazione dell'agente includa la creazione dell'identità crittografica con credenziali protette dall'hardware e registri di audit all'avvio immutabili contenenti l'ID dell'agente, marca temporale, hash della configurazione e parametri di inizializzazione.
 #9.11.2    Livello: 2    Ruolo: D/V
 Verificare che le transizioni di stato dell'agente siano firmate crittograficamente, marcate temporalmente e registrate con contesto completo, inclusi gli eventi scatenanti, l'hash dello stato precedente, l'hash dello stato nuovo e le verifiche di sicurezza eseguite.
 #9.11.3    Livello: 2    Ruolo: D/V
 Verificare che le procedure di spegnimento dell'agente includano la cancellazione sicura della memoria mediante cancellazione crittografica o sovrascrittura multipassi, la revoca delle credenziali con notifica all'autorità certificante e la generazione di certificati di terminazione a prova di manomissione.
 #9.11.4    Livello: 3    Ruolo: D/V
 Verificare che i meccanismi di recupero degli agenti convalidino l'integrità dello stato utilizzando checksum crittografici (SHA-256 minimo) e tornino a stati noti e affidabili quando venga rilevata la corruzione, con avvisi automatizzati e requisiti di approvazione manuale.
 #9.11.5    Livello: 3    Ruolo: D/V
 Verifica che i meccanismi di persistenza degli agenti cifrino i dati di stato sensibili con chiavi AES-256 per agente e implementino la rotazione sicura delle chiavi su intervalli configurabili (massimo 90 giorni) con distribuzione senza tempi di inattività.

---

### 9.12 Quadro di Sicurezza per l'Integrazione degli Strumenti

Controlli di sicurezza per il caricamento dinamico degli strumenti, l'esecuzione e la convalida dei risultati, con processi di valutazione del rischio e di approvazione definiti.

 #9.12.1    Livello: 1    Ruolo: D/V
 Verifica che i descrittori degli strumenti includano metadati di sicurezza che specificano privilegi richiesti (lettura/scrittura/esecuzione), livelli di rischio (basso/medio/alto), limiti delle risorse (CPU, memoria, rete) e requisiti di validazione documentati nei manifest degli strumenti.
 #9.12.2    Livello: 1    Ruolo: D/V
 Verifica che i risultati dell'esecuzione degli strumenti siano validati rispetto agli schemi attesi (JSON Schema, XML Schema) e alle politiche di sicurezza (sanitizzazione dell'output, classificazione dei dati) prima dell'integrazione con limiti di timeout e procedure di gestione degli errori.
 #9.12.3    Livello: 2    Ruolo: D/V
 Verifica che i log di interazione degli strumenti includano un contesto di sicurezza dettagliato, tra cui l'uso dei privilegi, i modelli di accesso ai dati, il tempo di esecuzione, il consumo di risorse e i codici di ritorno, con logging strutturato per l'integrazione SIEM.
 #9.12.4    Livello: 2    Ruolo: D/V
 Verifichi che i meccanismi di caricamento dinamico degli strumenti validino le firme digitali utilizzando l'infrastruttura PKI e implementino protocolli di caricamento sicuri con isolamento sandbox e verifica delle autorizzazioni prima dell'esecuzione.
 #9.12.5    Livello: 3    Ruolo: D/V
 Verificare che le valutazioni di sicurezza dello strumento vengano attivate automaticamente per le nuove versioni, con gate di approvazione obbligatori che includano analisi statica, test dinamici e revisione da parte del team di sicurezza, con criteri di approvazione documentati e requisiti SLA.

---

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

### Obiettivo di controllo

Assicura che i modelli di IA rimangano affidabili, rispettosi della privacy e resistenti agli abusi quando affrontano attacchi di elusione, inferenza, estrazione o avvelenamento.

---

### 10.1 Allineamento del modello e sicurezza

Proteggi da output dannosi o che violano le policy.

 #10.1.1    Livello: 1    Ruolo: D/V
 Verifica che un test-suite di allineamento (red-team prompts, jailbreak probes, disallowed content) sia version-controlled e venga eseguito ad ogni rilascio del modello.
 #10.1.2    Livello: 1    Ruolo: D
 Verifica che le barriere di rifiuto e di completamento sicuro siano applicate.
 #10.1.3    Livello: 2    Ruolo: D/V
 Verifichi che un valutatore automatizzato misuri il tasso di contenuti dannosi e segnali le regressioni oltre una soglia prestabilita.
 #10.1.4    Livello: 2    Ruolo: D
 Verificare che l'addestramento contro il jailbreaking sia documentato e riproducibile.
 #10.1.5    Livello: 3    Ruolo: V
 Verifichi che le prove formali di conformità alle politiche o il monitoraggio certificato coprano domini critici.

---

### 10.2 Rafforzamento contro esempi avversari

Aumentare la resilienza agli input manipolati. L'addestramento avversario robusto e la valutazione tramite benchmark sono le migliori pratiche attuali.

 #10.2.1    Livello: 1    Ruolo: D
 Verifica che i repository di progetto includano configurazioni di addestramento avversario con semi riproducibili.
 #10.2.2    Livello: 2    Ruolo: D/V
 Verifica che il rilevamento di esempi avversari generi avvisi di blocco nelle pipeline di produzione.
 #10.2.4    Livello: 3    Ruolo: V
 Verifica che le prove di robustezza-certificata o i certificati a intervallo coprano almeno le classi più critiche.
 #10.2.5    Livello: 3    Ruolo: V
 Verifica che i test di regressione utilizzino attacchi adattivi per confermare l'assenza di perdita di robustezza misurabile.

---

### 10.3 Mitigazione dell'inferenza di appartenenza

Limitare la capacità di determinare se un record fosse presente nei dati di addestramento. La privacy differenziale e il mascheramento dei punteggi di confidenza restano le difese note più efficaci.

 #10.3.1    Livello: 1    Ruolo: D
 Verifica che la regolarizzazione dell'entropia per query o la calibrazione tramite temperatura riduca le previsioni eccessivamente sicure.
 #10.3.2    Livello: 2    Ruolo: D
 Verifica che l'addestramento impieghi un’ottimizzazione differenzialmente privata vincolata da ε per set di dati sensibili.
 #10.3.3    Livello: 2    Ruolo: V
 Verifica che le simulazioni di attacco (modello-ombra o scatola nera) mostrino l'AUC dell'attacco ≤ 0.60 sui dati hold-out.

---

### 10.4 Resistenza all'inversione del modello

Impedire la ricostruzione degli attributi privati. I recenti studi sottolineano il troncamento dell'output e le garanzie di privacy differenziale come difese pratiche.

 #10.4.1    Livello: 1    Ruolo: D
 Verificare che gli attributi sensibili non vengano mai forniti direttamente; dove necessario, utilizzare la bucketizzazione o trasformazioni unidirezionali.
 #10.4.2    Livello: 1    Ruolo: D/V
 Verificare che i limiti di frequenza delle query limitino le interrogazioni adattive ripetute provenienti dallo stesso soggetto.
 #10.4.3    Livello: 2    Ruolo: D
 Verifica che il modello sia addestrato con rumore che preserva la privacy.

---

### 10.5 Difesa contro l'estrazione del modello

Rilevare e scoraggiare la clonazione non autorizzata. Si consiglia la marchiatura digitale e l'analisi dei pattern di query.

 #10.5.1    Livello: 1    Ruolo: D
 Verificare che i gateway di inferenza applichino limiti di velocità globali e per chiave API adeguati alla soglia di memorizzazione del modello.
 #10.5.2    Livello: 2    Ruolo: D/V
 Verifica che le statistiche di entropia della query e di pluralità dell'input alimentino un rilevatore di estrazione automatizzato.
 #10.5.3    Livello: 2    Ruolo: V
 Verificare che le filigrane fragili o probabilistiche possano essere dimostrate con p < 0,01 in ≤ 1 000 richieste contro un clone sospetto.
 #10.5.4    Livello: 3    Ruolo: D
 Verificare che le chiavi della filigrana e gli insiemi di trigger siano archiviati in un modulo di sicurezza hardware e vengano ruotati annualmente.
 #10.5.5    Livello: 3    Ruolo: V
 Verifica che gli eventi di allerta di estrazione includano query offensive e siano integrati con i playbook di risposta agli incidenti.

---

### 10.6 Rilevamento dei dati avvelenati durante l'inferenza

Identificare e neutralizzare input compromessi da backdoor o avvelenati.

 #10.6.1    Livello: 1    Ruolo: D
 Verifica che gli input passino attraverso un rilevatore di anomalie (ad es. STRIP, punteggio di coerenza) prima dell'inferenza del modello.
 #10.6.2    Livello: 1    Ruolo: V
 Verificare che le soglie del rilevatore siano tarate su set di validazione puliti/avvelenati per ottenere meno del 5% di falsi positivi.
 #10.6.3    Livello: 2    Ruolo: D
 Verifica che gli input etichettati come avvelenati attivino il blocco morbido e i flussi di lavoro di revisione umana.
 #10.6.4    Livello: 2    Ruolo: V
 Verifica che i rilevatori siano sottoposti a test di stress con attacchi backdoor adattivi senza trigger.
 #10.6.5    Livello: 3    Ruolo: D
 Verifica che le metriche di efficacia della rilevazione siano registrate e rivalutate periodicamente utilizzando nuove informazioni sulle minacce.

---

### 10.7 Adattamento dinamico della politica di sicurezza

Aggiornamenti in tempo reale delle politiche di sicurezza basati su informazioni sulle minacce e analisi comportamentale.

 #10.7.1    Livello: 1    Ruolo: D/V
 Verifica che le policy di sicurezza possano essere aggiornate dinamicamente senza riavviare l'agente, mantenendo l'integrità della versione della policy di sicurezza.
 #10.7.2    Livello: 2    Ruolo: D/V
 Verifica che gli aggiornamenti delle politiche siano firmati digitalmente da personale di sicurezza autorizzato e validati prima dell'applicazione.
 #10.7.3    Livello: 2    Ruolo: D/V
 Verificare che le modifiche dinamiche delle politiche siano registrate con tracce complete di audit, tra cui la giustificazione, le catene di approvazione e le procedure di rollback.
 #10.7.4    Livello: 3    Ruolo: D/V
 Verificare che i meccanismi di sicurezza adattivi adattino la sensibilità del rilevamento delle minacce in base al contesto di rischio e ai modelli comportamentali.
 #10.7.5    Livello: 3    Ruolo: D/V
 Verifica che le decisioni di adattamento delle politiche siano spiegabili e includano tracce di evidenza per la revisione da parte del team di sicurezza.

---

### 10.8 Analisi della sicurezza basata sulla riflessione

Verifica della sicurezza tramite autovalutazione dell'agente e analisi metacognitiva.

 #10.8.1    Livello: 1    Ruolo: D/V
 Verifica che i meccanismi di riflessione degli agenti includano un'autovalutazione orientata alla sicurezza delle decisioni e delle azioni.
 #10.8.2    Livello: 2    Ruolo: D/V
 Verificare che gli output della riflessione siano validati per prevenire la manipolazione dei meccanismi di autovalutazione da parte di input ostili.
 #10.8.3    Livello: 2    Ruolo: D/V
 Verifica che l'analisi di sicurezza metacognitiva identifichi potenziali bias, manipolazione o compromissione nei processi di ragionamento dell'agente.
 #10.8.4    Livello: 3    Ruolo: D/V
 Verifichi che gli avvisi di sicurezza basati sulla riflessione attivino un monitoraggio avanzato e potenziali flussi di intervento umano.
 #10.8.5    Livello: 3    Ruolo: D/V
 Verifica che l'apprendimento continuo dalle riflessioni sulla sicurezza migliori il rilevamento delle minacce senza compromettere la funzionalità legittima.

---

### 10.9 Evoluzione e Sicurezza dell'Auto-miglioramento

Controlli di sicurezza per sistemi agenti in grado di auto-modificarsi ed evolversi.

 #10.9.1    Livello: 1    Ruolo: D/V
 Verificare che le capacità di auto-modifica siano limitate alle aree designate sicure con confini di verifica formali.
 #10.9.2    Livello: 2    Ruolo: D/V
 Verificare che le proposte di evoluzione siano sottoposte a una valutazione dell'impatto sulla sicurezza prima dell'implementazione.
 #10.9.3    Livello: 2    Ruolo: D/V
 Verifica che i meccanismi di auto-miglioramento includano capacità di rollback con verifica dell'integrità.
 #10.9.4    Livello: 3    Ruolo: D/V
 Verifica che la sicurezza del meta-apprendimento impedisca la manipolazione avversaria degli algoritmi di miglioramento.
 #10.9.5    Livello: 3    Ruolo: D/V
 Verifica che l'auto-miglioramento ricorsivo sia limitato dai vincoli di sicurezza formali con dimostrazioni matematiche della convergenza.

---

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

### Obiettivo di controllo

Mantieni garanzie di privacy rigorose per l'intero ciclo di vita dell'IA—raccolta, addestramento, inferenza e gestione degli incidenti—in modo che i dati personali siano trattati solo con consenso chiaro, ambito minimo necessario, cancellazione dimostrabile e garanzie formali sulla privacy.

---

### 11.1 Anonimizzazione e minimizzazione dei dati

 #11.1.1    Livello: 1    Ruolo: D/V
 Verifica che gli identificatori diretti e i quasi-identificatori siano rimossi e hashati.
 #11.1.2    Livello: 2    Ruolo: D/V
 Verificare che le verifiche automatizzate misurino k-anonimato/l-diversità e avvisino quando le soglie scendono al di sotto della policy.
 #11.1.3    Livello: 2    Ruolo: V
 Verifichi che i report sull'importanza delle feature del modello dimostrino che non vi è alcuna fuga di identificatori oltre ε = 0.01 di informazione mutua.
 #11.1.4    Livello: 3    Ruolo: V
 Verifichi che le dimostrazioni formali o la certificazione dei dati sintetici mostrino un rischio di ri-identificazione ≤ 0.05 anche in presenza di attacchi di collegamento dei dati.

---

### 11.2 Diritto all'oblio e all'attuazione della cancellazione

 #11.2.1    Livello: 1    Ruolo: D/V
 Verifica che le richieste di cancellazione dei dati del soggetto si propaghino a dataset grezzi, checkpoint, embedding, log e backup entro gli accordi sul livello di servizio inferiori a 30 giorni.
 #11.2.2    Livello: 2    Ruolo: D
 Verifica che le routine di "machine-unlearning" riaddestrino fisicamente o approssimino la rimozione utilizzando algoritmi certificati di disimparazione.
 #11.2.3    Livello: 2    Ruolo: V
 Verifica che la valutazione del modello-ombra dimostri che i record dimenticati influenzano meno del 1% degli output dopo l'unlearning.
 #11.2.4    Livello: 3    Ruolo: V
 Verificare che gli eventi di cancellazione siano registrati in modo immutabile e auditabili per le autorità di regolamentazione.

---

### 11.3 Differential-Privacy Salvaguardie

 #11.3.1    Livello: 2    Ruolo: D/V
 Verifica che i cruscotti di rendicontazione della perdita di privacy emettano avvisi quando ε cumulativo supera le soglie della policy.
 #11.3.2    Livello: 2    Ruolo: V
 Verifica che le verifiche di privacy a scatola nera stimino ε̂ entro il 10% del valore dichiarato.
 #11.3.3    Livello: 3    Ruolo: V
 Verifica che le prove formali coprano tutti i processi di fine-tuning post-addestramento e le rappresentazioni di embedding.

---

### 11.4 Limitazione dello scopo e protezione contro l'espansione dell'ambito

 #11.4.1    Livello: 1    Ruolo: D
 Verifica che ogni dataset e ogni checkpoint del modello abbiano etichette di scopo leggibili da macchina allineate al consenso originale.
 #11.4.2    Livello: 1    Ruolo: D/V
 Verifica che i monitor di esecuzione rilevino richieste non allineate con lo scopo dichiarato e attivino un rifiuto morbido.
 #11.4.3    Livello: 3    Ruolo: D
 Verifica che i controlli basati su policy-as-code blocchino la ridistribuzione dei modelli verso nuovi domini senza una revisione DPIA.
 #11.4.4    Livello: 3    Ruolo: V
 Verificare che le prove di tracciabilità formale dimostrino che ogni ciclo di vita dei dati personali rimanga entro l'ambito consentito.

---

### 11.5 Gestione del consenso e tracciamento della base-giuridica

 #11.5.1    Livello: 1    Ruolo: D/V
 Verifica che una Piattaforma di Gestione del Consenso (CMP) registri lo stato di consenso esplicito, le finalità e il periodo di conservazione per ciascun interessato.
 #11.5.2    Livello: 2    Ruolo: D
 Verifica che le API espongano token di consenso; i modelli devono validare l'ambito del token prima dell'inferenza.
 #11.5.3    Livello: 2    Ruolo: D/V
 Verifica che il consenso negato o revocato interrompa le pipeline di elaborazione entro 24 ore.

---

### 11.6 Apprendimento Federato con Controlli della Privacy

 #11.6.1    Livello: 1    Ruolo: D
 Verifica che gli aggiornamenti dei client utilizzino l'aggiunta di rumore di privacy differenziale locale prima dell'aggregazione.
 #11.6.2    Livello: 2    Ruolo: D/V
 Verifica che le metriche di addestramento siano protette tramite privacy differenziale e non rivelino mai la perdita di un singolo cliente.
 #11.6.3    Livello: 2    Ruolo: V
 Verifica che l'aggregazione resistente all'avvelenamento (ad es., Krum/Trimmed-Mean) sia abilitata.
 #11.6.4    Livello: 3    Ruolo: V
 Verifica che le prove formali dimostrino un budget ε complessivo con una perdita di utilità inferiore a 5.

---

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

## Monitoraggio, registrazione e rilevamento di anomalie per C12

### Obiettivo di controllo

Questa sezione definisce i requisiti per fornire visibilità in tempo reale e forense su ciò che il modello e gli altri componenti di IA vedono, fanno e restituiscono, affinché le minacce possano essere rilevate, priorizzate nel triage e da cui apprendere.

### C12.1 Registrazione di richieste e risposte

 #12.1.1    Livello: 1    Ruolo: D/V
 Verifica che tutti i prompt dell'utente e le risposte del modello siano registrati con metadati appropriati (ad es. marcatempo, ID utente, ID sessione, versione del modello).
 #12.1.2    Livello: 1    Ruolo: D/V
 Verifica che i log siano archiviati in repository sicuri e protetti con controlli di accesso, politiche di conservazione adeguate e procedure di backup.
 #12.1.3    Livello: 1    Ruolo: D/V
 Verifica che i sistemi di archiviazione dei log implementino la crittografia a riposo e in transito per proteggere le informazioni sensibili contenute nei log.
 #12.1.4    Livello: 1    Ruolo: D/V
 Verifica che i dati sensibili presenti in prompt e output vengano automaticamente redatti o mascherati prima di essere registrati nei log, con regole di redazione configurabili per PII, credenziali e informazioni proprietarie.
 #12.1.5    Livello: 2    Ruolo: D/V
 Verificare che le decisioni di policy e le azioni di filtraggio di sicurezza siano registrate con dettagli sufficienti per consentire l'audit e il debugging dei sistemi di moderazione dei contenuti.
 #12.1.6    Livello: 2    Ruolo: D/V
 Verifica che l'integrità del registro sia protetta, ad es. mediante firme crittografiche o archiviazione in scrittura sola.

---

### C12.2 Rilevamento degli abusi e allerta

 #12.2.1    Livello: 1    Ruolo: D/V
 Verifica che il sistema rilevi e segnali i noti schemi di jailbreak, i tentativi di iniezione di prompt e gli input ostili utilizzando il rilevamento basato su firme.
 #12.2.2    Livello: 1    Ruolo: D/V
 Verificare che il sistema si integri con le piattaforme SIEM esistenti utilizzando formati di log standard e protocolli.
 #12.2.3    Livello: 2    Ruolo: D/V
 Verifica che gli eventi di sicurezza arricchiti includano contesto specifico dell'IA, come identificatori del modello, punteggi di confidenza e decisioni del filtro di sicurezza.
 #12.2.4    Livello: 2    Ruolo: D/V
 Verifica che il rilevamento delle anomalie comportamentali identifichi modelli di conversazione insoliti, un numero eccessivo di tentativi di riprova o comportamenti di sondaggio sistematici.
 #12.2.5    Livello: 2    Ruolo: D/V
 Verifica che i meccanismi di allerta in tempo reale notifichino ai team di sicurezza quando vengano rilevate potenziali violazioni delle politiche o tentativi di attacco.
 #12.2.6    Livello: 2    Ruolo: D/V
 Verifica che siano incluse regole personalizzate per rilevare schemi di minaccia specifici dell'IA, inclusi tentativi di jailbreak coordinati, campagne di iniezione di prompt e attacchi di estrazione del modello.
 #12.2.7    Livello: 3    Ruolo: D/V
 Verifica che i flussi di lavoro di risposta automatizzata agli incidenti possano isolare modelli compromessi, bloccare utenti malevoli e gestire l'escalation di eventi di sicurezza critici.

---

### C12.3 Rilevamento della deriva del modello

 #12.3.1    Livello: 1    Ruolo: D/V
 Verifica che il sistema tenga traccia di metriche di performance di base quali accuratezza, punteggi di confidenza, latenza e tassi di errore tra le versioni del modello e i periodi di tempo.
 #12.3.2    Livello: 2    Ruolo: D/V
 Verificare che gli avvisi automatici si attivino quando le metriche di prestazione superano le soglie di degrado predefinite o si discostano significativamente dalle linee di base.
 #12.3.3    Livello: 2    Ruolo: D/V
 Verifica che i monitor di rilevamento delle allucinazioni identifichino e segnalino gli esempi in cui gli output del modello contengono informazioni errate dal punto di vista fattuale, incoerenti o fabbricate.

---

### C12.4 Telemetria delle Prestazioni e del Comportamento

 #12.4.1    Livello: 1    Ruolo: D/V
 Verifichi che le metriche operative, tra cui la latenza delle richieste, il consumo di token, l'uso della memoria e il throughput, siano raccolte e monitorate continuamente.
 #12.4.2    Livello: 1    Ruolo: D/V
 Verifica che i tassi di successo e di fallimento siano tracciati con la categorizzazione dei tipi di errore e delle loro cause principali.
 #12.4.3    Livello: 2    Ruolo: D/V
 Verificare che il monitoraggio dell'utilizzo delle risorse includa l'utilizzo di GPU/CPU, il consumo di memoria e i requisiti di archiviazione, con avvisi in caso di superamento delle soglie.

---

### C12.5 Pianificazione e Esecuzione della Risposta agli Incidenti di IA

 #12.5.1    Livello: 1    Ruolo: D/V
 Verifica che i piani di risposta agli incidenti affrontino in modo specifico gli eventi di sicurezza correlati all'IA, tra cui la compromissione del modello, l'avvelenamento dei dati e gli attacchi avversariali.
 #12.5.2    Livello: 2    Ruolo: D/V
 Verifica che i team di risposta agli incidenti abbiano accesso a strumenti forensi specifici per l'IA e competenze per indagare sul comportamento dei modelli e sui vettori di attacco.
 #12.5.3    Livello: 3    Ruolo: D/V
 Verificare che l'analisi post-incidente includa considerazioni sul riaddestramento del modello, aggiornamenti dei filtri di sicurezza e l'integrazione delle lezioni apprese nei controlli di sicurezza.

---

### C12.5 Rilevamento della degradazione delle prestazioni dell'Intelligenza Artificiale

Monitora e rileva la degradazione delle prestazioni e della qualità del modello di IA nel tempo.

 #12.5.1    Livello: 1    Ruolo: D/V
 Verificare che l'accuratezza del modello, la precisione, il richiamo e i punteggi F1 siano monitorati costantemente e confrontati con soglie di riferimento.
 #12.5.2    Livello: 1    Ruolo: D/V
 Verifica che il rilevamento della deriva dei dati monitori i cambiamenti della distribuzione degli input che potrebbero influire sulle prestazioni del modello.
 #12.5.3    Livello: 2    Ruolo: D/V
 Verifica che il rilevamento del drift concettuale identifichi i cambiamenti nella relazione tra input e output attesi.
 #12.5.4    Livello: 2    Ruolo: D/V
 Verifica che il degrado delle prestazioni inneschi avvisi automatici e avvii flussi di lavoro di riaddestramento o sostituzione del modello.
 #12.5.5    Livello: 3    Ruolo: V
 Verificare che l'analisi della causa principale del degrado possa correlare i cali delle prestazioni con modifiche ai dati, problemi di infrastruttura o fattori esterni.

---

### C12.6 Visualizzazione DAG e Sicurezza del Flusso di Lavoro

Proteggere i sistemi di visualizzazione del flusso di lavoro dalle fughe di informazioni e dagli attacchi di manomissione.

 #12.6.1    Livello: 1    Ruolo: D/V
 Verificare che i dati di visualizzazione del DAG siano sanificati per rimuovere informazioni sensibili prima dell'archiviazione o della trasmissione.
 #12.6.2    Livello: 1    Ruolo: D/V
 Verificare che i controlli di accesso alla visualizzazione del flusso di lavoro assicurino che solo gli utenti autorizzati possano visualizzare i percorsi decisionali degli agenti e le tracce di ragionamento.
 #12.6.3    Livello: 2    Ruolo: D/V
 Verifica che l'integrità dei dati DAG sia protetta mediante firme criptografiche e meccanismi di archiviazione a prova di manomissione.
 #12.6.4    Livello: 2    Ruolo: D/V
 Verificare che i sistemi di visualizzazione dei flussi di lavoro implementino la validazione dell'input per prevenire attacchi di iniezione attraverso dati di nodi o archi appositamente costruiti.
 #12.6.5    Livello: 3    Ruolo: D/V
 Verificare che gli aggiornamenti in tempo reale dei DAG siano limitati in frequenza e validati per prevenire attacchi DoS sui sistemi di visualizzazione.

---

### C12.7 Monitoraggio proattivo del comportamento di sicurezza

Rilevazione e prevenzione delle minacce alla sicurezza attraverso l'analisi proattiva del comportamento degli agenti.

 #12.7.1    Livello: 1    Ruolo: D/V
 Verifica che i comportamenti degli agenti proattivi siano validati per la sicurezza prima dell'esecuzione, con integrazione della valutazione del rischio.
 #12.7.2    Livello: 2    Ruolo: D/V
 Verifica che gli inneschi di iniziativa autonoma includano la valutazione del contesto di sicurezza e la valutazione del panorama delle minacce.
 #12.7.3    Livello: 2    Ruolo: D/V
 Verifica che i modelli di comportamento proattivo siano analizzati per potenziali implicazioni di sicurezza e conseguenze non intenzionali.
 #12.7.4    Livello: 3    Ruolo: D/V
 Verificare che le azioni proattive critiche per la sicurezza richiedano catene di approvazione esplicite con registri di audit.
 #12.7.5    Livello: 3    Ruolo: D/V
 Verifica che il rilevamento delle anomalie comportamentali identifichi deviazioni nei modelli di comportamento degli agenti proattivi che potrebbero indicare una compromissione.

---

### Riferimenti

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13 Supervisione Umana, Responsabilità e Governance

### Obiettivo di controllo

Questo capitolo fornisce requisiti per mantenere la supervisione umana e chiare catene di responsabilità nei sistemi di IA, garantendo spiegabilità, trasparenza e una gestione etica durante l'intero ciclo di vita dell'IA.

---

### C13.1 Interruttore di spegnimento e meccanismi di sovrascrittura

Fornire percorsi di spegnimento o di rollback quando si osserva un comportamento non sicuro del sistema di intelligenza artificiale.

 #13.1.1    Livello: 1    Ruolo: D/V
 Verifica che esista un meccanismo di arresto manuale in grado di interrompere immediatamente l'inferenza e gli output del modello di IA.
 #13.1.2    Livello: 1    Ruolo: D
 Verifica che i controlli di override siano accessibili solo al personale autorizzato.
 #13.1.3    Livello: 3    Ruolo: D/V
 Verificare che le procedure di rollback possano ripristinare le versioni precedenti del modello o operazioni in modalità sicura.
 #13.1.4    Livello: 3    Ruolo: V
 Verificare che i meccanismi di override siano testati regolarmente.

---

### C13.2 Punti di controllo decisionali con coinvolgimento umano

Richiedere approvazioni umane quando gli importi in gioco superano soglie di rischio predefinite.

 #13.2.1    Livello: 1    Ruolo: D/V
 Verificare che le decisioni dell'IA ad alto rischio richiedano l'approvazione esplicita da parte di un essere umano prima dell'esecuzione.
 #13.2.2    Livello: 1    Ruolo: D
 Verifica che le soglie di rischio siano chiaramente definite e attivino automaticamente i flussi di lavoro di revisione umana.
 #13.2.3    Livello: 2    Ruolo: D
 Verifichi che le decisioni sensibili al tempo abbiano procedure di fallback quando l'approvazione umana non possa essere ottenuta entro i tempi previsti.
 #13.2.4    Livello: 3    Ruolo: D/V
 Verifica che le procedure di escalation definiscano livelli di autorità chiari per diversi tipi di decisione o categorie di rischio, se applicabili.

---

### C13.3 Catena di responsabilità e auditabilità

Registrare le azioni dell'operatore e le decisioni del modello.

 #13.3.1    Livello: 1    Ruolo: D/V
 Verifica che tutte le decisioni del sistema di IA e gli interventi umani siano registrati con marcature temporali, identità degli utenti e motivazione della decisione.
 #13.3.2    Livello: 2    Ruolo: D
 Verifica che i registri di audit non possano essere manomessi e includano meccanismi di verifica dell'integrità.

---

### C13.4 Tecniche di Explainable-AI

Importanza delle caratteristiche superficiali, spiegazioni controfattuali e spiegazioni locali.

 #13.4.1    Livello: 1    Ruolo: D/V
 Verifica che i sistemi di IA forniscano spiegazioni di base per le loro decisioni in formato leggibile dall'uomo.
 #13.4.2    Livello: 2    Ruolo: V
 Verificare che la qualità delle spiegazioni sia validata tramite studi di valutazione umana e metriche.
 #13.4.3    Livello: 3    Ruolo: D/V
 Verifica che siano disponibili i punteggi di importanza delle caratteristiche o i metodi di attribuzione (SHAP, LIME, ecc.) per decisioni critiche.
 #13.4.4    Livello: 3    Ruolo: V
 Verificare che le spiegazioni contrafattuali mostrino come gli input potrebbero essere modificati per cambiare gli esiti, se applicabile al caso d'uso e al dominio.

---

### C13.5 Schede dei modelli e divulgazioni sull'uso

Mantenere le schede del modello per l'uso previsto, le metriche delle prestazioni e le considerazioni etiche.

 #13.5.1    Livello: 1    Ruolo: D
 Verifica che le schede del modello documentino i casi d'uso previsti, le limitazioni e le modalità di guasto note.
 #13.5.2    Livello: 1    Ruolo: D/V
 Verificare che le metriche di prestazione relative ai diversi casi d'uso applicabili siano rese note.
 #13.5.3    Livello: 2    Ruolo: D
 Verifica che le considerazioni etiche, le valutazioni dei bias, le valutazioni di equità, le caratteristiche dei dati di addestramento e le limitazioni note dei dati di addestramento siano documentate e aggiornate regolarmente.
 #13.5.4    Livello: 2    Ruolo: D/V
 Verifica che le schede del modello siano versionate e mantenute durante l'intero ciclo di vita del modello, con tracciamento delle modifiche.

---

### C13.6 Quantificazione dell'incertezza

Propaga i punteggi di confidenza o le misure di entropia nelle risposte.

 #13.6.1    Livello: 1    Ruolo: D
 Verifica che i sistemi di IA forniscano punteggi di confidenza o misure di incertezza insieme ai loro output.
 #13.6.2    Livello: 2    Ruolo: D/V
 Verifica che le soglie di incertezza attivino una revisione umana aggiuntiva o percorsi decisionali alternativi.
 #13.6.3    Livello: 2    Ruolo: V
 Verificare che i metodi di quantificazione dell'incertezza siano calibrati e validati rispetto ai dati di verità a terra.
 #13.6.4    Livello: 3    Ruolo: D/V
 Verifica che la propagazione dell'incertezza sia mantenuta attraverso flussi di lavoro di IA a più passaggi.

---

### C13.7 Rapporti di trasparenza rivolti agli utenti

Fornire aggiornamenti periodici su incidenti, deriva e utilizzo dei dati.

 #13.7.1    Livello: 1    Ruolo: D/V
 Verifica che le politiche sull'utilizzo dei dati e le pratiche di gestione del consenso degli utenti siano comunicate chiaramente alle parti interessate.
 #13.7.2    Livello: 2    Ruolo: D/V
 Verifica che siano condotte valutazioni sull'impatto dell'IA e che i risultati siano inclusi nel reporting.
 #13.7.3    Livello: 2    Ruolo: D/V
 Verifica che i rapporti di trasparenza pubblicati regolarmente riportino gli incidenti legati all'IA e le metriche operative con un livello di dettaglio ragionevole.

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
GDPR — Article 5 "Transparency Principle" (Regulation (EU) 2016/679)
Human Oversight under Article 14 of the EU AI Act (Fink, 2025)

## Appendice A: Glossario

Questo glossario completo fornisce definizioni dei principali termini di IA, ML e sicurezza utilizzati in AISVS per garantire chiarezza e una comprensione comune.

Esempio avversario: un input appositamente progettato per indurre un modello di IA a commettere un errore, spesso aggiungendo perturbazioni sottili impercettibili agli esseri umani.
​
Robustezza avversaria – La robustezza avversaria nell'IA si riferisce alla capacità di un modello di mantenere le proprie prestazioni e di resistere all'inganno o alla manipolazione da input intenzionalmente creati, maliziosi, progettati per causare errori.
​
Agente – Gli agenti IA sono sistemi software che utilizzano l'IA per perseguire obiettivi e completare compiti per conto degli utenti. Essi mostrano ragionamento, pianificazione e memoria e hanno un livello di autonomia per prendere decisioni, imparare e adattarsi.
​
IA agentiva: sistemi di intelligenza artificiale che possono operare con un certo grado di autonomia per raggiungere obiettivi, spesso prendendo decisioni e intraprendendo azioni senza l'intervento diretto dell'essere umano.
​
Controllo di accesso basato su attributi (ABAC): un paradigma di controllo degli accessi in cui le decisioni di autorizzazione si basano sugli attributi dell'utente, della risorsa, dell'azione e dell'ambiente, valutati al momento dell'interrogazione.
​
Attacco con backdoor: un tipo di attacco di avvelenamento dei dati in cui il modello viene addestrato a rispondere in modo specifico a determinati inneschi, comportandosi altrimenti normalmente.
​
Pregiudizio: Errori sistematici negli output dei modelli di IA che possono portare a esiti ingiusti o discriminatori per determinati gruppi o in contesti specifici.
​
Sfruttamento dei bias: una tecnica di attacco che sfrutta bias noti nei modelli di IA per manipolare gli output o gli esiti.
​
Cedar: linguaggio di policy di Amazon e motore per autorizzazioni a granularità fine utilizzati per implementare ABAC per sistemi di IA.
​
Catena di pensiero: una tecnica per migliorare il ragionamento nei modelli linguistici generando passaggi di ragionamento intermedi prima di produrre una risposta finale.
​
Interruttori di circuito: Meccanismi che interrompono automaticamente le operazioni dei sistemi di IA quando si superano soglie di rischio specifiche.
​
Fuga di dati: Esposizione non intenzionale di informazioni sensibili tramite gli output o il comportamento del modello di IA.
​
Avvelenamento dei dati: la corruzione deliberata dei dati di addestramento per compromettere l'integrità del modello, spesso per installare backdoor o degradare le prestazioni.
​
Privacy differenziale – La privacy differenziale è un quadro matematicamente rigoroso per rilasciare informazioni statistiche sugli insiemi di dati, proteggendo la privacy degli individui. Consente al detentore dei dati di condividere schemi aggregati del gruppo, limitando al contempo le informazioni che vengono rivelate su singoli individui.
​
Embeddings: Rappresentazioni vettoriali dense dei dati (testo, immagini, ecc.) che catturano il significato semantico in uno spazio ad alta dimensione.
​
Spiegabilità – La spiegabilità nell'IA è la capacità di un sistema di IA di fornire ragioni comprensibili agli esseri umani per le sue decisioni e predizioni, offrendo intuizioni sul suo funzionamento interno.
​
Intelligenza artificiale spiegabile (XAI): sistemi di IA progettati per fornire spiegazioni comprensibili agli esseri umani riguardo alle loro decisioni e ai loro comportamenti, attraverso varie tecniche e quadri di riferimento.
​
Apprendimento Federato: un approccio di apprendimento automatico in cui i modelli vengono addestrati su più dispositivi decentralizzati che ospitano campioni di dati locali, senza scambiare i dati stessi.
​
Barriere di sicurezza: vincoli implementati per impedire ai sistemi di IA di produrre output dannosi, pregiudizievoli o altrimenti indesiderati.
​
Allucinazione – Un'allucinazione dell'IA si riferisce a un fenomeno in cui un modello di IA genera informazioni errate o fuorvianti che non si basano sui suoi dati di addestramento o sulla realtà fattuale.
​
Umano nel ciclo (HITL): Sistemi progettati per richiedere supervisione, verifica o intervento umano in punti decisionali cruciali.
​
Infrastruttura come codice (IaC): gestione e provisioning dell'infrastruttura tramite codice anziché processi manuali, consentendo la scansione di sicurezza e implementazioni coerenti.
​
Jailbreak: Tecniche usate per aggirare le barriere di sicurezza nei sistemi di IA, in particolare nei grandi modelli di linguaggio, per produrre contenuti vietati.
​
Principio del minimo privilegio: il principio di sicurezza che prevede di concedere solo i diritti di accesso strettamente necessari agli utenti e ai processi.
​
LIME (Spiegazioni Locali Interpretabili Indipendenti dal Modello): Una tecnica per spiegare le predizioni di qualsiasi classificatore di apprendimento automatico approssimandolo localmente con un modello interpretabile.
​
Attacco di inferenza di appartenenza: un attacco che mira a determinare se un determinato dato sia stato utilizzato per addestrare un modello di apprendimento automatico.
​
MITRE ATLAS: Paesaggio delle minacce avversarie per i sistemi di intelligenza artificiale; una base di conoscenza delle tattiche e delle tecniche avversarie contro i sistemi di IA.
​
Scheda del modello – Una scheda del modello è un documento che fornisce informazioni standardizzate sulle prestazioni di un modello di IA, sulle sue limitazioni, sugli usi previsti e sulle considerazioni etiche, al fine di promuovere la trasparenza e lo sviluppo responsabile dell'IA.
​
Estrazione del modello: un attacco in cui un avversario interroga ripetutamente un modello bersaglio per creare una copia funzionalmente simile senza autorizzazione.
​
Inversione del modello: un attacco che tenta di ricostruire i dati di addestramento analizzando gli output del modello.
​
Gestione del ciclo di vita del modello – La gestione del ciclo di vita dei modelli di IA è il processo di supervisione di tutte le fasi dell’esistenza di un modello di IA, tra cui progettazione, sviluppo, messa in produzione, monitoraggio, manutenzione e l’eventuale ritiro, al fine di garantire che rimanga efficace e allineato agli obiettivi.
​
Avvelenamento del modello: introdurre vulnerabilità o backdoor direttamente in un modello durante il processo di addestramento.
​
Furto del modello: Estrarre una copia o un'approssimazione di un modello proprietario tramite richieste ripetute.
​
Sistema multiagente: un sistema composto da più agenti IA interagenti, ciascuno con capacità e obiettivi potenzialmente differenti.
​
OPA (Open Policy Agent): un motore di policy open-source che consente l'applicazione uniforme delle politiche in tutto lo stack.
​
Privacy-Preserving Machine Learning (PPML): Tecniche e metodi per addestrare e distribuire modelli ML, proteggendo la privacy dei dati di addestramento.
​
Prompt Injection: un attacco in cui istruzioni malevole sono inserite negli input per sovrascrivere il comportamento previsto dal modello.
​
RAG (Retrieval-Augmented Generation): una tecnica che migliora i grandi modelli di linguaggio recuperando informazioni rilevanti da fonti di conoscenza esterne prima di generare una risposta.
​
Red-Teaming: La pratica di testare attivamente i sistemi di IA simulando attacchi avversariali per identificare vulnerabilità.
​
SBOM (Distinta dei materiali del software): Un registro formale contenente i dettagli e le relazioni della catena di fornitura di vari componenti utilizzati per costruire software o modelli di IA.
​
SHAP (SHapley Additive exPlanations): un approccio teorico dei giochi per spiegare l'output di qualsiasi modello di apprendimento automatico calcolando il contributo di ciascuna caratteristica alla previsione.
​
Attacco alla catena di fornitura: compromettere un sistema prendendo di mira elementi meno sicuri della sua catena di fornitura, come librerie di terze parti, set di dati o modelli preaddestrati.
​
Apprendimento trasferibile: Una tecnica in cui un modello sviluppato per un compito viene riutilizzato come punto di partenza per un modello su un secondo compito.
​
Database vettoriale: un database specializzato progettato per archiviare vettori ad alta dimensione (embedding) e per eseguire ricerche di similarità efficienti.
​
Scansione delle vulnerabilità: Strumenti automatizzati che identificano vulnerabilità di sicurezza note nei componenti software, inclusi framework di IA e dipendenze.
​
Marcatura ad acqua digitale: Tecniche per inserire marcatori impercettibili nel contenuto generato dall'IA per tracciare la sua origine o rilevare se è stata generata dall'IA.
​
Vulnerabilità zero-day: una vulnerabilità precedentemente sconosciuta che gli aggressori possono sfruttare prima che gli sviluppatori creino e distribuiscano una patch.

## Appendice B: Riferimenti

### TODO

## Appendice C: Governance della sicurezza dell'IA e Documentazione

### Obiettivo

Questa appendice fornisce i requisiti fondamentali per stabilire strutture organizzative, politiche e processi per governare la sicurezza dell'IA lungo l'intero ciclo di vita del sistema.

---

### AC.1 Adozione del Quadro di Gestione del Rischio dell'IA

Fornire un quadro formale per identificare, valutare e mitigare i rischi specifici dell'IA durante l'intero ciclo di vita del sistema.

 #AC.1.1    Livello: 1    Ruolo: D/V
 Verifica che una metodologia di valutazione del rischio specifica per l'IA sia documentata e implementata.
 #AC.1.2    Livello: 2    Ruolo: D
 Verificare che le valutazioni del rischio siano condotte in punti chiave del ciclo di vita dell'IA e prima di cambiamenti significativi.
 #AC.1.3    Livello: 3    Ruolo: D/V
 Verifica che il quadro di gestione del rischio sia allineato agli standard stabiliti (ad es., NIST AI RMF).

---

### AC.2 Politiche e Procedure di Sicurezza dell'Intelligenza Artificiale

Definire e far rispettare standard organizzativi per lo sviluppo, l'implementazione e l'operatività sicuri dell'IA.

 #AC.2.1    Livello: 1    Ruolo: D/V
 Verifica che esistano politiche di sicurezza dell'IA documentate.
 #AC.2.2    Livello: 2    Ruolo: D
 Verifica che le politiche siano riviste e aggiornate almeno annualmente e dopo cambiamenti significativi del panorama delle minacce.
 #AC.2.3    Livello: 3    Ruolo: D/V
 Verifica che le politiche coprano tutte le categorie AISVS e i requisiti normativi applicabili.

---

### AC.3 Ruoli e Responsabilità per la Sicurezza dell'IA

Stabilire una chiara responsabilità per la sicurezza dell'IA in tutta l'organizzazione.

 #AC.3.1    Livello: 1    Ruolo: D/V
 Verifica che i ruoli e le responsabilità di sicurezza dell'IA siano documentati.
 #AC.3.2    Livello: 2    Ruolo: D
 Verificare che i responsabili dispongano di competenze di sicurezza adeguate.
 #AC.3.3    Livello: 3    Ruolo: D/V
 Verifica che sia istituito un comitato etico per l'IA o un consiglio di governance per i sistemi di IA ad alto rischio.

---

### AC.4 Applicazione delle linee guida etiche per l'IA

Garantire che i sistemi di IA operino secondo principi etici stabiliti.

 #AC.4.1    Livello: 1    Ruolo: D/V
 Verifica che esistano linee guida etiche per lo sviluppo e l'impiego dell'IA.
 #AC.4.2    Livello: 2    Ruolo: D
 Verifica che siano presenti meccanismi per rilevare e segnalare violazioni etiche.
 #AC.4.3    Livello: 3    Ruolo: D/V
 Verificare che vengano eseguite revisioni etiche regolari dei sistemi di IA messi in produzione.

---

### AC.5 Monitoraggio della conformità normativa dell'IA

Mantieni la consapevolezza e la conformità alle normative sull'IA in evoluzione.

 #AC.5.1    Livello: 1    Ruolo: D/V
 Verificare che esistano processi per identificare le normative applicabili all'IA.
 #AC.5.2    Livello: 2    Ruolo: D
 Verifica che la conformità a tutti i requisiti normativi sia valutata.
 #AC.5.3    Livello: 3    Ruolo: D/V
 Verificare che le modifiche normative inneschino revisioni e aggiornamenti tempestivi ai sistemi di IA.

### AC.6 Governance dei dati di addestramento, documentazione e processo

 #1.1.2    Livello: 1    Ruolo: D/V
 Verifica che siano ammessi solo set di dati verificati per qualità, rappresentatività, approvvigionamento etico e conformità alle licenze, riducendo i rischi di avvelenamento dei dati, bias incorporato e violazione della proprietà intellettuale.
 #1.1.5    Livello: 2    Ruolo: D/V
 Verificare che la qualità dell'etichettatura/annotazione sia garantita mediante controlli incrociati tra i revisori o mediante consenso.
 #1.1.6    Livello: 2    Ruolo: D/V
 Verificare che le "data cards" o "datasheets for datasets" siano mantenute per i dataset di addestramento significativi, descrivendo caratteristiche, motivazioni, composizione, processi di raccolta, preprocessamento e usi raccomandati/da evitare.
 #1.3.2    Livello: 2    Ruolo: D/V
 Verifica che i bias identificati siano mitigati mediante strategie documentate quali ri-bilanciamento, augmentazione mirata dei dati, aggiustamenti algoritmici (ad es. tecniche di pre-processing, in-processing, post-processing) o rivalutazione dei pesi, e che l'impatto della mitigazione su entrambe le metriche di fairness e sulle prestazioni complessive del modello sia valutato.
 #1.3.3    Livello: 2    Ruolo: D/V
 Verifichi che le metriche di equità post-addestramento siano valutate e documentate.
 #1.3.4    Livello: 3    Ruolo: D/V
 Verifica che una policy di gestione del bias del ciclo di vita assegni i responsabili e la frequenza di revisione.
 #1.4.1    Livello: 2    Ruolo: D/V
 Verificare che la qualità dell'etichettatura/annotazione sia garantita tramite linee guida chiare, controlli incrociati tra revisori, meccanismi di consenso (ad es. monitoraggio dell'accordo tra annotatori) e processi definiti per risolvere le discrepanze.
 #1.4.4    Livello: 3    Ruolo: D/V
 Verificare che le etichette critiche per la sicurezza, la protezione o l'equità (ad es. identificare contenuti tossici, risultati medici critici) ricevano una revisione indipendente obbligatoria in duplice controllo o una verifica robusta equivalente.
 #1.4.6    Livello: 2    Ruolo: D/V
 Verifica che le guide e le istruzioni per l'etichettatura dei dati siano esaustive, con controllo di versione e revisionate tra pari.
 #1.4.6    Livello: 2    Ruolo: D/V
 Verificare che gli schemi dei dati per le etichette siano chiaramente definiti e versionati.
 #1.3.1    Livello: 1    Ruolo: D/V
 Verificare che i dataset siano profilati per squilibrio rappresentazionale e bias potenziali rispetto a attributi legalmente protetti (ad esempio razza, genere, età) e ad altre caratteristiche eticamente sensibili rilevanti per il dominio di applicazione del modello (ad esempio stato socio-economico, posizione geografica).
 #1.5.3    Livello: 2    Ruolo: V
 Verificare che i controlli manuali a campione eseguiti da esperti del dominio coprano un campione statisticamente significativo (ad es., ≥1% o 1,000 campioni, a seconda di quale sia maggiore, o come determinato dalla valutazione del rischio) per identificare problemi di qualità sottili che non sono stati rilevati dall'automazione.
 #1.8.4    Livello: 2    Ruolo: D/V
 Verificare che i flussi di etichettatura esternalizzati o affidati al crowdsourcing includano salvaguardie tecniche e procedurali volte a garantire la riservatezza e l'integrità dei dati, la qualità delle etichette e a prevenire la fuga di dati.
 #1.5.4    Livello: 2    Ruolo: D/V
 Verificare che le azioni correttive siano aggiunte ai registri di provenienza.
 #1.6.2    Livello: 2    Ruolo: D/V
 Verifica che i campioni contrassegnati attivino una revisione manuale prima dell'addestramento.
 #1.6.3    Livello: 2    Ruolo: V
 Verifica che i risultati alimentino il dossier di sicurezza del modello e forniscano informazioni sull'intelligence delle minacce in corso.
 #1.6.4    Livello: 3    Ruolo: D/V
 Verifica che la logica di rilevamento sia aggiornata con le nuove informazioni sulle minacce.
 #1.6.5    Livello: 3    Ruolo: D/V
 Verifica che le pipeline di apprendimento online monitorino la deriva della distribuzione.
 #1.7.1    Livello: 1    Ruolo: D/V
 Verificare che i flussi di lavoro per l'eliminazione dei dati di addestramento eliminino i dati primari e derivati e che venga valutato l'impatto sul modello, e che l'impatto sui modelli interessati sia valutato e, se necessario, affrontato (ad es., mediante riaddestramento o ricalibrazione).
 #1.7.2    Livello: 2    Ruolo: D
 Verificare che esistano meccanismi per tracciare e rispettare l'ambito e lo stato del consenso dell'utente (inclusa la revoca) per i dati utilizzati nell'addestramento, e che il consenso sia convalidato prima che i dati vengano incorporati in nuovi processi di addestramento o in aggiornamenti significativi del modello.
 #1.7.3    Livello: 2    Ruolo: V
 Verifica che i flussi di lavoro siano testati annualmente e registrati.
 #1.8.1    Livello: 2    Ruolo: D/V
 Verificare che i fornitori di dati di terze parti, inclusi i fornitori di modelli pre-addestrati e set di dati esterni, siano sottoposti a due diligence in materia di sicurezza, privacy, approvvigionamento etico e qualità dei dati prima che i loro dati o modelli siano integrati.
 #1.8.2    Livello: 1    Ruolo: D
 Verifica che i trasferimenti esterni utilizzino TLS/autenticazione e controlli di integrità.
 #1.8.3    Livello: 2    Ruolo: D/V
 Verificare che le fonti di dati ad alto rischio (ad es. set di dati open source con provenienza sconosciuta, fornitori non verificati) siano sottoposte a una verifica rafforzata, come analisi in sandbox, controlli esaustivi di qualità e di bias, e rilevamento mirato di avvelenamento dei dati, prima dell’uso in applicazioni sensibili.
 #1.8.4    Livello: 3    Ruolo: D/V
 Verificate che i modelli pre-addestrati ottenuti da terze parti siano valutati per bias incorporati, potenziali backdoor, l'integrità della loro architettura e la provenienza dei loro dati di addestramento originali prima di effettuare il fine-tuning o la messa in produzione.
 #1.5.3    Livello: 2    Ruolo: D/V
 Verificare che, qualora venga utilizzato l'addestramento avversario, la generazione, la gestione e il versionamento dei dataset avversari siano adeguatamente documentati e controllati.
 #1.5.3    Livello: 3    Ruolo: D/V
 Verificare che l'impatto dell'addestramento alla robustezza avversaria sulle prestazioni del modello (sia su input puliti sia su input avversari) e sulle metriche di equità sia valutato, documentato e monitorato.
 #1.5.4    Livello: 3    Ruolo: D/V
 Verificare che le strategie di addestramento avversario e di robustezza siano periodicamente riviste e aggiornate per contrastare le tecniche di attacco avversario in evoluzione.
 #1.4.2    Livello: 2    Ruolo: D/V
 Verificare che i dataset falliti siano messi in quarantena con tracce di audit.
 #1.4.3    Livello: 2    Ruolo: D/V
 Verifica che i controlli di qualità blocchino i dataset non conformi, a meno che non vengano approvate eccezioni.
 #1.11.2    Livello: 2    Ruolo: D/V
 Verificare che il processo di generazione, i parametri e l'uso previsto dei dati sintetici siano documentati.
 #1.11.3    Livello: 2    Ruolo: D/V
 Verificare che i dati sintetici siano soggetti a valutazione del rischio per pregiudizi, fughe di dati personali e problemi di rappresentazione prima dell'uso nell'addestramento.
 #1.12.3    Livello: 2    Ruolo: D/V
 Verificare che vengano generati avvisi per eventi di accesso sospetti e che vengano indagati tempestivamente.
 #1.13.1    Livello: 1    Ruolo: D/V
 Verifica che i periodi di conservazione espliciti siano definiti per tutti i dataset di addestramento.
 #1.13.2    Livello: 2    Ruolo: D/V
 Verifica che i dataset scadano automaticamente, vengano eliminati o siano sottoposti a revisione per l'eliminazione al termine del loro ciclo di vita.
 #1.13.3    Livello: 2    Ruolo: D/V
 Verificare che le azioni di conservazione e eliminazione siano registrate e auditabili.
 #1.14.1    Livello: 2    Ruolo: D/V
 Verificare che i requisiti di localizzazione dei dati e di trasferimento transfrontaliero siano identificati e applicati per tutti i set di dati.
 #1.14.2    Livello: 2    Ruolo: D/V
 Verificare che le normative specifiche del settore (ad es. sanità, finanza) siano identificate e affrontate nella gestione dei dati.
 #1.14.3    Livello: 2    Ruolo: D/V
 Verificare che la conformità alle leggi rilevanti sulla protezione dei dati (ad es. GDPR, CCPA) sia documentata e revisionata regolarmente.
 #1.16.1    Livello: 2    Ruolo: D/V
 Verificare che esistano meccanismi in grado di rispondere alle richieste del soggetto interessato relative all'accesso, alla rettifica, alla limitazione o all'opposizione al trattamento.
 #1.16.2    Livello: 2    Ruolo: D/V
 Verificare che le richieste siano registrate, tracciate e evase entro i termini previsti dalla legge.
 #1.16.3    Livello: 2    Ruolo: D/V
 Verifica che i processi relativi ai diritti degli interessati siano testati e riesaminati regolarmente per verificarne l'efficacia.
 #1.17.1    Livello: 2    Ruolo: D/V
 Verificare che venga condotta un’analisi d’impatto prima di aggiornare o sostituire una versione del set di dati, che comprenda le prestazioni del modello, l’equità e la conformità.
 #1.17.2    Livello: 2    Ruolo: D/V
 Verifica che i risultati dell'analisi d'impatto siano documentati e revisionati dalle parti interessate rilevanti.
 #1.17.3    Livello: 2    Ruolo: D/V
 Verificare che esistano piani di rollback nel caso in cui le nuove versioni introducano rischi inaccettabili o regressioni.
 #1.18.1    Livello: 2    Ruolo: D/V
 Verifichi che tutto il personale coinvolto nell’annotazione dei dati sia stato sottoposto a controlli dei precedenti e formato nella sicurezza dei dati e nella protezione della privacy.
 #1.18.2    Livello: 2    Ruolo: D/V
 Verifica che tutto il personale di annotazione abbia firmato accordi di riservatezza e di non divulgazione.
 #1.18.3    Livello: 2    Ruolo: D/V
 Verifica che le piattaforme di annotazione dei dati applichino controlli di accesso e monitorino le minacce interne.

#### Riferimenti

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Appendice D: Governance e Verifica della Programmazione Sicura Assistita dall'IA

### Obiettivo

Questo capitolo definisce controlli organizzativi di base per l'uso sicuro ed efficace degli strumenti di programmazione assistiti dall'IA durante lo sviluppo del software, garantendo sicurezza e tracciabilità lungo il ciclo di vita dello sviluppo del software (SDLC).

---

### AD.1 Flusso di lavoro per la programmazione sicura assistita dall'IA

Integra strumenti di IA nel ciclo di vita dello sviluppo software sicuro dell'organizzazione (SSDLC) senza indebolire i cancelli di sicurezza esistenti.

 #AD.1.1    Livello: 1    Ruolo: D/V
 Verifica che un flusso di lavoro documentato descriva quando e come gli strumenti di IA possono generare, rifattorizzare o rivedere il codice.
 #AD.1.2    Livello: 2    Ruolo: D
 Verifica che il flusso di lavoroMappi ciascuna fase del SSDLC (progettazione, implementazione, revisione del codice, test, messa in produzione).
 #AD.1.3    Livello: 3    Ruolo: D/V
 Verifica che le metriche (ad es. densità delle vulnerabilità, tempo medio di rilevamento) siano raccolte sul codice prodotto dall'IA e confrontate con linee di base basate solo su dati umani.

---

### AD.2 Qualificazione degli strumenti di IA e Modellazione delle minacce

Garantire che gli strumenti di codifica basati sull'IA siano valutati in termini di capacità di sicurezza, rischio e impatto della supply‑chain prima dell'adozione.

 #AD.2.1    Livello: 1    Ruolo: D/V
 Verifica che un modello di minaccia per ogni strumento di IA identifichi l'uso improprio, l'inversione del modello, la fuga di dati e i rischi della catena di dipendenze.
 #AD.2.2    Livello: 2    Ruolo: D
 Verifica che le valutazioni degli strumenti includano l'analisi statica/dinamica di eventuali componenti locali e la valutazione dei punti finali SaaS (TLS, autenticazione/autorizzazione, registrazione).
 #AD.2.3    Livello: 3    Ruolo: D/V
 Verificare che le valutazioni seguano un quadro di riferimento riconosciuto e che vengano rieseguite dopo cambiamenti di versione principali.

---

### AD.3 Prompt Sicuro e Gestione del Contesto

Previeni la fuga di segreti, codice proprietario e dati personali durante la creazione di prompt o contesti per modelli di IA.

 #AD.3.1    Livello: 1    Ruolo: D/V
 Verifichi che le linee guida scritte vietino l'invio di segreti, credenziali o dati classificati nei prompt.
 #AD.3.2    Livello: 2    Ruolo: D
 Verifica che i controlli tecnici (redazione client-side, filtri di contesto approvati) rimuovano automaticamente artefatti sensibili.
 #AD.3.3    Livello: 3    Ruolo: D/V
 Verifica che i prompt e le risposte siano tokenizzati, crittografati in transito e a riposo, e che i periodi di conservazione dei dati siano conformi alla policy di classificazione dei dati.

---

### AD.4 Validazione del codice generato dall'IA

Rileva e correggi le vulnerabilità introdotte dall'output dell'IA prima che il codice venga unito o distribuito.

 #AD.4.1    Livello: 1    Ruolo: D/V
 Verifica che il codice generato dall'IA sia sempre soggetto a revisione da parte di un essere umano.
 #AD.4.2    Livello: 2    Ruolo: D
 Verifica che gli scanner automatizzati (SAST/IAST/DAST) vengano eseguiti su ogni pull request contenente codice AI‑generato e blocchino le fusioni in caso di scoperte critiche.
 #AD.4.3    Livello: 3    Ruolo: D/V
 Verifica che fuzzing differenziale o property‑based tests dimostrino comportamenti critici per la sicurezza (ad es. validazione degli input, logica di autorizzazione).

---

### AD.5 Esplicabilità e tracciabilità dei suggerimenti di codice

Fornite ai revisori e agli sviluppatori una visione approfondita del motivo per cui è stata fatta una proposta e di come sia evoluta.

 #AD.5.1    Livello: 1    Ruolo: D/V
 Verifica che le coppie prompt/risposta siano registrate con gli ID di commit.
 #AD.5.2    Livello: 2    Ruolo: D
 Verificare che gli sviluppatori possano rendere disponibili citazioni del modello (frammenti di addestramento, documentazione) a supporto di un suggerimento.
 #AD.5.3    Livello: 3    Ruolo: D/V
 Verificare che i rapporti di spiegabilità siano archiviati insieme agli artefatti di progettazione e citati nelle revisioni di sicurezza, soddisfacendo i principi di tracciabilità ISO/IEC 42001.

---

### AD.6 Feedback continuo e Fine‑Tuning del modello

Migliorare nel tempo le prestazioni di sicurezza del modello, evitando la deriva negativa.

 #AD.6.1    Livello: 1    Ruolo: D/V
 Verificare che gli sviluppatori possano contrassegnare suggerimenti non sicuri o non conformi e che le segnalazioni siano tracciate.
 #AD.6.2    Livello: 2    Ruolo: D
 Verifica che il feedback aggregato informi un fine‑tuning periodico o retrieval‑augmented generation con corpora di codifica‑sicura verificati (ad es. OWASP Cheat Sheets).
 #AD.6.3    Livello: 3    Ruolo: D/V
 Verifica che un sistema di valutazione a ciclo chiuso esegua test di regressione dopo ogni messa a punto; le metriche di sicurezza devono soddisfare o superare i parametri di riferimento precedenti prima della messa in produzione.

---

#### Riferimenti

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Appendice E: Esempi di strumenti e framework

### Obiettivo

Questo capitolo fornisce esempi di strumenti e framework che possono supportare l'implementazione o l'adempimento di un determinato requisito AISVS. Questi non devono essere considerati come raccomandazioni o approvazioni da parte del team AISVS o del progetto OWASP GenAI Security.

---

### AE.1 Governance dei dati di addestramento e gestione dei bias

Strumenti utilizzati per l'analisi dei dati, la governance e la gestione del bias.

 #AE.1.1    Sezione: 1.1
 Strumentazione per l'inventario dei dati: strumenti di gestione dell'inventario dei dati come...
 #AE.1.2    Sezione: 1.2
 Crittografia in transito: usa TLS per applicazioni basate su HTTPS, con strumenti come OpenSSL e Python.`ssl` libreria.

---

### AE.2 Validazione dell'input dell'utente

Strumentazione per gestire e validare gli input degli utenti.

 #AE.2.1    Sezione: 2.1
 Strumentazione per la difesa contro l'iniezione di prompt: utilizzare strumenti guardrail come NeMo di NVIDIA o Guardrails AI.

---

