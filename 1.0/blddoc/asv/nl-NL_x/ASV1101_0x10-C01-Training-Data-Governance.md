# C1 Traininggegevensbeheer & Beheer van vooringenomenheid

## Beheersingsdoelstelling

Trainingsgegevens moeten worden verkregen, behandeld en onderhouden op een manier die de herkomst, beveiliging, kwaliteit en eerlijkheid waarborgt. Dit vervult juridische verplichtingen en vermindert de risico's van vooringenomenheid, vergiftiging of privacyinbreuken die tijdens het trainen naar voren kunnen komen en de gehele AI-levenscyclus kunnen beïnvloeden.

---

## C1.1 Herkomst van trainingsgegevens

Houd een verifieerbare inventaris bij van alle datasets, accepteer alleen vertrouwde bronnen en registreer elke wijziging voor auditbaarheid.

|   #   | Beschrijving                                                                                                                                                                                                      | Niveau | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 1.1.1 | Verifieer dat een up-to-date inventaris van elke trainingsgegevensbron (oorsprong, beheerder/eigenaar, licentie, verzamelmethode, beperkingen voor bedoeld gebruik en verwerkingsgeschiedenis) wordt bijgehouden. |   1    | D/V |
| 1.1.2 | Controleer of de trainingsdataprocessen onnodige kenmerken, attributen of velden uitsluiten (bijvoorbeeld ongebruikte metadata, gevoelige PII, gelekte testgegevens).                                             |   1    | D/V |
| 1.1.3 | Verifieer dat alle wijzigingen in de dataset onderhevig zijn aan een goedgekeurd en gelogd workflowproces.                                                                                                        |   2    | D/V |
| 1.1.4 | Controleer of datasets of subsets waar mogelijk zijn voorzien van een watermerk of fingerprint.                                                                                                                   |   3    | D/V |

---

## C1.2 Beveiliging en integriteit van trainingsgegevens

Beperk de toegang tot trainingsgegevens, versleutel deze wanneer ze opgeslagen zijn en tijdens overdracht, en valideer de integriteit om manipulatie, diefstal of datavervuiling te voorkomen.

|   #   | Beschrijving                                                                                                                                                                                              | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 1.2.1 | Controleer of toegangscontroles de opslag van trainingsgegevens en pijplijnen beschermen.                                                                                                                 |   1    | D/V |
| 1.2.2 | Controleer of alle toegang tot trainingsgegevens wordt geregistreerd, inclusief gebruiker, tijd en actie.                                                                                                 |   2    | D/V |
| 1.2.3 | Verifieer dat trainingsdatasets zowel tijdens het transport als in opslag versleuteld zijn, met gebruikmaking van cryptografische algoritmen en sleutelbeheerpraktijken volgens industriestandaarden.     |   2    | D/V |
| 1.2.4 | Controleer of cryptografische hashes of digitale handtekeningen worden gebruikt om de gegevensintegriteit tijdens het opslaan en overdragen van trainingsgegevens te waarborgen.                          |   2    | D/V |
| 1.2.5 | Verifieer dat geautomatiseerde detectietechnieken worden toegepast om te beschermen tegen ongeautoriseerde wijzigingen of corruptie van trainingsgegevens.                                                |   2    | D/V |
| 1.2.6 | Controleer of verouderde trainingsgegevens veilig worden verwijderd of geanonimiseerd.                                                                                                                    |   2    | D/V |
| 1.2.7 | Controleer of alle versies van de trainingsdataset uniek zijn geïdentificeerd, onveranderlijk zijn opgeslagen en controleerbaar zijn om ondersteuning te bieden voor terugdraaien en forensische analyse. |   3    | D/V |

---

## C1.3 Trainingsgegevens Labelkwaliteits-, Integriteits- en Beveiliging

Bescherm labels en vereis technische beoordeling voor kritieke gegevens.

|   #   | Beschrijving                                                                                                                                                                                                     | Niveau | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 1.3.1 | Controleer of cryptografische hashwaarden of digitale handtekeningen worden toegepast op label-artifacten om hun integriteit en authenticiteit te waarborgen.                                                    |   2    | D/V |
| 1.3.2 | Controleer of labeling-interfaces en -platforms sterke toegangscontroles afdwingen, tamper-evidente auditlogs van alle labeling-activiteiten bijhouden en bescherming bieden tegen ongeautoriseerde wijzigingen. |   2    | D/V |
| 1.3.3 | Controleer of gevoelige informatie in labels wordt weggelaten, geanonimiseerd of versleuteld op het niveau van gegevensvelden, zowel in rust als tijdens overdracht.                                             |   3    | D/V |

---

## C1.4 Kwaliteit van trainingsgegevens en borging van beveiliging

Combineer geautomatiseerde validatie, handmatige steekproeven en geregistreerde correcties om de betrouwbaarheid van de dataset te waarborgen.

|   #   | Beschrijving                                                                                                                                                                                                                                                                                                                                                                                                                                            | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 1.4.1 | Controleer of geautomatiseerde tests formaatfouten en null-waarden opvangen bij elke invoer of significante datatransformatie.                                                                                                                                                                                                                                                                                                                          |   1    |  D  |
| 1.4.2 | Controleer of LLM-trainings- en fijnstemmingspijplijnen het detecteren van vergiftiging en de validatie van gegevensintegriteit implementeren (bijv. statistische methoden, detectie van uitschieters, embedding-analyse) om mogelijke vergiftigingsaanvallen (bijv. labelomkering, invoeging van achterdeurtje-triggers, rolwisselcommando's, invloedrijke instantie-aanvallen) of onbedoelde gegevenscorruptie in trainingsgegevens te identificeren. |   2    | D/V |
| 1.4.3 | Verifieer dat passende verdedigingsmaatregelen, zoals adversarial training (met gegenereerde adversarial voorbeelden), data-augmentatie met gewijzigde invoerdata, of robuuste optimalisatietechnieken, zijn geïmplementeerd en afgestemd voor relevante modellen op basis van risicobeoordeling.                                                                                                                                                       |   3    | D/V |
| 1.4.4 | Verifieer dat automatisch gegenereerde labels (bijvoorbeeld via LLM's of zwakke supervisie) onderworpen zijn aan betrouwbaarheidsdrempels en consistentiecontroles om gehallucineerde, misleidende of labels met lage betrouwbaarheid te detecteren.                                                                                                                                                                                                    |   2    | D/V |
| 1.4.5 | Controleer of geautomatiseerde tests labelverschuivingen detecteren bij elke ingestie of significante datatransformatie.                                                                                                                                                                                                                                                                                                                                |   3    |  D  |

---

## C1.5 Gegevensafstamming en Traceerbaarheid

Volg de volledige reis van elk datapunt van bron tot modelinvoer voor controleerbaarheid en incidentrespons.

|   #   | Beschrijving                                                                                                                                                                                                                                                 | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 1.5.1 | Controleer of de herkomst van elk gegevenspunt, inclusief alle transformaties, augmentaties en samenvoegingen, is vastgelegd en kan worden gereconstrueerd.                                                                                                  |   2    | D/V |
| 1.5.2 | Controleer of stamboekrecords onveranderlijk, veilig opgeslagen en toegankelijk zijn voor audits.                                                                                                                                                            |   2    | D/V |
| 1.5.3 | Controleer of de herkomstregistratie synthetic data dekt die is gegenereerd via privacybeschermende of generatieve technieken en zorg ervoor dat alle synthetic data duidelijk is gelabeld en te onderscheiden is van echte data gedurende de hele pijplijn. |   2    | D/V |

---

## Referenties

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [EU AI Act – Article 10: Data & Data Governance](https://artificialintelligenceact.eu/article/10/)
* [MITRE ATLAS: Adversary Tactics for AI](https://atlas.mitre.org/)
* [Survey of ML Bias Mitigation Techniques – MDPI](https://www.mdpi.com/2673-6470/4/1/1)
* [Data Provenance & Lineage Best Practices – Nightfall AI](https://www.nightfall.ai/ai-security-101/data-provenance-and-lineage)
* [Data Labeling Quality Standards – LabelYourData](https://labelyourdata.com/articles/data-labeling-quality-and-how-to-measure-it)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [CISA Advisory: Securing Data for AI Systems](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [ISO/IEC 23053: AI Management Systems Framework](https://www.iso.org/sectors/it-technologies/ai)
* [IBM: What is AI Governance?](https://www.ibm.com/think/topics/ai-governance)
* [Google AI Principles](https://ai.google/principles/)
* [GDPR & AI Training Data – DataProtectionReport](https://www.dataprotectionreport.com/2024/08/recent-regulatory-developments-in-training-artificial-intelligence-ai-models-under-the-gdpr/)
* [Supply-Chain Security for AI Data – AppSOC](https://www.appsoc.com/blog/ai-is-the-new-frontier-of-supply-chain-security)
* [OpenAI Privacy Center – Data Deletion Controls](https://privacy.openai.com/policies?modal=take-control)
* [Adversarial ML Dataset – Kaggle](https://www.kaggle.com/datasets/cnrieiit/adversarial-machine-learning-dataset)

