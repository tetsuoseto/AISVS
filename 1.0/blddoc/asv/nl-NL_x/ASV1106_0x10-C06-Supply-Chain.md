# C6 Beveiliging van de toeleveringsketen voor modellen, frameworks en data

## Beheersingsdoelstelling

AI-aanvalen op de toeleveringsketen maken gebruik van modellen, frameworks of datasets van derden om achterdeurtjes, vooringenomenheid of exploitbare code in te bouwen. Deze controles bieden end-to-end herkomst, beheer van kwetsbaarheden en monitoring om de gehele levenscyclus van het model te beschermen.

---

## C6.1 Vooropleiding Modelbeoordeling & Herkomst

Beoordeel en verifieer de herkomst, licenties en verborgen gedragingen van modellen van derden voordat u enige fine-tuning of implementatie uitvoert.

|   #   | Beschrijving                                                                                                                                                                              | Niveau | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 6.1.1 | Verifieer dat elk derde‑partij modelartifact een ondertekend herkomstrecord bevat dat de bronrepository en commit-hash identificeert.                                                     |   1    | D/V |
| 6.1.2 | Verifieer dat modellen met geautomatiseerde hulpmiddelen worden gescand op kwaadaardige lagen of Trojaanse triggers voordat ze worden geïmporteerd.                                       |   1    | D/V |
| 6.1.3 | Controleer of transfer-learning fine-tuning slaagt voor adversariële evaluatie om verborgen gedragingen te detecteren.                                                                    |   2    |  D  |
| 6.1.4 | Controleer of modellicenties, exportcontroleslabels en verklaringen over de herkomst van gegevens zijn vastgelegd in een ML-BOM-item.                                                     |   2    |  V  |
| 6.1.5 | Verifieer dat hoog-risicomodellen (openbaar geüploade gewichten, niet-geverifieerde makers) in quarantaine blijven totdat een menselijke beoordeling en goedkeuring heeft plaatsgevonden. |   3    | D/V |

---

## C6.2 Framework- en bibliotheekscanning

Continu continu continu scannen ML-frameworks en -bibliotheken op CVE's en kwaadaardige code om de runtime-stack veilig te houden.

|   #   | Beschrijving                                                                                                                                 | Niveau | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 6.2.1 | Verifieer dat CI-pijplijnen afhankelijkheidsscanners uitvoeren op AI-frameworks en kritieke bibliotheken.                                    |   1    | D/V |
| 6.2.2 | Controleer of kritieke kwetsbaarheden (CVSS ≥ 7.0) de promotie naar productieafbeeldingen blokkeren.                                         |   1    | D/V |
| 6.2.3 | Controleer of statische code-analyse wordt uitgevoerd op geforkte of gevendorde ML-bibliotheken.                                             |   2    |  D  |
| 6.2.4 | Controleer of voorstellen voor framework-upgrades een beoordeling van de beveiligingsimpact bevatten met verwijzing naar openbare CVE-feeds. |   2    |  V  |
| 6.2.5 | Verifieer dat runtime-sensoren waarschuwen bij onverwachte dynamische bibliotheekladingen die afwijken van de ondertekende SBOM.             |   3    |  V  |

---

## C6.3 Afhankelijkheid vastzetten & verificatie

Veranker elke afhankelijkheid aan onveranderlijke digests en reproduceer builds om identieke, niet-te-manipuleren artefacten te garanderen.

|   #   | Beschrijving                                                                                                       | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 6.3.1 | Controleer of alle pakketbeheerders versiebevriezing afdwingen via lockfiles.                                      |   1    | D/V |
| 6.3.2 | Controleer of onveranderlijke digests worden gebruikt in plaats van wijzigbare tags in containerreferenties.       |   1    | D/V |
| 6.3.3 | Controleer of reproduceerbare-buildcontroles hashes vergelijken tussen CI-runs om identieke outputs te garanderen. |   2    |  D  |
| 6.3.4 | Controleer of bouwattesten 18 maanden worden opgeslagen voor audit-traceerbaarheid.                                |   2    |  V  |
| 6.3.5 | Controleer of verlopen afhankelijkheden geautomatiseerde PR's activeren om bijgewerkte of geforkte vaste versies.  |   3    |  D  |

---

## C6.4 Handhaving van Vertrouwde Bron

Sta alleen downloads van artefacten toe van cryptografisch geverifieerde, door de organisatie goedgekeurde bronnen en blokkeer alles wat anders is.

|   #   | Beschrijving                                                                                                                               | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 6.4.1 | Controleer of modelgewichten, datasets en containers alleen worden gedownload van goedgekeurde domeinen of interne registries.             |   1    | D/V |
| 6.4.2 | Controleer of Sigstore/Cosign-handtekeningen de identiteit van de uitgever verifiëren voordat artefacten lokaal worden gecachet.           |   1    | D/V |
| 6.4.3 | Controleer of uitgaande proxies onbevoegde downloads van artefacten blokkeren om het beleid voor vertrouwde bronnen af te dwingen.         |   2    |  D  |
| 6.4.4 | Verifieer dat repository-toegangs‑lijsten elk kwartaal worden herzien met bewijs van zakelijke rechtvaardiging voor elke vermelding.       |   2    |  V  |
| 6.4.5 | Controleer of beleidschendingen het in quarantaine plaatsen van artefacten en het terugdraaien van afhankelijke pijpleningsruns activeren. |   3    |  V  |

---

## C6.5 Risicobeoordeling van datasets van derden

Evalueer externe datasets op vergiftiging, vooringenomenheid en juridische naleving, en monitor ze gedurende hun hele levenscyclus.

|   #   | Beschrijving                                                                                                                             | Niveau | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 6.5.1 | Controleer of externe datasets een risicoanalyse op vergiftiging ondergaan (bijv. datafingerprinting, detectie van uitschieters).        |   1    | D/V |
| 6.5.2 | Controleer of bias-metrics (demografische pariteit, gelijke kansen) worden berekend vóór goedkeuring van de dataset.                     |   1    |  D  |
| 6.5.3 | Controleer of provenance en licentievoorwaarden voor datasets worden vastgelegd in ML-BOM-items.                                         |   2    |  V  |
| 6.5.4 | Verifieer dat periodieke monitoring afwijkingen of corruptie in gehoste datasets detecteert.                                             |   2    |  V  |
| 6.5.5 | Verifieer dat niet-toegestane inhoud (auteursrecht, PII) via geautomatiseerde verwijdering wordt verwijderd voorafgaand aan het trainen. |   3    |  D  |

---

## C6.6 Supply Chain-aanvalmonitoring

Detecteer dreigingen in de toeleveringsketen vroegtijdig via CVE-feeds, auditloganalyse en red-team simulaties.

|   #   | Beschrijving                                                                                                                        | Niveau | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 6.6.1 | Verifieer dat CI/CD-auditlogs worden gestreamd naar SIEM-detecties voor afwijkende pakketdownloads of gemanipuleerde bouwstappen.   |   1    |  V  |
| 6.6.2 | Verifieer of incident response playbooks terugrolprocedures bevatten voor gecompromitteerde modellen of bibliotheken.               |   2    |  D  |
| 6.6.3 | Controleer of threat-intel verrijking ML-specifieke indicatoren (bijv. modelvergiftiging IoC's) tagt bij de alerteringsverificatie. |   3    |  V  |

---

## C6.7 ML-BOM voor Model Artefacten

Genereer en onderteken gedetailleerde ML-specifieke SBOM's (ML-BOM's) zodat downstream gebruikers de integriteit van componenten kunnen verifiëren bij implementatietijd.

|   #   | Beschrijving                                                                                                                             | Niveau | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 6.7.1 | Verifieer dat elke modelartefact een ML-BOM publiceert die datasets, gewichten, hyperparameters en licenties vermeldt.                   |   1    | D/V |
| 6.7.2 | Verifieer dat de ML‑BOM generatie en Cosign ondertekening geautomatiseerd zijn in CI en vereist zijn voor samenvoeging.                  |   1    | D/V |
| 6.7.3 | Controleer of ML‑BOM volledigheidscontroles de build laten mislukken als er metadata van een component (hash, licentie) ontbreekt.       |   2    |  D  |
| 6.7.4 | Verifieer dat downstreamgebruikers ML-BOM's via API kunnen opvragen om geïmporteerde modellen te valideren tijdens de implementatietijd. |   2    |  V  |
| 6.7.5 | Controleer of ML-BOM's versiebeheer hebben en worden vergeleken om ongeautoriseerde wijzigingen te detecteren.                           |   3    |  V  |

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

