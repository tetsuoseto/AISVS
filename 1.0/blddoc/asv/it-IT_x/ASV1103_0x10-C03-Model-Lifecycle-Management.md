# Gestione del Ciclo di Vita del Modello C3 e Controllo delle Modifiche

## Obiettivo di Controllo

I sistemi di intelligenza artificiale devono implementare processi di controllo delle modifiche che impediscano modifiche non autorizzate o non sicure del modello di raggiungere la produzione. Questo controllo garantisce l'integrità del modello durante l'intero ciclo di vita--dallo sviluppo al dispiegamento fino alla disattivazione--consentendo una risposta rapida agli incidenti e mantenendo la responsabilità per tutte le modifiche.

Obiettivo principale di sicurezza: Solo modelli autorizzati e convalidati raggiungono la produzione impiegando processi controllati che mantengono integrità, tracciabilità e recuperabilità.

---

## C3.1 Autorizzazione e Integrità del Modello

Solo i modelli autorizzati con integrità verificata raggiungono gli ambienti di produzione.

|   #   | Descrizione                                                                                                                                                                                                                                  | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 3.1.1 | Verificare che tutti gli artefatti del modello (pesi, configurazioni, tokenizer) siano firmati crittograficamente da entità autorizzate prima della distribuzione.                                                                           |    1    |  D/V  |
| 3.1.2 | Verificare che il tracciamento delle dipendenze mantenga un inventario in tempo reale che consenta l’identificazione di tutti i sistemi consumatori.                                                                                         |    2    |   V   |
| 3.1.3 | Verificare che i record di provenienza del modello includano l'identità dell'entità autorizzante, i checksum dei dati di addestramento, i risultati dei test di validazione con stato di superamento/insuccesso e un timestamp di creazione. |    3    |  D/V  |

---

## C3.2 Validazione e Test del Modello

I modelli devono superare le convalide di sicurezza e protezione definite prima della distribuzione.

|   #   | Descrizione                                                                                                                                                                                                                                                                    | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 3.2.1 | Verificare che i modelli vengano sottoposti a test di sicurezza automatizzati che includano la convalida degli input, la sanificazione degli output e valutazioni di sicurezza con soglie di superamento/fallimento predefinite dall'organizzazione prima della distribuzione. |    1    |  D/V  |
| 3.2.2 | Verificare che tutte le modifiche al modello (deployment, configurazione, pensionamento) generino registri di audit immutabili che includano un timestamp, un'identità dell'attore autenticata, un tipo di modifica e gli stati precedente/dopo.                               |    1    |   V   |
| 3.2.3 | Verificare che i fallimenti di validazione blocchino automaticamente il deployment del modello dopo l'approvazione esplicita di una deroga da parte del personale autorizzato pre-designato con giustificazioni aziendali documentate.                                         |    2    |  D/V  |

---

## C3.3 Distribuzione Controllata e Ripristino

Le distribuzioni dei modelli devono essere controllate, monitorate e reversibili.

|   #   | Descrizione                                                                                                                                                                                                                                                         | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 3.3.1 | Verificare che i processi di distribuzione convalidino le firme crittografiche e calcolino checksum di integrità prima dell'attivazione del modello, interrompendo la distribuzione in caso di discrepanze.                                                         |    1    |  D/V  |
| 3.3.2 | Verificare che le distribuzioni in produzione implementino meccanismi di rollout graduale (deployment canary, deployment blue-green) con trigger di rollback automatici basati su tassi di errore, soglie di latenza o criteri di allerta di sicurezza predefiniti. |    1    |   D   |
| 3.3.3 | Verificare che le funzionalità di rollback ripristinino lo stato completo del modello (pesi, configurazioni, dipendenze) in modo atomico.                                                                                                                           |    2    |  D/V  |
| 3.3.4 | Verificare che le capacità di spegnimento di emergenza del modello possano disabilitare gli endpoint del modello entro una risposta predefinita.                                                                                                                    |    3    |  D/V  |

---

## C3.4 Pratiche di Sviluppo Sicuro

I processi di sviluppo e addestramento del modello devono seguire pratiche sicure per prevenire compromissioni.

|   #   | Descrizione                                                                                                                                                                                                                                                                          | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 3.4.1 | Verificare che gli ambienti di sviluppo, test e produzione del modello siano separati fisicamente o logicamente. Essi non devono condividere infrastrutture, devono avere controlli di accesso distinti e archivi di dati isolati.                                                   |    1    |  D/V  |
| 3.4.2 | Verificare che gli artefatti di sviluppo del modello (iperparametri, script di addestramento, file di configurazione, modelli di prompt, ecc.) siano archiviati nel controllo delle versioni e richiedano l'approvazione della revisione tra pari prima dell'uso nell'addestramento. |    1    |   D   |
| 3.4.3 | Verificare che l'addestramento e il fine-tuning del modello avvengano in ambienti isolati con accesso di rete controllato.                                                                                                                                                           |    2    |  D/V  |
| 3.4.4 | Verificare che le fonti dei dati di addestramento siano validate tramite controlli di integrità e autenticate tramite fonti affidabili con una documentata catena di custodia prima dell’utilizzo nello sviluppo del modello.                                                        |    2    |   D   |

---

## Ritiro e dismissione del modello C3.5

I modelli devono essere dismessi in modo sicuro quando non sono più necessari o quando vengono identificati problemi di sicurezza.

|   #   | Descrizione                                                                                                                                                                         | Livello | Ruolo |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 3.5.1 | Verificare che gli artefatti del modello dismesso siano cancellati in modo sicuro utilizzando la cancellazione crittografica sicura.                                                |    1    |  D/V  |
| 3.5.2 | Verificare che gli eventi di dismissione del modello siano registrati con data e ora e identità dell'attore, e che le firme del modello siano revocate per prevenire il riutilizzo. |    2    |   V   |

---

## Riferimenti

* [MITRE ATLAS](https://atlas.mitre.org/)
* [MLOps Principles](https://ml-ops.org/content/mlops-principles)
* [Reinforcement fine-tuning](https://platform.openai.com/docs/guides/reinforcement-fine-tuning)
* [What is AI adversarial robustness? – IBM Research](https://research.ibm.com/blog/securing-ai-workflows-with-adversarial-robustness)

