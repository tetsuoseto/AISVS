# Vedlegg B: Strategiske kontroller

## C4.15 Kvantebestandig infrastruktursikkerhet

Forbered AI-infrastruktur for kvanteberegnings trusler gjennom post-kvantekryptografi og kvantesikre protokoller.

|   #    | Beskrivelse                                                                                                                                                                                           | Nivå | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.15.1 | Verifiser at AI-infrastrukturen implementerer NIST-godkjente post-kvantemessige kryptografiske algoritmer (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) for nøkkelutveksling og digitale signaturer. |  3   |  D/V  |
| 4.15.2 | Verifiser at kvantekrypteringssystemer (QKD) er implementert for høysikkerhets AI-kommunikasjon med kvantesikre nøkkelhåndteringsprotokoller.                                                         |  3   |  D/V  |
| 4.15.3 | Bekreft at kryptografiske agilitetssystemer muliggjør rask migrering til nye post-kvantemessige algoritmer med automatisert sertifikat- og nøkkelrotasjon.                                            |  3   |  D/V  |
| 4.15.4 | Verifiser at kvante-trusselmodellering vurderer AI-infrastrukturens sårbarhet for kvanteangrep med dokumenterte migreringstidslinjer og risikovurderinger.                                            |  3   |   V   |
| 4.15.5 | Bekreft at hybride klassiske-kvantemessige kryptografisystemer gir flere lag med beskyttelse i overgangsperioden til kvantecomputere, samtidig som ytelsen overvåkes.                                 |  3   |  D/V  |

---

## C4.17 Infrastruktur for Null-Kunnskap

Implementer null-kunnskaps bevis systemer for personvernbeskyttende AI-verifisering og autentisering uten å avsløre sensitiv informasjon.

|   #    | Beskrivelse                                                                                                                                                         | Nivå | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.17.1 | Bekreft at null-kunnskapsbevis (ZK-SNARKs) verifiserer integriteten til AI-modellen og opprinnelsen til treningen uten å eksponere modellvekter eller treningsdata. |  3   |  D/V  |
| 4.17.2 | Bekreft at ZK-baserte autentiseringssystemer muliggjør personvernbevarende brukerautentisering for AI-tjenester uten å avsløre identitetsrelatert informasjon.      |  3   |  D/V  |
| 4.17.3 | Bekreft at private set intersection (PSI)-protokoller muliggjør sikker datamatching for føderert AI uten å avsløre individuelle datasett.                           |  3   |  D/V  |
| 4.17.4 | Verifiser at null-kunnskaps maskinlæringssystemer (ZKML) muliggjør verifiserbare AI-slutninger med kryptografisk bevis på korrekt beregning.                        |  3   |  D/V  |
| 4.17.5 | Bekreft at ZK-rollups gir skalerbar, personvernbevarende AI-transaksjonsbehandling med batchverifisering og redusert beregningskostnad.                             |  3   |  D/V  |

---

## C4.18 Forebygging av sidelkanalangrep

Beskytt AI-infrastrukturen mot tidsmåling-, strøm-, elektromagnetiske- og hurtigbufferbaserte sidekanalangrep som kan lekke sensitiv informasjon.

|   #    | Beskrivelse                                                                                                                                                    | Nivå | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.18.1 | Verifiser at AI-inferensens tidsbruk er normalisert ved bruk av konstant-tidsalgoritmer og utfylling for å forhindre tidsbaserte modelluttrekksangrep.         |  3   |  D/V  |
| 4.18.2 | Bekreft at beskyttelse mot strøm-analyse inkluderer støyinjeksjon, filtrering av strømlinjen og randomiserte utførelsesmønstre for AI-maskinvare.              |  3   |  D/V  |
| 4.18.3 | Bekreft at sidekanalmitigering basert på cache bruker cache-partisjonering, randomisering og flush-instruksjoner for å forhindre informasjonslekkasje.         |  3   |  D/V  |
| 4.18.4 | Bekreft at beskyttelse mot elektromagnetisk utsendelse inkluderer skjerming, signalfiltrering og tilfeldig behandling for å forhindre TEMPEST-lignende angrep. |  3   |  D/V  |
| 4.18.5 | Bekreft at mikroarkitektoniske sidekanalforsvar inkluderer kontroller for spekulativ utførelse og obfuskering av minnetilgangsmønstre.                         |  3   |  D/V  |

---

## C4.19 Nevrormorf og spesialisert AI maskinvare sikkerhet

Sikre nye AI-maskinvarearkitekturer inkludert nevromorfe brikker, FPGAer, tilpassede ASICer og optiske databehandlingssystemer.

|   #    | Beskrivelse                                                                                                                                                             | Nivå | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.19.1 | Bekreft at sikkerheten til nevromorfe brikker inkluderer kryptering av spike-mønstre, beskyttelse av synaptiske vekter og maskinvarebasert validering av læringsregler. |  3   |  D/V  |
| 4.19.2 | Bekreft at FPGA-baserte AI-akseleratorer implementerer bitstrømkryptering, antimanipulasjonsmekanismer og sikker konfigurasjonslasting med autentiserte oppdateringer.  |  3   |  D/V  |
| 4.19.3 | Bekreft at tilpasset ASIC-sikkerhet inkluderer sikkerhetsprosessorer på chip, maskinvarebasert tillitsanker og sikker nøkkellagring med manipulasjonsdeteksjon.         |  3   |  D/V  |
| 4.19.4 | Bekreft at optiske databehandlingssystemer implementerer kvantesikker optisk kryptering, sikker fotonisk switching og beskyttet optisk signalbehandling.                |  3   |  D/V  |
| 4.19.5 | Bekreft at hybride analog-digitale AI-brikker inkluderer sikker analog beregning, beskyttet lagring av vekter og autentisert analog-til-digital konvertering.           |  3   |  D/V  |

---

## C4.20 Personvernbevarende databehandlingsinfrastruktur

Implementer infrastrukturelle kontroller for personvernbevarende beregning for å beskytte sensitiv data under AI-behandling og -analyse.

|   #    | Beskrivelse                                                                                                                                                                                 | Nivå | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.20.1 | Verifiser at homomorf krypteringsinfrastruktur muliggjør kryptert beregning på sensitive AI-arbeidsbelastninger med kryptografisk integritetsverifisering og ytelsesovervåking.             |  3   |  D/V  |
| 4.20.2 | Bekreft at private informasjonsinnhentingssystemer muliggjør databaseforespørsler uten å avsløre forespørselsmønstre, med kryptografisk beskyttelse av tilgangsmønstre.                     |  3   |  D/V  |
| 4.20.3 | Bekreft at sikre multi-parti beregningsprotokoller muliggjør personvernbevarende AI-inferens uten å eksponere individuelle input eller mellomliggende beregninger.                          |  3   |  D/V  |
| 4.20.4 | Bekreft at personvernbevarende nøkkeladministrasjon inkluderer distribuert nøkkelsgenerering, terskelkryptografi og sikker nøkkelrotasjon med maskinvarebasert beskyttelse.                 |  3   |  D/V  |
| 4.20.5 | Bekreft at personvernbeskyttende beregningsytelse er optimalisert gjennom batchbehandling, caching og maskinvareakselerasjon samtidig som kryptografiske sikkerhetsgarantier opprettholdes. |  3   |  D/V  |

| 4.9.1 | Bekreft at alle skybaserte miljøer er integrert i sentraliserte identitetssystemer for å sikre konsekvent autentisering. | 1 | D/V |
| 4.9.2 | Verifiser at multi-sky-distribusjoner bruker fødererte identitetsstandarder (f.eks. OIDC, SAML) med sentralisert policyhåndhevelse på tvers av leverandører. | 2 | D/V |
| 4.9.3 | Verifiser at kryss-sky- og hybrid dataoverføringer bruker ende-til-ende kryptering med kundestyrte nøkler og håndhever jurisdiksjonsmessige krav til dataresidens. | 2 | D/V |
| 4.9.1 | Bekreft at skybasert lagringsintegrasjon bruker ende-til-ende-kryptering med nøkkelhåndtering kontrollert av agenten. | 1 | D/V |
| 4.9.2 | Bekreft at sikkerhetsgrenser for hybrid distribusjon er klart definert med krypterte kommunikasjonskanaler. | 2 | D/V |

