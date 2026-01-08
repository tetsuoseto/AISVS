# C4 Infrastruktur, konfigurasjon og distribusjonssikkerhet

## Kontrollmål

AI-infrastruktur må sikres mot privilegieeskalering, manipulasjon i forsyningskjeden og lateral bevegelse gjennom sikker konfigurasjon, kjøretidsisolasjon, betrodde distribusjonspipelines og omfattende overvåking. Bare validerte og autoriserte infrastrukturelementer når produksjon gjennom kontrollerte prosesser som sikrer sikkerhet, integritet og revisjonsspor.

---

## C4.1 Kjøretidsmiljøisolasjon

Forhindre container-unnslipp og privilegieeskalering gjennom OS-nivå isolasjonsprimitiver.

|   #   | Beskrivelse                                                                                                                                                                                                       | Nivå | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.1.1 | Sørg for at alle AI-arbeidsbelastninger kjører med minimale nødvendige tillatelser på operativsystemet, for eksempel ved å fjerne unødvendige Linux-funksjoner i tilfelle en container.                           |  1   |  D/V  |
| 4.1.2 | Bekreft at arbeidsmengder er beskyttet av teknologier som begrenser utnyttelse, slik som sandboxing, seccomp-profiler, AppArmor, SELinux eller lignende, og at konfigurasjonen er passende.                       |  1   |  D/V  |
| 4.1.3 | Verifiser at arbeidsbelastninger kjører med et skrivebeskyttet rotfilsystem, og at eventuelle skrivbare monteringer er eksplisitt definert og sikret med restriktive alternativer (f.eks. noexec, nosuid, nodev). |  2   |  D/V  |
| 4.1.4 | Verifiser at kjøretidsovervåking oppdager privilegieeskalerings- og container-fluktadferd og automatisk terminerer prosesser som bryter reglene.                                                                  |  2   |  D/V  |
| 4.1.5 | Bekreft at høyrisiko AI-arbeidsbelastninger kjører i maskinvare-isolerte miljøer (for eksempel TEEs, betrodde hypervisorer eller bare-metal noder) kun etter vellykket ekstern attestasjonskontroll.              |  3   |  D/V  |

---

## C4.2 Sikker bygging og distribusjonspipelines

Sikre kryptografisk integritet og sikkerhet i forsyningskjeden gjennom reproduserbare bygg og signerte artefakter.

|   #   | Beskrivelse                                                                                                                                                         | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.2.1 | Bekreft at bygg er reproducerbare og produserer signert opprinnelsesmetadata som er passende for byggeartifaktene og som kan verifiseres uavhengig.                 |  1   |  D/V  |
| 4.2.2 | Bekreft at byggeprosesser produserer en programvare-innholdsfortegnelse (SBOM) og blir signert før de godkjennes for distribusjon.                                  |  2   |  D/V  |
| 4.2.3 | Verifiser at signaturer og proveniensmetadata for byggeartefakter (for eksempel containerbilder) valideres ved distribusjon, og at uverifiserte artefakter avvises. |  2   |  D/V  |

---

## C4.3 Nettverkssikkerhet og tilgangskontroll

Implementer nulltillatelsesnettverk med standard nektingspolitikker og krypterte kommunikasjoner.

|   #   | Beskrivelse                                                                                                                                                                                                                    | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 4.3.1 | Bekreft at nettverkspolicyer håndhever standard-nektelse for inngående og utgående trafikk, med kun nødvendige tjenester eksplisitt tillatt.                                                                                   |  1   |  D/V  |
| 4.3.2 | Bekreft at protokoller for administrativ tilgang (f.eks. SSH, RDP) og tilgang til skymetadata-tjenester er begrenset og krever sterk autentisering.                                                                            |  1   |  D/V  |
| 4.3.3 | Bekreft at utgående trafikk er begrenset til godkjente destinasjoner og at alle forespørsler loggføres.                                                                                                                        |  2   |  D/V  |
| 4.3.4 | Verifiser at kommunikasjon mellom tjenester bruker gjensidig TLS med sertifikatvalidering og regelmessig automatisk rotasjon.                                                                                                  |  2   |  D/V  |
| 4.3.5 | Bekreft at AI-arbeidslaster og miljøer (utvikling, test, produksjon) kjører i isolerte nettverkssegmenter (VPCer/VNets) uten direkte internett-tilgang og uten delte IAM-roller, sikkerhetsgrupper eller kryssmiljøtilkobling. |  2   |  D/V  |

## C4.4 Hemmeligheter og kryptografisk nøkkelhåndtering

Beskytt hemmeligheter og kryptografiske nøkler med sikker lagring, automatisert rotasjon og sterke tilgangskontroller.

|   #   | Beskrivelse                                                                                                                                                                                                                                                 | Nivå | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.4.1 | Bekreft at hemmeligheter lagres i et dedikert system for hemmelighetshåndtering med kryptering i ro og isolert fra applikasjonsarbeidsbelastninger.                                                                                                         |  1   |  D/V  |
| 4.4.2 | Bekreft at kryptografiske nøkler genereres og lagres i maskinvarebaserte moduler (f.eks. HSM-er, sky-KMS).                                                                                                                                                  |  1   |  D/V  |
| 4.4.3 | Bekreft at tilgang til produksjonshemmeligheter krever sterk autentisering.                                                                                                                                                                                 |  1   |  D/V  |
| 4.4.4 | Verifiser at hemmeligheter distribueres til applikasjoner ved kjøretid gjennom et dedikert system for hemmelighetshåndtering. Hemmeligheter må aldri være innebygd i kildekode, konfigurasjonsfiler, byggeartefakter, containerbilder eller miljøvariabler. |  1   |  D/V  |
| 4.4.5 | Bekreft at rotasjon av hemmeligheter er automatisert.                                                                                                                                                                                                       |  2   |  D/V  |

---

## C4.5 AI arbeidsbelastnings-sandboxing og validering

Isoler uautoriserte AI-modeller i sikre sandkasser og beskytte sensitive AI-arbeidsbelastninger ved hjelp av betrodde kjøreomgivelser (TEEs) og konfidensialitetsteknologier.

|   #   | Beskrivelse                                                                                                                                                                | Nivå | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.5.1 | Sørg for at eksterne eller uautoriserte AI-modeller kjører i isolerte sandkasser.                                                                                          |  1   |  D/V  |
| 4.5.2 | Bekreft at sandkasseisolerte arbeidsoppgaver som standard ikke har utgående nettverkstilkobling, med eventuell nødvendig tilgang eksplisitt definert.                      |  1   |  D/V  |
| 4.5.3 | Bekreft at arbeidsbelastningsattestering utføres før lasting av modell eller arbeidsbelastning, for å sikre kryptografisk bevis på et betrodd utførelsesmiljø.             |  2   |  D/V  |
| 4.5.4 | Bekreft at konfidensielle arbeidsbelastninger kjøres innenfor et betrodd kjøreområde (TEE) som gir maskinvarerettet isolasjon, minne-kryptering og integritetsbeskyttelse. |  3   |  D/V  |
| 4.5.5 | Sørg for at konfidensielle inferenstjenester hindrer modeleksktraksjon gjennom kryptert beregning med forseglede modellvekter og beskyttet utførelse.                      |  3   |  D/V  |
| 4.5.6 | Bekreft at orkestrering av betrodde utførelsesmiljøer inkluderer livssyklusstyring, ekstern attestasjon og krypterte kommunikasjonskanaler.                                |  3   |  D/V  |
| 4.5.7 | Bekreft at sikker flerpartsberegning (SMPC) muliggjør samarbeidende AI-trening uten å eksponere individuelle datasett eller modellparametere.                              |  3   |  D/V  |

---

## C4.6 AI-infrastruktur Ressursstyring, sikkerhetskopiering og gjenoppretting

Forebygg ressursutmattelsesangrep og sørg for rettferdig ressursallokering gjennom kvoter og overvåking. Oppretthold infrastrukturens robusthet gjennom sikre sikkerhetskopier, testede gjenopprettingsprosedyrer og evner for katastrofegjenoppretting.

|   #   | Beskrivelse                                                                                                                                                                                                                               | Nivå | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.6.1 | Bekreft at arbeidsbelastningens ressursforbruk er begrenset på passende måte med for eksempel Kubernetes ResourceQuotas eller lignende for å redusere risikoen for tjenestenektangrep.                                                    |  2   |  D/V  |
| 4.6.2 | Bekreft at ressursuttømming utløser automatiserte beskyttelser (f.eks. hastighetsbegrensning eller arbeidsbelastningsisolasjon) når definerte terskler for CPU, minne eller forespørsler overskrides.                                     |  2   |  D/V  |
| 4.6.3 | Bekreft at sikkerhetssystemene kjører i isolerte nettverk med separate legitimasjoner, og at lagringssystemet enten kjører i et luftspaltet nettverk eller implementerer WORM (write-once-read-many) beskyttelse mot uautorisert endring. |  2   |  D/V  |

---

## C4.7 AI maskinvare sikkerhet

Sikre AI-spesifikke maskinvarekomponenter inkludert GPUer, TPUer og spesialiserte AI-akseleratorer.

|   #   | Beskrivelse                                                                                                                                                                                      | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 4.7.1 | Bekreft at før arbeidsbelastningen utføres, blir integriteten til AI-akseleratoren validert ved bruk av maskinvarebaserte attestasjonmekanismer (f.eks. TPM, DRTM eller tilsvarende).            |  2   |  D/V  |
| 4.7.2 | Bekreft at akseleratorminne (GPU) er isolert mellom arbeidsbelastninger gjennom partisjoneringsmekanismer med minne-rensing mellom jobber.                                                       |  2   |  D/V  |
| 4.7.3 | Verifiser at maskinvaresikkerhetsmoduler (HSM) beskytter AI-modellvekter og kryptografiske nøkler med sertifisering i henhold til FIPS 140-3 nivå 3 eller Common Criteria EAL4+.                 |  3   |  D/V  |
| 4.7.4 | Verifiser at akseleratorens fastvare (GPU/TPU/NPUs) er versjonfestet, signert og attestert ved oppstart; usignert eller feilsøkingsfastvare blokkertes.                                          |  2   |  D/V  |
| 4.7.5 | Bekreft at VRAM og minne på brikken blir nullstilt mellom jobber/leietakere, og at enhets tilbakestillingspolicyer forhindrer datarester mellom leietakere.                                      |  2   |  D/V  |
| 4.7.6 | Bekreft at partisjonerings-/isolasjonsegenskaper (f.eks. MIG/VM-partisjonering) håndheves per leietaker og forhindrer peer-to-peer-minnetilgang på tvers av partisjoner.                         |  2   |  D/V  |
| 4.7.7 | Sjekk at akseleratorforbindelser (NVLink/PCIe/InfiniBand/RDMA/NCCL) er begrenset til godkjente topologier og autentiserte endepunkter; ukrypterte lenker på tvers av leietakere er ikke tillatt. |  3   |  D/V  |
| 4.7.8 | Bekreft at akseleratortelemetri (strøm, temperaturer, ECC, ytelsestellere) eksporteres til SIEM/OTel og varsler om avvik som indikerer sidekanaler eller skjulte kanaler.                        |  3   |   D   |

---

## C4.8 Kant- og distribuert AI-sikkerhet

Sikre distribuerte AI-distribusjoner inkludert edge computing, føderert læring, og fler-steds arkitekturer.

|   #   | Beskrivelse                                                                                                                                                                                                                                                                                                | Nivå | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.8.1 | Bekreft at edge AI-enheter autentiserer mot sentral infrastruktur ved bruk av gjensidig TLS.                                                                                                                                                                                                               |  2   |  D/V  |
| 4.8.2 | Bekreft at edge-enheter implementerer sikker oppstart med verifiserte signaturer og tilbakerullingsbeskyttelse for å forhindre angrep som nedgraderer fastvaren.                                                                                                                                           |  2   |  D/V  |
| 4.8.3 | Verifiser at distribuert AI-koordinering bruker bysantinsk feil-tolerante konsensusmekanismer med deltakerverifisering og deteksjon av ondsinnede noder.                                                                                                                                                   |  3   |  D/V  |
| 4.8.4 | Verifiser at kommunikasjon fra kant til sky støtter båndbreddebegrensning, datakomprimering og sikker offline-operasjon med kryptert lokal lagring.                                                                                                                                                        |  3   |  D/V  |
| 4.8.5 | Sørg for at mobile eller edge-inferensapplikasjoner implementerer plattformnivå anti-manipulasjonsbeskyttelse (f.eks. kodesignering, verifisert oppstart, kjøretids selvintegritetssjekker) som oppdager og blokkerer modifiserte binærfiler, ompakkede apper eller tilknyttede instrumenteringsrammeverk. |  3   |  D/V  |
| 4.8.6 | Sørg for at modeller distribuert til edge- eller mobile enheter er kryptografisk signert under pakking, og at kjøretiden på enheten validerer disse signaturene eller sjekksummene før lasting eller inferens; uverifiserte eller endrede modeller må avvises.                                             |  3   |  D/V  |
| 4.8.7 | Bekreft at kjøretidsmiljøer for inferens på enheten håndhever isolasjon av prosess, minne og filtilgang for å forhindre dumping av modeller, feilsøking eller uthenting av mellomliggende innebygginger og aktiveringer.                                                                                   |  3   |  D/V  |
| 4.8.8 | Bekreft at modellvekter og sensitive parametere som lagres lokalt, er kryptert ved bruk av maskinvarebaserte nøkkel-lagre eller sikre kabinetter (f.eks. Android Keystore, iOS Secure Enclave, TPM/TEE), med nøkler utilgjengelige for brukermodus.                                                        |  3   |  D/V  |
| 4.8.9 | Verifiser at modeller pakket inn i mobile-, IoT- eller innebygde applikasjoner er kryptert eller obfuskert i hvilemodus, og bare dekryptert inne i en pålitelig runtime eller sikker enclave, for å forhindre direkte uthenting fra app-pakken eller filsystemet.                                          |  3   |  D/V  |

---

## Referanser

* [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework)
* [CIS Controls v8](https://www.cisecurity.org/controls/v8)
* [Kubernetes Security Best Practices](https://kubernetes.io/docs/concepts/security/)
* [Cloud Security Alliance: Cloud Controls Matrix](https://cloudsecurityalliance.org/research/cloud-controls-matrix/)
* [ENISA: Secure Infrastructure Design](https://www.enisa.europa.eu/topics/critical-information-infrastructures-and-services)
* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)

