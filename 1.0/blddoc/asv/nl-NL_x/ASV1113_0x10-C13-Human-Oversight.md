# C13 Menselijk toezicht, verantwoording en Governance

## Beheersdoel

Dit hoofdstuk biedt vereisten voor het behoud van menselijk toezicht en duidelijke verantwoordingsketens in AI-systemen, en waarborgt uitlegbaarheid, transparantie en ethisch beheer gedurende de gehele AI-levenscyclus.

---

## C13.1 Kill-Switch & Override Mechanismen

Voorzie shutdown- of rollback-paden wanneer onveilig gedrag van het AI-systeem wordt waargenomen.

|   #    | Beschrijving                                                                                                                          | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 13.1.1 | Verifieer of er een handmatig kill-switch-mechanisme bestaat om onmiddellijk de inferentie van het AI-model en de uitvoer te stoppen. |   1    | D/V |
| 13.1.2 | Controleer of override-controles alleen toegankelijk zijn voor geautoriseerd personeel.                                               |   1    |  D  |
| 13.1.3 | Controleer of rollback-procedures kunnen terugkeren naar eerdere modelversies of operaties in de veilige modus.                       |   3    | D/V |
| 13.1.4 | Controleer of override-mechanismen regelmatig worden getest.                                                                          |   3    |  V  |

---

## C13.2 Mens-in-de-lus Beslissingspunten

Vereis menselijke goedkeuringen wanneer de inzet de voorgedefinieerde risicogrensen overschrijdt.

|   #    | Beschrijving                                                                                                                                             | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 13.2.1 | Controleer of AI-beslissingen met hoog risico expliciete menselijke goedkeuring vereisen voordat ze worden uitgevoerd.                                   |   1    | D/V |
| 13.2.2 | Controleer of de risicodrempels duidelijk gedefinieerd zijn en automatisch menselijke beoordelingsworkflows activeren.                                   |   1    |  D  |
| 13.2.3 | Verifieer of tijdkritische beslissingen terugvalprocedures hebben wanneer menselijke goedkeuring niet binnen de vereiste termijnen kan worden verkregen. |   2    |  D  |
| 13.2.4 | Controleer of escalatieprocedures duidelijke bevoegdheidsniveaus definiëren voor verschillende besluittypen of risicocategorieën, indien van toepassing. |   3    | D/V |

---

## C13.3 Verantwoordelijkheidsketen en Auditbaarheid

Registreer de acties van de operator en de beslissingen van het model.

|   #    | Beschrijving                                                                                                                                          | Niveau | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 13.3.1 | Verifieer dat alle AI-systeembeslissingen en menselijke ingrepen worden vastgelegd met tijdstempels, gebruikersidentiteiten en de beslissingsredenen. |   1    | D/V |
| 13.3.2 | Controleer of auditlogboeken niet kunnen worden gemanipuleerd en voeg integriteitsverificatiemechanismen toe.                                         |   2    |  D  |

---

## C13.4 Uitlegbare AI-technieken

Belang van oppervlaktekenmerken, tegenfeitelijke scenario's en lokale verklaringen.

|   #    | Beschrijving                                                                                                                                                                              | Niveau | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 13.4.1 | Controleer of AI-systemen basisverklaringen geven voor hun beslissingen in een voor mensen leesbaar formaat.                                                                              |   1    | D/V |
| 13.4.2 | Verifieer dat de kwaliteit van de uitleg wordt gevalideerd door middel van menselijke evaluatiestudies en metrische evaluaties.                                                           |   2    |  V  |
| 13.4.3 | Controleer of de scores voor het belang van kenmerken of attributiemethoden (SHAP, LIME, enz.) beschikbaar zijn voor cruciale beslissingen.                                               |   3    | D/V |
| 13.4.4 | Verifieer dat contrafactuele toelichtingen laten zien hoe invoerwaarden gewijzigd kunnen worden om uitkomsten te veranderen, indien van toepassing op het toepassingsgeval en het domein. |   3    |  V  |

---

## C13.5 Modelkaarten & Gebruikverklaringen

Onderhoud modelkaarten voor het beoogde gebruik, prestatiemaatstaven en ethische overwegingen.

|   #    | Beschrijving                                                                                                                                                                                                    | Niveau | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 13.5.1 | Verifieer of modelkaarten de beoogde toepassingsgevallen, beperkingen en bekende faalmodi documenteren.                                                                                                         |   1    |  D  |
| 13.5.2 | Controleer of de prestatiemetrieken over verschillende toepassingsgevallen worden bekendgemaakt.                                                                                                                |   1    | D/V |
| 13.5.3 | Verifieer dat ethische overwegingen, biasbeoordelingen, eerlijkheidsbeoordelingen, kenmerken van trainingsgegevens en bekende beperkingen van trainingsgegevens gedocumenteerd en regelmatig bijgewerkt worden. |   2    |  D  |
| 13.5.4 | Controleer of modelkaarten onder versiebeheer staan en gedurende de levenscyclus van het model worden onderhouden met wijzigingsregistratie.                                                                    |   2    | D/V |

---

## C13.6 Onzekerheidskwantificatie

Verwerk betrouwbaarheidscores of entropiemetingen in antwoorden.

|   #    | Beschrijving                                                                                                       | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 13.6.1 | Verifieer dat AI-systemen vertrouwensscores of onzekerheidsmetingen bij hun uitvoer leveren.                       |   1    |  D  |
| 13.6.2 | Controleer of de onzekerheidsdrempels extra menselijke beoordeling of alternatieve besluitvormingspaden activeren. |   2    | D/V |
| 13.6.3 | Controleer of onzekerheidskwantificatiemethoden gekalibreerd en gevalideerd zijn tegen grondwaarheidsgegevens.     |   2    |  V  |
| 13.6.4 | Controleer of de onzekerheidspropagatie behouden blijft in AI-workflows met meerdere stappen.                      |   3    | D/V |

---

## C13.7 Gebruikersgerichte transparantieverslagen

Geef periodieke openbaarmakingen over incidenten, drift en gegevensgebruik.

|   #    | Beschrijving                                                                                                                                                     | Niveau | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 13.7.1 | Controleer of het beleid voor gegevensgebruik en de praktijken voor het beheer van gebruikerstoestemmingen duidelijk aan de belanghebbenden zijn gecommuniceerd. |   1    | D/V |
| 13.7.2 | Verifieer of AI-impactbeoordelingen worden uitgevoerd en of de resultaten in de rapportage zijn opgenomen.                                                       |   2    | D/V |
| 13.7.3 | Controleer of transparantierapporten die regelmatig worden gepubliceerd AI-incidenten en operationele statistieken in redelijke detail bekendmaken.              |   2    | D/V |

### Referenties

* [EU Artificial Intelligence Act — Regulation (EU) 2024/1689 (Official Journal, 12 July 2024)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj)
* [ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management](https://www.iso.org/standard/77304.html)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [NIST SP 800-53 Revision 5 — Security and Privacy Controls](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r5.pdf)
* [A Unified Approach to Interpreting Model Predictions (SHAP, ICML 2017)](https://arxiv.org/abs/1705.07874)
* [Model Cards for Model Reporting (Mitchell et al., 2018)](https://arxiv.org/abs/1810.03993)
* [Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning (Gal & Ghahramani, 2016)](https://arxiv.org/abs/1506.02142)
* [ISO/IEC 24029-2:2023 — Robustness of Neural Networks — Methodology for Formal Methods](https://www.iso.org/standard/79804.html)
* [IEEE 7001-2021 — Transparency of Autonomous Systems](https://standards.ieee.org/ieee/7001/6929/)
* [GDPR — Article 5 "Transparency Principle" (Regulation (EU) 2016/679)](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX%3A32016R0679)
* [Human Oversight under Article 14 of the EU AI Act (Fink, 2025)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5147196)

