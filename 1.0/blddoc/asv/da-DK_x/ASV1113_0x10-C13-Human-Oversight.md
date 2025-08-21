# C13 Menneskelig Tilsyn, Ansvarlighed & Styring

## Kontrolmål

Dette kapitel indeholder krav til at opretholde menneskelig overvågning og klare ansvarskæder i AI-systemer, hvilket sikrer forklarlighed, gennemsigtighed og etisk forvaltning gennem hele AI-livscyklussen.

---

## C13.1 Kill-Switch & Override-mekanismer

Sørg for nedluknings- eller tilbagestillingsmuligheder, når usikker adfærd i AI-systemet observeres.

|   #    | Beskrivelse                                                                                                             | Niveau | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 13.1.1 | Bekræft, at der findes en manuel driftsafbrydermekanisme til øjeblikkeligt at stoppe AI-modelinference og output.       |   1    |  D/V  |
| 13.1.2 | Bekræft, at tilsidesættelseskontroller kun er tilgængelige for autoriseret personale.                                   |   1    |   D   |
| 13.1.3 | Bekræft, at rollback-procedurer kan vende tilbage til tidligere modelversioner eller sikkerhedstilstandens operationer. |   3    |  D/V  |
| 13.1.4 | Sørg for, at overskrivningsmekanismer testes regelmæssigt.                                                              |   3    |   V   |

---

## C13.2 Menneske-i-løkken beslutningskontrolpunkter

Krav menneskelig godkendelse, når indsatsen overskrider foruddefinerede risikogrænser.

|   #    | Beskrivelse                                                                                                                                  | Niveau | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 13.2.1 | Bekræft, at højrisiko AI-beslutninger kræver eksplicit menneskelig godkendelse, før de udføres.                                              |   1    |  D/V  |
| 13.2.2 | Sørg for, at risikogrænser er klart definerede og automatisk udløser menneskelig gennemgangsarbejdsgang.                                     |   1    |   D   |
| 13.2.3 | Bekræft, at tidsfølsomme beslutninger har reservemetoder, når godkendelse fra mennesker ikke kan opnås inden for de krævede tidsrammer.      |   2    |   D   |
| 13.2.4 | Bekræft, at eskaleringsprocedurer definerer klare myndighedsniveauer for forskellige beslutningstyper eller risikokategorier, hvis relevant. |   3    |  D/V  |

---

## C13.3 Ansvarskæde og revisionsmulighed

Log operatørhandlinger og modelbeslutninger.

|   #    | Beskrivelse                                                                                                                           | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 13.3.1 | Bekræft, at alle AI-systembeslutninger og menneskelige indgreb logges med tidsstempler, brugeridentiteter og beslutningsbegrundelser. |   1    |  D/V  |
| 13.3.2 | Bekræft, at revisionslogfiler ikke kan manipuleres, og inkluder mekanismer til integritetsverifikation.                               |   2    |   D   |

---

## C13.4 Forklarlige AI-teknikker

Vigtighed af overfladefunktioner, kontra-faktiske eksempler og lokale forklaringer.

|   #    | Beskrivelse                                                                                                                                          | Niveau | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 13.4.1 | Sørg for, at AI-systemer giver grundlæggende forklaringer på deres beslutninger i et menneskeligt læsbart format.                                    |   1    |  D/V  |
| 13.4.2 | Bekræft, at forklaringskvaliteten er valideret gennem menneskelige evalueringsstudier og målinger.                                                   |   2    |   V   |
| 13.4.3 | Bekræft, at feature importance-scores eller attribueringsmetoder (SHAP, LIME osv.) er tilgængelige for kritiske beslutninger.                        |   3    |  D/V  |
| 13.4.4 | Bekræft, at kontrafaktiske forklaringer viser, hvordan input kan ændres for at ændre resultater, hvis det er relevant for brugstilfældet og domænet. |   3    |   V   |

---

## C13.5 Modelkort og brugsoplysninger

Vedligehold modelkort for tiltænkt anvendelse, præstationsmålinger og etiske overvejelser.

|   #    | Beskrivelse                                                                                                                                                                                        | Niveau | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 13.5.1 | Bekræft, at modelkort dokumenterer tilsigtede anvendelsestilfælde, begrænsninger og kendte fejlsituationer.                                                                                        |   1    |   D   |
| 13.5.2 | Bekræft, at ydelsesmålinger på tværs af forskellige relevante anvendelsestilfælde er oplyst.                                                                                                       |   1    |  D/V  |
| 13.5.3 | Bekræft, at etiske overvejelser, vurderinger af bias, evalueringer af retfærdighed, karakteristika ved træningsdata og kendte begrænsninger i træningsdata dokumenteres og opdateres regelmæssigt. |   2    |   D   |
| 13.5.4 | Bekræft, at modelkort er versionsstyrede og vedligeholdes gennem hele modellens livscyklus med ændringssporing.                                                                                    |   2    |  D/V  |

---

## C13.6 Usikkerhedskvantificering

Propagér konfidensscores eller entropimål i svarene.

|   #    | Beskrivelse                                                                                                      | Niveau | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 13.6.1 | Bekræft, at AI-systemer leverer tillidsvurderinger eller usikkerhedsmål sammen med deres output.                 |   1    |   D   |
| 13.6.2 | Bekræft, at usikkerhedsterskler udløser yderligere menneskelig gennemgang eller alternative beslutningsveje.     |   2    |  D/V  |
| 13.6.3 | Verificer, at metoder til usikkerhedskvantificering er kalibrerede og validerede mod grundlæggende sandhedsdata. |   2    |   V   |
| 13.6.4 | Bekræft, at usikkerhedspropagering opretholdes gennem flerstegs AI-arbejdsgange.                                 |   3    |  D/V  |

---

## C13.7 Brugervenlige gennemsigtighedsrapporter

Giv periodiske oplysninger om hændelser, drift og dataanvendelse.

|   #    | Beskrivelse                                                                                                                                | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 13.7.1 | Bekræft, at politikker for dataanvendelse og praksis for håndtering af brugeraccept klart kommunikeres til interessenter.                  |   1    |  D/V  |
| 13.7.2 | Bekræft, at AI-påvirkningsvurderinger udføres, og at resultaterne er inkluderet i rapporteringen.                                          |   2    |  D/V  |
| 13.7.3 | Bekræft, at gennemsigtighedsrapporter, der offentliggøres regelmæssigt, afslører AI-hændelser og operationelle målinger i rimelig detalje. |   2    |  D/V  |

### Referencer

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

