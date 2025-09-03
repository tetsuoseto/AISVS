# 10 Robustezza Avversaria e Difesa della Privacy

## Obiettivo di controllo

Assicura che i modelli di IA rimangano affidabili, rispettosi della privacy e resistenti agli abusi quando affrontano attacchi di elusione, inferenza, estrazione o avvelenamento.

---

## 10.1 Allineamento del modello e sicurezza

Proteggi da output dannosi o che violano le policy.

|   #    | Descrizione                                                                                                                                                               | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 10.1.1 | Verifica che un test-suite di allineamento (red-team prompts, jailbreak probes, disallowed content) sia version-controlled e venga eseguito ad ogni rilascio del modello. |    1    |  D/V  |
| 10.1.2 | Verifica che le barriere di rifiuto e di completamento sicuro siano applicate.                                                                                            |    1    |   D   |
| 10.1.3 | Verifichi che un valutatore automatizzato misuri il tasso di contenuti dannosi e segnali le regressioni oltre una soglia prestabilita.                                    |    2    |  D/V  |
| 10.1.4 | Verificare che l'addestramento contro il jailbreaking sia documentato e riproducibile.                                                                                    |    2    |   D   |
| 10.1.5 | Verifichi che le prove formali di conformità alle politiche o il monitoraggio certificato coprano domini critici.                                                         |    3    |   V   |

---

## 10.2 Rafforzamento contro esempi avversari

Aumentare la resilienza agli input manipolati. L'addestramento avversario robusto e la valutazione tramite benchmark sono le migliori pratiche attuali.

|   #    | Descrizione                                                                                                                   | Livello | Ruolo |
| :----: | ----------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 10.2.1 | Verifica che i repository di progetto includano configurazioni di addestramento avversario con semi riproducibili.            |    1    |   D   |
| 10.2.2 | Verifica che il rilevamento di esempi avversari generi avvisi di blocco nelle pipeline di produzione.                         |    2    |  D/V  |
| 10.2.4 | Verifica che le prove di robustezza-certificata o i certificati a intervallo coprano almeno le classi più critiche.           |    3    |   V   |
| 10.2.5 | Verifica che i test di regressione utilizzino attacchi adattivi per confermare l'assenza di perdita di robustezza misurabile. |    3    |   V   |

---

## 10.3 Mitigazione dell'inferenza di appartenenza

Limitare la capacità di determinare se un record fosse presente nei dati di addestramento. La privacy differenziale e il mascheramento dei punteggi di confidenza restano le difese note più efficaci.

|   #    | Descrizione                                                                                                                                | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 10.3.1 | Verifica che la regolarizzazione dell'entropia per query o la calibrazione tramite temperatura riduca le previsioni eccessivamente sicure. |    1    |   D   |
| 10.3.2 | Verifica che l'addestramento impieghi un’ottimizzazione differenzialmente privata vincolata da ε per set di dati sensibili.                |    2    |   D   |
| 10.3.3 | Verifica che le simulazioni di attacco (modello-ombra o scatola nera) mostrino l'AUC dell'attacco ≤ 0.60 sui dati hold-out.                |    2    |   V   |

---

## 10.4 Resistenza all'inversione del modello

Impedire la ricostruzione degli attributi privati. I recenti studi sottolineano il troncamento dell'output e le garanzie di privacy differenziale come difese pratiche.

|   #    | Descrizione                                                                                                                                                  | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 10.4.1 | Verificare che gli attributi sensibili non vengano mai forniti direttamente; dove necessario, utilizzare la bucketizzazione o trasformazioni unidirezionali. |    1    |   D   |
| 10.4.2 | Verificare che i limiti di frequenza delle query limitino le interrogazioni adattive ripetute provenienti dallo stesso soggetto.                             |    1    |  D/V  |
| 10.4.3 | Verifica che il modello sia addestrato con rumore che preserva la privacy.                                                                                   |    2    |   D   |

---

## 10.5 Difesa contro l'estrazione del modello

Rilevare e scoraggiare la clonazione non autorizzata. Si consiglia la marchiatura digitale e l'analisi dei pattern di query.

|   #    | Descrizione                                                                                                                                          | Livello | Ruolo |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 10.5.1 | Verificare che i gateway di inferenza applichino limiti di velocità globali e per chiave API adeguati alla soglia di memorizzazione del modello.     |    1    |   D   |
| 10.5.2 | Verifica che le statistiche di entropia della query e di pluralità dell'input alimentino un rilevatore di estrazione automatizzato.                  |    2    |  D/V  |
| 10.5.3 | Verificare che le filigrane fragili o probabilistiche possano essere dimostrate con p < 0,01 in ≤ 1 000 richieste contro un clone sospetto.          |    2    |   V   |
| 10.5.4 | Verificare che le chiavi della filigrana e gli insiemi di trigger siano archiviati in un modulo di sicurezza hardware e vengano ruotati annualmente. |    3    |   D   |
| 10.5.5 | Verifica che gli eventi di allerta di estrazione includano query offensive e siano integrati con i playbook di risposta agli incidenti.              |    3    |   V   |

---

## 10.6 Rilevamento dei dati avvelenati durante l'inferenza

Identificare e neutralizzare input compromessi da backdoor o avvelenati.

|   #    | Descrizione                                                                                                                                        | Livello | Ruolo |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 10.6.1 | Verifica che gli input passino attraverso un rilevatore di anomalie (ad es. STRIP, punteggio di coerenza) prima dell'inferenza del modello.        |    1    |   D   |
| 10.6.2 | Verificare che le soglie del rilevatore siano tarate su set di validazione puliti/avvelenati per ottenere meno del 5% di falsi positivi.           |    1    |   V   |
| 10.6.3 | Verifica che gli input etichettati come avvelenati attivino il blocco morbido e i flussi di lavoro di revisione umana.                             |    2    |   D   |
| 10.6.4 | Verifica che i rilevatori siano sottoposti a test di stress con attacchi backdoor adattivi senza trigger.                                          |    2    |   V   |
| 10.6.5 | Verifica che le metriche di efficacia della rilevazione siano registrate e rivalutate periodicamente utilizzando nuove informazioni sulle minacce. |    3    |   D   |

---

## 10.7 Adattamento dinamico della politica di sicurezza

Aggiornamenti in tempo reale delle politiche di sicurezza basati su informazioni sulle minacce e analisi comportamentale.

|   #    | Descrizione                                                                                                                                                                            | Livello | Ruolo |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 10.7.1 | Verifica che le policy di sicurezza possano essere aggiornate dinamicamente senza riavviare l'agente, mantenendo l'integrità della versione della policy di sicurezza.                 |    1    |  D/V  |
| 10.7.2 | Verifica che gli aggiornamenti delle politiche siano firmati digitalmente da personale di sicurezza autorizzato e validati prima dell'applicazione.                                    |    2    |  D/V  |
| 10.7.3 | Verificare che le modifiche dinamiche delle politiche siano registrate con tracce complete di audit, tra cui la giustificazione, le catene di approvazione e le procedure di rollback. |    2    |  D/V  |
| 10.7.4 | Verificare che i meccanismi di sicurezza adattivi adattino la sensibilità del rilevamento delle minacce in base al contesto di rischio e ai modelli comportamentali.                   |    3    |  D/V  |
| 10.7.5 | Verifica che le decisioni di adattamento delle politiche siano spiegabili e includano tracce di evidenza per la revisione da parte del team di sicurezza.                              |    3    |  D/V  |

---

## 10.8 Analisi della sicurezza basata sulla riflessione

Verifica della sicurezza tramite autovalutazione dell'agente e analisi metacognitiva.

|   #    | Descrizione                                                                                                                                                  | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 10.8.1 | Verifica che i meccanismi di riflessione degli agenti includano un'autovalutazione orientata alla sicurezza delle decisioni e delle azioni.                  |    1    |  D/V  |
| 10.8.2 | Verificare che gli output della riflessione siano validati per prevenire la manipolazione dei meccanismi di autovalutazione da parte di input ostili.        |    2    |  D/V  |
| 10.8.3 | Verifica che l'analisi di sicurezza metacognitiva identifichi potenziali bias, manipolazione o compromissione nei processi di ragionamento dell'agente.      |    2    |  D/V  |
| 10.8.4 | Verifichi che gli avvisi di sicurezza basati sulla riflessione attivino un monitoraggio avanzato e potenziali flussi di intervento umano.                    |    3    |  D/V  |
| 10.8.5 | Verifica che l'apprendimento continuo dalle riflessioni sulla sicurezza migliori il rilevamento delle minacce senza compromettere la funzionalità legittima. |    3    |  D/V  |

---

## 10.9 Evoluzione e Sicurezza dell'Auto-miglioramento

Controlli di sicurezza per sistemi agenti in grado di auto-modificarsi ed evolversi.

|   #    | Descrizione                                                                                                                                | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 10.9.1 | Verificare che le capacità di auto-modifica siano limitate alle aree designate sicure con confini di verifica formali.                     |    1    |  D/V  |
| 10.9.2 | Verificare che le proposte di evoluzione siano sottoposte a una valutazione dell'impatto sulla sicurezza prima dell'implementazione.       |    2    |  D/V  |
| 10.9.3 | Verifica che i meccanismi di auto-miglioramento includano capacità di rollback con verifica dell'integrità.                                |    2    |  D/V  |
| 10.9.4 | Verifica che la sicurezza del meta-apprendimento impedisca la manipolazione avversaria degli algoritmi di miglioramento.                   |    3    |  D/V  |
| 10.9.5 | Verifica che l'auto-miglioramento ricorsivo sia limitato dai vincoli di sicurezza formali con dimostrazioni matematiche della convergenza. |    3    |  D/V  |

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

