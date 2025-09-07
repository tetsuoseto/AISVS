## Frontespizio

### Informazioni sullo standard

Lo Standard di Verifica della Sicurezza dell'Intelligenza Artificiale (AISVS) è un catalogo di requisiti di sicurezza guidato dalla comunità che scienziati dei dati, ingegneri MLOps, architetti software, sviluppatori, tester, professionisti della sicurezza, fornitori di strumenti, regolatori e consumatori possono utilizzare per progettare, costruire, testare e verificare sistemi e applicazioni AI affidabili. Fornisce un linguaggio comune per la specifica dei controlli di sicurezza lungo l'intero ciclo di vita dell'AI — dalla raccolta dei dati e sviluppo del modello alla distribuzione e monitoraggio continuo — in modo che le organizzazioni possano misurare e migliorare la resilienza, la privacy e la sicurezza delle loro soluzioni AI.

### Copyright e licenza

Versione 0.1 (Prima Bozza Pubblica - Lavori in Corso), 2025  

![license](images/license.png)
Copyright © 2025 Il Progetto AISVS.  

Rilasciato sotto laCreative Commons Attribution‑ShareAlike 4.0 International License.
Per qualsiasi riutilizzo o distribuzione, devi comunicare chiaramente i termini di licenza di questo lavoro ad altri.

### Responsabili di progetto

Jim Manico
Aras “Russ” Memisyazici

### Collaboratori e Revisori

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


---

AISVS è uno standard completamente nuovo creato appositamente per affrontare le sfide uniche di sicurezza dei sistemi di intelligenza artificiale. Sebbene si ispiri alle migliori pratiche di sicurezza più ampie, ogni requisito di AISVS è stato sviluppato da zero per riflettere il panorama delle minacce dell’AI e per aiutare le organizzazioni a costruire soluzioni AI più sicure e resilienti.

## Prefazione

Benvenuti allo Standard di Verifica della Sicurezza dell'Intelligenza Artificiale (AISVS) versione 1.0!

### Introduzione

Fondata nel 2025 attraverso uno sforzo collaborativo della comunità, AISVS definisce i requisiti di sicurezza da considerare nella progettazione, sviluppo, distribuzione e gestione di modelli AI moderni, pipeline e servizi abilitati all'AI.

AISVS v1.0 rappresenta il lavoro combinato dei suoi leader di progetto, del gruppo di lavoro e dei contributori della comunità più ampia per produrre una linea di base pragmatica e testabile per la sicurezza dei sistemi di Intelligenza Artificiale.

Il nostro obiettivo con questa release è rendere AISVS facile da adottare mantenendo al contempo una concentrazione precisa sul suo ambito definito e affrontando il panorama dei rischi in rapido mutamento, unico per l'IA.

### Obiettivi principali per AISVS Versione 1.0

La Versione 1.0 sarà creata con diversi principi guida.

#### Ambito Ben Definito

Ogni requisito deve essere allineato con il nome e la missione di AISVS:

Intelligenza Artificiale – I controlli operano a livello AI/ML (dati, modello, pipeline o inferenza) e sono responsabilità degli operatori AI.
Sicurezza – I requisiti mitigano direttamente i rischi identificati relativi alla sicurezza, alla privacy o alla sicurezza operativa.
Verifica – Il linguaggio è scritto in modo che la conformità possa essere validata oggettivamente.
Standard – Le sezioni seguono una struttura e una terminologia coerenti per formare un riferimento coerente.
​
---

Seguendo AISVS, le organizzazioni possono valutare sistematicamente e rafforzare la postura di sicurezza delle loro soluzioni di intelligenza artificiale, promuovendo una cultura di ingegneria AI sicura.

## Utilizzo dell’AISVS

Lo Standard di Verifica della Sicurezza dell'Intelligenza Artificiale (AISVS) definisce i requisiti di sicurezza per le moderne applicazioni e servizi di IA, focalizzandosi sugli aspetti sotto il controllo degli sviluppatori delle applicazioni.

L'AISVS è destinato a chiunque sviluppi o valuti la sicurezza delle applicazioni di Intelligenza Artificiale, inclusi sviluppatori, architetti, ingegneri della sicurezza e revisori. Questo capitolo introduce la struttura e l'uso dell'AISVS, comprese le sue modalità di verifica e i casi d'uso previsti.

### Livelli di Verifica della Sicurezza dell'Intelligenza Artificiale

L'AISVS definisce tre livelli crescenti di verifica della sicurezza. Ogni livello aggiunge profondità e complessità, permettendo alle organizzazioni di adattare la loro postura di sicurezza al livello di rischio dei loro sistemi di intelligenza artificiale.

Le organizzazioni possono iniziare dal Livello 1 e adottare progressivamente livelli più elevati man mano che aumentano la maturità della sicurezza e l'esposizione alle minacce.

#### Definizione dei Livelli

Ogni requisito in AISVS v1.0 è assegnato a uno dei seguenti livelli:

 Requisiti di Livello 1

Il Livello 1 include i requisiti di sicurezza più critici e fondamentali. Questi si concentrano sulla prevenzione di attacchi comuni che non si basano su altre precondizioni o vulnerabilità. La maggior parte dei controlli del Livello 1 è semplice da implementare o sufficientemente essenziale da giustificare lo sforzo.

 Requisiti di livello 2

Il Livello 2 affronta attacchi più avanzati o meno comuni, oltre a difese stratificate contro minacce diffuse. Questi requisiti possono coinvolgere una logica più complessa o mirare a prerequisiti specifici dell’attacco.

 Requisiti di Livello 3

Il livello 3 include controlli che sono tipicamente più difficili da implementare o di applicabilità situazionale. Questi spesso rappresentano meccanismi di difesa in profondità o mitigazioni contro attacchi di nicchia, mirati o di alta complessità.

#### Ruolo (D/V)

Ogni requisito AISVS è contrassegnato in base al pubblico principale:

D – Requisiti focalizzati sullo sviluppatore
V – Requisiti focalizzati sul verificatore/revisore
D/V – Rilevante sia per sviluppatori che per verificatori

## Governance dei dati di training C1 e gestione dei bias

### Obiettivo di Controllo

I dati di addestramento devono essere ottenuti, gestiti e mantenuti in modo da preservare la provenienza, la sicurezza, la qualità e l'equità. Farlo soddisfa gli obblighi legali e riduce i rischi di bias, avvelenamento o violazioni della privacy che si manifestano durante l'addestramento e che potrebbero influenzare l'intero ciclo di vita dell'IA.

---

### C1.1 Provenienza dei dati di addestramento

Mantenere un inventario verificabile di tutti i dataset, accettare solo fonti affidabili e registrare ogni modifica per garantire l'auditabilità.

 #1.1.1    Livello: 1    Ruolo: D/V
 Verificare che sia mantenuto un inventario aggiornato di ogni fonte di dati di addestramento (origine, responsabile/proprietario, licenza, metodo di raccolta, vincoli d’uso previsti e cronologia di elaborazione).
 #1.1.2    Livello: 1    Ruolo: D/V
 Verificare che i processi di formazione dei dati escludano funzionalità, attributi o campi non necessari (ad esempio, metadati inutilizzati, PII sensibili, dati di test trapelati).
 #1.1.3    Livello: 2    Ruolo: D/V
 Verificare che tutte le modifiche al dataset siano soggette a un flusso di approvazione registrato.
 #1.1.4    Livello: 3    Ruolo: D/V
 Verificare che i dataset o i sottoinsiemi siano watermarkati o fingerprintati ove possibile.

---

### C1.2 Sicurezza e Integrità dei Dati di Addestramento

Limitare l'accesso ai dati di addestramento, crittografarli sia a riposo che in transito, e convalidarne l'integrità per prevenire manomissioni, furti o avvelenamento dei dati.

 #1.2.1    Livello: 1    Ruolo: D/V
 Verificare che i controlli di accesso proteggano l'archiviazione dei dati di addestramento e le pipeline.
 #1.2.2    Livello: 2    Ruolo: D/V
 Verificare che tutti gli accessi ai dati di addestramento siano registrati, includendo utente, ora e azione.
 #1.2.3    Livello: 2    Ruolo: D/V
 Verificare che i dataset di addestramento siano crittografati durante il trasferimento e in archivio, utilizzando algoritmi crittografici standard del settore e pratiche di gestione delle chiavi.
 #1.2.4    Livello: 2    Ruolo: D/V
 Verificare che vengano utilizzati hash crittografici o firme digitali per garantire l'integrità dei dati durante l'archiviazione e il trasferimento dei dati di addestramento.
 #1.2.5    Livello: 2    Ruolo: D/V
 Verificare che vengano applicate tecniche di rilevamento automatico per proteggere contro modifiche non autorizzate o la corruzione dei dati di addestramento.
 #1.2.6    Livello: 2    Ruolo: D/V
 Verificare che i dati di addestramento obsoleti siano eliminati in modo sicuro o anonimizzati.
 #1.2.7    Livello: 3    Ruolo: D/V
 Verificare che tutte le versioni del dataset di addestramento siano identificate in modo univoco, archiviate in modo immutabile e verificabili per supportare il rollback e l'analisi forense.

---

### C1.3 Qualità, Integrità e Sicurezza dell'Etichettatura dei Dati di Addestramento

Proteggi le etichette e richiedi una revisione tecnica per i dati critici.

 #1.3.1    Livello: 2    Ruolo: D/V
 Verificare che gli hash crittografici o le firme digitali siano applicati agli artefatti di etichettatura per garantirne l'integrità e l'autenticità.
 #1.3.2    Livello: 2    Ruolo: D/V
 Verificare che le interfacce e le piattaforme di etichettatura applichino controlli di accesso rigorosi, mantengano registri di audit a prova di manomissione di tutte le attività di etichettatura e proteggano contro modifiche non autorizzate.
 #1.3.3    Livello: 3    Ruolo: D/V
 Verificare che le informazioni sensibili nelle etichette siano occultate, anonimizzate o crittografate a livello di campo dati sia a riposo che in transito.

---

### C1.4 Qualità dei Dati di Addestramento e Garanzia di Sicurezza

Combina la convalida automatica, i controlli manuali a campione e la correzione registrata per garantire l'affidabilità del dataset.

 #1.4.1    Livello: 1    Ruolo: D
 Verifica che i test automatizzati rilevino errori di formato e valori nulli ad ogni ingestione o significativa trasformazione dei dati.
 #1.4.2    Livello: 2    Ruolo: D/V
 Verificare che le pipeline di addestramento e fine-tuning di LLM implementino la rilevazione del poisoning e la validazione dell'integrità dei dati (ad esempio, metodi statistici, rilevamento di outlier, analisi degli embedding) per identificare potenziali attacchi di poisoning (ad esempio, inversione delle etichette, inserimento di trigger backdoor, comandi di cambio ruolo, attacchi tramite istanze influenti) o corruzione accidentale dei dati di addestramento.
 #1.4.3    Livello: 3    Ruolo: D/V
 Verificare che siano implementate e tarate difese appropriate, come l'addestramento avversariale (utilizzando esempi avversariali generati), l'aumento dei dati con input perturbati o tecniche di ottimizzazione robusta, per i modelli rilevanti in base alla valutazione del rischio.
 #1.4.4    Livello: 2    Ruolo: D/V
 Verificare che le etichette generate automaticamente (ad esempio, tramite LLM o supervisione debole) siano soggette a soglie di confidenza e controlli di coerenza per rilevare etichette allucinatorie, fuorvianti o di bassa confidenza.
 #1.4.5    Livello: 3    Ruolo: D
 Verificare che i test automatizzati rilevino gli scostamenti delle etichette a ogni acquisizione o trasformazione significativa dei dati.

---

### C1.5 Traccia e Provenienza dei Dati

Traccia l’intero percorso di ogni punto dati dalla fonte all’input del modello per garantire la tracciabilità e la risposta agli incidenti.

 #1.5.1    Livello: 2    Ruolo: D/V
 Verificare che la provenienza di ogni punto dati, comprese tutte le trasformazioni, le aumentazioni e le fusioni, sia registrata e possa essere ricostruita.
 #1.5.2    Livello: 2    Ruolo: D/V
 Verificare che i record di provenienza siano immutabili, archiviati in modo sicuro e accessibili per le verifiche.
 #1.5.3    Livello: 2    Ruolo: D/V
 Verificare che il tracciamento della provenienza copra i dati sintetici generati tramite tecniche di protezione della privacy o generative e che tutti i dati sintetici siano chiaramente etichettati e distinguibili dai dati reali lungo tutto il processo.

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

## Validazione dell'input utente C2

### Obiettivo di Controllo

La convalida robusta dell'input dell'utente è una difesa di prima linea contro alcuni degli attacchi più dannosi ai sistemi di intelligenza artificiale. Gli attacchi di iniezione di prompt possono sovrascrivere le istruzioni di sistema, divulgare dati sensibili o indirizzare il modello verso comportamenti non consentiti. A meno che non siano presenti filtri dedicati e gerarchie di istruzioni, la ricerca dimostra che i jailbreak "multi-shot" che sfruttano finestre di contesto molto lunghe saranno efficaci. Inoltre, attacchi sottili di perturbazione adversariale—come sostituzioni di omoglifi o leetspeak—possono silenziosamente modificare le decisioni di un modello.

---

### C2.1 Difesa contro l'iniezione di prompt

L'iniezione di prompt è uno dei principali rischi per i sistemi di intelligenza artificiale. Le difese contro questa tattica utilizzano una combinazione di filtri statici basati su pattern, classificatori dinamici e l'applicazione gerarchica delle istruzioni.

 #2.1.1    Livello: 1    Ruolo: D/V
 Verificare che gli input dell'utente vengano filtrati confrontandoli con una libreria continuamente aggiornata di modelli noti di iniezione di prompt (parole chiave di jailbreak, "ignora precedente", catene di gioco di ruolo, attacchi indiretti HTML/URL).
 #2.1.2    Livello: 1    Ruolo: D/V
 Verificare che il sistema imponga una gerarchia di istruzioni in cui i messaggi di sistema o dello sviluppatore sovrascrivono le istruzioni dell'utente, anche dopo l'espansione della finestra di contesto.
 #2.1.3    Livello: 2    Ruolo: D/V
 Verificare che i test di valutazione adversariale (ad esempio, prompt "many-shot" del Red Team) siano eseguiti prima di ogni rilascio del modello o del template di prompt, con soglie di successo e blocchi automatici per regressioni.
 #2.1.4    Livello: 2    Ruolo: D
 Verificare che i prompt provenienti da contenuti di terze parti (pagine web, PDF, email) siano sanificati in un contesto di analisi isolato prima di essere concatenati nel prompt principale.
 #2.1.5    Livello: 3    Ruolo: D/V
 Verificare che tutti gli aggiornamenti delle regole di filtro del prompt, le versioni dei modelli di classificazione e le modifiche alla lista di blocco siano controllati tramite versionamento e verificabili.

---

### C2.2 Resistenza agli esempi avversari

I modelli di Elaborazione del Linguaggio Naturale (NLP) sono ancora vulnerabili a perturbazioni sottili a livello di caratteri o parole che gli esseri umani spesso non percepiscono, ma che i modelli tendono a classificare in modo errato.

 #2.2.1    Livello: 1    Ruolo: D
 Verificare che le operazioni di normalizzazione di base dell'input (Unicode NFC, mappatura degli omoglifici, rimozione degli spazi bianchi) vengano eseguite prima della tokenizzazione.
 #2.2.2    Livello: 2    Ruolo: D/V
 Verificare che il rilevamento statistico delle anomalie segnali input con distanza di modifica insolitamente alta rispetto alle norme linguistiche, token ripetuti eccessivi o distanze di embedding anomale.
 #2.2.3    Livello: 2    Ruolo: D
 Verificare che la pipeline di inferenza supporti varianti di modelli rinforzati con addestramento avversario opzionale o livelli di difesa (ad esempio, randomizzazione, distillazione difensiva) per endpoint ad alto rischio.
 #2.2.4    Livello: 2    Ruolo: V
 Verificare che gli input sospetti di tipo adversariale siano messi in quarantena e registrati con il payload completo (dopo la rimozione delle informazioni personali identificabili - PII).
 #2.2.5    Livello: 3    Ruolo: D/V
 Verificare che le metriche di robustezza (tasso di successo delle suite di attacchi conosciuti) vengano monitorate nel tempo e che le regressioni attivino un blocco per il rilascio.

---

### C2.3 Validazione di Schema, Tipo e Lunghezza

Gli attacchi di intelligenza artificiale che utilizzano input malformati o sovradimensionati possono causare errori di parsing, fuoriuscita di prompt tra i campi e esaurimento delle risorse. L'applicazione rigorosa dello schema è inoltre un prerequisito quando si eseguono chiamate a strumenti deterministici.

 #2.3.1    Livello: 1    Ruolo: D
 Verificare che ogni endpoint di chiamata API o funzione definisca uno schema di input esplicito (JSON Schema, Protobuf o equivalente multimodale) e che gli input vengano convalidati prima dell'assemblaggio del prompt.
 #2.3.2    Livello: 1    Ruolo: D/V
 Verificare che gli input che superano i limiti massimi di token o byte vengano rifiutati con un errore sicuro e mai troncati silenziosamente.
 #2.3.3    Livello: 2    Ruolo: D/V
 Verificare che i controlli di tipo (es. intervalli numerici, valori enum, tipi MIME per immagini/audio) siano applicati lato server, non solo nel codice client.
 #2.3.4    Livello: 2    Ruolo: D
 Verificare che i validatori semantici (ad esempio, JSON Schema) vengano eseguiti in tempo costante per prevenire attacchi DoS algoritmici.
 #2.3.5    Livello: 3    Ruolo: V
 Verificare che i fallimenti di convalida vengano registrati con frammenti di payload oscurati e codici di errore inequivocabili per facilitare la gestione della sicurezza.

---

### C2.4 Controllo dei Contenuti e delle Politiche

Gli sviluppatori dovrebbero essere in grado di rilevare prompt sintatticamente validi che richiedono contenuti non consentiti (come istruzioni illecite, discorsi di odio e testi protetti da copyright) e poi impedire la loro diffusione.

 #2.4.1    Livello: 1    Ruolo: D
 Verificare che un classificatore di contenuti (zero shot o fine-tuned) valuti ogni input per violenza, autolesionismo, odio, contenuti sessuali e richieste illegali, con soglie configurabili.
 #2.4.2    Livello: 1    Ruolo: D/V
 Verificare che gli input che violano le politiche ricevano rifiuti standardizzati o completamenti sicuri in modo che non vengano propagati a chiamate LLM successive.
 #2.4.3    Livello: 2    Ruolo: D
 Verificare che il modello di screening o il set di regole venga riqualificato/aggiornato almeno ogni trimestre, incorporando i nuovi schemi di jailbreak o di elusione delle policy osservati.
 #2.4.4    Livello: 2    Ruolo: D
 Verificare che il filtro rispetti le politiche specifiche per l'utente (età, vincoli legali regionali) tramite regole basate su attributi risolte al momento della richiesta.
 #2.4.5    Livello: 3    Ruolo: V
 Verificare che i registri di screening includano i punteggi di fiducia del classificatore e le etichette della categoria di policy per la correlazione SOC e la riproduzione futura del red-team.

---

### C2.5 Limitazione della velocità di input e prevenzione degli abusi

Gli sviluppatori dovrebbero prevenire abusi, esaurimento delle risorse e attacchi automatizzati contro i sistemi AI limitando i tassi di input e rilevando pattern di utilizzo anomali.

 #2.5.1    Livello: 1    Ruolo: D/V
 Verificare che i limiti di velocità per utente, per IP e per chiave API siano applicati a tutti gli endpoint di input.
 #2.5.2    Livello: 2    Ruolo: D/V
 Verificare che i limiti di velocità burst e sostenuti siano regolati per prevenire attacchi DoS e di forza bruta.
 #2.5.3    Livello: 2    Ruolo: D/V
 Verificare che modelli di utilizzo anomali (ad esempio, richieste rapide consecutive, flooding di input) attivino blocchi automatizzati o escalation.
 #2.5.4    Livello: 3    Ruolo: V
 Verificare che i registri di prevenzione degli abusi siano conservati e revisionati per individuare modelli emergenti di attacco.

---

### C2.6 Validazione dell'Input Multi-Modale

I sistemi di intelligenza artificiale dovrebbero includere una convalida robusta per input non testuali (immagini, audio, file) per prevenire iniezioni, elusioni o abusi di risorse.

 #2.6.1    Livello: 1    Ruolo: D
 Verificare che tutti gli input non testuali (immagini, audio, file) siano convalidati per tipo, dimensione e formato prima della elaborazione.
 #2.6.2    Livello: 2    Ruolo: D/V
 Verificare che i file siano sottoposti a scansione per malware e payload steganografici prima dell'ingestione.
 #2.6.3    Livello: 2    Ruolo: D/V
 Verificare che gli input immagine/audio siano controllati per perturbazioni avversarie o modelli di attacco noti.
 #2.6.4    Livello: 3    Ruolo: V
 Verificare che i fallimenti di validazione dell'input multimodale vengano registrati e attivino allarmi per l'indagine.

---

### C2.7 Origine e attribuzione dell'input

I sistemi di intelligenza artificiale dovrebbero supportare la verifica, il tracciamento degli abusi e la conformità monitorando e etichettando l’origine di tutti gli input degli utenti.

 #2.7.1    Livello: 1    Ruolo: D/V
 Verificare che tutti gli input degli utenti siano etichettati con metadati (ID utente, sessione, fonte, timestamp, indirizzo IP) al momento dell'ingestione.
 #2.7.2    Livello: 2    Ruolo: D/V
 Verificare che i metadati di provenienza siano conservati e verificabili per tutti gli input elaborati.
 #2.7.3    Livello: 2    Ruolo: D/V
 Verificare che le fonti di input anomale o non affidabili siano segnalate e soggette a un controllo più rigoroso o al blocco.

---

### C2.8 Rilevamento Adattivo delle Minacce in Tempo Reale

Gli sviluppatori dovrebbero utilizzare sistemi avanzati di rilevamento delle minacce per l'IA che si adattino ai nuovi schemi di attacco e forniscano protezione in tempo reale mediante il confronto di pattern compilati.

 #2.8.1    Livello: 1    Ruolo: D/V
 Verificare che i modelli di rilevamento delle minacce siano compilati in motori regex ottimizzati per un filtraggio in tempo reale ad alte prestazioni con un impatto minimo sulla latenza.
 #2.8.2    Livello: 1    Ruolo: D/V
 Verificare che i sistemi di rilevamento delle minacce mantengano librerie di pattern separate per diverse categorie di minacce (iniezione di prompt, contenuti dannosi, dati sensibili, comandi di sistema).
 #2.8.3    Livello: 2    Ruolo: D/V
 Verificare che il rilevamento delle minacce adattivo incorpori modelli di machine learning che aggiornano la sensibilità alle minacce in base alla frequenza e ai tassi di successo degli attacchi.
 #2.8.4    Livello: 2    Ruolo: D/V
 Verificare che i feed di intelligence sulle minacce in tempo reale aggiornino automaticamente le librerie di pattern con nuove firme di attacco e IOC (Indicatori di Compromissione).
 #2.8.5    Livello: 3    Ruolo: D/V
 Verificare che i tassi di falsi positivi nella rilevazione delle minacce siano monitorati continuamente e che la specificità dei modelli venga automaticamente regolata per ridurre al minimo le interferenze con i casi d'uso legittimi.
 #2.8.6    Livello: 3    Ruolo: D/V
 Verifica che l'analisi contestuale delle minacce consideri la fonte dell'input, i modelli di comportamento degli utenti e la cronologia delle sessioni per migliorare la precisione del rilevamento.
 #2.8.7    Livello: 3    Ruolo: D/V
 Verificare che le metriche di prestazione del rilevamento delle minacce (tasso di rilevamento, latenza di elaborazione, utilizzo delle risorse) siano monitorate e ottimizzate in tempo reale.

---

### C2.9 Pipeline di Validazione della Sicurezza Multi-Modale

Gli sviluppatori dovrebbero fornire la convalida della sicurezza per testo, immagini, audio e altre modalità di input AI con tipi specifici di rilevamento delle minacce e isolamento delle risorse.

 #2.9.1    Livello: 1    Ruolo: D/V
 Verificare che ogni modalità di input abbia validatori di sicurezza dedicati con modelli di minaccia documentati (testo: iniezione di prompt, immagini: steganografia, audio: attacchi allo spettrogramma) e soglie di rilevamento.
 #2.9.2    Livello: 2    Ruolo: D/V
 Verificare che gli input multi-modali siano elaborati in sandbox isolate con limiti di risorse definiti (memoria, CPU, tempo di elaborazione) specifici per ogni tipo di modalità e documentati nelle politiche di sicurezza.
 #2.9.3    Livello: 2    Ruolo: D/V
 Verificare che il rilevamento degli attacchi cross-modali identifichi attacchi coordinati che coinvolgono più tipi di input (ad esempio, payload steganografici nelle immagini combinati con iniezioni di prompt nel testo) tramite regole di correlazione e generazione di allarmi.
 #2.9.4    Livello: 3    Ruolo: D/V
 Verificare che i fallimenti di convalida multimodale attivino una registrazione dettagliata, includendo tutte le modalità di input, i risultati della convalida, i punteggi di minaccia e l'analisi di correlazione con formati di log strutturati per l'integrazione SIEM.
 #2.9.5    Livello: 3    Ruolo: D/V
 Verificare che i classificatori di contenuti specifici per modalità siano aggiornati secondo i programmi documentati (almeno ogni trimestre) con nuovi modelli di minacce, esempi avversari e che i benchmark di prestazione siano mantenuti al di sopra delle soglie di base.

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

## Gestione del Ciclo di Vita del Modello C3 e Controllo delle Modifiche

### Obiettivo di Controllo

I sistemi di intelligenza artificiale devono implementare processi di controllo delle modifiche che prevengano la diffusione in produzione di modifiche non autorizzate o non sicure del modello. Questo controllo garantisce l'integrità del modello durante l'intero ciclo di vita--dallo sviluppo, al deployment, fino alla dismissione--consentendo una rapida risposta agli incidenti e mantenendo la responsabilità per tutte le modifiche.

Obiettivo principale di sicurezza: Solo modelli autorizzati e validati raggiungono la produzione mediante processi controllati che mantengono integrità, tracciabilità e recuperabilità.

---

### C3.1 Autorizzazione e Integrità del Modello

Solo i modelli autorizzati con integrità verificata raggiungono gli ambienti di produzione.

 #3.1.1    Livello: 1    Ruolo: D/V
 Verificare che tutti gli artefatti del modello (pesi, configurazioni, tokenizer) siano firmati crittograficamente da entità autorizzate prima del deployment.
 #3.1.2    Livello: 1    Ruolo: D/V
 Verificare che l'integrità del modello venga convalidata al momento del deployment e che i fallimenti nella verifica della firma impediscano il caricamento del modello.
 #3.1.3    Livello: 2    Ruolo: D/V
 Verificare che i record di provenienza del modello includano l'identità dell'entità autorizzante, i checksum dei dati di addestramento, i risultati dei test di convalida con stato di superamento/insufficienza e un timestamp di creazione.
 #3.1.4    Livello: 2    Ruolo: D/V
 Verificare che tutti gli artefatti del modello utilizzino un versionamento semantico (MAJOR.MINOR.PATCH) con criteri documentati che specificano quando ogni componente della versione aumenta.
 #3.1.5    Livello: 2    Ruolo: V
 Verificare che il monitoraggio delle dipendenze mantenga un inventario in tempo reale che consenta un'identificazione rapida di tutti i sistemi consumatori.

---

### C3.2 Validazione e Test del Modello

I modelli devono superare le validazioni di sicurezza e protezione definite prima del loro dispiegamento.

 #3.2.1    Livello: 1    Ruolo: D/V
 Verificare che i modelli siano sottoposti a test di sicurezza automatizzati che includono la validazione degli input, la sanitizzazione degli output e le valutazioni di sicurezza con soglie di superamento/fallimento concordate preventivamente dall’organizzazione prima del dispiegamento.
 #3.2.2    Livello: 1    Ruolo: D/V
 Verificare che i fallimenti di validazione blocchino automaticamente il deployment del modello dopo un'esplicita approvazione di override da parte di personale autorizzato predesignato con giustificazioni aziendali documentate.
 #3.2.3    Livello: 2    Ruolo: V
 Verificare che i risultati del test siano firmati crittograficamente e collegati in modo immutabile all'hash della versione specifica del modello che viene convalidata.
 #3.2.4    Livello: 2    Ruolo: D/V
 Verificare che le deployment di emergenza richiedano una valutazione documentata del rischio di sicurezza e l'approvazione da parte di un'autorità di sicurezza predesignata entro i tempi concordati previamente.

---

### C3.3 Distribuzione Controllata e Ripristino

Le distribuzioni dei modelli devono essere controllate, monitorate e reversibili.

 #3.3.1    Livello: 1    Ruolo: D
 Verificare che le distribuzioni in produzione implementino meccanismi di rilascio graduale (deployamenti canary, deployamenti blue-green) con trigger di rollback automatici basati su tassi di errore pre-accordati, soglie di latenza o criteri di allerta di sicurezza.
 #3.3.2    Livello: 1    Ruolo: D/V
 Verificare che le capacità di rollback ripristino in modo atomico lo stato completo del modello (pesi, configurazioni, dipendenze) all’interno delle finestre temporali organizzative predefinite.
 #3.3.3    Livello: 2    Ruolo: D/V
 Verificare che i processi di distribuzione convalidino le firme crittografiche e calcolino i checksum di integrità prima dell'attivazione del modello, bloccando la distribuzione in caso di qualsiasi discrepanza.
 #3.3.4    Livello: 2    Ruolo: D/V
 Verificare che le capacità di arresto di emergenza del modello possano disabilitare gli endpoint del modello entro tempi di risposta predefiniti tramite interruttori automatici o manuali.
 #3.3.5    Livello: 2    Ruolo: V
 Verificare che gli artefatti di rollback (versioni precedenti del modello, configurazioni, dipendenze) siano mantenuti secondo le politiche organizzative con archiviazione immutabile per la risposta agli incidenti.

---

### C3.4 Modifica della Responsabilità e Audit

Tutte le modifiche del ciclo di vita del modello devono essere tracciabili e verificabili.

 #3.4.1    Livello: 1    Ruolo: V
 Verificare che tutte le modifiche al modello (deploy, configurazione, dismissione) generino registrazioni di audit immutabili che includano un timestamp, un’identità autenticata dell’attore, un tipo di modifica e gli stati prima/dopo.
 #3.4.2    Livello: 2    Ruolo: D/V
 Verificare che l'accesso al registro di controllo richieda un'autorizzazione appropriata e che tutti i tentativi di accesso siano registrati con l'identità dell'utente e un timestamp.
 #3.4.3    Livello: 2    Ruolo: D/V
 Verificare che i template dei prompt e i messaggi di sistema siano sottoposti a controllo di versione nei repository git, con revisione del codice obbligatoria e approvazione da parte di revisori designati prima della distribuzione.
 #3.4.4    Livello: 2    Ruolo: V
 Verificare che i record di audit includano dettagli sufficienti (hash dei modelli, snapshot di configurazione, versioni delle dipendenze) per consentire la completa ricostruzione dello stato del modello per qualsiasi timestamp all'interno del periodo di conservazione.

---

### Pratiche di Sviluppo Sicuro C3.5

I processi di sviluppo e addestramento del modello devono seguire pratiche sicure per prevenire compromissioni.

 #3.5.1    Livello: 1    Ruolo: D
 Verificare che gli ambienti di sviluppo, test e produzione del modello siano separati fisicamente o logicamente. Essi non devono condividere infrastrutture, devono avere controlli di accesso distinti e archivi dati isolati.
 #3.5.2    Livello: 1    Ruolo: D
 Verificare che l’addestramento e la messa a punto del modello avvengano in ambienti isolati con accesso di rete controllato.
 #3.5.3    Livello: 1    Ruolo: D/V
 Verificare che le fonti dei dati di addestramento siano validate attraverso controlli di integrità e autentificate tramite fonti affidabili con una catena di custodia documentata prima dell'uso nello sviluppo del modello.
 #3.5.4    Livello: 2    Ruolo: D
 Verificare che gli artefatti dello sviluppo del modello (iperparametri, script di addestramento, file di configurazione) siano archiviati nel controllo di versione e richiedano l'approvazione da parte di un revisore prima dell'uso nell'addestramento.

---

### C3.6 Ritiro e dismissione del modello

I modelli devono essere ritirati in modo sicuro quando non sono più necessari o quando vengono identificati problemi di sicurezza.

 #3.6.1    Livello: 1    Ruolo: D
 Verificare che i processi di dismissione del modello scansionino automaticamente i grafi di dipendenza, identifichino tutti i sistemi utilizzatori e forniscano periodi di preavviso concordati in anticipo prima della dismissione.
 #3.6.2    Livello: 1    Ruolo: D/V
 Verificare che gli artefatti del modello ritirato siano cancellati in modo sicuro utilizzando l'eliminazione crittografica o la sovrascrittura multi-pass secondo le politiche documentate di conservazione dei dati, con certificati di distruzione verificati.
 #3.6.3    Livello: 2    Ruolo: V
 Verificare che gli eventi di ritiro del modello siano registrati con timestamp e identità dell'attore, e che le firme del modello siano revocate per prevenire il riutilizzo.
 #3.6.4    Livello: 2    Ruolo: D/V
 Verificare che il ritiro di emergenza del modello possa disabilitare l'accesso al modello entro i tempi di risposta di emergenza predefiniti mediante interruttori di arresto automatico se vengono rilevate vulnerabilità di sicurezza critiche.

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

## Sicurezza dell'Infrastruttura, della Configurazione e del Deployment C4

### Obiettivo di Controllo

L'infrastruttura di intelligenza artificiale deve essere rafforzata contro l'escalation dei privilegi, la manomissione della catena di fornitura e i movimenti laterali tramite configurazioni sicure, isolamento durante l'esecuzione, pipeline di distribuzione affidabili e monitoraggio completo. Solo componenti e configurazioni di infrastruttura autorizzati e validati raggiungono la produzione attraverso processi controllati che mantengono sicurezza, integrità e tracciabilità.

Obiettivo principale di sicurezza: solo i componenti infrastrutturali firmati crittograficamente e sottoposti a scansione delle vulnerabilità raggiungono la produzione tramite pipeline di convalida automatizzate che applicano le politiche di sicurezza e mantengono tracce di controllo immutabili.

---

### C4.1 Isolamento dell'Ambiente di Esecuzione

Impedire fughe dal container e escalation di privilegi attraverso primitive di isolamento a livello kernel e controlli di accesso obbligatori.

 #4.1.1    Livello: 1    Ruolo: D/V
 Verificare che tutti i container AI eliminino TUTTE le capacità Linux eccetto CAP_SETUID, CAP_SETGID e le capacità esplicitamente richieste documentate nelle baseline di sicurezza.
 #4.1.2    Livello: 1    Ruolo: D/V
 Verificare che i profili seccomp blocchino tutte le chiamate di sistema tranne quelle presenti nelle whitelist pre-approvate, con le violazioni che terminano il container e generano avvisi di sicurezza.
 #4.1.3    Livello: 2    Ruolo: D/V
 Verificare che i carichi di lavoro AI vengano eseguiti con filesystem root di sola lettura, tmpfs per i dati temporanei e volumi nominati per i dati persistenti con opzioni di mount noexec applicate.
 #4.1.4    Livello: 2    Ruolo: D/V
 Verificare che il monitoraggio in runtime basato su eBPF (Falco, Tetragon o equivalente) rilevi i tentativi di escalation dei privilegi e termini automaticamente i processi responsabili entro i tempi di risposta previsti dall'organizzazione.
 #4.1.5    Livello: 3    Ruolo: D/V
 Verificare che i carichi di lavoro AI ad alto rischio vengano eseguiti in ambienti isolati dall'hardware (Intel TXT, AMD SVM o nodi bare-metal dedicati) con verifica di attestazione.

---

### C4.2 Pipeline Sicure di Build e Deployment

Garantire l'integrità crittografica e la sicurezza della catena di approvvigionamento tramite build riproducibili e artefatti firmati.

 #4.2.1    Livello: 1    Ruolo: D/V
 Verificare che l'infrastruttura come codice venga scansionata con strumenti (tfsec, Checkov o Terrascan) ad ogni commit, bloccando le fusioni in presenza di rilevamenti con severità CRITICA o ALTA.
 #4.2.2    Livello: 1    Ruolo: D/V
 Verificare che le compilazioni dei container siano riproducibili con hash SHA256 identici tra le compilazioni e generare attestazioni di provenienza SLSA Livello 3 firmate con Sigstore.
 #4.2.3    Livello: 2    Ruolo: D/V
 Verificare che le immagini dei container incorporino SBOM CycloneDX o SPDX e siano firmate con Cosign prima del push al registro, con il rifiuto delle immagini non firmate durante la distribuzione.
 #4.2.4    Livello: 2    Ruolo: D/V
 Verificare che le pipeline CI/CD utilizzino token OIDC da HashiCorp Vault, ruoli IAM AWS o identità gestite Azure con durate che non superano i limiti stabiliti dalla politica di sicurezza organizzativa.
 #4.2.5    Livello: 2    Ruolo: D/V
 Verificare che le firme Cosign e la provenienza SLSA siano validate durante il processo di distribuzione prima dell'esecuzione del container e che gli errori di verifica causino il fallimento della distribuzione.
 #4.2.6    Livello: 2    Ruolo: D/V
 Verificare che gli ambienti di build vengano eseguiti in container effimeri o VM senza storage persistente e con isolamento di rete rispetto alle VPC di produzione.

---

### C4.3 Sicurezza di Rete e Controllo degli Accessi

Implementare il networking a zero-trust con politiche di default-deny e comunicazioni criptate.

 #4.3.1    Livello: 1    Ruolo: D/V
 Verificare che le NetworkPolicy di Kubernetes o qualsiasi equivalente implementino il default-deny per ingressi/uscite con regole esplicite di autorizzazione per le porte necessarie (443, 8080, ecc.).
 #4.3.2    Livello: 1    Ruolo: D/V
 Verificare che SSH (porta 22), RDP (porta 3389) e gli endpoint dei metadata cloud (169.254.169.254) siano bloccati o richiedano l’autenticazione basata su certificato.
 #4.3.3    Livello: 2    Ruolo: D/V
 Verificare che il traffico in uscita venga filtrato tramite proxy HTTP/HTTPS (Squid, Istio o gateway NAT cloud) con liste di domini consentiti e che le richieste bloccate vengano registrate.
 #4.3.4    Livello: 2    Ruolo: D/V
 Verificare che la comunicazione tra servizi utilizzi mutual TLS con certificati ruotati secondo la politica organizzativa e che la validazione dei certificati sia applicata (nessun flag skip-verify).
 #4.3.5    Livello: 2    Ruolo: D/V
 Verificare che l'infrastruttura AI funzioni in VPC/VNet dedicati senza accesso diretto a internet e comunichi esclusivamente attraverso gateway NAT o host bastione.

---

### C4.4 Gestione dei Segreti e delle Chiavi Criptografiche

Proteggi le credenziali tramite archiviazione supportata da hardware e rotazione automatizzata con accesso a fiducia zero.

 #4.4.1    Livello: 1    Ruolo: D/V
 Verificare che i segreti siano archiviati in HashiCorp Vault, AWS Secrets Manager, Azure Key Vault o Google Secret Manager con crittografia a riposo utilizzando AES-256.
 #4.4.2    Livello: 1    Ruolo: D/V
 Verificare che le chiavi crittografiche siano generate in HSM conformi a FIPS 140-2 Livello 2 (AWS CloudHSM, Azure Dedicated HSM) con rotazione delle chiavi secondo la politica crittografica organizzativa.
 #4.4.3    Livello: 2    Ruolo: D/V
 Verificare che la rotazione dei segreti sia automatizzata con un deployment senza tempi di inattività e una rotazione immediata attivata da cambiamenti del personale o incidenti di sicurezza.
 #4.4.4    Livello: 2    Ruolo: D/V
 Verificare che le immagini dei container siano scansionate con strumenti (GitLeaks, TruffleHog o detect-secrets) che bloccano le build contenenti chiavi API, password o certificati.
 #4.4.5    Livello: 2    Ruolo: D/V
 Verificare che l'accesso ai segreti di produzione richieda l'MFA con token hardware (YubiKey, FIDO2) e sia registrato da log di audit immutabili con identità utente e timestamp.
 #4.4.6    Livello: 2    Ruolo: D/V
 Verificare che i segreti vengano iniettati tramite segreti di Kubernetes, volumi montati o container di inizializzazione e assicurarsi che i segreti non siano mai incorporati nelle variabili d'ambiente o nelle immagini.

---

### C4.5 Sandboxing e Validazione del Carico di Lavoro AI

Isolare i modelli di intelligenza artificiale non fidati in sandbox sicure con un'analisi comportamentale completa.

 #4.5.1    Livello: 1    Ruolo: D/V
 Verificare che i modelli di AI esterni vengano eseguiti in gVisor, microVM (come Firecracker, CrossVM) o container Docker con le opzioni --security-opt=no-new-privileges e --read-only.
 #4.5.2    Livello: 1    Ruolo: D/V
 Verificare che gli ambienti sandbox non abbiano connettività di rete (--network=none) oppure che abbiano accesso solo a localhost con tutte le richieste esterne bloccate dalle regole iptables.
 #4.5.3    Livello: 2    Ruolo: D/V
 Verificare che la convalida del modello AI includa test di red-team automatizzati con copertura di test definita dall'organizzazione e analisi comportamentale per il rilevamento di backdoor.
 #4.5.4    Livello: 2    Ruolo: D/V
 Verificare che, prima che un modello di IA venga promosso in produzione, i risultati nel sandbox siano firmati crittograficamente dal personale di sicurezza autorizzato e archiviati in log di audit immutabili.
 #4.5.5    Livello: 2    Ruolo: D/V
 Verificare che gli ambienti sandbox vengano distrutti e ricreati dalle immagini di riferimento tra le valutazioni con una completa pulizia del filesystem e della memoria.

---

### C4.6 Monitoraggio della Sicurezza dell'Infrastruttura

Scansiona e monitora continuamente l'infrastruttura con risoluzione automatica e allerta in tempo reale.

 #4.6.1    Livello: 1    Ruolo: D/V
 Verificare che le immagini dei container siano scansionate secondo i programmi organizzativi, con le vulnerabilità CRITICHE che bloccano la distribuzione in base alle soglie di rischio organizzative.
 #4.6.2    Livello: 1    Ruolo: D/V
 Verificare che l'infrastruttura rispetti i CIS Benchmarks o i controlli NIST 800-53 con soglie di conformità definite dall'organizzazione e con la rimedio automatico per i controlli non superati.
 #4.6.3    Livello: 2    Ruolo: D/V
 Verificare che le vulnerabilità di gravità ALTA siano corrette secondo le tempistiche di gestione del rischio organizzativo con procedure di emergenza per le CVE attivamente sfruttate.
 #4.6.4    Livello: 2    Ruolo: V
 Verificare che gli avvisi di sicurezza si integrino con le piattaforme SIEM (Splunk, Elastic o Sentinel) utilizzando i formati CEF o STIX/TAXII con arricchimento automatizzato.
 #4.6.5    Livello: 3    Ruolo: V
 Verificare che le metriche dell'infrastruttura siano esportate ai sistemi di monitoraggio (Prometheus, DataDog) con dashboard SLA e reportistica esecutiva.
 #4.6.6    Livello: 2    Ruolo: D/V
 Verificare che la deriva della configurazione venga rilevata utilizzando strumenti (Chef InSpec, AWS Config) secondo i requisiti di monitoraggio organizzativo con rollback automatico per modifiche non autorizzate.

---

### Gestione delle Risorse dell'Infrastruttura AI C4.7

Prevenire gli attacchi di esaurimento delle risorse e garantire un'allocazione equa delle risorse tramite quote e monitoraggio.

 #4.7.1    Livello: 1    Ruolo: D/V
 Verificare che l'utilizzo di GPU/TPU sia monitorato con avvisi attivati a soglie definite dall'organizzazione e che venga attivato il ridimensionamento automatico o il bilanciamento del carico in base alle politiche di gestione della capacità.
 #4.7.2    Livello: 1    Ruolo: D/V
 Verificare che le metriche del carico di lavoro AI (latenza di inferenza, throughput, tassi di errore) siano raccolte in conformità ai requisiti di monitoraggio dell’organizzazione e correlate con l’utilizzo dell’infrastruttura.
 #4.7.3    Livello: 2    Ruolo: D/V
 Verificare che i ResourceQuota di Kubernetes o equivalenti limitino i singoli carichi di lavoro secondo le politiche di allocazione delle risorse dell'organizzazione con limiti rigidi applicati.
 #4.7.4    Livello: 2    Ruolo: V
 Verificare che il monitoraggio dei costi tenga traccia della spesa per carico di lavoro/tenant con avvisi basati sulle soglie di budget organizzativo e controlli automatizzati per il superamento del budget.
 #4.7.5    Livello: 3    Ruolo: V
 Verificare che la pianificazione della capacità utilizzi dati storici con periodi di previsione definiti dall'organizzazione e provisioning automatico delle risorse basato sui modelli di domanda.
 #4.7.6    Livello: 2    Ruolo: D/V
 Verificare che l'esaurimento delle risorse attivi gli interruttori automatici (circuit breakers) secondo i requisiti di risposta dell'organizzazione, inclusi il limitazione della velocità basata sulle politiche di capacità e l'isolamento del carico di lavoro.

---

### C4.8 Controlli per la Separazione degli Ambienti e la Promozione

Imporre rigidi confini ambientali con cancelli di promozione automatizzati e validazione della sicurezza.

 #4.8.1    Livello: 1    Ruolo: D/V
 Verificare che gli ambienti dev/test/prod operino in VPC/VNet separati senza ruoli IAM, gruppi di sicurezza o connettività di rete condivisi.
 #4.8.2    Livello: 1    Ruolo: D/V
 Verificare che la promozione dell’ambiente richieda l’approvazione da parte del personale autorizzato definito a livello organizzativo, con firme crittografiche e registri di controllo immutabili.
 #4.8.3    Livello: 2    Ruolo: D/V
 Verificare che gli ambienti di produzione blocchino l'accesso SSH, disabilitino gli endpoint di debug e richiedano richieste di modifica con requisiti di preavviso organizzativo, ad eccezione delle emergenze.
 #4.8.4    Livello: 2    Ruolo: D/V
 Verificare che le modifiche all'infrastruttura come codice richiedano una revisione tra pari con test automatizzati e scansione di sicurezza prima della fusione nel ramo principale.
 #4.8.5    Livello: 2    Ruolo: D/V
 Verificare che i dati non di produzione siano anonimizzati secondo i requisiti di privacy dell'organizzazione, con generazione di dati sintetici o mascheramento completo dei dati con rimozione delle PII verificata.
 #4.8.6    Livello: 2    Ruolo: D/V
 Verificare che i gate di promozione includano test di sicurezza automatizzati (SAST, DAST, scansione dei container) con zero risultati CRITICI richiesti per l'approvazione.

---

### Backup e ripristino dell'infrastruttura C4.9

Garantire la resilienza dell'infrastruttura tramite backup automatizzati, procedure di recupero testate e capacità di ripristino in caso di disastro.

 #4.9.1    Livello: 1    Ruolo: D/V
 Verificare che le configurazioni dell'infrastruttura siano sottoposte a backup secondo i programmi di backup organizzativi verso regioni geograficamente separate con l'implementazione della strategia di backup 3-2-1.
 #4.9.2    Livello: 2    Ruolo: D/V
 Verificare che i sistemi di backup funzionino in reti isolate con credenziali separate e archiviazione air-gapped per la protezione contro il ransomware.
 #4.9.3    Livello: 2    Ruolo: V
 Verificare che le procedure di ripristino siano testate e validate tramite test automatizzati secondo i programmi organizzativi, con obiettivi di RTO e RPO che soddisfano i requisiti dell'organizzazione.
 #4.9.4    Livello: 3    Ruolo: V
 Verificare che il disaster recovery includa runbook specifici per l’IA con il ripristino dei pesi del modello, la ricostruzione del cluster GPU e la mappatura delle dipendenze di servizio.

---

### C4.10 Conformità e Governance dell'Infrastruttura

Garantire la conformità normativa attraverso una valutazione continua, la documentazione e controlli automatizzati.

 #4.10.1    Livello: 2    Ruolo: D/V
 Verificare che la conformità dell'infrastruttura sia valutata secondo i programmi organizzativi rispetto ai controlli SOC 2, ISO 27001 o FedRAMP con la raccolta automatizzata delle evidenze.
 #4.10.2    Livello: 2    Ruolo: V
 Verificare che la documentazione dell'infrastruttura includa diagrammi di rete, mappe di flusso dei dati e modelli di minacce aggiornati secondo i requisiti della gestione del cambiamento organizzativo.
 #4.10.3    Livello: 3    Ruolo: D/V
 Verificare che le modifiche all'infrastruttura vengano sottoposte a una valutazione automatizzata dell'impatto sulla conformità con flussi di lavoro di approvazione normativa per modifiche ad alto rischio.

---

### C4.11 Sicurezza dell'Hardware per l'IA

Proteggere i componenti hardware specifici per l'IA, inclusi GPU, TPU e acceleratori AI specializzati.

 #4.11.1    Livello: 2    Ruolo: D/V
 Verificare che il firmware dell'acceleratore AI (BIOS GPU, firmware TPU) sia verificato con firme crittografiche e aggiornato secondo le tempistiche di gestione delle patch dell'organizzazione.
 #4.11.2    Livello: 2    Ruolo: D/V
 Verificare che, prima dell'esecuzione del carico di lavoro, l'integrità dell'acceleratore AI sia validata mediante attestazione hardware utilizzando TPM 2.0, Intel TXT o AMD SVM.
 #4.11.3    Livello: 2    Ruolo: D/V
 Verificare che la memoria GPU sia isolata tra i carichi di lavoro utilizzando SR-IOV, MIG (Multi-Instance GPU) o un partizionamento hardware equivalente con sanificazione della memoria tra i processi.
 #4.11.4    Livello: 3    Ruolo: V
 Verificare che la catena di fornitura dell'hardware AI includa la verifica della provenienza con certificati del produttore e la convalida dell'imballaggio a prova di manomissione.
 #4.11.5    Livello: 3    Ruolo: D/V
 Verificare che i moduli di sicurezza hardware (HSM) proteggano i pesi del modello AI e le chiavi crittografiche con certificazione FIPS 140-2 Livello 3 o Common Criteria EAL4+.

---

### C4.12 Infrastruttura AI Edge e Distribuita

Distribuzioni AI distribuite sicure, inclusi edge computing, apprendimento federato e architetture multi-sito.

 #4.12.1    Livello: 2    Ruolo: D/V
 Verificare che i dispositivi edge AI si autentichino all'infrastruttura centrale utilizzando mutual TLS con certificati di dispositivo ruotati secondo la politica organizzativa di gestione dei certificati.
 #4.12.2    Livello: 2    Ruolo: D/V
 Verificare che i dispositivi edge implementino il secure boot con firme verificate e protezione rollback per prevenire attacchi di downgrade del firmware.
 #4.12.3    Livello: 3    Ruolo: D/V
 Verificare che il coordinamento dell'intelligenza artificiale distribuita utilizzi algoritmi di consenso tolleranti ai guasti bizantini con validazione dei partecipanti e rilevamento di nodi malevoli.
 #4.12.4    Livello: 3    Ruolo: D/V
 Verificare che la comunicazione edge-to-cloud includa il controllo della larghezza di banda, la compressione dei dati e le capacità di funzionamento offline con archiviazione locale sicura.

---

### C4.13 Sicurezza dell'Infrastruttura Multi-Cloud e Ibrida

Proteggi i carichi di lavoro AI in modo sicuro attraverso più provider cloud e implementazioni ibride cloud-on-premises.

 #4.13.1    Livello: 2    Ruolo: D/V
 Verificare che le distribuzioni AI multi-cloud utilizzino la federazione di identità cloud-agnostica (OIDC, SAML) con una gestione centralizzata delle policy tra i provider.
 #4.13.2    Livello: 2    Ruolo: D/V
 Verificare che il trasferimento di dati tra cloud utilizzi la crittografia end-to-end con chiavi gestite dal cliente e che i controlli sulla residenza dei dati siano applicati in base alla giurisdizione.
 #4.13.3    Livello: 2    Ruolo: D/V
 Verificare che i workload di AI in cloud ibrido implementino politiche di sicurezza consistenti tra ambienti on-premise e cloud con monitoraggio e allerta unificati.
 #4.13.4    Livello: 3    Ruolo: V
 Verificare che la prevenzione del lock-in del fornitore cloud includa un'infrastruttura-as-code portatile, API standardizzate e capacità di esportazione dei dati con strumenti di conversione dei formati.
 #4.13.5    Livello: 3    Ruolo: V
 Verificare che l'ottimizzazione dei costi multi-cloud includa controlli di sicurezza per prevenire la proliferazione delle risorse e le spese non autorizzate per il trasferimento di dati tra cloud.

---

### C4.14 Automazione dell'Infrastruttura e Sicurezza GitOps

Automatizzare in modo sicuro le pipeline di infrastruttura e i flussi di lavoro GitOps per la gestione dell'infrastruttura AI.

 #4.14.1    Livello: 2    Ruolo: D/V
 Verificare che i repository GitOps richiedano commit firmati con chiavi GPG e regole di protezione dei rami che impediscano push diretti ai rami principali.
 #4.14.2    Livello: 2    Ruolo: D/V
 Verificare che l'automazione dell'infrastruttura includa il rilevamento delle derivate con capacità di rimedio automatico e rollback attivate in base ai requisiti di risposta organizzativa per modifiche non autorizzate.
 #4.14.3    Livello: 2    Ruolo: D/V
 Verificare che la fornitura automatizzata dell'infrastruttura includa la convalida della politica di sicurezza con il blocco della distribuzione per configurazioni non conformi.
 #4.14.4    Livello: 2    Ruolo: D/V
 Verificare che i segreti dell'automazione dell'infrastruttura siano gestiti tramite operatori di segreti esterni (External Secrets Operator, Bank-Vaults) con rotazione automatica.
 #4.14.5    Livello: 3    Ruolo: V
 Verificare che l'infrastruttura self-healing includa la correlazione degli eventi di sicurezza con la risposta automatizzata agli incidenti e i flussi di lavoro per la notifica agli stakeholder.

---

### C4.15 Sicurezza dell'Infrastruttura Resistente alla Quantum

Preparare l'infrastruttura di intelligenza artificiale per le minacce del calcolo quantistico tramite crittografia post-quantistica e protocolli sicuri contro il quantum.

 #4.15.1    Livello: 3    Ruolo: D/V
 Verificare che l'infrastruttura AI implementi algoritmi crittografici post-quantistici approvati dal NIST (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) per lo scambio di chiavi e le firme digitali.
 #4.15.2    Livello: 3    Ruolo: D/V
 Verificare che i sistemi di distribuzione di chiavi quantistiche (QKD) siano implementati per comunicazioni AI ad alta sicurezza con protocolli di gestione delle chiavi quantisticamente sicuri.
 #4.15.3    Livello: 3    Ruolo: D/V
 Verificare che i framework di agilità crittografica consentano una migrazione rapida a nuovi algoritmi post-quantistici con la rotazione automatica di certificati e chiavi.
 #4.15.4    Livello: 3    Ruolo: V
 Verificare che la modellazione delle minacce quantistiche valuti la vulnerabilità dell'infrastruttura AI agli attacchi quantistici con tempistiche di migrazione documentate e valutazioni del rischio.
 #4.15.5    Livello: 3    Ruolo: D/V
 Verificare che i sistemi crittografici ibridi classico-quantistici offrano una difesa approfondita durante il periodo di transizione quantistica con il monitoraggio delle prestazioni.

---

### C4.16 Calcolo Confidenziale e Enclavi Sicure

Proteggi i carichi di lavoro AI e i pesi del modello utilizzando ambienti di esecuzione attendibili basati su hardware e tecnologie di calcolo confidenziale.

 #4.16.1    Livello: 3    Ruolo: D/V
 Verificare che i modelli di intelligenza artificiale sensibili vengano eseguiti all'interno di enclave Intel SGX, AMD SEV-SNP o ARM TrustZone con memoria crittografata e verifica di attestazione.
 #4.16.2    Livello: 3    Ruolo: D/V
 Verificare che i container riservati (Kata Containers, gVisor con computing riservato) isolino i carichi di lavoro AI con crittografia della memoria applicata a livello hardware.
 #4.16.3    Livello: 3    Ruolo: D/V
 Verificare che l'attestazione remota convalidi l'integrità dell'enclave prima di caricare i modelli di IA con una prova crittografica dell'autenticità dell'ambiente di esecuzione.
 #4.16.4    Livello: 3    Ruolo: D/V
 Verificare che i servizi di inferenza AI riservati prevengano l'estrazione del modello tramite calcolo crittografato con pesi del modello sigillati ed esecuzione protetta.
 #4.16.5    Livello: 3    Ruolo: D/V
 Verificare che l'orchestrazione dell'ambiente di esecuzione attendibile gestisca il ciclo di vita dell'enclave sicura con attestazione remota e canali di comunicazione crittografati.
 #4.16.6    Livello: 3    Ruolo: D/V
 Verificare che il calcolo sicuro multi-parte (SMPC) consenta l'addestramento collaborativo dell'IA senza esporre i singoli set di dati o i parametri del modello.

---

### C4.17 Infrastruttura a Conoscenza Zero

Implementare sistemi di prova a conoscenza zero per la verifica e l'autenticazione dell'IA preservando la privacy senza rivelare informazioni sensibili.

 #4.17.1    Livello: 3    Ruolo: D/V
 Verificare che le zero-knowledge proofs (ZK-SNARKs, ZK-STARKs) confermino l'integrità del modello AI e la provenienza dell'addestramento senza esporre i pesi del modello o i dati di addestramento.
 #4.17.2    Livello: 3    Ruolo: D/V
 Verificare che i sistemi di autenticazione basati su ZK consentano la verifica dell'utente preservando la privacy per i servizi di intelligenza artificiale senza rivelare informazioni legate all'identità.
 #4.17.3    Livello: 3    Ruolo: D/V
 Verificare che i protocolli di intersezione di insiemi privati (PSI) consentano un confronto sicuro dei dati per l'AI federata senza esporre i dataset individuali.
 #4.17.4    Livello: 3    Ruolo: D/V
 Verificare che i sistemi di machine learning a conoscenza zero (ZKML) consentano inferenze AI verificabili con una prova crittografica della correttezza del calcolo.
 #4.17.5    Livello: 3    Ruolo: D/V
 Verificare che gli ZK-rollup offrano un'elaborazione delle transazioni AI scalabile e rispettosa della privacy con verifica batch e riduzione del carico computazionale.

---

### C4.18 Prevenzione degli attacchi di canalizzazione laterale

Proteggi l'infrastruttura AI da attacchi side-channel basati su temporizzazione, potenza, elettromagnetismo e cache che potrebbero divulgare informazioni sensibili.

 #4.18.1    Livello: 3    Ruolo: D/V
 Verificare che il tempo di inferenza dell'IA sia normalizzato utilizzando algoritmi a tempo costante e padding per prevenire attacchi di estrazione del modello basati sul tempo.
 #4.18.2    Livello: 3    Ruolo: D/V
 Verificare che la protezione contro l'analisi della potenza includa l'iniezione di rumore, il filtraggio della linea di alimentazione e schemi di esecuzione randomizzati per l'hardware AI.
 #4.18.3    Livello: 3    Ruolo: D/V
 Verificare che la mitigazione dei canali laterali basati sulla cache utilizzi la partizione della cache, la randomizzazione e le istruzioni di flush per prevenire la fuoriuscita di informazioni.
 #4.18.4    Livello: 3    Ruolo: D/V
 Verificare che la protezione contro le emanazioni elettromagnetiche includa schermatura, filtraggio del segnale e elaborazione casualizzata per prevenire attacchi di tipo TEMPEST.
 #4.18.5    Livello: 3    Ruolo: D/V
 Verificare che le difese contro i canali laterali microarchitetturali includano controlli sull'esecuzione speculativa e l'offuscamento dei modelli di accesso alla memoria.

---

### C4.19 Sicurezza dell'Hardware Neuromorfico e AI Specializzato

Proteggere le architetture hardware emergenti dell'IA, inclusi chip neuromorfici, FPGA, ASIC personalizzati e sistemi di calcolo ottico.

 #4.19.1    Livello: 3    Ruolo: D/V
 Verificare che la sicurezza del chip neuromorfico includa la crittografia dei modelli di spike, la protezione del peso sinaptico e la convalida basata sull'hardware delle regole di apprendimento.
 #4.19.2    Livello: 3    Ruolo: D/V
 Verificare che gli accelerator AI basati su FPGA implementino la crittografia del bitstream, meccanismi anti-manomissione e caricamento sicuro della configurazione con aggiornamenti autenticati.
 #4.19.3    Livello: 3    Ruolo: D/V
 Verificare che la sicurezza ASIC personalizzata includa processori di sicurezza on-chip, root of trust hardware e archiviazione sicura delle chiavi con rilevamento delle manomissioni.
 #4.19.4    Livello: 3    Ruolo: D/V
 Verificare che i sistemi di calcolo ottico implementino crittografia ottica quantisticamente sicura, commutazione fotonica sicura e elaborazione dei segnali ottici protetta.
 #4.19.5    Livello: 3    Ruolo: D/V
 Verificare che i chip AI ibridi analogico-digitali includano computazione analogica sicura, memorizzazione protetta dei pesi e conversione da analogico a digitale autenticata.

---

### C4.20 Infrastruttura di Calcolo per la Privacy

Implementare controlli infrastrutturali per il calcolo che preserva la privacy al fine di proteggere i dati sensibili durante l'elaborazione e l'analisi AI.

 #4.20.1    Livello: 3    Ruolo: D/V
 Verificare che l'infrastruttura di crittografia omomorfica consenta il calcolo crittografato su carichi di lavoro AI sensibili con verifica dell'integrità crittografica e monitoraggio delle prestazioni.
 #4.20.2    Livello: 3    Ruolo: D/V
 Verificare che i sistemi di recupero di informazioni private permettano interrogazioni al database senza rivelare i modelli di query tramite la protezione crittografica dei modelli di accesso.
 #4.20.3    Livello: 3    Ruolo: D/V
 Verificare che i protocolli di computazione multipartita sicura consentano inferenze AI preservanti la privacy senza esporre input individuali o computazioni intermedie.
 #4.20.4    Livello: 3    Ruolo: D/V
 Verificare che la gestione delle chiavi che preserva la privacy includa la generazione distribuita delle chiavi, la crittografia a soglia e la rotazione sicura delle chiavi con protezione supportata da hardware.
 #4.20.5    Livello: 3    Ruolo: D/V
 Verificare che le prestazioni del calcolo in modalità privacy-preserving siano ottimizzate tramite batching, caching e accelerazione hardware, mantenendo al contempo le garanzie di sicurezza crittografica.

---

### C4.15 Sicurezza dell'integrazione cloud e distribuzione ibrida del framework agenti

Controlli di sicurezza per framework agenti integrati nel cloud con architetture ibride on-premises/cloud.

 #4.15.1    Livello: 1    Ruolo: D/V
 Verificare che l'integrazione dello storage cloud utilizzi la crittografia end-to-end con gestione delle chiavi controllata dall'agente.
 #4.15.2    Livello: 2    Ruolo: D/V
 Verificare che i confini di sicurezza del deployment ibrido siano chiaramente definiti con canali di comunicazione criptati.
 #4.15.3    Livello: 2    Ruolo: D/V
 Verificare che l'accesso alle risorse cloud includa la verifica zero-trust con autenticazione continua.
 #4.15.4    Livello: 3    Ruolo: D/V
 Verificare che i requisiti di residenza dei dati siano applicati mediante attestazione crittografica delle posizioni di archiviazione.
 #4.15.5    Livello: 3    Ruolo: D/V
 Verificare che le valutazioni di sicurezza del provider cloud includano la modellazione delle minacce specifica per l’agente e la valutazione del rischio.

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

## Controllo Accessi C5 e Identità per Componenti e Utenti AI

### Obiettivo di Controllo

Un controllo di accesso efficace per i sistemi di intelligenza artificiale richiede una gestione robusta dell'identità, un'autorizzazione consapevole del contesto e un'applicazione in tempo reale secondo i principi del zero-trust. Questi controlli garantiscono che esseri umani, servizi e agenti autonomi interagiscano solo con modelli, dati e risorse computazionali all'interno di ambiti esplicitamente concessi, con capacità di verifica continua e di audit.

---

### C5.1 Gestione dell'Identità e Autenticazione

Stabilire identità crittograficamente supportate per tutte le entità con autenticazione multi-fattore per le operazioni privilegiate.

 #5.1.1    Livello: 1    Ruolo: D/V
 Verificare che tutti gli utenti umani e i principali servizi si autentichino tramite un provider di identità aziendale centralizzato (IdP) utilizzando i protocolli OIDC/SAML con mappature uniche da identità a token (niente account o credenziali condivisi).
 #5.1.2    Livello: 1    Ruolo: D/V
 Verificare che le operazioni ad alto rischio (implementazione del modello, esportazione dei pesi, accesso ai dati di addestramento, modifiche alla configurazione di produzione) richiedano l'autenticazione a più fattori o un'autenticazione avanzata con rivalidazione della sessione.
 #5.1.3    Livello: 2    Ruolo: D
 Verificare che i nuovi responsabili siano sottoposti a un processo di verifica dell'identità conforme a NIST 800-63-3 IAL-2 o a standard equivalenti prima di ricevere l'accesso ai sistemi di produzione.
 #5.1.4    Livello: 2    Ruolo: V
 Verificare che le revisioni degli accessi siano effettuate trimestralmente con rilevamento automatico degli account inattivi, applicazione della rotazione delle credenziali e flussi di lavoro per la de-provisioning.
 #5.1.5    Livello: 3    Ruolo: D/V
 Verificare che gli agenti AI federati si autentichino tramite asserzioni JWT firmate che abbiano una durata massima di 24 ore e includano una prova crittografica dell'origine.

---

### C5.2 Autorizzazione delle risorse e minimo privilegio

Implementare controlli di accesso granulare per tutte le risorse AI con modelli di autorizzazione espliciti e registri di controllo.

 #5.2.1    Livello: 1    Ruolo: D/V
 Verificare che ogni risorsa AI (dataset, modelli, endpoint, raccolte di vettori, indici di embedding, istanze di calcolo) applichi controlli di accesso basati sui ruoli con liste di permessi esplicite e politiche di negazione predefinite.
 #5.2.2    Livello: 1    Ruolo: D/V
 Verificare che i principi di minimo privilegio siano applicati per impostazione predefinita agli account di servizio, con permessi iniziali in sola lettura e una giustificazione aziendale documentata richiesta per l’accesso in scrittura.
 #5.2.3    Livello: 1    Ruolo: V
 Verificare che tutte le modifiche al controllo degli accessi siano collegate a richieste di modifica approvate e registrate in modo immutabile con timestamp, identità degli attori, identificatori delle risorse e delta di permessi.
 #5.2.4    Livello: 2    Ruolo: D
 Verificare che le etichette di classificazione dei dati (PII, PHI, controllati per l'esportazione, proprietari) si propaghino automaticamente alle risorse derivate (embedding, cache dei prompt, output del modello) con un'applicazione coerente delle policy.
 #5.2.5    Livello: 2    Ruolo: D/V
 Verificare che i tentativi di accesso non autorizzati e gli eventi di escalation dei privilegi generino avvisi in tempo reale con metadata contestuali ai sistemi SIEM entro 5 minuti.

---

### C5.3 Valutazione Dinamica delle Politiche

Distribuire motori di controllo degli accessi basato su attributi (ABAC) per decisioni di autorizzazione contestuali con capacità di audit.

 #5.3.1    Livello: 1    Ruolo: D/V
 Verificare che le decisioni di autorizzazione siano esternalizzate a un motore di policy dedicato (OPA, Cedar o equivalente) accessibile tramite API autenticate con protezione di integrità crittografica.
 #5.3.2    Livello: 1    Ruolo: D/V
 Verificare che le politiche valutino gli attributi dinamici in fase di esecuzione, inclusi il livello di autorizzazione dell'utente, la classificazione della sensibilità della risorsa, il contesto della richiesta, l'isolamento del tenant e i vincoli temporali.
 #5.3.3    Livello: 2    Ruolo: D
 Verificare che le definizioni delle policy siano versionate, sottoposte a revisione tra pari e validate tramite test automatizzati nelle pipeline CI/CD prima del deployment in produzione.
 #5.3.4    Livello: 2    Ruolo: V
 Verificare che i risultati della valutazione delle policy includano ragioni decisionali strutturate e siano trasmessi ai sistemi SIEM per l'analisi di correlazione e la reportistica di conformità.
 #5.3.5    Livello: 3    Ruolo: D/V
 Verificare che i valori del tempo di vita (TTL) della cache delle policy non superino i 5 minuti per le risorse ad alta sensibilità e 1 ora per le risorse standard con capacità di invalidamento della cache.

---

### C5.4 Applicazione della Sicurezza al Momento della Query

Implementare controlli di sicurezza a livello di database con filtraggio obbligatorio e politiche di sicurezza a livello di riga.

 #5.4.1    Livello: 1    Ruolo: D/V
 Verificare che tutte le query sui database vettoriali e SQL includano i filtri di sicurezza obbligatori (ID tenant, etichette di sensibilità, ambito utente) applicati a livello del motore di database e non nel codice dell'applicazione.
 #5.4.2    Livello: 1    Ruolo: D/V
 Verificare che le politiche di sicurezza a livello di riga (RLS) e la mascheratura a livello di campo siano abilitate con l’ereditarietà delle policy per tutti i database vettoriali, gli indici di ricerca e i set di dati di addestramento.
 #5.4.3    Livello: 2    Ruolo: D
 Verificare che le valutazioni di autorizzazione fallite impediscano gli "attacchi del dodicesimo confuso" interrompendo immediatamente le query e restituendo codici di errore di autorizzazione espliciti invece di restituire insiemi di risultati vuoti.
 #5.4.4    Livello: 2    Ruolo: V
 Verificare che la latenza nella valutazione delle politiche venga monitorata continuamente con allarmi automatizzati per condizioni di timeout che potrebbero consentire la bypass dell'autorizzazione.
 #5.4.5    Livello: 3    Ruolo: D/V
 Verificare che i meccanismi di ritentativo delle query rivalutino le politiche di autorizzazione per tenere conto delle modifiche dinamiche dei permessi all'interno delle sessioni utente attive.

---

### Filtraggio output C5.5 e prevenzione della perdita di dati

Implementare controlli post-elaborazione per prevenire l'esposizione non autorizzata dei dati nei contenuti generati dall'IA.

 #5.5.1    Livello: 1    Ruolo: D/V
 Verificare che i meccanismi di filtraggio post-inferenza eseguano la scansione e la redazione di informazioni personali identificabili (PII), informazioni classificate e dati proprietari non autorizzati prima di fornire il contenuto ai richiedenti.
 #5.5.2    Livello: 1    Ruolo: D/V
 Verificare che citazioni, riferimenti e attribuzioni di fonte nei risultati del modello siano convalidati rispetto ai diritti dell’utilizzatore e rimossi se viene rilevato un accesso non autorizzato.
 #5.5.3    Livello: 2    Ruolo: D
 Verificare che le restrizioni sul formato di output (PDF sanificati, immagini senza metadati, tipi di file approvati) siano applicate in base ai livelli di autorizzazione degli utenti e alle classificazioni dei dati.
 #5.5.4    Livello: 2    Ruolo: V
 Verificare che gli algoritmi di redazione siano deterministici, controllati nelle versioni e mantengano registri di audit per supportare le indagini di conformità e l'analisi forense.
 #5.5.5    Livello: 3    Ruolo: V
 Verificare che gli eventi di redazione ad alto rischio generino log adattivi che includano hash crittografici del contenuto originale per il recupero forense senza esposizione dei dati.

---

### C5.6 Isolamento Multi-Tenant

Garantire l'isolamento crittografico e logico tra i tenant in un'infrastruttura AI condivisa.

 #5.6.1    Livello: 1    Ruolo: D/V
 Verificare che gli spazi di memoria, gli archivi di embedding, le voci della cache e i file temporanei siano segregati per namespace per ogni tenant con una cancellazione sicura alla eliminazione del tenant o alla terminazione della sessione.
 #5.6.2    Livello: 1    Ruolo: D/V
 Verificare che ogni richiesta API includa un identificatore tenant autenticato che sia convalidato crittograficamente rispetto al contesto della sessione e alle autorizzazioni dell'utente.
 #5.6.3    Livello: 2    Ruolo: D
 Verificare che le policy di rete implementino regole di negazione predefinite per la comunicazione tra tenant all'interno di service mesh e piattaforme di orchestrazione di container.
 #5.6.4    Livello: 3    Ruolo: D
 Verificare che le chiavi di crittografia siano uniche per ogni tenant con supporto per chiavi gestite dal cliente (CMK) e isolamento crittografico tra gli archivi di dati dei tenant.

---

### C5.7 Autorizzazione dell'Agente Autonomo

Controllo delle autorizzazioni per agenti AI e sistemi autonomi tramite token di capacità con ambito e autorizzazione continua.

 #5.7.1    Livello: 1    Ruolo: D/V
 Verificare che gli agenti autonomi ricevano token di capacità delimitati che enumerano esplicitamente le azioni consentite, le risorse accessibili, i limiti temporali e i vincoli operativi.
 #5.7.2    Livello: 1    Ruolo: D/V
 Verificare che le funzionalità ad alto rischio (accesso al file system, esecuzione di codice, chiamate API esterne, transazioni finanziarie) siano disabilitate di default e richiedano autorizzazioni esplicite per l'attivazione con giustificazioni aziendali.
 #5.7.3    Livello: 2    Ruolo: D
 Verificare che i token di capacità siano vincolati alle sessioni utente, includano la protezione dell'integrità crittografica e garantiscano che non possano essere memorizzati o riutilizzati in scenari offline.
 #5.7.4    Livello: 2    Ruolo: V
 Verificare che le azioni avviate dall'agente siano soggette a una seconda autorizzazione tramite il motore di politica ABAC con valutazione del contesto completo e registrazione dell'audit.
 #5.7.5    Livello: 3    Ruolo: V
 Verificare che le condizioni di errore dell'agente e la gestione delle eccezioni includano informazioni sull'ambito delle capacità per supportare l'analisi degli incidenti e le indagini forensi.

---

### Riferimenti

#### Standard e Framework

NIST SP 800-63-3: Digital Identity Guidelines
Zero Trust Architecture – NIST SP 800-207
OWASP Application Security Verification Standard (AISVS)
​
#### Guide all'implementazione

Identity and Access Management in the AI Era: 2025 Guide – IDSA
Attribute-Based Access Control with OPA – Permify
How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS
​
#### Sicurezza Specifica per l'Intelligenza Artificiale

Row Level Security in Vector DBs for RAG – Bluetuple.ai
Tenant Isolation in Multi-Tenant Systems – WorkOS
Handling AI Agent Permissions – Stytch
OWASP Top 10 for Large Language Model Applications

## C6 Sicurezza della catena di approvvigionamento per modelli, framework e dati

### Obiettivo di Controllo

Gli attacchi alla supply‑chain dell'IA sfruttano modelli, framework o dataset di terze parti per inserire backdoor, bias o codice vulnerabile. Questi controlli offrono tracciabilità end‑to‑end, gestione delle vulnerabilità e monitoraggio per proteggere l'intero ciclo di vita del modello.

---

### C6.1 Verifica e Provenienza del Modello Preaddestrato

Valutare e autenticare le origini, le licenze e i comportamenti nascosti dei modelli di terze parti prima di qualsiasi fine-tuning o distribuzione.

 #6.1.1    Livello: 1    Ruolo: D/V
 Verificare che ogni artefatto di modello di terze parti includa un record di provenienza firmato che identifichi il repository di origine e l'hash del commit.
 #6.1.2    Livello: 1    Ruolo: D/V
 Verificare che i modelli siano scansionati per rilevare layer dannosi o trigger Trojan utilizzando strumenti automatizzati prima dell'importazione.
 #6.1.3    Livello: 2    Ruolo: D
 Verificare che il fine-tuning con transfer learning superi la valutazione di tipo adversariale per rilevare comportamenti nascosti.
 #6.1.4    Livello: 2    Ruolo: V
 Verificare che le licenze del modello, i tag di controllo delle esportazioni e le dichiarazioni sull'origine dei dati siano registrati in una voce ML‑BOM.
 #6.1.5    Livello: 3    Ruolo: D/V
 Verificare che i modelli ad alto rischio (pesi caricati pubblicamente, creatori non verificati) rimangano in quarantena fino alla revisione e all'approvazione umana.

---

### C6.2 Scansione di Framework e Librerie

Scansionare continuamente i framework e le librerie di machine learning per CVE e codice dannoso per mantenere sicuro lo stack di runtime.

 #6.2.1    Livello: 1    Ruolo: D/V
 Verificare che le pipeline CI eseguano scanner di dipendenze su framework di AI e librerie critiche.
 #6.2.2    Livello: 1    Ruolo: D/V
 Verificare che le vulnerabilità critiche (CVSS ≥ 7.0) blocchino la promozione delle immagini in produzione.
 #6.2.3    Livello: 2    Ruolo: D
 Verificare che l'analisi statica del codice venga eseguita sulle librerie ML forkate o distribuite.
 #6.2.4    Livello: 2    Ruolo: V
 Verificare che le proposte di aggiornamento del framework includano una valutazione dell'impatto sulla sicurezza con riferimento ai feed pubblici CVE.
 #6.2.5    Livello: 3    Ruolo: V
 Verificare che i sensori di runtime segnalino i caricamenti di librerie dinamiche imprevisti che deviano dal SBOM firmato.

---

### C6.3 Blocco e Verifica delle Dipendenze

Blocca ogni dipendenza su digest immutabili e riproduci le build per garantire artefatti identici e privi di manomissioni.

 #6.3.1    Livello: 1    Ruolo: D/V
 Verificare che tutti i gestori di pacchetti applicano il vincolo delle versioni tramite lockfile.
 #6.3.2    Livello: 1    Ruolo: D/V
 Verificare che nei riferimenti ai container vengano utilizzati digest immutabili invece di tag mutabili.
 #6.3.3    Livello: 2    Ruolo: D
 Verificare che i controlli di build riproducibile confrontino gli hash tra le esecuzioni CI per garantire output identici.
 #6.3.4    Livello: 2    Ruolo: V
 Verificare che le attestazioni di build siano conservate per 18 mesi per la tracciabilità dell’audit.
 #6.3.5    Livello: 3    Ruolo: D
 Verificare che le dipendenze scadute attivino PR automatizzate per aggiornare o forkare le versioni vincolate.

---

### C6.4 Applicazione della Fonte Affidabile

Consenti il download di artefatti solo da fonti approvate dall'organizzazione e verificate crittograficamente, e blocca tutto il resto.

 #6.4.1    Livello: 1    Ruolo: D/V
 Verificare che i pesi del modello, i dataset e i container vengano scaricati solo da domini approvati o registry interni.
 #6.4.2    Livello: 1    Ruolo: D/V
 Verificare che le firme Sigstore/Cosign convalidino l'identità del publisher prima che gli artifact vengano memorizzati nella cache locale.
 #6.4.3    Livello: 2    Ruolo: D
 Verificare che i proxy di uscita blocchino i download di artifact non autenticati per applicare la politica della fonte attendibile.
 #6.4.4    Livello: 2    Ruolo: V
 Verificare che le liste di autorizzazione del repository vengano revisionate trimestralmente con evidenza della giustificazione aziendale per ciascuna voce.
 #6.4.5    Livello: 3    Ruolo: V
 Verificare che le violazioni delle policy attivino la messa in quarantena degli artifact e il rollback delle esecuzioni della pipeline dipendenti.

---

### C6.5 Valutazione del Rischio dei Dataset di Terze Parti

Valutare i dataset esterni per avvelenamento, pregiudizi e conformità legale, e monitorarli durante tutto il loro ciclo di vita.

 #6.5.1    Livello: 1    Ruolo: D/V
 Verificare che i dataset esterni siano sottoposti a una valutazione del rischio di avvelenamento (ad esempio, fingerprinting dei dati, rilevamento di valori anomali).
 #6.5.2    Livello: 1    Ruolo: D
 Verificare che le metriche di bias (parità demografica, pari opportunità) siano calcolate prima dell'approvazione del dataset.
 #6.5.3    Livello: 2    Ruolo: V
 Verifica che le provenienze e i termini di licenza per i dataset siano registrati nelle voci ML‑BOM.
 #6.5.4    Livello: 2    Ruolo: V
 Verificare che il monitoraggio periodico rilevi deriva o corruzione nei dataset ospitati.
 #6.5.5    Livello: 3    Ruolo: D
 Verificare che i contenuti non consentiti (copyright, dati personali identificabili) vengano rimossi tramite pulizia automatizzata prima dell'addestramento.

---

### C6.6 Monitoraggio degli Attacchi alla Catena di Fornitura

Rileva precocemente le minacce alla supply chain attraverso feed CVE, analisi dei log di audit e simulazioni red team.

 #6.6.1    Livello: 1    Ruolo: V
 Verificare che i log di audit CI/CD vengano trasmessi ai rilevamenti SIEM per identificare prelievi anomali di pacchetti o passaggi di build manomessi.
 #6.6.2    Livello: 2    Ruolo: D
 Verificare che i playbook di risposta agli incidenti includano procedure di rollback per modelli o librerie compromessi.
 #6.6.3    Livello: 3    Ruolo: V
 Verificare che l'arricchimento delle informazioni sulle minacce etichetti indicatori specifici per l'apprendimento automatico (ad esempio, IoC di avvelenamento del modello) nella classificazione degli alert.

---

### C6.7 ML-BOM per Artefatti Modello

Generare e firmare SBOM specifici per il ML (ML-BOM) dettagliati in modo che i consumatori a valle possano verificare l'integrità dei componenti al momento della distribuzione.

 #6.7.1    Livello: 1    Ruolo: D/V
 Verificare che ogni artefatto del modello pubblichi un ML-BOM che elenchi dataset, pesi, iperparametri e licenze.
 #6.7.2    Livello: 1    Ruolo: D/V
 Verificare che la generazione di ML‑BOM e la firma Cosign siano automatizzate nel CI e richieste per la fusione.
 #6.7.3    Livello: 2    Ruolo: D
 Verificare che i controlli di completezza ML‑BOM interrompano la compilazione se manca qualsiasi metadato del componente (hash, licenza).
 #6.7.4    Livello: 2    Ruolo: V
 Verificare che i consumatori a valle possano interrogare gli ML-BOM tramite API per convalidare i modelli importati al momento del deploy.
 #6.7.5    Livello: 3    Ruolo: V
 Verificare che i ML-BOM siano versionati e confrontati per rilevare modifiche non autorizzate.

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

## Comportamento del Modello C7, Controllo dell'Uscita e Garanzia di Sicurezza

### Obiettivo di Controllo

I risultati del modello devono essere strutturati, affidabili, sicuri, spiegabili e costantemente monitorati in produzione. Questo riduce le allucinazioni, le fughe di dati personali, i contenuti dannosi e le azioni incontrollate, aumentando al contempo la fiducia degli utenti e la conformità normativa.

---

### C7.1 Applicazione del formato di output

Schemi rigorosi, decodifica vincolata e validazione downstream fermano contenuti malformati o dannosi prima che si propaghino.

 #7.1.1    Livello: 1    Ruolo: D/V
 Verificare che gli schemi di risposta (ad esempio, JSON Schema) siano forniti nel prompt di sistema e che ogni output venga automaticamente convalidato; gli output non conformi attivano la riparazione o il rifiuto.
 #7.1.2    Livello: 1    Ruolo: D/V
 Verificare che la decodifica vincolata (token di stop, regex, max-token) sia abilitata per prevenire overflow o canali laterali di iniezione nel prompt.
 #7.1.3    Livello: 2    Ruolo: D/V
 Verificare che i componenti a valle considerino gli output come non attendibili e li convalidino rispetto agli schemi o utilizzino de-serializzatori sicuri contro le injection.
 #7.1.4    Livello: 3    Ruolo: V
 Verificare che gli eventi di output improprio siano registrati, soggetti a limitazione della frequenza e resi visibili al monitoraggio.

---

### C7.2 Rilevamento e Mitigazione delle Allucinazioni

La stima dell'incertezza e le strategie di fallback limitano le risposte inventate.

 #7.2.1    Livello: 1    Ruolo: D/V
 Verificare che le log-probabilità a livello di token, la coerenza autonoma dell'ensemble o i rilevatori di allucinazioni messa a punto assegnino un punteggio di confidenza a ogni risposta.
 #7.2.2    Livello: 1    Ruolo: D/V
 Verificare che le risposte al di sotto di una soglia di confidenza configurabile attivino flussi di lavoro di fallback (ad esempio, generazione aumentata dal recupero, modello secondario o revisione umana).
 #7.2.3    Livello: 2    Ruolo: D/V
 Verificare che gli incidenti di allucinazione siano etichettati con metadati sulla causa principale e inseriti nelle pipeline di post-mortem e di fine-tuning.
 #7.2.4    Livello: 3    Ruolo: D/V
 Verificare che le soglie e i rilevatori vengano ricalibrati dopo aggiornamenti importanti del modello o della base di conoscenza.
 #7.2.5    Livello: 3    Ruolo: V
 Verificare che le visualizzazioni della dashboard traccino i tassi di allucinazione.

---

### C7.3 Filtraggio di Sicurezza e Privacy in Output

I filtri di policy e la copertura del red team proteggono gli utenti e i dati riservati.

 #7.3.1    Livello: 1    Ruolo: D/V
 Verificare che i classificatori pre e post-generazione blocchino contenuti di odio, molestie, autolesionismo, estremismo e contenuti sessualmente espliciti in conformità con la policy.
 #7.3.2    Livello: 1    Ruolo: D/V
 Verificare che il rilevamento di PII/PCI e la redazione automatica vengano eseguiti su ogni risposta; le violazioni comportano la segnalazione di un incidente sulla privacy.
 #7.3.3    Livello: 2    Ruolo: D
 Verificare che i tag di riservatezza (ad esempio, segreti commerciali) si propaghino attraverso le modalità per prevenire la fuga di informazioni in testi, immagini o codice.
 #7.3.4    Livello: 3    Ruolo: D/V
 Verificare che i tentativi di bypassare il filtro o le classificazioni ad alto rischio richiedano un'approvazione secondaria o una ri-autenticazione dell'utente.
 #7.3.5    Livello: 3    Ruolo: D/V
 Verificare che le soglie di filtraggio riflettano le giurisdizioni legali e il contesto di età/ruolo dell'utente.

---

### C7.4 Limitazione dell'Output e delle Azioni

I limiti di velocità e i gate di approvazione prevengono abusi e autonomia eccessiva.

 #7.4.1    Livello: 1    Ruolo: D
 Verificare che le quote per utente e per chiave API limitino le richieste, i token e i costi con un back-off esponenziale sugli errori 429.
 #7.4.2    Livello: 1    Ruolo: D/V
 Verificare che le azioni privilegiate (scritture di file, esecuzione di codice, chiamate di rete) richiedano l'approvazione basata su policy o l'intervento umano.
 #7.4.3    Livello: 2    Ruolo: D/V
 Verifica che i controlli di coerenza cross-modale garantiscano che immagini, codice e testo generati per la stessa richiesta non possano essere utilizzati per introdurre contenuti dannosi.
 #7.4.4    Livello: 2    Ruolo: D
 Verificare che la profondità di delega degli agenti, i limiti di ricorsione e le liste degli strumenti consentiti siano configurati esplicitamente.
 #7.4.5    Livello: 3    Ruolo: V
 Verificare che la violazione dei limiti generi eventi di sicurezza strutturati per l'ingestione nel SIEM.

---

### C7.5 Spiegabilità dell'Output

I segnali trasparenti migliorano la fiducia degli utenti e il debug interno.

 #7.5.1    Livello: 2    Ruolo: D/V
 Verificare che i punteggi di confidenza rivolti all’utente o i brevi riassunti delle motivazioni siano esposti quando la valutazione del rischio lo ritiene appropriato.
 #7.5.2    Livello: 2    Ruolo: D/V
 Verificare che le spiegazioni generate evitino di rivelare prompt di sistema sensibili o dati proprietari.
 #7.5.3    Livello: 3    Ruolo: D
 Verificare che il sistema acquisisca le log-probabilità a livello di token o le mappe di attenzione e le memorizzi per ispezioni autorizzate.
 #7.5.4    Livello: 3    Ruolo: V
 Verificare che gli artefatti di spiegabilità siano sottoposti a controllo delle versioni insieme alle release dei modelli per garantire la tracciabilità.

---

### C7.6 Integrazione del Monitoraggio

L'osservabilità in tempo reale chiude il ciclo tra sviluppo e produzione.

 #7.6.1    Livello: 1    Ruolo: D
 Verificare che le metriche (violazioni dello schema, tasso di allucinazioni, tossicità, fughe di dati PII, latenza, costo) vengano trasmesse a una piattaforma centrale di monitoraggio.
 #7.6.2    Livello: 1    Ruolo: V
 Verificare che le soglie di allerta siano definite per ogni metrica di sicurezza, con percorsi di escalation per il personale di reperibilità.
 #7.6.3    Livello: 2    Ruolo: V
 Verificare che i cruscotti mettano in relazione le anomalie di output con il modello/versione, il flag delle funzionalità e le modifiche ai dati upstream.
 #7.6.4    Livello: 2    Ruolo: D/V
 Verificare che i dati di monitoraggio vengano reinseriti nel processo di retraining, fine-tuning o aggiornamento delle regole all'interno di un flusso di lavoro MLOps documentato.
 #7.6.5    Livello: 3    Ruolo: V
 Verificare che le pipeline di monitoraggio siano sottoposte a penetration test e controllate negli accessi per evitare la fuoriuscita di log sensibili.

---

### 7.7 Salvaguardie per i Media Generativi

Garantire che i sistemi di IA non generino contenuti multimediali illegali, dannosi o non autorizzati, applicando vincoli di policy, convalida dell'output e tracciabilità.

 #7.7.1    Livello: 1    Ruolo: D/V
 Verificare che i prompt di sistema e le istruzioni per l'utente proibiscano esplicitamente la generazione di contenuti deepfake illegali, dannosi o non consensuali (ad esempio, immagini, video, audio).
 #7.7.2    Livello: 2    Ruolo: D/V
 Verificare che i prompt siano filtrati per tentativi di generare imitazioni, deepfake sessualmente espliciti o media che ritraggono persone reali senza consenso.
 #7.7.3    Livello: 2    Ruolo: V
 Verifica che il sistema utilizzi hashing percettivo, rilevamento di watermark o fingerprinting per prevenire la riproduzione non autorizzata di contenuti protetti da copyright.
 #7.7.4    Livello: 3    Ruolo: D/V
 Verificare che tutti i media generati siano firmati crittograficamente, watermarkati o incorporati con metadati di provenienza resistenti alla manomissione per la tracciabilità a valle.
 #7.7.5    Livello: 3    Ruolo: V
 Verificare che i tentativi di bypass (ad esempio, offuscamento del prompt, gergo, formulazioni avversarie) siano rilevati, registrati e soggetti a limitazione di frequenza; gli abusi ripetuti devono essere segnalati ai sistemi di monitoraggio.

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

## Sicurezza della Memoria C8, degli Embedding e dei Database Vettoriali

### Obiettivo di Controllo

Gli embeddings e gli store vettoriali agiscono come la "memoria attiva" dei sistemi di AI contemporanei, accettando continuamente dati forniti dagli utenti e riportandoli nei contesti del modello tramite la Generazione Aumentata da Recupero (RAG). Se lasciata senza controllo, questa memoria può divulgare informazioni personali identificabili (PII), violare il consenso o essere invertita per ricostruire il testo originale. L'obiettivo di questa famiglia di controlli è rafforzare le pipeline di memoria e i database vettoriali affinché l'accesso sia a privilegio minimo, gli embeddings siano rispettosi della privacy, i vettori memorizzati scadano o possano essere revocati su richiesta, e la memoria per utente non contamini mai le richieste o le risposte di un altro utente.

---

### C8.1 Controlli di Accesso su Memoria e Indici RAG

Applicare controlli di accesso granulari su ogni collezione vettoriale.

 #8.1.1    Livello: 1    Ruolo: D/V
 Verificare che le regole di controllo accesso a livello di riga/namespace limitino le operazioni di inserimento, eliminazione e interrogazione per tenant, collezione o tag del documento.
 #8.1.2    Livello: 1    Ruolo: D/V
 Verificare che le chiavi API o i JWT contengano richieste con ambito definito (ad esempio, ID delle collezioni, verbi di azione) e che vengano ruotati almeno trimestralmente.
 #8.1.3    Livello: 2    Ruolo: D/V
 Verificare che i tentativi di escalation dei privilegi (ad esempio, query di similarità tra namespace diversi) vengano rilevati e registrati in un SIEM entro 5 minuti.
 #8.1.4    Livello: 2    Ruolo: D/V
 Verificare che il database vettoriale registri nel diario di controllo l'identificatore del soggetto, l'operazione, l'ID/namespace del vettore, la soglia di somiglianza e il conteggio dei risultati.
 #8.1.5    Livello: 3    Ruolo: V
 Verificare che le decisioni di accesso vengano testate per individuare eventuali falle di bypass ogni volta che i motori vengono aggiornati o le regole di suddivisione dell'indice cambiano.

---

### C8.2 Sanitizzazione e Validazione dell'Embedding

Pre-selezionare il testo per dati personali identificabili (PII), oscurare o pseudonimizzare prima della vettorializzazione, e opzionalmente post-elaborare gli embedding per rimuovere segnali residui.

 #8.2.1    Livello: 1    Ruolo: D/V
 Verificare che i dati PII e i dati regolamentati siano rilevati tramite classificatori automatici e mascherati, tokenizzati o eliminati prima dell'embedding.
 #8.2.2    Livello: 1    Ruolo: D
 Verificare che le pipeline di embedding rifiutino o mettano in quarantena gli input contenenti codice eseguibile o artefatti non UTF-8 che potrebbero compromettere l'indice.
 #8.2.3    Livello: 2    Ruolo: D/V
 Verificare che venga applicata la sanificazione della privacy differenziale locale o metrica agli embeddings delle frasi la cui distanza da qualsiasi token PII noto scende al di sotto di una soglia configurabile.
 #8.2.4    Livello: 2    Ruolo: V
 Verificare che l'efficacia della sanitizzazione (ad esempio, il richiamo della redazione delle PII, la deriva semantica) venga convalidata almeno ogni sei mesi rispetto a corpus di riferimento.
 #8.2.5    Livello: 3    Ruolo: D/V
 Verifica che le configurazioni di sanitizzazione siano controllate tramite versionamento e che le modifiche vengano sottoposte a revisione tra pari.

---

### C8.3 Scadenza, Revoca e Cancellazione della Memoria

Il GDPR "diritto all'oblio" e leggi simili richiedono la cancellazione tempestiva; pertanto, gli archivi vettoriali devono supportare TTL, eliminazioni definitive e tomb-stoning affinché i vettori revocati non possano essere recuperati o reindicizzati.

 #8.3.1    Livello: 1    Ruolo: D/V
 Verificare che ogni vettore e record di metadata possieda un TTL o un’etichetta di conservazione esplicita rispettata dai processi automatici di pulizia.
 #8.3.2    Livello: 1    Ruolo: D/V
 Verificare che le richieste di eliminazione avviate dall'utente cancellino vettori, metadati, copie della cache e indici derivati entro 30 giorni.
 #8.3.3    Livello: 2    Ruolo: D
 Verificare che le eliminazioni logiche siano seguite dalla cancellazione crittografica dei blocchi di archiviazione se l'hardware lo supporta, oppure dalla distruzione della chiave del key vault.
 #8.3.4    Livello: 3    Ruolo: D/V
 Verificare che i vettori scaduti siano esclusi dai risultati della ricerca dei vicini più prossimi in meno di 500 ms dopo la scadenza.

---

### C8.4 Prevenire l'inversione e la fuoriuscita dell'embedding

Le recenti difese—sovrapposizione del rumore, reti di proiezione, perturbazione dei neuroni della privacy e crittografia a livello di applicazione—possono ridurre i tassi di inversione a livello di token sotto il 5%.

 #8.4.1    Livello: 1    Ruolo: V
 Verificare che esista un modello di minaccia formale che copra gli attacchi di inversione, di membership e di inferenza degli attributi e che venga revisionato annualmente.
 #8.4.2    Livello: 2    Ruolo: D/V
 Verificare che la crittografia a livello applicativo o la crittografia ricercabile proteggano i vettori da letture dirette da parte degli amministratori dell'infrastruttura o del personale cloud.
 #8.4.3    Livello: 3    Ruolo: V
 Verificare che i parametri di difesa (ε per DP, rumore σ, rango di proiezione k) bilancino la privacy ≥ 99 % protezione del token e l’utilità ≤ 3 % perdita di accuratezza.
 #8.4.4    Livello: 3    Ruolo: D/V
 Verificare che le metriche di resilienza all'inversione facciano parte delle soglie di rilascio per gli aggiornamenti del modello, con budget di regressione definiti.

---

### C8.5 Applicazione del Controllo di Ambito per la Memoria Specifica dell'Utente

La perdita di dati tra tenant rimane un rischio principale per RAG: query di similarità filtrate in modo improprio possono far emergere documenti privati di un altro cliente.

 #8.5.1    Livello: 1    Ruolo: D/V
 Verificare che ogni query di recupero sia filtrata successivamente dall’ID del tenant/utente prima di essere inviata al prompt LLM.
 #8.5.2    Livello: 1    Ruolo: D
 Verificare che i nomi delle collezioni o gli ID con namespace siano salati per utente o tenant in modo che i vettori non possano collidere tra gli ambiti.
 #8.5.3    Livello: 2    Ruolo: D/V
 Verificare che i risultati di similarità superiori a una soglia di distanza configurabile ma al di fuori dell'ambito del chiamante vengano scartati e attivino avvisi di sicurezza.
 #8.5.4    Livello: 2    Ruolo: V
 Verificare che i test di stress multi-tenant simulino query avversarie che tentano di recuperare documenti fuori ambito e dimostrino assenza totale di perdite.
 #8.5.5    Livello: 3    Ruolo: D/V
 Verificare che le chiavi di crittografia siano separate per tenant, garantendo l'isolamento crittografico anche se lo storage fisico è condiviso.

---

### C8.6 Sicurezza avanzata del sistema di memoria

Controlli di sicurezza per architetture di memoria sofisticate, comprese la memoria episodica, semantica e di lavoro, con requisiti specifici di isolamento e validazione.

 #8.6.1    Livello: 1    Ruolo: D/V
 Verificare che i diversi tipi di memoria (episodica, semantica, di lavoro) abbiano contesti di sicurezza isolati con controlli di accesso basati sui ruoli, chiavi di crittografia separate e modelli di accesso documentati per ciascun tipo di memoria.
 #8.6.2    Livello: 2    Ruolo: D/V
 Verificare che i processi di consolidamento della memoria includano la validazione della sicurezza per prevenire l'iniezione di memorie dannose attraverso la sanificazione dei contenuti, la verifica delle fonti e i controlli di integrità prima dell'archiviazione.
 #8.6.3    Livello: 2    Ruolo: D/V
 Verificare che le query di recupero della memoria siano validate e sanificate per prevenire l'estrazione di informazioni non autorizzate tramite l'analisi dei modelli di query, l'applicazione del controllo degli accessi e il filtraggio dei risultati.
 #8.6.4    Livello: 3    Ruolo: D/V
 Verificare che i meccanismi di oblio della memoria eliminino in modo sicuro le informazioni sensibili con garanzie di cancellazione crittografica utilizzando la cancellazione delle chiavi, la sovrascrittura multipla o la cancellazione sicura basata su hardware con certificati di verifica.
 #8.6.5    Livello: 3    Ruolo: D/V
 Verificare che l'integrità del sistema di memoria sia continuamente monitorata per modifiche non autorizzate o corruzioni mediante checksum, registri di controllo e avvisi automatici quando il contenuto della memoria cambia al di fuori delle operazioni normali.

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

## 9 Sicurezza dell'Orchestrazione Autonoma e dell'Azione Agentica

### Obiettivo di Controllo

Garantire che i sistemi di IA autonomi o multi-agente possano eseguire solo azioni esplicitamente intenzionate, autenticate, verificabili e all’interno di soglie limitate di costo e rischio. Questo protegge contro minacce quali Compromissione del Sistema Autonomo, Uso Improprio degli Strumenti, Rilevamento di Cicli degli Agenti, Dirottamento della Comunicazione, Falsificazione dell’Identità, Manipolazione degli Sciami e Manipolazione dell’Intento.

---

### 9.1 Pianificazione dei compiti dell'agente e budget di ricorsione

Limitare i piani ricorsivi e imporre checkpoint umani per azioni privilegiate.

 #9.1.1    Livello: 1    Ruolo: D/V
 Verificare che la profondità massima della ricorsione, la larghezza, il tempo di orologio a parete, i token e il costo monetario per l'esecuzione di ogni agente siano configurati centralmente e versionati.
 #9.1.2    Livello: 1    Ruolo: D/V
 Verificare che azioni privilegiate o irreversibili (ad esempio, commit di codice, trasferimenti finanziari) richiedano l'approvazione esplicita da parte di un umano tramite un canale verificabile prima dell'esecuzione.
 #9.1.3    Livello: 2    Ruolo: D
 Verificare che i monitor delle risorse in tempo reale attivino l'interruzione del circuito di sicurezza quando viene superata qualsiasi soglia di budget, interrompendo l'espansione ulteriore delle attività.
 #9.1.4    Livello: 2    Ruolo: D/V
 Verificare che gli eventi del circuito di interruzione vengano registrati con l'ID dell'agente, la condizione di attivazione e lo stato del piano acquisito per la revisione forense.
 #9.1.5    Livello: 3    Ruolo: V
 Verificare che i test di sicurezza coprano scenari di esaurimento del budget e di piano fuori controllo, confermando l'arresto sicuro senza perdita di dati.
 #9.1.6    Livello: 3    Ruolo: D
 Verificare che le politiche di budget siano espresse come policy-as-code e applicate nel CI/CD per bloccare la deriva delle configurazioni.

---

### 9.2 Sandboxing dei Plugin degli Strumenti

Isolare le interazioni degli strumenti per prevenire accessi non autorizzati al sistema o l'esecuzione di codice.

 #9.2.1    Livello: 1    Ruolo: D/V
 Verificare che ogni strumento/plugin venga eseguito all'interno di un sistema operativo, container o sandbox a livello WASM con politiche di minimo privilegio per il file-system, la rete e le chiamate di sistema.
 #9.2.2    Livello: 1    Ruolo: D/V
 Verificare che le quote delle risorse del sandbox (CPU, memoria, disco, uscita di rete) e i timeout di esecuzione siano applicati e registrati.
 #9.2.3    Livello: 2    Ruolo: D/V
 Verificare che i binari o i descrittori degli strumenti siano firmati digitalmente; le firme devono essere convalidate prima del caricamento.
 #9.2.4    Livello: 2    Ruolo: V
 Verificare che la telemetria del sandbox fluisca verso un SIEM; le anomalie (ad esempio, tentativi di connessioni in uscita) generano allarmi.
 #9.2.5    Livello: 3    Ruolo: V
 Verificare che i plugin ad alto rischio siano sottoposti a revisione della sicurezza e test di penetrazione prima del rilascio in produzione.
 #9.2.6    Livello: 3    Ruolo: D/V
 Verificare che i tentativi di fuga dalla sandbox vengano bloccati automaticamente e che il plugin responsabile venga messo in quarantena in attesa di indagini.

---

### 9.3 Ciclo Autonomo e Limite dei Costi

Rilevare e fermare la ricorsione incontrollata da agente ad agente e le esplosioni di costi.

 #9.3.1    Livello: 1    Ruolo: D/V
 Verificare che le chiamate tra agenti includano un hop-limit o TTL che il runtime decrementa e applica.
 #9.3.2    Livello: 2    Ruolo: D
 Verificare che gli agenti mantengano un ID univoco del grafo di invocazione per individuare l'auto-invocazione o schemi ciclici.
 #9.3.3    Livello: 2    Ruolo: D/V
 Verificare che i contatori cumulativi delle unità di calcolo e della spesa siano tracciati per ogni catena di richieste; il superamento del limite interrompe la catena.
 #9.3.4    Livello: 3    Ruolo: V
 Verificare che l'analisi formale o il model checking dimostrino l'assenza di ricorsione non limitata nei protocolli degli agenti.
 #9.3.5    Livello: 3    Ruolo: D
 Verificare che gli eventi di interruzione del ciclo generino avvisi e alimentino metriche di miglioramento continuo.

---

### 9.4 Protezione contro l'abuso a livello di protocollo

Canali di comunicazione sicuri tra agenti e sistemi esterni per prevenire il dirottamento o la manipolazione.

 #9.4.1    Livello: 1    Ruolo: D/V
 Verificare che tutti i messaggi agent-to-tool e agent-to-agent siano autenticati (ad esempio, mutual TLS o JWT) e criptati end-to-end.
 #9.4.2    Livello: 1    Ruolo: D
 Verificare che gli schemi siano rigorosamente convalidati; i campi sconosciuti o i messaggi malformati devono essere respinti.
 #9.4.3    Livello: 2    Ruolo: D/V
 Verificare che i controlli di integrità (MAC o firme digitali) coprano l'intero payload del messaggio, compresi i parametri dello strumento.
 #9.4.4    Livello: 2    Ruolo: D
 Verificare che la protezione contro la ripetizione (nonce o finestre temporali) sia applicata a livello di protocollo.
 #9.4.5    Livello: 3    Ruolo: V
 Verificare che le implementazioni dei protocolli vengano sottoposte a fuzzing e analisi statica per individuare difetti di injection o deserializzazione.

---

### 9.5 Identità dell'Agente e Prova di Manomissione

Garantire che le azioni siano attribuibili e le modifiche rilevabili.

 #9.5.1    Livello: 1    Ruolo: D/V
 Verificare che ogni istanza dell'agente possieda un'identità crittografica unica (coppia di chiavi o credenziale basata su hardware).
 #9.5.2    Livello: 2    Ruolo: D/V
 Verificare che tutte le azioni dell'agente siano firmate e corredate da marca temporale; i registri devono includere la firma per la non ripudiabilità.
 #9.5.3    Livello: 2    Ruolo: V
 Verificare che i log a prova di manomissione siano memorizzati in un supporto solo in append o scrittura unica.
 #9.5.4    Livello: 3    Ruolo: D
 Verificare che le chiavi di identità ruotino secondo un programma definito e in presenza di indicatori di compromissione.
 #9.5.5    Livello: 3    Ruolo: D/V
 Verificare che i tentativi di spoofing o di conflitto di chiavi attivino l'immediata quarantena dell'agente interessato.

---

### 9.6 Riduzione del Rischio tramite Sciame Multi-Agente

Mitigare i rischi legati al comportamento collettivo tramite isolamento e modellazione formale della sicurezza.

 #9.6.1    Livello: 1    Ruolo: D/V
 Verificare che gli agenti che operano in diversi domini di sicurezza vengano eseguiti in sandbox di runtime isolati o in segmenti di rete separati.
 #9.6.2    Livello: 3    Ruolo: V
 Verificare che i comportamenti dello sciame siano modellati e formalmente verificati per la vivacità e la sicurezza prima della distribuzione.
 #9.6.3    Livello: 3    Ruolo: D
 Verificare che i monitor di runtime rilevino pattern emergenti di insicurezza (ad esempio, oscillazioni, deadlock) e avviino azioni correttive.

---

### 9.7 Autenticazione / Autorizzazione Utente e Strumento

Implementare controlli di accesso robusti per ogni azione attivata dall'agente.

 #9.7.1    Livello: 1    Ruolo: D/V
 Verificare che gli agenti si autentichino come principali di prima classe ai sistemi a valle, senza mai riutilizzare le credenziali dell'utente finale.
 #9.7.2    Livello: 2    Ruolo: D
 Verificare che le politiche di autorizzazione dettagliate limitino quali strumenti un agente può invocare e quali parametri può fornire.
 #9.7.3    Livello: 2    Ruolo: V
 Verificare che i controlli dei privilegi vengano rivalutati ad ogni chiamata (autorizzazione continua), non solo all'inizio della sessione.
 #9.7.4    Livello: 3    Ruolo: D
 Verificare che i privilegi delegati scadano automaticamente e richiedano un nuovo consenso dopo il timeout o una modifica dell’ambito.

---

### 9.8 Sicurezza della comunicazione agente-agente

Cripta e proteggi l'integrità di tutti i messaggi tra agenti per prevenire l'intercettazione e la manomissione.

 #9.8.1    Livello: 1    Ruolo: D/V
 Verificare che l'autenticazione reciproca e la cifratura con segretezza perfetta in avanti (ad esempio TLS 1.3) siano obbligatorie per i canali degli agenti.
 #9.8.2    Livello: 1    Ruolo: D
 Verificare che l'integrità e l'origine del messaggio siano convalidate prima dell'elaborazione; i fallimenti generano avvisi e scartano il messaggio.
 #9.8.3    Livello: 2    Ruolo: D/V
 Verificare che i metadati di comunicazione (timestamp, numeri di sequenza) vengano registrati per supportare la ricostruzione forense.
 #9.8.4    Livello: 3    Ruolo: V
 Verificare che la verifica formale o il model checking confermino che le macchine a stati del protocollo non possano essere portate in stati non sicuri.

---

### 9.9 Verifica dell'intento e applicazione dei vincoli

Convalidare che le azioni dell'agente siano in linea con l'intento dichiarato dall'utente e i vincoli del sistema.

 #9.9.1    Livello: 1    Ruolo: D
 Verificare che i risolutori di vincoli pre-esecuzione controllino le azioni proposte rispetto a regole di sicurezza e politiche codificate rigidamente.
 #9.9.2    Livello: 2    Ruolo: D/V
 Verificare che le azioni ad alto impatto (finanziarie, distruttive, sensibili alla privacy) richiedano una conferma esplicita dell'intento da parte dell'utente che le avvia.
 #9.9.3    Livello: 2    Ruolo: V
 Verificare che i controlli post-condizione confermino che le azioni completate abbiano raggiunto gli effetti previsti senza effetti collaterali; eventuali discrepanze attivano il rollback.
 #9.9.4    Livello: 3    Ruolo: V
 Verificare che i metodi formali (ad esempio, model checking, dimostrazione di teoremi) o i test basati sulle proprietà dimostrino che i piani degli agenti soddisfano tutti i vincoli dichiarati.
 #9.9.5    Livello: 3    Ruolo: D
 Verificare che gli incidenti di discrepanza di intento o violazione di vincoli alimentino cicli di miglioramento continuo e la condivisione di informazioni sulle minacce.

---

### 9.10 Strategia di Ragionamento dell'Agente Sicurezza

Selezione ed esecuzione sicura di diverse strategie di ragionamento, inclusi gli approcci ReAct, Chain-of-Thought e Tree-of-Thoughts.

 #9.10.1    Livello: 1    Ruolo: D/V
 Verificare che la selezione della strategia di ragionamento utilizzi criteri deterministici (complessità dell'input, tipo di compito, contesto di sicurezza) e che input identici producano selezioni di strategia identiche all'interno dello stesso contesto di sicurezza.
 #9.10.2    Livello: 1    Ruolo: D/V
 Verificare che ogni strategia di ragionamento (ReAct, Catena di Pensieri, Albero dei Pensieri) abbia una convalida degli input dedicata, una sanitizzazione degli output e limiti di tempo di esecuzione specifici per il suo approccio cognitivo.
 #9.10.3    Livello: 2    Ruolo: D/V
 Verificare che le transizioni della strategia di ragionamento siano registrate con il contesto completo, incluse le caratteristiche dell'input, i valori dei criteri di selezione e i metadati di esecuzione per la ricostruzione della traccia di controllo.
 #9.10.4    Livello: 2    Ruolo: D/V
 Verificare che il ragionamento Tree-of-Thoughts includa meccanismi di potatura dei rami che terminano l’esplorazione quando vengono rilevate violazioni di policy, limiti di risorse o confini di sicurezza.
 #9.10.5    Livello: 2    Ruolo: D/V
 Verificare che i cicli ReAct (Reason-Act-Observe) includano punti di controllo di convalida in ogni fase: verifica del passo di ragionamento, autorizzazione dell’azione e sanificazione dell’osservazione prima di procedere.
 #9.10.6    Livello: 3    Ruolo: D/V
 Verificare che le metriche di prestazione della strategia di ragionamento (tempo di esecuzione, utilizzo delle risorse, qualità dell'output) siano monitorate con avvisi automatici quando le metriche deviano oltre le soglie configurate.
 #9.10.7    Livello: 3    Ruolo: D/V
 Verificare che gli approcci di ragionamento ibrido che combinano più strategie mantengano la convalida degli input e i vincoli di output di tutte le strategie costituenti senza aggirare alcun controllo di sicurezza.
 #9.10.8    Livello: 3    Ruolo: D/V
 Verifica che il testing della sicurezza della strategia di ragionamento includa il fuzzing con input malformati, prompt avversari progettati per forzare il cambio di strategia e il testing delle condizioni al limite per ogni approccio cognitivo.

---

### 9.11 Gestione dello Stato del Ciclo di Vita dell'Agente e Sicurezza

Inizializzazione sicura dell'agente, transizioni di stato e terminazione con tracciamenti di audit crittografici e procedure di recupero definite.

 #9.11.1    Livello: 1    Ruolo: D/V
 Verifica che l'inizializzazione dell'agente includa l'istituzione dell'identità crittografica con credenziali supportate da hardware e registri di audit di avvio immutabili contenenti l'ID dell'agente, il timestamp, l'hash della configurazione e i parametri di inizializzazione.
 #9.11.2    Livello: 2    Ruolo: D/V
 Verificare che le transizioni di stato dell'agente siano firmate criptograficamente, contrassegnate con data e ora e registrate con il contesto completo, inclusi gli eventi scatenanti, l'hash dello stato precedente, l'hash del nuovo stato e le convalide di sicurezza eseguite.
 #9.11.3    Livello: 2    Ruolo: D/V
 Verificare che le procedure di spegnimento dell'agente includano la cancellazione sicura della memoria mediante cancellazione crittografica o sovrascrittura multipla, la revoca delle credenziali con notifica all'autorità di certificazione e la generazione di certificati di terminazione a prova di manomissione.
 #9.11.4    Livello: 3    Ruolo: D/V
 Verificare che i meccanismi di recupero degli agenti convalidino l'integrità dello stato utilizzando checksum crittografici (SHA-256 minimo) e tornino a stati noti funzionanti quando viene rilevata una corruzione, con avvisi automatici e requisiti di approvazione manuale.
 #9.11.5    Livello: 3    Ruolo: D/V
 Verificare che i meccanismi di persistenza degli agenti cifrino i dati di stato sensibili con chiavi AES-256 univoche per ogni agente e implementino la rotazione sicura delle chiavi secondo programmi configurabili (massimo 90 giorni) con deployment a tempo zero senza interruzioni.

---

### 9.12 Framework di Sicurezza per l'Integrazione degli Strumenti

Controlli di sicurezza per il caricamento dinamico degli strumenti, l'esecuzione e la convalida dei risultati con processi definiti di valutazione del rischio e approvazione.

 #9.12.1    Livello: 1    Ruolo: D/V
 Verificare che i descrittori degli strumenti includano metadati di sicurezza che specificano i privilegi richiesti (lettura/scrittura/esecuzione), i livelli di rischio (basso/medio/alto), i limiti delle risorse (CPU, memoria, rete) e i requisiti di convalida documentati nei manifest degli strumenti.
 #9.12.2    Livello: 1    Ruolo: D/V
 Verificare che i risultati dell'esecuzione degli strumenti siano convalidati rispetto agli schemi previsti (Schema JSON, Schema XML) e alle politiche di sicurezza (sanificazione dell'output, classificazione dei dati) prima dell'integrazione, con limiti di timeout e procedure di gestione degli errori.
 #9.12.3    Livello: 2    Ruolo: D/V
 Verificare che i log di interazione degli strumenti includano un contesto di sicurezza dettagliato che comprenda l'uso dei privilegi, i modelli di accesso ai dati, il tempo di esecuzione, il consumo di risorse e i codici di ritorno, con una registrazione strutturata per l'integrazione SIEM.
 #9.12.4    Livello: 2    Ruolo: D/V
 Verificare che i meccanismi di caricamento dinamico degli strumenti convalidino le firme digitali utilizzando l'infrastruttura PKI e implementino protocolli di caricamento sicuri con isolamento sandbox e verifica dei permessi prima dell'esecuzione.
 #9.12.5    Livello: 3    Ruolo: D/V
 Verificare che le valutazioni di sicurezza degli strumenti vengano attivate automaticamente per le nuove versioni con gate di approvazione obbligatori che includano analisi statica, test dinamici e revisione da parte del team di sicurezza, con criteri di approvazione documentati e requisiti di SLA.

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

### Obiettivo di Controllo

Garantire che i modelli di AI rimangano affidabili, rispettosi della privacy e resistenti agli abusi quando affrontano attacchi di elusione, inferenza, estrazione o avvelenamento.

---

### 10.1 Allineamento e Sicurezza del Modello

Proteggere contro output dannosi o contrari alle politiche.

 #10.1.1    Livello: 1    Ruolo: D/V
 Verificare che una suite di test di allineamento (prompt del red-team, sonde per jailbreak, contenuti non consentiti) sia gestita con controllo di versione e venga eseguita a ogni rilascio del modello.
 #10.1.2    Livello: 1    Ruolo: D
 Verificare che siano applicate le misure di sicurezza per il rifiuto e il completamento sicuro.
 #10.1.3    Livello: 2    Ruolo: D/V
 Verifica che un valutatore automatico misuri il tasso di contenuti dannosi e segnali regressioni oltre una soglia prestabilita.
 #10.1.4    Livello: 2    Ruolo: D
 Verificare che l'addestramento contro i jailbreak sia documentato e riproducibile.
 #10.1.5    Livello: 3    Ruolo: V
 Verificare che le prove di conformità formale alle politiche o il monitoraggio certificato coprano domini critici.

---

### 10.2 Rafforzamento contro esempi avversari

Aumentare la resilienza agli input manipolati. L'addestramento avversariale robusto e la valutazione tramite benchmark sono le migliori pratiche attuali.

 #10.2.1    Livello: 1    Ruolo: D
 Verificare che i repository del progetto includano configurazioni di addestramento avversariale con semi riproducibili.
 #10.2.2    Livello: 2    Ruolo: D/V
 Verificare che il rilevamento di esempi avversari sollevi avvisi di blocco nelle pipeline di produzione.
 #10.2.4    Livello: 3    Ruolo: V
 Verificare che le prove di robustezza certificate o i certificati di intervallo coprano almeno le principali classi critiche.
 #10.2.5    Livello: 3    Ruolo: V
 Verificare che i test di regressione utilizzino attacchi adattivi per confermare l’assenza di perdita di robustezza misurabile.

---

### 10.3 Mitigazione dell'inferenza di appartenenza

Limitare la capacità di decidere se un record era nei dati di addestramento. La privacy differenziale e la mascheratura del punteggio di confidenza restano le difese conosciute più efficaci.

 #10.3.1    Livello: 1    Ruolo: D
 Verificare che la regolarizzazione dell'entropia per query o la scala della temperatura riducano le predizioni eccessivamente sicure.
 #10.3.2    Livello: 2    Ruolo: D
 Verificare che l'addestramento utilizzi un'ottimizzazione differenzialmente privata con vincolo ε per i dataset sensibili.
 #10.3.3    Livello: 2    Ruolo: V
 Verificare che le simulazioni di attacco (modello shadow o black-box) mostrino un AUC di attacco ≤ 0,60 sui dati di test.

---

### 10.4 Resistenza all'inversione del modello

Prevenire la ricostruzione degli attributi privati. Recenti indagini sottolineano la troncatura dell'output e le garanzie DP come difese pratiche.

 #10.4.1    Livello: 1    Ruolo: D
 Verificare che gli attributi sensibili non vengano mai esportati direttamente; dove necessario, utilizzare bucket o trasformazioni unidirezionali.
 #10.4.2    Livello: 1    Ruolo: D/V
 Verificare che i limiti di frequenza delle query limitino le query adattive ripetute dallo stesso principale.
 #10.4.3    Livello: 2    Ruolo: D
 Verifica che il modello sia addestrato con rumore che preserva la privacy.

---

### 10.5 Difesa contro l'estrazione del modello

Rilevare e scoraggiare la clonazione non autorizzata. Si consigliano watermarking e analisi dei modelli di query.

 #10.5.1    Livello: 1    Ruolo: D
 Verificare che i gateway di inferenza applichino limiti di velocità globali e per singola chiave API, tarati sulla soglia di memorizzazione del modello.
 #10.5.2    Livello: 2    Ruolo: D/V
 Verificare che le statistiche di entropia della query e di pluralità dell’input alimentino un rilevatore di estrazione automatica.
 #10.5.3    Livello: 2    Ruolo: V
 Verificare che i watermark fragili o probabilistici possano essere dimostrati con p < 0,01 in ≤ 1 000 query contro un clone sospetto.
 #10.5.4    Livello: 3    Ruolo: D
 Verificare che le chiavi di watermark e i set di trigger siano memorizzati in un modulo di sicurezza hardware e ruotati annualmente.
 #10.5.5    Livello: 3    Ruolo: V
 Verificare che gli eventi di extraction-alert includano le query offender e siano integrati con i playbook di risposta agli incidenti.

---

### 10.6 Rilevamento di dati avvelenati durante l'inferenza

Identificare e neutralizzare gli input con backdoor o avvelenati.

 #10.6.1    Livello: 1    Ruolo: D
 Verificare che gli input vengano analizzati da un rilevatore di anomalie (ad esempio, STRIP, scoring di coerenza) prima dell'inferenza del modello.
 #10.6.2    Livello: 1    Ruolo: V
 Verificare che le soglie del rilevatore siano regolate su set di validazione puliti/avvelenati per ottenere meno del 5% di falsi positivi.
 #10.6.3    Livello: 2    Ruolo: D
 Verificare che gli input segnalati come avvelenati attivino il soft-blocking e i flussi di lavoro per la revisione umana.
 #10.6.4    Livello: 2    Ruolo: V
 Verificare che i rilevatori siano sottoposti a stress test con attacchi backdoor adattativi e senza trigger.
 #10.6.5    Livello: 3    Ruolo: D
 Verificare che le metriche di efficacia del rilevamento siano registrate e riesaminate periodicamente con nuove informazioni sulle minacce.

---

### 10.7 Adattamento Dinamico della Politica di Sicurezza

Aggiornamenti in tempo reale delle politiche di sicurezza basati su intelligence sulle minacce e analisi comportamentale.

 #10.7.1    Livello: 1    Ruolo: D/V
 Verificare che le politiche di sicurezza possano essere aggiornate dinamicamente senza il riavvio dell’agente mantenendo l’integrità della versione della politica.
 #10.7.2    Livello: 2    Ruolo: D/V
 Verificare che gli aggiornamenti delle politiche siano firmati crittograficamente da personale di sicurezza autorizzato e convalidati prima dell'applicazione.
 #10.7.3    Livello: 2    Ruolo: D/V
 Verificare che le modifiche dinamiche alla policy vengano registrate con tracce di audit complete, includendo giustificazioni, catene di approvazione e procedure di rollback.
 #10.7.4    Livello: 3    Ruolo: D/V
 Verificare che i meccanismi di sicurezza adattivi regolino la sensibilità del rilevamento delle minacce in base al contesto di rischio e ai modelli comportamentali.
 #10.7.5    Livello: 3    Ruolo: D/V
 Verificare che le decisioni di adattamento delle policy siano spiegabili e includano tracce di evidenza per la revisione del team di sicurezza.

---

### 10.8 Analisi della Sicurezza Basata sulla Riflessività

Validazione della sicurezza tramite auto-riflessione dell’agente e analisi meta-cognitiva.

 #10.8.1    Livello: 1    Ruolo: D/V
 Verificare che i meccanismi di riflessione dell'agente includano un'autovalutazione focalizzata sulla sicurezza delle decisioni e delle azioni.
 #10.8.2    Livello: 2    Ruolo: D/V
 Verificare che gli output della riflessione siano convalidati per prevenire la manipolazione dei meccanismi di autovalutazione da parte di input avversari.
 #10.8.3    Livello: 2    Ruolo: D/V
 Verificare che l'analisi meta-cognitiva della sicurezza identifichi potenziali bias, manipolazioni o compromissioni nei processi di ragionamento dell'agente.
 #10.8.4    Livello: 3    Ruolo: D/V
 Verificare che gli avvisi di sicurezza basati sulla riflessione attivino il monitoraggio avanzato e i potenziali flussi di lavoro di intervento umano.
 #10.8.5    Livello: 3    Ruolo: D/V
 Verificare che l'apprendimento continuo dalle riflessioni sulla sicurezza migliori il rilevamento delle minacce senza degradare la funzionalità legittima.

---

### 10.9 Evoluzione e Auto-Miglioramento della Sicurezza

Controlli di sicurezza per sistemi agenti capaci di auto-modifica ed evoluzione.

 #10.9.1    Livello: 1    Ruolo: D/V
 Verificare che le capacità di automodifica siano limitate ad aree designate come sicure con confini di verifica formale.
 #10.9.2    Livello: 2    Ruolo: D/V
 Verificare che le proposte di evoluzione siano sottoposte ad una valutazione dell’impatto sulla sicurezza prima dell’implementazione.
 #10.9.3    Livello: 2    Ruolo: D/V
 Verificare che i meccanismi di auto-miglioramento includano capacità di rollback con verifica dell'integrità.
 #10.9.4    Livello: 3    Ruolo: D/V
 Verificare che la sicurezza del meta-apprendimento prevenga la manipolazione avversaria degli algoritmi di miglioramento.
 #10.9.5    Livello: 3    Ruolo: D/V
 Verificare che il miglioramento auto-ricorsivo sia limitato da vincoli formali di sicurezza con dimostrazioni matematiche di convergenza.

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

## 11 Protezione della Privacy e Gestione dei Dati Personali

### Obiettivo di Controllo

Mantenere rigorose garanzie di privacy lungo l'intero ciclo di vita dell'IA—raccolta, addestramento, inferenza e risposta agli incidenti—affinché i dati personali siano processati solo con chiaro consenso, ambito minimo necessario, cancellazione dimostrabile e garanzie formali di privacy.

---

### 11.1 Anonimizzazione e Minimizzazione dei Dati

 #11.1.1    Livello: 1    Ruolo: D/V
 Verificare che gli identificatori diretti e quasi-identificatori siano rimossi o sottoposti a hashing.
 #11.1.2    Livello: 2    Ruolo: D/V
 Verificare che le verifiche automatizzate misurino la k-anonimato/l-diversità e generino un allarme quando le soglie scendono al di sotto della policy.
 #11.1.3    Livello: 2    Ruolo: V
 Verificare che i report di importanza delle caratteristiche del modello dimostrino l'assenza di fuoriuscita di identificatori oltre ε = 0,01 di informazione mutua.
 #11.1.4    Livello: 3    Ruolo: V
 Verificare che le dimostrazioni formali o la certificazione dei dati sintetici mostrino un rischio di re-identificazione ≤ 0,05 anche in caso di attacchi di linkage.

---

### 11.2 Diritto all'Oblio e Applicazione della Cancellazione

 #11.2.1    Livello: 1    Ruolo: D/V
 Verificare che le richieste di cancellazione dei dati del soggetto si propaghino ai dataset grezzi, ai checkpoint, agli embedding, ai log e ai backup entro i livelli di servizio concordati, inferiori a 30 giorni.
 #11.2.2    Livello: 2    Ruolo: D
 Verifica che le routine di "machine-unlearning" ri-addestrino fisicamente o approssimino la rimozione utilizzando algoritmi di unlearning certificati.
 #11.2.3    Livello: 2    Ruolo: V
 Verificare che la valutazione del modello ombra dimostri che i record dimenticati influenzano meno dell'1% dei risultati dopo il processo di unlearning.
 #11.2.4    Livello: 3    Ruolo: V
 Verificare che gli eventi di cancellazione siano registrati in modo immutabile e siano verificabili per i regolatori.

---

### 11.3 Misure di Salvaguardia sulla Privacy Differenziale

 #11.3.1    Livello: 2    Ruolo: D/V
 Verificare che i cruscotti di rendicontazione della perdita di privacy segnalino quando il valore cumulativo di ε supera le soglie di politica.
 #11.3.2    Livello: 2    Ruolo: V
 Verificare che gli audit di privacy black-box stimino ε̂ entro il 10% del valore dichiarato.
 #11.3.3    Livello: 3    Ruolo: V
 Verificare che le dimostrazioni formali coprano tutti i fine-tune post-addestramento e gli embeddings.

---

### 11.4 Limitazione dello scopo e protezione contro l’espansione incontrollata del campo di applicazione

 #11.4.1    Livello: 1    Ruolo: D
 Verificare che ogni set di dati e checkpoint del modello abbia un tag di scopo leggibile dalla macchina allineato al consenso originale.
 #11.4.2    Livello: 1    Ruolo: D/V
 Verificare che i monitor di runtime rilevino le query incoerenti con lo scopo dichiarato e attivino un rifiuto soft.
 #11.4.3    Livello: 3    Ruolo: D
 Verificare che i gate di policy-as-code blocchino la ridistribuzione dei modelli in nuovi domini senza la revisione DPIA.
 #11.4.4    Livello: 3    Ruolo: V
 Verificare che le prove formali di tracciabilità dimostrino che ogni ciclo di vita dei dati personali rimanga entro l'ambito consentito.

---

### 11.5 Gestione del Consenso e Tracciamento su Base Legale

 #11.5.1    Livello: 1    Ruolo: D/V
 Verificare che una Piattaforma di Gestione del Consenso (CMP) registri lo stato di opt-in, lo scopo e il periodo di conservazione per ogni soggetto dei dati.
 #11.5.2    Livello: 2    Ruolo: D
 Verificare che le API espongano i token di consenso; i modelli devono convalidare l'ambito del token prima dell'inferenza.
 #11.5.3    Livello: 2    Ruolo: D/V
 Verificare che il consenso negato o revocato fermi le pipeline di elaborazione entro 24 ore.

---

### 11.6 Apprendimento Federato con Controlli sulla Privacy

 #11.6.1    Livello: 1    Ruolo: D
 Verificare che gli aggiornamenti del client impieghino l'aggiunta di rumore di privacy differenziale locale prima dell'aggregazione.
 #11.6.2    Livello: 2    Ruolo: D/V
 Verificare che le metriche di addestramento siano private differenziali e non rivelino mai la perdita di un singolo cliente.
 #11.6.3    Livello: 2    Ruolo: V
 Verificare che l'aggregazione resistente all'avvelenamento (ad esempio, Krum/Trimmed-Mean) sia abilitata.
 #11.6.4    Livello: 3    Ruolo: V
 Verificare che le dimostrazioni formali mostrino un budget complessivo di ε con una perdita di utilità inferiore a 5.

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

## C12 Monitoraggio, Registrazione e Rilevamento Anomalie

### Obiettivo di Controllo

Questa sezione fornisce i requisiti per offrire una visibilità in tempo reale e forense su ciò che il modello e gli altri componenti di AI vedono, fanno e restituiscono, affinché le minacce possano essere rilevate, classificate e analizzate.

### C12.1 Registrazione delle richieste e delle risposte

 #12.1.1    Livello: 1    Ruolo: D/V
 Verificare che tutti i prompt degli utenti e le risposte del modello siano registrati con metadati appropriati (ad esempio, timestamp, ID utente, ID sessione, versione del modello).
 #12.1.2    Livello: 1    Ruolo: D/V
 Verificare che i log siano archiviati in repository sicuri, con controllo degli accessi, politiche di conservazione appropriate e procedure di backup.
 #12.1.3    Livello: 1    Ruolo: D/V
 Verificare che i sistemi di archiviazione dei log implementino la crittografia a riposo e in transito per proteggere le informazioni sensibili contenute nei log.
 #12.1.4    Livello: 1    Ruolo: D/V
 Verificare che i dati sensibili nei prompt e nei risultati siano automaticamente oscurati o mascherati prima della registrazione, con regole di oscuramento configurabili per PII, credenziali e informazioni proprietarie.
 #12.1.5    Livello: 2    Ruolo: D/V
 Verificare che le decisioni politiche e le azioni di filtraggio della sicurezza siano registrate con dettagli sufficienti per consentire l'audit e il debug dei sistemi di moderazione dei contenuti.
 #12.1.6    Livello: 2    Ruolo: D/V
 Verificare che l'integrità dei log sia protetta tramite, ad esempio, firme crittografiche o memorizzazione in sola scrittura.

---

### C12.2 Rilevamento e Allerta per Abusi

 #12.2.1    Livello: 1    Ruolo: D/V
 Verificare che il sistema rilevi e avvisi in merito a pattern di jailbreak noti, tentativi di iniezione di prompt e input avversari utilizzando la rilevazione basata su firme.
 #12.2.2    Livello: 1    Ruolo: D/V
 Verificare che il sistema si integri con le piattaforme esistenti di Security Information and Event Management (SIEM) utilizzando formati di log e protocolli standard.
 #12.2.3    Livello: 2    Ruolo: D/V
 Verificare che gli eventi di sicurezza arricchiti includano contesti specifici dell'IA come identificatori di modelli, punteggi di confidenza e decisioni del filtro di sicurezza.
 #12.2.4    Livello: 2    Ruolo: D/V
 Verificare che il rilevamento delle anomalie comportamentali identifichi modelli di conversazione insoliti, tentativi di ripetizione eccessivi o comportamenti di sondaggio sistematici.
 #12.2.5    Livello: 2    Ruolo: D/V
 Verificare che i meccanismi di allerta in tempo reale notifichino i team di sicurezza quando vengono rilevate potenziali violazioni di policy o tentativi di attacco.
 #12.2.6    Livello: 2    Ruolo: D/V
 Verificare che siano incluse regole personalizzate per rilevare modelli di minacce specifici per l'IA, comprese le tentativi coordinati di jailbreak, le campagne di iniezione di prompt e gli attacchi di estrazione del modello.
 #12.2.7    Livello: 3    Ruolo: D/V
 Verificare che i flussi di lavoro automatizzati di risposta agli incidenti possano isolare i modelli compromessi, bloccare gli utenti malevoli e segnalare gli eventi di sicurezza critici.

---

### C12.3 Rilevamento della deriva del modello

 #12.3.1    Livello: 1    Ruolo: D/V
 Verificare che il sistema monitori metriche di prestazione di base come accuratezza, punteggi di fiducia, latenza e tassi di errore attraverso le versioni del modello e i periodi di tempo.
 #12.3.2    Livello: 2    Ruolo: D/V
 Verificare che l'allerta automatica venga attivata quando le metriche di prestazione superano le soglie di degrado predefinite o si discostano significativamente dai valori basali.
 #12.3.3    Livello: 2    Ruolo: D/V
 Verificare che i monitor di rilevamento delle allucinazioni identifichino e segnalino i casi in cui le risposte del modello contengano informazioni fattualmente errate, incoerenti o inventate.

---

### C12.4 Telemetria delle Prestazioni e del Comportamento

 #12.4.1    Livello: 1    Ruolo: D/V
 Verificare che le metriche operative, inclusi la latenza delle richieste, il consumo di token, l’utilizzo della memoria e la larghezza di banda, siano continuamente raccolte e monitorate.
 #12.4.2    Livello: 1    Ruolo: D/V
 Verificare che i tassi di successo e di fallimento siano monitorati con la categorizzazione dei tipi di errore e delle loro cause principali.
 #12.4.3    Livello: 2    Ruolo: D/V
 Verificare che il monitoraggio dell'utilizzo delle risorse includa l'uso della GPU/CPU, il consumo di memoria e i requisiti di archiviazione con allerta in caso di superamento delle soglie.

---

### C12.5 Pianificazione ed esecuzione della risposta agli incidenti di IA

 #12.5.1    Livello: 1    Ruolo: D/V
 Verificare che i piani di risposta agli incidenti affrontino specificamente eventi di sicurezza legati all'IA, inclusi il compromesso del modello, l'avvelenamento dei dati e gli attacchi adversariali.
 #12.5.2    Livello: 2    Ruolo: D/V
 Verificare che i team di risposta agli incidenti abbiano accesso a strumenti forensi specifici per l'IA e competenze per indagare il comportamento dei modelli e i vettori di attacco.
 #12.5.3    Livello: 3    Ruolo: D/V
 Verificare che l'analisi post-incidente includa considerazioni sul retraining del modello, aggiornamenti dei filtri di sicurezza e l'integrazione delle lezioni apprese nei controlli di sicurezza.

---

### C12.5 Rilevamento del Deterioramento delle Prestazioni dell'IA

Monitorare e rilevare il degrado delle prestazioni e della qualità del modello di intelligenza artificiale nel tempo.

 #12.5.1    Livello: 1    Ruolo: D/V
 Verificare che l'accuratezza del modello, la precisione, il richiamo e i punteggi F1 siano continuamente monitorati e confrontati con le soglie di riferimento.
 #12.5.2    Livello: 1    Ruolo: D/V
 Verificare che il rilevamento del drift dei dati monitori le variazioni nella distribuzione degli input che potrebbero influire sulle prestazioni del modello.
 #12.5.3    Livello: 2    Ruolo: D/V
 Verificare che il rilevamento del concetto di drift identifichi i cambiamenti nella relazione tra input e output previsti.
 #12.5.4    Livello: 2    Ruolo: D/V
 Verificare che il degrado delle prestazioni attivi avvisi automatici e avvii workflow di riqualificazione o sostituzione del modello.
 #12.5.5    Livello: 3    Ruolo: V
 Verificare che l’analisi della causa principale della degradazione correli i cali di prestazioni con cambiamenti nei dati, problemi di infrastruttura o fattori esterni.

---

### C12.6 Visualizzazione DAG e Sicurezza del Flusso di Lavoro

Proteggere i sistemi di visualizzazione del flusso di lavoro da fughe di informazioni e attacchi di manipolazione.

 #12.6.1    Livello: 1    Ruolo: D/V
 Verificare che i dati di visualizzazione del DAG siano sanificati per rimuovere informazioni sensibili prima della memorizzazione o della trasmissione.
 #12.6.2    Livello: 1    Ruolo: D/V
 Verificare che i controlli di accesso alla visualizzazione del workflow garantiscano che solo gli utenti autorizzati possano vedere i percorsi decisionali dell'agente e le tracce del ragionamento.
 #12.6.3    Livello: 2    Ruolo: D/V
 Verificare che l'integrità dei dati del DAG sia protetta tramite firme crittografiche e meccanismi di memorizzazione a prova di manomissione.
 #12.6.4    Livello: 2    Ruolo: D/V
 Verificare che i sistemi di visualizzazione dei workflow implementino la convalida dell'input per prevenire attacchi di injection tramite dati manipolati di nodi o archi.
 #12.6.5    Livello: 3    Ruolo: D/V
 Verificare che gli aggiornamenti in tempo reale del DAG siano limitati in frequenza e convalidati per prevenire attacchi di denial-of-service sui sistemi di visualizzazione.

---

### C12.7 Monitoraggio Proattivo del Comportamento di Sicurezza

Rilevamento e prevenzione delle minacce alla sicurezza attraverso l'analisi proattiva del comportamento degli agenti.

 #12.7.1    Livello: 1    Ruolo: D/V
 Verificare che i comportamenti proattivi dell'agente siano convalidati per la sicurezza prima dell'esecuzione con l'integrazione della valutazione del rischio.
 #12.7.2    Livello: 2    Ruolo: D/V
 Verificare che le iniziative autonome includano la valutazione del contesto di sicurezza e la valutazione del panorama delle minacce.
 #12.7.3    Livello: 2    Ruolo: D/V
 Verificare che i modelli di comportamento proattivo siano analizzati per potenziali implicazioni di sicurezza e conseguenze non intenzionali.
 #12.7.4    Livello: 3    Ruolo: D/V
 Verificare che le azioni proattive critiche per la sicurezza richiedano catene di approvazione esplicite con registrazioni di audit.
 #12.7.5    Livello: 3    Ruolo: D/V
 Verificare che il rilevamento di anomalie comportamentali identifichi deviazioni nei modelli degli agenti proattivi che potrebbero indicare un compromesso.

---

### Riferimenti

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13 Supervisione Umana, Responsabilità e Governance

### Obiettivo di Controllo

Questo capitolo fornisce requisiti per mantenere la supervisione umana e catene di responsabilità chiare nei sistemi di intelligenza artificiale, garantendo spiegabilità, trasparenza e gestione etica lungo l'intero ciclo di vita dell'IA.

---

### C13.1 Meccanismi di Kill-Switch e Override

Fornire percorsi di spegnimento o rollback quando viene osservato un comportamento non sicuro del sistema di intelligenza artificiale.

 #13.1.1    Livello: 1    Ruolo: D/V
 Verificare che esista un meccanismo di interruzione manuale per arrestare immediatamente l'inferenza e le uscite del modello AI.
 #13.1.2    Livello: 1    Ruolo: D
 Verificare che i controlli di override siano accessibili solo al personale autorizzato.
 #13.1.3    Livello: 3    Ruolo: D/V
 Verificare che le procedure di rollback possano tornare alle versioni precedenti del modello o alle operazioni in modalità sicura.
 #13.1.4    Livello: 3    Ruolo: V
 Verificare che i meccanismi di override vengano testati regolarmente.

---

### C13.2 Punti di Controllo Decisionale con Intervento Umano

Richiedere approvazioni umane quando le poste in gioco superano soglie di rischio predefinite.

 #13.2.1    Livello: 1    Ruolo: D/V
 Verificare che le decisioni IA ad alto rischio richiedano un'approvazione esplicita umana prima dell'esecuzione.
 #13.2.2    Livello: 1    Ruolo: D
 Verificare che le soglie di rischio siano chiaramente definite e attivino automaticamente i flussi di lavoro per la revisione umana.
 #13.2.3    Livello: 2    Ruolo: D
 Verificare che le decisioni sensibili al fattore tempo prevedano procedure di emergenza quando non è possibile ottenere l'approvazione umana entro i tempi richiesti.
 #13.2.4    Livello: 3    Ruolo: D/V
 Verificare che le procedure di escalation definiscano chiaramente i livelli di autorità per i diversi tipi di decisioni o categorie di rischio, se applicabile.

---

### C13.3 Catena di Responsabilità e Auditabilità

Registra le azioni dell'operatore e le decisioni del modello.

 #13.3.1    Livello: 1    Ruolo: D/V
 Verificare che tutte le decisioni del sistema AI e gli interventi umani siano registrati con timestamp, identità degli utenti e motivazione della decisione.
 #13.3.2    Livello: 2    Ruolo: D
 Verificare che i log di audit non possano essere manomessi e includano meccanismi di verifica dell'integrità.

---

### C13.4 Tecniche di Explainable AI

Importanza delle caratteristiche superficiali, controfattuali e spiegazioni locali.

 #13.4.1    Livello: 1    Ruolo: D/V
 Verificare che i sistemi di intelligenza artificiale forniscano spiegazioni di base per le loro decisioni in un formato comprensibile dall'uomo.
 #13.4.2    Livello: 2    Ruolo: V
 Verificare che la qualità della spiegazione sia convalidata tramite studi e metriche di valutazione umana.
 #13.4.3    Livello: 3    Ruolo: D/V
 Verificare che i punteggi di importanza delle caratteristiche o i metodi di attribuzione (SHAP, LIME, ecc.) siano disponibili per decisioni critiche.
 #13.4.4    Livello: 3    Ruolo: V
 Verificare che le spiegazioni controfattuali mostrino come gli input potrebbero essere modificati per cambiare i risultati, se applicabile al caso d'uso e al dominio.

---

### C13.5 Schede Modello e Dichiarazioni d'Uso

Mantenere le schede modello per l'uso previsto, le metriche di prestazione e le considerazioni etiche.

 #13.5.1    Livello: 1    Ruolo: D
 Verificare che le schede modello documentino i casi d'uso previsti, le limitazioni e le modalità di malfunzionamento note.
 #13.5.2    Livello: 1    Ruolo: D/V
 Verificare che le metriche di prestazione per i diversi casi d'uso applicabili siano comunicate.
 #13.5.3    Livello: 2    Ruolo: D
 Verificare che le considerazioni etiche, le valutazioni dei bias, le analisi di equità, le caratteristiche dei dati di addestramento e le limitazioni note dei dati di addestramento siano documentate e aggiornate regolarmente.
 #13.5.4    Livello: 2    Ruolo: D/V
 Verificare che le schede dei modelli siano sottoposte a controllo di versione e mantenute durante l'intero ciclo di vita del modello con il tracciamento delle modifiche.

---

### C13.6 Quantificazione dell'Incertezza

Propagare i punteggi di confidenza o le misure di entropia nelle risposte.

 #13.6.1    Livello: 1    Ruolo: D
 Verificare che i sistemi di intelligenza artificiale forniscano punteggi di confidenza o misure di incertezza con i loro output.
 #13.6.2    Livello: 2    Ruolo: D/V
 Verificare che le soglie di incertezza attivino una revisione umana aggiuntiva o percorsi decisionali alternativi.
 #13.6.3    Livello: 2    Ruolo: V
 Verificare che i metodi di quantificazione dell'incertezza siano calibrati e validati rispetto ai dati di verità a terra.
 #13.6.4    Livello: 3    Ruolo: D/V
 Verifica che la propagazione dell'incertezza sia mantenuta attraverso flussi di lavoro AI a più fasi.

---

### C13.7 Rapporti di trasparenza rivolti agli utenti

Fornire divulgazioni periodiche su incidenti, deriva e utilizzo dei dati.

 #13.7.1    Livello: 1    Ruolo: D/V
 Verificare che le politiche di utilizzo dei dati e le pratiche di gestione del consenso degli utenti siano comunicate chiaramente alle parti interessate.
 #13.7.2    Livello: 2    Ruolo: D/V
 Verificare che le valutazioni dell'impatto dell'IA siano condotte e che i risultati siano inclusi nella reportistica.
 #13.7.3    Livello: 2    Ruolo: D/V
 Verificare che i rapporti di trasparenza pubblicati regolarmente divulghino incidenti di IA e metriche operative in dettaglio ragionevole.

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

Questo glossario completo fornisce definizioni dei principali termini di AI, ML e sicurezza utilizzati in tutto l'AISVS per garantire chiarezza e comprensione comune.

Esempio avversario: un input appositamente creato per far commettere un errore a un modello di IA, spesso aggiungendo lievi perturbazioni impercettibili agli esseri umani.
​
Robustezza avversaria – La robustezza avversaria nell'IA si riferisce alla capacità di un modello di mantenere le proprie prestazioni e di resistere a essere ingannato o manipolato da input intenzionalmente progettati e malevoli, creati per causare errori.
​
Agente – Gli agenti AI sono sistemi software che utilizzano l'intelligenza artificiale per perseguire obiettivi e completare compiti per conto degli utenti. Mostrano capacità di ragionamento, pianificazione e memoria e possiedono un livello di autonomia per prendere decisioni, apprendere e adattarsi.
​
Agentic AI: sistemi di intelligenza artificiale che possono operare con un certo grado di autonomia per raggiungere obiettivi, spesso prendendo decisioni e compiendo azioni senza intervento umano diretto.
​
Controllo degli Accessi Basato su Attributi (ABAC): Un paradigma di controllo degli accessi in cui le decisioni di autorizzazione si basano sugli attributi dell'utente, della risorsa, dell'azione e dell'ambiente, valutati al momento della richiesta.
​
Attacco Backdoor: Un tipo di attacco di avvelenamento dei dati in cui il modello viene addestrato a rispondere in un modo specifico a determinati trigger mentre si comporta normalmente altrimenti.
​
Bias: Errori sistematici nei risultati dei modelli di IA che possono portare a risultati ingiusti o discriminatori per determinati gruppi o in specifici contesti.
​
Sfruttamento dei bias: una tecnica di attacco che sfrutta i bias noti nei modelli di intelligenza artificiale per manipolare risultati o output.
​
Cedar: il linguaggio di policy e motore di Amazon per permessi granulati utilizzato nell'implementazione di ABAC per sistemi di intelligenza artificiale.
​
Catena di pensiero: una tecnica per migliorare il ragionamento nei modelli linguistici generando passaggi intermedi di ragionamento prima di produrre una risposta finale.
​
Interruttori automatici: meccanismi che interrompono automaticamente le operazioni del sistema di intelligenza artificiale quando vengono superate soglie di rischio specifiche.
​
Perdita di dati: esposizione non intenzionale di informazioni sensibili tramite output o comportamento del modello AI.
​
Avvelenamento dei dati: la corruzione deliberata dei dati di addestramento per compromettere l'integrità del modello, spesso per installare backdoor o degradare le prestazioni.
​
Privacy Differenziale – La privacy differenziale è un quadro matematicamente rigoroso per la divulgazione di informazioni statistiche su insiemi di dati proteggendo la privacy dei singoli soggetti coinvolti. Consente a un detentore di dati di condividere modelli aggregati del gruppo limitando le informazioni che possono essere divulgate su individui specifici.
​
Incorporamenti: rappresentazioni vettoriali dense di dati (testo, immagini, ecc.) che catturano il significato semantico in uno spazio ad alta dimensione.
​
Spiegabilità – La spiegabilità nell'IA è la capacità di un sistema di intelligenza artificiale di fornire motivazioni comprensibili dall'uomo per le sue decisioni e previsioni, offrendo approfondimenti sul suo funzionamento interno.
​
Intelligenza Artificiale Spiegabile (XAI): sistemi di IA progettati per fornire spiegazioni comprensibili all'essere umano riguardo alle loro decisioni e comportamenti attraverso varie tecniche e framework.
​
Apprendimento Federato: un approccio di machine learning in cui i modelli vengono addestrati su più dispositivi decentralizzati che possiedono campioni di dati locali, senza scambiare i dati stessi.
​
Guardrails: vincoli implementati per impedire ai sistemi di intelligenza artificiale di produrre output dannosi, faziosi o altrimenti indesiderati.
​
Allucinazione – Un’allucinazione dell’IA si riferisce a un fenomeno in cui un modello di intelligenza artificiale genera informazioni errate o fuorvianti che non sono basate sui suoi dati di addestramento o sulla realtà fattuale.
​
Human-in-the-Loop (HITL): Sistemi progettati per richiedere supervisione, verifica o intervento umano nei punti critici decisionali.
​
Infrastructure as Code (IaC): Gestione e provisioning dell'infrastruttura tramite codice invece di processi manuali, consentendo la scansione della sicurezza e distribuzioni coerenti.
​
Jailbreak: Tecniche utilizzate per eludere le barriere di sicurezza nei sistemi di intelligenza artificiale, in particolare nei modelli linguistici di grandi dimensioni, per produrre contenuti proibiti.
​
Privilegio minimo: il principio di sicurezza che prevede di concedere solo i diritti di accesso minimi necessari agli utenti e ai processi.
​
LIME (Local Interpretable Model-agnostic Explanations): una tecnica per spiegare le predizioni di qualsiasi classificatore di apprendimento automatico approssimandolo localmente con un modello interpretabile.
​
Attacco di Inferenza sull'Appartenenza: un attacco che mira a determinare se un punto dati specifico è stato utilizzato per addestrare un modello di machine learning.
​
MITRE ATLAS: Panorama delle minacce avversarie per i sistemi di intelligenza artificiale; una base di conoscenza delle tattiche e tecniche avversarie contro i sistemi di IA.
​
Scheda del Modello – Una scheda del modello è un documento che fornisce informazioni standardizzate sulle prestazioni di un modello di intelligenza artificiale, le sue limitazioni, gli usi previsti e le considerazioni etiche per promuovere la trasparenza e uno sviluppo responsabile dell'IA.
​
Estrazione del Modello: Un attacco in cui un avversario interroga ripetutamente un modello target per creare una copia funzionalmente simile senza autorizzazione.
​
Inversione del modello: un attacco che tenta di ricostruire i dati di addestramento analizzando gli output del modello.
​
Gestione del Ciclo di Vita del Modello – La Gestione del Ciclo di Vita del Modello AI è il processo di supervisione di tutte le fasi dell'esistenza di un modello AI, inclusi progettazione, sviluppo, implementazione, monitoraggio, manutenzione e eventuale ritiro, per garantire che rimanga efficace e allineato agli obiettivi.
​
Avvelenamento del Modello: Introduzione di vulnerabilità o backdoor direttamente in un modello durante il processo di addestramento.
​
Furto/Rubare il Modello: Estrarre una copia o un'approssimazione di un modello proprietario tramite richieste ripetute.
​
Sistema multi-agente: un sistema composto da più agenti IA interagenti, ciascuno con potenzialmente capacità e obiettivi diversi.
​
OPA (Open Policy Agent): Un motore di policy open-source che consente l'applicazione unificata delle policy attraverso l'intero stack.
​
Apprendimento Automatico che Preserva la Privacy (PPML): Tecniche e metodi per addestrare e distribuire modelli di ML proteggendo la privacy dei dati di addestramento.
​
Iniezione di prompt: un attacco in cui istruzioni dannose sono incorporate negli input per sovrascrivere il comportamento previsto di un modello.
​
RAG (Generazione Integrata con Recupero): Una tecnica che migliora i modelli di linguaggio di grandi dimensioni recuperando informazioni rilevanti da fonti di conoscenza esterne prima di generare una risposta.
​
Red-Teaming: La pratica di testare attivamente i sistemi di IA simulando attacchi avversari per identificare le vulnerabilità.
​
SBOM (Software Bill of Materials): Un registro formale contenente i dettagli e le relazioni della catena di fornitura di vari componenti utilizzati nella creazione di software o modelli di Intelligenza Artificiale.
​
SHAP (SHapley Additive exPlanations): Un approccio teorico dei giochi per spiegare l'output di qualsiasi modello di machine learning calcolando il contributo di ciascuna caratteristica alla previsione.
​
Attacco alla catena di approvvigionamento: compromettere un sistema prendendo di mira elementi meno sicuri della sua catena di approvvigionamento, come librerie di terze parti, set di dati o modelli pre-addestrati.
​
Apprendimento per trasferimento: Una tecnica in cui un modello sviluppato per un compito viene riutilizzato come punto di partenza per un modello su un secondo compito.
​
Database vettoriale: un database specializzato progettato per memorizzare vettori ad alta dimensionalità (embedding) ed eseguire ricerche di similarità efficienti.
​
Scansione delle vulnerabilità: Strumenti automatizzati che identificano vulnerabilità di sicurezza note nei componenti software, inclusi framework di IA e dipendenze.
​
Watermarking: Tecniche per inserire marker impercettibili nei contenuti generati dall'IA per tracciare la loro origine o rilevare la generazione da parte dell'IA.
​
Vulnerabilità Zero-Day: Una vulnerabilità precedentemente sconosciuta che gli aggressori possono sfruttare prima che gli sviluppatori creino e distribuiscano una patch.

## Appendice B: Riferimenti

### TODO

## Appendice C: Governance e Documentazione della Sicurezza AI

### Obiettivo

Questo appendice fornisce requisiti fondamentali per l'istituzione di strutture organizzative, politiche e processi per governare la sicurezza dell'IA durante l'intero ciclo di vita del sistema.

---

### Adozione del quadro di gestione del rischio AI AC.1

Fornire un quadro formale per identificare, valutare e mitigare i rischi specifici dell'IA durante l'intero ciclo di vita del sistema.

 #AC.1.1    Livello: 1    Ruolo: D/V
 Verificare che una metodologia di valutazione del rischio specifica per l'IA sia documentata e implementata.
 #AC.1.2    Livello: 2    Ruolo: D
 Verificare che le valutazioni del rischio vengano effettuate in momenti chiave del ciclo di vita dell'IA e prima di cambiamenti significativi.
 #AC.1.3    Livello: 3    Ruolo: D/V
 Verificare che il framework di gestione del rischio sia allineato agli standard stabiliti (ad esempio, NIST AI RMF).

---

### AC.2 Politiche e Procedure di Sicurezza per l'IA

Definire e applicare standard organizzativi per lo sviluppo, il deployment e il funzionamento sicuri dell'IA.

 #AC.2.1    Livello: 1    Ruolo: D/V
 Verificare che esistano politiche di sicurezza AI documentate.
 #AC.2.2    Livello: 2    Ruolo: D
 Verificare che le politiche vengano riviste e aggiornate almeno annualmente e dopo cambiamenti significativi del panorama delle minacce.
 #AC.2.3    Livello: 3    Ruolo: D/V
 Verificare che le politiche affrontino tutte le categorie AISVS e i requisiti normativi applicabili.

---

### AC.3 Ruoli e Responsabilità per la Sicurezza dell'IA

Stabilire una chiara responsabilità per la sicurezza dell'AI in tutta l'organizzazione.

 #AC.3.1    Livello: 1    Ruolo: D/V
 Verificare che i ruoli e le responsabilità relative alla sicurezza dell'IA siano documentati.
 #AC.3.2    Livello: 2    Ruolo: D
 Verificare che le persone responsabili possiedano adeguate competenze in materia di sicurezza.
 #AC.3.3    Livello: 3    Ruolo: D/V
 Verificare che sia stato istituito un comitato etico per l'IA o un organismo di governance per i sistemi di IA ad alto rischio.

---

### AC.4 Applicazione delle Linee Guida per l’Intelligenza Artificiale Etica

Garantire che i sistemi di intelligenza artificiale operino secondo principi etici stabiliti.

 #AC.4.1    Livello: 1    Ruolo: D/V
 Verificare che esistano linee guida etiche per lo sviluppo e l'implementazione dell'IA.
 #AC.4.2    Livello: 2    Ruolo: D
 Verificare che siano in atto meccanismi per rilevare e segnalare le violazioni etiche.
 #AC.4.3    Livello: 3    Ruolo: D/V
 Verificare che vengano effettuate revisioni etiche regolari dei sistemi di intelligenza artificiale implementati.

---

### AC.5 Monitoraggio della Conformità Regolamentare dell'IA

Mantenere consapevolezza e conformità alle normative sull'IA in evoluzione.

 #AC.5.1    Livello: 1    Ruolo: D/V
 Verificare che esistano processi per identificare le normative AI applicabili.
 #AC.5.2    Livello: 2    Ruolo: D
 Verificare che la conformità a tutti i requisiti normativi venga valutata.
 #AC.5.3    Livello: 3    Ruolo: D/V
 Verificare che le modifiche normative attivino revisioni e aggiornamenti tempestivi ai sistemi di intelligenza artificiale.

### AC.6 Governance, documentazione e processo dei dati di addestramento

 #1.1.2    Livello: 1    Ruolo: D/V
 Verificare che siano consentiti solo i dataset controllati per qualità, rappresentatività, provenienza etica e conformità alle licenze, riducendo i rischi di avvelenamento, bias incorporato e violazione della proprietà intellettuale.
 #1.1.5    Livello: 2    Ruolo: D/V
 Verificare che la qualità dell'etichettatura/annotazione sia garantita tramite controlli incrociati da parte dei revisori o consenso.
 #1.1.6    Livello: 2    Ruolo: D/V
 Verificare che siano mantenute "schede dati" o "schede delle specifiche per dataset" per i dataset di addestramento significativi, dettagliando caratteristiche, motivazioni, composizione, processi di raccolta, preprocessing e usi consigliati/sconsigliati.
 #1.3.2    Livello: 2    Ruolo: D/V
 Verificare che i bias identificati siano mitigati tramite strategie documentate come il riequilibrio, l’aumento mirato dei dati, gli aggiustamenti algoritmici (ad esempio, tecniche di pre-elaborazione, elaborazione in-processo, post-elaborazione) o la ripesatura, e che l’impatto della mitigazione sia valutato sia sulla equità sia sulle prestazioni complessive del modello.
 #1.3.3    Livello: 2    Ruolo: D/V
 Verificare che le metriche di equità post-addestramento siano valutate e documentate.
 #1.3.4    Livello: 3    Ruolo: D/V
 Verificare che una politica di gestione del bias del ciclo di vita assegni proprietari e cadenza di revisione.
 #1.4.1    Livello: 2    Ruolo: D/V
 Verificare che la qualità dell'etichettatura/annotazione sia garantita tramite linee guida chiare, controlli incrociati dei revisori, meccanismi di consenso (ad esempio, monitoraggio dell'accordo tra annotatori) e processi definiti per la risoluzione delle discrepanze.
 #1.4.4    Livello: 3    Ruolo: D/V
 Verificare che le etichette critiche per la sicurezza, la protezione o l'equità (ad esempio, l'identificazione di contenuti tossici, risultati medici critici) ricevano una revisione doppia indipendente obbligatoria o una verifica equivalente e robusta.
 #1.4.6    Livello: 2    Ruolo: D/V
 Verificare che le guide di etichettatura e le istruzioni siano complete, controllate nelle versioni e revisionate da colleghi.
 #1.4.6    Livello: 2    Ruolo: D/V
 Verificare che gli schemi dei dati per le etichette siano chiaramente definiti e controllati nelle versioni.
 #1.3.1    Livello: 1    Ruolo: D/V
 Verificare che i dataset siano sottoposti a profilazione per squilibri rappresentazionali e potenziali bias riguardanti attributi protetti legalmente (ad esempio, razza, genere, età) e altre caratteristiche eticamente sensibili rilevanti per il dominio di applicazione del modello (ad esempio, status socio-economico, localizzazione).
 #1.5.3    Livello: 2    Ruolo: V
 Verificare che i controlli manuali a campione effettuati da esperti del dominio coprano un campione statisticamente significativo (ad esempio, ≥1% o 1.000 campioni, a seconda di quale sia maggiore, o come determinato dalla valutazione del rischio) per identificare problemi di qualità sottili non rilevati dall'automazione.
 #1.8.4    Livello: 2    Ruolo: D/V
 Verificare che i flussi di lavoro di etichettatura esternalizzati o basati sul crowdsourcing includano salvaguardie tecniche/procedurali per garantire la riservatezza dei dati, l'integrità, la qualità delle etichette e prevenire la perdita di dati.
 #1.5.4    Livello: 2    Ruolo: D/V
 Verificare che le fasi di rimedio siano aggiunte ai registri di provenienza.
 #1.6.2    Livello: 2    Ruolo: D/V
 Verificare che i campioni segnalati attivino la revisione manuale prima dell'addestramento.
 #1.6.3    Livello: 2    Ruolo: V
 Verificare che i risultati alimentino il dossier di sicurezza del modello e informino l'intelligence sulle minacce in corso.
 #1.6.4    Livello: 3    Ruolo: D/V
 Verificare che la logica di rilevamento venga aggiornata con nuove informazioni sulle minacce.
 #1.6.5    Livello: 3    Ruolo: D/V
 Verificare che le pipeline di apprendimento online monitorino la deriva della distribuzione.
 #1.7.1    Livello: 1    Ruolo: D/V
 Verificare che i flussi di lavoro per la cancellazione dei dati di addestramento eliminino i dati primari e derivati e valutare l'impatto sul modello, assicurandosi che l'impatto sui modelli interessati venga valutato e, se necessario, affrontato (ad esempio, tramite riaddestramento o ricalibrazione).
 #1.7.2    Livello: 2    Ruolo: D
 Verificare che siano presenti meccanismi per monitorare e rispettare l'ambito e lo stato del consenso degli utenti (e dei reindirizzi) per i dati utilizzati nell'addestramento, e che il consenso venga convalidato prima che i dati vengano incorporati in nuovi processi di addestramento o in aggiornamenti significativi del modello.
 #1.7.3    Livello: 2    Ruolo: V
 Verificare che i flussi di lavoro siano testati annualmente e registrati.
 #1.8.1    Livello: 2    Ruolo: D/V
 Verificare che i fornitori di dati terzi, inclusi i provider di modelli pre-addestrati e dataset esterni, siano sottoposti a procedure di due diligence in materia di sicurezza, privacy, approvvigionamento etico e qualità dei dati prima che i loro dati o modelli vengano integrati.
 #1.8.2    Livello: 1    Ruolo: D
 Verificare che i trasferimenti esterni utilizzino TLS/autenticazione e controlli di integrità.
 #1.8.3    Livello: 2    Ruolo: D/V
 Verificare che le fonti di dati ad alto rischio (ad esempio, dataset open-source con provenienza sconosciuta, fornitori non verificati) ricevano una scrutinio approfondito, come analisi in sandbox, controlli estesi di qualità/bias e rilevazione mirata di avvelenamento, prima dell'uso in applicazioni sensibili.
 #1.8.4    Livello: 3    Ruolo: D/V
 Verificare che i modelli pre-addestrati ottenuti da terze parti siano valutati per bias incorporati, potenziali backdoor, integrità della loro architettura e provenienza dei dati originali di addestramento prima di eseguire il fine-tuning o la messa in produzione.
 #1.5.3    Livello: 2    Ruolo: D/V
 Verificare che, se viene utilizzato l'addestramento adversariale, la generazione, gestione e versionamento dei dataset adversariali siano documentati e controllati.
 #1.5.3    Livello: 3    Ruolo: D/V
 Verificare che l'impatto dell'addestramento per la robustezza avversaria sulle prestazioni del modello (sia contro input puliti che avversari) e sulle metriche di equità sia valutato, documentato e monitorato.
 #1.5.4    Livello: 3    Ruolo: D/V
 Verificare che le strategie per l'addestramento avversario e la robustezza siano periodicamente riviste e aggiornate per contrastare le tecniche di attacco avversario in evoluzione.
 #1.4.2    Livello: 2    Ruolo: D/V
 Verifica che i dataset non riusciti siano messi in quarantena con tracciamenti di audit.
 #1.4.3    Livello: 2    Ruolo: D/V
 Verificare che i quality gates blocchino i dataset di qualità inferiore a meno che non siano approvate delle eccezioni.
 #1.11.2    Livello: 2    Ruolo: D/V
 Verificare che il processo di generazione, i parametri e l'uso previsto dei dati sintetici siano documentati.
 #1.11.3    Livello: 2    Ruolo: D/V
 Verificare che i dati sintetici siano sottoposti a valutazione del rischio per bias, perdita di privacy e problemi di rappresentazione prima dell'uso nell'addestramento.
 #1.12.3    Livello: 2    Ruolo: D/V
 Verificare che gli alert siano generati per eventi di accesso sospetti e che vengano indagati tempestivamente.
 #1.13.1    Livello: 1    Ruolo: D/V
 Verificare che siano definiti periodi di conservazione espliciti per tutti i set di dati di addestramento.
 #1.13.2    Livello: 2    Ruolo: D/V
 Verificare che i dataset vengano automaticamente scaduti, eliminati o sottoposti a revisione per l'eliminazione al termine del loro ciclo di vita.
 #1.13.3    Livello: 2    Ruolo: D/V
 Verificare che le azioni di conservazione e cancellazione siano registrate e verificabili.
 #1.14.1    Livello: 2    Ruolo: D/V
 Verificare che i requisiti di residenza dei dati e di trasferimento transfrontaliero siano identificati e applicati per tutti i set di dati.
 #1.14.2    Livello: 2    Ruolo: D/V
 Verificare che le normative specifiche di settore (ad esempio, sanità, finanza) siano identificate e gestite nella gestione dei dati.
 #1.14.3    Livello: 2    Ruolo: D/V
 Verificare che la conformità alle leggi sulla privacy pertinenti (ad esempio, GDPR, CCPA) sia documentata e rivista regolarmente.
 #1.16.1    Livello: 2    Ruolo: D/V
 Verificare che esistano meccanismi per rispondere alle richieste del soggetto dei dati per accesso, rettifica, limitazione o opposizione.
 #1.16.2    Livello: 2    Ruolo: D/V
 Verificare che le richieste siano registrate, monitorate e soddisfatte entro i termini previsti dalla legge.
 #1.16.3    Livello: 2    Ruolo: D/V
 Verificare che i processi relativi ai diritti degli interessati siano testati e revisionati regolarmente per garantirne l'efficacia.
 #1.17.1    Livello: 2    Ruolo: D/V
 Verificare che venga eseguita un'analisi d'impatto prima di aggiornare o sostituire una versione del dataset, coprendo le prestazioni del modello, l'equità e la conformità.
 #1.17.2    Livello: 2    Ruolo: D/V
 Verificare che i risultati dell'analisi dell'impatto siano documentati e riesaminati dai soggetti interessati pertinenti.
 #1.17.3    Livello: 2    Ruolo: D/V
 Verificare che esistano piani di rollback nel caso in cui le nuove versioni introducano rischi inaccettabili o regressioni.
 #1.18.1    Livello: 2    Ruolo: D/V
 Verificare che tutto il personale coinvolto nell'annotazione dei dati sia stato sottoposto a controlli di background e sia formato in materia di sicurezza e privacy dei dati.
 #1.18.2    Livello: 2    Ruolo: D/V
 Verificare che tutto il personale di annotazione firmi accordi di riservatezza e non divulgazione.
 #1.18.3    Livello: 2    Ruolo: D/V
 Verificare che le piattaforme di annotazione applicano controlli di accesso e monitorano le minacce interne.

#### Riferimenti

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Appendice D: Governance e Verifica della Scrittura Sicura Assistita da AI

### Obiettivo

Questo capitolo definisce i controlli organizzativi di base per l'uso sicuro ed efficace degli strumenti di codifica assistita dall'IA durante lo sviluppo software, garantendo sicurezza e tracciabilità lungo l'intero ciclo di vita del software (SDLC).

---

### AD.1 Flusso di lavoro per la programmazione sicura assistita da AI

Integrare gli strumenti di intelligenza artificiale nel ciclo di vita dello sviluppo software sicuro (SSDLC) dell'organizzazione senza indebolire i controlli di sicurezza esistenti.

 #AD.1.1    Livello: 1    Ruolo: D/V
 Verifica che un flusso di lavoro documentato descriva quando e come gli strumenti di intelligenza artificiale possono generare, rifattorizzare o revisionare il codice.
 #AD.1.2    Livello: 2    Ruolo: D
 Verificare che il flusso di lavoro corrisponda a ciascuna fase del SSDLC (progettazione, implementazione, revisione del codice, test, distribuzione).
 #AD.1.3    Livello: 3    Ruolo: D/V
 Verificare che le metriche (ad esempio, densità delle vulnerabilità, tempo medio di rilevamento) siano raccolte sul codice prodotto dall'IA e confrontate con i parametri di riferimento esclusivamente umani.

---

### AD.2 Qualificazione dello Strumento AI e Modellazione delle Minacce

Assicurarsi che gli strumenti di codifica AI vengano valutati per le capacità di sicurezza, il rischio e l'impatto sulla catena di approvvigionamento prima dell'adozione.

 #AD.2.1    Livello: 1    Ruolo: D/V
 Verificare che un modello di minaccia per ogni strumento di IA identifichi abusi, inversione del modello, perdita di dati e rischi nella catena di dipendenza.
 #AD.2.2    Livello: 2    Ruolo: D
 Verificare che le valutazioni degli strumenti includano l’analisi statica/dinamica di eventuali componenti locali e la valutazione degli endpoint SaaS (TLS, autenticazione/autorizzazione, registrazione).
 #AD.2.3    Livello: 3    Ruolo: D/V
 Verificare che le valutazioni seguano un quadro riconosciuto e siano ripetute dopo cambiamenti significativi di versione.

---

### AD.3 Gestione sicura di prompt e contesto

Impedire la fuoriuscita di segreti, codice proprietario e dati personali durante la costruzione di prompt o contesti per modelli di IA.

 #AD.3.1    Livello: 1    Ruolo: D/V
 Verificare che le linee guida scritte vietino l'invio di segreti, credenziali o dati riservati nelle richieste.
 #AD.3.2    Livello: 2    Ruolo: D
 Verificare che i controlli tecnici (redazione lato client, filtri di contesto approvati) rimuovano automaticamente gli elementi sensibili.
 #AD.3.3    Livello: 3    Ruolo: D/V
 Verificare che i prompt e le risposte siano tokenizzati, crittografati durante la trasmissione e a riposo, e che i periodi di conservazione siano conformi alla politica di classificazione dei dati.

---

### AD.4 Validazione del codice generato da AI

Rilevare e correggere le vulnerabilità introdotte dall'output dell'IA prima che il codice venga integrato o distribuito.

 #AD.4.1    Livello: 1    Ruolo: D/V
 Verificare che il codice generato dall'IA sia sempre sottoposto a revisione umana.
 #AD.4.2    Livello: 2    Ruolo: D
 Verificare che gli scanner automatizzati (SAST/IAST/DAST) vengano eseguiti su ogni pull request contenente codice generato dall'IA e bloccare le fusioni in caso di riscontri critici.
 #AD.4.3    Livello: 3    Ruolo: D/V
 Verificare che i test di fuzzing differenziale o i test basati su proprietà dimostrino comportamenti critici per la sicurezza (ad es., convalida degli input, logica di autorizzazione).

---

### AD.5 Spiegabilità e Tracciabilità dei Suggerimenti di Codice

Fornire agli auditor e agli sviluppatori una panoramica sul motivo per cui è stato fatto un suggerimento e su come è evoluto.

 #AD.5.1    Livello: 1    Ruolo: D/V
 Verificare che le coppie prompt/risposta siano registrate con gli ID di commit.
 #AD.5.2    Livello: 2    Ruolo: D
 Verificare che gli sviluppatori possano mostrare le citazioni del modello (estratti di addestramento, documentazione) a supporto di un suggerimento.
 #AD.5.3    Livello: 3    Ruolo: D/V
 Verificare che i rapporti di spiegabilità siano archiviati insieme agli artefatti di progettazione e citati nelle revisioni di sicurezza, soddisfacendo i principi di tracciabilità ISO/IEC 42001.

---

### AD.6 Feedback Continuo e Messa a Punto del Modello

Migliorare le prestazioni di sicurezza del modello nel tempo prevenendo la deriva negativa.

 #AD.6.1    Livello: 1    Ruolo: D/V
 Verificare che gli sviluppatori possano segnalare suggerimenti non sicuri o non conformi, e che le segnalazioni vengano monitorate.
 #AD.6.2    Livello: 2    Ruolo: D
 Verificare che il feedback aggregato informi il fine-tuning periodico o la generazione aumentata da recupero con corpora di codifica sicura verificati (ad esempio, OWASP Cheat Sheets).
 #AD.6.3    Livello: 3    Ruolo: D/V
 Verificare che un sistema di valutazione a circuito chiuso esegua test di regressione dopo ogni fine-tuning; le metriche di sicurezza devono soddisfare o superare le baseline precedenti prima del rilascio.

---

#### Riferimenti

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Appendice E: Esempi di Strumenti e Framework

### Obiettivo

Questo capitolo fornisce esempi di strumenti e framework che possono supportare l'implementazione o il soddisfacimento di un dato requisito AISVS. Questi non devono essere considerati come raccomandazioni o approvazioni da parte del team AISVS o del progetto OWASP GenAI Security.

---

### AE.1 Governance dei dati di addestramento e gestione dei bias

Strumenti utilizzati per l'analisi dei dati, la governance e la gestione dei bias.

 #AE.1.1    Sezione: 1.1
 Strumenti per l'inventario dei dati: Strumenti per la gestione dell'inventario dei dati come...
 #AE.1.2    Sezione: 1.2
 Crittografia in transito Utilizzare TLS per applicazioni basate su HTTPS, con strumenti come openSSL e python's`ssl`libreria.

---

### AE.2 Validazione dell'Input Utente

Strumenti per gestire e convalidare gli input degli utenti.

 #AE.2.1    Sezione: 2.1
 Strumenti di difesa contro l'iniezione di prompt: utilizzare strumenti di protezione come NeMo di NVIDIA o Guardrails AI.

---

