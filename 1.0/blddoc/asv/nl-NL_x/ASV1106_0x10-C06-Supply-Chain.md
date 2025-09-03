# C6 Beveiliging van de toeleveringsketen voor Modellen, Frameworks en Data

## Beheersdoel

AI‑toeleveringsketen‑aanvallen misbruiken modellen, raamwerken of datasets van derden om achterdeuren, bias of exploitbare code in te bouwen. Deze controles bieden end‑to‑end herkomstregistratie, kwetsbaarheidsbeheer en monitoring om de hele modellevenscyclus te beschermen.

---

## C6.1 Voorafgetraind modelkeuring en provenantie

Beoordeel en authenticeer de oorsprongen van derde‑partijmodellen, licenties en verborgen gedragingen, vóór enige fijn‑afstemming of uitrol.

|   #   | Beschrijving                                                                                                                                                                     | Niveau | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 6.1.1 | Verifieer dat elk modelartefact van derden een ondertekend provenance-record bevat dat de bronrepository en de commit-hash identificeert.                                        |   1    | D/V |
| 6.1.2 | Verifieer dat modellen vóór importeren worden gescand op kwaadaardige lagen of Trojaanse triggers met behulp van geautomatiseerde tools.                                         |   1    | D/V |
| 6.1.3 | Verifieer dat transfer-learning fijn-tunen een adversariële evaluatie doorstaat om verborgen gedragingen te detecteren.                                                          |   2    |  D  |
| 6.1.4 | Verifieer of modellicenties, exportcontrole-tags en data-origin-verklaringen zijn vastgelegd in een ML‑BOM‑vermelding.                                                           |   2    |  V  |
| 6.1.5 | Controleer of hoog-risico-modellen (openbaar geüploade gewichten, niet-geverifieerde makers) in quarantaine blijven totdat menselijke beoordeling en ondertekening plaatsvinden. |   3    | D/V |

---

## C6.2 Raamwerk & Bibliotheekscan

Blijf voortdurend ML-frameworks en bibliotheken scannen op CVEs en kwaadaardige code om de runtime-stack veilig te houden.

|   #   | Beschrijving                                                                                                                       | Niveau | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 6.2.1 | Controleer of CI-pijplijnen afhankelijkheids-scanners uitvoeren op AI-frameworks en kritieke bibliotheken.                         |   1    | D/V |
| 6.2.2 | Controleer of kritieke kwetsbaarheden (CVSS ≥ 7.0) de promotie naar productie-afbeeldingen blokkeren.                              |   1    | D/V |
| 6.2.3 | Verifieer of de statische code-analyse draait op geforkte of meegeleverde ML-bibliotheken.                                         |   2    |  D  |
| 6.2.4 | Verifieer dat voorstellen voor framework-upgrades beveiligingsimpactanalyses bevatten die verwijzen naar openbare CVE-feeds.       |   2    |  V  |
| 6.2.5 | Verifieer dat runtime-sensoren waarschuwen bij onverwacht laden van dynamische bibliotheken die afwijken van de ondertekende SBOM. |   3    |  V  |

---

## C6.3 Afhankelijkheden Vastzetten & Verificatie

Zet elke afhankelijkheid vast met onveranderlijke digests en maak builds reproduceerbaar om identieke, tamper-vrije artefacten te garanderen.

|   #   | Beschrijving                                                                                                        | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 6.3.1 | Verifieer dat alle pakketbeheerders versiepinning afdwingen via lockfiles.                                          |   1    | D/V |
| 6.3.2 | Verifieer dat onveranderlijke digests worden gebruikt in plaats van veranderlijke tags in containerreferenties.     |   1    | D/V |
| 6.3.3 | Verifieer dat reproduceerbaar‑build-controles hashes vergelijken tussen CI runs om identieke uitvoer te garanderen. |   2    |  D  |
| 6.3.4 | Verifieer dat build-attestaties gedurende 18 maanden worden bewaard voor audittraceerbaarheid.                      |   2    |  V  |
| 6.3.5 | Verifieer dat verlopen afhankelijkheden automatische PRs activeren om gepinde versies bij te werken of te forken.   |   3    |  D  |

---

## C6.4 Handhaving van vertrouwde bronnen

Sta downloads van artefacten alleen toe vanaf cryptografisch geverifieerde, door de organisatie goedgekeurde bronnen en blokkeer alles wat niet uit deze bronnen komt.

|   #   | Beschrijving                                                                                                                                                | Niveau | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 6.4.1 | Verifieer dat modelgewichten, datasets en containers uitsluitend van goedgekeurde domeinen of interne registries worden gedownload.                         |   1    | D/V |
| 6.4.2 | Controleer of Sigstore/Cosign-handtekeningen de identiteit van de uitgever valideren voordat artefacten lokaal in de cache worden opgeslagen.               |   1    | D/V |
| 6.4.3 | Controleer of uitgaande proxies niet-geauthenticeerde artefact-downloads blokkeren om het beleid voor vertrouwde bronnen af te dwingen.                     |   2    |  D  |
| 6.4.4 | Controleer of repository allow‑lists elk kwartaal worden herzien met bewijs van zakelijke rechtvaardiging voor elke invoer.                                 |   2    |  V  |
| 6.4.5 | Controleer of beleidsinbreuken ervoor zorgen dat artefacten in quarantaine worden geplaatst en dat afhankelijke pipeline-uitvoeringen worden teruggedraaid. |   3    |  V  |

---

## C6.5 Derdepartij‑dataset Risicobeoordeling

Externe datasets evalueren op data-poisoning, bias en wettelijke naleving, en ze gedurende hun hele levenscyclus monitoren.

|   #   | Beschrijving                                                                                                                                          | Niveau | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 6.5.1 | Controleer dat externe datasets een risicoscore voor poisoning-aanvallen ondergaan (bijv. datavingerafdrukken, detectie van uitschieters).            |   1    | D/V |
| 6.5.2 | Controleer of biasmetingen (demografische pariteit, gelijke kansen) worden berekend voordat de dataset wordt goedgekeurd.                             |   1    |  D  |
| 6.5.3 | Controleer of de herkomst en licentievoorwaarden voor datasets zijn vastgelegd in ML‑BOM‑vermeldingen.                                                |   2    |  V  |
| 6.5.4 | Controleer of periodieke bewaking datadrift of gegevenscorruptie in gehoste datasets detecteert.                                                      |   2    |  V  |
| 6.5.5 | Controleer of verboden inhoud (auteursrechtelijk beschermd materiaal, PII) wordt verwijderd via geautomatiseerd opschonen van gegevens vóór training. |   3    |  D  |

---

## C6.6 Toeleveringsketen-aanvalbewaking

Detecteer vroegtijdig dreigingen in de toeleverings‑keten via CVE-feeds, audit‑log analyses en red‑team simulaties.

|   #   | Beschrijving                                                                                                                   | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 6.6.1 | Verifieer dat CI/CD-auditlogboeken naar SIEM-detecties stromen voor anomale pakketdownloads of gemanipuleerde build-stappen.   |   1    |  V  |
| 6.6.2 | Controleer of incidentresponsiehandleidingen terugzettingsprocedures bevatten voor gecompromitteerde modellen of bibliotheken. |   2    |  D  |
| 6.6.3 | Verifieer of dreigingsinformatie‑verrijking ML‑specifieke indicatoren tagt (bijv. model‑poisoning IoCs) in alert triage.       |   3    |  V  |

---

## C6.7 ML‑BOM voor modelartefacten

Genereer en onderteken gedetailleerde ML-specifieke SBOMs (ML‑BOMs) zodat downstream-gebruikers de integriteit van componenten tijdens de uitrol kunnen verifiëren.

|   #   | Beschrijving                                                                                                                               | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 6.7.1 | Verifieer dat elk modelartefact een ML‑BOM publiceert die datasets, gewichten, hyperparameters en licenties vermeldt.                      |   1    | D/V |
| 6.7.2 | Verifieer of ML‑BOM-generatie en Cosign-handtekening in CI automatisch verlopen en voor het samenvoegen vereist zijn.                      |   1    | D/V |
| 6.7.3 | Verifieer of ML‑BOM‑volledigheidscontroles ervoor zorgen dat de build faalt als er metadata voor een component ontbreekt (hash, licentie). |   2    |  D  |
| 6.7.4 | Controleer of downstream-consumenten via een API ML-BOMs kunnen opvragen om geïmporteerde modellen tijdens de uitrol te valideren.         |   2    |  V  |
| 6.7.5 | Verifieer of ML‑BOMs onder versiebeheer staan en met diff worden vergeleken om ongeautoriseerde wijzigingen op te sporen.                  |   3    |  V  |

---

## Referenties

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

