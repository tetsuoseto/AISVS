# 9 Autonom orkestrering og agentbasert handlingssikkerhet

## Kontrollmål

Sørg for at autonome eller multi-agent AI-systemer kun kan utføre handlinger som er eksplisitt tiltenkt, autentisert, reviderbare og innenfor avgrensede kostnads- og risikogrenseverdier. Dette beskytter mot trusler som kompromittering av autonome systemer, feilbruk av verktøy, agent-loop-detektering, kapring av kommunikasjon, identitetsspoofing, svermmanipulering og intensjonsmanipulering.

---

## 9.1 Agentoppgaveplanlegging og rekursjonsbudsjetter

Begrens rekursive planer og påtving menneskelige kontrollpunkter for privilegerte handlinger.

|   #   | Beskrivelse                                                                                                                                                                                 | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.1.1 | Bekreft at maksimal rekursjonsdybde, bredde, veggur-tid, tokens og monetær kostnad per agentkjøring er sentralt konfigurert og versjonskontrollert.                                         |  1   |  D/V  |
| 9.1.2 | Sørg for at privilegerte eller irreversible handlinger (f.eks. kodeinnsendinger, finansielle overføringer) krever eksplisitt menneskelig godkjenning via en reviderbar kanal før utførelse. |  1   |  D/V  |
| 9.1.3 | Bekreft at sanntids ressursmonitorer utløser kretsbryteravbrudd når noen budsjettgrense overskrides, og stopper videre oppgaveutvidelse.                                                    |  2   |   D   |
| 9.1.4 | Bekreft at kretsbryterhendelser blir logget med agent-ID, utløsende betingelse og fanget planstatus for rettsmedisinsk gjennomgang.                                                         |  2   |  D/V  |
| 9.1.5 | Bekreft at sikkerhetstestene dekker scenarioer for budsjettuttømmelse og løpsk plan, og bekrefter sikker stopp uten datatap.                                                                |  3   |   V   |
| 9.1.6 | Bekreft at budsjettpolitikkene uttrykkes som politikk-som-kode og håndheves i CI/CD for å blokkere konfigurasjonsavvik.                                                                     |  3   |   D   |

---

## 9.2 Sandkasse for verktøyplugins

Isoler verktøysinteraksjoner for å forhindre uautorisert systemtilgang eller kodeutførelse.

|   #   | Beskrivelse                                                                                                                                                                     | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.2.1 | Bekreft at hvert verktøy/plugin kjører inne i et OS-, container- eller WASM-nivå sandkassemiljø med minst mulig privilegium for filsystem-, nettverks- og systemkallpolitikker. |  1   |  D/V  |
| 9.2.2 | Bekreft at ressurskvoter for sandbox (CPU, minne, disk, nettverksutgang) og tidsavbrudd for utførelse håndheves og loggføres.                                                   |  1   |  D/V  |
| 9.2.3 | Bekreft at verktøy-binærer eller beskrivelser er digitalt signert; signaturer valideres før lasting.                                                                            |  2   |  D/V  |
| 9.2.4 | Bekreft at sandkasse-telemetri strømmer til en SIEM; avvik (for eksempel forsøk på utgående tilkoblinger) utløser varsler.                                                      |  2   |   V   |
| 9.2.5 | Sørg for at høy-risiko plugins gjennomgår sikkerhetsgjennomgang og penetrasjonstesting før produksjonsutrulling.                                                                |  3   |   V   |
| 9.2.6 | Bekreft at forsøk på å unnslippe sandkassen automatisk blokkeres, og at det mistenkelige pluginet settes i karantene i påvente av undersøkelse.                                 |  3   |  D/V  |

---

## 9.3 Autonom Sløyfe og Kostnadsbegrensning

Oppdage og stoppe ukontrollert agent-til-agent rekursjon og kostnadseksplosjoner.

|   #   | Beskrivelse                                                                                                                     | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.3.1 | Bekreft at anrop mellom agenter inkluderer en hop-grense eller TTL som kjøretiden reduserer og håndhever.                       |  1   |  D/V  |
| 9.3.2 | Bekreft at agenter opprettholder en unik invokasjonsgraf-ID for å oppdage selv-invokasjon eller sykliske mønstre.               |  2   |   D   |
| 9.3.3 | Bekreft at akkumulerte beregningsenheter og forbruks teller blir sporet per forespørselskjed; brudd på grensen avbryter kjeden. |  2   |  D/V  |
| 9.3.4 | Verifiser at formell analyse eller modellkontroll påviser fravær av ubundet rekursjon i agentprotokoller.                       |  3   |   V   |
| 9.3.5 | Bekreft at løkke-avbrudds-hendelser genererer varsler og gir kontinuerlige forbedringsmålinger.                                 |  3   |   D   |

---

## 9.4 Beskyttelse mot misbruk på protokollnivå

Sikre kommunikasjonskanaler mellom agenter og eksterne systemer for å forhindre kapring eller manipulering.

|   #   | Beskrivelse                                                                                                                               | Nivå | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.4.1 | Bekreft at alle agent-til-verktøy og agent-til-agent meldinger er autentisert (f.eks. gjensidig TLS eller JWT) og ende-til-ende kryptert. |  1   |  D/V  |
| 9.4.2 | Verifiser at skjemaer blir strengt validert; ukjente felt eller feilformatert meldinger blir avvist.                                      |  1   |   D   |
| 9.4.3 | Verifiser at integritetskontroller (MAC-er eller digitale signaturer) dekker hele meldingsinnholdet inkludert verktøyparametere.          |  2   |  D/V  |
| 9.4.4 | Bekreft at replay-beskyttelse (nonser eller tidsstempelvinduer) håndheves på protokollaget.                                               |  2   |   D   |
| 9.4.5 | Bekreft at protokollimplementeringer gjennomgår fuzzing og statisk analyse for injeksjons- eller deserialiseringsfeil.                    |  3   |   V   |

---

## 9.5 Agentidentitet og manipuleringsevidens

Sørg for at handlinger kan tilskrives og at endringer kan oppdages.

|   #   | Beskrivelse                                                                                                           | Nivå | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.5.1 | Verifiser at hver agentinstans har en unik kryptografisk identitet (nøkkelpar eller maskinvarebasert rot-sertifikat). |  1   |  D/V  |
| 9.5.2 | Bekreft at alle agenthandlinger er signert og tidsstemplet; logger inkluderer signaturen for å forhindre fornektelse. |  2   |  D/V  |
| 9.5.3 | Bekreft at manipulasjonsbeviste logger lagres i et medium som kun tillater tillegg eller skrives én gang.             |  2   |   V   |
| 9.5.4 | Bekreft at identitetsnøkler roteres i henhold til en definert tidsplan og ved indikasjoner på kompromittering.        |  3   |   D   |
| 9.5.5 | Bekreft at forsøk på forfalskning eller nøkkelkonflikt umiddelbart utløser karantene for den berørte agenten.         |  3   |  D/V  |

---

## 9.6 Fleragent-sverm risiko reduksjon

Reduser farer ved kollektiv atferd gjennom isolasjon og formell sikkerhetsmodellering.

|   #   | Beskrivelse                                                                                                                                 | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.6.1 | Bekreft at agenter som opererer i forskjellige sikkerhetsdomener kjører i isolerte kjøretids-sandkasser eller nettverkssegmenter.           |  1   |  D/V  |
| 9.6.2 | Bekreft at sværmadferder er modellert og formelt verifisert for livskraft og sikkerhet før distribusjon.                                    |  3   |   V   |
| 9.6.3 | Verifiser at kjøretidsovervåkere oppdager fremvoksende usikre mønstre (f.eks. oscilleringer, deadlocks) og iverksetter korrigerende tiltak. |  3   |   D   |

---

## 9.7 Bruker- og verktøyauntentisering / autorisering

Implementer robuste tilgangskontroller for hver agentutløst handling.

|   #   | Beskrivelse                                                                                                                        | Nivå | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.7.1 | Bekreft at agenter autentiserer som førsteklasses prinsipper til nedstrøms systemer, uten å gjenbruke sluttbrukerens legitimasjon. |  1   |  D/V  |
| 9.7.2 | Bekreft at finmasket autorisasjonspolitikk begrenser hvilke verktøy en agent kan påkalle, og hvilke parametere den kan gi.         |  2   |   D   |
| 9.7.3 | Verifiser at privilegietsjekker blir evaluert på nytt ved hvert kall (kontinuerlig autorisasjon), ikke bare ved starten av økten.  |  2   |   V   |
| 9.7.4 | Bekreft at delegert privilegium utløper automatisk og krever ny samtykke etter tidsavbrudd eller endring av omfang.                |  3   |   D   |

---

## 9.8 Agent-til-Agent Kommunikasjonssikkerhet

Krypter og integritetsbeskytt alle meldinger mellom agenter for å forhindre avlytting og manipulering.

|   #   | Beskrivelse                                                                                                                             | Nivå | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.8.1 | Bekreft at gjensidig autentisering og perfekt fremoverhemmelig kryptering (f.eks. TLS 1.3) er obligatorisk for agentkanaler.            |  1   |  D/V  |
| 9.8.2 | Bekreft at meldingsintegritet og opprinnelse valideres før behandling; feil utløser varsler og avviser meldingen.                       |  1   |   D   |
| 9.8.3 | Bekreft at kommunikasjonsmetadata (tidsstempler, sekvensnumre) blir logget for å støtte rettsmedisinsk rekonstruksjon.                  |  2   |  D/V  |
| 9.8.4 | Bekreft at formell verifikasjon eller modellkontroll bekrefter at protokolltilstandsautomater ikke kan bringes inn i usikre tilstander. |  3   |   V   |

---

## 9.9 Intensjonsverifisering og håndheving av begrensninger

Bekreft at agentens handlinger samsvarer med brukerens oppgitte intensjon og systembegrensninger.

|   #   | Beskrivelse                                                                                                                                                         | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.9.1 | Bekreft at pre-eksekveringsbegrensningsløsere sjekker foreslåtte handlinger mot hardkodede sikkerhets- og policyregler.                                             |  1   |   D   |
| 9.9.2 | Verifiser at handlinger med stor påvirkning (økonomiske, destruktive, personvernsensitive) krever eksplisitt bekreftelse av intensjon fra den initierende brukeren. |  2   |  D/V  |
| 9.9.3 | Bekreft at etterbetingelseskontroller validerer at fullførte handlinger oppnådde tiltenkte effekter uten bivirkninger; avvik utløser tilbakestilling.               |  2   |   V   |
| 9.9.4 | Verifiser at formelle metoder (for eksempel modellkontroll, teorembevis) eller egenskapsbaserte tester viser at agentplaner oppfyller alle erklærte begrensninger.  |  3   |   V   |
| 9.9.5 | Bekreft at hendelser med intensjonsavvik eller brudd på begrensninger gir kontinuerlige forbedringssykluser og deling av trusselintelligens.                        |  3   |   D   |

---

## 9.10 Agentresonneringsstrategi-sikkerhet

Sikker seleksjon og utførelse av forskjellige resonnementstrategier inkludert ReAct, Chain-of-Thought og Tree-of-Thoughts metoder.

|   #    | Beskrivelse                                                                                                                                                                                                                  | Nivå | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.10.1 | Bekreft at valg av resonneringsstrategi bruker deterministiske kriterier (inngangskompleksitet, oppgavetyp, sikkerhetskontekst) og at identiske innganger gir identiske strategiutvelgelser innen samme sikkerhetskontekst.  |  1   |  D/V  |
| 9.10.2 | Bekreft at hver resonnementstrategi (ReAct, Chain-of-Thought, Tree-of-Thoughts) har dedikert inndata validering, utdata sanitering og tidsbegrensninger for utførelse som er spesifikke for dens kognitive tilnærming.       |  1   |  D/V  |
| 9.10.3 | Bekreft at overganger i resonnementstrategier logges med fullstendig kontekst, inkludert inndatakjennetegn, verdier for utvalgs kriterier og metadata for utførelse, for å muliggjøre rekonstruksjon av revisjonsspor.       |  2   |  D/V  |
| 9.10.4 | Bekreft at Tree-of-Thoughts- resonnement inkluderer grenbeskjæringsmekanismer som avslutter utforskning når policybrudd, ressursbegrensninger eller sikkerhetsgrenser oppdages.                                              |  2   |  D/V  |
| 9.10.5 | Bekreft at ReAct (Reason-Act-Observe) sykluser inkluderer valideringskontroller i hver fase: verifisering av resonnementstrinn, godkjenning av handling, og rensing av observasjon før videreføring.                         |  2   |  D/V  |
| 9.10.6 | Verifiser at ytelsesmetrikker for resonnementstrategien (eksekveringstid, ressursbruk, outputkvalitet) overvåkes med automatiserte varsler når metrikker avviker utover konfigurerte terskler.                               |  3   |  D/V  |
| 9.10.7 | Bekreft at hybride resonnementstilnærminger som kombinerer flere strategier opprettholder inndata-validering og utgangsbegrensninger for alle underliggende strategier uten å omgå noen sikkerhetskontroller.                |  3   |  D/V  |
| 9.10.8 | Bekreft at sikkerhetstesting av resonneringsstrategier inkluderer fuzzing med feilaktige innganger, motstridende prompt designet for å tvinge strategiskifte, og grenseverdibetingelsestesting for hver kognitiv tilnærming. |  3   |  D/V  |

---

## 9.11 Agentens livssyklus-tilstandsadministrasjon og sikkerhet

Sikker agentinitialisering, tilstandsoverganger og avslutning med kryptografiske revisjonsspor og definerte gjenopprettingsprosedyrer.

|   #    | Beskrivelse                                                                                                                                                                                                                                                                      | Nivå | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.11.1 | Bekreft at agentinitialisering inkluderer etablering av kryptografisk identitet med maskinvarebaserte legitimasjoner og uforanderlige oppstartsauditlogger som inneholder agent-ID, tidsstempel, konfigurasjonshash og initialiseringsparametere.                                |  1   |  D/V  |
| 9.11.2 | Bekreft at agenttilstandsoverganger er kryptografisk signert, tidsstemplet og loggført med komplett kontekst, inkludert utløsende hendelser, forrige tilstandshash, ny tilstandshash og utførte sikkerhetsvalideringer.                                                          |  2   |  D/V  |
| 9.11.3 | Bekreft at agentens avslutningsprosedyrer inkluderer sikker minnrensing ved bruk av kryptografisk sletting eller flerpassasje-overskriving, tilbakekalling av legitimasjon med melding til sertifikatmyndigheten, og generering av manipulasjonsbeviste avslutningssertifikater. |  2   |  D/V  |
| 9.11.4 | Bekreft at agentgjenopprettingsmekanismer validerer tilstandsintegritet ved bruk av kryptografiske kontrollsummer (minimum SHA-256) og ruller tilbake til kjente gode tilstander når korrupsjon oppdages, med automatiske varsler og krav om manuell godkjenning.                |  3   |  D/V  |
| 9.11.5 | Bekreft at agentens vedvarende mekanismer krypterer sensitiv tilstandsdata med per-agent AES-256-nøkler og implementerer sikker nøkkelrotasjon på konfigurerbare tidsplaner (maksimalt 90 dager) med distribusjon uten nedetid.                                                  |  3   |  D/V  |

---

## 9.12 Verktøyintegrasjon Sikkerhetsrammeverk

Sikkerhetskontroller for dynamisk verktøyinnlasting, kjøring og resultatvalidering med definerte risikovurderings- og godkjenningsprosesser.

|   #    | Beskrivelse                                                                                                                                                                                                                                             | Nivå | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.12.1 | Bekreft at verktøybeskrivelser inkluderer sikkerhetsmetadata som spesifiserer nødvendige privilegier (lese/skrive/utføre), risikonivåer (lavt/middels/høyt), ressursgrenser (CPU, minne, nettverk) og valideringskrav dokumentert i verktøymanifestene. |  1   |  D/V  |
| 9.12.2 | Verifiser at verktøyutførelsesresultater valideres mot forventede skjemaer (JSON-skjema, XML-skjema) og sikkerhetspolicyer (output-rensing, dataklassifisering) før integrering med tidsavbruddsgrenser og feilhåndteringsprosedyrer.                   |  1   |  D/V  |
| 9.12.3 | Verifiser at verktøyinteraksjonslogger inkluderer detaljert sikkerhetskontekst, inkludert privilegiebruk, datatilgangsmønstre, kjøretid, ressursforbruk og returkoder med strukturert logging for SIEM-integrasjon.                                     |  2   |  D/V  |
| 9.12.4 | Sørg for at mekanismer for dynamisk verktøylasting validerer digitale signaturer ved bruk av PKI-infrastruktur og implementerer sikre lastingsprotokoller med sandkasseisolasjon og tillatelsesverifisering før utførelse.                              |  2   |  D/V  |
| 9.12.5 | Bekreft at verktøysikkerhetsvurderinger automatisk utløses for nye versjoner med obligatoriske godkjenningsporter, inkludert statisk analyse, dynamisk testing og sikkerhetsteamets vurdering med dokumenterte godkjenningskriterier og SLA-krav.       |  3   |  D/V  |

---

## C9.13 Modellkontekstprotokoll (MCP) sikkerhet

Sikre trygg oppdagelse, autentisering, autorisasjon, transport og bruk av MCP-baserte verktøy- og ressursintegrasjoner for å forhindre kontekstforvirring, uautorisert verktøypåkalelse eller eksponering av data på tvers av leietakere.

### Komponentintegritet og leverandørkjedehygiene

|   #    | Beskrivelse                                                                                                                                                                                                                                            | Nivå | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 9.13.1 | Bekreft at MCP-server-, klient- og verktøyimplementeringer blir manuelt gjennomgått eller automatisk analysert for å identifisere usikker funksjonseksponering, usikre standardinnstillinger, manglende autentisering eller manglende inputvalidering. |  1   |  D/V  |
| 9.13.2 | Bekreft at eksterne eller åpen-kildekode MCP-servere eller pakker gjennomgår automatisert sårbarhets- og forsyningskjede-skanning (f.eks. SCA) før integrering, og at komponenter med kjente kritiske sårbarheter ikke brukes.                         |  1   |  D/V  |
| 9.13.3 | Verifiser at MCP-server- og klientkomponenter kun er hentet fra pålitelige kilder og verifisert ved hjelp av signaturer, sjekksummer eller sikker pakkemetadata, og avvis manipulerte eller usignerte versjoner.                                       |  1   |  D/V  |

### Autentisering og autorisering

|   #    | Beskrivelse                                                                                                                                                                                                                                    | Nivå | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.13.4 | Bekreft at MCP-klienter og -servere gjensidig autentiserer ved bruk av sterke, ikke-brukerbaserte legitimasjoner (for eksempel mTLS, signerte token, eller plattformutstedte identiteter), og at uautentiserte MCP-endepunkter blir avvist.    |  2   |  D/V  |
| 9.13.5 | Bekreft at MCP-servere er registrert gjennom en kontrollert teknisk onboarding-mekanisme som krever eksplisitte definisjoner av eier, miljø og ressurs; uregistrerte eller ikke oppdagbare servere må ikke kunne kalles i produksjon.          |  2   |  D/V  |
| 9.13.6 | Bekreft at hvert MCP-verktøy eller -ressurs definerer eksplisitte autorisasjonsområder (f.eks. kun lesetilgang, begrensede forespørsler, nivåer av sideeffekter), og at agenter ikke kan påkalle MCP-funksjoner utenfor deres tildelte område. |  2   |  D/V  |

### Sikker transport og nettverksgrensebeskyttelse

|    #    | Beskrivelse                                                                                                                                                                                                                                                                            | Nivå | Rolle |
| :-----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.13.7  | Verifiser at autentisert, kryptert streambar-HTTP brukes som hovedtransport for MCP i produksjonsmiljøer; alternative transportmetoder (stdio, SSE) er begrenset til lokale eller strengt kontrollerte miljøer med eksplisitt begrunnelse.                                             |  2   |  D/V  |
| 9.13.8  | Bekreft at streamable-HTTP MCP-transporter bruker autentiserte, krypterte kanaler (TLS 1.3 eller nyere) med sertifikatvalidering og fremoverrettet hemmelighold for å sikre konfidensialitet og integritet til strømmede MCP-meldinger.                                                |  2   |  D/V  |
| 9.13.9  | Bekreft at SSE-baserte MCP-transporter kun brukes innenfor private, autentiserte interne kanaler, og håndhev TLS, autentisering, skjema-validering, begrensninger på nyttelaststørrelse og hastighetsbegrensning; SSE-endepunkter må ikke være eksponert mot det offentlige internett. |  2   |  D/V  |
| 9.13.10 | Bekreft at MCP-servere validerer `Origin` og`Host` overskrifter på alle HTTP-baserte overføringer (inkludert SSE og strømbar HTTP) for å forhindre DNS-rebindingangrep, og avvis forespørsler fra ikke-pålitelige, feiltilpassede eller manglende opprinnelser.                        |  2   |  D/V  |

### Skjema, melding og inndatavalidering

|    #    | Beskrivelse                                                                                                                                                                                                                                                                   | Nivå | Rolle |
| :-----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.13.11 | Bekreft at MCP-verktøy- og ressurs-skjemaer (f.eks. JSON-skjemaer eller kapabilitetsbeskrivelser) blir validert for ekthet og integritet ved bruk av signaturer, kontrollsummer eller serverattestasjon for å forhindre skjema-manipulering eller ondsinnet parameterendring. |  2   |  D/V  |
| 9.13.12 | Bekreft at alle MCP-transporter håndhever meldingsinnrammingsintegritet, streng skjema-validering, maks tillatte nyttelaststørrelser, og avvisning av feilaktige, trunkerte eller sammenflettede rammer for å forhindre desynkronisering eller injeksjonsangrep.              |  2   |  D/V  |
| 9.13.13 | Bekreft at MCP-servere utfører streng inputvalidering for alle funksjonsanrop, inkludert typetesting, grensekontroll, håndheving av enumerasjoner, og avvisning av ukjente eller for store parametere.                                                                        |  2   |  D/V  |

### Utgående tilgang og agentsikkerhet ved kjøring

|    #    | Beskrivelse                                                                                                                                                                                                                                                              | Nivå | Rolle |
| :-----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 9.13.14 | Bekreft at MCP-servere kun kan initiere utgående forespørsler til godkjente interne eller eksterne destinasjoner i henhold til policyer for minste privilegium for egress, og at de ikke kan få tilgang til vilkårlige nettverksmål eller interne skymetadata-tjenester. |  2   |  D/V  |
| 9.13.15 | Bekreft at utgående MCP-handlinger implementerer utførelsesgrenser (tidsavbrudd, rekursjonsgrenser, samtidighetskapper, sikringsbrytere) for å forhindre ubegrenset agentdrevet verktøyutløsning eller kjedede sideeffekter.                                             |  2   |  D/V  |
| 9.13.16 | Verifiser at MCP-forespørsel- og responsmetadata (server-ID, ressursnavn, verktøynavn, øktidentifikator, leietaker, miljø) logges med integritetsbeskyttelse og korreleres med agentaktivitet for rettsmedisinsk analyse.                                                |  2   |  D/V  |

### Transportbegrensninger og kontroll av høy-risiko grenser

|    #    | Beskrivelse                                                                                                                                                                                                                                               | Nivå | Rolle |
| :-----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.13.17 | Bekreft at stdio-baserte MCP-transporter er begrenset til samlokaliserte, enkeltprosessorutviklingsscenarier, isolert fra skalletkjøring, terminalinjeksjon og prosessopprettingsmuligheter; stdio må aldri krysse nettverks- eller flerleietakergrenser. |  3   |  D/V  |
| 9.13.18 | Verifiser at MCP-servere kun eksponerer funksjoner og ressurser som er på godkjent liste, og forbyr dynamisk distribusjon, reflektiv invokasjon eller utførelse av funksjonsnavn påvirket av bruker- eller modelltilført input.                           |  3   |  D/V  |
| 9.13.19 | Verifiser at leietakergrenser, miljøgrenser (dev/test/prod) og datadomenegrenser håndheves på MCP-laget, for å forhindre kryss-leietaker eller kryss-miljø oppdagelse av servere eller ressurser.                                                         |  3   |  D/V  |

---

### Referanser

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
* [Model Context Protocol Specification](https://modelcontextprotocol.io)
* [Model Context Protocol Tools & Resources Specification](https://modelcontextprotocol.io/specification/2025-06-18/basic)
* [Model Context Protocol Transport Documentation](https://modelcontextprotocol.io/specification/2025-06-18/basic/transports)
* [OWASP GenAI Security Project — “A Practical Guide for Securely Using Third-Party MCP Servers 1.0”](https://genai.owasp.org/resource/cheatsheet-a-practical-guide-for-securely-using-third-party-mcp-servers-1-0/)
* [Cloud Security Alliance – Model Context Protocol Security Working Group](https://modelcontextprotocol-security.io)
* [CSA MCP Security: Top 10 Risks](https://modelcontextprotocol-security.io/top10/)
* [CSA MCP Security: TTPs & Hardening Guidance](https://modelcontextprotocol-security.io/ttps/)

