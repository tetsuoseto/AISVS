# 11 Privacybescherming & Beheer van Persoonlijke Gegevens

## Beheersdoel

Handhaaf strikte privacywaarborgen gedurende de volledige AI-levenscyclus—verzameling, training, inferentie en incidentrespons—zodat persoonlijke gegevens uitsluitend worden verwerkt met duidelijke toestemming, de minimale noodzakelijke reikwijdte, aantoonbaar wissen, en formele privacygaranties.

---

## 11.1 Anonimisatie & Gegevensminimalisatie

|   #    | Beschrijving                                                                                                                                               | Niveau | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 11.1.1 | Verifieer dat directe en quasi-identificatoren zijn verwijderd en gehasht.                                                                                 |   1    | D/V |
| 11.1.2 | Verifieer dat geautomatiseerde audits k-anonimiteit/l-diversiteit meten en waarschuwen wanneer drempels onder het beleid dalen.                            |   2    | D/V |
| 11.1.3 | Verifieer dat de rapporten over de feature-belangrijkheid van het model geen identificatorlekken aantonen die groter zijn dan ε = 0.01 mutual information. |   2    |  V  |
| 11.1.4 | Verifieer dat formele bewijzen of certificering van synthetische data aantonen dat het re-identificatierisico ≤ 0.05 zelfs onder linkage-aanvallen.        |   3    |  V  |

---

## 11.2 Recht op vergetelheid en verwijderingshandhaving

|   #    | Beschrijving                                                                                                                                                                                            | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 11.2.1 | Controleer of verwijderingsverzoeken van betrokkene zich verspreiden naar ruwe datasets, checkpoints, embeddings, logs en back-ups binnen serviceniveau-overeenkomsten die minder dan 30 dagen beslaan. |   1    | D/V |
| 11.2.2 | Verifieer dat 'machine-unlearning'-routines fysiek opnieuw trainen of de verwijdering nabootsen met behulp van gecertificeerde unlearning-algoritmen.                                                   |   2    |  D  |
| 11.2.3 | Controleer dat de evaluatie van het schaduwmodel aantoont dat vergeten records minder dan 1% van de uitvoer beïnvloeden na het onleren.                                                                 |   2    |  V  |
| 11.2.4 | Verifieer dat verwijderingsgebeurtenissen onveranderlijk gelogd en auditbaar zijn voor toezichthouders.                                                                                                 |   3    |  V  |

---

## 11.3 Differentiële privacy-waarborgen

|   #    | Beschrijving                                                                                                                   | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 11.3.1 | Verifieer dat dashboards voor privacyverlies-boekhouding waarschuwen wanneer de cumulatieve ε de beleidsdrempels overschrijdt. |   2    | D/V |
| 11.3.2 | Controleer of ε̂ door black-box privacy-audits binnen 10% van de opgegeven waarde wordt geschat.                               |   2    |  V  |
| 11.3.3 | Verifieer dat formele bewijzen alle post-training finetunes en embeddings dekken.                                              |   3    |  V  |

---

## 11.4 Doelbeperking & Scope-uitbreiding Bescherming

|   #    | Beschrijving                                                                                                                                            | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 11.4.1 | Verifieer dat elke dataset en elk model-checkpoint een machineleesbare doel-tag draagt die is afgestemd op de oorspronkelijke toestemming.              |   1    |  D  |
| 11.4.2 | Controleer of runtime-monitoren query's detecteren die niet in overeenstemming zijn met het opgegeven doel en een zachte weigering activeren.           |   1    | D/V |
| 11.4.3 | Controleer of beleid-als-code-controles de herdeployering van modellen naar nieuwe domeinen blokkeren zonder DPIA-beoordeling.                          |   3    |  D  |
| 11.4.4 | Verifieer dat formele traceerbaarheidsbewijzen aantonen dat elke fase van de levenscyclus van persoonsgegevens binnen de toegestemde reikwijdte blijft. |   3    |  V  |

---

## 11.5 Toestemmingsbeheer & Tracking op basis van rechtsgrondslag

|   #    | Beschrijving                                                                                                                     | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 11.5.1 | Controleer of een Toestemmingsbeheerplatform (CMP) de opt-in-status, het doel en de bewaartermijn per betrokkene registreert.    |   1    | D/V |
| 11.5.2 | Controleer of API's toestemmingstokens blootleggen; modellen moeten het bereik van toestemmingstokens valideren vóór inferentie. |   2    |  D  |
| 11.5.3 | Controleer of geweigerde of ingetrokken toestemming de verwerkingspijplijnen binnen 24 uur stopt.                                |   2    | D/V |

---

## 11.6 Federated Learning met privacycontroles

|   #    | Beschrijving                                                                                                                  | Niveau | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 11.6.1 | Controleer of de updates van cliënten lokale differentiële privacy-ruis toevoegen vóór aggregatie.                            |   1    |  D  |
| 11.6.2 | Verifieer of de trainingsmetingen onder de differentiële privacy vallen en nooit het verlies van een enkele cliënt onthullen. |   2    | D/V |
| 11.6.3 | Controleer of poisoning-bestendige aggregatie (bijv. Krum/Trimmed-Mean) is ingeschakeld.                                      |   2    |  V  |
| 11.6.4 | Verifieer dat formele bewijzen aantonen dat het totale ε-budget minder dan 5 nutverlies oplevert.                             |   3    |  V  |

---

### Referenties

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

