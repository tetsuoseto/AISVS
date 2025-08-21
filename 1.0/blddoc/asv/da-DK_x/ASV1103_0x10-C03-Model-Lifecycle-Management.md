# C3 Model Livscyklusstyring & Ændringskontrol

## Kontrolmål

AI-systemer skal implementere ændringskontrolprocesser, der forhindrer uautoriserede eller usikre modelændringer i at nå produktionen. Denne kontrol sikrer modelintegritet gennem hele livscyklussen – fra udvikling gennem implementering til udfasning – hvilket muliggør hurtig hændelsesrespons og opretholder ansvarlighed for alle ændringer.

Kerne Sikkerhedsmål: Kun autoriserede, validerede modeller når produktion ved brug af kontrollerede processer, der opretholder integritet, sporbarhed og genoprettelighed.

---

## C3.1 Modelautorisation og integritet

Kun autoriserede modeller med verificeret integritet når produktionsmiljøer.

|   #   | Beskrivelse                                                                                                                                                                                                 | Niveau | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 3.1.1 | Bekræft, at alle modelartefakter (vægt, konfigurationer, tokenizere) er kryptografisk underskrevet af autoriserede enheder før implementering.                                                              |   1    |  D/V  |
| 3.1.2 | Bekræft, at modelintegriteten valideres ved implementeringstidspunktet, og at underskriftsverifikationsfejl forhindrer indlæsning af modellen.                                                              |   1    |  D/V  |
| 3.1.3 | Bekræft, at modelproveniensregistreringer indeholder en autoriserende enheds identitet, checksums for træningsdata, valideringstestresultater med bestået/ikke-bestået status og et oprettelsestidsstempel. |   2    |  D/V  |
| 3.1.4 | Bekræft, at alle modelartefakter bruger semantisk versionering (MAJOR.MINOR.PATCH) med dokumenterede kriterier, der specificerer, hvornår hver versionskomponent øges.                                      |   2    |  D/V  |
| 3.1.5 | Bekræft, at afhængighedssporing opretholder et realtidslager, som muliggør hurtig identifikation af alle forbrugende systemer.                                                                              |   2    |   V   |

---

## C3.2 Modelvalidering og testning

Modeller skal bestå definerede sikkerheds- og tryghedsgodkendelser før implementering.

|   #   | Beskrivelse                                                                                                                                                                                                                              | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 3.2.1 | Sørg for, at modeller gennemgår automatiseret sikkerhedstestning, der inkluderer inputvalidering, outputsanitering og sikkerhedsevalueringer med forudbestemte organisatoriske beståelses-/ikke-beståelsesgrænser, før de implementeres. |   1    |  D/V  |
| 3.2.2 | Bekræft, at valideringsfejl automatisk blokerer modeludrulning efter eksplicit overstyringsgodkendelse fra forudbestemte autoriserede personer med dokumenterede forretningsmæssige begrundelser.                                        |   1    |  D/V  |
| 3.2.3 | Bekræft, at testresultater er kryptografisk underskrevet og uforanderligt knyttet til den specifikke modelversions hash, der valideres.                                                                                                  |   2    |   V   |
| 3.2.4 | Bekræft, at nødudrulninger kræver dokumenteret sikkerhedsrisikovurdering og godkendelse fra en forudbestemt sikkerhedsmyndighed inden for forhåndsaftalte tidsfrister.                                                                   |   2    |  D/V  |

---

## C3.3 Kontrolleret Udrulning & Tilbageførsel

Modelimplementeringer skal kontrolleres, overvåges og være reversible.

|   #   | Beskrivelse                                                                                                                                                                                                                                                  | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 3.3.1 | Bekræft, at produktionsudrulninger implementerer gradvise udrulningsmekanismer (canary-udrulninger, blue-green-udrulninger) med automatiserede rollback-trigger baseret på forud aftalte fejlprocenter, latenstærskler eller sikkerhedsalarmeringskriterier. |   1    |   D   |
| 3.3.2 | Bekræft, at rollback-funktioner gendanner hele modeltilstanden (vægtninger, konfigurationer, afhængigheder) atomisk inden for foruddefinerede organisatoriske tidsvinduer.                                                                                   |   1    |  D/V  |
| 3.3.3 | Bekræft, at implementeringsprocesser validerer kryptografiske signaturer og beregner integritetskontrolsummer før modelaktivering, og at implementeringen mislykkes ved enhver uoverensstemmelse.                                                            |   2    |  D/V  |
| 3.3.4 | Bekræft, at nødafbrydelsesfunktioner for modellen kan deaktivere modelendepunkter inden for foruddefinerede svartider via automatiserede afbrydere eller manuelle dræberkontakter.                                                                           |   2    |  D/V  |
| 3.3.5 | Bekræft, at rollback-artifakter (tidligere modelversioner, konfigurationer, afhængigheder) opbevares i overensstemmelse med organisationspolitikker med uforanderlig lagring til hændelsesrespons.                                                           |   2    |   V   |

---

## C3.4 Ændringsansvar og Revision

Alle ændringer i modellens livscyklus skal kunne spores og revideres.

|   #   | Beskrivelse                                                                                                                                                                                                                                                | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 3.4.1 | Bekræft, at alle modelændringer (implementering, konfiguration, pensionering) genererer uforanderlige revisionsposter, der inkluderer et tidsstempel, en autentificeret aktøridentitet, en ændringstype samt tilstande før og efter ændringen.             |   1    |   V   |
| 3.4.2 | Bekræft, at adgang til revisionslog kræver passende autorisation, og at alle adgangsforsøg logges med brugeridentitet og et tidsstempel.                                                                                                                   |   2    |  D/V  |
| 3.4.3 | Bekræft, at promptskabeloner og systemmeddelelser er versionskontrolleret i git-repositorier med obligatorisk kodegennemgang og godkendelse fra udpegede anmeldere før implementering.                                                                     |   2    |  D/V  |
| 3.4.4 | Bekræft, at revisionsposter indeholder tilstrækkelige detaljer (modelhashes, konfigurationsøjebliksbilleder, afhængighedsudgaver) for at muliggøre fuldstændig genskabelse af modeltilstanden for et vilkårligt tidsstempel inden for opbevaringsperioden. |   2    |   V   |

---

## C3.5 Sikker udviklingspraksis

Modeludviklings- og træningsprocesser skal følge sikre praksisser for at forhindre kompromittering.

|   #   | Beskrivelse                                                                                                                                                                             | Niveau | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 3.5.1 | Verificer, at modeludviklings-, test- og produktionsmiljøer er fysisk eller logisk adskilte. De må ikke have delt infrastruktur, meningsfulde adgangskontroller og isolerede datalagre. |   1    |   D   |
| 3.5.2 | Bekræft, at modeltræning og finjustering foregår i isolerede miljøer med kontrolleret netværksadgang.                                                                                   |   1    |   D   |
| 3.5.3 | Bekræft, at træningsdatakilder valideres gennem integritetskontroller og autentificeres via betroede kilder med dokumenteret ansvarskæde, før de bruges i modeludvikling.               |   1    |  D/V  |
| 3.5.4 | Bekræft, at modeludviklingsartefakter (hyperparametre, træningsscripts, konfigurationsfiler) gemmes i versionskontrol og kræver godkendelse fra kollegaer, før de anvendes i træning.   |   2    |   D   |

---

## C3.6 Model Pensionering & Udrangering

Modeller skal sikkert udfases, når de ikke længere er nødvendige, eller når sikkerhedsproblemer identificeres.

|   #   | Beskrivelse                                                                                                                                                                                                                            | Niveau | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 3.6.1 | Bekræft, at modelafviklingsprocesser automatisk gennemgår afhængighedsgrafer, identificerer alle forbrugende systemer og giver forhåndsaftalte varselsperioder, inden afvikling.                                                       |   1    |   D   |
| 3.6.2 | Bekræft, at pensionerede modelartefakter slettes sikkert ved hjælp af kryptografisk sletning eller multi-pass overskrivning i overensstemmelse med dokumenterede politikker for datalagring med verificerede destruktionscertifikater. |   1    |  D/V  |
| 3.6.3 | Bekræft, at modelpensio\-neringsbegivenheder logges med tidsstempel og aktøridentitet, og at model-signaturer tilbagekaldes for at forhindre genbrug.                                                                                  |   2    |   V   |
| 3.6.4 | Bekræft, at nødmodel-fasthævelse kan deaktivere modeladgang inden for forudbestemte nødresponstidsrammer via automatiserede afbrydelsesbryder, hvis kritiske sikkerheds-sårbarheder opdages.                                           |   2    |  D/V  |

---

## Referencer

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

