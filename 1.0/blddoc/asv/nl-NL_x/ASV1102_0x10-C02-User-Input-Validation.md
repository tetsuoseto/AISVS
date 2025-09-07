# C2 Gebruikersinvoer Validatie

## Beheersingsdoelstelling

Robuuste validatie van gebruikersinvoer is een eerste verdedigingslinie tegen enkele van de meest schadelijke aanvallen op AI-systemen. Prompt-injectieaanvallen kunnen systeeminstructies overschrijven, gevoelige gegevens lekken of het model sturen naar gedrag dat niet is toegestaan. Tenzij er speciale filters en instructiehiërarchieën zijn, toont onderzoek aan dat "multi-shot" jailbreaks die gebruikmaken van zeer lange contextvensters effectief zullen zijn. Ook kunnen subtiele adversariale perturbatieaanvallen—zoals homoglyph swaps of leetspeak—stilletjes de beslissingen van een model wijzigen.

---

## C2.1 Verdediging tegen promptinjectie

Promptinjectie is een van de grootste risico's voor AI-systemen. Verdedigingen tegen deze tactiek maken gebruik van een combinatie van statische patroonfilters, dynamische classifiers en handhaving van instructiehiërarchie.

|   #   | Beschrijving                                                                                                                                                                                                                      | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.1.1 | Controleer of gebruikersinvoer wordt gescreend aan de hand van een continu bijgewerkte bibliotheek van bekende promptinjectiepatronen (jailbreak-trefwoorden, "negeer vorige", rollenspelketens, indirecte HTML/URL-aanvallen).   |   1    | D/V |
| 2.1.2 | Controleer of het systeem een instructiehiërarchie afdwingt waarbij systeem- of ontwikkelaarsberichten gebruikersinstructies overstemmen, zelfs na uitbreiding van het contextvenster.                                            |   1    | D/V |
| 2.1.3 | Verifieer dat adversariale evaluatietests (bijv. Red Team "many-shot" prompts) worden uitgevoerd vóór elke release van een model of prompt-sjabloon, met succespercentage-drempels en geautomatiseerde blokkades voor regressies. |   2    | D/V |
| 2.1.4 | Controleer of prompts afkomstig van content van derden (webpagina's, PDF's, e-mails) worden gezuiverd in een geïsoleerde parseercontext voordat ze worden samengevoegd in de hoofdprompt.                                         |   2    |  D  |
| 2.1.5 | Verifieer dat alle updates van prompt-filterregels, versies van classificatiemodellen en wijzigingen in de blokkadelijsten versiebeheer hebben en controleerbaar zijn.                                                            |   3    | D/V |

---

## C2.2 Weerstand tegen adversariële voorbeelden

Modellen voor natuurlijke taalverwerking (NLP) zijn nog steeds kwetsbaar voor subtiele verstoringen op karakter- of woordniveau die mensen vaak over het hoofd zien, maar die door modellen vaak verkeerd worden geclassificeerd.

|   #   | Beschrijving                                                                                                                                                                                                    | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.2.1 | Controleer of de basisstappen voor invoernormalisatie (Unicode NFC, homoglyph mapping, het trimmen van witruimtes) worden uitgevoerd voordat de tokenisatie plaatsvindt.                                        |   1    |  D  |
| 2.2.2 | Verifieer dat statistische anomaliedetectie invoer markeert met een ongewoon hoge bewerkingsafstand tot taalkundige normen, overmatige herhaalde tokens of abnormale insluitingsafstanden.                      |   2    | D/V |
| 2.2.3 | Controleer of de inferentie-pijplijn optionele, door adversariële training versterkte modelvarianten of verdedigingslagen ondersteunt (bijv. randomisatie, defensieve distillatie) voor hoog-risico eindpunten. |   2    |  D  |
| 2.2.4 | Controleer of vermoedelijke vijandige invoer in quarantaine wordt geplaatst en wordt gelogd met volledige payloads (na redactie van PII).                                                                       |   2    |  V  |
| 2.2.5 | Verifieer dat robuustheidsmetrics (succespercentage van bekende aanvalspakketten) in de loop van de tijd worden gevolgd en dat regressies een releaseblokker activeren.                                         |   3    | D/V |

---

## C2.3 Schema-, Type- en Lengtevalidatie

AI-aanvallen met slecht gevormde of te grote invoer kunnen parseringsfouten veroorzaken, overlopen van prompts over velden heen en uitputting van bronnen. Strikte naleving van schema's is ook een vereiste bij het uitvoeren van deterministische toolaanroepen.

|   #   | Beschrijving                                                                                                                                                                                                           | Niveau | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.3.1 | Verifieer dat elke API- of functie-aanroependpoint een expliciet invoerdomeinschema definieert (JSON Schema, Protobuf of multimodaal equivalent) en dat invoer wordt gevalideerd voordat de prompt wordt samengesteld. |   1    |  D  |
| 2.3.2 | Verifieer dat invoer die de maximale token- of bytelimieten overschrijdt, wordt afgewezen met een veilige foutmelding en nooit stilzwijgend wordt afgekapt.                                                            |   1    | D/V |
| 2.3.3 | Controleer of typecontroles (bijv. numerieke bereiken, enumwaarden, MIME-types voor afbeeldingen/audio) aan de serverzijde worden afgedwongen en niet alleen in clientcode.                                            |   2    | D/V |
| 2.3.4 | Controleer of semantische validateurs (bijvoorbeeld JSON Schema) in constante tijd draaien om algoritmische DoS te voorkomen.                                                                                          |   2    |  D  |
| 2.3.5 | Verifieer dat validatiefouten worden geregistreerd met geredigeerde payloadfragmenten en ondubbelzinnige foutcodes om de beveiligingstriage te ondersteunen.                                                           |   3    |  V  |

---

## C2.4 Inhouds- en beleidscontrole

Ontwikkelaars moeten in staat zijn om syntactisch geldige prompts te detecteren die niet-toegestane inhoud verzoeken (zoals illegale instructies, haatspraak en auteursrechtelijk beschermde tekst) en vervolgens voorkomen dat deze zich verspreiden.

|   #   | Beschrijving                                                                                                                                                                                                | Niveau | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.4.1 | Verifieer dat een contentclassificator (zero shot of fijn-afgestemd) elke invoer beoordeelt op geweld, zelfbeschadiging, haat, seksueel inhoud en illegale verzoeken, met configureerbare drempels.         |   1    |  D  |
| 2.4.2 | Controleer of invoer die het beleid overtreedt gestandaardiseerde weigeringen of veilige voltooiingen ontvangt, zodat deze niet worden doorgegeven aan downstream LLM-aanroepen.                            |   1    | D/V |
| 2.4.3 | Controleer of het screeningsmodel of de regelset ten minste elk kwartaal wordt hertraind/geüpdatet, waarbij nieuw waargenomen jailbreak- of beleidsomzeilingspatronen worden opgenomen.                     |   2    |  D  |
| 2.4.4 | Controleer of screenings voldoen aan gebruikersspecifieke beleidsregels (leeftijd, regionale wettelijke beperkingen) via op attributen gebaseerde regels die op het moment van de aanvraag worden opgelost. |   2    |  D  |
| 2.4.5 | Controleer of screeningslogboeken classificatorvertrouwensscores en beleidscategorie-tags bevatten voor SOC-correlatie en toekomstige red-team herhaling.                                                   |   3    |  V  |

---

## C2.5 Invoer Snelheidsbeperking & Misbruik Preventie

Ontwikkelaars moeten misbruik, uitputting van middelen en geautomatiseerde aanvallen op AI-systemen voorkomen door de invoersnelheid te beperken en afwijkende gebruikspatronen te detecteren.

|   #   | Beschrijving                                                                                                                                             | Niveau | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.5.1 | Controleer of per-gebruiker, per-IP en per-API-sleutel snelheidslimieten worden gehandhaafd voor alle invoerendpoints.                                   |   1    | D/V |
| 2.5.2 | Controleer of burst- en aanhoudende snelheidslimieten zijn afgestemd om DoS- en brute force-aanvallen te voorkomen.                                      |   2    | D/V |
| 2.5.3 | Verifieer dat afwijkende gebruikspatronen (bijv. snelle opeenvolgende aanvragen, input overstroming) geautomatiseerde blokkades of escalaties activeren. |   2    | D/V |
| 2.5.4 | Controleer of misbruikpreventielogs worden bewaard en geanalyseerd op opkomende aanvalspatronen.                                                         |   3    |  V  |

---

## C2.6 Multi-Modal Invoervalidatie

AI-systemen moeten robuuste validatie bevatten voor niet-tekstuele invoer (afbeeldingen, audio, bestanden) om injectie, ontwijking of misbruik van middelen te voorkomen.

|   #   | Beschrijving                                                                                                                                        | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.6.1 | Controleer of alle niet-tekstuele invoer (afbeeldingen, audio, bestanden) wordt gevalideerd op type, grootte en formaat voordat ze worden verwerkt. |   1    |  D  |
| 2.6.2 | Controleer of bestanden worden gescand op malware en steganografische payloads voordat ze worden geïmporteerd.                                      |   2    | D/V |
| 2.6.3 | Controleer of beeld-/audio-invoer wordt gecontroleerd op adversariële verstoringen of bekende aanvalspatronen.                                      |   2    | D/V |
| 2.6.4 | Controleer of multi-modale invoervalidatiefouten worden geregistreerd en waarschuwingen activeren voor onderzoek.                                   |   3    |  V  |

---

## C2.7 Invoer Herkomst & Toeschrijving

AI-systemen moeten auditing, misbruikregistratie en naleving ondersteunen door de oorsprong van alle gebruikersinvoer te monitoren en te taggen.

|   #   | Beschrijving                                                                                                                         | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 2.7.1 | Controleer of alle gebruikersinvoer bij binnenkomst zijn voorzien van metadata (gebruikers-ID, sessie, bron, tijdstempel, IP-adres). |   1    | D/V |
| 2.7.2 | Verifieer dat provenance metadata behouden blijft en controleerbaar is voor alle verwerkte invoer.                                   |   2    | D/V |
| 2.7.3 | Controleer of anomalieën of niet-vertrouwde invoerbronnen worden gemarkeerd en onderworpen aan verhoogde controle of blokkering.     |   2    | D/V |

---

## C2.8 Real-Time Adaptieve Dreigingsdetectie

Ontwikkelaars moeten geavanceerde dreigingsdetectiesystemen voor AI gebruiken die zich aanpassen aan nieuwe aanvalspatronen en realtime bescherming bieden met gecompileerde patroonherkenning.

|   #   | Beschrijving                                                                                                                                                                                                      | Niveau | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.8.1 | Controleer of dreigingsdetectiepatronen worden gecompileerd in geoptimaliseerde regex-engines voor hoge prestaties bij realtime filtering met minimale latentie-impact.                                           |   1    | D/V |
| 2.8.2 | Controleer of dreigingsdetectiesystemen afzonderlijke patroonbibliotheken bijhouden voor verschillende dreigingscategorieën (promptinjectie, schadelijke inhoud, gevoelige gegevens, systeemcommando's).          |   1    | D/V |
| 2.8.3 | Controleer of adaptieve dreigingsdetectie machinaal leermodellen bevat die de dreigingsgevoeligheid bijwerken op basis van de frequentie en succesratio's van aanvallen.                                          |   2    | D/V |
| 2.8.4 | Controleer of real-time dreigingsinformatiesystemen patroonbibliotheken automatisch bijwerken met nieuwe aanvalssignaturen en IOC's (Indicators of Compromise).                                                   |   2    | D/V |
| 2.8.5 | Verifieer dat fout-positieve niveaus van dreigingsdetectie continu worden gemonitord en dat patroon-specificiteit automatisch wordt aangepast om interferentie met legitieme gebruiksscenario's te minimaliseren. |   3    | D/V |
| 2.8.6 | Verifieer dat contextuele dreigingsanalyse rekening houdt met de invoerbron, gebruikersgedragspatronen en sessiegeschiedenis om de detectienauwkeurigheid te verbeteren.                                          |   3    | D/V |
| 2.8.7 | Verifieer dat de prestatiestatistieken van bedreigingsdetectie (detectiesnelheid, verwerkingslatentie, resourcegebruik) in realtime worden bewaakt en geoptimaliseerd.                                            |   3    | D/V |

---

## C2.9 Multi-Modale Beveiligingsvalidatie-Pijplijn

Ontwikkelaars moeten beveiligingsvalidatie bieden voor tekst-, beeld-, audio- en andere AI-invoermodaliteiten met specifieke typen bedreigingsdetectie en resource-isolatie.

|   #   | Beschrijving                                                                                                                                                                                                                                                    | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.9.1 | Verifieer dat elke invoermodaliteit toegewijde beveiligingsvalidators heeft met gedocumenteerde bedreigingspatronen (tekst: promptinjectie, afbeeldingen: steganografie, audio: spectrogramaanvallen) en detectiedrempels.                                      |   1    | D/V |
| 2.9.2 | Verifieer dat multi-modale inputs worden verwerkt in geïsoleerde sandboxes met gedefinieerde resourcebeperkingen (geheugen, CPU, verwerkingstijd) die specifiek zijn voor elk modaliteitstype en gedocumenteerd zijn in het beveiligingsbeleid.                 |   2    | D/V |
| 2.9.3 | Verifieer dat cross-modale aanvaldetectie gecoördineerde aanvallen identificeert die meerdere inputtypen omvatten (bijv. steganografische payloads in afbeeldingen gecombineerd met promptinjectie in tekst) met behulp van correlatieregels en alarmgeneratie. |   2    | D/V |
| 2.9.4 | Verifieer dat multi-modale validatiefouten gedetailleerde logregistratie activeren, inclusief alle inputmodaliteiten, validatieresultaten, dreigingsscores en correlatieanalyse met gestructureerde logformaten voor SIEM-integratie.                           |   3    | D/V |
| 2.9.5 | Controleer of modality-specifieke inhoudsclassificaties worden bijgewerkt volgens gedocumenteerde schema's (minimaal elk kwartaal) met nieuwe bedreigingspatronen, adversariële voorbeelden en prestatiebenchmarks die boven baseline-drempels worden gehouden. |   3    | D/V |

---

## Referenties

* [LLM01:2025 Prompt Injection – OWASP Top 10 for LLM & Generative AI Security](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)
* [Generative AI's Biggest Security Flaw Is Not Easy to Fix](https://www.wired.com/story/generative-ai-prompt-injection-hacking)
* [Many-shot jailbreaking \ Anthropic](https://www.anthropic.com/research/many-shot-jailbreaking)
* [$PDF$ OpenAI GPT-4.5 System Card](https://cdn.openai.com/gpt-4-5-system-card-2272025.pdf)
* [Notebook for the CheckThat Lab at CLEF 2024](https://ceur-ws.org/Vol-3740/paper-53.pdf)
* [Mitigate jailbreaks and prompt injections – Anthropic](https://docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/mitigate-jailbreaks)
* [Chapter 3 MITRE ATT\&CK – Adversarial Model Analysis](https://ama.drwhy.ai/mitre-attck.html)
* [OWASP Top 10 for LLM Applications 2025 – WorldTech IT](https://wtit.com/blog/2025/04/17/owasp-top-10-for-llm-applications-2025/)
* [OWASP Machine Learning Security Top Ten](https://owasp.org/www-project-machine-learning-security-top-10/)
* [Few words about AI Security – Jussi Metso](https://www.jussimetso.com/index.php/2024/09/28/few-words-about-ai-security/)
* [How To Ensure LLM Output Adheres to a JSON Schema | Modelmetry](https://modelmetry.com/blog/how-to-ensure-llm-output-adheres-to-a-json-schema)
* [Easily enforcing valid JSON schema following – API](https://community.openai.com/t/feature-request-function-calling-easily-enforcing-valid-json-schema-following/263515?utm_source)
* [AI Safety + Cybersecurity R\&D Tracker – Fairly AI](https://www.fairly.ai/blog/ai-cybersecurity-tracker)
* [Anthropic makes 'jailbreak' advance to stop AI models producing harmful results](https://www.ft.com/content/cf11ebd8-aa0b-4ed4-945b-a5d4401d186e)
* [Pattern matching filter rules - IBM](https://www.ibm.com/docs/ssw_aix_71/security/intrusion_pattern_matching_filter_rules.html)
* [Real-time Threat Detection](https://www.darktrace.com/cyber-ai-glossary/real-time-threat-detection)

