# C13 Menselijk Toezicht, Verantwoordingsplicht & Bestuur

## Beheersingsdoelstelling

Dit hoofdstuk bevat vereisten voor het behouden van menselijke controle en duidelijke verantwoordingsketens in AI-systemen, waarbij uitlegbaarheid, transparantie en ethisch beheer tijdens de hele AI-levenscyclus worden gewaarborgd.

---

## C13.1 Noodstop- & Override-Mechanismen

Bied uitschakel- of terugdraaiopties aan wanneer onveilig gedrag van het AI-systeem wordt waargenomen.

|   #    | Beschrijving                                                                                                               | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 13.1.1 | Controleer of er een handmatig noodstopmechanisme aanwezig is om de AI-modelinferenzie en uitvoer onmiddellijk te stoppen. |   1    | D/V |
| 13.1.2 | Controleer of override-voorzieningen alleen toegankelijk zijn voor geautoriseerd personeel.                                |   1    |  D  |
| 13.1.3 | Controleer of rollback-procedures kunnen terugkeren naar eerdere modelversies of veilige-modusoperaties.                   |   3    | D/V |
| 13.1.4 | Controleer of override-mechanismen regelmatig worden getest.                                                               |   3    |  V  |

---

## C13.2 Beslispunten met Mens-in-de-Lus

Vereis menselijke goedkeuringen wanneer de inzetten vooraf gedefinieerde risicodrempels overschrijden.

|   #    | Beschrijving                                                                                                                                                           | Niveau | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 13.2.1 | Verifieer dat AI-beslissingen met hoog risico expliciete menselijke goedkeuring vereisen voordat ze worden uitgevoerd.                                                 |   1    | D/V |
| 13.2.2 | Controleer of risicodrempels duidelijk zijn gedefinieerd en automatisch menselijke beoordelingsworkflows activeren.                                                    |   1    |  D  |
| 13.2.3 | Verifieer dat tijdgevoelige beslissingen noodprocedures hebben wanneer menselijke goedkeuring niet binnen de vereiste tijdsbestekken kan worden verkregen.             |   2    |  D  |
| 13.2.4 | Controleer of escalatieprocedures duidelijke bevoegdheidsniveaus vastleggen voor verschillende besluitvormingscategorieën of risicocategorieën, indien van toepassing. |   3    | D/V |

---

## C13.3 Keten van Verantwoordelijkheid & Controleerbaarheid

Log operatoracties en modelbeslissingen.

|   #    | Beschrijving                                                                                                                                                               | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 13.3.1 | Controleer of alle beslissingen van het AI-systeem en menselijke interventies worden geregistreerd met tijdstempels, gebruikersidentiteiten en de reden van de beslissing. |   1    | D/V |
| 13.3.2 | Controleer of auditlogs niet kunnen worden aangepast en of er mechanismen voor integriteitsverificatie zijn opgenomen.                                                     |   2    |  D  |

---

## C13.4 Uitlegbare-AI Technieken

Belang van oppervlaktekenmerken, tegenfeitelijke voorbeelden en lokale verklaringen.

|   #    | Beschrijving                                                                                                                                                           | Niveau | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 13.4.1 | Controleer of AI-systemen basisuitleg geven voor hun beslissingen in een voor mensen leesbaar formaat.                                                                 |   1    | D/V |
| 13.4.2 | Verifieer dat de kwaliteit van de uitleg wordt gevalideerd door middel van menselijke evaluatiestudies en -metingen.                                                   |   2    |  V  |
| 13.4.3 | Verifieer dat scores voor feature-importance of attributiemethoden (SHAP, LIME, enz.) beschikbaar zijn voor kritieke beslissingen.                                     |   3    | D/V |
| 13.4.4 | Controleer of contra-feitelijke verklaringen laten zien hoe invoer kan worden aangepast om resultaten te wijzigen, indien van toepassing op de use-case en het domein. |   3    |  V  |

---

## C13.5 Modelkaarten & Gebruiksverklaringen

Onderhoud modelkaarten voor beoogd gebruik, prestatiemaatstaven en ethische overwegingen.

|   #    | Beschrijving                                                                                                                                                                                                  | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 13.5.1 | Controleer of modelkaarten de beoogde gebruikssituaties, beperkingen en bekende faalmodi documenteren.                                                                                                        |   1    |  D  |
| 13.5.2 | Verifieer dat prestatie-indicatoren voor verschillende toepasselijke gebruiksscenario's worden bekendgemaakt.                                                                                                 |   1    | D/V |
| 13.5.3 | Verifieer dat ethische overwegingen, bias-beoordelingen, eerlijkheidsevaluaties, kenmerken van trainingsgegevens en bekende beperkingen van trainingsgegevens gedocumenteerd en regelmatig bijgewerkt worden. |   2    |  D  |
| 13.5.4 | Controleer of modelkaarten versiebeheerd zijn en gedurende de gehele levenscyclus van het model worden onderhouden met wijzigingsregistratie.                                                                 |   2    | D/V |

---

## C13.6 Kwantificering van onzekerheid

Verspreid betrouwbaarheidscores of entropiematen in antwoorden.

|   #    | Beschrijving                                                                                                                   | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 13.6.1 | Controleer of AI-systemen betrouwbaarheidscores of onzekerheidsmaten bij hun output leveren.                                   |   1    |  D  |
| 13.6.2 | Controleer of onzekerheidsdrempels extra menselijke beoordeling of alternatieve besluitvormingspaden activeren.                |   2    | D/V |
| 13.6.3 | Controleer of methoden voor onzekerheidskwantificatie zijn gekalibreerd en gevalideerd aan de hand van grondwaarheidsgegevens. |   2    |  V  |
| 13.6.4 | Verifieer dat onzekerheidspropagatie behouden blijft door multi-stap AI-werkstromen.                                           |   3    | D/V |

---

## C13.7 Transparantieverslagen voor gebruikers

Geef periodieke openbaarmakingen over incidenten, afwijkingen en datagebruik.

|   #    | Beschrijving                                                                                                                                                  | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 13.7.1 | Controleer of het gebruik van gegevensbeleid en praktijken voor het beheren van gebruikersconsent duidelijk worden gecommuniceerd aan belanghebbenden.        |   1    | D/V |
| 13.7.2 | Verifieer dat AI-impactbeoordelingen worden uitgevoerd en dat de resultaten worden opgenomen in de rapportage.                                                |   2    | D/V |
| 13.7.3 | Controleer of transparantierapporten die regelmatig worden gepubliceerd, AI-incidenten en operationele statistieken in redelijke mate van detail bekendmaken. |   2    | D/V |

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

