# C2 Brugerinputvalidering

## Kontrolmål

Robust validering af brugerinput er en førstelinjeforsvar mod nogle af de mest skadelige angreb på AI-systemer. Prompt injection-angreb kan tilsidesætte systeminstruktioner, lække følsomme data eller styre modellen mod adfærd, der ikke er tilladt. Medmindre dedikerede filtre og instruktionshierarkier er på plads, viser forskning, at "multi-shot" jailbreaks, der udnytter meget lange kontekstvinduer, vil være effektive. Også subtile adversariale perturbationsangreb—såsom homoglyf-udskiftninger eller leetspeak—kan stille og roligt ændre en models beslutninger.

---

## C2.1 Forsvar mod promptinjektion

Prompt injection er en af de største risici for AI-systemer. Forsvar mod denne taktik anvender en kombination af statiske mønstermasker, dynamiske klassifikatorer og håndhævelse af instruktionshierarki.

|   #   | Beskrivelse                                                                                                                                                                                                | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 2.1.1 | Bekræft, at brugerinput gennemgås mod et løbende opdateret bibliotek af kendte prompt-injektionsmønstre (jailbreak-nøgleord, "ignorer tidligere", rollespils-kæder, indirekte HTML/URL-angreb).            |   1    |  D/V  |
| 2.1.2 | Bekræft, at systemet håndhæver en instruktionshierarki, hvor system- eller udviklerbeskeder tilsidesætter brugerens instruktioner, selv efter udvidelse af kontekstvinduet.                                |   1    |  D/V  |
| 2.1.3 | Bekræft, at avancerede evaluerings-tests (f.eks. Red Team "many-shot" prompts) køres før hver model- eller prompt-skabelonudgivelse, med succesrategrænser og automatiserede blokeringer for regressioner. |   2    |  D/V  |
| 2.1.4 | Bekræft, at prompts, der stammer fra tredjepartsindhold (websider, PDF'er, e-mails), bliver renset i en isoleret parseringskontekst, inden de bliver sammenkædet i hovedprompten.                          |   2    |   D   |
| 2.1.5 | Bekræft, at alle opdateringer af prompt-filterregler, versioner af klassifikationsmodeller og ændringer i bloklisten er versionsstyrede og kan revideres.                                                  |   3    |  D/V  |

---

## C2.2 Modstandsdygtighed over for adversarielle eksempler

Modeller inden for Natural Language Processing (NLP) er stadig sårbare over for subtile forstyrrelser på tegn- eller ordniveau, som mennesker ofte overser, men som modeller har tendens til at fejlkategorisere.

|   #   | Beskrivelse                                                                                                                                                                                        | Niveau | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 2.2.1 | Bekræft, at grundlæggende inputnormaliseringstrin (Unicode NFC, homoglyphkortlægning, fjernelse af mellemrum) kører før tokenisering.                                                              |   1    |   D   |
| 2.2.2 | Bekræft, at statistisk anomalidetektion markerer input med usædvanligt høj redigeringsafstand til sprognormer, overdreven gentagelse af tokens eller unormale indlejringafstande.                  |   2    |  D/V  |
| 2.2.3 | Bekræft, at inferenspipelinens understøtter valgfrie modelvarianter eller forsvarslag for hærdning gennem modstandertræning (f.eks. randomisering, defensiv destillation) til højrisiko-endpoints. |   2    |   D   |
| 2.2.4 | Sørg for, at mistænkte fjendtlige input bliver sat i karantæne og logget med fulde nyttelaster (efter fjernelse af PII).                                                                           |   2    |   V   |
| 2.2.5 | Sørg for, at robusthedsmål (succesrate for kendte angrebssuiter) overvåges over tid, og at tilbageskridt udløser en udgivelsesblokering.                                                           |   3    |  D/V  |

---

## C2.3 Skema-, type- og længdevalidering

AI-angreb med skadede eller overdimensionerede input kan forårsage parsefejl, promptudslip på tværs af felter og ressourceudtømning. Streng skemahåndhævelse er også en forudsætning ved udførelse af deterministiske værktøjskald.

|   #   | Beskrivelse                                                                                                                                                                               | Niveau | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 2.3.1 | Bekræft, at hvert API- eller funktionskalds-endpoint definerer et eksplicit inputskema (JSON Schema, Protobuf eller multimodal ækvivalent) og at input valideres, før promptsamling sker. |   1    |   D   |
| 2.3.2 | Bekræft, at input, der overskrider de maksimale token- eller bytelimitter, afvises med en sikker fejl og aldrig bliver tavst afkortet.                                                    |   1    |  D/V  |
| 2.3.3 | Bekræft, at typekontroller (f.eks. numeriske intervaller, enum-værdier, MIME-typer for billeder/lyd) håndhæves på serversiden, ikke kun i klientkode.                                     |   2    |  D/V  |
| 2.3.4 | Bekræft, at semantiske validatorer (f.eks. JSON Schema) kører i konstant tid for at forhindre algoritmisk DoS.                                                                            |   2    |   D   |
| 2.3.5 | Bekræft, at valideringsfejl registreres med redigerede nyttedatauddrag og entydige fejlkoder for at lette sikkerhedstriangulering.                                                        |   3    |   V   |

---

## C2.4 Indholds- og politikscreening

Udviklere bør kunne opdage syntaktisk gyldige prompts, der anmoder om ikke-tilladt indhold (såsom ulovlige instruktioner, hadetale og ophavsretligt beskyttet tekst), og derefter forhindre, at disse spredes.

|   #   | Beskrivelse                                                                                                                                                                                  | Niveau | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 2.4.1 | Bekræft, at en indholdsklassificerer (zero shot eller finjusteret) scorer hvert input for vold, selvskade, had, seksuelt indhold og ulovlige anmodninger, med konfigurerbare tærskelværdier. |   1    |   D   |
| 2.4.2 | Bekræft, at input, der overtræder politikker, vil modtage standardiserede afvisninger eller sikre færdiggørelser, så de ikke videreføres til efterfølgende LLM-kald.                         |   1    |  D/V  |
| 2.4.3 | Bekræft, at screeningsmodellen eller regelsættet genuddannes/opdateres mindst kvartalsvis, og at nye observerede jailbreak- eller politikomgåelsesmønstre indarbejdes.                       |   2    |   D   |
| 2.4.4 | Bekræft, at screening overholder brugerspecifikke politikker (alder, regionale lovmæssige begrænsninger) via attributbaserede regler, der løses ved anmodningstidspunktet.                   |   2    |   D   |
| 2.4.5 | Bekræft, at screeningslogs inkluderer klassifikatorens tillidsvurderinger og politikkategori-tags til SOC-korrelation og fremtidig red-team genspilning.                                     |   3    |   V   |

---

## C2.5 Input Rate Begrænsning & Misbrugsforebyggelse

Udviklere bør forhindre misbrug, ressourceudtømning og automatiserede angreb mod AI-systemer ved at begrænse inputhastigheder og opdage unormale brugsmønstre.

|   #   | Beskrivelse                                                                                                                                 | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 2.5.1 | Bekræft, at grænser for hastighed pr. bruger, pr. IP og pr. API-nøgle håndhæves for alle inputendepunkter.                                  |   1    |  D/V  |
| 2.5.2 | Bekræft, at burst- og vedvarende hastighedsbegrænsninger er indstillet til at forhindre DoS- og brute force-angreb.                         |   2    |  D/V  |
| 2.5.3 | Bekræft, at unormale brugsmønstre (f.eks. hurtige anmodninger, input-overbelastning) udløser automatiserede blokeringer eller eskaleringer. |   2    |  D/V  |
| 2.5.4 | Bekræft, at logs for misbrugsforebyggelse opbevares og gennemgås for nye angrebsmønstre.                                                    |   3    |   V   |

---

## C2.6 Multi-Modale Inputvalidering

AI-systemer bør inkludere robust validering af ikke-tekstuelle input (billeder, lyd, filer) for at forhindre injektion, unddragelse eller misbrug af ressourcer.

|   #   | Beskrivelse                                                                                                      | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 2.6.1 | Bekræft, at alle ikke-tekst input (billeder, lyd, filer) valideres for type, størrelse og format før behandling. |   1    |   D   |
| 2.6.2 | Bekræft, at filer scannes for malware og steganografiske payloads før indtagelse.                                |   2    |  D/V  |
| 2.6.3 | Bekræft, at billede-/lydinput kontrolleres for fjendtlige forstyrrelser eller kendte angrebsmønstre.             |   2    |  D/V  |
| 2.6.4 | Bekræft, at fejl i multimodal inputvalidering bliver logget og udløser advarsler til undersøgelse.               |   3    |   V   |

---

## C2.7 Input-kilde og attribution

AI-systemer bør understøtte revision, misbrugsregistrering og overholdelse ved at overvåge og mærke oprindelsen af alle brugerinput.

|   #   | Beskrivelse                                                                                                                | Niveau | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 2.7.1 | Bekræft, at alle brugerinput er markeret med metadata (bruger-ID, session, kilde, tidsstempel, IP-adresse) ved indtagelse. |   1    |  D/V  |
| 2.7.2 | Bekræft, at oprindelsesmetadata bevares og kan revideres for alle behandlede input.                                        |   2    |  D/V  |
| 2.7.3 | Bekræft, at anomaløse eller ikke-pålidelige inputkilder bliver markeret og underlagt forøget kontrol eller blokering.      |   2    |  D/V  |

---

## C2.8 Realtids Tilpasset Trusselsdetektion

Udviklere bør anvende avancerede trusselsdetekteringssystemer til AI, som tilpasser sig nye angrebsmønstre og giver realtidsbeskyttelse med kompileret mønstergenkendelse.

|   #   | Beskrivelse                                                                                                                                                                                | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 2.8.1 | Bekræft, at trusselsdetektionsmønstre er kompileret til optimerede regex-motorer for højtydende realtidsfiltrering med minimal latensepåvirkning.                                          |   1    |  D/V  |
| 2.8.2 | Sørg for, at trusselsdetekteringssystemer opretholder separate mønstrekataloger for forskellige trussels kategorier (promptinjektion, skadeligt indhold, følsomme data, systemkommandoer). |   1    |  D/V  |
| 2.8.3 | Bekræft, at adaptiv trusselsdetektion inkorporerer maskinlæringsmodeller, der opdaterer trusselsfølsomheden baseret på angrebsfrekvens og succesrater.                                     |   2    |  D/V  |
| 2.8.4 | Bekræft, at realtids trusselsintelligensfeeds automatisk opdaterer mønst bibliotekker med nye angrebssignaturer og IOCs (Indicators of Compromise).                                        |   2    |  D/V  |
| 2.8.5 | Bekræft, at falske positive fejlrater for trusselsdetektion løbende overvåges, og at mønsterspecificiteten automatisk tilpasses for at minimere forstyrrelser af legitime brugsscenarier.  |   3    |  D/V  |
| 2.8.6 | Bekræft, at kontekstuel trusselsanalyse tager hensyn til inputkilde, brugeradfærdsmønstre og sessionshistorik for at forbedre detektionsnøjagtigheden.                                     |   3    |  D/V  |
| 2.8.7 | Bekræft, at ydelsesmetriker for trusselsdetektion (detektionsrate, behandlingstidsforsinkelse, ressourceudnyttelse) overvåges og optimeres i realtid.                                      |   3    |  D/V  |

---

## C2.9 Multi-Modal sikkerhedsvalideringspipeline

Udviklere bør levere sikkerhedsvalidering for tekst-, billede-, lyd- og andre AI-inputmodaliteter med specifikke typer trusselsdetektion og ressourceisolation.

|   #   | Beskrivelse                                                                                                                                                                                                                                                 | Niveau | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 2.9.1 | Bekræft, at hver inputmodalitet har dedikerede sikkerhedsvalidatorer med dokumenterede trusselsmønstre (tekst: promptinjektion, billeder: steganografi, lyd: spektrogramangreb) og detektionsgrænser.                                                       |   1    |  D/V  |
| 2.9.2 | Bekræft, at multimodale input behandles i isolerede sandkasser med definerede ressourcebegrænsninger (hukommelse, CPU, behandlingstid), som er specifikke for hver modalitytype og dokumenteret i sikkerhedspolitikker.                                     |   2    |  D/V  |
| 2.9.3 | Bekræft, at detektionssystemet for tværmodal angreb identificerer koordinerede angreb, der spænder over flere inputtyper (f.eks. steganografiske payloads i billeder kombineret med promptinjektion i tekst) ved hjælp af korrelationsregler og alarmering. |   2    |  D/V  |
| 2.9.4 | Bekræft, at multi-modale valideringsfejl udløser detaljeret logning, inklusive alle inputmodaliteter, valideringsresultater, trusselscores og korrelationsanalyse med strukturerede logformater til SIEM-integration.                                       |   3    |  D/V  |
| 2.9.5 | Bekræft, at modalitetsspecifikke indholdsklassifikatorer opdateres i overensstemmelse med dokumenterede tidsplaner (minimum kvartalsvis) med nye trusselsmønstre, adversarielle eksempler og ydeevnebenchmark, der opretholdes over baseline-grænser.       |   3    |  D/V  |

---

## Referencer

* [LLM01:2025 Prompt Injection – OWASP Top 10 for LLM & Generative AI Security](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)
* [Generative AI's Biggest Security Flaw Is Not Easy to Fix](https://www.wired.com/story/generative-ai-prompt-injection-hacking)
* [Many-shot jailbreaking \ Anthropic](https://www.anthropic.com/research/many-shot-jailbreaking)
* [$PDF$ OpenAI GPT-4.5 System Card](https://cdn.openai.com/gpt-4-5-system-card-2272025.pdf)
* [Notebook for the CheckThat Lab at CLEF 2024](https://ceur-ws.org/Vol-3740/paper-53.pdf)
* [Mitigate jailbreaks and prompt injections – Anthropic](https://docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/mitigate-jailbreaks)
* [Chapter 3 MITRE ATT\&CK – Adversarial Model Analysis](https://ama.drwhy.ai/mitre-attck.html)
* [OWASP Top 10 for LLM Applications 2025 – WorldTech IT](https://wtit.com/blog/2025/04/17/owasp-top-10-for-llm-applications-2025/)
* [OWASP Machine Learning Security Top Ten](https://owasp.org/www-project-machine-learning-security-top-10/)
* [Few words about AI Security – Jussi Metso](https://www.jussimetso.com/index.php/2024/09/28/few-words-about-ai-security/)
* [How To Ensure LLM Output Adheres to a JSON Schema | Modelmetry](https://modelmetry.com/blog/how-to-ensure-llm-output-adheres-to-a-json-schema)
* [Easily enforcing valid JSON schema following – API](https://community.openai.com/t/feature-request-function-calling-easily-enforcing-valid-json-schema-following/263515?utm_source)
* [AI Safety + Cybersecurity R\&D Tracker – Fairly AI](https://www.fairly.ai/blog/ai-cybersecurity-tracker)
* [Anthropic makes 'jailbreak' advance to stop AI models producing harmful results](https://www.ft.com/content/cf11ebd8-aa0b-4ed4-945b-a5d4401d186e)
* [Pattern matching filter rules - IBM](https://www.ibm.com/docs/ssw_aix_71/security/intrusion_pattern_matching_filter_rules.html)
* [Real-time Threat Detection](https://www.darktrace.com/cyber-ai-glossary/real-time-threat-detection)

