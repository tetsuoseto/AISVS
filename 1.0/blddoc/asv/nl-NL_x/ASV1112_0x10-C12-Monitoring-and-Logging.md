# C12 Bewaking, logregistratie & anomaliedetectie

## Beheersdoel

Deze sectie beschrijft de vereisten voor het leveren van real-time en forensische zichtbaarheid van wat het model en andere AI-componenten zien, doen en teruggeven, zodat bedreigingen kunnen worden gedetecteerd, geprioriteerd en waaruit kan worden geleerd.

## C12.1 Verzoek & Responselogging

|   #    | Beschrijving                                                                                                                                                                                                          | Niveau | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 12.1.1 | Controleer dat alle gebruikersprompts en modelantwoorden worden gelogd met de juiste metadata (bijv. tijdstempel, gebruikers-ID, sessie-ID, modelversie).                                                             |   1    | D/V |
| 12.1.2 | Verifieer dat logbestanden worden opgeslagen in beveiligde opslagplaatsen met passend retentiebeleid en back-upprocedures.                                                                                            |   1    | D/V |
| 12.1.3 | Controleer of logopslagsystemen versleuteling bij opslag en tijdens verzending implementeren om gevoelige informatie in logs te beschermen.                                                                           |   1    | D/V |
| 12.1.4 | Controleer of gevoelige gegevens in prompts en uitvoer automatisch worden afgedekt of gemaskeerd voordat ze gelogd worden, met configureerbare maskeringsregels voor PII, inloggegevens en vertrouwelijke informatie. |   1    | D/V |
| 12.1.5 | Verifieer dat beleidsbeslissingen en veiligheidsfilteringsacties met voldoende detail worden vastgelegd om audits en foutopsporing van contentmoderatiesystemen mogelijk te maken.                                    |   2    | D/V |
| 12.1.6 | Verifieer dat de logintegriteit beschermd is door bijvoorbeeld cryptografische handtekeningen of write-only opslag.                                                                                                   |   2    | D/V |

---

## C12.2 Misbruikdetectie en Waarschuwingsmeldingen

|   #    | Beschrijving                                                                                                                                                                                       | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 12.2.1 | Controleer of het systeem bekende jailbreak-patronen, prompt-injectie-pogingen en adversariële invoer detecteert en hierop waarschuwt met behulp van detectie op basis van handtekeningen.         |   1    | D/V |
| 12.2.2 | Verifieer dat het systeem integreert met bestaande Security Information and Event Management (SIEM)-platforms met behulp van standaard logformaten en protocollen.                                 |   1    | D/V |
| 12.2.3 | Controleer of verrijkte beveiligingsgebeurtenissen AI-specifieke context bevatten, zoals modelidentificatoren, betrouwbaarheidscores en beslissingen van veiligheidsfilters.                       |   2    | D/V |
| 12.2.4 | Controleer of detectie van gedragsanomalieën ongewone gesprekspatronen, overmatige herhaalpogingen of systematische probeergedragingen identificeert.                                              |   2    | D/V |
| 12.2.5 | Verifieer of real-time waarschuwingsmechanismen beveiligingsteams informeren wanneer potentiële beleidsovertredingen of aanvalspogingen worden gedetecteerd.                                       |   2    | D/V |
| 12.2.6 | Controleer of aangepaste regels zijn opgenomen om AI-specifieke dreigingspatronen te detecteren, waaronder gecoördineerde jailbreakpogingen, promptinjectie-campagnes en modelextractie-aanvallen. |   2    | D/V |
| 12.2.7 | Verifieer dat geautomatiseerde incidentrespons-workflows gecompromitteerde modellen kunnen isoleren, kwaadaardige gebruikers blokkeren en kritieke beveiligingsgebeurtenissen escaleren.           |   3    | D/V |

---

## C12.3 Detectie van modeldrift

|   #    | Beschrijving                                                                                                                                                                                     | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 12.3.1 | Verifieer of het systeem basisprestatie-indicatoren bijhoudt, zoals nauwkeurigheid, betrouwbaarheidscores, latentie en foutpercentages, over modelversies en tijdperken.                         |   1    | D/V |
| 12.3.2 | Controleer dat geautomatiseerde waarschuwingen worden geactiveerd wanneer prestatiemetingen de vooraf gedefinieerde degradatiedrempels overschrijden of aanzienlijk afwijken van de basislijnen. |   2    | D/V |
| 12.3.3 | Verifieer dat hallucinatiedetectie-monitoren gevallen identificeren en markeren waarin de modeluitvoer feitelijk onjuist, inconsistente of gefabriceerde informatie bevat.                       |   2    | D/V |

---

## C12.4 Prestatie- en Gedragstelemetrie

|   #    | Beschrijving                                                                                                                                             | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 12.4.1 | Controleer of operationele statistieken, inclusief verzoeklatentie, tokenverbruik, geheugenverbruik en doorvoer, continu verzameld en bewaakt worden.    |   1    | D/V |
| 12.4.2 | Controleer of de succespercentages en mislukkingspercentages worden vastgelegd met de categorisatie van fouttypes en hun onderliggende oorzaken.         |   1    | D/V |
| 12.4.3 | Zorg ervoor dat de bewaking van resources GPU/CPU-gebruik, geheugengebruik en opslagvereisten omvat, met waarschuwingen bij overschrijding van drempels. |   2    | D/V |

---

## C12.5 AI-incidentresponsplanning en uitvoering

|   #    | Beschrijving                                                                                                                                                                           | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 12.5.1 | Verifieer dat incidentresponsplannen specifiek AI-gerelateerde beveiligingsgebeurtenissen behandelen, waaronder modelcompromittering, gegevensvergiftiging en adversariële aanvallen.  |   1    | D/V |
| 12.5.2 | Controleer of incidentrespons-teams toegang hebben tot AI-specifieke forensische tools en expertise om het gedrag van het model en aanvalsvectoren te onderzoeken.                     |   2    | D/V |
| 12.5.3 | Controleer of de post-incidentanalyse rekening houdt met de hertraining van het model, updates van veiligheidsfilters en de integratie van geleerde lessen in beveiligingsmaatregelen. |   3    | D/V |

---

## C12.5 Detectie van AI-prestatiedaling

Monitor en detecteer degradatie in de prestaties en de kwaliteit van het AI-model na verloop van tijd.

|   #    | Beschrijving                                                                                                                                               | Niveau | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 12.5.1 | Verifieer dat de nauwkeurigheid van het model, precisie, herinneringsratio en F1-scores voortdurend gemonitord en vergeleken worden met baseline-drempels. |   1    | D/V |
| 12.5.2 | Controleer of detectie van datadrift de veranderingen in de invoerverdeling bewaakt die mogelijk de prestaties van het model beïnvloeden.                  |   1    | D/V |
| 12.5.3 | Verifieer dat detectie van concept drift veranderingen in de relatie tussen de invoer en de verwachte uitvoer identificeert.                               |   2    | D/V |
| 12.5.4 | Verifieer dat prestatieverlies automatische waarschuwingen activeert en workflows voor het hertrainen van het model of vervangingsworkflows initieert.     |   2    | D/V |
| 12.5.5 | Controleer of de oorzakenanalyse van degradatie correleert met gegevenswijzigingen, infrastructuurproblemen of externe factoren.                           |   3    |  V  |

---

## C12.6 DAG-visualisatie en workflowbeveiliging

Bescherm workflow-visualisatiesystemen tegen informatielekken en manipulatie-aanvallen.

|   #    | Beschrijving                                                                                                                                                                         | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 12.6.1 | Controleer of DAG-visualisatiegegevens zijn opgeschoond om gevoelige informatie te verwijderen voordat ze worden opgeslagen of verzonden.                                            |   1    | D/V |
| 12.6.2 | Verifieer of de toegangscontroles voor workflowvisualisatie ervoor zorgen dat alleen geautoriseerde gebruikers de beslissingspaden van agenten en redeneringssporen kunnen bekijken. |   1    | D/V |
| 12.6.3 | Verifieer dat de DAG-gegevensintegriteit beschermd is door cryptografische handtekeningen en tamper-evidente opslagmechanismen.                                                      |   2    | D/V |
| 12.6.4 | Controleer of workflow-visualisatiesystemen invoervalidatie implementeren om injectie-aanvallen te voorkomen door bewerkte knooppunt- of randgegevens.                               |   2    | D/V |
| 12.6.5 | Verifieer dat real-time DAG-updates worden beperkt in snelheid en gevalideerd om DoS-aanvallen op visualisatiesystemen te voorkomen.                                                 |   3    | D/V |

---

## C12.7 Proactieve beveiligingsgedragsmonitoring

Detectie en preventie van beveiligingsdreigingen door middel van proactieve analyse van agentengedrag.

|   #    | Beschrijving                                                                                                                                | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 12.7.1 | Controleer of proactieve agentengedragingen vóór uitvoering beveiligingsgevalideerd zijn met integratie van risicobeoordeling.              |   1    | D/V |
| 12.7.2 | Controleer of autonome initiatieftriggers beveiligingscontext-evaluatie en dreigingslandschap-beoordeling bevatten.                         |   2    | D/V |
| 12.7.3 | Verifieer dat proactieve gedragspatronen worden geanalyseerd op potentiële beveiligingsimplicaties en onbedoelde gevolgen.                  |   2    | D/V |
| 12.7.4 | Controleer of beveiligings-kritische proactieve acties expliciete goedkeuringsketens met auditsporen vereisen.                              |   3    | D/V |
| 12.7.5 | Controleer of gedragsanomaliedetectie afwijkingen identificeert in proactieve agentpatronen die mogelijk duiden op een beveiligingsinbreuk. |   3    | D/V |

---

## Referenties

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)
* [EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R1689)

