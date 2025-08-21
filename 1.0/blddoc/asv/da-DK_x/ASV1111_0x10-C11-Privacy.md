# 11 Beskyttelse af privatliv og håndtering af persondata

## Kontrolmål

Oprethold strenge privatlivsgarantier gennem hele AI-livscyklussen—indsamling, træning, inferens og hændelsesrespons—så persondata kun behandles med klart samtykke, minimalt nødvendigt omfang, beviselig sletning og formelle privatlivsgarantier.

---

## 11.1 Anonymisering og dataminimering

|   #    | Beskrivelse                                                                                                                                               | Niveau | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 11.1.1 | Bekræft, at direkte og kvasi-identifikatorer er fjernet eller hash'et.                                                                                    |   1    |  D/V  |
| 11.1.2 | Bekræft, at automatiserede revisioner måler k-anonymitet/l-diversitet og alarmerer, når tærskler falder under politikken.                                 |   2    |  D/V  |
| 11.1.3 | Bekræft, at model-attributevigtighedsrapporter beviser, at der ikke er nogen identificeringslækage ud over ε = 0.01 gensidig information.                 |   2    |   V   |
| 11.1.4 | Bekræft, at formelle beviser eller certificering baseret på syntetiske data viser, at risikoen for genidentifikation er ≤ 0,05 selv under koblingsangreb. |   3    |   V   |

---

## 11.2 Ret-og-at-blive-glemt & Håndhævelse af sletning

|   #    | Beskrivelse                                                                                                                                                      | Niveau | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 11.2.1 | Bekræft, at sletningsanmodninger for dataemner forplanter sig til rå datasæt, checkpoints, embeddings, logs og backup inden for serviceaftaler på under 30 dage. |   1    |  D/V  |
| 11.2.2 | Bekræft, at "machine-unlearning" rutiner fysisk gentræner eller tilnærmer fjernelse ved hjælp af certificerede unlearning-algoritmer.                            |   2    |   D   |
| 11.2.3 | Bekræft, at evaluering af shadow-modellen beviser, at slettede poster påvirker mindre end 1% af outputtene efter unlearning.                                     |   2    |   V   |
| 11.2.4 | Bekræft, at slettebegivenheder bliver uforanderligt logget og kan revideres for regulatorer.                                                                     |   3    |   V   |

---

## 11.3 Differential-Privacy-sikkerhedsforanstaltninger

|   #    | Beskrivelse                                                                                                                | Niveau | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 11.3.1 | Bekræft, at overvågningspaneler for privatlivs-tab-rapportering giver advarsel, når kumulativ ε overskrider policygrænser. |   2    |  D/V  |
| 11.3.2 | Bekræft, at black-box privatlivsaudits estimerer ε̂ inden for 10% af den erklærede værdi.                                  |   2    |   V   |
| 11.3.3 | Bekræft, at formelle beviser dækker alle efter-trænings finjusteringer og indlejringer.                                    |   3    |   V   |

---

## 11.4 Formålsbegrænsning & Beskyttelse mod omfangsspredning

|   #    | Beskrivelse                                                                                                                               | Niveau | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 11.4.1 | Bekræft, at hvert datasæt og model-checkpoint bærer et maskinlæsbart formåls-tag, der er i overensstemmelse med den oprindelige samtykke. |   1    |   D   |
| 11.4.2 | Bekræft, at runtime-overvågninger opdager forespørgsler, der er inkonsistente med det deklarerede formål, og udløser blød afvisning.      |   1    |  D/V  |
| 11.4.3 | Bekræft, at policy-as-code-gates blokerer genudrulning af modeller til nye domæner uden DPIA-gennemgang.                                  |   3    |   D   |
| 11.4.4 | Bekræft, at formelle sporbarhedsbeviser viser, at hele livscyklussen for personlige data forbliver inden for det givne samtykkeområde.    |   3    |   V   |

---

## 11.5 Samtykkestyring og juridisk grundlag for tracking

|   #    | Beskrivelse                                                                                                                | Niveau | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 11.5.1 | Bekræft, at en samtykkestyringsplatform (CMP) registrerer tilmeldingsstatus, formål og opbevaringsperiode pr. datasubjekt. |   1    |  D/V  |
| 11.5.2 | Bekræft, at API'er udsender samtykke-tokens; modeller skal validere token-omfanget før inferens.                           |   2    |   D   |
| 11.5.3 | Bekræft, at afvist eller tilbagetrukket samtykke stopper behandlingspipeline inden for 24 timer.                           |   2    |  D/V  |

---

## 11.6 Fødereret læring med privatlivskontrol

|   #    | Beskrivelse                                                                                        | Niveau | Rolle |
| :----: | -------------------------------------------------------------------------------------------------- | :----: | :---: |
| 11.6.1 | Bekræft, at klientopdateringer anvender lokal differentialprivacy-støjtilføjelse før aggregering.  |   1    |   D   |
| 11.6.2 | Bekræft, at træningsmålinger er differentielt private og aldrig afslører tab for en enkelt klient. |   2    |  D/V  |
| 11.6.3 | Bekræft, at forgiftningsresistent aggregering (f.eks. Krum/Trimmet-Middel) er aktiveret.           |   2    |   V   |
| 11.6.4 | Bekræft, at formelle beviser viser et samlet ε-budget med mindre end 5 nyttetab.                   |   3    |   V   |

---

### Referencer

* [GDPR & AI Compliance Best Practices](https://www.exabeam.com/explainers/gdpr-compliance/the-intersection-of-gdpr-and-ai-and-6-compliance-best-practices/)
* [EU Parliament Study on GDPR & AI, 2020](https://www.europarl.europa.eu/RegData/etudes/STUD/2020/641530/EPRS_STU%282020%29641530_EN.pdf)
* [ISO 31700-1:2023 — Privacy by Design for Consumer Products](https://www.iso.org/standard/84977.html)
* [NIST Privacy Framework 1.1 (2025 Draft)](https://www.nist.gov/privacy-framework)
* [Machine Unlearning: Right-to-Be-Forgotten Techniques](https://www.kaggle.com/code/tamlhp/machine-unlearning-the-right-to-be-forgotten)
* [A Survey of Machine Unlearning, 2024](https://arxiv.org/html/2209.02299v6)
* [Auditing DP-SGD — ArXiv 2024](https://arxiv.org/html/2405.14106v4)
* [DP-SGD Explained — PyTorch Blog](https://medium.com/pytorch/differential-privacy-series-part-1-dp-sgd-algorithm-explained-12512c3959a3)
* [Purpose-Limitation for AI — IJLIT 2025](https://academic.oup.com/ijlit/article/doi/10.1093/ijlit/eaaf003/8121663)
* [Data-Protection Considerations for AI — URM Consulting](https://www.urmconsulting.com/blog/data-protection-considerations-for-artificial-intelligence-ai)
* [Top Consent-Management Platforms, 2025](https://www.enzuzo.com/blog/best-consent-management-platforms)
* [Secure Aggregation in DP Federated Learning — ArXiv 2024](https://arxiv.org/abs/2407.19286)

