# 9 Autonom orkestrering og agentisk handlingssikkerhed

## Kontrolmål

Sørg for, at autonome eller multi-agent AI-systemer kun kan udføre handlinger, der er eksplicit tiltænkt, autentificeret, reviderbare og inden for afgrænsede omkostnings- og risikogrenser. Dette beskytter mod trusler såsom kompromittering af autonome systemer, misbrug af værktøjer, agentloop-detektion, kapring af kommunikation, identitetsspoofing, sværmmanipulation og hensigtsmanipulation.

---

## 9.1 Agentopgaveplanlægning og rekursionsbudgetter

Begræns rekursive planer og kræv menneskelige kontrolpunkter for privilegerede handlinger.

|   #   | Beskrivelse                                                                                                                                                                                | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 9.1.1 | Bekræft, at maksimal rekursionsdybde, bredde, vægurstid, tokens og monetære omkostninger pr. agentudførelse er centralt konfigureret og versionsstyret.                                    |   1    |  D/V  |
| 9.1.2 | Bekræft, at privilegerede eller irreversible handlinger (f.eks. kodeindsendelser, finansielle overførsler) kræver eksplicit menneskelig godkendelse via en auditerbar kanal før udførelse. |   1    |  D/V  |
| 9.1.3 | Bekræft, at realtidsressourcemonitorer udløser afbrydelse via kredsløbsafbryder, når nogen budgetgrænse overskrides, og stopper yderligere opgaveudvidelse.                                |   2    |   D   |
| 9.1.4 | Bekræft, at circuit-breaker-hændelser logges med agent-ID, udløsende betingelse og optaget planstatus til retsmedicinsk gennemgang.                                                        |   2    |  D/V  |
| 9.1.5 | Bekræft, at sikkerhedstests dækker budget-udtømnings- og løbe-amok-plan-scenarier, og sikrer sikker standsning uden datatab.                                                               |   3    |   V   |
| 9.1.6 | Bekræft, at budgetpolitikker er udtrykt som policy-som-kode og håndhæves i CI/CD for at forhindre konfigurationsdrift.                                                                     |   3    |   D   |

---

## 9.2 Værktøjsplugin Sandboxing

Isolér værktøjsinteraktioner for at forhindre uautoriseret systemadgang eller kodeeksekvering.

|   #   | Beskrivelse                                                                                                                                                              | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 9.2.1 | Bekræft, at hvert værktøj/plugin kører inden for et OS-, container- eller WASM-niveau sandbox med mindst-privilegier for filsystem-, netværks- og systemkaldspolitikker. |   1    |  D/V  |
| 9.2.2 | Bekræft, at begrænsninger for sandbox-ressourcer (CPU, hukommelse, disk, netværksudgående trafik) og udførelsestidsgrænser håndhæves og logges.                          |   1    |  D/V  |
| 9.2.3 | Bekræft, at værktøjsbinærer eller beskrivelser er digitalt signerede; signaturer valideres før indlæsning.                                                               |   2    |  D/V  |
| 9.2.4 | Bekræft, at sandbox-telemetri strømmer til en SIEM; afvigelser (f.eks. forsøg på udgående forbindelser) udløser alarmer.                                                 |   2    |   V   |
| 9.2.5 | Bekræft, at højrisko-plugins gennemgår sikkerhedsvurdering og penetrationstest, inden de tages i brug i produktion.                                                      |   3    |   V   |
| 9.2.6 | Bekræft, at forsøg på at undslippe sandbox automatisk bliver blokeret, og at den overtrædende plugin sættes i karantæne, indtil efterforskning er afsluttet.             |   3    |  D/V  |

---

## 9.3 Autonom løkke og omkostningsbegrænsning

Registrer og stop ukontrolleret agent-til-agent rekursion og omkostningseksplosioner.

|   #   | Beskrivelse                                                                                                                   | Niveau | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 9.3.1 | Bekræft, at opkald mellem agenter inkluderer en hop-grænse eller TTL, som runtime-miljøet tæller ned og håndhæver.            |   1    |  D/V  |
| 9.3.2 | Bekræft, at agenter opretholder et unikt invocation-graph ID for at opdage selv-påberåbelse eller cykliske mønstre.           |   2    |   D   |
| 9.3.3 | Bekræft, at akkumulerede compute-unit og forbrugs-tællere spores pr. anmodningskæde; overskridelse af grænsen afbryder kæden. |   2    |  D/V  |
| 9.3.4 | Bekræft, at formel analyse eller modelkontrol demonstrerer fraværet af ubegrænset rekursion i agentprotokoller.               |   3    |   V   |
| 9.3.5 | Bekræft, at loop-afbruds-begivenheder genererer advarsler og leverer målinger til løbende forbedring.                         |   3    |   D   |

---

## 9.4 Beskyttelse mod misbrug på protokolniveau

Sikre kommunikationskanaler mellem agenter og eksterne systemer for at forhindre kapring eller manipulation.

|   #   | Beskrivelse                                                                                                                                 | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 9.4.1 | Bekræft, at alle agent-til-værktøj og agent-til-agent beskeder er autentificerede (f.eks. gensidig TLS eller JWT) og end-to-end krypterede. |   1    |  D/V  |
| 9.4.2 | Sørg for, at skemaer er strengt validerede; ukendte felter eller fejlbehæftede meddelelser afvises.                                         |   1    |   D   |
| 9.4.3 | Bekræft, at integritetskontroller (MAC'er eller digitale signaturer) dækker hele meddelelsens nyttelast, inklusive værktøjsparametre.       |   2    |  D/V  |
| 9.4.4 | Bekræft, at gengivelsesbeskyttelse (noncer eller tidsstempelvinduer) håndhæves på protokolniveau.                                           |   2    |   D   |
| 9.4.5 | Bekræft, at protokolimplementeringer gennemgår fuzzing og statisk analyse for injektions- eller deserialiseringsfejl.                       |   3    |   V   |

---

## 9.5 Agentidentitet og Manipulationssikkerhed

Sørg for, at handlinger kan tilskrives, og at ændringer kan opdages.

|   #   | Beskrivelse                                                                                                                     | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 9.5.1 | Bekræft, at hver agentinstans har en unik kryptografisk identitet (nøglepar eller hardware-forankret legitimationsoplysninger). |   1    |  D/V  |
| 9.5.2 | Bekræft, at alle agenthandlinger er underskrevet og tidsstemplet; logfiler inkluderer signaturen for ikke-afvisning.            |   2    |  D/V  |
| 9.5.3 | Bekræft, at manipulationssikre logs gemmes i et kun-tilføj eller skriv-en-gang medie.                                           |   2    |   V   |
| 9.5.4 | Bekræft, at identitetsnøgler roterer efter en defineret tidsplan og ved tegn på kompromittering.                                |   3    |   D   |
| 9.5.5 | Bekræft, at forsøg på spoofing eller nøglekonflikt straks udløser karantæne af den berørte agent.                               |   3    |  D/V  |

---

## 9.6 Multi-Agent Swarm Risikoreduktion

Afbød kollektive adfærdssikkerhedsrisici gennem isolation og formel sikkerhedsmodellering.

|   #   | Beskrivelse                                                                                                                                | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 9.6.1 | Bekræft, at agenter, der opererer i forskellige sikkerhedsdomaener, kører i isolerede runtime-sandboxe eller netværkssegmenter.            |   1    |  D/V  |
| 9.6.2 | Bekræft, at sværmadfærd modelleres og formelt verificeres for livlighed og sikkerhed inden implementering.                                 |   3    |   V   |
| 9.6.3 | Bekræft, at runtime-monitors opdager fremspirende usikre mønstre (f.eks. oscillationer, deadlocks) og igangsætter korrigerende handlinger. |   3    |   D   |

---

## 9.7 Bruger- og værktøjsautentificering / -autorisation

Implementer robuste adgangskontroller for hver agent-udløste handling.

|   #   | Beskrivelse                                                                                                                                    | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 9.7.1 | Bekræft, at agenter godkender som førsteklasses principper til downstream-systemer og aldrig genbruger slutbrugerens legitimationsoplysninger. |   1    |  D/V  |
| 9.7.2 | Verificer, at detaljerede autorisationspolitikker begrænser, hvilke værktøjer en agent må anvende, og hvilke parametre den må angive.          |   2    |   D   |
| 9.7.3 | Bekræft, at privilegietjek genvurderes ved hvert opkald (kontinuerlig autorisation), ikke kun ved sessionens start.                            |   2    |   V   |
| 9.7.4 | Bekræft, at delegerede privilegier udløber automatisk og kræver gensamtykke efter timeout eller ændring i omfang.                              |   3    |   D   |

---

## 9.8 Agent-til-Agent Kommunikationssikkerhed

Krypter og beskytt integriteten af alle beskeder mellem agenter for at forhindre aflytning og manipulation.

|   #   | Beskrivelse                                                                                                                         | Niveau | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 9.8.1 | Bekræft, at gensidig autentificering og perfekt-fremad-sikker kryptering (f.eks. TLS 1.3) er obligatorisk for agentkanaler.         |   1    |  D/V  |
| 9.8.2 | Bekræft, at meddelelsens integritet og oprindelse valideres, før den behandles; fejl udløser advarsler og afvisning af meddelelsen. |   1    |   D   |
| 9.8.3 | Bekræft, at kommunikationsmetadata (tidsstempler, sekvensnumre) bliver logget for at understøtte retsmedicinsk rekonstruktion.      |   2    |  D/V  |
| 9.8.4 | Bekræft, at formel verifikation eller modelkontrol bekræfter, at protokoltilstandsmaskiner ikke kan bringes ind i usikre tilstande. |   3    |   V   |

---

## 9.9 Intentverifikation og håndhævelse af begrænsninger

Bekræft, at agentens handlinger stemmer overens med brugerens angivne intention og systemets begrænsninger.

|   #   | Beskrivelse                                                                                                                                                         | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 9.9.1 | Bekræft, at constraint-løsere før udførelse kontrollerer foreslåede handlinger mod hardkodede sikkerheds- og politikregler.                                         |   1    |   D   |
| 9.9.2 | Bekræft, at handlinger med høj påvirkning (finansielle, destruktive, privatlivsfølsomme) kræver eksplicit hensigtsbekræftelse fra den igangsættende bruger.         |   2    |  D/V  |
| 9.9.3 | Bekræft, at post-betingelsestjek validerer, at afsluttede handlinger opnåede tilsigtede effekter uden bivirkninger; uoverensstemmelser udløser tilbageførsel.       |   2    |   V   |
| 9.9.4 | Bekræft, at formelle metoder (f.eks. modelkontrol, teorembevis) eller egenskabsbaserede tests demonstrerer, at agentplaner opfylder alle erklærede begrænsninger.   |   3    |   V   |
| 9.9.5 | Sørg for, at hændelser med intention-mismatch eller overtrædelse af begrænsninger bidrager til kontinuerlige forbedringscyklusser og deling af trusselsinformation. |   3    |   D   |

---

## 9.10 Agentbegrænsningsstrategi Sikkerhed

Sikker udvælgelse og udførelse af forskellige ræsonneringsstrategier herunder ReAct, Chain-of-Thought og Tree-of-Thoughts tilgange.

|   #    | Beskrivelse                                                                                                                                                                                                                | Niveau | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 9.10.1 | Bekræft, at valg af ræsonneringsstrategi bruger deterministiske kriterier (inputkompleksitet, opgavetype, sikkerhedskontekst), og at identiske input producerer identiske strategivalg inden for samme sikkerhedskontekst. |   1    |  D/V  |
| 9.10.2 | Bekræft, at hver ræsonneringsstrategi (ReAct, Chain-of-Thought, Tree-of-Thoughts) har dedikeret inputvalidering, outputsanitering og eksekveringstidbegrænsninger, der er specifikke for dens kognitive tilgang.           |   1    |  D/V  |
| 9.10.3 | Bekræft, at overgange i ræsonneringsstrategi logges med fuldstændig kontekst, herunder inputkarakteristika, værdier for udvælgelseskriterier og eksekveringsmetadata til rekonstruktion af revisionsspor.                  |   2    |  D/V  |
| 9.10.4 | Bekræft, at Tree-of-Thoughts-argumentation inkluderer grenbeskæringsmekanismer, der afslutter udforskning, når politikovertrædelser, ressourcebegrænsninger eller sikkerhedsgrænser opdages.                               |   2    |  D/V  |
| 9.10.5 | Bekræft, at ReAct (Reason-Act-Observe)-cyklusser inkluderer valideringskontrolpunkter i hver fase: verifikation af ræsonneringstrin, handlingstilladelse og observationrensning, før der fortsættes.                       |   2    |  D/V  |
| 9.10.6 | Bekræft, at præstationsmål for ræsonneringsstrategi (eksekveringstid, ressourceforbrug, outputkvalitet) overvåges med automatiserede advarsler, når målene afviger ud over konfigurerede grænseværdier.                    |   3    |  D/V  |
| 9.10.7 | Verificer, at hybride ræsonneringstilgange, der kombinerer flere strategier, opretholder inputvalidering og outputbegrænsninger for alle indgående strategier uden at omgå nogen sikkerhedskontroller.                     |   3    |  D/V  |
| 9.10.8 | Bekræft, at sikkerhedstest af ræsonneringsstrategi inkluderer fuzzing med fejlbehæftede input, fjendtlige prompts designet til at tvinge strategiændring samt test af grænsetilstande for hver kognitiv tilgang.           |   3    |  D/V  |

---

## 9.11 Agentens livscyklusstatusstyring og sikkerhed

Sikker agentinitialisering, tilstandsovergange og afslutning med kryptografiske revisionsspor og definerede genopretningsprocedurer.

|   #    | Beskrivelse                                                                                                                                                                                                                                                                                              | Niveau | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 9.11.1 | Bekræft, at agentinitialisering inkluderer etablering af kryptografisk identitet med hardware-understøttede legitimationsoplysninger og uforanderlige opstartsrevisionslogfiler, der indeholder agent-ID, tidsstempel, konfigurationshash og initialiseringsparametre.                                   |   1    |  D/V  |
| 9.11.2 | Bekræft, at agentens tilstandsændringer er kryptografisk underskrevet, tidsstemplet og logget med fuldstændig kontekst, herunder udløsende begivenheder, tidligere tilstandshash, ny tilstandshash og udførte sikkerhedsvalideringer.                                                                    |   2    |  D/V  |
| 9.11.3 | Bekræft, at agentens nedlukningsprocedurer inkluderer sikker hukommelsesrensning ved hjælp af kryptografisk sletning eller multi-gennemskrivning, tilbagekaldelse af legitimationsoplysninger med underretning til certifikatmyndigheden, samt generering af manipulationssikre afslutningscertifikater. |   2    |  D/V  |
| 9.11.4 | Bekræft, at agentens genopretningsmekanismer validerer tilstandsintegritet ved hjælp af kryptografiske kontrolsummer (mindst SHA-256) og ruller tilbage til kendte gode tilstande, når korruption opdages, med automatiserede alarmer og krav om manuel godkendelse.                                     |   3    |  D/V  |
| 9.11.5 | Bekræft, at agentens vedholdenhedsmekanismer krypterer følsomme tilstandsdata med per-agent AES-256-nøgler og implementerer sikker nøgleudskiftning efter konfigurerbare tidsplaner (maksimalt 90 dage) med nul nedetid ved implementering.                                                              |   3    |  D/V  |

---

## 9.12 Værktøjsintegrationssikkerhedsramme

Sikkerhedskontroller for dynamisk værktøjsindlæsning, udførelse og resultatvalidering med definerede risikovurderings- og godkendelsesprocesser.

|   #    | Beskrivelse                                                                                                                                                                                                                                                        | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 9.12.1 | Bekræft, at værktøjsbeskrivelser indeholder sikkerhedsmetadata, der specificerer nødvendige privilegier (læs/skrive/udfør), risikoniveauer (lav/mellem/høj), ressourcebegrænsninger (CPU, hukommelse, netværk) og valideringskrav dokumenteret i værktøjsmanifest. |   1    |  D/V  |
| 9.12.2 | Bekræft, at værktøjets udførelsesresultater valideres i forhold til forventede skemaer (JSON Schema, XML Schema) og sikkerhedspolitikker (outputsanitering, dataklassificering) før integration med timeout-grænser og fejlbehandlingsprocedurer.                  |   1    |  D/V  |
| 9.12.3 | Bekræft, at værktøjsinteraktionslogfiler inkluderer detaljeret sikkerhedskontekst, herunder brug af privilegier, dataadgangsmønstre, eksekveringstid, ressourceforbrug og returkoder med struktureret logning til SIEM-integration.                                |   2    |  D/V  |
| 9.12.4 | Bekræft, at dynamiske værktøjsindlæsningsmekanismer validerer digitale signaturer ved hjælp af PKI-infrastruktur og implementerer sikre indlæsningsprotokoller med sandbox-isolation og tilladelsesverifikation før eksekvering.                                   |   2    |  D/V  |
| 9.12.5 | Bekræft, at værktøjssikkerhedsvurderinger automatisk udløses for nye versioner med obligatoriske godkendelsesporte, herunder statisk analyse, dynamisk test og sikkerhedsteamets gennemgang med dokumenterede godkendelseskriterier og SLA-krav.                   |   3    |  D/V  |

---

### Referencer

* [MITRE ATLAS tactics ML09](https://atlas.mitre.org/)
* [Circuit-breaker research for AI agents — Zou et al., 2024](https://arxiv.org/abs/2406.04313)
* [Trend Micro analysis of sandbox escapes in AI agents — Park, 2025](https://www.trendmicro.com/vinfo/us/security/news/cybercrime-and-digital-threats/unveiling-ai-agent-vulnerabilities-code-execution)
* [Auth0 guidance on human-in-the-loop authorization for agents — Martinez, 2025](https://auth0.com/blog/secure-human-in-the-loop-interactions-for-ai-agents/)
* [Medium deep-dive on MCP & A2A protocol hijacking — ForAISec, 2025](https://medium.com/%40foraisec/security-analysis-potential-ai-agent-hijacking-via-mcp-and-a2a-protocol-insights-cd1ec5e6045f)
* [Rapid7 fundamentals on spoofing attack prevention — 2024](https://www.rapid7.com/fundamentals/spoofing-attacks/)
* [Imperial College verification of swarm systems — Lomuscio et al.](https://sail.doc.ic.ac.uk/projects/swarms/)
* [NIST AI Risk Management Framework 1.0, 2023](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [WIRED security briefing on encryption best practices, 2024](https://www.wired.com/story/encryption-apps-chinese-telecom-hacking-hydra-russia-exxon)
* [OWASP Top 10 for LLM Applications, 2025](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Comprehensive Vulnerability Analysis is Necessary for Trustworthy LLM-MAS](https://arxiv.org/html/2506.01245v1)
* [How Is LLM Reasoning Distracted by Irrelevant Context?
  An Analysis Using a Controlled Benchmark](https://www.arxiv.org/pdf/2505.18761)
* [Large Language Model Sentinel: LLM Agent for Adversarial Purification](https://arxiv.org/pdf/2405.20770)
* [Securing Agentic AI: A Comprehensive Threat Model and Mitigation Framework for Generative AI Agents](https://arxiv.org/html/2504.19956v2)

