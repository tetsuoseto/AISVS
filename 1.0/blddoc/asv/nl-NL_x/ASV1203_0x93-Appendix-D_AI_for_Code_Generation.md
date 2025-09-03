# Bijlage D: AI-ondersteunde veilige codering governance en verificatie

## Doel

Dit hoofdstuk definieert basiscontroles op organisatorisch vlak voor het veilige en effectieve gebruik van AI-ondersteunde codeertools tijdens softwareontwikkeling, met waarborging van beveiliging en traceerbaarheid gedurende de SDLC.

---

## AD.1 AI-ondersteunde veilige coderingswerkstroom

Integreer AI-hulpmiddelen in de veilige-software-ontwikkelingslevenscyclus (SSDLC) van de organisatie zonder de bestaande beveiligingspoorten te verzwakken.

|   #    | Beschrijving                                                                                                                                                                                | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| AD.1.1 | Verifieer dat een gedocumenteerde workflow beschrijft wanneer en hoe AI-tools code kunnen genereren, refactoren of reviewen.                                                                |   1    | D/V |
| AD.1.2 | Verifieer of de workflow overeenkomt met elke SSDLC-fase (ontwerp, implementatie, codebeoordeling, testen, uitrol).                                                                         |   2    |  D  |
| AD.1.3 | Verifieer dat metingen (bijv. kwetsbaarheidsdichtheid, mean‑time‑to‑detect) worden verzameld op AI-geproduceerde code en vergeleken met baselines die uitsluitend door mensen zijn gemaakt. |   3    | D/V |

---

## AD.2 AI-toolkwalificatie en dreigingsmodellering

Zorg ervoor dat AI-codeertools worden beoordeeld op beveiligingscapaciteiten, risico's en de impact op de toeleverings‑keten voordat ze in gebruik worden genomen.

|   #    | Beschrijving                                                                                                                                                                                       | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| AD.2.1 | Controleer of het dreigingsmodel voor elk AI-hulpmiddel misbruik, model‑inversion, gegevenslekken en afhankelijkheids‑ketenrisico's identificeert.                                                 |   1    | D/V |
| AD.2.2 | Controleer of de toolbeoordelingen een statische en dynamische analyse van eventuele lokale componenten bevatten en een beoordeling van SaaS-eindpunten (TLS, authenticatie/autorisatie, logging). |   2    |  D  |
| AD.2.3 | Controleer of evaluaties volgens een erkend raamwerk plaatsvinden en na grote versie-updates opnieuw worden uitgevoerd.                                                                            |   3    | D/V |

---

## Beveiligde Prompt & Contextbeheer

Voorkom lekkage van geheimen, auteursrechtelijk beschermde code en persoonlijke gegevens bij het opstellen van prompts of contexten voor AI-modellen.

|   #    | Beschrijving                                                                                                                                                        | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| AD.3.1 | Controleer of de schriftelijke richtlijnen het verzenden van geheimen, inloggegevens of geclassificeerde gegevens in prompts verbieden.                             |   1    | D/V |
| AD.3.2 | Controleer of technische controles (client‑side redactie, goedgekeurde contextfilters) automatisch gevoelige artefacten verwijderen.                                |   2    |  D  |
| AD.3.3 | Verifieer dat prompts en antwoorden getokeniseerd zijn, versleuteld tijdens verzending en in rust, en bewaartermijnen voldoen aan het gegevens-classificatiebeleid. |   3    | D/V |

---

## AD.4 Validatie van AI‑gegenereerde code

Identificeer en verhelp kwetsbaarheden die door AI-uitvoer zijn geïntroduceerd voordat de code wordt samengevoegd of uitgerold.

|   #    | Beschrijving                                                                                                                                                   | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| AD.4.1 | Verifieer dat door AI‑gegenereerde code altijd aan een menselijke codebeoordeling onderworpen is.                                                              |   1    | D/V |
| AD.4.2 | Verifieer dat automatische scanners (SAST/IAST/DAST) op elke pull request die AI‑gegenereerde code bevat draaien en merges blokkeren bij kritieke bevindingen. |   2    |  D  |
| AD.4.3 | Verifieer of differentiële fuzzing of property‑gebaseerde tests beveiligingskritische gedragingen bewijzen (bijv. invoervalidatie, autorisatie-logica).        |   3    | D/V |

---

## AD.5 Verklaarbaarheid & Traceerbaarheid van Code-aanbevelingen

Bied auditors en ontwikkelaars inzicht in waarom een suggestie is gedaan en hoe deze zich heeft ontwikkeld.

|   #    | Beschrijving                                                                                                                                                                                                     | Niveau | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| AD.5.1 | Verifieer dat prompt/response-paaren worden gelogd met commit-ID's.                                                                                                                                              |   1    | D/V |
| AD.5.2 | Controleer of ontwikkelaars in staat zijn om modelcitaten (trainingsfragmenten, documentatie) die een suggestie ondersteunen te tonen.                                                                           |   2    |  D  |
| AD.5.3 | Controleer dat verklarbaarheidsrapporten samen met ontwerpartifacten worden opgeslagen en in beveiligingsbeoordelingen worden genoemd, waarbij wordt voldaan aan de traceerbaarheidsprincipes van ISO/IEC 42001. |   3    | D/V |

---

## AD.6 Voortdurende Feedback & Model Fijn‑afstemming

Verbeter de beveiligingsprestaties van het model na verloop van tijd terwijl negatieve drift wordt voorkomen.

|   #    | Beschrijving                                                                                                                                                                                                 | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| AD.6.1 | Controleer of ontwikkelaars onveilige of niet-conforme suggesties kunnen markeren en of de vlaggen worden bijgehouden.                                                                                       |   1    | D/V |
| AD.6.2 | Verifieer dat geaggregeerde feedback periodieke fine‑tuning of retrieval‑augmented generation informeert met geverifieerde secure‑coding corpora (bijv. OWASP Cheat Sheets).                                 |   2    |  D  |
| AD.6.3 | Verifieer dat een gesloten‑lus evaluatieharnas regressietests uitvoert na elke fijn‑afstemming; beveiligingsmetrieken moeten voldoen aan of hoger zijn dan de eerdere basislijnen voordat ze worden ingezet. |   3    | D/V |

---

### Referenties

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

