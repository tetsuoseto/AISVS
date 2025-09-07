# C7 Modelgedrag, outputcontrole en veiligheidsborging

## Beheersingsdoelstelling

Modeluitvoer moet gestructureerd, betrouwbaar, veilig, verklaarbaar en continu gemonitord worden in productie. Dit vermindert hallucinaties, privacylekken, schadelijke inhoud en ongecontroleerde acties, terwijl het vertrouwen van gebruikers en naleving van regelgeving toenemen.

---

## C7.1 Handhaving van het uitvoerformaat

Strikte schema's, beperkte decodering en downstream validatie voorkomen dat verkeerd gevormde of kwaadaardige inhoud zich verspreidt.

|   #   | Beschrijving                                                                                                                                                                                              | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.1.1 | Verifieer dat responschema's (bijv. JSON Schema) worden meegeleverd in de systeem prompt en dat elke output automatisch wordt gevalideerd; niet-conforme outputs leiden tot herstelpogingen of afwijzing. |   1    | D/V |
| 7.1.2 | Controleer of begrensde decodering (stop tokens, regex, max-tokens) is ingeschakeld om overloop of promptinjectie-zijdekanalen te voorkomen.                                                              |   1    | D/V |
| 7.1.3 | Controleer of downstreamcomponenten uitvoer als onbetrouwbaar behandelen en deze valideren aan de hand van schema's of injectieveilige deserializers.                                                     |   2    | D/V |
| 7.1.4 | Verifieer dat onjuiste uitvoergebeurtenissen worden gelogd, gerate-limiteerd en zichtbaar gemaakt voor monitoring.                                                                                        |   3    |  V  |

---

## C7.2 Hallucinatie Detectie & Mitigatie

Onzekerheidsinschatting en terugvalstrategieën beperken gefabriceerde antwoorden.

|   #   | Beschrijving                                                                                                                                                                               | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 7.2.1 | Controleer of token-niveau log-waarschijnlijkheden, ensemble zelfconsistentie, of fijn afgestelde hallucinatie detectors een vertrouwensscore aan elk antwoord toewijzen.                  |   1    | D/V |
| 7.2.2 | Controleer of reacties onder een configureerbare betrouwbaarheidsdrempel fallback-werkstromen activeren (bijv. retrieval-augmented generation, secundair model of menselijke beoordeling). |   1    | D/V |
| 7.2.3 | Controleer of hallucinatie-incidenten zijn voorzien van root-cause metadata en worden doorgegeven aan post-mortem en finetuning pijplijnen.                                                |   2    | D/V |
| 7.2.4 | Controleer of drempelwaarden en detectoren opnieuw worden gekalibreerd na grote model- of kennisbasisupdates.                                                                              |   3    | D/V |
| 7.2.5 | Controleer of dashboardvisualisaties de hallucinatiepercentages bijhouden.                                                                                                                 |   3    |  V  |

---

## C7.3 Outputveiligheid en Privacyfiltering

Beleidsfilters en red-team dekking beschermen gebruikers en vertrouwelijke gegevens.

|   #   | Beschrijving                                                                                                                                                                    | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.3.1 | Controleer of pre- en post-generatie classificatoren haat, intimidatie, zelfbeschadiging, extremistische en seksueel expliciete inhoud die in lijn is met het beleid blokkeren. |   1    | D/V |
| 7.3.2 | Controleer of PII/PCI-detectie en automatische redactie op elke respons worden uitgevoerd; overtredingen leiden tot een privacy-incident.                                       |   1    | D/V |
| 7.3.3 | Controleer of vertrouwelijkheidslabels (bijvoorbeeld handelsgeheimen) zich over modaliteiten heen verspreiden om lekkage in tekst, afbeeldingen of code te voorkomen.           |   2    |  D  |
| 7.3.4 | Controleer of pogingen tot het omzeilen van de filter of classificaties met hoog risico secundaire goedkeuring of herauthenticatie van de gebruiker vereisen.                   |   3    | D/V |
| 7.3.5 | Controleer of de filterdrempels overeenkomen met de juridische jurisdicties en de context van de leeftijd/rol van de gebruiker.                                                 |   3    | D/V |

---

## C7.4 Output- en Actiebeperking

Rate-limieten en goedkeuringspoorten voorkomen misbruik en buitensporige autonomie.

|   #   | Beschrijving                                                                                                                                                                                                 | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 7.4.1 | Controleer of per-gebruiker en per-API-sleutel quota verzoeken, tokens en kosten beperken met exponentiële back-off bij 429-fouten.                                                                          |   1    |  D  |
| 7.4.2 | Verifieer dat geprivilegieerde acties (bestandsschrijvingen, code-uitvoering, netwerkoproepen) goedkeuring op basis van beleid of menselijke tussenkomst vereisen.                                           |   1    | D/V |
| 7.4.3 | Verifieer dat cross-modale consistentiecontroles ervoor zorgen dat afbeeldingen, code en tekst die voor dezelfde aanvraag zijn gegenereerd, niet kunnen worden gebruikt om kwaadaardige inhoud te smokkelen. |   2    | D/V |
| 7.4.4 | Controleer of agentdelegatiediepte, recursielimieten en toegestane hulplijsten expliciet zijn geconfigureerd.                                                                                                |   2    |  D  |
| 7.4.5 | Verifieer dat het overschrijden van limieten gestructureerde beveiligingsgebeurtenissen genereert voor SIEM-inname.                                                                                          |   3    |  V  |

---

## C7.5 Uitvoer Verklaarbaarheid

Transparante signalen verbeteren het vertrouwen van gebruikers en interne foutopsporing.

|   #   | Beschrijving                                                                                                                                             | Niveau | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.5.1 | Controleer of gebruikersgerichte betrouwbaarheidscores of korte redeneersamenvattingen worden weergegeven wanneer de risicobeoordeling dit passend acht. |   2    | D/V |
| 7.5.2 | Controleer of gegenereerde uitleg vermijdt het onthullen van gevoelige systeemopdrachten of propriëtaire gegevens.                                       |   2    | D/V |
| 7.5.3 | Controleer of het systeem token-niveau log-waarschijnlijkheden of attentiekaarten vastlegt en opslaat voor geautoriseerde inspectie.                     |   3    |  D  |
| 7.5.4 | Verifieer dat uitlegbaarheidsartefacten versiebeheer hebben naast modelreleases voor controleerbaarheid.                                                 |   3    |  V  |

---

## C7.6 Monitoring Integratie

Realtime observeerbaarheid sluit de lus tussen ontwikkeling en productie.

|   #   | Beschrijving                                                                                                                                                                 | Niveau | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.6.1 | Controleer of de statistieken (schema-overtredingen, hallucinatiepercentage, toxiciteit, PII-lekken, latentie, kosten) naar een centraal bewakingsplatform worden gestreamd. |   1    |  D  |
| 7.6.2 | Controleer of waarschuwingsdrempels zijn gedefinieerd voor elke veiligheidsmaatstaf, met escalatieroutes voor de dienstdoende medewerker.                                    |   1    |  V  |
| 7.6.3 | Controleer of dashboards output-anomalieën correleren met model/versie, feature-flag en wijzigingen in upstream-gegevens.                                                    |   2    |  V  |
| 7.6.4 | Verifieer dat monitoringgegevens terugkoppelen naar het retrainen, fijn afstemmen of bijwerken van regels binnen een gedocumenteerde MLOps-workflow.                         |   2    | D/V |
| 7.6.5 | Verifieer dat monitoring-pijplijnen zijn onderworpen aan penetratietests en toegangsgeregeld zijn om het lekken van gevoelige logbestanden te voorkomen.                     |   3    |  V  |

---

## 7.7 Generatieve media beveiligingen

Zorg ervoor dat AI-systemen geen illegale, schadelijke of niet-geautoriseerde mediacontent genereren door beleidsbeperkingen, uitvoervalidatie en traceerbaarheid af te dwingen.

|   #   | Beschrijving                                                                                                                                                                                                | Niveau | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.7.1 | Controleer of systeem prompts en gebruikersinstructies expliciet het genereren van illegale, schadelijke of niet-consensuele deepfake-media (zoals afbeelding, video, audio) verbieden.                     |   1    | D/V |
| 7.7.2 | Controleer of prompts worden gefilterd op pogingen om imitatie te genereren, seksueel expliciete deepfakes, of media die echte personen zonder toestemming afbeelden.                                       |   2    | D/V |
| 7.7.3 | Controleer of het systeem gebruikmaakt van perceptuele hashing, watermerkdetectie of fingerprinting om ongeoorloofde reproductie van auteursrechtelijk beschermd materiaal te voorkomen.                    |   2    |  V  |
| 7.7.4 | Verifieer dat alle gegenereerde media cryptografisch is ondertekend, van een watermerk is voorzien of is ingebed met manipulatieresistente herkomstmetadata voor traceerbaarheid downstream.                |   3    | D/V |
| 7.7.5 | Verifieer dat omzeilingspogingen (bijv. promptverduistering, slang, vijandige bewoording) worden gedetecteerd, gelogd en rate-limiting wordt toegepast; herhaald misbruik wordt aan monitorsystemen gemeld. |   3    |  V  |

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

