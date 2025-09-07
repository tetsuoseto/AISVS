# 10 Tegenaanvalbestendigheid & Privacybescherming

## Beheersingsdoelstelling

Zorg ervoor dat AI-modellen betrouwbaar, privacybeschermend en bestand tegen misbruik blijven bij het omgaan met ontwijkings-, inferentie-, extractie- of vergiftigingsaanvallen.

---

## 10.1 Modelafstemming & Veiligheid

Waak tegen schadelijke of beleidschendende output.

|   #    | Beschrijving                                                                                                                                                        | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.1.1 | Verifieer dat een alignement testpakket (red-team prompts, jailbreak probes, niet-toegestane inhoud) versiebeheerd wordt en bij elke modelrelease wordt uitgevoerd. |   1    | D/V |
| 10.1.2 | Controleer of weigering en veilige-voltooiing beveiligingsmaatregelen worden gehandhaafd.                                                                           |   1    |  D  |
| 10.1.3 | Controleer of een geautomatiseerde beoordelaar het percentage schadelijke inhoud meet en regressies boven een bepaalde drempel markeert.                            |   2    | D/V |
| 10.1.4 | Controleer of tegen-jailbreaktraining gedocumenteerd en reproduceerbaar is.                                                                                         |   2    |  D  |
| 10.1.5 | Controleer of formele bewijsvoering van beleidsnaleving of gecertificeerde monitoring kritieke domeinen dekt.                                                       |   3    |  V  |

---

## 10.2 Versterking tegen tegenstandersvoorbeelden

Verhoog de veerkracht tegen gemanipuleerde inputs. Robuuste adversariële training en benchmarkbeoordeling zijn de huidige beste praktijk.

|   #    | Beschrijving                                                                                                                         | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 10.2.1 | Controleer of projectrepositories adversarial-trainingconfiguraties bevatten met reproduceerbare seeds.                              |   1    |  D  |
| 10.2.2 | Verifieer dat detectie van adversarial-examples blokkadewaarschuwingen veroorzaakt in productiepijplijnen.                           |   2    | D/V |
| 10.2.4 | Controleer of gecertificeerde robuustheidsbewijzen of intervalgrenscertificaten minimaal de belangrijkste kritieke klassen omvatten. |   3    |  V  |
| 10.2.5 | Verifieer dat regressietests adaptieve aanvallen gebruiken om te bevestigen dat er geen meetbaar verlies aan robuustheid is.         |   3    |  V  |

---

## 10.3 Beperking van lidmaatschapsinzicht

Beperk de mogelijkheid om te bepalen of een record in de trainingsgegevens zat. Differential privacy en maskering van confidence-scores blijven de meest effectieve bekende verdedigingsmethoden.

|   #    | Beschrijving                                                                                                                    | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.3.1 | Controleer of per-query entropieregulering of temperatuurschaling overmatige vertrouwen in voorspellingen vermindert.           |   1    |  D  |
| 10.3.2 | Verifieer dat training gebruikmaakt van ε-beperkte differentieel-private optimalisatie voor gevoelige datasets.                 |   2    |  D  |
| 10.3.3 | Controleer of aanvalssimulaties (shadow-model of black-box) een aanval AUC ≤ 0,60 laten zien op niet eerder gebruikte gegevens. |   2    |  V  |

---

## 10.4 Model-omkeringsbestendigheid

Voorkom reconstructie van private attributen. Recente onderzoeken benadrukken outputtruncatie en DP-garanties als praktische verdedigingsmaatregelen.

|   #    | Beschrijving                                                                                                               | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.4.1 | Verifieer dat gevoelige attributen nooit direct worden weergegeven; gebruik waar nodig buckets of eenrichtingsomzettingen. |   1    |  D  |
| 10.4.2 | Verifieer dat query-snelheidslimieten herhaalde adaptieve queries van dezelfde hoofdgebruiker beperken.                    |   1    | D/V |
| 10.4.3 | Controleer of het model is getraind met privacybeschermende ruis.                                                          |   2    |  D  |

---

## 10.5 Verdediging tegen model-extractie

Detecteer en voorkom ongeautoriseerd klonen. Watermerken en analyse van query-patronen worden aanbevolen.

|   #    | Beschrijving                                                                                                                                            | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.5.1 | Verifieer dat inferentie-gateways wereldwijde en per-API-sleutel snelheidslimieten afdwingen die zijn afgestemd op de memorisatiedrempel van het model. |   1    |  D  |
| 10.5.2 | Controleer of query-entropie en input-meervoudigheidsstatistieken een geautomatiseerde extractiedetector voeden.                                        |   2    | D/V |
| 10.5.3 | Verifieer dat fragiele of probabilistische watermerken kunnen worden bewezen met p < 0,01 in ≤ 1 000 queries tegen een vermoedelijke kloon.             |   2    |  V  |
| 10.5.4 | Verifieer dat watermerksleutels en trigger-sets zijn opgeslagen in een hardware-beveiligingsmodule en jaarlijks worden geroteerd.                       |   3    |  D  |
| 10.5.5 | Verifieer dat extraction-alert evenementen de overtredende queries bevatten en geïntegreerd zijn met incident-response draaiboeken.                     |   3    |  V  |

---

## 10.6 Detectie van Vergiftigde Gegevens tijdens de Inference-tijd

Identificeer en neutraliseer achterdeurs- of vergiftigde invoer.

|   #    | Beschrijving                                                                                                                                   | Niveau | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.6.1 | Verifieer dat invoer wordt gecontroleerd door een anomaliedetector (bijv. STRIP, consistentiescorering) voordat het model inferentie uitvoert. |   1    |  D  |
| 10.6.2 | Controleer of de detector drempels zijn afgestemd op schone/vervuilde validatiesets om minder dan 5% fout-positieven te bereiken.              |   1    |  V  |
| 10.6.3 | Controleer of invoer die als vergiftigd wordt gemarkeerd, zachte blokkering en workflows voor menselijke beoordeling activeert.                |   2    |  D  |
| 10.6.4 | Verifieer dat detectoren worden onderworpen aan stresstests met adaptieve, triggerloze backdoor-aanvallen.                                     |   2    |  V  |
| 10.6.5 | Controleer of detectie-efficiëntiemaatstaven worden vastgelegd en periodiek opnieuw worden geëvalueerd met nieuwe dreigingsinformatie.         |   3    |  D  |

---

## 10.7 Dynamische aanpassing van het beveiligingsbeleid

Realtime updates van beveiligingsbeleid op basis van dreigingsinformatie en gedragsanalyse.

|   #    | Beschrijving                                                                                                                                                                       | Niveau | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.7.1 | Controleer of beveiligingsbeleid dynamisch kan worden bijgewerkt zonder dat de agent opnieuw hoeft te worden gestart, terwijl de integriteit van de beleidsversie behouden blijft. |   1    | D/V |
| 10.7.2 | Verifieer dat beleidsupdates cryptografisch zijn ondertekend door geautoriseerd beveiligingspersoneel en worden gevalideerd voordat ze worden toegepast.                           |   2    | D/V |
| 10.7.3 | Controleer of dynamische beleidswijzigingen worden geregistreerd met volledige audittrails, inclusief rechtvaardiging, goedkeuringsketens en terugdraaiprocedures.                 |   2    | D/V |
| 10.7.4 | Controleer of adaptieve beveiligingsmechanismen de gevoeligheid van dreigingsdetectie aanpassen op basis van risicocontext en gedragsinzichten.                                    |   3    | D/V |
| 10.7.5 | Verifieer dat beleidsaanpassingsbeslissingen verklaarbaar zijn en bewijsstromen bevatten voor beoordeling door het beveiligingsteam.                                               |   3    | D/V |

---

## 10.8 Reflectie-gebaseerde Beveiligingsanalyse

Beveiligingsvalidatie via agent zelfreflectie en metacognitieve analyse.

|   #    | Beschrijving                                                                                                                                               | Niveau | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.8.1 | Controleer of agentreflectiemechanismen een op beveiliging gerichte zelfbeoordeling van beslissingen en acties omvatten.                                   |   1    | D/V |
| 10.8.2 | Controleer of reflectie-uitvoer wordt gevalideerd om manipulatie van zelfbeoordelingsmechanismen door vijandige invoer te voorkomen.                       |   2    | D/V |
| 10.8.3 | Verifieer dat meta-cognitieve beveiligingsanalyse potentiële vooringenomenheid, manipulatie of compromittering in agentredeneringsprocessen identificeert. |   2    | D/V |
| 10.8.4 | Verifieer dat op reflectie gebaseerde beveiligingswaarschuwingen geavanceerde monitoring en mogelijke menselijke interventieworkflows activeren.           |   3    | D/V |
| 10.8.5 | Verifieer dat continu leren van beveiligingsreflecties de bedreigingsdetectie verbetert zonder de legitieme functionaliteit te verminderen.                |   3    | D/V |

---

## 10.9 Evolutie & Zelfverbeteringsbeveiliging

Beveiligingscontroles voor agentensystemen die in staat zijn tot zelfmodificatie en evolutie.

|   #    | Beschrijving                                                                                                                            | Niveau | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.9.1 | Verifieer dat zelfmodificatiecapaciteiten beperkt zijn tot aangewezen veilige gebieden met formele verificatiegrenzen.                  |   1    | D/V |
| 10.9.2 | Verifieer dat evolutievoorstellen een veiligheidsbeoordeling ondergaan voordat ze worden geïmplementeerd.                               |   2    | D/V |
| 10.9.3 | Verifieer dat zelfverbeteringsmechanismen herstelopties bevatten met integriteitscontrole.                                              |   2    | D/V |
| 10.9.4 | Verifieer dat meta-learning beveiliging voorkomt dat verbetering algoritmen door tegenstanders worden gemanipuleerd.                    |   3    | D/V |
| 10.9.5 | Verifieer dat recursieve zelfverbetering beperkt wordt door formele veiligheidsbeperkingen met mathematische bewijzen van convergentie. |   3    | D/V |

---

### Referenties

* [MITRE ATLAS adversary tactics for ML](https://atlas.mitre.org/)
* [NIST AI Risk Management Framework 1.0, 2023](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [OWASP Top 10 for LLM Applications, 2025](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Adversarial Training: A Survey — Zhao et al., 2024](https://arxiv.org/abs/2410.15042)
* [RobustBench adversarial-robustness benchmark](https://robustbench.github.io/)
* [Membership-Inference & Model-Inversion Risk Survey, 2025](https://www.sciencedirect.com/science/article/abs/pii/S0950705125003867)
* [PURIFIER: Confidence-Score Defense against MI Attacks — AAAI 2023](https://ojs.aaai.org/index.php/AAAI/article/view/26289)
* [Model-Inversion Attacks & Defenses Survey — AI Review, 2025](https://link.springer.com/article/10.1007/s10462-025-11248-0)
* [Comprehensive Defense Framework Against Model Extraction — IEEE TDSC 2024](https://doi.org/10.1109/TDSC.2023.3261327)
* [Fragile Model Watermarking Survey — 2025](https://www.sciencedirect.com/science/article/abs/pii/S0165168425002026)
* [Data Poisoning in Deep Learning: A Survey — Zhao et al., 2025](https://arxiv.org/abs/2503.22759)
* [BDetCLIP: Multimodal Prompting Backdoor Detection — Niu et al., 2024](https://arxiv.org/abs/2405.15269)

