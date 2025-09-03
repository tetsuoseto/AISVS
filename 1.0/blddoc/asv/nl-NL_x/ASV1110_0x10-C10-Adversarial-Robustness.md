# 10 Adversarial robuustheid & privacybescherming

## Beheersdoel

Zorg ervoor dat AI-modellen betrouwbaar blijven, privacybeschermend en misbruikbestendig zijn bij ontwijkings-, inferentie-, extractie- of vergiftigingsaanvallen.

---

## 10.1 Modelafstemming en Veiligheid

Bescherm tegen schadelijke of beleidsbrekende uitvoer.

|   #    | Beschrijving                                                                                                                                                       | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 10.1.1 | Controleer of een afstemmings-test-suite (red-team prompts, jailbreak probes, verboden inhoud) onder versiebeheer staat en bij elke modeluitgave wordt uitgevoerd. |   1    | D/V |
| 10.1.2 | Controleer of afwijzing en beveiligingsrails voor veilige voltooiing worden afgedwongen.                                                                           |   1    |  D  |
| 10.1.3 | Controleer of een geautomatiseerde beoordelaar de mate van schadelijke inhoud meet en regressies signaleert die buiten een ingestelde drempel vallen.              |   2    | D/V |
| 10.1.4 | Controleer of counter-jailbreak training gedocumenteerd en reproduceerbaar is.                                                                                     |   2    |  D  |
| 10.1.5 | Verifieer dat formele bewijzen van beleidsconformiteit of gecertificeerde monitoring de kritieke domeinen afdekken.                                                |   3    |  V  |

---

## 10.2 Adversarial-Example Verharding

Verhoog de veerkracht tegen gemanipuleerde invoer. Robuuste adversarial-training en benchmarkbeoordeling zijn de huidige beste praktijk.

|   #    | Beschrijving                                                                                                                             | Niveau | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.2.1 | Controleer of de projectrepositories configuraties voor adversarial training met reproduceerbare zaden bevatten.                         |   1    |  D  |
| 10.2.2 | Controleer of detectie van adversarial-voorbeelden blokkeringswaarschuwingen activeert in productiepijplijnen.                           |   2    | D/V |
| 10.2.4 | Controleer of gecertificeerde robuustheidsbewijzen of intervalgrenzen-certificaten ten minste de belangrijkste kritische klassen dekken. |   3    |  V  |
| 10.2.5 | Controleer of regressietests adaptieve aanvallen gebruiken om aan te tonen dat er geen meetbaar verlies aan robuustheid is.              |   3    |  V  |

---

## 10.3 Lidmaatschaps-inferentie Mitigatie

Beperk het vermogen om te bepalen of een record in de trainingsdata aanwezig was. Differentiële privacy en het maskeren van betrouwbaarheidscores blijven de meest effectieve bekende verdedigingsmaatregelen.

|   #    | Beschrijving                                                                                                        | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.3.1 | Verifieer dat per-query entropie-regularisatie of temperatuurskalering overconfidente voorspellingen vermindert.    |   1    |  D  |
| 10.3.2 | Verifieer dat de training ε-gebonden differentiële privacy-optimalisatie toepast op gevoelige datasets.             |   2    |  D  |
| 10.3.3 | Verifieer dat aanvalssimulaties (shadow-model of black-box) de AUC van de aanval ≤ 0.60 tonen op hold-out-gegevens. |   2    |  V  |

---

## 10.4 Modelinversie-weerstand

Voorkom reconstructie van privé-attributen. Recente onderzoeken benadrukken uitvoertruncatie en DP-garanties als praktische verdedigingsmaatregelen.

|   #    | Beschrijving                                                                                                                          | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.4.1 | Controleer dat gevoelige attributen nooit rechtstreeks worden weergegeven; waar nodig gebruik buckets of eenrichtings-transformaties. |   1    |  D  |
| 10.4.2 | Verifieer dat de query-rate-limieten herhaalde adaptieve queries van dezelfde identiteit afremmen.                                    |   1    | D/V |
| 10.4.3 | Controleer of het model is getraind met privacybeschermende ruis.                                                                     |   2    |  D  |

---

## 10.5 Model-extractie verdediging

Ongeautoriseerde clonering detecteren en afschrikken. Watermarking en analyse van querypatronen worden aanbevolen.

|   #    | Beschrijving                                                                                                                                       | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.5.1 | Verifieer dat inferentie-gateways globale en per-API-sleutel limieten afdwingen die zijn afgestemd op de memorisatie-drempel van het model.        |   1    |  D  |
| 10.5.2 | Controleer of query-entropie en input-pluraliteit-statistieken een geautomatiseerde extractiedetector voeden.                                      |   2    | D/V |
| 10.5.3 | Bevestig dat fragiele of probabilistische watermerken kunnen worden bewezen met p < 0.01 in ≤ 1 000 queries tegen een verdachte kloon.             |   2    |  V  |
| 10.5.4 | Verifieer dat watermerk-sleutels en triggerverzamelingen in een hardware-beveiligingsmodule (HSM) worden opgeslagen en jaarlijks worden geroteerd. |   3    |  D  |
| 10.5.5 | Controleer of extraction-alert-evenementen de kwaadwillige zoekopdrachten bevatten en of ze zijn geïntegreerd met incident-response playbooks.     |   3    |  V  |

---

## 10.6 Inferentie-tijd vergiftigde gegevens detectie

Identificeer en neutraliseer invoer met een achterdeur of besmette invoer.

|   #    | Beschrijving                                                                                                                           | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.6.1 | Verifieer dat de invoer door een anomaliedetector gaat (bijv. STRIP, consistentie-score) voordat het model inferentie uitvoert.        |   1    |  D  |
| 10.6.2 | Controleer of de detectordrempels zijn afgesteld op schone en vergiftigde validatiesets om minder dan 5% valse positieven te bereiken. |   1    |  V  |
| 10.6.3 | Verifieer dat inputs die als vergiftigd gemarkeerd zijn soft-blocking en workflows voor menselijke beoordeling activeren.              |   2    |  D  |
| 10.6.4 | Verifieer dat detectoren onder stress getest worden met adaptieve, triggerloze achterdeur-aanvallen.                                   |   2    |  V  |
| 10.6.5 | Controleer of de detectie-effectiviteitsmetingen worden vastgelegd en periodiek opnieuw geëvalueerd met actuele dreigingsinformatie.   |   3    |  D  |

---

## 10.7 Dynamische beleidsaanpassing

Beveiligingsbeleidupdates in realtime op basis van dreigingsinformatie en gedragsanalyse.

|   #    | Beschrijving                                                                                                                                                  | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.7.1 | Verifieer dat beveiligingsbeleid dynamisch kan worden bijgewerkt zonder de agent te herstarten, terwijl de integriteit van de beleidsversies behouden blijft. |   1    | D/V |
| 10.7.2 | Verifieer dat beleidsupdates cryptografisch ondertekend zijn door geautoriseerd beveiligingspersoneel en vóór toepassing gevalideerd zijn.                    |   2    | D/V |
| 10.7.3 | Verifieer dat dynamische beleidswijzigingen worden vastgelegd met volledige auditsporen, inclusief motivering, goedkeuringsketens en terugrolprocedures.      |   2    | D/V |
| 10.7.4 | Controleer of adaptieve beveiligingsmechanismen de gevoeligheid voor dreigingsdetectie aanpassen op basis van risicocontext en gedragspatronen.               |   3    | D/V |
| 10.7.5 | Controleer of beleidsaanpassingsbeslissingen uitlegbaar zijn en zorg voor bewijssporen voor beoordeling door het beveiligingsteam.                            |   3    | D/V |

---

## 10.8 Reflectie-gebaseerde Beveiligingsanalyse

Beveiligingsvalidatie door agent-zelfreflectie en meta-cognitieve analyse.

|   #    | Beschrijving                                                                                                                                           | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 10.8.1 | Controleer of de reflectiemechanismen van agenten een veiligheidsgerichte zelfevaluatie van beslissingen en acties omvatten.                           |   1    | D/V |
| 10.8.2 | Verifieer dat reflectie-uitgangen gevalideerd worden om manipulatie van zelfbeoordelingsmechanismen door adversariale invoer te voorkomen.             |   2    | D/V |
| 10.8.3 | Controleer of meta-cognitive beveiligingsanalyse potentiële bias, manipulatie of compromittering identificeert in de redeneringsprocessen van agenten. |   2    | D/V |
| 10.8.4 | Verifieer dat reflectie-gebaseerde beveiligingswaarschuwingen zorgen voor versterkte bewaking en mogelijk workflows voor menselijke interventie.       |   3    | D/V |
| 10.8.5 | Controleer of continu leren uit beveiligingsreflecties de dreigingsdetectie verbetert zonder dat de legitieme functionaliteit wordt aangetast.         |   3    | D/V |

---

## 10.9 Evolutie & Zelfverbeteringsbeveiliging

Beveiligingscontroles voor agentensystemen die in staat zijn tot zelfmodificatie en evolutie.

|   #    | Beschrijving                                                                                                                       | Niveau | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.9.1 | Verifieer dat zelfmodificatie-mogelijkheden beperkt zijn tot aangewezen veilige gebieden met formele verificatiegrenzen.           |   1    | D/V |
| 10.9.2 | Verifieer dat evolutievoorstellen vóór implementatie een beveiligingsimpactbeoordeling ondergaan.                                  |   2    | D/V |
| 10.9.3 | Controleer of zelfverbeteringsmechanismen terugrolmogelijkheden bevatten met integriteitsverificatie.                              |   2    | D/V |
| 10.9.4 | Controleer of de beveiliging van meta-leren adversariële manipulatie van verbeteringsalgoritmen voorkomt.                          |   3    | D/V |
| 10.9.5 | Verifieer dat recursieve zelfverbetering begrensd is door formele veiligheidsbeperkingen met wiskundige bewijzen van convergentie. |   3    | D/V |

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

