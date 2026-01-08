# Vedlegg C: AI-sikkerhetsstyring og dokumentasjon (omorganisert)

## Målsetting

Dette vedlegget gir grunnleggende krav for å etablere organisatoriske strukturer, retningslinjer, dokumentasjon og prosesser for å styre AI-sikkerhet gjennom hele systemets livssyklus.

---

## AC.1 Adopsjon av rammeverk for risikostyring av AI

|   #    | Beskrivelse                                                                                                  | Nivå | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| AC.1.1 | Bekreft at en AI-spesifikk risikovurderingsmetodikk er dokumentert og implementert.                          |  1   |  D/V  |
| AC.1.2 | Sørg for at risikovurderinger gjennomføres på viktige punkter i AI-livssyklusen og før betydelige endringer. |  2   |   D   |
| AC.1.3 | Bekreft at risikostyringsrammeverket samsvarer med etablerte standarder (f.eks. NIST AI RMF).                |  3   |  D/V  |

---

## AC.2 AI-sikkerhetspolicy og prosedyrer

|   #    | Beskrivelse                                                                                                            | Nivå | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.2.1 | Bekreft at dokumenterte AI-sikkerhetspolicyer eksisterer.                                                              |  1   |  D/V  |
| AC.2.2 | Bekreft at retningslinjer blir gjennomgått og oppdatert minst årlig og etter betydelige endringer i trussellandskapet. |  2   |   D   |
| AC.2.3 | Sørg for at retningslinjene dekker alle AISVS-kategorier og gjeldende regulatoriske krav.                              |  3   |  D/V  |

---

## AC.3 Roller og ansvar for AI-sikkerhet

|   #    | Beskrivelse                                                                            | Nivå | Rolle |
| :----: | -------------------------------------------------------------------------------------- | :--: | :---: |
| AC.3.1 | Bekreft at AI-sikkerhetsroller og -ansvar er dokumentert.                              |  1   |  D/V  |
| AC.3.2 | Sikre at ansvarlige personer har relevant sikkerhetsekspertise.                        |  2   |   D   |
| AC.3.3 | Bekreft at en AI-etikkkomité eller styringsråd er opprettet for høyrisiko AI-systemer. |  3   |  D/V  |

---

## AC.4 Håndhevelse av etiske retningslinjer for AI

|   #    | Beskrivelse                                                                        | Nivå | Rolle |
| :----: | ---------------------------------------------------------------------------------- | :--: | :---: |
| AC.4.1 | Bekreft at etiske retningslinjer for utvikling og implementering av AI eksisterer. |  1   |  D/V  |
| AC.4.2 | Bekreft at mekanismer er på plass for å oppdage og rapportere etiske brudd.        |  2   |   D   |
| AC.4.3 | Sørg for at regelmessige etiske vurderinger av implementerte AI-systemer utføres.  |  3   |  D/V  |

---

## AC.5 Overvåking av samsvar med AI-regelverk

|   #    | Beskrivelse                                                                                       | Nivå | Rolle |
| :----: | ------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.5.1 | Bekreft at det finnes prosesser for å identifisere gjeldende AI-regelverk.                        |  1   |  D/V  |
| AC.5.2 | Verifiser at etterlevelse av alle regulatoriske krav blir vurdert.                                |  2   |   D   |
| AC.5.3 | Bekreft at regulatoriske endringer utløser rettidige vurderinger og oppdateringer av AI-systemer. |  3   |  D/V  |

---

## AC.6 Styring av treningsdata, dokumentasjon og prosess

### AC.6.1 Datainnhenting og aktsomhetsvurdering

|    #     | Beskrivelse                                                                                                                                                                                                                                                                             | Nivå | Rolle |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.6.1.1 | Bekreft at kun datasett som er vurdert for kvalitet, representativitet, etisk innhenting og lisenssamsvar, er tillatt, for å redusere risiko for forgiftning, innebygd skjevhet og brudd på immaterielle rettigheter.                                                                   |  1   |  D/V  |
| AC.6.1.2 | Sikre at tredjepartsdataleverandører, inkludert leverandører av forhåndstrente modeller og eksterne datasett, gjennomgår sikkerhets-, personvern-, etisk anskaffelse- og datakvalitetsvurderinger før deres data eller modeller integreres.                                             |  2   |  D/V  |
| AC.6.1.3 | Bekreft at eksterne overføringer bruker TLS/autentisering og integritetskontroller.                                                                                                                                                                                                     |  1   |   D   |
| AC.6.1.4 | Bekreft at høy-risiko datakilder (f.eks. open-source datasett med ukjent opphav, uverifiserte leverandører) blir utsatt for økt gransking, slik som sandbox-analyse, omfattende kvalitets- og skjevhetssjekker, og målrettet forgiftningsdeteksjon, før bruk i sensitive applikasjoner. |  2   |  D/V  |
| AC.6.1.5 | Bekreft at forhåndstrente modeller hentet fra tredjepartsleverandører blir evaluert for innebygde skjevheter, potensielle bakdører, integriteten til arkitekturen deres, og opphavet til deres originale treningsdata før viderefinjustering eller distribusjon.                        |  3   |  D/V  |

### AC.6.2 Håndtering av skjevhet og rettferdighet

|    #     | Beskrivelse                                                                                                                                                                                                                                                                                                                                                    | Nivå | Rolle |
| :------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.6.2.1 | Bekreft at datasett blir analysert for representasjonsubalanse og potensielle skjevheter knyttet til juridisk beskyttede egenskaper (f.eks. rase, kjønn, alder) og andre etisk sensitive kjennetegn som er relevante for modellens anvendelsesområde (f.eks. sosioøkonomisk status, geografisk beliggenhet).                                                   |  1   |  D/V  |
| AC.6.2.2 | Bekreft at de identifiserte skjevhetene blir redusert gjennom dokumenterte strategier som ombalansering, målrettet dataforsterkning, algoritmiske justeringer (for eksempel teknikker for forhåndsbehandling, behandling og etterbehandling) eller re-vektlegging, og at virkningen av demping på både rettferdighet og samlet modellprestasjon blir evaluert. |  2   |  D/V  |
| AC.6.2.3 | Bekreft at etter-trening rettferdighetsmålinger blir evaluert og dokumentert.                                                                                                                                                                                                                                                                                  |  2   |  D/V  |
| AC.6.2.4 | Verifiser at en livssyklusstyringspolicy for skjevheter tilordner eiere og gjennomgangsfrekvens.                                                                                                                                                                                                                                                               |  3   |  D/V  |

### AC.6.3 Merking og annotasjonsstyring

|     #     | Beskrivelse                                                                                                                                                                                                                                       | Nivå | Rolle |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.6.3.1  | Verifiser at kvaliteten på merking/annotasjon sikres gjennom krysskontroller eller konsensus blant gjennomsynere.                                                                                                                                 |  2   |  D/V  |
| AC.6.3.2  | Verifiser at datakort opprettholdes for betydelige treningsdatasett, og inkluderer detaljer om egenskaper, motivasjoner, sammensetning, innsamlingsprosesser, forhåndsbehandling, lisenser, og anbefalte/ikke anbefalte bruksområder.             |  2   |  D/V  |
| AC.6.3.3  | Verifiser at datakort dokumenterer biasrisikoer, demografiske skjevheter og etiske hensyn som er relevante for datasettet.                                                                                                                        |  2   |  D/V  |
| AC.6.3.4  | Kontroller at datakort versjoneres sammen med datasett og oppdateres hver gang datasettet endres.                                                                                                                                                 |  2   |  D/V  |
| AC.6.3.5  | Bekreft at datakort blir gjennomgått og godkjent av både tekniske og ikke-tekniske interessenter (f.eks. samsvar, etikk, domeneeksperter).                                                                                                        |  2   |  D/V  |
| AC.6.3.6  | Bekreft at kvaliteten på merking/annotering sikres gjennom klare retningslinjer, krysskontroller av gjennomgangere, konsensusmekanismer (f.eks. overvåking av enighet mellom annotatorer) og definerte prosesser for å løse uoverensstemmelser.   |  2   |  D/V  |
| AC.6.3.7  | Bekreft at merkelapper som er kritiske for sikkerhet, trygghet eller rettferdighet (f.eks. identifisering av giftig innhold, kritiske medisinske funn) gjennomgår obligatorisk uavhengig dobbel vurdering eller tilsvarende grundig verifisering. |  3   |  D/V  |
| AC.6.3.8  | Sørg for at merkingsveiledninger og instruksjoner er omfattende, versjonskontrollerte og fagfellevurderte.                                                                                                                                        |  2   |  D/V  |
| AC.6.3.9  | Sørg for at datastrukturer for etiketter er klart definerte og versjonskontrollerte.                                                                                                                                                              |  2   |  D/V  |
| AC.6.3.10 | Bekreft at outsourcet eller crowdsourcet merkemarkeringsarbeidsflyter inkluderer tekniske/prosedyremessige sikringer for å sikre datakonfidensialitet, integritet, merkemarkeringskvalitet, og forhindre datalekkasjer.                           |  2   |  D/V  |
| AC.6.3.11 | Bekreft at alt personell som er involvert i dataannotasjon, har bakgrunnssjekk og opplæring i datasikkerhet og personvern.                                                                                                                        |  2   |  D/V  |
| AC.6.3.12 | Bekreft at alt annotasjonspersonell signerer konfidensialitets- og taushetserklæringer.                                                                                                                                                           |  2   |  D/V  |
| AC.6.3.13 | Bekreft at annotasjonsplattformer håndhever tilgangskontroller og overvåker for interne trusler.                                                                                                                                                  |  2   |  D/V  |

### AC.6.4 Datasett Kvalitetsporter og Karantene

|    #     | Beskrivelse                                                                                                                                                                                                                                                                      | Nivå | Rolle |
| :------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.6.4.1 | Bekreft at mislykkede datasett blir satt i karantene med revisjonsspor.                                                                                                                                                                                                          |  2   |  D/V  |
| AC.6.4.2 | Bekreft at kvalitetsporter blokkerer undermåls datasett med mindre unntak er godkjent.                                                                                                                                                                                           |  2   |  D/V  |
| AC.6.4.3 | Bekreft at manuelle stikkprøver utført av fageksperter dekker et statistisk signifikant utvalg (f.eks. ≥1 % eller 1 000 prøver, det som er størst, eller som bestemt gjennom risikovurdering) for å identifisere subtile kvalitetsproblemer som ikke oppdages av automatisering. |  2   |   V   |

### AC.6.5 Trussel-/Forgiftningsdeteksjon og drift

|    #     | Beskrivelse                                                                                       | Nivå | Rolle |
| :------: | ------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.6.5.1 | Bekreft at flaggede prøver utløser manuell gjennomgang før trening.                               |  2   |  D/V  |
| AC.6.5.2 | Bekreft at resultatene gir modellens sikkerhetsdossier og informerer pågående trusselintelligens. |  2   |   V   |
| AC.6.5.3 | Bekreft at deteksjonslogikken oppdateres med ny trusselinformasjon.                               |  3   |  D/V  |
| AC.6.5.4 | Bekreft at nettbaserte læringsrørledninger overvåker distribusjonsavvik.                          |  3   |  D/V  |

### AC.6.6 Sletting, samtykke, rettigheter, oppbevaring og etterlevelse

|     #     | Beskrivelse                                                                                                                                                                                                                                                            | Nivå | Rolle |
| :-------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.6.6.1  | Verifiser at arbeidsflyter for sletting av opplæringsdata fjerner både primære og avledede data og vurder modellpåvirkningen, samt at påvirkningen på berørte modeller blir vurdert og, om nødvendig, håndtert (for eksempel gjennom nytrening eller rekalibrering).   |  1   |  D/V  |
| AC.6.6.2  | Bekreft at det finnes mekanismer for å spore og respektere omfanget og statusen for brukersamtykke (og tilbaketrekkinger) for data brukt i trening, og at samtykke blir validert før data blir inkludert i nye treningsprosesser eller betydelige modelloppdateringer. |  2   |   D   |
| AC.6.6.3  | Sørg for at arbeidsflyter testes årlig og loggføres.                                                                                                                                                                                                                   |  2   |   V   |
| AC.6.6.4  | Bekreft at eksplisitte lagringsperioder er definert for alle treningsdatasett.                                                                                                                                                                                         |  1   |  D/V  |
| AC.6.6.5  | Bekreft at datasett automatisk utløper, slettes eller blir vurdert for sletting ved slutten av livssyklusen.                                                                                                                                                           |  2   |  D/V  |
| AC.6.6.6  | Bekreft at oppbevarings- og slettingshandlinger blir loggført og kan revideres.                                                                                                                                                                                        |  2   |  D/V  |
| AC.6.6.7  | Verifiser at krav til datahjemmel og grensekryssende overføringer er identifisert og håndhevet for alle datasett.                                                                                                                                                      |  2   |  D/V  |
| AC.6.6.8  | Bekreft at sektorspesifikke forskrifter (f.eks. helsevesen, finans) er identifisert og håndtert i databehandlingen.                                                                                                                                                    |  2   |  D/V  |
| AC.6.6.9  | Verifiser at overholdelse av relevante personvernlover (f.eks. GDPR, CCPA) er dokumentert og gjennomgås regelmessig.                                                                                                                                                   |  2   |  D/V  |
| AC.6.6.10 | Bekreft at det finnes mekanismer for å svare på forespørsler fra registrerte om tilgang, retting, begrensning eller innsigelse.                                                                                                                                        |  2   |  D/V  |
| AC.6.6.11 | Bekreft at forespørsler blir loggført, sporet og oppfylt innen lovpålagte tidsfrister.                                                                                                                                                                                 |  2   |  D/V  |
| AC.6.6.12 | Bekreft at prosessene for rettigheter til den registrerte blir testet og gjennomgått regelmessig for effektivitet.                                                                                                                                                     |  2   |  D/V  |

### AC.6.7 Versjonering og endringsstyring

|    #     | Beskrivelse                                                                                                                                                 | Nivå | Rolle |
| :------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.6.7.1 | Bekreft at en konsekvensanalyse utføres før oppdatering eller utskifting av en datasettversjon, som dekker modellens ytelse, rettferdighet og overholdelse. |  2   |  D/V  |
| AC.6.7.2 | Bekreft at resultatene av konsekvensanalysen er dokumentert og gjennomgått av relevante interessenter.                                                      |  2   |  D/V  |
| AC.6.7.3 | Bekreft at tilbakestillingsplaner eksisterer i tilfelle nye versjoner introduserer uakseptable risikoer eller tilbakeslag.                                  |  2   |  D/V  |

### AC.6.8 Styring av syntetiske data

|    #     | Beskrivelse                                                                                                                       | Nivå | Rolle |
| :------: | --------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.6.8.1 | Bekreft at genereringsprosessen, parametrene og tiltenkt bruk av syntetiske data er dokumentert.                                  |  2   |  D/V  |
| AC.6.8.2 | Sørg for at syntetiske data blir risikovurdert for skjevhet, personvernlekkasje og representasjonsproblemer før bruk i opplæring. |  2   |  D/V  |

### AC.6.9 Tilgangsovervåking

|    #     | Beskrivelse                                                                                                                      | Nivå | Rolle |
| :------: | -------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.6.9.1 | Kontroller at tilgangslogger regelmessig gjennomgås for uvanlige mønstre, som store eksporteringer eller tilgang fra nye steder. |  2   |  D/V  |
| AC.6.9.2 | Bekreft at varsler genereres for mistenkelige tilgangshendelser og blir undersøkt raskt.                                         |  2   |  D/V  |

### AC.6.10 Styring av motstandertrening

|     #     | Beskrivelse                                                                                                                                                                                      | Nivå | Rolle |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| AC.6.10.1 | Verifiser at hvis adversarial trening brukes, er genereringen, håndteringen og versjoneringen av adversariale datasett dokumentert og kontrollert.                                               |  2   |  D/V  |
| AC.6.10.2 | Sørg for at effekten av trening for motstand mot adversarial angrep på modellens ytelse (både mot rene og adversariale input) og rettferdighetsmålinger blir evaluert, dokumentert og overvåket. |  3   |  D/V  |
| AC.6.10.3 | Bekreft at strategier for adversarial trening og robusthet blir periodisk gjennomgått og oppdatert for å motvirke utviklende teknikker for adversariale angrep.                                  |  3   |  D/V  |

---

## AC.7 Modell livssyklus styring og dokumentasjon

|   #    | Beskrivelse                                                                                                                                                            | Nivå | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.7.1 | Verifiser at alle modellelementer bruker semantisk versjonering (MAJOR.MINOR.PATCH) med dokumenterte kriterier som spesifiserer når hver versjonskomponent økes.       |  2   |  D/V  |
| AC.7.2 | Bekreft at nødimplementeringer krever dokumentert sikkerhetsrisikovurdering og godkjenning fra en forhåndsutpekt sikkerhetsmyndighet innen forhåndsavtalte tidsrammer. |  2   |  D/V  |
| AC.7.3 | Bekreft at rollback-artifakter (tidligere modellversjoner, konfigurasjoner, avhengigheter) beholdes i henhold til organisasjonens retningslinjer.                      |  2   |   V   |
| AC.7.4 | Bekreft at tilgang til revisjonslogg krever riktig autorisasjon, og at alle tilgangsforsøk blir loggført med brukeridentitet og tidsstempel.                           |  2   |  D/V  |
| AC.7.5 | Bekreft at arkiverte modellartefakter beholdes i samsvar med retningslinjer for datalagring.                                                                           |  1   |  D/V  |

---

## AC.8 Styring av sikkerhet for prompt, inndata og utdata

### AC.8.1 Forsvar mot promptinjektjon

|    #     | Beskrivelse                                                                                                                                                                                        | Nivå | Rolle |
| :------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.8.1.1 | Bekreft at adversarial evalueringstester (f.eks. Red Team "many-shot" prompts) kjøres før hver modell- eller prompt-malutgivelse, med suksessrategrenser og automatiserte sperrer for tilbakeslag. |  2   |  D/V  |
| AC.8.1.2 | Sørg for at alle oppdateringer av prompt-filterregler, versjoner av klassifiseringsmodeller og endringer i blokklisten er versjonskontrollerte og reviderbare.                                     |  3   |  D/V  |

### AC.8.2 Motstand mot adversarielle eksempler

|    #     | Beskrivelse                                                                                                                              | Nivå | Rolle |
| :------: | ---------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.8.2.1 | Verifiser at robusthetsmål (suksessrate for kjente angrepssett) spores over tid via automatisering, og at regresjoner utløser et varsel. |  3   |  D/V  |

### AC.8.3 Innhold- og policyvurdering

|    #     | Beskrivelse                                                                                                                                                                                | Nivå | Rolle |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| AC.8.3.1 | Bekreft at screeningsmodellen eller regelsettet blir ettertrent/oppdatert minst kvartalsvis, og at det inkluderer nylig observerte mønstre for jailbreak eller omgåelse av retningslinjer. |  2   |   D   |

### AC.8.4 Inndatahastighetsbegrensning og misbruksforebygging

|    #     | Beskrivelse                                                                                   | Nivå | Rolle |
| :------: | --------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.8.4.1 | Bekreft at logger for misbruksforebygging blir beholdt og gjennomgått for nye angrepsmønstre. |  3   |   V   |

### AC.8.5 Inndataopprinnelse og attribusjon

|    #     | Beskrivelse                                                                                                           | Nivå | Rolle |
| :------: | --------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.8.5.1 | Verifiser at alle brukerinnganger er merket med metadata (bruker-ID, økt, kilde, tidsstempel, IP-adresse) ved inntak. |  1   |  D/V  |
| AC.8.5.2 | Bekreft at opprinnelsesmetadata beholdes og kan revideres for alle behandlede innganger.                              |  2   |  D/V  |
| AC.8.5.3 | Sørg for at unormale eller upålitelige inngangskilder blir merket og utsatt for strengere kontroll eller blokkering.  |  2   |  D/V  |

---

## AC.9 Multimodal validering, MLOps og styring av infrastruktur

### AC.9.1 Multimodal sikkerhetsvalideringspipeline

|    #     | Beskrivelse                                                                                                                                                                                                                                | Nivå | Rolle |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| AC.9.1.1 | Bekreft at modalitetsspesifikke innholdsklassifikatorer oppdateres i henhold til dokumenterte tidsplaner (minst kvartalsvis) med nye trusselmønstre, adversarielle eksempler, og ytelsesbenchmarks opprettholdt over basestrenge terskler. |  3   |  D/V  |

### AC.9.2 CI/CD og byggesikkerhet

|    #     | Beskrivelse                                                                                                                        | Nivå | Rolle |
| :------: | ---------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.9.2.1 | Sørg for at infrastruktur-som-kode skannes ved hver commit, og at sammenslåinger blokkeres ved kritiske eller høyt alvorlige funn. |  1   |  D/V  |
| AC.9.2.2 | Bekreft at CI/CD-pipelines bruker kortvarige, avgrensede identiteter for tilgang til hemmeligheter og infrastruktur.               |  2   |  D/V  |
| AC.9.2.3 | Bekreft at byggeomgivelser er isolert fra produksjonsnettverk og data.                                                             |  2   |  D/V  |

### AC.9.3 Container- og bildesikkerhet

|    #     | Beskrivelse                                                                                                                                                                      | Nivå | Rolle |
| :------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.9.3.1 | Bekreft at containerbilder blir skannet for å blokkere hardkodede hemmeligheter (f.eks. API-nøkler, legitimasjon, sertifikater).                                                 |  2   |  D/V  |
| AC.9.3.2 | Sørg for at containerbilder skannes i henhold til organisasjonens tidsplaner, med KRITISKE sårbarheter som blokkerer distribusjon basert på organisasjonens risikogrenseverdier. |  1   |  D/V  |

### AC.9.4 Overvåking, Varsling og SIEM

|    #     | Beskrivelse                                                                                                                                                        | Nivå | Rolle |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| AC.9.4.1 | Bekreft at sikkerhetsvarsler integreres med SIEM-plattformer (Splunk, Elastic eller Sentinel) ved bruk av CEF- eller STIX/TAXII-formater med automatisk berikelse. |  2   |   V   |

### AC.9.5 Sårbarhetshåndtering

|    #     | Beskrivelse                                                                                                                                                          | Nivå | Rolle |
| :------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.9.5.1 | Bekreft at sårbarheter med HØY alvorlighetsgrad blir utbedret i henhold til organisatoriske risikostyringstidslinjer, med nødprosedyrer for aktivt utnyttede CVE-er. |  2   |  D/V  |

### AC.9.6 Konfigurasjons- og avdriftskontroll

|    #     | Beskrivelse                                                                                                                                                                                     | Nivå | Rolle |
| :------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.9.6.1 | Bekreft at konfigurasjonsavvik oppdages ved bruk av verktøy (Chef InSpec, AWS Config) i henhold til organisasjonens overvåkingskrav, med automatisk tilbakestilling for uautoriserte endringer. |  2   |  D/V  |

### AC.9.7 Sikring av produksjonsmiljøet

|    #     | Beskrivelse                                                                                                                                                                               | Nivå | Rolle |
| :------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.9.7.1 | Bekreft at produksjonsmiljøer blokkerer SSH-tilgang, deaktiverer debug-endepunkter, og krever endringsforespørsler med organisatoriske krav til forhåndsvarsel, unntatt i nødsituasjoner. |  2   |  D/V  |

### AC.9.8 Frigivelsesfremmende porter

|    #     | Beskrivelse                                                                                                                                                | Nivå | Rolle |
| :------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.9.8.1 | Verifiser at godkjenningsporter inkluderer automatiserte sikkerhetstester (SAST, DAST, container-skanning) med krav om null KRITISKE funn for godkjenning. |  2   |  D/V  |

### AC.9.9 Overvåking av arbeidsbelastning, kapasitet og kostnader

|    #     | Beskrivelse                                                                                                                                                                                            | Nivå | Rolle |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| AC.9.9.1 | Bekreft at GPU/TPU-utnyttelse overvåkes med varsler som utløses ved organisasjonsdefinerte terskler, og at automatisk skalerings- eller lastbalansering aktiveres basert på kapasitetsstyringsregler.  |  1   |  D/V  |
| AC.9.9.2 | Verifiser at AI-arbeidsbelastningsmålinger (slutningstidsforsinkelse, gjennomstrømning, feilrater) samles inn i henhold til organisasjonens overvåkingskrav og korreleres med infrastrukturutnyttelse. |  1   |  D/V  |
| AC.9.9.3 | Bekreft at kostnadsovervåking sporer forbruk per arbeidsbelastning/leietaker med varsler basert på organisasjonens budsjettgrenser og automatiserte kontroller for budsjettoverskridelser.             |  2   |   V   |
| AC.9.9.4 | Bekreft at kapasitetsplanlegging bruker historiske data med organisasjonsdefinerte prognoseperioder og automatisert ressursprovisjonering basert på etterspørselmønstre.                               |  3   |   V   |

### AC.9.10 Godkjenninger og revisjonsspor

|     #     | Beskrivelse                                                                                                                                                   | Nivå | Rolle |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.9.10.1 | Verifiser at miljøfremming krever godkjenning fra organisatorisk definerte autoriserte personer med kryptografiske signaturer og uforanderlige revisjonsspor. |  1   |  D/V  |

### AC.9.11 Styring av IaC

|     #     | Beskrivelse                                                                                                                                            | Nivå | Rolle |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| AC.9.11.1 | Bekreft at endringer i infrastruktur-som-kode krever kollegagjennomgang med automatisert testing og sikkerhetsskanning før sammenslåing til hovedgren. |  2   |  D/V  |

### AC.9.12 Datahåndtering i ikke-produksjonsmiljø

|     #     | Beskrivelse                                                                                                                                                                            | Nivå | Rolle |
| :-------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.9.12.1 | Bekreft at ikke-produksjonsdata er anonymisert i henhold til organisasjonens personvernkrav, syntetisk datagenerering, eller fullstendig datamaskering med verifisert fjerning av PII. |  2   |  D/V  |

### AC.9.13 Sikkerhetskopiering og katastrofegjenoppretting

|     #     | Beskrivelse                                                                                                                                                                                                      | Nivå | Rolle |
| :-------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.9.13.1 | Verifiser at infrastrukturkonfigurasjoner sikkerhetskopieres i henhold til organisasjonens sikkerhetskopieringsplaner til geografisk separate regioner med implementering av 3-2-1 sikkerhetskopieringsstrategi. |  1   |  D/V  |
| AC.9.13.2 | Verifiser at gjenopprettingsprosedyrer blir testet og validert gjennom automatisert testing i henhold til organisatoriske tidsplaner, med RTO- og RPO-mål som oppfyller organisatoriske krav.                    |  2   |   V   |
| AC.9.13.3 | Bekreft at katastrofegjenoppretting inkluderer AI-spesifikke kjørebøker med gjenoppretting av modellvekter, gjenoppbygging av GPU-klynger og kartlegging av tjenesteavhengigheter.                               |  3   |   V   |

### AC.9.14 Overholdelse og dokumentasjon

|     #     | Beskrivelse                                                                                                                                                                   | Nivå | Rolle |
| :-------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.9.14.1 | Verifiser at infrastrukturens samsvar blir vurdert i henhold til organisatoriske tidsplaner mot SOC 2, ISO 27001 eller FedRAMP-kontroller med automatisert evidensinnsamling. |  2   |  D/V  |
| AC.9.14.2 | Bekreft at infrastrukturdokumentasjonen inkluderer nettverksdiagrammer, dataflytkart og trusselmodeller oppdatert i samsvar med organisasjonens endringsstyringskrav.         |  2   |   V   |
| AC.9.14.3 | Sørg for at infrastrukturendringer gjennomgår automatisert vurdering av samsvarspåvirkning med regulatoriske godkjenningsarbeidsflyter for høyrisikoendringer.                |  3   |  D/V  |

### AC.9.15 Maskinvare og forsyningskjede

|     #     | Beskrivelse                                                                                                                                                                                   | Nivå | Rolle |
| :-------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.9.15.1 | Bekreft at firmware for AI-akseleratorer (GPU BIOS, TPU-firmware) er verifisert med kryptografiske signaturer og oppdatert i henhold til organisasjonens tidslinjer for patch-administrasjon. |  2   |  D/V  |
| AC.9.15.2 | Bekreft at AI-maskinvareforsyningskjeden inkluderer opprinnelsesverifisering med produsentsertifikater og validering av manipulasjons-sårbar emballasje.                                      |  3   |   V   |

### AC.9.16 Skystrategi og portabilitet

|     #     | Beskrivelse                                                                                                                                                                  | Nivå | Rolle |
| :-------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.9.16.1 | Bekreft at forebygging av leverandørlås i skyen inkluderer bærbar infrastruktur-som-kode, standardiserte API-er og datatekportfunksjoner med verktøy for formatkonvertering. |  3   |   V   |
| AC.9.16.2 | Bekreft at fler-sky kostnadsoptimalisering inkluderer sikkerhetskontroller som forhindrer ressursoverspredning samt uautoriserte kostnader for datatransfer mellom skyer.    |  3   |   V   |

### AC.9.17 GitOps og selvhelbredende

|     #     | Beskrivelse                                                                                                                                                              | Nivå | Rolle |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| AC.9.17.1 | Bekreft at GitOps-repositorier krever signerte commits med GPG-nøkler og branch-beskyttelsesregler som hindrer direkte pushes til hovedbrancher.                         |  2   |  D/V  |
| AC.9.17.2 | Bekreft at selvhelbredende infrastruktur inkluderer korrelasjon av sikkerhetshendelser med automatisert hendelsesrespons og arbeidsflyter for varsling av interessenter. |  3   |   V   |

### AC.9.18 Nulltillit, agenter, provisjonering og bosettingsattestasjon

|     #     | Beskrivelse                                                                                                                                                     | Nivå | Rolle |
| :-------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AC.9.18.1 | Bekreft at tilgang til skyressurser inkluderer null-tillit-verifisering med kontinuerlig autentisering.                                                         |  2   |  D/V  |
| AC.9.18.2 | Bekreft at automatisert infrastrukturprovisionering inkluderer validering av sikkerhetspolicy med distribusjonsblokkering for ikke-kompatible konfigurasjoner.  |  2   |  D/V  |
| AC.9.18.3 | Bekreft at automatisert infrastrukturprovisjonering validerer sikkerhetspolicyer under CI/CD, og at ikke-kompatible konfigurasjoner blokkeres fra distribusjon. |  2   |  D/V  |
| AC.9.18.4 | Bekreft at krav til datalagringssted håndheves gjennom kryptografisk attestasjon av lagringssteder.                                                             |  3   |  D/V  |
| AC.9.18.5 | Bekreft at sikkerhetsvurderinger fra skytilbydere inkluderer agent-spesifikk trusselmodellering og risikovurdering.                                             |  3   |  D/V  |

### AC.9.19 Tilgangskontroll og identitet

|   #   | Beskrivelse                                                                                                                                                                                            | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 5.1.3 | Bekreft at nye ledere gjennomgår identitetsbekreftelse som er i samsvar med NIST 800-63-3 IAL-2 eller tilsvarende standarder før de får tilgang til produksjonssystemet.                               |  2   |   D   |
| 5.1.4 | Bekreft at tilgangsvurderinger gjennomføres kvartalsvis med automatisk deteksjon av inaktive kontoer, håndheving av rotasjon for påloggingsinformasjon og arbeidsflyter for de-provisionering.         |  2   |   V   |
| 5.2.2 | Bekreft at prinsippene om minste privilegium håndheves som standard for servicekontoer, med start på skrivebeskyttet tilgang, og at dokumentert forretningsmessig begrunnelse kreves for skriveadgang. |  1   |  D/V  |
| 5.3.3 | Bekreft at policydefinisjoner er versjonskontrollerte, fagfellevurdert, og validert gjennom automatisert testing i CI/CD-pipelines før produksjonsutplassering.                                        |  2   |   D   |
| 5.3.4 | Sørg for at policy-evalueringsresultater inkluderer beslutningsbegrunnelser og sendes til SIEM-systemer for korrelasjonsanalyse og samsvarsrapportering.                                               |  2   |   V   |
| 5.4.4 | Bekreft at evaluering av policy-latens overvåkes kontinuerlig med automatiske varsler for tidsavbruddsforhold som kan muliggjøre omgåelse av autorisasjon.                                             |  2   |   V   |
| 5.5.4 | Bekreft at raderingsalgoritmer er deterministiske, versjonskontrollerte, og opprettholder revisjonslogger for å støtte samsvarsundersøkelser og rettsmedisinsk analyse.                                |  2   |   V   |
| 5.5.5 | Verifiser at hendelser med høy risiko for sensur genererer adaptive logger som inkluderer kryptografiske hasher av originalinnhold for rettsmedisinsk gjenfinning uten datalekkasjer.                  |  3   |   V   |
| 5.7.5 | Bekreft at agentens feilsituasjoner og unntakshåndtering inkluderer informasjon om kapabilitetsomfang for å støtte hendelsesanalyse og rettsmedisinsk undersøkelse.                                    |  3   |   V   |
| 5.4.2 | Bekreft at sitater, referanser og kildehenvisninger i modellens utdata blir validert mot innringeres rettigheter, og fjernet hvis uautorisert tilgang oppdages.                                        |  1   |  D/V  |

### Nye elementer som skal integreres ovenfor

|   #   | Beskrivelse                                                                                                                                      | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 2.3.3 | Sørg for at det tillatte tegnsettet blir jevnlig gjennomgått og oppdatert for å sikre at det fortsatt er i samsvar med forretningsbehovene.      |  2   |  D/V  |
| 7.2.4 | Bekreft at terskler og detektorer blir rekalibrert etter større oppdateringer av modell eller kunnskapsbase.                                     |  3   |  D/V  |
| 7.2.5 | Bekreft at dashbordvisualiseringer sporer hallusinasjonsrater.                                                                                   |  3   |   V   |
| 7.5.4 | Bekreft at forklaringsartefakter er versjonskontrollert sammen med modellutgivelser for revisjonssporbarhet.                                     |  3   |   V   |
| 7.6.5 | Bekreft at overvåkingspipelines er penetrasjonstestet og tilgangskontrollert for å unngå lekkasje av sensitive logger.                           |  3   |   V   |
| 7.6.4 | Verifiser at overvåkingsdata blir matet tilbake til re-trening, finjustering eller regeloppdateringer innenfor en dokumentert MLOps-arbeidsflyt. |  2   |  D/V  |

