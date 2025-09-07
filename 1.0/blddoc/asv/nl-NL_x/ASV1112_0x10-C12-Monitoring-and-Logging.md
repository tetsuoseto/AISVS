# C12 Monitoring, Logging & Anomaliedetectie

## Beheersingsdoelstelling

Deze sectie bevat eisen voor het leveren van realtime en forensische zichtbaarheid in wat het model en andere AI-componenten zien, doen en retourneren, zodat bedreigingen kunnen worden gedetecteerd, geprioriteerd en hiervan geleerd kan worden.

## C12.1 Aanvraag- enantwoordlogboekregistratie

|   #    | Beschrijving                                                                                                                                                                                                                   | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 12.1.1 | Verifieer dat alle gebruikersprompts en modelantwoorden worden geregistreerd met de juiste metadata (bijv. tijdstempel, gebruikers-ID, sessie-ID, modelversie).                                                                |   1    | D/V |
| 12.1.2 | Verifieer dat logs worden opgeslagen in beveiligde, toegang-gecontroleerde repositories met geschikte bewaarbeleid en back-upprocedures.                                                                                       |   1    | D/V |
| 12.1.3 | Controleer of logopslagsystemen encryptie toepassen voor gegevens in rust en tijdens overdracht om gevoelige informatie in de logs te beschermen.                                                                              |   1    | D/V |
| 12.1.4 | Verifieer dat gevoelige gegevens in prompts en outputs automatisch worden doorgestreept of afgeschermd voordat ze worden gelogd, met configureerbare regels voor het afschermen van PII, inloggegevens en eigendomsinformatie. |   1    | D/V |
| 12.1.5 | Verifieer dat beleidsbeslissingen en veiligheidsfilteracties met voldoende detail worden vastgelegd om audit en debugging van contentmoderatiesystemen mogelijk te maken.                                                      |   2    | D/V |
| 12.1.6 | Controleer of de logintegriteit wordt beschermd door bijvoorbeeld cryptografische handtekeningen of alleen-schrijven opslag.                                                                                                   |   2    | D/V |

---

## C12.2 Misbruikdetectie en waarschuwingen

|   #    | Beschrijving                                                                                                                                                                                           | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 12.2.1 | Controleer of het systeem bekende jailbreak-patronen, pogingen tot promptinjectie en vijandige invoer detecteert en waarschuwingen geeft met behulp van handtekeninggebaseerde detectie.               |   1    | D/V |
| 12.2.2 | Controleer of het systeem integreert met bestaande Security Information and Event Management (SIEM)-platforms met gebruik van standaard logformaten en protocollen.                                    |   1    | D/V |
| 12.2.3 | Controleer of verrijkte beveiligingsgebeurtenissen AI-specifieke context bevatten, zoals modelidentificaties, betrouwbaarheidscores en beslissingen van veiligheidsfilters.                            |   2    | D/V |
| 12.2.4 | Controleer of gedragsafwijkingsdetectie ongebruikelijke gespreks­patronen, overmatige pogingen tot herhaling of systematische onderzoeks­gedragingen identificeert.                                    |   2    | D/V |
| 12.2.5 | Controleer of realtime waarschuwingsmechanismen beveiligingsteams op de hoogte stellen wanneer mogelijke beleidschendingen of aanvalspogingen worden gedetecteerd.                                     |   2    | D/V |
| 12.2.6 | Verifieer dat aangepaste regels zijn opgenomen om AI-specifieke dreigingspatronen te detecteren, waaronder gecoördineerde jailbreakpogingen, promptinjectiecampagnes en modelextractie-aanvallen.      |   2    | D/V |
| 12.2.7 | Controleer of geautomatiseerde incidentreactieworkflows in staat zijn om gecompromitteerde modellen te isoleren, kwaadaardige gebruikers te blokkeren en kritieke beveiligingsincidenten te escaleren. |   3    | D/V |

---

## C12.3 Detectie van Modelafwijking

|   #    | Beschrijving                                                                                                                                                                                | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 12.3.1 | Controleer of het systeem basisprestatie-indicatoren bijhoudt, zoals nauwkeurigheid, betrouwbaarheidswaarden, latentie en foutpercentages over verschillende modelversies en tijdsperioden. |   1    | D/V |
| 12.3.2 | Controleer of geautomatiseerde waarschuwingen worden geactiveerd wanneer prestatiestatistieken vooraf gedefinieerde degradatiedrempels overschrijden of aanzienlijk afwijken van baselines. |   2    | D/V |
| 12.3.3 | Controleer of de monitors voor hallucinatie-detectie gevallen identificeren en markeren wanneer modeluitvoer feitelijk onjuiste, inconsistente of verzonnen informatie bevat.               |   2    | D/V |

---

## C12.4 Prestaties & Gedrags-Telemetrie

|   #    | Beschrijving                                                                                                                                                             | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 12.4.1 | Verifieer dat operationele metrics zoals verzoeklatentie, tokenverbruik, geheugengebruik en doorvoersnelheid continu worden verzameld en gemonitord.                     |   1    | D/V |
| 12.4.2 | Verifieer dat succes- en faalpercentages worden bijgehouden met categorisering van fouttypes en hun oorzaken.                                                            |   1    | D/V |
| 12.4.3 | Controleer of het monitoren van resourcegebruik GPU-/CPU-gebruik, geheugengebruik en opslagvereisten omvat, met waarschuwingen bij het overschrijden van drempelwaarden. |   2    | D/V |

---

## C12.5 AI-incidentresponsplanning & uitvoering

|   #    | Beschrijving                                                                                                                                                                  | Niveau | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 12.5.1 | Controleer of incidentresponsplannen specifiek AI-gerelateerde beveiligingsincidenten behandelen, zoals modelcompromittering, datavervuiling en adversariële aanvallen.       |   1    | D/V |
| 12.5.2 | Controleer of de incidentrespons-teams toegang hebben tot AI-specifieke forensische tools en expertise om modelgedrag en aanvalspatronen te onderzoeken.                      |   2    | D/V |
| 12.5.3 | Controleer of de analyse na het incident rekening houdt met modelhertraining, updates van veiligheidsfilters en de integratie van geleerde lessen in beveiligingsmaatregelen. |   3    | D/V |

---

## C12.5 Detectie van prestatieverslechtering van AI

Bewaken en detecteren van achteruitgang in de prestaties en kwaliteit van AI-modellen in de loop van de tijd.

|   #    | Beschrijving                                                                                                                                                   | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 12.5.1 | Controleer of de nauwkeurigheid, precisie, recall en F1-scores van het model continu worden gemonitord en vergeleken met de basisdrempels.                     |   1    | D/V |
| 12.5.2 | Bevestig dat data drift-detectie veranderingen in de inputverdeling bewaakt die de modelprestaties kunnen beïnvloeden.                                         |   1    | D/V |
| 12.5.3 | Controleer of concept drift-detectie veranderingen in de relatie tussen invoer en verwachte uitvoer detecteert.                                                |   2    | D/V |
| 12.5.4 | Verifieer dat prestatieverval geautomatiseerde waarschuwingen activeert en workflows voor het opnieuw trainen of vervangen van het model start.                |   2    | D/V |
| 12.5.5 | Verifieer dat de oorzaak-analyse van degradatie prestatieverminderingen correleert met veranderingen in gegevens, infrastructuurproblemen of externe factoren. |   3    |  V  |

---

## C12.6 DAG Visualisatie & Workflow Beveiliging

Bescherm workflowvisualisatiesystemen tegen informatielekken en manipulatie-aanvallen.

|   #    | Beschrijving                                                                                                                                                                    | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 12.6.1 | Controleer of de gegevens voor DAG-visualisatie worden gesanitiseerd om gevoelige informatie te verwijderen voordat ze worden opgeslagen of verzonden.                          |   1    | D/V |
| 12.6.2 | Controleer of de toegangscontroles voor workflowvisualisatie garanderen dat alleen geautoriseerde gebruikers de beslissingspaden van agenten en redeneersporen kunnen bekijken. |   1    | D/V |
| 12.6.3 | Verifieer dat de integriteit van DAG-gegevens wordt beschermd door cryptografische handtekeningen en manipulatiebestendige opslagmechanismen.                                   |   2    | D/V |
| 12.6.4 | Verifieer dat workflowvisualisatiesystemen invoervalidatie implementeren om injectie-aanvallen via speciaal vervaardigde knoop- of randgegevens te voorkomen.                   |   2    | D/V |
| 12.6.5 | Verifieer dat realtime DAG-updates worden gereguleerd qua snelheid en gevalideerd om denial-of-service-aanvallen op visualisatiesystemen te voorkomen.                          |   3    | D/V |

---

## C12.7 Proactieve monitoring van beveiligingsgedrag

Detectie en preventie van beveiligingsdreigingen door middel van proactieve analyse van agentgedrag.

|   #    | Beschrijving                                                                                                                                 | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 12.7.1 | Verifieer dat proactieve agentgedragingen worden beveiligingsgevalideerd voordat ze worden uitgevoerd, met integratie van risicobeoordeling. |   1    | D/V |
| 12.7.2 | Verifieer dat autonome initiatieftriggers beveiligingscontextevaluatie en beoordeling van het dreigingslandschap omvatten.                   |   2    | D/V |
| 12.7.3 | Controleer of proactieve gedrags- patronen worden geanalyseerd op mogelijke beveiligingsimplicaties en onbedoelde gevolgen.                  |   2    | D/V |
| 12.7.4 | Verifieer dat beveiligingskritieke proactieve acties expliciete goedkeuringsketens vereisen met auditsporen.                                 |   3    | D/V |
| 12.7.5 | Verifieer dat gedragsafwijkingsdetectie afwijkingen in proactieve agentpatronen identificeert die op compromittering kunnen duiden.          |   3    | D/V |

---

## Referenties

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)
* [EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R1689)

