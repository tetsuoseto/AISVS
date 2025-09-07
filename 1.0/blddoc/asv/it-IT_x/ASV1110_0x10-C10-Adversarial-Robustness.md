# 10 Robustezza Avversaria e Difesa della Privacy

## Obiettivo di Controllo

Garantire che i modelli di AI rimangano affidabili, rispettosi della privacy e resistenti agli abusi quando affrontano attacchi di elusione, inferenza, estrazione o avvelenamento.

---

## 10.1 Allineamento e Sicurezza del Modello

Proteggere contro output dannosi o contrari alle politiche.

|   #    | Descrizione                                                                                                                                                                                               | Livello | Ruolo |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 10.1.1 | Verificare che una suite di test di allineamento (prompt del red-team, sonde per jailbreak, contenuti non consentiti) sia gestita con controllo di versione e venga eseguita a ogni rilascio del modello. |    1    |  D/V  |
| 10.1.2 | Verificare che siano applicate le misure di sicurezza per il rifiuto e il completamento sicuro.                                                                                                           |    1    |   D   |
| 10.1.3 | Verifica che un valutatore automatico misuri il tasso di contenuti dannosi e segnali regressioni oltre una soglia prestabilita.                                                                           |    2    |  D/V  |
| 10.1.4 | Verificare che l'addestramento contro i jailbreak sia documentato e riproducibile.                                                                                                                        |    2    |   D   |
| 10.1.5 | Verificare che le prove di conformità formale alle politiche o il monitoraggio certificato coprano domini critici.                                                                                        |    3    |   V   |

---

## 10.2 Rafforzamento contro esempi avversari

Aumentare la resilienza agli input manipolati. L'addestramento avversariale robusto e la valutazione tramite benchmark sono le migliori pratiche attuali.

|   #    | Descrizione                                                                                                                     | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 10.2.1 | Verificare che i repository del progetto includano configurazioni di addestramento avversariale con semi riproducibili.         |    1    |   D   |
| 10.2.2 | Verificare che il rilevamento di esempi avversari sollevi avvisi di blocco nelle pipeline di produzione.                        |    2    |  D/V  |
| 10.2.4 | Verificare che le prove di robustezza certificate o i certificati di intervallo coprano almeno le principali classi critiche.   |    3    |   V   |
| 10.2.5 | Verificare che i test di regressione utilizzino attacchi adattivi per confermare l’assenza di perdita di robustezza misurabile. |    3    |   V   |

---

## 10.3 Mitigazione dell'inferenza di appartenenza

Limitare la capacità di decidere se un record era nei dati di addestramento. La privacy differenziale e la mascheratura del punteggio di confidenza restano le difese conosciute più efficaci.

|   #    | Descrizione                                                                                                                           | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 10.3.1 | Verificare che la regolarizzazione dell'entropia per query o la scala della temperatura riducano le predizioni eccessivamente sicure. |    1    |   D   |
| 10.3.2 | Verificare che l'addestramento utilizzi un'ottimizzazione differenzialmente privata con vincolo ε per i dataset sensibili.            |    2    |   D   |
| 10.3.3 | Verificare che le simulazioni di attacco (modello shadow o black-box) mostrino un AUC di attacco ≤ 0,60 sui dati di test.             |    2    |   V   |

---

## 10.4 Resistenza all'inversione del modello

Prevenire la ricostruzione degli attributi privati. Recenti indagini sottolineano la troncatura dell'output e le garanzie DP come difese pratiche.

|   #    | Descrizione                                                                                                                                        | Livello | Ruolo |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 10.4.1 | Verificare che gli attributi sensibili non vengano mai esportati direttamente; dove necessario, utilizzare bucket o trasformazioni unidirezionali. |    1    |   D   |
| 10.4.2 | Verificare che i limiti di frequenza delle query limitino le query adattive ripetute dallo stesso principale.                                      |    1    |  D/V  |
| 10.4.3 | Verifica che il modello sia addestrato con rumore che preserva la privacy.                                                                         |    2    |   D   |

---

## 10.5 Difesa contro l'estrazione del modello

Rilevare e scoraggiare la clonazione non autorizzata. Si consigliano watermarking e analisi dei modelli di query.

|   #    | Descrizione                                                                                                                                              | Livello | Ruolo |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 10.5.1 | Verificare che i gateway di inferenza applichino limiti di velocità globali e per singola chiave API, tarati sulla soglia di memorizzazione del modello. |    1    |   D   |
| 10.5.2 | Verificare che le statistiche di entropia della query e di pluralità dell’input alimentino un rilevatore di estrazione automatica.                       |    2    |  D/V  |
| 10.5.3 | Verificare che i watermark fragili o probabilistici possano essere dimostrati con p < 0,01 in ≤ 1 000 query contro un clone sospetto.                    |    2    |   V   |
| 10.5.4 | Verificare che le chiavi di watermark e i set di trigger siano memorizzati in un modulo di sicurezza hardware e ruotati annualmente.                     |    3    |   D   |
| 10.5.5 | Verificare che gli eventi di extraction-alert includano le query offender e siano integrati con i playbook di risposta agli incidenti.                   |    3    |   V   |

---

## 10.6 Rilevamento di dati avvelenati durante l'inferenza

Identificare e neutralizzare gli input con backdoor o avvelenati.

|   #    | Descrizione                                                                                                                                         | Livello | Ruolo |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 10.6.1 | Verificare che gli input vengano analizzati da un rilevatore di anomalie (ad esempio, STRIP, scoring di coerenza) prima dell'inferenza del modello. |    1    |   D   |
| 10.6.2 | Verificare che le soglie del rilevatore siano regolate su set di validazione puliti/avvelenati per ottenere meno del 5% di falsi positivi.          |    1    |   V   |
| 10.6.3 | Verificare che gli input segnalati come avvelenati attivino il soft-blocking e i flussi di lavoro per la revisione umana.                           |    2    |   D   |
| 10.6.4 | Verificare che i rilevatori siano sottoposti a stress test con attacchi backdoor adattativi e senza trigger.                                        |    2    |   V   |
| 10.6.5 | Verificare che le metriche di efficacia del rilevamento siano registrate e riesaminate periodicamente con nuove informazioni sulle minacce.         |    3    |   D   |

---

## 10.7 Adattamento Dinamico della Politica di Sicurezza

Aggiornamenti in tempo reale delle politiche di sicurezza basati su intelligence sulle minacce e analisi comportamentale.

|   #    | Descrizione                                                                                                                                                                    | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 10.7.1 | Verificare che le politiche di sicurezza possano essere aggiornate dinamicamente senza il riavvio dell’agente mantenendo l’integrità della versione della politica.            |    1    |  D/V  |
| 10.7.2 | Verificare che gli aggiornamenti delle politiche siano firmati crittograficamente da personale di sicurezza autorizzato e convalidati prima dell'applicazione.                 |    2    |  D/V  |
| 10.7.3 | Verificare che le modifiche dinamiche alla policy vengano registrate con tracce di audit complete, includendo giustificazioni, catene di approvazione e procedure di rollback. |    2    |  D/V  |
| 10.7.4 | Verificare che i meccanismi di sicurezza adattivi regolino la sensibilità del rilevamento delle minacce in base al contesto di rischio e ai modelli comportamentali.           |    3    |  D/V  |
| 10.7.5 | Verificare che le decisioni di adattamento delle policy siano spiegabili e includano tracce di evidenza per la revisione del team di sicurezza.                                |    3    |  D/V  |

---

## 10.8 Analisi della Sicurezza Basata sulla Riflessività

Validazione della sicurezza tramite auto-riflessione dell’agente e analisi meta-cognitiva.

|   #    | Descrizione                                                                                                                                                   | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 10.8.1 | Verificare che i meccanismi di riflessione dell'agente includano un'autovalutazione focalizzata sulla sicurezza delle decisioni e delle azioni.               |    1    |  D/V  |
| 10.8.2 | Verificare che gli output della riflessione siano convalidati per prevenire la manipolazione dei meccanismi di autovalutazione da parte di input avversari.   |    2    |  D/V  |
| 10.8.3 | Verificare che l'analisi meta-cognitiva della sicurezza identifichi potenziali bias, manipolazioni o compromissioni nei processi di ragionamento dell'agente. |    2    |  D/V  |
| 10.8.4 | Verificare che gli avvisi di sicurezza basati sulla riflessione attivino il monitoraggio avanzato e i potenziali flussi di lavoro di intervento umano.        |    3    |  D/V  |
| 10.8.5 | Verificare che l'apprendimento continuo dalle riflessioni sulla sicurezza migliori il rilevamento delle minacce senza degradare la funzionalità legittima.    |    3    |  D/V  |

---

## 10.9 Evoluzione e Auto-Miglioramento della Sicurezza

Controlli di sicurezza per sistemi agenti capaci di auto-modifica ed evoluzione.

|   #    | Descrizione                                                                                                                               | Livello | Ruolo |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 10.9.1 | Verificare che le capacità di automodifica siano limitate ad aree designate come sicure con confini di verifica formale.                  |    1    |  D/V  |
| 10.9.2 | Verificare che le proposte di evoluzione siano sottoposte ad una valutazione dell’impatto sulla sicurezza prima dell’implementazione.     |    2    |  D/V  |
| 10.9.3 | Verificare che i meccanismi di auto-miglioramento includano capacità di rollback con verifica dell'integrità.                             |    2    |  D/V  |
| 10.9.4 | Verificare che la sicurezza del meta-apprendimento prevenga la manipolazione avversaria degli algoritmi di miglioramento.                 |    3    |  D/V  |
| 10.9.5 | Verificare che il miglioramento auto-ricorsivo sia limitato da vincoli formali di sicurezza con dimostrazioni matematiche di convergenza. |    3    |  D/V  |

---

### Riferimenti

* [MITRE ATLAS adversary tactics for ML](https://atlas.mitre.org/)
* [NIST AI Risk Management Framework 1.0, 2023](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [OWASP Top 10 for LLM Applications, 2025](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Adversarial Training: A Survey — Zhao et al., 2024](https://arxiv.org/abs/2410.15042)
* [RobustBench adversarial-robustness benchmark](https://robustbench.github.io/)
* [Membership-Inference & Model-Inversion Risk Survey, 2025](https://www.sciencedirect.com/science/article/abs/pii/S0950705125003867)
* [PURIFIER: Confidence-Score Defense against MI Attacks — AAAI 2023](https://ojs.aaai.org/index.php/AAAI/article/view/26289)
* [Model-Inversion Attacks & Defenses Survey — AI Review, 2025](https://link.springer.com/article/10.1007/s10462-025-11248-0)
* [Comprehensive Defense Framework Against Model Extraction — IEEE TDSC 2024](https://doi.org/10.1109/TDSC.2023.3261327)
* [Fragile Model Watermarking Survey — 2025](https://www.sciencedirect.com/science/article/abs/pii/S0165168425002026)
* [Data Poisoning in Deep Learning: A Survey — Zhao et al., 2025](https://arxiv.org/abs/2503.22759)
* [BDetCLIP: Multimodal Prompting Backdoor Detection — Niu et al., 2024](https://arxiv.org/abs/2405.15269)

