# Appendice A: Glossario

>Questo glossario completo fornisce definizioni dei principali termini di IA, ML e sicurezza utilizzati in AISVS per garantire chiarezza e una comprensione comune.

* Esempio avversario: un input appositamente progettato per indurre un modello di IA a commettere un errore, spesso aggiungendo perturbazioni sottili impercettibili agli esseri umani.
  ​
* Robustezza avversaria – La robustezza avversaria nell'IA si riferisce alla capacità di un modello di mantenere le proprie prestazioni e di resistere all'inganno o alla manipolazione da input intenzionalmente creati, maliziosi, progettati per causare errori.
  ​
* Agente – Gli agenti IA sono sistemi software che utilizzano l'IA per perseguire obiettivi e completare compiti per conto degli utenti. Essi mostrano ragionamento, pianificazione e memoria e hanno un livello di autonomia per prendere decisioni, imparare e adattarsi.
  ​
* IA agentiva: sistemi di intelligenza artificiale che possono operare con un certo grado di autonomia per raggiungere obiettivi, spesso prendendo decisioni e intraprendendo azioni senza l'intervento diretto dell'essere umano.
  ​
* Controllo di accesso basato su attributi (ABAC): un paradigma di controllo degli accessi in cui le decisioni di autorizzazione si basano sugli attributi dell'utente, della risorsa, dell'azione e dell'ambiente, valutati al momento dell'interrogazione.
  ​
* Attacco con backdoor: un tipo di attacco di avvelenamento dei dati in cui il modello viene addestrato a rispondere in modo specifico a determinati inneschi, comportandosi altrimenti normalmente.
  ​
* Pregiudizio: Errori sistematici negli output dei modelli di IA che possono portare a esiti ingiusti o discriminatori per determinati gruppi o in contesti specifici.
  ​
* Sfruttamento dei bias: una tecnica di attacco che sfrutta bias noti nei modelli di IA per manipolare gli output o gli esiti.
  ​
* Cedar: linguaggio di policy di Amazon e motore per autorizzazioni a granularità fine utilizzati per implementare ABAC per sistemi di IA.
  ​
* Catena di pensiero: una tecnica per migliorare il ragionamento nei modelli linguistici generando passaggi di ragionamento intermedi prima di produrre una risposta finale.
  ​
* Interruttori di circuito: Meccanismi che interrompono automaticamente le operazioni dei sistemi di IA quando si superano soglie di rischio specifiche.
  ​
* Fuga di dati: Esposizione non intenzionale di informazioni sensibili tramite gli output o il comportamento del modello di IA.
  ​
* Avvelenamento dei dati: la corruzione deliberata dei dati di addestramento per compromettere l'integrità del modello, spesso per installare backdoor o degradare le prestazioni.
  ​
* Privacy differenziale – La privacy differenziale è un quadro matematicamente rigoroso per rilasciare informazioni statistiche sugli insiemi di dati, proteggendo la privacy degli individui. Consente al detentore dei dati di condividere schemi aggregati del gruppo, limitando al contempo le informazioni che vengono rivelate su singoli individui.
  ​
* Embeddings: Rappresentazioni vettoriali dense dei dati (testo, immagini, ecc.) che catturano il significato semantico in uno spazio ad alta dimensione.
  ​
* Spiegabilità – La spiegabilità nell'IA è la capacità di un sistema di IA di fornire ragioni comprensibili agli esseri umani per le sue decisioni e predizioni, offrendo intuizioni sul suo funzionamento interno.
  ​
* Intelligenza artificiale spiegabile (XAI): sistemi di IA progettati per fornire spiegazioni comprensibili agli esseri umani riguardo alle loro decisioni e ai loro comportamenti, attraverso varie tecniche e quadri di riferimento.
  ​
* Apprendimento Federato: un approccio di apprendimento automatico in cui i modelli vengono addestrati su più dispositivi decentralizzati che ospitano campioni di dati locali, senza scambiare i dati stessi.
  ​
* Barriere di sicurezza: vincoli implementati per impedire ai sistemi di IA di produrre output dannosi, pregiudizievoli o altrimenti indesiderati.
  ​
* Allucinazione – Un'allucinazione dell'IA si riferisce a un fenomeno in cui un modello di IA genera informazioni errate o fuorvianti che non si basano sui suoi dati di addestramento o sulla realtà fattuale.
  ​
* Umano nel ciclo (HITL): Sistemi progettati per richiedere supervisione, verifica o intervento umano in punti decisionali cruciali.
  ​
* Infrastruttura come codice (IaC): gestione e provisioning dell'infrastruttura tramite codice anziché processi manuali, consentendo la scansione di sicurezza e implementazioni coerenti.
  ​
* Jailbreak: Tecniche usate per aggirare le barriere di sicurezza nei sistemi di IA, in particolare nei grandi modelli di linguaggio, per produrre contenuti vietati.
  ​
* Principio del minimo privilegio: il principio di sicurezza che prevede di concedere solo i diritti di accesso strettamente necessari agli utenti e ai processi.
  ​
* LIME (Spiegazioni Locali Interpretabili Indipendenti dal Modello): Una tecnica per spiegare le predizioni di qualsiasi classificatore di apprendimento automatico approssimandolo localmente con un modello interpretabile.
  ​
* Attacco di inferenza di appartenenza: un attacco che mira a determinare se un determinato dato sia stato utilizzato per addestrare un modello di apprendimento automatico.
  ​
* MITRE ATLAS: Paesaggio delle minacce avversarie per i sistemi di intelligenza artificiale; una base di conoscenza delle tattiche e delle tecniche avversarie contro i sistemi di IA.
  ​
* Scheda del modello – Una scheda del modello è un documento che fornisce informazioni standardizzate sulle prestazioni di un modello di IA, sulle sue limitazioni, sugli usi previsti e sulle considerazioni etiche, al fine di promuovere la trasparenza e lo sviluppo responsabile dell'IA.
  ​
* Estrazione del modello: un attacco in cui un avversario interroga ripetutamente un modello bersaglio per creare una copia funzionalmente simile senza autorizzazione.
  ​
* Inversione del modello: un attacco che tenta di ricostruire i dati di addestramento analizzando gli output del modello.
  ​
* Gestione del ciclo di vita del modello – La gestione del ciclo di vita dei modelli di IA è il processo di supervisione di tutte le fasi dell’esistenza di un modello di IA, tra cui progettazione, sviluppo, messa in produzione, monitoraggio, manutenzione e l’eventuale ritiro, al fine di garantire che rimanga efficace e allineato agli obiettivi.
  ​
* Avvelenamento del modello: introdurre vulnerabilità o backdoor direttamente in un modello durante il processo di addestramento.
  ​
* Furto del modello: Estrarre una copia o un'approssimazione di un modello proprietario tramite richieste ripetute.
  ​
* Sistema multiagente: un sistema composto da più agenti IA interagenti, ciascuno con capacità e obiettivi potenzialmente differenti.
  ​
* OPA (Open Policy Agent): un motore di policy open-source che consente l'applicazione uniforme delle politiche in tutto lo stack.
  ​
* Privacy-Preserving Machine Learning (PPML): Tecniche e metodi per addestrare e distribuire modelli ML, proteggendo la privacy dei dati di addestramento.
  ​
* Prompt Injection: un attacco in cui istruzioni malevole sono inserite negli input per sovrascrivere il comportamento previsto dal modello.
  ​
* RAG (Retrieval-Augmented Generation): una tecnica che migliora i grandi modelli di linguaggio recuperando informazioni rilevanti da fonti di conoscenza esterne prima di generare una risposta.
  ​
* Red-Teaming: La pratica di testare attivamente i sistemi di IA simulando attacchi avversariali per identificare vulnerabilità.
  ​
* SBOM (Distinta dei materiali del software): Un registro formale contenente i dettagli e le relazioni della catena di fornitura di vari componenti utilizzati per costruire software o modelli di IA.
  ​
* SHAP (SHapley Additive exPlanations): un approccio teorico dei giochi per spiegare l'output di qualsiasi modello di apprendimento automatico calcolando il contributo di ciascuna caratteristica alla previsione.
  ​
* Attacco alla catena di fornitura: compromettere un sistema prendendo di mira elementi meno sicuri della sua catena di fornitura, come librerie di terze parti, set di dati o modelli preaddestrati.
  ​
* Apprendimento trasferibile: Una tecnica in cui un modello sviluppato per un compito viene riutilizzato come punto di partenza per un modello su un secondo compito.
  ​
* Database vettoriale: un database specializzato progettato per archiviare vettori ad alta dimensione (embedding) e per eseguire ricerche di similarità efficienti.
  ​
* Scansione delle vulnerabilità: Strumenti automatizzati che identificano vulnerabilità di sicurezza note nei componenti software, inclusi framework di IA e dipendenze.
  ​
* Marcatura ad acqua digitale: Tecniche per inserire marcatori impercettibili nel contenuto generato dall'IA per tracciare la sua origine o rilevare se è stata generata dall'IA.
  ​
* Vulnerabilità zero-day: una vulnerabilità precedentemente sconosciuta che gli aggressori possono sfruttare prima che gli sviluppatori creino e distribuiscano una patch.

