# C1 Træningsdataforvaltning & Håndtering af bias

## Kontrolmål

Træningsdata skal indsamles, håndteres og vedligeholdes på en måde, der bevarer oprindelse, sikkerhed, kvalitet og retfærdighed. Dette opfylder juridiske forpligtelser og reducerer risikoen for bias, forgiftning eller brud på privatlivets fred, som kan opstå under træningen og påvirke hele AI-livscyklussen.

---

## C1.1 Oprindelse af træningsdata

Oprethold et verificerbart inventar over alle datasæt, accepter kun betroede kilder, og log hver ændring for revisionssikkerhed.

|   #   | Beskrivelse                                                                                                                                                                                    | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 1.1.1 | Bekræft, at der vedligeholdes en opdateret oversigt over alle træningsdatakilder (oprindelse, forvalter/ejer, licens, indsamlingmetode, tilsigtede brugsbegrænsninger og behandlingshistorik). |   1    |  D/V  |
| 1.1.2 | Bekræft, at træningsdata-processer udelukker unødvendige funktioner, attributter eller felter (f.eks. ubrugt metadata, følsomme persondata, lækket testdata).                                  |   1    |  D/V  |
| 1.1.3 | Bekræft, at alle ændringer i datasættet er underlagt en registreret godkendelsesproces.                                                                                                        |   2    |  D/V  |
| 1.1.4 | Sørg for, at datasæt eller delmængder er vandmærket eller fingeraftrykt, hvor det er muligt.                                                                                                   |   3    |  D/V  |

---

## C1.2 Sikkerhed og Integritet af Træningsdata

Begræns adgangen til træningsdata, krypter det både i hvile og under overførsel, og valider dets integritet for at forhindre manipulation, tyveri eller datamisbrug.

|   #   | Beskrivelse                                                                                                                                                                   | Niveau | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 1.2.1 | Bekræft, at adgangskontroller beskytter lagring af træningsdata og pipelines.                                                                                                 |   1    |  D/V  |
| 1.2.2 | Bekræft, at al adgang til træningsdata logges, inklusive bruger, tid og handling.                                                                                             |   2    |  D/V  |
| 1.2.3 | Bekræft, at træningsdatasæt er krypteret under overførsel og i hvile, ved brug af branchesstandard kryptografiske algoritmer og nøglehåndteringsmetoder.                      |   2    |  D/V  |
| 1.2.4 | Bekræft, at kryptografiske hashes eller digitale signaturer bruges til at sikre dataintegritet under lagring og overførsel af træningsdata.                                   |   2    |  D/V  |
| 1.2.5 | Bekræft, at automatiserede detektionsteknikker anvendes til at beskytte mod uautoriserede ændringer eller korruption af træningsdata.                                         |   2    |  D/V  |
| 1.2.6 | Sørg for, at forældede træningsdata bliver sikkert slettet eller anonymiseret.                                                                                                |   2    |  D/V  |
| 1.2.7 | Sørg for, at alle versioner af træningsdatasættet er entydigt identificeret, lagret uforanderligt og reviderbare for at understøtte tilbagetrækning og retsmedicinsk analyse. |   3    |  D/V  |

---

## C1.3 Kvalitet, integritet og sikkerhed for træningsdatalabeling

Beskyt etiketter og kræv teknisk gennemgang for kritiske data.

|   #   | Beskrivelse                                                                                                                                                                                                   | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 1.3.1 | Bekræft, at kryptografiske hashværdier eller digitale signaturer anvendes på mærkningsartefakter for at sikre deres integritet og ægthed.                                                                     |   2    |  D/V  |
| 1.3.2 | Verificer, at mærkningsgrænseflader og platforme håndhæver stærke adgangskontroller, opretholder manipulationssikre revisionslogfiler for alle mærkningsaktiviteter og beskytter mod uautoriserede ændringer. |   2    |  D/V  |
| 1.3.3 | Bekræft, at følsomme oplysninger i etiketter er maskeret, anonymiseret eller krypteret på datafeltniveau både i hvile og under overførsel.                                                                    |   3    |  D/V  |

---

## C1.4 Kvalitet af træningsdata og sikring af sikkerhed

Kombiner automatiseret validering, manuel stikprøvekontrol og logget afhjælpning for at garantere datasæt-pålidelighed.

|   #   | Beskrivelse                                                                                                                                                                                                                                                                                                                                                                                                          | Niveau | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 1.4.1 | Bekræft, at automatiserede tests fanger formateringsfejl og null-værdier ved hver indlæsning eller væsentlig datatransformation.                                                                                                                                                                                                                                                                                     |   1    |   D   |
| 1.4.2 | Sørg for, at LLM-trænings- og finjusteringspipelines implementerer forgiftningsdetektion og validering af dataintegritet (f.eks. statistiske metoder, outlier-detektion, indlejringsanalyse) for at identificere potentielle forgiftningsangreb (f.eks. label-flipping, indsættelse af backdoor-triggers, rolleombytningskommandoer, indflydelsesrige instansangreb) eller utilsigtet datakorruption i træningsdata. |   2    |  D/V  |
| 1.4.3 | Bekræft, at passende forsvar, såsom modstridstræning (ved brug af genererede modstridende eksempler), dataforøgelse med perturbede input eller robuste optimeringsteknikker, er implementeret og justeret for relevante modeller baseret på risikovurdering.                                                                                                                                                         |   3    |  D/V  |
| 1.4.4 | Bekræft, at automatisk genererede etiketter (f.eks. via LLM'er eller svag supervision) er underlagt tillidsgrænser og konsistenskontroller for at opdage hallucinerede, vildledende eller lavtillids-etiketter.                                                                                                                                                                                                      |   2    |  D/V  |
| 1.4.5 | Bekræft, at automatiserede tests opdager label-skævheder ved hver indlæsning eller væsentlig datatransformation.                                                                                                                                                                                                                                                                                                     |   3    |   D   |

---

## C1.5 Data Stifternes Oprindelse og Sporbarhed

Spor hele rejsen for hvert datapunkt fra kilde til modelinput for revisionssporbarhed og hændelsesrespons.

|   #   | Beskrivelse                                                                                                                                                                                                                      | Niveau | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 1.5.1 | Bekræft, at afstamningen for hvert datapunkt, inklusive alle transformationer, augmentationer og sammenlægninger, er registreret og kan rekonstrueres.                                                                           |   2    |  D/V  |
| 1.5.2 | Bekræft, at slægtsoplysninger er uforanderlige, sikkert opbevaret og tilgængelige til revision.                                                                                                                                  |   2    |  D/V  |
| 1.5.3 | Bekræft, at sporing af oprindelse dækker syntetiske data, der genereres via privatlivsbevarende eller generative teknikker, og at alle syntetiske data tydeligt er mærket og kan skelnes fra rigtige data gennem hele processen. |   2    |  D/V  |

---

## Referencer

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [EU AI Act – Article 10: Data & Data Governance](https://artificialintelligenceact.eu/article/10/)
* [MITRE ATLAS: Adversary Tactics for AI](https://atlas.mitre.org/)
* [Survey of ML Bias Mitigation Techniques – MDPI](https://www.mdpi.com/2673-6470/4/1/1)
* [Data Provenance & Lineage Best Practices – Nightfall AI](https://www.nightfall.ai/ai-security-101/data-provenance-and-lineage)
* [Data Labeling Quality Standards – LabelYourData](https://labelyourdata.com/articles/data-labeling-quality-and-how-to-measure-it)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [CISA Advisory: Securing Data for AI Systems](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [ISO/IEC 23053: AI Management Systems Framework](https://www.iso.org/sectors/it-technologies/ai)
* [IBM: What is AI Governance?](https://www.ibm.com/think/topics/ai-governance)
* [Google AI Principles](https://ai.google/principles/)
* [GDPR & AI Training Data – DataProtectionReport](https://www.dataprotectionreport.com/2024/08/recent-regulatory-developments-in-training-artificial-intelligence-ai-models-under-the-gdpr/)
* [Supply-Chain Security for AI Data – AppSOC](https://www.appsoc.com/blog/ai-is-the-new-frontier-of-supply-chain-security)
* [OpenAI Privacy Center – Data Deletion Controls](https://privacy.openai.com/policies?modal=take-control)
* [Adversarial ML Dataset – Kaggle](https://www.kaggle.com/datasets/cnrieiit/adversarial-machine-learning-dataset)

