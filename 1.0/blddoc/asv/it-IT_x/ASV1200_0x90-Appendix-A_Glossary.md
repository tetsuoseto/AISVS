# Appendice A: Glossario

>Questo glossario completo fornisce definizioni dei termini chiave di AI, ML e sicurezza utilizzati in tutto l'AISVS per garantire chiarezza e comprensione comune.

* Esempio avversario: un input deliberatamente creato per far commettere un errore a un modello di IA, spesso aggiungendo sottili perturbazioni impercettibili agli esseri umani.
  ​
* Robustezza Avversaria – La robustezza avversaria nell'AI si riferisce alla capacità di un modello di mantenere le proprie prestazioni e resistere a essere ingannato o manipolato da input intenzionalmente creati e dannosi, progettati per causare errori.
  ​
* Agente – Gli agenti AI sono sistemi software che utilizzano l'intelligenza artificiale per perseguire obiettivi e completare compiti per conto degli utenti. Mostrano capacità di ragionamento, pianificazione e memoria e possiedono un livello di autonomia per prendere decisioni, apprendere e adattarsi.
  ​
* Agentic AI: Sistemi di intelligenza artificiale che possono operare con un certo grado di autonomia per raggiungere obiettivi, spesso prendendo decisioni e compiendo azioni senza intervento umano diretto.
  ​
* Controllo di Accesso Basato su Attributi (ABAC): un paradigma di controllo degli accessi in cui le decisioni di autorizzazione si basano sugli attributi dell'utente, della risorsa, dell'azione e dell'ambiente, valutati al momento della richiesta.
  ​
* Attacco Backdoor: Un tipo di attacco di avvelenamento dei dati in cui il modello viene addestrato a rispondere in un modo specifico a determinati trigger mentre si comporta normalmente altrimenti.
  ​
* Bias: Errori sistematici nei risultati dei modelli di IA che possono portare a risultati ingiusti o discriminatori per determinati gruppi o in contesti specifici.
  ​
* Sfruttamento dei Bias: Una tecnica di attacco che sfrutta i bias noti nei modelli di AI per manipolare risultati o esiti.
  ​
* Cedar: il linguaggio e il motore di policy di Amazon per permessi dettagliati utilizzati nell'implementazione di ABAC per sistemi di intelligenza artificiale.
  ​
* Catena di pensiero: una tecnica per migliorare il ragionamento nei modelli linguistici generando passaggi intermedi di ragionamento prima di produrre una risposta finale.
  ​
* Interruttori automatici: Meccanismi che interrompono automaticamente le operazioni del sistema AI quando vengono superate specifiche soglie di rischio.
  ​
* Servizio di Inferenza Confidenziale: un servizio di inferenza che esegue modelli di intelligenza artificiale all'interno di un ambiente di esecuzione attendibile (TEE) o di un meccanismo equivalente di calcolo confidenziale, garantendo che i pesi del modello e i dati di inferenza rimangano criptati, sigillati e protetti da accessi non autorizzati o manomissioni.
  ​
* Carico di lavoro confidenziale: un carico di lavoro AI (ad esempio, training, inferenza, preprocessing) eseguito all'interno di un ambiente di esecuzione affidabile (TEE) con isolamento hardware, crittografia della memoria e attestazione remota per proteggere codice, dati e modelli dall'accesso da parte dell'host o di co-tenant.
  ​
* Perdita di dati: esposizione involontaria di informazioni sensibili tramite output o comportamento del modello AI.
  ​
* Avvelenamento dei dati: la corruzione deliberata dei dati di addestramento per compromettere l'integrità del modello, spesso per installare backdoor o degradare le prestazioni.
  ​
* Privacy differenziale – La privacy differenziale è un quadro matematicamente rigoroso per la divulgazione di informazioni statistiche su insiemi di dati proteggendo al contempo la privacy dei singoli soggetti dei dati. Consente a chi detiene i dati di condividere modelli aggregati del gruppo limitando le informazioni che vengono rivelate su individui specifici.
  ​
* Embedding: Rappresentazioni vettoriali dense di dati (testo, immagini, ecc.) che catturano il significato semantico in uno spazio ad alta dimensione.
  ​
* Spiegabilità – La spiegabilità nell'IA è la capacità di un sistema di intelligenza artificiale di fornire motivazioni comprensibili all’essere umano per le proprie decisioni e previsioni, offrendo approfondimenti sul suo funzionamento interno.
  ​
* Intelligenza Artificiale Spiegabile (XAI): sistemi di intelligenza artificiale progettati per fornire spiegazioni comprensibili agli esseri umani riguardo alle loro decisioni e comportamenti attraverso diverse tecniche e framework.
  ​
* Apprendimento Federato: un approccio di machine learning in cui i modelli vengono addestrati su più dispositivi decentralizzati che possiedono campioni di dati locali, senza scambiare i dati stessi.
  ​
* Formulazione: La ricetta o il metodo utilizzato per produrre un artefatto o un dataset, come gli iperparametri, la configurazione dell'addestramento, i passaggi di preprocessamento o gli script di compilazione.
  ​
* Limitazioni: Vincoli implementati per prevenire che i sistemi di IA producano risultati dannosi, parziali o altrimenti indesiderati.
  ​
* Allucinazione – Un'allucinazione dell'IA si riferisce a un fenomeno in cui un modello di IA genera informazioni errate o fuorvianti che non si basano sui suoi dati di addestramento o sulla realtà fattuale.
  ​
* Human-in-the-Loop (HITL): Sistemi progettati per richiedere supervisione, verifica o intervento umano in punti decisionali cruciali.
  ​
* Infrastructure as Code (IaC): Gestione e provisioning dell'infrastruttura tramite codice anziché processi manuali, consentendo la scansione della sicurezza e distribuzioni coerenti.
  ​
* Jailbreak: Tecniche utilizzate per eludere i vincoli di sicurezza nei sistemi di intelligenza artificiale, in particolare nei grandi modelli linguistici, per produrre contenuti proibiti.
  ​
* Minimo privilegio: Il principio di sicurezza che concede solo i diritti di accesso minimi necessari per utenti e processi.
  ​
* LIME (Local Interpretable Model-agnostic Explanations): Una tecnica per spiegare le predizioni di qualsiasi classificatore di machine learning approssimandolo localmente con un modello interpretabile.
  ​
* Attacco di Inferenza di Membri: Un attacco che mira a determinare se un dato specifico è stato utilizzato per addestrare un modello di machine learning.
  ​
* MITRE ATLAS: Paesaggio delle minacce avversarie per i sistemi di intelligenza artificiale; una base di conoscenza delle tattiche e tecniche avversarie contro i sistemi di IA.
  ​
* Scheda Modello – Una scheda modello è un documento che fornisce informazioni standardizzate sulle prestazioni di un modello di intelligenza artificiale, sui limiti, sugli utilizzi previsti e sulle considerazioni etiche per promuovere la trasparenza e lo sviluppo responsabile dell’intelligenza artificiale.
  ​
* Estrazione del modello: Un attacco in cui un avversario interroga ripetutamente un modello di destinazione per creare una copia funzionalmente simile senza autorizzazione.
  ​
* Inversione del modello: un attacco che tenta di ricostruire i dati di addestramento analizzando gli output del modello.
  ​
* Gestione del Ciclo di Vita del Modello – La gestione del ciclo di vita del modello AI è il processo di supervisione di tutte le fasi dell'esistenza di un modello AI, inclusi progettazione, sviluppo, distribuzione, monitoraggio, manutenzione e eventuale dismissione, per garantire che rimanga efficace e allineato agli obiettivi.
  ​
* Avvelenamento del modello: introdurre vulnerabilità o backdoor direttamente in un modello durante il processo di addestramento.
  ​
* Furto/Rubare un Modello: Estrarre una copia o un'approssimazione di un modello proprietario tramite ripetute interrogazioni.
  ​
* Sistema multi-agente: un sistema composto da più agenti di IA interagenti, ciascuno con potenzialmente capacità e obiettivi differenti.
  ​
* OPA (Open Policy Agent): Un motore di policy open-source che consente l'applicazione unificata delle policy a tutti i livelli della stack.
  ​
* Provenienza: La genealogia e la catena di custodia di un artefatto o un dataset, compresi la sua origine, i responsabili, il percorso di trasferimento e le prove di integrità (ad esempio, checksum, firme).
  ​
* Apprendimento Automatico Preservante la Privacy (PPML): Tecniche e metodi per addestrare e distribuire modelli di ML proteggendo la privacy dei dati di addestramento.
  ​
* Iniezione di prompt: un attacco in cui istruzioni dannose sono inserite negli input per sovrascrivere il comportamento previsto di un modello.
  ​
* RAG (Generazione Incrementata dal Recupero): Una tecnica che migliora i grandi modelli linguistici recuperando informazioni rilevanti da fonti di conoscenza esterne prima di generare una risposta.
  ​
* Red-Teaming: La pratica di testare attivamente i sistemi di IA simulando attacchi avversari per identificare le vulnerabilità.
  ​
* Provenienza SLSA: Metadati definiti dal framework SLSA che registrano dove, quando e come è stato prodotto un artefatto (ad esempio, repository sorgente, hash del commit, sistema di build e parametri).
  ​
* SBOM (Elenco dei Materiali Software): Un registro formale contenente i dettagli e le relazioni della catena di fornitura di vari componenti utilizzati nella creazione di software o modelli di AI.
  ​
* SHAP (SHapley Additive exPlanations): un approccio basato sulla teoria dei giochi per spiegare l’output di qualsiasi modello di machine learning calcolando il contributo di ciascuna caratteristica alla previsione.
  ​
* Autenticazione Forte: Autenticazione che resiste al furto di credenziali e al replay richiedendo almeno due fattori (conoscenza, possesso, inherenza) e meccanismi resistenti al phishing come FIDO2/WebAuthn, autenticazione di servizio basata su certificato o token a breve durata.
  ​
* Attacco alla catena di approvvigionamento: compromettere un sistema prendendo di mira elementi meno sicuri nella sua catena di approvvigionamento, come librerie di terze parti, set di dati o modelli pre-addestrati.
  ​
* Apprendimento di trasferimento: una tecnica in cui un modello sviluppato per un compito viene riutilizzato come punto di partenza per un modello su un secondo compito.
  ​
* Database vettoriale: un database specializzato progettato per memorizzare vettori ad alta dimensionalità (embedding) ed eseguire ricerche di similarità in modo efficiente.
  ​
* Scansione delle vulnerabilità: Strumenti automatizzati che identificano le vulnerabilità di sicurezza note nei componenti software, inclusi i framework AI e le dipendenze.
  ​
* Watermarking: Tecniche per incorporare marcatori impercettibili nei contenuti generati dall'IA per tracciare la loro origine o rilevare la generazione da parte dell'IA.
  ​
* Vulnerabilità Zero-Day: Una vulnerabilità precedentemente sconosciuta che gli attaccanti possono sfruttare prima che gli sviluppatori creino e distribuiscano una patch.

