# C1 Trainingsgegevens Governance & Biasbeheer

## Beheersdoel

Trainingsdata moeten op een manier worden verkregen, behandeld en onderhouden die provenance, veiligheid, kwaliteit en eerlijkheid waarborgt. Dit voldoet aan wettelijke verplichtingen en vermindert risico's op bias, datavervalsing of privacy-inbreuken die tijdens de training voorkomen en die de gehele AI-levenscyclus kunnen beïnvloeden.

---

## C1.1 Oorsprong van trainingsdata

Onderhoud een verifieerbare inventaris van alle datasets, accepteer uitsluitend betrouwbare bronnen en registreer elke wijziging voor auditbaarheid.

|   #   | Beschrijving                                                                                                                                                                                                       | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 1.1.1 | Controleer of een actuele inventaris van elke trainingsdata-bron (herkomst, beheerder/eigenaar, licentie, verzamelingsmethode, beperkingen voor het beoogde gebruik en verwerkingsgeschiedenis) wordt onderhouden. |   1    | D/V |
| 1.1.2 | Verifieer dat trainingsdata-processen onnodige kenmerken, attributen of velden uitsluiten (bijv. ongebruikte metadata, gevoelige PII, gelekte testgegevens).                                                       |   1    | D/V |
| 1.1.3 | Controleer of alle datasetwijzigingen onderworpen zijn aan een gelogd goedkeuringsproces.                                                                                                                          |   2    | D/V |
| 1.1.4 | Verifieer of datasets of subsets waar mogelijk watermerken bevatten of vingerafdrukken hebben.                                                                                                                     |   3    | D/V |

---

## C1.2 Trainingsgegevens Beveiliging & Integriteit

Beperk de toegang tot trainingsgegevens, versleutel deze zowel in rusttoestand als tijdens verzending, en valideer de integriteit ervan om manipulatie, diefstal of data-poisoning te voorkomen.

|   #   | Beschrijving                                                                                                                                                                            | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 1.2.1 | Verifieer dat toegangscontroles de opslag van trainingsdata en datapijplijnen beschermen.                                                                                               |   1    | D/V |
| 1.2.2 | Controleer of alle toegang tot trainingsdata gelogd is, inclusief gebruiker, tijd en actie.                                                                                             |   2    | D/V |
| 1.2.3 | Verifieer dat trainingsdatasets tijdens overdracht en in rust zijn versleuteld, met behulp van cryptografische algoritmen volgens industrienormen en praktijken voor sleutelbeheer.     |   2    | D/V |
| 1.2.4 | Verifieer of cryptografische hashwaarden of digitale handtekeningen worden gebruikt om de integriteit van gegevens te waarborgen tijdens de opslag en overdracht van trainingsgegevens. |   2    | D/V |
| 1.2.5 | Controleer of geautomatiseerde detectietechnieken worden toegepast om ongeautoriseerde wijzigingen of corruptie van trainingsgegevens te voorkomen.                                     |   2    | D/V |
| 1.2.6 | Controleer of verouderde trainingsgegevens veilig zijn gewist of geanonimiseerd.                                                                                                        |   2    | D/V |
| 1.2.7 | Verifieer dat alle versies van trainingsdatasets uniek geïdentificeerd zijn, onveranderlijk opgeslagen zijn en auditbaar zijn om rollback en forensische analyse mogelijk te maken.     |   3    | D/V |

---

## C1.3 Labelen van trainingsdata: Kwaliteit, Integriteit en Beveiliging

Bescherm labels en eis een technische beoordeling voor kritische gegevens.

|   #   | Beschrijving                                                                                                                                                                                                           | Niveau | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 1.3.1 | Controleer of cryptografische hashes of digitale handtekeningen op labelartefacten zijn toegepast om hun integriteit en authenticiteit te waarborgen.                                                                  |   2    | D/V |
| 1.3.2 | Controleer of etiketterings-interfaces en platformen sterke toegangscontroles afdwingen, alle etiketterings-activiteiten bijhouden in tamper-evidente auditlogboeken en beschermen tegen ongeautoriseerde wijzigingen. |   2    | D/V |
| 1.3.3 | Controleer of gevoelige informatie in labels op veldniveau is geredigeerd, geanonimiseerd of versleuteld, zowel in rust als tijdens verzending.                                                                        |   3    | D/V |

---

## C1.4 Kwaliteit van trainingsgegevens en beveiligingswaarborging

Combineer geautomatiseerde validatie, handmatige steekproefscontroles en gelogde herstelmaatregelen om de betrouwbaarheid van de dataset te waarborgen.

|   #   | Beschrijving                                                                                                                                                                                                                                                                                                                                                                                                   | Niveau | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 1.4.1 | Controleer of geautomatiseerde tests formaatfouten en nullwaarden opvangen bij elke gegevensinname of significante gegevenstransformatie.                                                                                                                                                                                                                                                                      |   1    |  D  |
| 1.4.2 | Controleer of de LLM-trainings- en fijnafstemmingspijplijnen poisoning-detectie en data-integriteitsvalidatie implementeren (bijv. statistische methoden, uitbijterdetectie, embedding-analyse) om potentiële poisoning-aanvallen (bijv. label-flipping, backdoor-triggerinvoer, rolwisselingscommando's, invloedrijke exemplaar-aanvallen) of onbedoelde datacorruptie in trainingsgegevens te identificeren. |   2    | D/V |
| 1.4.3 | Verifieer dat passende verdedigingen, zoals adversarial training (met gegenereerde adversariale voorbeelden), data-augmentatie met verstoorde invoer, of robuuste optimalisatietechnieken, zijn geïmplementeerd en afgestemd voor relevante modellen op basis van een risicobeoordeling.                                                                                                                       |   3    | D/V |
| 1.4.4 | Verifieer dat automatisch gegenereerde labels (bijv. via LLMs of zwakke supervisie) onderworpen zijn aan betrouwbaarheidsdrempels en controles op consistentie om hallucinatoire labels, misleidende labels of labels met lage betrouwbaarheid te detecteren.                                                                                                                                                  |   2    | D/V |
| 1.4.5 | Controleer of geautomatiseerde tests labelverschuivingen opvangen bij elke inlezing van data of bij een significante datatransformatie.                                                                                                                                                                                                                                                                        |   3    |  D  |

---

## C1.5 Gegevensafstamming en traceerbaarheid

Volg de volledige reis van elk gegevenspunt van de bron tot de modelinvoer voor auditbaarheid en incidentrespons.

|   #   | Beschrijving                                                                                                                                                                                                                                                                         | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 1.5.1 | Verifieer dat de herkomst van elk datapunt, inclusief alle transformaties, augmentaties en samenvoegingen, is vastgelegd en kan worden gereconstrueerd.                                                                                                                              |   2    | D/V |
| 1.5.2 | Verifieer dat de lineage-registraties onveranderlijk zijn, veilig opgeslagen en toegankelijk voor audits.                                                                                                                                                                            |   2    | D/V |
| 1.5.3 | Verifieer dat de data-lineage (afstammings-traceerbaarheid) synthetische gegevens die zijn gegenereerd via privacybeschermende of generatieve technieken dekt, en dat alle synthetische gegevens in de hele pipeline duidelijk gelabeld en te onderscheiden zijn van echte gegevens. |   2    | D/V |

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

