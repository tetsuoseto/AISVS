# C4 Infrastruktur, Konfiguration & Udrulningssikkerhed

## Kontrolmål

AI-infrastruktur skal gøres modstandsdygtig over for privilegieeskalering, manipulation af forsyningskæden og lateral bevægelse gennem sikker konfiguration, runtime-isolering, betroede deployments pipelines og omfattende overvågning. Kun autoriserede, validerede infrastrukturkomponenter og konfigurationer når produktion gennem kontrollerede processer, der opretholder sikkerhed, integritet og revisionsevne.

Kerne Sikkerhedsmål: Kun kryptografisk signerede, sårbarhedsscannede infrastrukturobjekter når produktion gennem automatiserede valideringspipelines, som håndhæver sikkerhedspolitikker og opretholder uforanderlige revisionsspor.

---

## C4.1 Runtime-miljøisolering

Forhindr container-udbrud og rettighedsoptrapning gennem kerne-niveau isolationsprimitiver og obligatoriske adgangskontroller.

|   #   | Beskrivelse                                                                                                                                                                                                    | Niveau | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.1.1 | Bekræft, at alle AI-containere fjerner ALLE Linux-evner undtagen CAP_SETUID, CAP_SETGID samt eksplicit påkrævede evner dokumenteret i sikkerhedsbaselines.                                                     |   1    |  D/V  |
| 4.1.2 | Bekræft, at seccomp-profiler blokerer alle systemkald undtagen dem, der er på forhånd godkendte tilladelseslister, hvor overtrædelser fører til, at containeren afsluttes, og der genereres sikkerhedsalarmer. |   1    |  D/V  |
| 4.1.3 | Bekræft, at AI-arbejdsbelastninger kører med skrivebeskyttede rodfilsystemer, tmpfs til midlertidige data og navngivne volumener til vedvarende data med noexec monteringsmuligheder håndhævet.                |   2    |  D/V  |
| 4.1.4 | Bekræft, at eBPF-baseret runtime-overvågning (Falco, Tetragon eller tilsvarende) opdager forsøg på privilegieoptrapning og automatisk dræber krænkende processer inden for organisationens svartidskrav.       |   2    |  D/V  |
| 4.1.5 | Bekræft, at højrisiko AI-arbejdsbelastninger kører i hardware-isolerede miljøer (Intel TXT, AMD SVM eller dedikerede bare-metal noder) med attestationsverifikation.                                           |   3    |  D/V  |

---

## C4.2 Sikker build- og deployments-pipelines

Sikre kryptografisk integritet og forsyningskædesikkerhed gennem reproducerbare builds og underskrevne artefakter.

|   #   | Beskrivelse                                                                                                                                                                                       | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.2.1 | Bekræft, at infrastruktur-som-kode bliver scannet med værktøjer (tfsec, Checkov eller Terrascan) ved hver commit, og at merges blokeres ved fund af KRITISKE eller HØJ alvorlighedsgrad.          |   1    |  D/V  |
| 4.2.2 | Bekræft, at containerbygninger er reproducerbare med identiske SHA256-hashværdier på tværs af builds, og generer SLSA niveau 3 oprindelsesattester underskrevet med Sigstore.                     |   1    |  D/V  |
| 4.2.3 | Bekræft, at containerbilleder indeholder CycloneDX- eller SPDX SBOM'er og er signeret med Cosign, før de skubbes til registreringsdatabasen, hvor usignerede billeder afvises ved implementering. |   2    |  D/V  |
| 4.2.4 | Bekræft, at CI/CD-pipelines bruger OIDC-tokens fra HashiCorp Vault, AWS IAM-roller eller Azure Managed Identity med levetider, der ikke overstiger organisationens sikkerhedspolitiske grænser.   |   2    |  D/V  |
| 4.2.5 | Bekræft, at Cosign-signaturer og SLSA-proveniens valideres under udrulningsprocessen før container-eksekvering, og at verificeringsfejl får udrulningen til at fejle.                             |   2    |  D/V  |
| 4.2.6 | Bekræft, at bygge-miljøer kører i flygtige containere eller virtuelle maskiner uden vedvarende lagring og med netværks-isolering fra produktions VPC’er.                                          |   2    |  D/V  |

---

## C4.3 Netværkssikkerhed & Adgangskontrol

Implementer zero-trust netværk med standard-afvis-politikker og krypteret kommunikation.

|   #   | Beskrivelse                                                                                                                                                                                     | Niveau | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.3.1 | Bekræft, at Kubernetes NetworkPolicies eller en tilsvarende løsning implementerer default-deny ingress/egress med eksplicitte tilladelsesregler for nødvendige porte (443, 8080, osv.).         |   1    |  D/V  |
| 4.3.2 | Bekræft, at SSH (port 22), RDP (port 3389) og cloud metadata-endpoints (169.254.169.254) er blokeret eller kræver certifikatbaseret autentificering.                                            |   1    |  D/V  |
| 4.3.3 | Bekræft, at egress-trafik filtreres gennem HTTP/HTTPS-proxies (Squid, Istio eller cloud NAT-gateways) med domænetilladelseslister, og at blokerede forespørgsler logges.                        |   2    |  D/V  |
| 4.3.4 | Bekræft, at inter-service kommunikation anvender mutual TLS med certifikater, der roteres i henhold til organisationspolitikken, og at certifikatvalidering håndhæves (ingen skip-verify flag). |   2    |  D/V  |
| 4.3.5 | Bekræft, at AI-infrastrukturen kører i dedikerede VPC'er/VNets uden direkte internetadgang og kun kommunikerer gennem NAT-gateways eller bastionhosts.                                          |   2    |  D/V  |

---

## C4.4 Hemmeligheder og kryptografisk nøglehåndtering

Beskyt legitimationsoplysninger gennem hardware-baseret lagring og automatiseret rotation med zero-trust adgang.

|   #   | Beskrivelse                                                                                                                                                                                     | Niveau | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.4.1 | Bekræft, at hemmeligheder opbevares i HashiCorp Vault, AWS Secrets Manager, Azure Key Vault eller Google Secret Manager med kryptering ved hvile ved brug af AES-256.                           |   1    |  D/V  |
| 4.4.2 | Bekræft, at kryptografiske nøgler genereres i FIPS 140-2 Level 2 HSM'er (AWS CloudHSM, Azure Dedicated HSM) med nøgleudskiftning i overensstemmelse med den organisatoriske kryptografipolitik. |   1    |  D/V  |
| 4.4.3 | Bekræft, at automatisk rotation af hemmeligheder sker med nul nedetid ved implementering og øjeblikkelig rotation udløst af personaleændringer eller sikkerhedshændelser.                       |   2    |  D/V  |
| 4.4.4 | Bekræft, at containerbilleder scannes med værktøjer (GitLeaks, TruffleHog eller detect-secrets), der blokerer builds, der indeholder API-nøgler, adgangskoder eller certifikater.               |   2    |  D/V  |
| 4.4.5 | Bekræft, at adgang til produktionshemmeligheder kræver MFA med hardwaretokens (YubiKey, FIDO2) og registreres i uforanderlige revisionslogfiler med brugeridentiteter og tidsstempler.          |   2    |  D/V  |
| 4.4.6 | Bekræft, at hemmeligheder indsættes via Kubernetes-hemmeligheder, monterede volumener eller init-containere, og sørg for, at hemmeligheder aldrig indlejres i miljøvariabler eller billeder.    |   2    |  D/V  |

---

## C4.5 AI Arbejdsbelastnings-sandkasse og validering

Isoler uautoriserede AI-modeller i sikre sandkasser med omfattende adfærdsanalyse.

|   #   | Beskrivelse                                                                                                                                                                                | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 4.5.1 | Bekræft, at eksterne AI-modeller kører i gVisor, microVMs (såsom Firecracker, CrossVM) eller Docker-containere med --security-opt=no-new-privileges og --read-only flag.                   |   1    |  D/V  |
| 4.5.2 | Bekræft, at sandbox-miljøer ikke har netværksforbindelse (--network=none) eller kun adgang til localhost, hvor alle eksterne forespørgsler blokeres af iptables-regler.                    |   1    |  D/V  |
| 4.5.3 | Bekræft, at validering af AI-modeller inkluderer automatiseret red-team testning med organisatorisk defineret testdækning og adfærdsanalyse til bagdørsdetektion.                          |   2    |  D/V  |
| 4.5.4 | Bekræft, at før en AI-model promoveres til produktion, er dens sandbox-resultater kryptografisk underskrevet af autoriseret sikkerhedspersonale og gemt i uforanderlige revisionslogfiler. |   2    |  D/V  |
| 4.5.5 | Bekræft, at sandkassemiljøer bliver ødelagt og genskabt fra gyldne billeder mellem evalueringerne med fuldstændig oprydning af filsystem og hukommelse.                                    |   2    |  D/V  |

---

## C4.6 Infrastruktur Sikkerhedsovervågning

Kontinuerligt scanne og overvåge infrastrukturen med automatiseret udbedring og realtidsadvarsler.

|   #   | Beskrivelse                                                                                                                                                                                            | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 4.6.1 | Bekræft, at containerbilleder bliver scannet i henhold til organisatoriske tidsplaner, hvor KRITISKE sårbarheder blokerer implementering baseret på organisatoriske risikothresholds.                  |   1    |  D/V  |
| 4.6.2 | Bekræft, at infrastrukturen overholder CIS Benchmarks eller NIST 800-53-kontroller med organisatorisk definerede overholdelsestærskler og automatiseret afhjælpning for mislykkede kontroller.         |   1    |  D/V  |
| 4.6.3 | Verificer, at sårbarheder med HØJ alvorlighed bliver patchet i overensstemmelse med organisationens risikostyringstidslinjer, med nødprocedurer for aktivt udnyttede CVE'er.                           |   2    |  D/V  |
| 4.6.4 | Bekræft, at sikkerhedsalarmer integreres med SIEM-platforme (Splunk, Elastic eller Sentinel) ved hjælp af CEF- eller STIX/TAXII-formater med automatiseret berigelse.                                  |   2    |   V   |
| 4.6.5 | Verificer, at infrastrukturmålinger eksporteres til overvågningssystemer (Prometheus, DataDog) med SLA-dashboard og ledelsesrapportering.                                                              |   3    |   V   |
| 4.6.6 | Verificer, at konfigurationsafvigelse opdages ved brug af værktøjer (Chef InSpec, AWS Config) i henhold til organisatoriske overvågningskrav med automatisk tilbageførsel for uautoriserede ændringer. |   2    |  D/V  |

---

## C4.7 AI Infrastruktur Ressourcehåndtering

Forebyg ressourceudtrætningsangreb og sikr retfærdig ressourcefordeling gennem kvoter og overvågning.

|   #   | Beskrivelse                                                                                                                                                                                                     | Niveau | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.7.1 | Bekræft, at GPU/TPU-udnyttelse overvåges med alarmer, der aktiveres ved organisatorisk definerede tærskler, og at automatisk skalering eller loadbalancering aktiveres baseret på kapacitetsstyringspolitikker. |   1    |  D/V  |
| 4.7.2 | Bekræft, at AI-arbejdsbyrdemålinger (inferenzlatens, gennemløb, fejlprocenter) indsamles i overensstemmelse med organisatoriske overvågningskrav og korreleres med infrastrukturudnyttelsen.                    |   1    |  D/V  |
| 4.7.3 | Verificer, at Kubernetes ResourceQuotas eller tilsvarende begrænser individuelle arbejdsbelastninger i henhold til organisatoriske ressourcetildelingspolitikker med håndhævede hårde grænser.                  |   2    |  D/V  |
| 4.7.4 | Bekræft, at omkostningsovervågning sporer forbrug pr. arbejdsbyrde/lejer med alarmer baseret på organisatoriske budgetgrænser og automatiserede kontroller for budgetoverskridelser.                            |   2    |   V   |
| 4.7.5 | Bekræft, at kapacitetsplanlægning bruger historiske data med organisationsdefinerede prognoseperioder og automatiseret ressourceallokering baseret på efterspørgselsmønstre.                                    |   3    |   V   |
| 4.7.6 | Bekræft, at ressourceudmattelse udløser kredsløbsafbrydere i henhold til organisatoriske responskrav, herunder hastighedsbegrænsning baseret på kapacitets-politikker og arbejdsbelastningsisolation.           |   2    |  D/V  |

---

## C4.8 Adskillelse af miljøer og kontrol med promotion

Håndhæv strenge miljøgrænser med automatiserede promoveringsporte og sikkerhedsvalidering.

|   #   | Beskrivelse                                                                                                                                                                                                                             | Niveau | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.8.1 | Bekræft, at dev/test/prod-miljøer kører i separate VPC’er/VNets uden delte IAM-roller, sikkerhedsgrupper eller netværksforbindelser.                                                                                                    |   1    |  D/V  |
| 4.8.2 | Bekræft, at forfremmelse af miljøet kræver godkendelse fra organisatorisk defineret autoriseret personale med kryptografiske signaturer og uforanderlige revisionsspor.                                                                 |   1    |  D/V  |
| 4.8.3 | Bekræft, at produktionsmiljøer blokerer SSH-adgang, deaktiverer debug-endpoints og kræver ændringsanmodninger med organisatoriske varslingskrav på forhånd, undtagen i nødstilfælde.                                                    |   2    |  D/V  |
| 4.8.4 | Bekræft, at infrastruktur-som-kode ændringer kræver peer review med automatiseret testning og sikkerhedsscanning, inden de flettes til hovedgrenen.                                                                                     |   2    |  D/V  |
| 4.8.5 | Bekræft, at ikke-produktionsdata er anonymiseret i overensstemmelse med organisatoriske privatlivskrav, syntetisk datagenerering eller komplet datamaskering med verificeret fjernelse af personligt identificerbare oplysninger (PII). |   2    |  D/V  |
| 4.8.6 | Bekræft, at promotionsporte inkluderer automatiserede sikkerhedstest (SAST, DAST, container scanning) med krav om nul KRITISKE fund for godkendelse.                                                                                    |   2    |  D/V  |

---

## C4.9 Infrastruktur Backup & Gendannelse

Sikre infrastrukturens robusthed gennem automatiserede backups, testede genoprettelsesprocedurer og katastrofeberedskabskapaciteter.

|   #   | Beskrivelse                                                                                                                                                                                    | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.9.1 | Bekræft, at infrastrukturkonfigurationer sikkerhedskopieres i overensstemmelse med organisationens backup-planer til geografisk adskilte regioner med implementering af 3-2-1 backup-strategi. |   1    |  D/V  |
| 4.9.2 | Bekræft, at backup-systemer kører i isolerede netværk med separate legitimationsoplysninger og luftadskilt lagring for beskyttelse mod ransomware.                                             |   2    |  D/V  |
| 4.9.3 | Bekræft, at genoprettelsesprocedurer testes og valideres gennem automatiseret test i henhold til organisatoriske tidsplaner, hvor RTO- og RPO-mål opfylder organisationens krav.               |   2    |   V   |
| 4.9.4 | Bekræft, at katastrofe-genopretning inkluderer AI-specifikke runbooks med modelvægt-gendannelse, genopbygning af GPU-klynger og kortlægning af servicedependenser.                             |   3    |   V   |

---

## C4.10 Infrastrukturoverholdelse og -styring

Oprethold overholdelse af regler gennem kontinuerlig vurdering, dokumentation og automatiserede kontrolforanstaltninger.

|   #    | Beskrivelse                                                                                                                                                                               | Niveau | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.10.1 | Bekræft, at infrastrukturens overholdelse vurderes i henhold til organisatoriske tidsplaner mod SOC 2, ISO 27001 eller FedRAMP-kontroller med automatiseret indsamling af bevismateriale. |   2    |  D/V  |
| 4.10.2 | Sørg for, at infrastrukturens dokumentation inkluderer netværksdiagrammer, dataflowkort og trusselsmodeller, der er opdateret i henhold til organisationens krav til ændringsstyring.     |   2    |   V   |
| 4.10.3 | Sørg for, at infrastrukturændringer gennemgår automatiseret vurdering af compliance-påvirkning med regulatoriske godkendelsesarbejdsgange for højrisikomodifikationer.                    |   3    |  D/V  |

---

## C4.11 AI Hardware Sikkerhed

Sikre AI-specifikke hardwarekomponenter, herunder GPU'er, TPU'er og specialiserede AI-acceleratorer.

|   #    | Beskrivelse                                                                                                                                                                                          | Niveau | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.11.1 | Bekræft, at AI-accelerator firmware (GPU BIOS, TPU firmware) er verificeret med kryptografiske signaturer og opdateret i overensstemmelse med organisationens patch-management tidsplaner.           |   2    |  D/V  |
| 4.11.2 | Bekræft, at inden arbejdsbelastningens udførelse valideres AI-acceleratorens integritet ved hardwareattestation ved hjælp af TPM 2.0, Intel TXT eller AMD SVM.                                       |   2    |  D/V  |
| 4.11.3 | Verificer, at GPU-hukommelsen er isoleret mellem arbejdsbelastninger ved brug af SR-IOV, MIG (Multi-Instance GPU) eller tilsvarende hardwarepartitionering med hukommelsessanitering mellem opgaver. |   2    |  D/V  |
| 4.11.4 | Bekræft, at AI-hardwareforsyningskæden inkluderer oprindelsesverifikation med producentcertifikater og validering af manipulationssikkert emballage.                                                 |   3    |   V   |
| 4.11.5 | Bekræft, at hardware-sikkerhedsmoduler (HSM'er) beskytter AI-modelvægt og kryptografiske nøgler med FIPS 140-2 Level 3 eller Common Criteria EAL4+ certificering.                                    |   3    |  D/V  |

---

## C4.12 Edge & Distribueret AI Infrastruktur

Sikre distribuerede AI-implementeringer inklusive edge computing, fødereret læring og multi-site arkitekturer.

|   #    | Beskrivelse                                                                                                                                                                                               | Niveau | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.12.1 | Bekræft, at edge AI-enheder autentificerer til den centrale infrastruktur ved hjælp af mutual TLS med enhedscertifikater, der roteres i henhold til organisationens politik for certifikatadministration. |   2    |  D/V  |
| 4.12.2 | Bekræft, at edge-enheder implementerer secure boot med verificerede signaturer og rollback-beskyttelse, der forhindrer firmware-nedgraderingsangreb.                                                      |   2    |  D/V  |
| 4.12.3 | Bekræft, at distribueret AI-koordinering bruger byzantinsk fejltolerante konsensusalgoritmer med deltagervalidering og detektion af ondsindede noder.                                                     |   3    |  D/V  |
| 4.12.4 | Bekræft, at kommunikation fra edge til cloud inkluderer båndbreddebegrænsning, datakomprimering og offline driftsmuligheder med sikker lokal lagring.                                                     |   3    |  D/V  |

---

## C4.13 Sikkerhed i Multi-Cloud og Hybrid Infrastruktur

Sikre AI-arbejdsmængder på tværs af flere cloud-udbydere og hybride cloud-on-premises implementeringer.

|   #    | Beskrivelse                                                                                                                                                                           | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.13.1 | Bekræft, at multi-cloud AI-implementeringer bruger cloud-agnostisk identitetsfederation (OIDC, SAML) med centraliseret politikstyring på tværs af udbydere.                           |   2    |  D/V  |
| 4.13.2 | Bekræft, at kryds-cloud dataoverførsel bruger ende-til-ende kryptering med kundeadministrerede nøgler og datalokalitetkontroller håndhævet i henhold til jurisdiktion.                |   2    |  D/V  |
| 4.13.3 | Bekræft, at hybrid cloud AI-arbejdsbelastninger implementerer konsekvente sikkerhedspolitikker på tværs af on-premise og cloud-miljøer med enhedsovervågning og advarsler.            |   2    |  D/V  |
| 4.13.4 | Bekræft, at forebyggelse af cloud-leverandørlåsning inkluderer portabel infrastruktur-som-kode, standardiserede API'er og datalekportfunktioner med værktøjer til formatkonvertering. |   3    |   V   |
| 4.13.5 | Sørg for, at multi-cloud omkostningsoptimering inkluderer sikkerhedskontroller, der forhindrer ressourceudbredelse samt uautoriserede tvær-cloud dataoverførselsgebyrer.              |   3    |   V   |

---

## C4.14 Infrastrukturautomatisering & GitOps-sikkerhed

Sikre automatiseringspipelines for infrastruktur og GitOps-arbejdsgange til AI-infrastrukturstyring.

|   #    | Beskrivelse                                                                                                                                                                                                 | Niveau | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.14.1 | Bekræft, at GitOps-repositorier kræver underskrevne commits med GPG-nøgler og branch-beskyttelsesregler, der forhindrer direkte push til hovedbrancher.                                                     |   2    |  D/V  |
| 4.14.2 | Bekræft, at infrastrukturautomatisering inkluderer driftregistrering med automatiske udbedrings- og rollback-funktioner, som udløses i henhold til organisatoriske responskrav for uautoriserede ændringer. |   2    |  D/V  |
| 4.14.3 | Bekræft, at automatiseret infrastrukturudrulning inkluderer validering af sikkerhedspolitikker med udrulningsblokering for ikke-overholdende konfigurationer.                                               |   2    |  D/V  |
| 4.14.4 | Bekræft, at hemmeligheder til infrastrukturautomatisering håndteres gennem eksterne hemmelighedsoperatører (External Secrets Operator, Bank-Vaults) med automatisk rotation.                                |   2    |  D/V  |
| 4.14.5 | Bekræft, at selvhelende infrastruktur inkluderer korrelation af sikkerhedshændelser med automatiseret hændelsesrespons og arbejdsgange til underretning af interessenter.                                   |   3    |   V   |

---

## C4.15 Kvantesikret Infrastruktur Sikkerhed

Forbered AI-infrastrukturen på trusler fra kvantecomputing gennem post-kvantekryptografi og kvantesikre protokoller.

|   #    | Beskrivelse                                                                                                                                                                                  | Niveau | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.15.1 | Bekræft, at AI-infrastrukturen implementerer NIST-godkendte post-kvante kryptografiske algoritmer (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) til nøgleudveksling og digitale signaturer. |   3    |  D/V  |
| 4.15.2 | Bekræft, at kvante-nøglefordelingssystemer (QKD) implementeres til højsikkerheds-AI-kommunikation med kvantesikre nøglestyringsprotokoller.                                                  |   3    |  D/V  |
| 4.15.3 | Bekræft, at kryptografiske agilitetssystemer muliggør hurtig overgang til nye post-kvante algoritmer med automatiseret certifikat- og nøgleudskiftning.                                      |   3    |  D/V  |
| 4.15.4 | Bekræft, at kvantetrusselsmodellering vurderer AI-infrastrukturs sårbarhed over for kvanteangreb med dokumenterede migrations-tidslinjer og risikovurderinger.                               |   3    |   V   |
| 4.15.5 | Verificer, at hybride klassiske-kvantemæssige kryptografiske systemer giver forsvar-i-dybden under kvanteovergangsperioden med ydelsesovervågning.                                           |   3    |  D/V  |

---

## C4.16 Fortrolig Computing & Sikkerhedsindelinger

Beskyt AI-arbejdsbelastninger og modelvægte ved hjælp af hardwarebaserede betroede udførelsesmiljøer og fortrolige beregningsteknologier.

|   #    | Beskrivelse                                                                                                                                                    | Niveau | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.16.1 | Bekræft, at følsomme AI-modeller kører inden for Intel SGX-enklaver, AMD SEV-SNP eller ARM TrustZone med krypteret hukommelse og attestationsverifikation.     |   3    |  D/V  |
| 4.16.2 | Bekræft, at fortrolige containere (Kata Containers, gVisor med fortrolig computing) isolerer AI-arbejdsmængder med hardwareunderstøttet hukommelseskryptering. |   3    |  D/V  |
| 4.16.3 | Bekræft, at fjernattestering validerer enclave-integritet, før AI-modeller indlæses, med kryptografisk bevis for et eksekveringsmiljøs ægthed.                 |   3    |  D/V  |
| 4.16.4 | Bekræft, at fortrolige AI-inferencetjenester forhindrer modelekstraktion gennem krypteret beregning med forseglede modelvægte og beskyttet udførelse.          |   3    |  D/V  |
| 4.16.5 | Bekræft, at orkestrering af trusted execution environment styrer den sikre enclave-livscyklus med fjernattestation og krypterede kommunikationskanaler.        |   3    |  D/V  |
| 4.16.6 | Bekræft, at sikker multi-part beregning (SMPC) muliggør samarbejdende AI-træning uden at afsløre individuelle datasæt eller modelparametre.                    |   3    |  D/V  |

---

## C4.17 Zero-Knowledge Infrastruktur

Implementer nul-videns bevis systemer til privatlivsbeskyttende AI-verifikation og autentificering uden at afsløre følsomme oplysninger.

|   #    | Beskrivelse                                                                                                                                                        | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 4.17.1 | Bekræft, at zero-knowledge beviser (ZK-SNARKs, ZK-STARKs) verificerer AI-modelintegritet og træningsoprindelse uden at afsløre modelvægte eller træningsdata.      |   3    |  D/V  |
| 4.17.2 | Bekræft, at ZK-baserede autentificeringssystemer muliggør privatlivsbevarende brugerbekræftelse for AI-tjenester uden at afsløre identitetsrelaterede oplysninger. |   3    |  D/V  |
| 4.17.3 | Bekræft, at private set intersection (PSI) protokoller muliggør sikker datamatchning for fødereret AI uden at eksponere individuelle datasæt.                      |   3    |  D/V  |
| 4.17.4 | Bekræft, at zero-knowledge maskinlæringssystemer (ZKML) muliggør verificerbare AI-afledninger med kryptografisk bevis for korrekt beregning.                       |   3    |  D/V  |
| 4.17.5 | Bekræft, at ZK-rollups leverer skalerbar, privatlivsbevarende AI-transaktionsbehandling med batchverifikation og reduceret beregningsmæssigt overhead.             |   3    |  D/V  |

---

## C4.18 Forebyggelse af sidekanalangreb

Beskyt AI-infrastruktur mod timing-, strøm-, elektromagnetiske og cache-baserede sidekanalangreb, der kan lække følsomme oplysninger.

|   #    | Beskrivelse                                                                                                                                                      | Niveau | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.18.1 | Bekræft, at AI-inferens timing er normaliseret ved brug af algoritmer med konstant tid og udfyldning for at forhindre timing-baserede modeludtrækningsangreb.    |   3    |  D/V  |
| 4.18.2 | Bekræft, at beskyttelse mod strøm-analyse inkluderer støjindsprøjtning, filtrering af strømforsyningslinjer og tilfældige udførelsesmønstre for AI-hardware.     |   3    |  D/V  |
| 4.18.3 | Bekræft, at cache-baseret side-channel afbødning bruger cache-partitionering, randomisering og flush-instruktioner for at forhindre informationslækage.          |   3    |  D/V  |
| 4.18.4 | Bekræft, at beskyttelse mod elektromagnetisk udsendelse omfatter afskærmning, signalfiltrering og tilfældig behandling for at forhindre TEMPEST-lignende angreb. |   3    |  D/V  |
| 4.18.5 | Bekræft, at mikroarkitekturens sidekanal-foranstaltninger inkluderer kontrol med spekulativ udførelse og obfuskering af hukommelsesadgangsmønstre.               |   3    |  D/V  |

---

## C4.19 Neuromorfisk & Specialiseret AI Hardware Sikkerhed

Sikre fremadstormende AI-hardwarearkitekturer, herunder neuromorfe chips, FPGA'er, tilpassede ASIC'er og optiske computersystemer.

|   #    | Beskrivelse                                                                                                                                                                      | Niveau | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.19.1 | Bekræft, at neuromorfe chip-sikkerhed inkluderer kryptering af spike-mønstre, beskyttelse af synaptiske vægte og hardwarebaseret validering af læringsregler.                    |   3    |  D/V  |
| 4.19.2 | Bekræft, at FPGA-baserede AI-acceleratorer implementerer bitstream-kryptering, anti-manipulationsmekanismer og sikker konfigurationsindlæsning med autentificerede opdateringer. |   3    |  D/V  |
| 4.19.3 | Bekræft, at brugerdefineret ASIC-sikkerhed inkluderer indbyggede sikkerhedsprocessorer, hardware root of trust og sikker nøglelagring med manipulationsdetektion.                |   3    |  D/V  |
| 4.19.4 | Bekræft, at optiske computersystemer implementerer kvantesikret optisk kryptering, sikker fotonisk switching og beskyttet optisk signalbehandling.                               |   3    |  D/V  |
| 4.19.5 | Bekræft, at hybride analoge-digitale AI-chips inkluderer sikker analog beregning, beskyttet vægtlagring og autentificeret analog-til-digital konvertering.                       |   3    |  D/V  |

---

## C4.20 Privatlivsbevarende beregningsinfrastruktur

Implementer infrastrukturelle kontroller for privatlivsbeskyttende beregning for at beskytte følsomme data under AI-behandling og analyse.

|   #    | Beskrivelse                                                                                                                                                                               | Niveau | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.20.1 | Bekræft, at homomorf krypteringsinfrastruktur muliggør krypteret beregning på følsomme AI-arbejdsbelastninger med kryptografisk integritetsverifikation og ydeevneovervågning.            |   3    |  D/V  |
| 4.20.2 | Bekræft, at private information retrieval-systemer muliggør databaseforespørgsler uden at afsløre forespørgsmønstre med kryptografisk beskyttelse af adgangsmønstre.                      |   3    |  D/V  |
| 4.20.3 | Bekræft, at sikre multi-parti beregningsprotokoller muliggør privatlivsbevarende AI-inferens uden at afsløre individuelle input eller mellemliggende beregninger.                         |   3    |  D/V  |
| 4.20.4 | Bekræft, at privatlivsbevarende nøglehåndtering omfatter distribueret nøglegenerering, tærskelkryptografi og sikker nøglerotation med hardware-understøttet beskyttelse.                  |   3    |  D/V  |
| 4.20.5 | Bekræft, at ydeevnen for privatlivsbeskyttende beregninger er optimeret gennem batching, caching og hardwareacceleration, samtidig med at kryptografiske sikkerhedsgarantier opretholdes. |   3    |  D/V  |

---

## C4.15 Agent Framework Cloud Integration Sikkerhed & Hybrid Implementering

Sikkerhedskontroller for sky-integrerede agentrammer med hybride lokale/sky-arkitekturer.

|   #    | Beskrivelse                                                                                                             | Niveau | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.15.1 | Bekræft, at cloud-lagringsintegration bruger ende-til-ende-kryptering med agentstyret nøglehåndtering.                  |   1    |  D/V  |
| 4.15.2 | Bekræft, at sikkerhedsgrænserne for hybridimplementering er klart definerede med krypterede kommunikationskanaler.      |   2    |  D/V  |
| 4.15.3 | Bekræft, at adgang til cloud-ressourcer inkluderer zero-trust-verifikation med kontinuerlig autentificering.            |   2    |  D/V  |
| 4.15.4 | Bekræft, at krav til datalagring overholdes ved kryptografisk attestering af lagringssteder.                            |   3    |  D/V  |
| 4.15.5 | Bekræft, at sikkerhedsvurderinger fra cloud-udbyderen inkluderer agent-specifik trusselsmodellering og risikovurdering. |   3    |  D/V  |

---

## Referencer

* [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework)
* [CIS Controls v8](https://www.cisecurity.org/controls/v8)
* [OWASP Container Security Verification Standard](https://github.com/OWASP/Container-Security-Verification-Standard)
* [Kubernetes Security Best Practices](https://kubernetes.io/docs/concepts/security/)
* [SLSA Supply Chain Security Framework](https://slsa.dev/)
* [NIST SP 800-190: Application Container Security Guide](https://csrc.nist.gov/publications/detail/sp/800-190/final)
* [Cloud Security Alliance: Cloud Controls Matrix](https://cloudsecurityalliance.org/research/cloud-controls-matrix/)
* [ENISA: Secure Infrastructure Design](https://www.enisa.europa.eu/topics/critical-information-infrastructures-and-services)
* [NIST SP 800-53: Security Controls for Federal Information Systems](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final)
* [ISO 27001:2022 Information Security Management](https://www.iso.org/standard/27001)
* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [CIS Kubernetes Benchmark](https://www.cisecurity.org/benchmark/kubernetes)
* [FIPS 140-2 Security Requirements](https://csrc.nist.gov/publications/detail/fips/140/2/final)
* [NIST SP 800-207: Zero Trust Architecture](https://csrc.nist.gov/publications/detail/sp/800-207/final)
* [IEEE 2857: Privacy Engineering for AI Systems](https://standards.ieee.org/ieee/2857/7273/)
* [NIST SP 800-161: Cybersecurity Supply Chain Risk Management](https://csrc.nist.gov/publications/detail/sp/800-161/rev-1/final)
* [NIST Post-Quantum Cryptography Standards](https://csrc.nist.gov/Projects/post-quantum-cryptography)
* [Intel SGX Developer Guide](https://www.intel.com/content/www/us/en/developer/tools/software-guard-extensions/overview.html)
* [AMD SEV-SNP White Paper](https://www.amd.com/system/files/TechDocs/SEV-SNP-strengthening-vm-isolation-with-integrity-protection-and-more.pdf)
* [ARM TrustZone Technology](https://developer.arm.com/ip-products/security-ip/trustzone)
* [ZK-SNARKs: A Gentle Introduction](https://blog.ethereum.org/2016/12/05/zksnarks-in-a-nutshell/)
* [NIST SP 800-57: Cryptographic Key Management](https://csrc.nist.gov/publications/detail/sp/800-57-part-1/rev-5/final)
* [Side-Channel Attack Countermeasures](https://link.springer.com/book/10.1007/978-3-319-75268-6)
* [Neuromorphic Computing Security Challenges](https://ieeexplore.ieee.org/document/9458103)
* [FPGA Security: Fundamentals, Evaluation, and Countermeasures](https://link.springer.com/book/10.1007/978-3-319-90385-9)
* [Microsoft SEAL: Homomorphic Encryption Library](https://github.com/Microsoft/SEAL)
* [HElib: Homomorphic Encryption Library](https://github.com/homenc/HElib)
* [PALISADE Lattice Cryptography Library](https://palisade-crypto.org/)
* [Differential Privacy: A Survey of Results](https://link.springer.com/chapter/10.1007/978-3-540-79228-4_1)
* [Secure Aggregation for Federated Learning](https://eprint.iacr.org/2017/281.pdf)
* [Private Information Retrieval: Concepts and Constructions](https://link.springer.com/book/10.1007/978-3-030-16234-8)

