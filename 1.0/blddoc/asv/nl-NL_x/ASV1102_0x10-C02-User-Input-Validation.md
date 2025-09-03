# C2 Gebruikersinvoervalidatie

## Beheersdoel

Robuuste validatie van gebruikersinvoer is een eerste verdedigingslinie tegen enkele van de meest schadelijke aanvallen op KI-systemen. Promptinjection-aanvallen kunnen systeeminstructies overschrijven, gevoelige gegevens lekken, of het model laten leiden naar gedrag dat niet is toegestaan. Tenzij er specifieke filters en instructiehiërarchieën zijn, blijkt uit onderzoek dat "multi-shot" jailbreak-aanvallen die profiteren van zeer lange contextvensters effectief zullen zijn. Ook subtiele adversarial-perturbatie-aanvallen—zoals homoglyph-wissels of 1337-taal—kunnen stilletjes de beslissingen van een model veranderen.

---

## C2.1 Bescherming tegen promptinjectie

Promptinjection is een van de grootste risico's voor AI-systemen. Beschermingen tegen deze tactiek maken gebruik van een combinatie van statische patroonfilters, dynamische classificatoren en handhaving van de instructiehiërarchie.

|   #   | Beschrijving                                                                                                                                                                                                                                  | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.1.1 | Verifieer of gebruikersinvoer wordt gescreend tegen een voortdurend bijgewerkte bibliotheek van bekende promptinjectiepatronen (jailbreak-sleutelwoorden, "negeer eerder", rolspelsketens, indirecte HTML/URL-aanvallen).                     |   1    | D/V |
| 2.1.2 | Controleer dat het systeem een instructiehiërarchie afdwingt waarin berichten van het systeem of van de ontwikkelaar de instructies van de gebruiker overschrijven, zelfs na de uitbreiding van het contextvenster.                           |   1    | D/V |
| 2.1.3 | Verifieer dat adversarial evaluation tests (bijv. Red Team "many-shot" prompts) vóór elke release van een model of prompt-template worden uitgevoerd, met drempels voor het slagingspercentage en geautomatiseerde blokkades voor regressies. |   2    | D/V |
| 2.1.4 | Controleer of prompts afkomstig uit inhoud van derden (webpagina's, PDF's, e-mails) gezuiverd zijn in een geïsoleerde parsing-context voordat ze in de hoofdprompt worden samengevoegd.                                                       |   2    |  D  |
| 2.1.5 | Verifieer dat alle updates van prompt-filterregels, versies van classificatiemodellen en wijzigingen aan de bloklijst onder versiebeheer staan en auditbaar zijn.                                                                             |   3    | D/V |

---

## C2.2 Weerstand tegen adversarial-voorbeelden

Modellen voor natuurlijke taalverwerking (NLP) zijn nog steeds kwetsbaar voor subtiele teken- en woordniveau verstoringen die mensen vaak over het hoofd zien, maar modellen neigen ertoe ze verkeerd te classificeren.

|   #   | Beschrijving                                                                                                                                                                                                 | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 2.2.1 | Controleer of de basisinvoer-normalisatiestappen (Unicode NFC, homoglyph mapping, whitespace trimming) vóór tokenisatie worden uitgevoerd.                                                                   |   1    |  D  |
| 2.2.2 | Verifieer dat statistische anomaliedetectie invoer markeert met een ongebruikelijk hoge Levenshtein-afstand tot taalkundige normen, overmatig herhaalde tokens of abnormale embedding-afstanden.             |   2    | D/V |
| 2.2.3 | Verifieer dat de inferentie-pijplijn optionele adversarial-training–geharde modelvarianten of verdedigingslagen ondersteunt (bijvoorbeeld randomisatie, defensieve distillatie) voor hoog-risico-eindpunten. |   2    |  D  |
| 2.2.4 | Controleer of vermoedelijke adversarial invoer in quarantaine wordt geplaatst, gelogd met volledige payloads (na PII-redactie).                                                                              |   2    |  V  |
| 2.2.5 | Verifieer dat robuustheidsmetingen (de slagingskans van bekende aanvalssuites) in de loop der tijd worden bijgehouden en regressies leiden tot een release-blocker.                                          |   3    | D/V |

---

## C2.3 Schema, Type & Lengtevalidatie

AI-aanvallen met misvormde of te grote invoer kunnen parsingfouten veroorzaken, promptspilling tussen velden veroorzaken en bronnenuitputting tot gevolg hebben.  Strikte handhaving van het schema is ook een vereiste bij het uitvoeren van deterministische tool-aanroepen.

|   #   | Beschrijving                                                                                                                                                                                                          | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.3.1 | Controleer dat elk API-eindpunt of elke functie-aanroep een expliciet invoerschema definieert (JSON Schema, Protobuf of multimodale equivalent) en dat invoerwaarden vóór de prompt-samenstelling gevalideerd worden. |   1    |  D  |
| 2.3.2 | Controleer dat invoer die de maximale token- of byte-limieten overschrijdt, wordt geweigerd met een veilige foutmelding en nooit stilletjes wordt afgekapt.                                                           |   1    | D/V |
| 2.3.3 | Verifieer dat typecontroles (bijv. numerieke bereiken, enum-waarden, MIME-types voor afbeeldingen/audio) aan de server-side worden afgedwongen, en niet alleen in de client code.                                     |   2    | D/V |
| 2.3.4 | Controleer dat semantische validators (bijv. JSON Schema) in constante tijd worden uitgevoerd om algorithmische DoS te voorkomen.                                                                                     |   2    |  D  |
| 2.3.5 | Verifieer dat validatiefouten worden gelogd met geredigeerde payload-snippets en eenduidige foutcodes om de beveiligingstriage te vergemakkelijken.                                                                   |   3    |  V  |

---

## C2.4 Inhoud en Beleidscreening

Ontwikkelaars moeten in staat zijn syntactisch geldige prompts te detecteren die om verboden inhoud vragen (zoals illegale instructies, haatspraak en auteursrechtelijk beschermd materiaal) en deze vervolgens te voorkomen dat ze zich verspreiden.

|   #   | Beschrijving                                                                                                                                                                                    | Niveau | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.4.1 | Verifieer dat een inhoudsclassificator (zero-shot of fijn afgesteld) elke invoer beoordeelt op geweld, zelfbeschadiging, haat, seksuele inhoud en illegale verzoeken, met instelbare drempels.  |   1    |  D  |
| 2.4.2 | Verifieer dat invoeren die beleidsregels overtreden standaardafwijzingen of veilige voltooiingen ontvangen, zodat ze niet worden doorgegeven aan downstream LLM-aanroepen.                      |   1    | D/V |
| 2.4.3 | Verifieer dat het screeningmodel of de regelset ten minste elk kwartaal opnieuw wordt getraind/bijgewerkt, waarbij nieuw waargenomen jailbreak- of beleidsomzeilingspatronen worden meegenomen. |   2    |  D  |
| 2.4.4 | Controleer of screening voldoet aan gebruikersspecifieke beleidsregels (leeftijd, regionale wettelijke beperkingen) via regels op basis van attributen die bij het verzoek worden opgelost.     |   2    |  D  |
| 2.4.5 | Verifieer dat screeninglogboeken de waarschijnlijkheidscores van het classificatiemodel en labels voor beleidscategorieën bevatten voor SOC-correlatie en toekomstige red-team-replay.          |   3    |  V  |

---

## C2.5 Invoerlimiet en Misbruikpreventie

Ontwikkelaars moeten misbruik, uitputting van bronnen en geautomatiseerde aanvallen tegen AI-systemen voorkomen door de invoersnelheden te beperken en afwijkende gebruikspatronen te detecteren.

|   #   | Beschrijving                                                                                                                                              | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.5.1 | Controleer of per-gebruiker, per-IP-adres en per-API-sleutel rate-limieten worden afgedwongen voor alle invoer-eindpunten.                                |   1    | D/V |
| 2.5.2 | Controleer of burst-rate-limits en sustained-rate-limits zijn afgesteld om DoS- en brute-force-aanvallen te voorkomen.                                    |   2    | D/V |
| 2.5.3 | Controleer of afwijkende gebruikspatronen (bijv. snelle opeenvolgende verzoeken, invoeroverbelasting) geautomatiseerde blokkades of escalaties activeren. |   2    | D/V |
| 2.5.4 | Controleer of de logbestanden voor misbruikpreventie worden bewaard en beoordeeld op opkomende aanvalspatronen.                                           |   3    |  V  |

---

## C2.6 Multimodale Invoervalidatie

AI-systemen moeten robuuste validatie van niet-tekstuele invoer (afbeeldingen, audio, bestanden) inbouwen om injectie, omzeiling of misbruik van middelen te voorkomen.

|   #   | Beschrijving                                                                                                                                      | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.6.1 | Verifieer dat alle niet-tekstuele invoer (afbeeldingen, audio, bestanden) op type, grootte en formaat is gevalideerd voordat deze wordt verwerkt. |   1    |  D  |
| 2.6.2 | Verifieer dat bestanden vóór de gegevensinname worden gescand op malware en steganografische payloads.                                            |   2    | D/V |
| 2.6.3 | Zorg ervoor dat afbeeldings- en audiogegevens worden gecontroleerd op adversariële verstoringen of bekende aanvalspatronen.                       |   2    | D/V |
| 2.6.4 | Controleer of multimodale invoervalidatiefouten worden gelogd en waarschuwingen activeren voor nader onderzoek.                                   |   3    |  V  |

---

## C2.7 Invoerherkomst & Toeschrijving

AI-systemen moeten auditing, misbruikregistratie en naleving ondersteunen door de oorsprong van alle gebruikersinvoer te monitoren en te taggen.

|   #   | Beschrijving                                                                                                                           | Niveau | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.7.1 | Controleer of alle gebruikersinvoer bij het opnemen is voorzien van metagegevens (gebruikers-ID, sessie, bron, tijdstempel, IP-adres). |   1    | D/V |
| 2.7.2 | Controleer of herkomstmetadata behouden blijft en auditbaar is voor alle verwerkte invoer.                                             |   2    | D/V |
| 2.7.3 | Controleer of anomale of onbetrouwbare invoerbronnen worden gemarkeerd en onderworpen aan verhoogde screening of blokkering.           |   2    | D/V |

---

## C2.8 Real-Time Adaptieve Dreigingsdetectie

Ontwikkelaars moeten geavanceerde dreigingsdetectiesystemen voor AI inzetten die zich aanpassen aan nieuwe aanvalspatronen en realtime bescherming bieden met gecompileerde patroonmatching.

|   #   | Beschrijving                                                                                                                                                                                                           | Niveau | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.8.1 | Controleer of bedreigingsdetectiepatronen zijn gecompileerd tot geoptimaliseerde regex-engines voor realtime filtering met hoge prestaties en minimale latentie.                                                       |   1    | D/V |
| 2.8.2 | Controleer of bedreigingsdetectiesystemen afzonderlijke patroonbibliotheken bijhouden voor verschillende dreigingscategorieën (promptinjectie, schadelijke inhoud, gevoelige gegevens, systeemcommando's).             |   1    | D/V |
| 2.8.3 | Verifieer dat adaptieve dreigingsdetectie machine-learning-modellen omvat die de gevoeligheid voor dreigingen bijwerken op basis van aanvalfrequentie en succespercentages.                                            |   2    | D/V |
| 2.8.4 | Verifieer dat real-time dreigingsinformatiefeeds automatisch patroonbibliotheken bijwerken met nieuwe aanvalssignaturen en IOCs (Indicatoren van compromissie).                                                        |   2    | D/V |
| 2.8.5 | Controleer of de ratio van valse positieven bij dreigingsdetectie continu wordt gemonitord en of de patroonspecificiteit automatisch wordt afgesteld om verstoring van legitieme toepassingsgevallen te minimaliseren. |   3    | D/V |
| 2.8.6 | Controleer of contextuele dreigingsanalyse rekening houdt met de invoerbron, gedragspatronen van de gebruiker en sessiegeschiedenis om de detectienauwkeurigheid te verbeteren.                                        |   3    | D/V |
| 2.8.7 | Verifieer dat de prestatie-indicatoren voor dreigingsdetectie (detectiepercentage, verwerkingslatentie, middelenverbruik) in realtime worden gemonitord en geoptimaliseerd.                                            |   3    | D/V |

---

## C2.9 Multimodale Beveiligingsvalidatiepijplijn

Ontwikkelaars moeten beveiligingsvalidatie bieden voor tekst-, beeld-, audio- en andere AI-invoer-modi met specifieke soorten dreigingsdetectie en resource-isolatie.

|   #   | Beschrijving                                                                                                                                                                                                                                                                          | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.9.1 | Controleer of elke invoermodaliteit toegewijde beveiligingsvalidatoren heeft met gedocumenteerde dreigingspatronen (tekst: promptinjection, afbeeldingen: steganografie, audio: spectrogramaanvallen) en detectiedrempels.                                                            |   1    | D/V |
| 2.9.2 | Controleer dat multimodale invoer wordt verwerkt in geïsoleerde sandbox-omgevingen met gedefinieerde bronnenlimieten (geheugen, CPU, verwerkingstijd) die specifiek zijn voor elk modaliteitstype en vastgelegd in beveiligingsbeleid.                                                |   2    | D/V |
| 2.9.3 | Controleer of cross-modal aanvalendetectie gecoördineerde aanvallen identificeert die zich over meerdere invoertypen uitstrekken (bijv. steganografische payloads in afbeeldingen gecombineerd met promptinjectie in tekst) met correlatieregels en het genereren van waarschuwingen. |   2    | D/V |
| 2.9.4 | Controleer of multimodale validatiefouten leiden tot gedetailleerde logging, inclusief alle invoermodaliteiten, validatieresultaten, dreigingsscores en correlatieanalyse met gestructureerde logformaten voor SIEM-integratie.                                                       |   3    | D/V |
| 2.9.5 | Verifieer dat modaliteitsspecifieke inhoudsclassificatoren zijn bijgewerkt volgens gedocumenteerde schema's (minimaal elk kwartaal) met nieuwe dreigingspatronen, adversariële voorbeelden en prestatiebenchmarks die boven de basisdrempels blijven.                                 |   3    | D/V |

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

