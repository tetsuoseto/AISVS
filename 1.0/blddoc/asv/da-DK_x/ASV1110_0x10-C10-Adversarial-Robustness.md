# 10 Modstandsdygtighed over for angreb og privatlivsbeskyttelse

## Kontrolmål

Sørg for, at AI-modeller forbliver pålidelige, privatlivsbevarende og modstandsdygtige over for misbrug, når de udsættes for undvigelses-, inferens-, udtræknings- eller forgiftningsangreb.

---

## 10.1 Modeljustering og sikkerhed

Beskyt mod skadelige eller politikovertrædende output.

|   #    | Beskrivelse                                                                                                                                            | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 10.1.1 | Bekræft, at en testsuite for alignment (red-team prompts, jailbreak probes, forbudt indhold) er versionskontrolleret og køres ved hver modeludgivelse. |   1    |  D/V  |
| 10.1.2 | Bekræft, at afvisnings- og sikker-afslutnings-sikkerhedsforanstaltninger håndhæves.                                                                    |   1    |   D   |
| 10.1.3 | Bekræft, at en automatiseret evaluator måler graden af skadeligt indhold og markerer regressionsændringer, der overstiger en fastsat tærskel.          |   2    |  D/V  |
| 10.1.4 | Bekræft, at counter-jailbreak-træning er dokumenteret og reproducerbar.                                                                                |   2    |   D   |
| 10.1.5 | Bekræft, at formelle beviser for overholdelse af politikker eller certificeret overvågning dækker kritiske domæner.                                    |   3    |   V   |

---

## 10.2 Modstandsdygtighed over for modstridende eksempler

Øg modstandsdygtigheden over for manipulerede input. Robust modstandertræning og benchmarkscoring er den nuværende bedste praksis.

|   #    | Beskrivelse                                                                                                           | Niveau | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 10.2.1 | Bekræft, at projektrepositories inkluderer adversarial-træningskonfigurationer med reproducerbare frø.                |   1    |   D   |
| 10.2.2 | Bekræft, at detektionssystemet for fjendtlige eksempler udløser blokeringsadvarsler i produktionspipelines.           |   2    |  D/V  |
| 10.2.4 | Bekræft, at certificerede robusthedsbeviser eller interval-grænsecertifikater dækker mindst de mest kritiske klasser. |   3    |   V   |
| 10.2.5 | Bekræft, at regressions tests bruger adaptive angreb for at bekræfte, at der ikke er noget målbar tab af robusthed.   |   3    |   V   |

---

## 10.3 Medlemskabsinferenceafværgelse

Begræns muligheden for at afgøre, om en post var i træningsdataene. Differential privacy og maskering af konfidensscore forbliver de mest effektive kendte forsvar.

|   #    | Beskrivelse                                                                                                  | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 10.3.1 | Bekræft, at entropiregulering pr. forespørgsel eller temperaturskalering reducerer overmodige forudsigelser. |   1    |   D   |
| 10.3.2 | Bekræft, at træning anvender ε-begrænset differentialt privat optimering for følsomme datasæt.               |   2    |   D   |
| 10.3.3 | Bekræft, at angrebssimuleringer (shadow-model eller black-box) viser angrebs AUC ≤ 0,60 på hold-out data.    |   2    |   V   |

---

## 10.4 Modstand mod modelinversion

Forhindre rekonstruktion af private attributter. Nylige undersøgelser understreger output-trunkering og DP-garantier som praktiske forsvar.

|   #    | Beskrivelse                                                                                                                | Niveau | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 10.4.1 | Bekræft, at følsomme attributter aldrig udskrives direkte; hvor det er nødvendigt, brug segmenter eller envejsomdannelser. |   1    |   D   |
| 10.4.2 | Bekræft, at forespørgselsrater begrænser gentagne adaptive forespørgsler fra samme principal.                              |   1    |  D/V  |
| 10.4.3 | Bekræft, at modellen er trænet med privatlivsbevarende støj.                                                               |   2    |   D   |

---

## 10.5 Model-Uddragelsesforsvar

Opdag og forhindre uautoriseret kloning. Vandmærkning og analyse af forespørgselsmønstre anbefales.

|   #    | Beskrivelse                                                                                                                          | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 10.5.1 | Bekræft, at inferens-gateways håndhæver globale og per-API-nøgle ratebegrænsninger, som er tilpasset modellens memoriseringstærskel. |   1    |   D   |
| 10.5.2 | Bekræft, at statistikkerne for forespørgselsentropi og input-flertal fodrer en automatiseret ekstraktionsdetektor.                   |   2    |  D/V  |
| 10.5.3 | Bekræft, at skrøbelige eller probabilistiske vandmærker kan bevises med p < 0,01 i ≤ 1 000 forespørgsler mod en mistænkt klon.       |   2    |   V   |
| 10.5.4 | Bekræft, at watermark-nøgler og trigger-sæt opbevares i en hardware-sikkerhedsmodul og roteres årligt.                               |   3    |   D   |
| 10.5.5 | Bekræft, at extraction-alert-hændelser inkluderer de problematiske forespørgsler og er integreret med incident-response playbooks.   |   3    |   V   |

---

## 10.6 Detektion af forgiftede data ved inferenstidspunktet

Identificer og neutraliser bagdørs- eller forgiftede input.

|   #    | Beskrivelse                                                                                                            | Niveau | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 10.6.1 | Bekræft, at inputs passerer gennem en anomali-detektor (f.eks. STRIP, konsistensscoring) før modelinference.           |   1    |   D   |
| 10.6.2 | Bekræft, at detektortærskler er justeret på rene/forurenede valideringssæt for at opnå mindre end 5% falske positiver. |   1    |   V   |
| 10.6.3 | Bekræft, at input, der er markeret som forgiftede, udløser blød blokering og menneskelig gennemgangsarbejdsgange.      |   2    |   D   |
| 10.6.4 | Bekræft, at detektorer er stress-testet med adaptive, triggerløse bagdørsangreb.                                       |   2    |   V   |
| 10.6.5 | Bekræft, at målinger af detektions effektivitet logges og periodisk genvurderes med frisk trusselinformation.          |   3    |   D   |

---

## 10.7 Dynamisk tilpasning af sikkerhedspolitik

Opdateringer af sikkerhedspolitikker i realtid baseret på trusselsintelligens og adfærdsanalyse.

|   #    | Beskrivelse                                                                                                                                  | Niveau | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 10.7.1 | Bekræft, at sikkerhedspolitikker kan opdateres dynamisk uden genstart af agenten, samtidig med at politikversionens integritet opretholdes.  |   1    |  D/V  |
| 10.7.2 | Bekræft, at politikopdateringer er kryptografisk underskrevet af autoriseret sikkerhedspersonale og valideret, før de anvendes.              |   2    |  D/V  |
| 10.7.3 | Bekræft, at dynamiske politikændringer logges med fulde revisionsspor, inklusive begrundelse, godkendelseskæder og tilbageførselsprocedurer. |   2    |  D/V  |
| 10.7.4 | Bekræft, at adaptive sikkerhedsmekanismer justerer trusselsdetektionsfølsomheden baseret på risikokontekst og adfærdsmønstre.                |   3    |  D/V  |
| 10.7.5 | Bekræft, at beslutninger om politiktilpasning er forklarlige og indeholder bevisspor til gennemgang af sikkerhedsteamet.                     |   3    |  D/V  |

---

## 10.8 Reflektionsbaseret sikkerhedsanalyse

Sikkerhedsvalidering gennem agentens selvrefleksion og meta-kognitiv analyse.

|   #    | Beskrivelse                                                                                                                                    | Niveau | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 10.8.1 | Bekræft, at agentrefleksionsmekanismer inkluderer sikkerhedsorienteret selvevaluering af beslutninger og handlinger.                           |   1    |  D/V  |
| 10.8.2 | Sørg for, at refleksionsudgange bliver valideret for at forhindre manipulation af selvvurderingsmekanismer ved hjælp af modstridende input.    |   2    |  D/V  |
| 10.8.3 | Bekræft, at meta-kognitiv sikkerhedsanalyse identificerer potentiel bias, manipulation eller kompromittering i agenters ræsonneringsprocesser. |   2    |  D/V  |
| 10.8.4 | Bekræft, at sikkerhedsadvarsler baseret på refleksion udløser forbedret overvågning og potentielle arbejdsgange for menneskelig indgriben.     |   3    |  D/V  |
| 10.8.5 | Bekræft, at kontinuerlig læring fra sikkerhedsrefleksioner forbedrer trusselsdetektion uden at forringe legitim funktionalitet.                |   3    |  D/V  |

---

## 10.9 Evolution & Selvforbedringssikkerhed

Sikkerhedskontroller for agentsystemer med evne til selvmodifikation og udvikling.

|   #    | Beskrivelse                                                                                                                | Niveau | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 10.9.1 | Bekræft, at evnen til selvmodifikation er begrænset til udpegede sikre områder med formelle verifikationsgrænser.          |   1    |  D/V  |
| 10.9.2 | Sørg for, at evolutionsforslag gennemgår en sikkerhedsvurdering, før de implementeres.                                     |   2    |  D/V  |
| 10.9.3 | Bekræft, at selvforbedringsmekanismer inkluderer rollback-funktioner med integritetsverifikation.                          |   2    |  D/V  |
| 10.9.4 | Bekræft, at meta-læringssikkerhed forhindrer fjendtlig manipulation af forbedringsalgoritmer.                              |   3    |  D/V  |
| 10.9.5 | Verificer, at rekursiv selvforbedring er begrænset af formelle sikkerhedskriterier med matematiske beviser for konvergens. |   3    |  D/V  |

---

### Referencer

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

