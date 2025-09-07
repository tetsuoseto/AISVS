# Bijlage D: Governance en verificatie van veilig coderen met AI-ondersteuning

## Doelstelling

Dit hoofdstuk definieert basisorganisatorische controles voor het veilige en effectieve gebruik van AI-ondersteunde codeerhulpmiddelen tijdens softwareontwikkeling, waarbij veiligheid en traceerbaarheid gedurende de SDLC worden gegarandeerd.

---

## AD.1 AI-ondersteunde veilige coderingsworkflow

Integreer AI-tools in de veilige softwareontwikkelingslevenscyclus (SSDLC) van de organisatie zonder de bestaande beveiligingspoorten te verzwakken.

|   #    | Beschrijving                                                                                                                                                                                       | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| AD.1.1 | Controleer of een gedocumenteerde workflow beschrijft wanneer en hoe AI-tools code mogen genereren, herstructureren of beoordelen.                                                                 |   1    | D/V |
| AD.1.2 | Controleer of de workflow overeenkomt met elke SSDLC-fase (ontwerp, uitvoering, codebeoordeling, testen, implementatie).                                                                           |   2    |  D  |
| AD.1.3 | Controleer of metrieken (bijv. kwetsbaarheidsdichtheid, gemiddelde detectietijd) worden verzameld voor door AI geproduceerde code en vergeleken met baselines die alleen door mensen zijn gemaakt. |   3    | D/V |

---

## AD.2 AI-hulpmiddelkwalificatie & dreigingsmodellering

Zorg ervoor dat AI-codeertools worden geëvalueerd op beveiligingsmogelijkheden, risico's en impact op de toeleveringsketen voordat ze worden geïmplementeerd.

|   #    | Beschrijving                                                                                                                                                                         | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| AD.2.1 | Controleer of een dreigingsmodel voor elk AI-instrument misbruik, modelinversie, datalekken en risico's in de afhankelijkheidsketen identificeert.                                   |   1    | D/V |
| AD.2.2 | Verifieer dat toolbeoordelingen statische/dynamische analyse omvatten van eventuele lokale componenten en beoordeling van SaaS-eindpunten (TLS, authenticatie/autorisatie, logging). |   2    |  D  |
| AD.2.3 | Verifieer dat evaluaties een erkend kader volgen en opnieuw worden uitgevoerd na belangrijke versie-updates.                                                                         |   3    | D/V |

---

## AD.3 Beheer van beveiligde prompts en context

Voorkom het lekken van geheimen, eigendomsgevoerde code en persoonlijke gegevens bij het opstellen van prompts of contexten voor AI-modellen.

|   #    | Beschrijving                                                                                                                                                             | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| AD.3.1 | Controleer of de schriftelijke richtlijnen het versturen van geheimen, inloggegevens of geclassificeerde gegevens in prompts verbieden.                                  |   1    | D/V |
| AD.3.2 | Controleer of technische controles (redactie aan de clientzijde, goedgekeurde contextfilters) automatisch gevoelige gegevens verwijderen.                                |   2    |  D  |
| AD.3.3 | Controleer of prompts en antwoorden worden getokeniseerd, versleuteld tijdens overdracht en in opslag, en of de bewaartermijnen voldoen aan het dataclassificatiebeleid. |   3    | D/V |

---

## AD.4 Validatie van door AI gegenereerde code

Detecteer en herstel kwetsbaarheden die door AI-uitvoer zijn geïntroduceerd voordat de code wordt samengevoegd of geïmplementeerd.

|   #    | Beschrijving                                                                                                                                                           | Niveau | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| AD.4.1 | Zorg ervoor dat AI-gegenereerde code altijd wordt onderworpen aan een menselijke codebeoordeling.                                                                      |   1    | D/V |
| AD.4.2 | Verifieer dat geautomatiseerde scanners (SAST/IAST/DAST) worden uitgevoerd bij elke pull request met AI‑gegenereerde code en blokkeer merges bij kritieke bevindingen. |   2    |  D  |
| AD.4.3 | Verifieer dat differentiële fuzz-testing of op eigenschappen gebaseerde tests veiligheid‑kritieke gedragingen bewijzen (bijv. invoervalidatie, autorisatielogica).     |   3    | D/V |

---

## AD.5 Verklaarbaarheid en Traceerbaarheid van Code Suggesties

Bied auditors en ontwikkelaars inzicht in waarom een suggestie is gedaan en hoe deze is geëvolueerd.

|   #    | Beschrijving                                                                                                                                                                                         | Niveau | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| AD.5.1 | Verifieer dat prompt/response-paren worden vastgelegd met commit-ID's.                                                                                                                               |   1    | D/V |
| AD.5.2 | Controleer of ontwikkelaars modelverwijzingen (trainingsfragmenten, documentatie) kunnen weergeven ter ondersteuning van een suggestie.                                                              |   2    |  D  |
| AD.5.3 | Verifieer dat verklaringsrapporten worden opgeslagen met ontwerpdocumenten en worden genoemd in beveiligingsbeoordelingen, waarbij wordt voldaan aan de traceerbaarheidsprincipes van ISO/IEC 42001. |   3    | D/V |

---

## AD.6 Continüe feedback en modelfijnafstelling

Verbeter de beveiligingsprestaties van het model in de loop van de tijd terwijl negatieve verschuiving wordt voorkomen.

|   #    | Beschrijving                                                                                                                                                                              | Niveau | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| AD.6.1 | Controleer of ontwikkelaars onveilige of niet-conforme suggesties kunnen markeren en dat deze markeringen worden bijgehouden.                                                             |   1    | D/V |
| AD.6.2 | Controleer of verzamelde feedback periodiek wordt gebruikt voor fijn-afstemming of retrieval-augmented generatie met geverifieerde beveiligde-codeer corpora (bijv. OWASP Cheat Sheets).  |   2    |  D  |
| AD.6.3 | Verifieer dat een evaluatiekader met gesloten lus regressietests uitvoert na elke fine-tune; beveiligingsmetriek moet voldoen aan of beter zijn dan eerdere baselines vóór implementatie. |   3    | D/V |

---

### Referenties

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

