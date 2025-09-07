# Utilizzo dell’AISVS

Lo Standard di Verifica della Sicurezza dell'Intelligenza Artificiale (AISVS) definisce i requisiti di sicurezza per le moderne applicazioni e servizi di IA, focalizzandosi sugli aspetti sotto il controllo degli sviluppatori delle applicazioni.

L'AISVS è destinato a chiunque sviluppi o valuti la sicurezza delle applicazioni di Intelligenza Artificiale, inclusi sviluppatori, architetti, ingegneri della sicurezza e revisori. Questo capitolo introduce la struttura e l'uso dell'AISVS, comprese le sue modalità di verifica e i casi d'uso previsti.

## Livelli di Verifica della Sicurezza dell'Intelligenza Artificiale

L'AISVS definisce tre livelli crescenti di verifica della sicurezza. Ogni livello aggiunge profondità e complessità, permettendo alle organizzazioni di adattare la loro postura di sicurezza al livello di rischio dei loro sistemi di intelligenza artificiale.

Le organizzazioni possono iniziare dal Livello 1 e adottare progressivamente livelli più elevati man mano che aumentano la maturità della sicurezza e l'esposizione alle minacce.

### Definizione dei Livelli

Ogni requisito in AISVS v1.0 è assegnato a uno dei seguenti livelli:

#### Requisiti di Livello 1

Il Livello 1 include i requisiti di sicurezza più critici e fondamentali. Questi si concentrano sulla prevenzione di attacchi comuni che non si basano su altre precondizioni o vulnerabilità. La maggior parte dei controlli del Livello 1 è semplice da implementare o sufficientemente essenziale da giustificare lo sforzo.

#### Requisiti di livello 2

Il Livello 2 affronta attacchi più avanzati o meno comuni, oltre a difese stratificate contro minacce diffuse. Questi requisiti possono coinvolgere una logica più complessa o mirare a prerequisiti specifici dell’attacco.

#### Requisiti di Livello 3

Il livello 3 include controlli che sono tipicamente più difficili da implementare o di applicabilità situazionale. Questi spesso rappresentano meccanismi di difesa in profondità o mitigazioni contro attacchi di nicchia, mirati o di alta complessità.

### Ruolo (D/V)

Ogni requisito AISVS è contrassegnato in base al pubblico principale:

* D – Requisiti focalizzati sullo sviluppatore
* V – Requisiti focalizzati sul verificatore/revisore
* D/V – Rilevante sia per sviluppatori che per verificatori

