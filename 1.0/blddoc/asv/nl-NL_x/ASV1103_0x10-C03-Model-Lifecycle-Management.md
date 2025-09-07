# Beheer van de levenscyclus van het C3-model en wijzigingscontrole

## Beheersingsdoelstelling

AI-systemen moeten wijzigingsbeheerprocessen implementeren die voorkomen dat ongeautoriseerde of onveilige modelwijzigingen in productie terechtkomen. Deze controle waarborgt de integriteit van het model gedurende de hele levenscyclus—van ontwikkeling tot implementatie en buiten gebruikstelling—wat snelle incidentrespons mogelijk maakt en verantwoordelijkheid voor alle wijzigingen behoudt.

Kernbeveiligingsdoel: Alleen geautoriseerde, gevalideerde modellen komen in productie door het toepassen van gecontroleerde processen die integriteit, traceerbaarheid en herstelbaarheid waarborgen.

---

## C3.1 Modelautorisatie & Integriteit

Alleen geautoriseerde modellen met geverifieerde integriteit bereiken productieomgevingen.

|   #   | Beschrijving                                                                                                                                                                                                       | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 3.1.1 | Verifieer dat alle modelartefacten (gewichten, configuraties, tokenizers) cryptografisch zijn ondertekend door geautoriseerde entiteiten voordat ze worden ingezet.                                                |   1    | D/V |
| 3.1.2 | Verifieer dat de integriteit van het model wordt gevalideerd bij de implementatietijd en dat fouten bij handtekeningverificatie het laden van het model voorkomen.                                                 |   1    | D/V |
| 3.1.3 | Controleer of de herkomstgegevens van het model de identiteit van de bevoegde entiteit, controlesommen van de trainingsgegevens, validatietestresultaten met slaag-/faalstatus en een creatietijdstempel bevatten. |   2    | D/V |
| 3.1.4 | Verifieer dat alle modelartefacten semantische versiebeheer gebruiken (MAJOR.MINOR.PATCH) met gedocumenteerde criteria waarin wordt gespecificeerd wanneer elk versieonderdeel wordt verhoogd.                     |   2    | D/V |
| 3.1.5 | Verifieer dat de afhankelijkheidsregistratie een realtime inventaris bijhoudt die snelle identificatie van alle verbruikende systemen mogelijk maakt.                                                              |   2    |  V  |

---

## C3.2 Modelvalidatie & Testen

Modellen moeten gedefinieerde beveiligings- en veiligheidscontroles doorstaan voordat ze worden ingezet.

|   #   | Beschrijving                                                                                                                                                                                                                         | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 3.2.1 | Verifieer dat modellen geautomatiseerde beveiligingstests ondergaan die inputvalidatie, outputsanering en veiligheidsbeoordelingen omvatten met vooraf afgesproken organisatorische slaag-/faalthresholds voordat ze worden ingezet. |   1    | D/V |
| 3.2.2 | Controleer of validatiefouten automatisch de implementatie van het model blokkeren na expliciete goedkeuring van een vooraf aangewezen bevoegd persoon met gedocumenteerde zakelijke rechtvaardigingen.                              |   1    | D/V |
| 3.2.3 | Verifieer dat testresultaten cryptografisch zijn ondertekend en onveranderbaar gekoppeld aan de specifieke modelversie-hash die wordt gevalideerd.                                                                                   |   2    |  V  |
| 3.2.4 | Verifieer dat noodimplementaties een gedocumenteerde veiligheidsrisicoanalyse en goedkeuring vereisen van een vooraf aangewezen veiligheidsautoriteit binnen vooraf afgesproken termijnen.                                           |   2    | D/V |

---

## C3.3 Gecontroleerde implementatie en terugrol

Modelimplementaties moeten worden gecontroleerd, gemonitord en omkeerbaar zijn.

|   #   | Beschrijving                                                                                                                                                                                                                                                                 | Niveau | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 3.3.1 | Verifieer of productiedeployments geleidelijke uitrolmechanismen implementeren (canary deployments, blue-green deployments) met geautomatiseerde rollback-triggers op basis van vooraf overeengekomen foutpercentages, latentiegrenzen of beveiligingswaarschuwingscriteria. |   1    |  D  |
| 3.3.2 | Verifieer dat rollback-mogelijkheden de volledige modelstatus (gewichten, configuraties, afhankelijkheden) atomair herstellen binnen vooraf gedefinieerde organisatorische tijdsvensters.                                                                                    |   1    | D/V |
| 3.3.3 | Controleer of implementatieprocessen cryptografische handtekeningen valideren en integriteitschecksommen berekenen vóór modelactivatie, en de implementatie laten mislukken bij enige afwijking.                                                                             |   2    | D/V |
| 3.3.4 | Controleer of noodmodussluitingsmogelijkheden het uitschakelen van modeleindpunten binnen vooraf gedefinieerde reactietijden kunnen garanderen via geautomatiseerde stroomonderbrekers of handmatige kill switches.                                                          |   2    | D/V |
| 3.3.5 | Controleer of rollback-artifacten (vorige modelversies, configuraties, afhankelijkheden) worden behouden volgens de organisatorische beleidsregels met onveranderlijke opslag voor incidentrespons.                                                                          |   2    |  V  |

---

## C3.4 Verantwoordingsplicht & Audit wijzigen

Alle wijzigingen in de levenscyclus van het model moeten traceerbaar en controleerbaar zijn.

|   #   | Beschrijving                                                                                                                                                                                                                             | Niveau | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 3.4.1 | Verifieer dat alle modelwijzigingen (implementatie, configuratie, uitschakeling) onveranderlijke auditrecords genereren, inclusief een tijdstempel, een geverifieerde identiteit van de actor, een wijzigingstype, en voor/na-statussen. |   1    |  V  |
| 3.4.2 | Controleer of toegang tot het auditlogboek de juiste autorisatie vereist en dat alle toegangspogingen worden geregistreerd met gebruikersidentiteit en een tijdstempel.                                                                  |   2    | D/V |
| 3.4.3 | Verifieer dat prompt-sjablonen en systeemberichten versiebeheer hebben in git-repositories met verplichte codebeoordeling en goedkeuring van aangewezen reviewers voordat ze worden uitgerold.                                           |   2    | D/V |
| 3.4.4 | Verifieer dat auditrecords voldoende details bevatten (modelhashes, configuratiesnapshots, afhankelijkheidsversies) om volledige reconstructie van de modelstatus mogelijk te maken voor elk tijdstip binnen de bewaartermijn.           |   2    |  V  |

---

## C3.5 Veilige ontwikkelingspraktijken

Modelontwikkelings- en trainingsprocessen moeten veilige praktijken volgen om compromittering te voorkomen.

|   #   | Beschrijving                                                                                                                                                                                                                  | Niveau | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 3.5.1 | Verifieer dat modelontwikkeling, test- en productieomgevingen fysiek of logisch gescheiden zijn. Ze hebben geen gedeelde infrastructuur, aparte toegangscontroles en geïsoleerde gegevensopslag.                              |   1    |  D  |
| 3.5.2 | Controleer of modeltraining en fine-tuning plaatsvinden in geïsoleerde omgevingen met gecontroleerde netwerktoegang.                                                                                                          |   1    |  D  |
| 3.5.3 | Verifieer dat trainingsgegevensbronnen worden gevalideerd via integriteitscontroles en geauthenticeerd via vertrouwde bronnen met een gedocumenteerde keten van bewaring voordat ze worden gebruikt in modelontwikkeling.     |   1    | D/V |
| 3.5.4 | Verifieer dat artefacten voor modelontwikkeling (hyperparameters, trainingsscripts, configuratiebestanden) worden opgeslagen in versiebeheer en goedkeuring door collega’s vereisen voordat ze worden gebruikt voor training. |   2    |  D  |

---

## C3.6 Model Uitfasering & Buiten Gebruik Stelling

Modellen moeten veilig worden uitgefaseerd wanneer ze niet langer nodig zijn of wanneer beveiligingsproblemen worden vastgesteld.

|   #   | Beschrijving                                                                                                                                                                                                              | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 3.6.1 | Controleer of modeluitfasering processen automatisch afhankelijkheidsgrafieken scannen, alle afnemende systemen identificeren en vooraf afgesproken kennisgevingsperiodes bieden vóór het buiten gebruik stellen.         |   1    |  D  |
| 3.6.2 | Controleer of afgevoerde modelartefacten veilig worden gewist met behulp van cryptografische wissen of meervoudig overschrijven volgens gedocumenteerde gegevensbewaarbeleid met geverifieerde vernietigingscertificaten. |   1    | D/V |
| 3.6.3 | Controleer of modeluitdiensttreding gebeurtenissen worden geregistreerd met tijdstempel en identiteit van de actor, en dat modelhandtekeningen worden ingetrokken om hergebruik te voorkomen.                             |   2    |  V  |
| 3.6.4 | Verifieer dat noodmodelpensioen toegang tot het model kan uitschakelen binnen vooraf vastgestelde responsperioden voor noodgevallen via geautomatiseerde killschakelaars als kritieke beveiligingslekken worden ontdekt.  |   2    | D/V |

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

