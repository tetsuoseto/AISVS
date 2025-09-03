# 11 Protezione della privacy e gestione dei dati personali

## Obiettivo di controllo

Mantieni garanzie di privacy rigorose per l'intero ciclo di vita dell'IA—raccolta, addestramento, inferenza e gestione degli incidenti—in modo che i dati personali siano trattati solo con consenso chiaro, ambito minimo necessario, cancellazione dimostrabile e garanzie formali sulla privacy.

---

## 11.1 Anonimizzazione e minimizzazione dei dati

|   #    | Descrizione                                                                                                                                                                            | Livello | Ruolo |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 11.1.1 | Verifica che gli identificatori diretti e i quasi-identificatori siano rimossi e hashati.                                                                                              |    1    |  D/V  |
| 11.1.2 | Verificare che le verifiche automatizzate misurino k-anonimato/l-diversità e avvisino quando le soglie scendono al di sotto della policy.                                              |    2    |  D/V  |
| 11.1.3 | Verifichi che i report sull'importanza delle feature del modello dimostrino che non vi è alcuna fuga di identificatori oltre ε = 0.01 di informazione mutua.                           |    2    |   V   |
| 11.1.4 | Verifichi che le dimostrazioni formali o la certificazione dei dati sintetici mostrino un rischio di ri-identificazione ≤ 0.05 anche in presenza di attacchi di collegamento dei dati. |    3    |   V   |

---

## 11.2 Diritto all'oblio e all'attuazione della cancellazione

|   #    | Descrizione                                                                                                                                                                                           | Livello | Ruolo |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 11.2.1 | Verifica che le richieste di cancellazione dei dati del soggetto si propaghino a dataset grezzi, checkpoint, embedding, log e backup entro gli accordi sul livello di servizio inferiori a 30 giorni. |    1    |  D/V  |
| 11.2.2 | Verifica che le routine di "machine-unlearning" riaddestrino fisicamente o approssimino la rimozione utilizzando algoritmi certificati di disimparazione.                                             |    2    |   D   |
| 11.2.3 | Verifica che la valutazione del modello-ombra dimostri che i record dimenticati influenzano meno del 1% degli output dopo l'unlearning.                                                               |    2    |   V   |
| 11.2.4 | Verificare che gli eventi di cancellazione siano registrati in modo immutabile e auditabili per le autorità di regolamentazione.                                                                      |    3    |   V   |

---

## 11.3 Differential-Privacy Salvaguardie

|   #    | Descrizione                                                                                                                             | Livello | Ruolo |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 11.3.1 | Verifica che i cruscotti di rendicontazione della perdita di privacy emettano avvisi quando ε cumulativo supera le soglie della policy. |    2    |  D/V  |
| 11.3.2 | Verifica che le verifiche di privacy a scatola nera stimino ε̂ entro il 10% del valore dichiarato.                                      |    2    |   V   |
| 11.3.3 | Verifica che le prove formali coprano tutti i processi di fine-tuning post-addestramento e le rappresentazioni di embedding.            |    3    |   V   |

---

## 11.4 Limitazione dello scopo e protezione contro l'espansione dell'ambito

|   #    | Descrizione                                                                                                                               | Livello | Ruolo |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 11.4.1 | Verifica che ogni dataset e ogni checkpoint del modello abbiano etichette di scopo leggibili da macchina allineate al consenso originale. |    1    |   D   |
| 11.4.2 | Verifica che i monitor di esecuzione rilevino richieste non allineate con lo scopo dichiarato e attivino un rifiuto morbido.              |    1    |  D/V  |
| 11.4.3 | Verifica che i controlli basati su policy-as-code blocchino la ridistribuzione dei modelli verso nuovi domini senza una revisione DPIA.   |    3    |   D   |
| 11.4.4 | Verificare che le prove di tracciabilità formale dimostrino che ogni ciclo di vita dei dati personali rimanga entro l'ambito consentito.  |    3    |   V   |

---

## 11.5 Gestione del consenso e tracciamento della base-giuridica

|   #    | Descrizione                                                                                                                                                             | Livello | Ruolo |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 11.5.1 | Verifica che una Piattaforma di Gestione del Consenso (CMP) registri lo stato di consenso esplicito, le finalità e il periodo di conservazione per ciascun interessato. |    1    |  D/V  |
| 11.5.2 | Verifica che le API espongano token di consenso; i modelli devono validare l'ambito del token prima dell'inferenza.                                                     |    2    |   D   |
| 11.5.3 | Verifica che il consenso negato o revocato interrompa le pipeline di elaborazione entro 24 ore.                                                                         |    2    |  D/V  |

---

## 11.6 Apprendimento Federato con Controlli della Privacy

|   #    | Descrizione                                                                                                                                 | Livello | Ruolo |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 11.6.1 | Verifica che gli aggiornamenti dei client utilizzino l'aggiunta di rumore di privacy differenziale locale prima dell'aggregazione.          |    1    |   D   |
| 11.6.2 | Verifica che le metriche di addestramento siano protette tramite privacy differenziale e non rivelino mai la perdita di un singolo cliente. |    2    |  D/V  |
| 11.6.3 | Verifica che l'aggregazione resistente all'avvelenamento (ad es., Krum/Trimmed-Mean) sia abilitata.                                         |    2    |   V   |
| 11.6.4 | Verifica che le prove formali dimostrino un budget ε complessivo con una perdita di utilità inferiore a 5.                                  |    3    |   V   |

---

### Riferimenti

* [GDPR & AI Compliance Best Practices](https://www.exabeam.com/explainers/gdpr-compliance/the-intersection-of-gdpr-and-ai-and-6-compliance-best-practices/)
* [EU Parliament Study on GDPR & AI, 2020](https://www.europarl.europa.eu/RegData/etudes/STUD/2020/641530/EPRS_STU%282020%29641530_EN.pdf)
* [ISO 31700-1:2023 — Privacy by Design for Consumer Products](https://www.iso.org/standard/84977.html)
* [NIST Privacy Framework 1.1 (2025 Draft)](https://www.nist.gov/privacy-framework)
* [Machine Unlearning: Right-to-Be-Forgotten Techniques](https://www.kaggle.com/code/tamlhp/machine-unlearning-the-right-to-be-forgotten)
* [A Survey of Machine Unlearning, 2024](https://arxiv.org/html/2209.02299v6)
* [Auditing DP-SGD — ArXiv 2024](https://arxiv.org/html/2405.14106v4)
* [DP-SGD Explained — PyTorch Blog](https://medium.com/pytorch/differential-privacy-series-part-1-dp-sgd-algorithm-explained-12512c3959a3)
* [Purpose-Limitation for AI — IJLIT 2025](https://academic.oup.com/ijlit/article/doi/10.1093/ijlit/eaaf003/8121663)
* [Data-Protection Considerations for AI — URM Consulting](https://www.urmconsulting.com/blog/data-protection-considerations-for-artificial-intelligence-ai)
* [Top Consent-Management Platforms, 2025](https://www.enzuzo.com/blog/best-consent-management-platforms)
* [Secure Aggregation in DP Federated Learning — ArXiv 2024](https://arxiv.org/abs/2407.19286)

