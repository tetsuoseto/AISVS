# C3-modellevenscyclusbeheer en wijzigingsbeheer

## Beheersdoel

AI-systemen moeten wijzigingscontroleprocessen implementeren die voorkomen dat onbevoegde of onveilige modelwijzigingen in productie terechtkomen. Deze controle waarborgt de integriteit van het model gedurende de gehele levenscyclus--van ontwikkeling via uitrol tot ontmanteling--wat snelle incidentrespons mogelijk maakt en verantwoording voor alle wijzigingen waarborgt.

Kernbeveiligingsdoel: Alleen geautoriseerde, gevalideerde modellen komen in productie door middel van gecontroleerde processen die integriteit, traceerbaarheid en herstelbaarheid waarborgen.

---

## C3.1 Modelautorisatie & Integriteit

Alleen geautoriseerde modellen met geverifieerde integriteit bereiken productieomgevingen.

|   #   | Beschrijving                                                                                                                                                                                                                                | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 3.1.1 | Controleer of alle modelartefacten (gewichten, configuraties, tokenizers) cryptografisch ondertekend zijn door geautoriseerde partijen vóór de uitrol.                                                                                      |   1    | D/V |
| 3.1.2 | Verifieer dat de integriteit van het model tijdens de uitrol wordt gevalideerd en dat verificatiefouten bij de handtekening het laden van het model verhinderen.                                                                            |   1    | D/V |
| 3.1.3 | Verifieer dat registraties van modelprovenantie de identiteit van een autoriserende entiteit, de controlesommen van trainingsgegevens, validatietestresultaten met de status geslaagd of niet geslaagd, en een aanmaaktijdstempel bevatten. |   2    | D/V |
| 3.1.4 | Verifieer dat alle modelartefacten semantische versienummering gebruiken (MAJOR.MINOR.PATCH) met gedocumenteerde criteria die aangeven wanneer elk versiecomponent toeneemt.                                                                |   2    | D/V |
| 3.1.5 | Controleer of de afhankelijkheidsregistratie een real-time inventaris bijhoudt die een snelle identificatie van alle verbruikende systemen mogelijk maakt.                                                                                  |   2    |  V  |

---

## C3.2 Model Validatie & Testen

Modellen moeten vóór de uitrol voldoen aan gedefinieerde beveiligings- en veiligheidsvalidaties.

|   #   | Beschrijving                                                                                                                                                                                                                     | Niveau | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 3.2.1 | Controleer of modellen geautomatiseerde beveiligingstests ondergaan die invoervalidatie, uitvoer-sanitatie en veiligheidsbeoordelingen omvatten, met van tevoren afgesproken organisatorische pass/fail-drempels vóór de uitrol. |   1    | D/V |
| 3.2.2 | Controleer of validatiefouten automatisch de modelimplementatie blokkeren na expliciete override-goedkeuring door vooraf aangewezen geautoriseerd personeel met gedocumenteerde zakelijke rechtvaardigingen.                     |   1    | D/V |
| 3.2.3 | Controleer of de testresultaten cryptografisch ondertekend zijn en onveranderlijk gekoppeld zijn aan de specifieke hash van de modelversie die wordt gevalideerd.                                                                |   2    |  V  |
| 3.2.4 | Controleer dat nooduitrollen een gedocumenteerde beveiligingsrisicoanalyse en goedkeuring van een vooraf aangewezen beveiligingsautoriteit binnen afgesproken termijnen vereisen.                                                |   2    | D/V |

---

## C3.3 Gecontroleerde Uitrol & Rollback

Modelimplementaties moeten worden gecontroleerd, gemonitord en omkeerbaar zijn.

|   #   | Beschrijving                                                                                                                                                                                                                                                                               | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 3.3.1 | Verifieer dat productie-implementaties geleidelijke uitrolmechanismen toepassen (canary-implementaties, blue-green-implementaties) met automatische rollback-triggers op basis van foutpercentages die van tevoren zijn afgesproken, latentiegrenzen of beveiligingswaarschuwingscriteria. |   1    |  D  |
| 3.3.2 | Controleer of rollback-mogelijkheden de volledige modeltoestand (gewichten, configuraties, afhankelijkheden) atomair herstellen binnen voorgedefinieerde organisatorische tijdvensters.                                                                                                    |   1    | D/V |
| 3.3.3 | Controleer dat uitrolprocessen cryptografische handtekeningen valideren en integriteitschecksums berekenen vóór activatie van het model, en laat de uitrol mislukken bij elke afwijking.                                                                                                   |   2    | D/V |
| 3.3.4 | Controleer of noodafsluitingsmogelijkheden voor modellen model-endpoints kunnen uitschakelen binnen vooraf gedefinieerde responstijden via geautomatiseerde circuit-breakers of handmatige kill-switches.                                                                                  |   2    | D/V |
| 3.3.5 | Controleer of rollback artefacten (vorige modelversies, configuraties, afhankelijkheden) worden bewaard volgens het beleid van de organisatie met immutabele opslag voor incidentrespons.                                                                                                  |   2    |  V  |

---

## C3.4 Verantwoording van wijzigingen & audit

Alle wijzigingen in de levenscyclus van het model moeten traceerbaar en auditbaar zijn.

|   #   | Beschrijving                                                                                                                                                                                                                                              | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 3.4.1 | Controleer dat alle modelwijzigingen (uitrol, configuratie, uitfasering) onveranderlijke auditlogboeken genereren, inclusief een tijdstempel, een geauthenticeerde actor-identiteit, een wijzigingstype en toestanden vóór en na.                         |   1    |  V  |
| 3.4.2 | Controleer of toegang tot auditlogboeken de juiste autorisatie vereist en of alle toegangspogingen worden gelogd met gebruikersidentiteit en een tijdstempel.                                                                                             |   2    | D/V |
| 3.4.3 | Verifieer dat prompt-sjablonen en systeemberichten onder versiebeheer staan in Git-repositories met verplichte codebeoordeling en goedkeuring door aangewezen beoordelaars voordat ze in productie worden genomen.                                        |   2    | D/V |
| 3.4.4 | Controleer of auditregistraties voldoende details bevatten (model-hashes, configuratie-snapshots, afhankelijkheidsversies) om een volledige reconstructie van de toestand van het model mogelijk te maken voor elk tijdstempel binnen de retentieperiode. |   2    |  V  |

---

## C3.5 Veilige ontwikkelingspraktijken

Modelontwikkeling en trainingsprocessen moeten veilige praktijken volgen om beveiligingsinbreuken te voorkomen.

|   #   | Beschrijving                                                                                                                                                                                                                          | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 3.5.1 | Controleer of omgevingen voor modelontwikkeling, testen en productie fysiek of logisch gescheiden zijn. Ze hebben geen gedeelde infrastructuur, afzonderlijke toegangscontroles en geïsoleerde gegevensopslag.                        |   1    |  D  |
| 3.5.2 | Verifieer dat modeltraining en fijn afstemmen plaatsvinden in geïsoleerde omgevingen met gecontroleerde netwerktoegang.                                                                                                               |   1    |  D  |
| 3.5.3 | Verifieer dat trainingsgegevens-bronnen gevalideerd zijn via integriteitscontroles en geauthenticeerd via vertrouwde bronnen met een gedocumenteerde keten van bewaring voordat ze worden gebruikt bij de ontwikkeling van het model. |   1    | D/V |
| 3.5.4 | Verifieer dat modelontwikkelingsartefacten (hyperparameters, trainingscripts, configuratiebestanden) zijn opgeslagen in versiebeheer en die goedkeuring na peer review vereisen voordat ze voor training worden gebruikt.             |   2    |  D  |

---

## C3.6 Model Uitdienststelling & Ontmanteling

Modellen moeten veilig buiten gebruik worden gesteld wanneer ze niet langer nodig zijn of wanneer beveiligingsproblemen worden vastgesteld.

|   #   | Beschrijving                                                                                                                                                                                                                                           | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 3.6.1 | Controleer dat processen voor het uitfaseren van modellen automatisch afhankelijkheidsgrafen scannen, alle systemen identificeren die het model gebruiken, en vooraf afgesproken aankondigingsperiodes bieden voordat de modellen worden uitgefaseerd. |   1    |  D  |
| 3.6.2 | Controleer dat uit dienst genomen modelartefacten veilig worden gewist door middel van cryptografische uitwissing of multi-pass overschrijven, overeenkomstig gedocumenteerd dataretentiebeleid met gevalideerde vernietigingscertificaten.            |   1    | D/V |
| 3.6.3 | Controleer dat gebeurtenissen bij het buiten gebruik stellen van modellen worden gelogd met een tijdstempel en de identiteit van de actor, en dat modelhandtekeningen worden ingetrokken om hergebruik te voorkomen.                                   |   2    |  V  |
| 3.6.4 | Verifieer dat nooduitfasering van het model de toegang tot het model kan uitschakelen binnen vooraf vastgestelde noodreactietermijnen via geautomatiseerde kill-switches als kritieke beveiligingslekken worden ontdekt.                               |   2    | D/V |

---

## Referenties

* [MLOps Principles](https://ml-ops.org/content/mlops-principles)
* [Securing AI/ML Ops – Cisco.com](https://sec.cloudapps.cisco.com/security/center/resources/SecuringAIMLOps)
* [Audit logs security: cryptographically signed tamper-proof logs](https://www.cossacklabs.com/blog/audit-logs-security/)
* [Machine Learning Model Versioning: Top Tools & Best Practices](https://lakefs.io/blog/model-versioning/)
* [AI Hygiene Starts with Models and Data Loaders – SEI Blog](https://insights.sei.cmu.edu/documents/6190/AI-Hygiene-Starts-with-Models-and-Data-Loaders_1G0KTRh.pdf)
* [How to handle versioning and rollback of a deployed ML model?](https://learn.microsoft.com/en-au/answers/questions/1845378/how-to-handle-versioning-and-rollback-of-a-deploye)
* [Reinforcement fine-tuning – OpenAI API](https://platform.openai.com/docs/guides/reinforcement-fine-tuning)
* [Auditing Machine Learning models: Governance, Data Security and …](https://www.linkedin.com/pulse/auditing-machine-learning-models-governance-data-security-negrete-yn81f)
* [Adversarial Training to Improve Model Robustness](https://medium.com/%40amit25173/adversarial-training-to-improve-model-robustness-5e285b516713)
* [What is AI adversarial robustness? – IBM Research](https://research.ibm.com/blog/securing-ai-workflows-with-adversarial-robustness)
* [Exploring Data Provenance: Ensuring Data Integrity and Authenticity](https://www.astera.com/type/blog/data-provenance/)
* [MITRE ATLAS](https://atlas.mitre.org/)
* [AWS Prescriptive Guidance – Best practices for retiring applications …](https://docs.aws.amazon.com/pdfs/prescriptive-guidance/latest/migration-app-retirement-best-practices/migration-app-retirement-best-practices.pdf)

