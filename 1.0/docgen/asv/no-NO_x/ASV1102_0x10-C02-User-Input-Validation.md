# C2 Brukerinputvalidering

## Kontrollmål

Robust validering av brukerinput er en første linjens forsvar mot noen av de mest skadelige angrepene på AI-systemer. Angrep via promptinjeksjon kan overstyre systeminstruksjoner, lekke sensitiv data eller styre modellen mot uønsket oppførsel. Med mindre dedikerte filtre og annen validering er på plass, viser forskning at jailbreaks som utnytter kontekstvinduer vil fortsette å være effektive.

---

## C2.1 Forsvar mot prompt-injeksjon

Prompt-injeksjon er en av de største risikoene for AI-systemer. Forsvar mot denne taktikken benytter en kombinasjon av mønstergjenkjenningsfiltre, dataklassifikatorer og håndhevelse av instruksjonshierarki.

|   #   | Beskrivelse                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Nivå | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.1.1 | Sørg for at all ekstern eller avledet input som kan styre atferd, inkludert brukerpåminnelser, RAG-resultater, plugin- eller MCP-utdata, meldinger mellom agenter, API- eller webhook-svar, konfigurasjons- eller policyfiler, minneavlesninger og minneskrivinger, behandles som utrygge, gjøres inaktive ved sitat eller merking og fjerning av aktivt innhold, og blir kontrollert av et vedlikeholdt regelverk eller tjeneste for påvisning av promptinjeksjon før sammenkobling i prompts eller utførelse av handlinger. |  1   |  D/V  |
| 2.1.2 | Bekreft at systemet håndhever en instruksjonshierarki der system- og utviklermeldinger overstyrer brukerinstruksjoner og andre ikke-pålitelige input, selv etter behandling av brukerinstruksjoner.                                                                                                                                                                                                                                                                                                                           |  1   |  D/V  |
| 2.1.3 | Bekreft at forespørsler som stammer fra tredjepartsinnhold (nettsider, PDF-er, e-poster) blir renset isolert (for eksempel ved å fjerne instruksjonslignende direktiver og nøytralisere HTML-, Markdown- og skriptinnhold) før de settes sammen i hovedforespørselen.                                                                                                                                                                                                                                                         |  2   |   D   |

---

## C2.2 Motstand mot motstridende eksempler

Naturlige språkbehandlingsmodeller (NLP) er fortsatt sårbare for subtile forstyrrelser på tegn- eller ordnivå som mennesker ofte overser, men som modellene har en tendens til å feiltolke.

|   #   | Beskrivelse                                                                                                                                                                                                                                                                                                                      | Nivå | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.2.1 | Verifiser at grunnleggende inndatanormaliseringssteg (Unicode NFC, homoglyph-mapping, trimming av mellomrom, fjerning av kontroll- og usynlige Unicode-tegn) kjøres før tokenisering eller embedding og før tolking til verktøy- eller MCP-argumenter.                                                                           |  1   |   D   |
| 2.2.2 | Bekreft at statistisk anomalidetectering markerer input med uvanlig høy redigeringsavstand til språknormer eller unormale innebyggingsavstander, og at markerte input blir sperret før de settes sammen i prompts eller før handlinger utføres.                                                                                  |  2   |  D/V  |
| 2.2.3 | Bekreft at inferensrøret støtter modeller med motstandsdyktighet mot angrep basert på adversarial-trening eller forsvarslag (f.eks. randomisering, defensiv destillasjon, justeringssjekker) for høyrisiko-endepunkter.                                                                                                          |  2   |   D   |
| 2.2.4 | Bekreft at mistenkte fiendtlige innganger blir satt i karantene og loggført med full belastning og sporingsmetadata (kilde, verktøy eller MCP-server, agent-ID, økt).                                                                                                                                                            |  2   |   V   |
| 2.2.5 | Bekreft at innslusing av koding og representasjon i både innganger og utganger (for eksempel usynlige Unicode/kontrolltegn, homoglyph-byttinger eller tekst med blandet retning) blir oppdaget og avverget. Godkjente tiltak inkluderer kanonisering, streng skjema-validering, policybasert avvisning eller eksplisitt merking. |  2   |  D/V  |

---

## C2.3 Tegnsnitt for prompt

Begrensning av tegnsettet i brukerinnspill til kun å tillate tegn som er nødvendige for forretningskrav, kan bidra til å forhindre ulike typer angrep.

|   #   | Beskrivelse                                                                                                                                                                | Nivå | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.3.1 | Bekreft at systemet implementerer en begrensning på tegnsettet for brukerinnspill, som kun tillater tegn som eksplisitt er nødvendige for forretningsformål.               |  1   |   D   |
| 2.3.2 | Bekreft at en tillatt-liste tilnærming brukes for å definere det tillatte tegnsettet.                                                                                      |  1   |   D   |
| 2.3.3 | Bekreft at inndata som inneholder tegn utenfor den tillatte settet blir avvist og logget med sporingsmetadatainformasjon (kilde, verktøy eller MCP-server, agent-ID, økt). |  1   |  D/V  |

---

## C2.4 Skjema-, type- og lengdevalidering

AI-angrep som involverer feilformede eller overdimensjonerte inndata kan forårsake parsingsfeil, at forespørsler lekker over felt, og ressursutmattelse. Streng skjemahåndheving er også en forutsetning ved utføring av deterministiske verktøysanrop.

|   #   | Beskrivelse                                                                                                                                                                                                                                                                            | Nivå | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.4.1 | Bekreft at hver API, verktøy eller MCP-endepunkt definerer et eksplisitt inndataskjema (JSON Schema, Protobuf eller multimodal ekvivalent), avviser ekstra eller ukjente felter og implisitt typekoherens, og validerer input på serversiden før promptsetning eller verktøyutførelse. |  1   |   D   |
| 2.4.2 | Bekreft at inndata som overskrider maksimale token- eller bytegrenser blir avvist med en sikker feilmelding og aldri tause avkortet.                                                                                                                                                   |  1   |  D/V  |
| 2.4.3 | Bekreft at typetester (f.eks. numeriske områder, enum-verdier, MIME-typer for bilder/lyd) håndheves på serversiden, inkludert for verktøy- eller MCP-argumenter.                                                                                                                       |  2   |  D/V  |
| 2.4.4 | Bekreft at semantiske validatorer, som forstår NLP-inndata, kjører i konstant tid og unngår eksterne nettverkskall for å forhindre algoritmisk DoS.                                                                                                                                    |  2   |   D   |
| 2.4.5 | Bekreft at valideringsfeil logges med redigerte nyttelastutdrag og entydige feilkoder, og inkluderer spormetadata (kilde, verktøy eller MCP-server, agent-ID, økt) for å støtte sikkerhetstriage.                                                                                      |  3   |   V   |

---

## C2.5 Innhold og policy-sjekk

Utviklere bør kunne oppdage syntaktisk gyldige spørringer som etterspør forbudt innhold (slik som ulovlige instruksjoner, hatprat og/eller opphavsrettsbeskyttet tekst) og deretter forhindre at disse spres videre.

|   #   | Beskrivelse                                                                                                                                                                                                                                                                   | Nivå | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.5.1 | Verifiser at en innholdsklassifiserer (zero shot eller finjustert) vurderer hver inngang og utgang for vold, selvskading, hat, seksuelt innhold og ulovlige forespørsler, med konfigurerbare terskler.                                                                        |  1   |   D   |
| 2.5.2 | Bekreft at input som bryter med retningslinjer blir avvist slik at de ikke videresendes til etterfølgende LLM- eller verktøy-/MCP-kall.                                                                                                                                       |  1   |  D/V  |
| 2.5.3 | Bekreft at screening respekterer brukerspesifikke retningslinjer (alder, regionale juridiske begrensninger) gjennom attributtbaserte regler som løses ved forespørselstidspunktet, inkludert agent-rolleattributter.                                                          |  2   |   D   |
| 2.5.4 | Bekreft at screeningslogger inkluderer klassifiseringsnøyaktighetspoeng og policykategorietagger med anvendt fase (før-prompt eller etter-svar) og sporingsmetadata (kilde, verktøy eller MCP-server, agent-ID, sesjon) for SOC-korrelasjon og fremtidig red-team-avspilling. |  3   |   V   |

---

## C2.6 Inngangshastighetsbegrensning og misbruksforebygging

Utviklere bør forhindre misbruk, ressursutmattelse og automatiserte angrep mot AI-systemer ved å begrense inntaksrater og oppdage unormale bruks- mønstre.

|   #   | Beskrivelse                                                                                                                                                                                                                     | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.6.1 | Bekreft at grenseverdier for hastighet per bruker, per IP, per API-nøkkel, per agent og per økt/oppgave håndheves for alle inngangs- og verktøy-/MCP-endepunkter.                                                               |  1   |  D/V  |
| 2.6.2 | Bekreft at burst- og vedvarende hastighetsgrenser er justert for å forhindre DoS- og brute force-angrep, og at per-oppgavebudsjetter (for eksempel tokens, verktøy/MCP-kall og kostnad) håndheves for agentplanleggingssløyfer. |  2   |  D/V  |
| 2.6.3 | Bekreft at unormale bruksmønstre (f.eks. raskt etterfølgende forespørsler, input-flom, gjentatte mislykkede verktøy-/MCP-kall eller rekursive agentløkker) utløser automatiske blokkeringer eller eskaleringer.                 |  2   |  D/V  |
| 2.6.4 | Bekreft at logger for misbruksforebygging blir beholdt og gjennomgått for å identifisere nye angrepsmønstre, med sporingsmetadata (kilde, verktøy eller MCP-server, agent-ID, økt).                                             |  3   |   V   |

---

## C2.7 Multi-Modale inndata-validering

AI-systemer bør inkludere robust validering for ikke-tekstlige innganger (bilder, lyd, filer) for å forhindre injeksjon, unnvikelse eller ressursmisbruk.

|   #   | Beskrivelse                                                                                                                                                                                                                                                                                                                               | Nivå | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.7.1 | Sørg for at alle ikke-tekstlige inndata (bilder, lyd, filer) blir validert for type, størrelse og format før behandling, og at all utvunnet tekst (bilde-til-tekst eller tale-til-tekst) samt eventuelle skjulte eller innebygde instruksjoner (metadata, lag, alternativ tekst, kommentarer) behandles som utrygge i henhold til 2.1.1.  |  1   |   D   |
| 2.7.2 | Bekreft at filer blir skannet for skadelig programvare og steganografiske last før inntak, og at aktivt innhold (som skript eller makroer) fjernes eller at filen isoleres.                                                                                                                                                               |  2   |  D/V  |
| 2.7.3 | Bekreft at bilde-/lydinndata kontrolleres for fiendtlige forstyrrelser eller kjente angrepsmønstre, og at deteksjoner utløser sperring (blokkerer eller reduserer funksjonalitet) før modellen tas i bruk.                                                                                                                                |  2   |  D/V  |
| 2.7.4 | Bekreft at valideringsfeil for multimodale inndata loggføres og utløser varsler for undersøkelse, med sporingsmetadata (kilde, verktøy eller MCP-server, agent-ID, økt).                                                                                                                                                                  |  3   |   V   |
| 2.7.5 | Bekreft at kryss-modal angrepsdeteksjon identifiserer koordinerte angrep som spenner over flere inngangstyper (f.eks. steganografiske payloads i bilder kombinert med promptinjeksjon i tekst) med korrelasjonsregler og varselsgenerering, og at bekreftede deteksjoner blir blokkert eller krever HITL (human-in-the-loop) godkjenning. |  2   |  D/V  |
| 2.7.6 | Bekreft at multimodale valideringsfeil utløser detaljert logging som inkluderer alle inndata-modaliteter, valideringsresultater og trusselpoeng, samt spormetadatat (kilde, verktøy eller MCP-server, agent-ID, økt).                                                                                                                     |  3   |  D/V  |
---

## C2.8 Sanntids adaptiv trusseldeteksjon

Utviklere bør bruke avanserte trusseldeteksjonssystemer for AI som tilpasser seg nye angrepsmønstre og gir sanntidsbeskyttelse med kompilert mønstergjenkjenning.

|   #   | Beskrivelse                                                                                                                                                                                                                                                          | Nivå | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.8.1 | Verifiser at mønstersøking (f.eks. kompilert regex) kjører på alle inndata og utdata (inkludert verktøy-/MCP-flater) med minimal forsinkelsespåvirkning.                                                                                                             |  1   |  D/V  |
| 2.8.3 | Bekreft at adaptive deteksjonsmodeller justerer sensitiviteten basert på nylig angrepsaktivitet og oppdateres med nye mønstre i sanntid, og utløser risikotilpassede responser (for eksempel deaktiverer verktøy, reduserer kontekst eller krever HITL-godkjenning). |  2   |  D/V  |
| 2.8.4 | Bekreft at deteksjonsnøyaktigheten forbedres gjennom kontekstuell analyse av brukerhistorikk, kilde og sesjonsatferd, inkludert sporingsmetadata (kilde, verktøy eller MCP-server, agent-ID, sesjon).                                                                |  3   |  D/V  |
| 2.8.5 | Bekreft at ytelsesmetrikker for deteksjon (deteksjonsrate, feilpositiv rate, behandlingslatens) overvåkes og optimaliseres kontinuerlig, inkludert tid-til-blokkering og fase (før-prompt/etter-respons).                                                            |  3   |  D/V  |

## Referanser

* [OWASP LLM01:2025 Prompt Injection](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)
* [LLM Prompt Injection Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/LLM_Prompt_Injection_Prevention_Cheat_Sheet.html)
* [MITRE ATLAS : Adversarial Input Detection](https://atlas.mitre.org/mitigations/AML.M00150)
* [Mitigate jailbreaks and prompt injections](https://docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/mitigate-jailbreaks)

