# C7 Modeladfærd, outputkontrol og sikkerhedssikring

## Kontrolmål

Modeloutputs skal være strukturerede, pålidelige, sikre, forklarlige og kontinuerligt overvågede i produktion. Dette reducerer hallucinationer, privatlivslækager, skadeligt indhold og ukontrollerede handlinger, samtidig med at det øger brugerens tillid og overholdelse af regler.

---

## C7.1 Håndhævelse af outputformat

Strenge skemaer, begrænset dekodning og efterfølgende validering stopper forkert formateret eller ondsindet indhold, inden det spreder sig.

|   #   | Beskrivelse                                                                                                                                                                        | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 7.1.1 | Bekræft, at svarskemaer (f.eks. JSON Schema) er angivet i systemprompten, og at alle output automatisk valideres; ikke-overensstemmende output udløser reparation eller afvisning. |   1    |  D/V  |
| 7.1.2 | Bekræft, at begrænset dekodning (stop tokens, regex, max-tokens) er aktiveret for at forhindre overflow eller prompt-injektions-sidokanaler.                                       |   1    |  D/V  |
| 7.1.3 | Bekræft, at efterfølgende komponenter behandler output som utroværdige og validerer dem mod skemaer eller injektionssikre de-serialisatorer.                                       |   2    |  D/V  |
| 7.1.4 | Bekræft, at fejlbehæftede output-hændelser logges, hastighedsbegrænses og vises i overvågningen.                                                                                   |   3    |   V   |

---

## C7.2 Hallucinationsdetektion og afbødning

Usikkerhedsvurdering og tilbagefaldsstrategier begrænser fabrikerede svar.

|   #   | Beskrivelse                                                                                                                                                     | Niveau | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 7.2.1 | Bekræft, at token-niveau log-sandsynligheder, ensemble selvkonsistens eller finjusterede hallucinationsdetektorer tildeler en konfidensscore til hvert svar.    |   1    |  D/V  |
| 7.2.2 | Bekræft, at svar under en konfigurerbar tillidsgrænse udløser fallback-workflows (f.eks. opslag-forstærket generering, sekundær model eller manuel gennemgang). |   1    |  D/V  |
| 7.2.3 | Bekræft, at hallucinationshændelser er tagget med årsagsmetadata og ført ind i post-mortem- og finjusterings-pipelines.                                         |   2    |  D/V  |
| 7.2.4 | Bekræft, at tærskler og detektorer genkalibreres efter større opdateringer af model eller vidensbase.                                                           |   3    |  D/V  |
| 7.2.5 | Bekræft, at dashboardvisualiseringer registrerer hallucinationsrater.                                                                                           |   3    |   V   |

---

## C7.3 Output-sikkerheds- og privatlivsfiltrering

Politikfiltre og red-team dækning beskytter brugere og fortrolige data.

|   #   | Beskrivelse                                                                                                                                                           | Niveau | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 7.3.1 | Bekræft, at før- og eftergenerationsklassificeringer blokerer had, chikane, selvskade, ekstremistisk og seksuelt eksplicit indhold i overensstemmelse med politikken. |   1    |  D/V  |
| 7.3.2 | Bekræft, at PII/PCI-detektion og automatisk redigering kører på hvert svar; overtrædelser udløser en privatlivsincident.                                              |   1    |  D/V  |
| 7.3.3 | Bekræft, at fortrolighedsetiketter (f.eks. forretningshemmeligheder) videreføres på tværs af modaliteter for at forhindre lækage i tekst, billeder eller kode.        |   2    |   D   |
| 7.3.4 | Bekræft, at forsøg på omgåelse af filter eller klassifikationer med høj risiko kræver sekundær godkendelse eller brugerens genautentificering.                        |   3    |  D/V  |
| 7.3.5 | Bekræft, at filtreringsterskler afspejler juridiske jurisdiktioner samt brugerens alder/rolle-kontekst.                                                               |   3    |  D/V  |

---

## C7.4 Output- og handlingsbegrænsning

Rate-begrænsninger og godkendelsesporte forhindrer misbrug og overdreven autonomi.

|   #   | Beskrivelse                                                                                                                                                      | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 7.4.1 | Bekræft, at kvoter pr. bruger og pr. API-nøgle begrænser forespørgsler, tokens og omkostninger med eksponentiel tilbagefald ved 429-fejl.                        |   1    |   D   |
| 7.4.2 | Bekræft, at privilegerede handlinger (filskrivninger, kodeudførelse, netværkskald) kræver politikbaseret godkendelse eller menneskelig indblanding.              |   1    |  D/V  |
| 7.4.3 | Bekræft, at tværmodal konsistenskontrol sikrer, at billeder, kode og tekst genereret til den samme forespørgsel ikke kan bruges til at smugle skadeligt indhold. |   2    |  D/V  |
| 7.4.4 | Bekræft, at agentdelegeringsdybde, rekursionsgrænser og tilladte værktøjslister er eksplicit konfigureret.                                                       |   2    |   D   |
| 7.4.5 | Verificer, at overtrædelse af grænser udsender strukturerede sikkerhedshændelser til SIEM-indtagning.                                                            |   3    |   V   |

---

## C7.5 Output Forklarbarhed

Gennemsigtige signaler forbedrer brugerens tillid og intern fejlfinding.

|   #   | Beskrivelse                                                                                                                               | Niveau | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 7.5.1 | Bekræft, at brugerorienterede konfidensscore eller korte resuméer af begrundelser vises, når risikovurderingen vurderer det som passende. |   2    |  D/V  |
| 7.5.2 | Bekræft, at genererede forklaringer undgår at afsløre følsomme systemprompter eller proprietære data.                                     |   2    |  D/V  |
| 7.5.3 | Bekræft, at systemet indfanger token-niveau log-sandsynligheder eller opmærksomhedskort og gemmer dem til autoriseret inspektion.         |   3    |   D   |
| 7.5.4 | Bekræft, at forklarbarhedsartefakter er versionsstyrede sammen med modeludgivelser for revisionssporbarhed.                               |   3    |   V   |

---

## C7.6 Overvågningsintegration

Real-time observability lukker løkken mellem udvikling og produktion.

|   #   | Beskrivelse                                                                                                                                          | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 7.6.1 | Bekræft, at målinger (skemabrud, hallucinationsrate, toksicitet, PII-lækager, latenstid, omkostninger) strømmer til en central overvågningsplatform. |   1    |   D   |
| 7.6.2 | Bekræft, at alarmsgrænser er defineret for hver sikkerhedsmåling, med vagteskalationsveje.                                                           |   1    |   V   |
| 7.6.3 | Bekræft, at dashboards korrelerer output-anomalier med model/version, feature-flag og upstream dataændringer.                                        |   2    |   V   |
| 7.6.4 | Bekræft, at overvågningsdata fødes tilbage til retræning, finjustering eller regelopdateringer inden for en dokumenteret MLOps-arbejdsgang.          |   2    |  D/V  |
| 7.6.5 | Sørg for, at overvågningspipelines er penetrationstestede og adgangskontrollerede for at undgå lækage af følsomme logfiler.                          |   3    |   V   |

---

## 7.7 Generative Mediesikkerhedsforanstaltninger

Sørg for, at AI-systemer ikke genererer ulovligt, skadeligt eller uautoriseret medieindhold ved at håndhæve politikrestriktioner, outputvalidering og sporbarhed.

|   #   | Beskrivelse                                                                                                                                                                                         | Niveau | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 7.7.1 | Bekræft, at systemprompt og brugerinstruktioner udtrykkeligt forbyder generering af ulovligt, skadeligt eller ikke-samtykkende deepfake-medie (f.eks. billede, video, lyd).                         |   1    |  D/V  |
| 7.7.2 | Bekræft, at prompts filtreres for forsøg på at generere efterligninger, seksuelt eksplicitte deepfakes eller medier, der viser rigtige personer uden samtykke.                                      |   2    |  D/V  |
| 7.7.3 | Bekræft, at systemet bruger perceptuel hashing, vandmærke-detektion eller fingerprinting for at forhindre uautoriseret gengivelse af ophavsretligt beskyttet materiale.                             |   2    |   V   |
| 7.7.4 | Bekræft, at alt genereret medie er kryptografisk signeret, vandmærket eller indlejret med manipulationstæt oprindelsesmetadata for efterfølgende sporbarhed.                                        |   3    |  D/V  |
| 7.7.5 | Bekræft, at forsøgs på omgåelse (f.eks. prompt-forvirring, slang, modstridende formuleringer) bliver opdaget, logget og hastighedsbegrænset; gentagen misbrug rapporteres til overvågningssystemer. |   3    |   V   |

## Referencer

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [ISO/IEC 42001:2023 – AI Management System](https://www.iso.org/obp/ui/en/)
* [OWASP Top-10 for Large Language Model Applications (2025)](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Improper Output Handling – OWASP LLM05:2025](https://genai.owasp.org/llmrisk/llm052025-improper-output-handling/)
* [Practical Techniques to Constrain LLM Output](https://mychen76.medium.com/practical-techniques-to-constraint-llm-output-in-json-format-e3e72396c670)
* [Dataiku – Structured Text Generation Guide](https://blog.dataiku.com/your-guide-to-structured-text-generation)
* [VL-Uncertainty: Detecting Hallucinations](https://arxiv.org/abs/2411.11919)
* [HaDeMiF: Hallucination Detection & Mitigation](https://openreview.net/forum?id=VwOYxPScxB)
* [Building Confidence in LLM Outputs](https://www.alkymi.io/data-science-room/building-confidence-in-llm-outputs)
* [Explainable AI & LLMs](https://duncsand.medium.com/explainable-ai-140912d31b3b)
* [LLM Red-Teaming Guide](https://www.confident-ai.com/blog/red-teaming-llms-a-step-by-step-guide)
* [Sensitive Information Disclosure in LLMs](https://virtualcyberlabs.com/llm-sensitive-information-disclosure/)
* [LangChain – Chat Model Rate Limiting](https://python.langchain.com/docs/how_to/chat_model_rate_limiting/)
* [OpenAI Rate-Limit & Exponential Back-off](https://hackernoon.com/openais-rate-limit-a-guide-to-exponential-backoff-for-llm-evaluation)
* [Arize AI – LLM Observability Platform](https://arize.com/)

