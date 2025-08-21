# C6 Forsyningskædesikkerhed for Modeller, Frameworks & Data

## Kontrolmål

AI-forsyningskædeangreb udnytter tredjepartsmodeller, -rammer eller -datasæt til at indlejre bagdøre, bias eller udnyttelig kode. Disse kontroller tilbyder ende-til-ende oprindelsesoplysninger, sårbarhedsstyring og overvågning for at beskytte hele modellens livscyklus.

---

## C6.1 Forhåndstrænet Model Vurdering & Oprindelse

Vurder og godkend tredjeparts modelers oprindelse, licenser og skjulte adfærd, før der foretages finjustering eller implementering.

|   #   | Beskrivelse                                                                                                                                           | Niveau | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 6.1.1 | Bekræft, at hvert tredjeparts modelartefakt inkluderer en underskrevet oprindelsesregistrering, der identificerer kildearkivet og commit-hashen.      |   1    |  D/V  |
| 6.1.2 | Bekræft, at modeller bliver scannet for ondsindede lag eller Trojan-udløsere ved hjælp af automatiserede værktøjer før import.                        |   1    |  D/V  |
| 6.1.3 | Bekræft, at transfer-learning finjusterer og består adversarial evaluering for at opdage skjulte adfærd.                                              |   2    |   D   |
| 6.1.4 | Bekræft, at modellicenser, eksportkontrolmærker og dataoprindelseserklæringer er registreret i en ML-BOM-post.                                        |   2    |   V   |
| 6.1.5 | Bekræft, at højrisikomodeller (offentligt uploadede vægte, uverificerede skabere) forbliver i karantæne indtil menneskelig gennemgang og godkendelse. |   3    |  D/V  |

---

## C6.2 Framework- og biblioteks-scanning

Skann løbende ML-rammeværk og biblioteker for CVE'er og ondsindet kode for at holde runtime-stakken sikker.

|   #   | Beskrivelse                                                                                                                  | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 6.2.1 | Bekræft, at CI-pipelines kører afhængighedsscannere på AI-rammeværk og kritiske biblioteker.                                 |   1    |  D/V  |
| 6.2.2 | Bekræft, at kritiske sårbarheder (CVSS ≥ 7.0) blokerer for promovering til produktionsbilleder.                              |   1    |  D/V  |
| 6.2.3 | Bekræft, at statisk kodeanalyse kører på forgrenede eller leverede ML-biblioteker.                                           |   2    |   D   |
| 6.2.4 | Bekræft, at forslag til opgradering af framework inkluderer en sikkerhedsvurdering med reference til offentlige CVE-feeds.   |   2    |   V   |
| 6.2.5 | Bekræft, at runtime-sensorer advarer ved uventede indlæsninger af dynamiske biblioteker, der afviger fra den signerede SBOM. |   3    |   V   |

---

## C6.3 Fastlåsning og verifikation af afhængigheder

Fastlås hver afhængighed til uforanderlige digests og reproducer builds for at garantere identiske, manipulationsfrie artefakter.

|   #   | Beskrivelse                                                                                                         | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 6.3.1 | Bekræft, at alle pakkestyringsværktøjer håndhæver versionsfastlåsning via låsefiler.                                |   1    |  D/V  |
| 6.3.2 | Bekræft, at uforanderlige digest-værdier anvendes i stedet for foranderlige tags i containerhenvisninger.           |   1    |  D/V  |
| 6.3.3 | Bekræft, at reproducible‑build kontroller sammenligner hashes på tværs af CI-kørsler for at sikre identiske output. |   2    |   D   |
| 6.3.4 | Bekræft, at build-attestationer opbevares i 18 måneder for revisionssporbarhed.                                     |   2    |   V   |
| 6.3.5 | Bekræft, at udløbne afhængigheder udløser automatiserede PR'er for at opdatere eller forgrejne fastlåste versioner. |   3    |   D   |

---

## C6.4 Håndhævelse af betroede kilder

Tillad kun download af artefakter fra kryptografisk verificerede, organisationsgodkendte kilder og bloker alt andet.

|   #   | Beskrivelse                                                                                                                        | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 6.4.1 | Bekræft, at modelvægte, datasæt og containere kun downloades fra godkendte domæner eller interne registre.                         |   1    |  D/V  |
| 6.4.2 | Bekræft, at Sigstore/Cosign-signaturer validerer udgiverens identitet, før artefakter caches lokalt.                               |   1    |  D/V  |
| 6.4.3 | Bekræft, at egress-proxyer blokerer uautoriserede download af artefakter for at håndhæve politikken om betroede kilder.            |   2    |   D   |
| 6.4.4 | Bekræft, at repository tilladelseslister gennemgås kvartalsvist med dokumentation for forretningsmæssig begrundelse for hver post. |   2    |   V   |
| 6.4.5 | Bekræft, at politikovertrædelser udløser karantæne af artefakter og tilbagerulning af afhængige pipeline-kørsler.                  |   3    |   V   |

---

## C6.5 Vurdering af risiko ved tredjepartsdatasæt

Evaluer eksterne datasæt for forgiftning, bias og juridisk overholdelse, og overvåg dem gennem hele deres livscyklus.

|   #   | Beskrivelse                                                                                                                       | Niveau | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 6.5.1 | Bekræft, at eksterne datasæt gennemgår vurdering af forgiftningsrisiko (f.eks. datafingeraftryk, outlier-detektion).              |   1    |  D/V  |
| 6.5.2 | Bekræft, at bias-målinger (demografisk paritet, lige mulighed) beregnes før godkendelse af datasættet.                            |   1    |   D   |
| 6.5.3 | Bekræft, at oprindelse og licensbetingelser for datasæt er registreret i ML‑BOM-poster.                                           |   2    |   V   |
| 6.5.4 | Bekræft, at periodisk overvågning opdager drift eller korruption i hostede datasæt.                                               |   2    |   V   |
| 6.5.5 | Bekræft, at forbudt indhold (ophavsret, personligt identificerbare oplysninger) fjernes via automatiseret rensning inden træning. |   3    |   D   |

---

## C6.6 Overvågning af angreb på forsyningskæden

Opdag trusler mod forsyningskæden tidligt gennem CVE-feeds, audit-loganalyse og red-team-simulationer.

|   #   | Beskrivelse                                                                                                                        | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 6.6.1 | Bekræft, at CI/CD-revisionslogfiler strømmer til SIEM-detektioner for unormale pakkeudtræk eller manipulerede byggetrin.           |   1    |   V   |
| 6.6.2 | Kontroller, at procedurer for hændelsesrespons inkluderer tilbageførselsprocedurer for kompromitterede modeller eller biblioteker. |   2    |   D   |
| 6.6.3 | Bekræft, at trusselsintelligensberigelse markerer ML-specifikke indikatorer (f.eks. modelforgiftning IoC’er) i alarmernes triage.  |   3    |   V   |

---

## C6.7 ML‑BOM for Model Artefakter

Generer og signer detaljerede ML-specifikke SBOM'er (ML-BOM'er), så downstream-forbrugere kan verificere komponentintegritet ved implementeringstidspunktet.

|   #   | Beskrivelse                                                                                                                             | Niveau | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 6.7.1 | Bekræft, at hver modelartefakt udgiver en ML‑BOM, der angiver datasæt, vægte, hyperparametre og licenser.                               |   1    |  D/V  |
| 6.7.2 | Bekræft, at ML-BOM-generering og Cosign-signering er automatiseret i CI og påkrævet for sammenfletning.                                 |   1    |  D/V  |
| 6.7.3 | Bekræft, at ML‑BOM komplethedstjek fejler byggeprocessen, hvis nogen komponentmetadata (hash, licens) mangler.                          |   2    |   D   |
| 6.7.4 | Bekræft, at downstream-forbrugere kan forespørge ML-BOM'er via API for at validere importerede modeller ved implementeringstidspunktet. |   2    |   V   |
| 6.7.5 | Bekræft, at ML-BOM'er er versionsstyrede og sammenlignet for at opdage uautoriserede ændringer.                                         |   3    |   V   |

---

## Referencer

* [ML Supply Chain Compromise – MITRE ATLAS](https://misp-galaxy.org/mitre-atlas-attack-pattern/)
* [Supply‑chain Levels for Software Artifacts (SLSA)](https://slsa.dev/)
* [CycloneDX – Machine Learning Bill of Materials](https://cyclonedx.org/capabilities/mlbom/)
* [What is Data Poisoning? – SentinelOne](https://www.sentinelone.com/cybersecurity-101/cybersecurity/data-poisoning/)
* [Transfer Learning Attack – OWASP ML Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/docs/ML07_2023-Transfer_Learning_Attack)
* [AI Data Security Best Practices – CISA](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [Secure CI/CD Supply Chain – Sumo Logic](https://www.sumologic.com/blog/secure-azure-devops-github-supply-chain-attacks)
* [AI & Transparency: Protect ML Models – ReversingLabs](https://www.reversinglabs.com/blog/ai-and-transparency-how-ml-model-creators-can-protect-against-supply-chain-attacks)
* [SBOM Overview – CISA](https://www.cisa.gov/sbom)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [Dependency Pinning for Reproducible Python – Medium](https://medium.com/data-science-collective/guarantee-a-locked-reproducible-environment-with-every-python-run-c0e2bf19fb53)

