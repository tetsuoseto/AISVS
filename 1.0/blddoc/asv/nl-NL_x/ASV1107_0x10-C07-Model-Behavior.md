# C7 Modelgedrag, Uitvoercontrole & Veiligheidsborging

## Beheersdoel

Modeluitvoer moet gestructureerd, betrouwbaar, veilig, uitlegbaar en continu bewaakt in productie zijn. Dit vermindert hallucinaties, privacylekken, schadelijke inhoud en uit de hand lopende acties, terwijl het het vertrouwen van gebruikers vergroot en de naleving van regelgeving bevordert.

---

## C7.1 Handhouding van het uitvoerformaat

Strikte schema's, afgebakende decodering en downstream-validatie voorkomen dat misvormde of kwaadaardige inhoud zich verspreidt.

|   #   | Beschrijving                                                                                                                                                                                  | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.1.1 | Controleer of antwoordschema's (bijv. JSON Schema) in de systeemprompt zijn opgenomen en of elke uitvoer automatisch wordt gevalideerd; niet-conforme uitvoer leidt tot herstel of afwijzing. |   1    | D/V |
| 7.1.2 | Controleer of beperkte decodering (stoptekens, regex, max-tokens) is ingeschakeld om overflow of prompt-injectie side-kanalen te voorkomen.                                                   |   1    | D/V |
| 7.1.3 | Controleer dat downstream-componenten de uitvoer als onbetrouwbaar beschouwen en deze valideren tegen schema's of injectie-veilige deserialisatoren.                                          |   2    | D/V |
| 7.1.4 | Controleer of onjuiste uitvoergebeurtenissen gelogd worden, rate-limited zijn en aan de monitoring worden weergegeven.                                                                        |   3    |  V  |

---

## C7.2 Hallucinatie-detectie en Mitigatie

Onzekerheidsinschatting en terugvalstrategieën beperken verzonnen antwoorden.

|   #   | Beschrijving                                                                                                                                                                             | Niveau | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.2.1 | Verifieer dat token-niveau log-waarschijnlijkheden, ensemble-zelfconsistentie en fijn afgestelde hallucinatie-detectoren aan elk antwoord een vertrouwensscore toekennen.                |   1    | D/V |
| 7.2.2 | Verifieer of reacties onder een configureerbare betrouwbaarheidsdrempel fallback-workflows activeren (bijv. retrieval-augmented generation, secondary model, of menselijke beoordeling). |   1    | D/V |
| 7.2.3 | Controleer of hallucinatie-incidenten zijn gelabeld met hoofdoorzaak-metadata en doorgegeven aan post-mortem en finetuning-pijplijnen.                                                   |   2    | D/V |
| 7.2.4 | Controleer of de drempels en detectoren na grote model- en kennisbankupdates opnieuw gekalibreerd worden.                                                                                |   3    | D/V |
| 7.2.5 | Controleer of dashboardvisualisaties de hallucinatiepercentages bijhouden.                                                                                                               |   3    |  V  |

---

## C7.3 Uitvoerveiligheid & privacyfiltrering

Beleidsfilters en red-team-dekking beschermen gebruikers en vertrouwelijke gegevens.

|   #   | Beschrijving                                                                                                                                                                                      | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.3.1 | Verifieer dat voor- en post-generatie-classificatiemodellen inhoud die haat, intimidatie, zelfbeschadiging, extremisme en seksueel expliciete inhoud blokkeren in overeenstemming met het beleid. |   1    | D/V |
| 7.3.2 | Controleer of PII/PCI-detectie en automatische redactie bij elke reactie worden uitgevoerd; overtredingen leiden tot een privacy-incident.                                                        |   1    | D/V |
| 7.3.3 | Controleer of vertrouwelijkheidslabels (bijv. bedrijfsgeheimen) zich verspreiden over modaliteiten om lekkage in tekst, afbeeldingen of code te voorkomen.                                        |   2    |  D  |
| 7.3.4 | Controleer of pogingen tot omzeiling van filters of classificaties met een hoog risico een tweede goedkeuring of her-authenticatie door de gebruiker vereisen.                                    |   3    | D/V |
| 7.3.5 | Verifieer dat de filterdrempels rekening houden met de wettelijke rechtsgebieden en met de context van de leeftijd/rol van de gebruiker.                                                          |   3    | D/V |

---

## C7.4 Uitvoer en Actiebeperking

Ratelimieten en goedkeuringspoorten voorkomen misbruik en overmatige autonomie.

|   #   | Beschrijving                                                                                                                                                                                                 | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 7.4.1 | Verifieer of de quota's per-gebruiker en per-API-sleutel het aantal verzoeken, tokens en kosten beperken, met exponentiële back-off bij 429-fouten.                                                          |   1    |  D  |
| 7.4.2 | Controleer of bevoorrechte acties (bestandsschrijven, code-uitvoering, netwerkoproepen) een goedkeuringsproces op basis van beleid of menselijke tussenkomst vereisen.                                       |   1    | D/V |
| 7.4.3 | Controleer dat crossmodale consistentiecontroles ervoor zorgen dat afbeeldingen, code en tekst die voor hetzelfde verzoek zijn gegenereerd, niet kunnen worden gebruikt om kwaadaardige inhoud te smokkelen. |   2    | D/V |
| 7.4.4 | Verifieer dat de diepte van agentendelegatie, recursielimieten en toegestane hulpmiddelenlijsten expliciet zijn geconfigureerd.                                                                              |   2    |  D  |
| 7.4.5 | Verifieer dat overtreding van limieten gestructureerde beveiligingsgebeurtenissen genereert voor SIEM-ingestie.                                                                                              |   3    |  V  |

---

## C7.5 Uitvoer Uitlegbaarheid

Transparante signalen vergroten het gebruikersvertrouwen en de interne foutopsporing.

|   #   | Beschrijving                                                                                                                                                     | Niveau | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.5.1 | Verifieer of aan de gebruiker getoonde vertrouwensscores of beknopte redeneringssamenvattingen worden weergegeven wanneer de risicobeoordeling dit passend acht. |   2    | D/V |
| 7.5.2 | Controleer of gegenereerde verklaringen geen gevoelige systeemprompts of bedrijfseigen gegevens prijsgeven.                                                      |   2    | D/V |
| 7.5.3 | Zorg ervoor dat het systeem token-niveau log-probabiliteiten of aandachtkaarten vastlegt en deze opslaat voor geautoriseerde inspectie.                          |   3    |  D  |
| 7.5.4 | Controleer of verklaarbaarheidsartefacten onder versiebeheer staan naast modelreleases voor auditabiliteit.                                                      |   3    |  V  |

---

## C7.6 Monitoring-integratie

Observability in realtime sluit de lus tussen ontwikkeling en productie.

|   #   | Beschrijving                                                                                                                                                       | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 7.6.1 | Controleer of de metriek(en) (schema-overtredingen, hallucinatiepercentage, toxiciteit, PII-lekken, latentie, kosten) naar een centraal bewakingsplatform stromen. |   1    |  D  |
| 7.6.2 | Verifieer dat voor elke veiligheidsmetriek waarschuwingsdrempels zijn gedefinieerd, met escalatiepaden voor de dienstdoende operationele staf.                     |   1    |  V  |
| 7.6.3 | Verifieer dat dashboards uitvoerafwijkingen correleren met model/versie, feature-vlag, en upstream-gegevenswijzigingen.                                            |   2    |  V  |
| 7.6.4 | Verifieer of monitoringgegevens terugkoppelen naar retraining, fine-tuning of regelupdates binnen een gedocumenteerde MLOps-workflow mogelijk is.                  |   2    | D/V |
| 7.6.5 | Verifieer dat monitoringpijplijnen aan penetratietests zijn onderworpen en onder toegangscontrole staan om lekken van gevoelige logbestanden te voorkomen.         |   3    |  V  |

---

## 7.7 Generatieve media-waarborgen

Zorg ervoor dat AI-systemen geen illegale, schadelijke of ongeautoriseerde media-inhoud genereren door beleidsbeperkingen af te dwingen, uitvoervalidatie te implementeren en traceerbaarheid te waarborgen.

|   #   | Beschrijving                                                                                                                                                                                              | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.7.1 | Controleer of systeemprompts en gebruikersinstructies uitdrukkelijk verbieden het genereren van illegale, schadelijke of zonder toestemming gemaakte deepfake-media (bijv. afbeeldingen, video’s, audio). |   1    | D/V |
| 7.7.2 | Controleer of prompts gefilterd worden op pogingen om personen te impersoneren, seksueel expliciete deepfakes te genereren, of media die echte personen zonder toestemming tonen.                         |   2    | D/V |
| 7.7.3 | Controleer of het systeem gebruikmaakt van perceptuele hashing, watermerkdetectie of fingerprinting om ongeautoriseerde reproductie van auteursrechtelijk beschermd materiaal te voorkomen.               |   2    |  V  |
| 7.7.4 | Verifieer dat alle gegenereerde media cryptografisch ondertekend zijn, watermerken bevatten, of voorzien zijn van tamperbestendige herkomstmetadata voor downstream traceerbaarheid.                      |   3    | D/V |
| 7.7.5 | Controleer dat omzeilpogingen (bijv. prompt-obfuscatie, slang, adversariële formuleringen) worden gedetecteerd, gelogd en rate-limiting toegepast; herhaald misbruik wordt gemeld bij monitoringsystemen. |   3    |  V  |

## Referenties

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [ISO/IEC 42001:2023 – AI Management System](https://www.iso.org/obp/ui/en/)
* [OWASP Top-10 for Large Language Model Applications (2025)](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Improper Output Handling – OWASP LLM05:2025](https://genai.owasp.org/llmrisk/llm052025-improper-output-handling/)
* [Practical Techniques to Constrain LLM Output](https://mychen76.medium.com/practical-techniques-to-constraint-llm-output-in-json-format-e3e72396c670)
* [Dataiku – Structured Text Generation Guide](https://blog.dataiku.com/your-guide-to-structured-text-generation)
* [VL-Uncertainty: Detecting Hallucinations](https://arxiv.org/abs/2411.11919)
* [HaDeMiF: Hallucination Detection & Mitigation](https://openreview.net/forum?id=VwOYxPScxB)
* [Building Confidence in LLM Outputs](https://www.alkymi.io/data-science-room/building-confidence-in-llm-outputs)
* [Explainable AI & LLMs](https://duncsand.medium.com/explainable-ai-140912d31b3b)
* [LLM Red-Teaming Guide](https://www.confident-ai.com/blog/red-teaming-llms-a-step-by-step-guide)
* [Sensitive Information Disclosure in LLMs](https://virtualcyberlabs.com/llm-sensitive-information-disclosure/)
* [LangChain – Chat Model Rate Limiting](https://python.langchain.com/docs/how_to/chat_model_rate_limiting/)
* [OpenAI Rate-Limit & Exponential Back-off](https://hackernoon.com/openais-rate-limit-a-guide-to-exponential-backoff-for-llm-evaluation)
* [Arize AI – LLM Observability Platform](https://arize.com/)

