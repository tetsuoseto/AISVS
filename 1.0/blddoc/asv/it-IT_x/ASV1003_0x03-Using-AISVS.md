# Utilizzando l'AISVS

Lo Standard di Verifica della Sicurezza dell'Intelligenza Artificiale (AISVS) definisce i requisiti di sicurezza per le moderne applicazioni e servizi di IA, concentrandosi sugli aspetti entro il controllo degli sviluppatori delle applicazioni.

L'AISVS è destinato a chiunque sviluppi o valuti la sicurezza delle applicazioni di IA, inclusi sviluppatori, architetti, ingegneri della sicurezza e revisori. Questo capitolo presenta la struttura e l'utilizzo dell'AISVS, inclusi i suoi livelli di verifica e i casi d'uso previsti.

## Livelli di verifica della sicurezza dell'intelligenza artificiale

L'AISVS definisce tre livelli crescenti di verifica della sicurezza. Ogni livello aggiunge profondità e complessità, consentendo alle organizzazioni di adeguare la propria postura di sicurezza al livello di rischio dei loro sistemi di IA.

Le organizzazioni possono iniziare dal Livello 1 e adottare progressivamente livelli superiori man mano che aumentano la maturità della sicurezza e l'esposizione alle minacce.

### Definizione dei livelli

Ogni requisito in AISVS v1.0 viene assegnato a uno dei seguenti livelli:

#### Requisiti di livello 1

Livello 1 include i requisiti di sicurezza più critici e fondamentali. Questi si concentrano sulla prevenzione di attacchi comuni che non dipendono da altri prerequisiti o vulnerabilità. La maggior parte dei controlli di Livello 1 è di facile implementazione o è abbastanza essenziale da giustificare l'impegno.

#### Requisiti di livello 2

Livello 2 affronta attacchi più avanzati o meno comuni, nonché difese a strati contro minacce diffuse. Questi requisiti possono comportare una logica più complessa o mirare a prerequisiti specifici dell'attacco.

#### Requisiti di livello 3

Il livello 3 include controlli che sono tipicamente più difficili da implementare o applicabili solo in determinate situazioni. Questi controlli spesso rappresentano meccanismi di difesa in profondità o mitigazioni contro attacchi di nicchia, mirati o ad alta complessità.

### Ruolo (D/V)

Ogni requisito AISVS è contrassegnato in base al pubblico primario:

* D – Requisiti orientati agli sviluppatori
* V – Requisiti incentrati sul verificatore/auditor
* D/V – Rilevante sia per gli sviluppatori che per i verificatori

