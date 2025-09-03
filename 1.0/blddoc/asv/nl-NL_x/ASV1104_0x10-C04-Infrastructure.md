# C4 Infrastructuur, Configuratie & Implementatiebeveiliging

## Beheersdoel

AI-infrastructuur moet bestand zijn tegen privilege-escalatie, manipulatie van de toeleveringsketen en laterale beweging via veilige configuratie, runtime-isolatie, vertrouwde deployment-pijplijnen en uitgebreide monitoring. Alleen geautoriseerde, gevalideerde infrastructuurcomponenten en configuraties bereiken productie via gecontroleerde processen die veiligheid, integriteit en auditabiliteit waarborgen.

Kernbeveiligingsdoel: Alleen cryptografisch ondertekende, op kwetsbaarheden gescande infrastructuurcomponenten bereiken productie via geautomatiseerde validatiepijplijnen die beveiligingsbeleid afdwingen en onveranderlijke auditsporen handhaven.

---

## C4.1 Runtime-omgeving isolatie

Voorkom containeruitbraken en privilege-escalatie door isolatieprimitieven op kernel-niveau en verplichte toegangscontroles.

|   #   | Beschrijving                                                                                                                                                                                                                                          | Niveau | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.1.1 | Verifieer dat alle AI-containers ALLE Linux-capabilities verwijderen behalve CAP_SETUID, CAP_SETGID en de expliciet vereiste Linux-capabilities die in de beveiligingsbasislijnen zijn gedocumenteerd.                                                |   1    | D/V |
| 4.1.2 | Controleer of seccomp-profielen alle systeemoproepen blokkeren, behalve die in vooraf goedgekeurde toegestane lijsten, waarbij overtredingen de container beëindigen en beveiligingswaarschuwingen genereren.                                         |   1    | D/V |
| 4.1.3 | Controleer dat AI-workloads draaien met root-bestandssystemen die alleen-lezen zijn, tmpfs voor tijdelijke gegevens, en genaamde volumes voor persistente gegevens, waarbij noexec-mountopties afgedwongen worden.                                    |   2    | D/V |
| 4.1.4 | Verifieer of eBPF-gebaseerde runtimebewaking (Falco, Tetragon, of een gelijkwaardig alternatief) detecteert pogingen tot privilege-escalatie en beëindigt automatisch de overtredende processen binnen de door de organisatie gestelde responstijden. |   2    | D/V |
| 4.1.5 | Controleer of AI-werkbelastingen met een hoog risico worden uitgevoerd in hardware-geïsoleerde omgevingen (Intel TXT, AMD SVM, of toegewijde bare-metal knooppunten) met attestatieverificatie.                                                       |   3    | D/V |

---

## C4.2 Veilige Build- en Deployment-pijplijnen

Zorg voor cryptografische integriteit en beveiliging van de toeleveringsketen door middel van herhaalbare builds en ondertekende artefacten.

|   #   | Beschrijving                                                                                                                                                                                                                               | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 4.2.1 | Verifieer dat infrastructuur-als-code bij elke commit wordt gescand met tools (tfsec, Checkov of Terrascan) en merges blokkeert bij bevindingen met CRITICAL of HIGH-ernst.                                                                |   1    | D/V |
| 4.2.2 | Controleer dat container-builds reproduceerbaar zijn met identieke SHA256-hashes over meerdere builds heen en genereer provenance-attestaties van SLSA-niveau 3 die met Sigstore zijn ondertekend.                                         |   1    | D/V |
| 4.2.3 | Verifieer dat containerafbeeldingen CycloneDX- of SPDX-SBOMs bevatten en door Cosign ondertekend zijn vóór het pushen naar de registry, en dat niet-ondertekende afbeeldingen bij de implementatie worden geweigerd.                       |   2    | D/V |
| 4.2.4 | Verifieer dat CI/CD-pijplijnen OIDC-tokens gebruiken afkomstig van HashiCorp Vault, AWS IAM-rollen of Azure-beheerde identiteit, met een geldigheidsduur die niet langer is dan de limieten van het beveiligingsbeleid van de organisatie. |   2    | D/V |
| 4.2.5 | Verifieer dat Cosign-handtekeningen en SLSA-provenance tijdens het uitrolproces worden gevalideerd voordat de container wordt uitgevoerd, en dat verificatiefouten ervoor zorgen dat de uitrol mislukt.                                    |   2    | D/V |
| 4.2.6 | Controleer of buildomgevingen draaien in tijdelijke containers of VM's zonder persistente opslag en netwerkisolatie ten opzichte van productie-VPC's.                                                                                      |   2    | D/V |

---

## C4.3 Netwerkbeveiliging & Toegangscontrole

Implementeer Zero-Trust-netwerken met standaard-weigeringsbeleid en versleutelde communicatie.

|   #   | Beschrijving                                                                                                                                                                                                           | Niveau | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.3.1 | Controleer of Kubernetes NetworkPolicies of een gelijkwaardig systeem een default-deny-beleid voor inkomend en uitgaand verkeer implementeert, met expliciete toegangsregels voor vereiste poorten (443, 8080, enz.).  |   1    | D/V |
| 4.3.2 | Controleer of SSH (poort 22), RDP (poort 3389) en cloud metadata-eindpunten (169.254.169.254) zijn geblokkeerd of certificaatgebaseerde authenticatie vereisen.                                                        |   1    | D/V |
| 4.3.3 | Controleer dat uitgaand verkeer via HTTP/HTTPS-proxies (Squid, Istio of cloud NAT-gateways) wordt gefilterd met domeintoegestane lijsten en dat geblokkeerde verzoeken worden gelogd.                                  |   2    | D/V |
| 4.3.4 | Verifieer dat de communicatie tussen services mutual TLS (mTLS) gebruikt, met certificaten die volgens het organisatiebeleid zijn vernieuwd, en dat certificaatvalidatie wordt afgedwongen (geen skip-verify-vlaggen). |   2    | D/V |
| 4.3.5 | Controleer of AI-infrastructuur draait in toegewijde VPCs/VNets zonder directe internettoegang en communiceert uitsluitend via NAT-gateways of bastion hosts.                                                          |   2    | D/V |

---

## C4.4 Geheimen & cryptografisch sleutelbeheer

Bescherm referenties via hardware-backed opslag en automatische rotatie met zero-trust-toegang.

|   #   | Beschrijving                                                                                                                                                                                                 | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 4.4.1 | Controleer of geheimen zijn opgeslagen in HashiCorp Vault, AWS Secrets Manager, Azure Key Vault of Google Secret Manager met AES-256-versleuteling in rust.                                                  |   1    | D/V |
| 4.4.2 | Controleer of cryptografische sleutels worden gegenereerd in FIPS 140-2 Niveau 2 HSM's (AWS CloudHSM, Azure Dedicated HSM) met sleutelrotatie volgens het cryptografisch beleid van de organisatie.          |   1    | D/V |
| 4.4.3 | Verifieer dat de rotatie van geheimen geautomatiseerd is met een implementatie zonder downtime en een onmiddellijke rotatie die wordt geactiveerd door personeelswijzigingen of beveiligingsincidenten.      |   2    | D/V |
| 4.4.4 | Verifieer dat containerafbeeldingen worden gescand met tools (GitLeaks, TruffleHog of detect-secrets) die builds blokkeren waarin API-sleutels, wachtwoorden of certificaten voorkomen.                      |   2    | D/V |
| 4.4.5 | Controleer of de toegang tot productiegeheimen MFA vereist met hardwaretokens (YubiKey, FIDO2) en of dit wordt vastgelegd in onveranderlijke auditlogboeken met gebruikersidentiteiten en tijdstempels.      |   2    | D/V |
| 4.4.6 | Controleer of geheimen via Kubernetes-geheimen, gemonteerde volumes of init-containers worden geïnjecteerd en zorg ervoor dat geheimen nooit worden ingebed in omgevingsvariabelen of containerafbeeldingen. |   2    | D/V |

---

## C4.5 AI-werkbelasting sandboxing en validatie

Isoleer onbetrouwbare AI-modellen in veilige sandboxen met een uitgebreide gedragsanalyse.

|   #   | Beschrijving                                                                                                                                                                                                              | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.5.1 | Verifieer dat externe AI-modellen worden uitgevoerd in gVisor, microVM's (zoals Firecracker, CrossVM) of Docker-containers met de opties --security-opt=no-new-privileges en --read-only.                                 |   1    | D/V |
| 4.5.2 | Controleer of sandboxomgevingen geen netwerkconnectiviteit hebben (--network=none) of alleen toegang hebben tot localhost, waarbij alle externe verzoeken door iptables-regels worden geblokkeerd.                        |   1    | D/V |
| 4.5.3 | Verifieer dat AI-modelvalidatie geautomatiseerde red-teamtesten omvat met organisatorisch gedefinieerde testdekking en gedragsanalyse voor backdoor-detectie.                                                             |   2    | D/V |
| 4.5.4 | Verifieer dat voordat een AI-model naar productie wordt gepromoveerd, de sandboxresultaten cryptografisch ondertekend zijn door geautoriseerd beveiligingspersoneel en in onveranderlijke auditlogboeken zijn opgeslagen. |   2    | D/V |
| 4.5.5 | Verifieer dat sandbox-omgevingen tussen evaluaties worden vernietigd en opnieuw aangemaakt uit gouden afbeeldingen met volledige bestandssysteem- en geheugenopruiming.                                                   |   2    | D/V |

---

## C4.6 Infrastructuurbeveiligingsbewaking

Infrastructuur continu scannen en monitoren met geautomatiseerde herstelmaatregelen en real-time waarschuwingen.

|   #   | Beschrijving                                                                                                                                                                                                         | Niveau | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.6.1 | Verifieer dat containerafbeeldingen volgens de planning van de organisatie worden gescand, waarbij kritieke kwetsbaarheden de implementatie blokkeren op basis van de risicogrens van de organisatie.                |   1    | D/V |
| 4.6.2 | Verifieer of de infrastructuur voldoet aan CIS Benchmarks of NIST 800-53-beheersmaatregelen met door de organisatie gedefinieerde nalevingsdrempels en geautomatiseerde remediatie voor mislukte controles.          |   1    | D/V |
| 4.6.3 | Controleer dat kwetsbaarheden met een hoge ernst volgens de tijdlijnen van het organisatorische risicobeheer zijn gepatcht, met noodprocedures voor CVEs die actief worden uitgebuit.                                |   2    | D/V |
| 4.6.4 | Controleer of beveiligingswaarschuwingen kunnen integreren met SIEM-platforms (Splunk, Elastic of Sentinel) via CEF- of STIX/TAXII-formaten met geautomatiseerde verrijking.                                         |   2    |  V  |
| 4.6.5 | Controleer of infrastructuurmetingen worden geëxporteerd naar monitoringsystemen (Prometheus, DataDog) met SLA-dashboards en managementrapportage.                                                                   |   3    |  V  |
| 4.6.6 | Verifieer dat configuratiedrift wordt gedetecteerd met behulp van hulpmiddelen (Chef InSpec, AWS Config) volgens de organisatorische bewakingsvereisten met automatische rollback voor ongeautoriseerde wijzigingen. |   2    | D/V |

---

## C4.7 AI-infrastructuurbronnenbeheer

Voorkom uitputtingsaanvallen op bronnen en zorg voor een eerlijke toewijzing van middelen via quota en bewaking.

|   #   | Beschrijving                                                                                                                                                                                                                                                           | Niveau | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.7.1 | Verifieer dat de GPU/TPU-utilisatie wordt gemonitord met waarschuwingen die bij door de organisatie vastgestelde drempels worden geactiveerd, en dat automatische schaalvergroting of belastingverdeling wordt geactiveerd op basis van beleid voor capaciteitsbeheer. |   1    | D/V |
| 4.7.2 | Verifieer dat AI-werkbelastingsmetriek(en) volgens de monitoringvereisten van de organisatie worden verzameld en gecorreleerd met de infrastructuurbenutting.                                                                                                          |   1    | D/V |
| 4.7.3 | Controleer of Kubernetes ResourceQuotas of gelijkwaardige mechanismen de individuele workloads beperken volgens het organisatorische beleid voor resource-allocatie, met afdwingbare harde limieten.                                                                   |   2    | D/V |
| 4.7.4 | Controleer of kostenmonitoring de uitgaven per workload/tenant bijhoudt met waarschuwingen op basis van organisatorische budgetdrempels en geautomatiseerde controles voor begrotingsoverschrijdingen.                                                                 |   2    |  V  |
| 4.7.5 | Controleer of capaciteitsplanning historische gegevens gebruikt met door de organisatie gedefinieerde prognoseperiodes en automatische toewijzing van bronnen die gebaseerd is op vraagpatronen.                                                                       |   3    |  V  |
| 4.7.6 | Controleer of bronnenuitputting circuit breakers activeert volgens de organisatorische responsvereisten, inclusief rate-limiting op basis van capaciteitsbeleid en werklastisolatie.                                                                                   |   2    | D/V |

---

## C4.8 Omgevingscheiding en Promotiecontroles

Handhaaf strikte omgevingsgrenzen met geautomatiseerde promotiepoorten en beveiligingsvalidatie.

|   #   | Beschrijving                                                                                                                                                                                                           | Niveau | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.8.1 | Verifieer dat de dev/test/prod-omgevingen in afzonderlijke VPCs/VNets draaien zonder gedeelde IAM-rollen, beveiligingsgroepen of netwerkconnectiviteit.                                                                |   1    | D/V |
| 4.8.2 | Verifieer dat de omgevingspromotie goedkeuring vereist van organisatorisch gedefinieerde bevoegde personen met cryptografische handtekeningen en onveranderlijke auditsporen.                                          |   1    | D/V |
| 4.8.3 | Controleer of productieomgevingen SSH-toegang blokkeren, debug-eindpunten uitschakelen en wijzigingsverzoeken vereisen met organisatorische vereisten voor voorafgaande kennisgeving, behalve in noodgevallen.         |   2    | D/V |
| 4.8.4 | Verifieer dat wijzigingen in infrastructuur-als-code een collegiale beoordeling vereisen met geautomatiseerde tests en beveiligingsscans voordat ze worden samengevoegd in de hoofdbranch.                             |   2    | D/V |
| 4.8.5 | Verifieer dat niet-productiegegevens zijn geanonimiseerd volgens de privacy-eisen van de organisatie, synthetische gegevensgeneratie, of volledige gegevensmaskering met PII-verwijdering, en dat dit is geverifieerd. |   2    | D/V |
| 4.8.6 | Controleer dat promotiepoorten geautomatiseerde beveiligingstests bevatten (SAST, DAST, container scanning) waarbij voor goedkeuring geen kritieke bevindingen vereist zijn.                                           |   2    | D/V |

---

## C4.9 Infrastructuur Back-up & Herstel

Zorg voor de veerkracht van de infrastructuur door middel van geautomatiseerde back-ups, geteste herstelprocedures en rampenherstelcapaciteiten.

|   #   | Beschrijving                                                                                                                                                                                                                 | Niveau | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.9.1 | Verifieer of infrastructuurconfiguraties volgens de organisatorische back-upschema's worden geback-upt naar geografisch gescheiden regio's met de 3-2-1-back-upstrategie-implementatie.                                      |   1    | D/V |
| 4.9.2 | Controleer of backup-systemen draaien in geïsoleerde netwerken met aparte inloggegevens en air-gapped opslag voor ransomwarebescherming.                                                                                     |   2    | D/V |
| 4.9.3 | Verifieer dat herstelprocedures worden getest en gevalideerd door middel van geautomatiseerd testen volgens de planningen van de organisatie met RTO- en RPO-doelstellingen die voldoen aan de vereisten van de organisatie. |   2    |  V  |
| 4.9.4 | Controleer of rampenherstel AI-specifieke runbooks omvat met herstel van modelgewichten, het opnieuw opbouwen van GPU-clusters en het in kaart brengen van dienstafhankelijkheden.                                           |   3    |  V  |

---

## C4.10 Infrastructuur Naleving & Bestuur

Zorg voor naleving van regelgeving door voortdurende beoordeling, documentatie en geautomatiseerde controles.

|   #    | Beschrijving                                                                                                                                                                                            | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.10.1 | Verifieer dat de naleving van de infrastructuur volgens de organisatorische schema's wordt beoordeeld tegen SOC 2, ISO 27001 of FedRAMP-controles met geautomatiseerde verzameling van bewijsmateriaal. |   2    | D/V |
| 4.10.2 | Verifieer of de infrastructuurdocumentatie netwerkdiagrammen, gegevensstroomkaarten en dreigingsmodellen bevat die zijn bijgewerkt volgens de vereisten van organisatorisch verandermanagement.         |   2    |  V  |
| 4.10.3 | Verifieer dat infrastructuurwijzigingen een geautomatiseerde nalevingsimpactbeoordeling ondergaan met regulatoire goedkeuringsworkflows voor wijzigingen met hoog risico.                               |   3    | D/V |

---

## C4.11 AI-hardwarebeveiliging

Beveilig AI-specifieke hardwarecomponenten, waaronder GPU's, TPU's en gespecialiseerde AI-acceleratoren.

|   #    | Beschrijving                                                                                                                                                                                     | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 4.11.1 | Controleer of AI-accelerator-firmware (GPU BIOS, TPU-firmware) geverifieerd is met cryptografische handtekeningen en bijgewerkt volgens de patchbeheer-tijdlijnen van de organisatie.            |   2    | D/V |
| 4.11.2 | Verifieer dat vóór de uitvoering van de werkbelasting de integriteit van de AI-accelerator wordt gevalideerd door hardware-attestatie met TPM 2.0, Intel TXT of AMD SVM.                         |   2    | D/V |
| 4.11.3 | Verifieer dat het GPU-geheugen geïsoleerd is tussen werkbelastingen met behulp van SR-IOV, MIG (Multi-Instance GPU) of vergelijkbare hardware-partitionering met geheugenreiniging tussen taken. |   2    | D/V |
| 4.11.4 | Verifieer dat de AI-hardware-toeleveringsketen herkomstverificatie omvat, met fabrikantcertificaten en tamper-evidente verpakkingsvalidatie.                                                     |   3    |  V  |
| 4.11.5 | Controleer dat hardwarebeveiligingsmodules (HSMs) AI-modelgewichten en cryptografische sleutels beschermen met certificering volgens FIPS 140-2 Niveau 3 of Common Criteria EAL4+.               |   3    | D/V |

---

## C4.12 Edge- en gedistribueerde AI-infrastructuur

Veilige gedistribueerde AI-implementaties, inclusief edge computing, federated learning en architecturen op meerdere locaties.

|   #    | Beschrijving                                                                                                                                                                                                                        | Niveau | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.12.1 | Verifieer dat edge-AI-apparaten zich authenticeren bij de centrale infrastructuur via wederzijdse TLS (mTLS), met apparaatcertificaten die volgens het beleid voor certificaatbeheer van de organisatie periodiek worden vernieuwd. |   2    | D/V |
| 4.12.2 | Verifieer dat edge-apparaten Secure Boot implementeren met geverifieerde handtekeningen en rollbackbescherming die firmware-downgrade-aanvallen voorkomt.                                                                           |   2    | D/V |
| 4.12.3 | Controleer of de gedistribueerde AI-coördinatie byzantijns fouttolerante consensusalgoritmen gebruikt met deelnemersvalidatie en detectie van kwaadaardige knooppunten.                                                             |   3    | D/V |
| 4.12.4 | Controleer of edge-to-cloud-communicatie bandbreedtebeperking, gegevenscompressie en offline operationele mogelijkheden met beveiligde lokale opslag omvat.                                                                         |   3    | D/V |

---

## C4.13 Meerdere Cloud-omgevingen en Hybride Infrastructuurbeveiliging

Beveilig AI-workloads over meerdere cloudproviders en hybride cloud-on-premises-implementaties.

|   #    | Beschrijving                                                                                                                                                                                                                     | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.13.1 | Controleer of multi-cloud AI-implementaties cloud-agnostische identiteitsfederatie (OIDC, SAML) gebruiken met gecentraliseerd beleidsbeheer over aanbieders.                                                                     |   2    | D/V |
| 4.13.2 | Verifieer dat cross-cloud gegevensoverdracht end-to-end encryptie gebruikt met door de klant beheerde sleutels en controles voor gegevensresidentie die per rechtsgebied worden afgedwongen.                                     |   2    | D/V |
| 4.13.3 | Controleer of hybride cloud AI workloads een consistent beveiligingsbeleid implementeren over on-premise en cloudomgevingen met geïntegreerde bewaking en waarschuwingen.                                                        |   2    | D/V |
| 4.13.4 | Controleer of de voorkoming van leveranciersafhankelijkheid voor cloudomgevingen portabele infrastructuur-als-code, gestandaardiseerde API's en mogelijkheden voor gegevensexport omvat, samen met formaatconversiehulpmiddelen. |   3    |  V  |
| 4.13.5 | Controleer of multi-cloud kostenoptimalisatie beveiligingscontroles omvat die zowel resource-sprawl voorkomen als onbevoegde cross-cloud gegevensoverdrachtskosten voorkomen.                                                    |   3    |  V  |

---

## C4.14 Infrastructuurautomatisering en GitOps-beveiliging

Beveilig infrastructuurautomatiseringspijplijnen en GitOps-workflows voor AI-infrastructuurbeheer.

|   #    | Beschrijving                                                                                                                                                                                                                      | Niveau | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.14.1 | Controleer of GitOps-repositories ondertekende commits met GPG-sleutels vereisen en branchbeschermingsregels die directe pushes naar hoofdbranches voorkomen.                                                                     |   2    | D/V |
| 4.14.2 | Controleer of infrastructuurautomatisering driftdetectie omvat met automatische herstelmaatregelen en rollback-mogelijkheden die worden geactiveerd volgens de vereisten voor organisatorische respons op onbevoegde wijzigingen. |   2    | D/V |
| 4.14.3 | Controleer of de geautomatiseerde provisioning van infrastructuur een validering van beveiligingsbeleid omvat, met blokkering van implementaties voor niet-conforme configuraties.                                                |   2    | D/V |
| 4.14.4 | Controleer of de geheimen voor infrastructuurautomatisering via externe Secret-Operators (External Secrets Operator, Bank-Vaults) met automatische rotatie worden beheerd.                                                        |   2    | D/V |
| 4.14.5 | Verifieer dat zelfherstellende infrastructuur correlatie van beveiligingsgebeurtenissen bevat, met geautomatiseerde incidentrespons en workflows voor notificatie aan belanghebbenden.                                            |   3    |  V  |

---

## C4.15 Kwantumresistente infrastructuurbeveiliging

Bereid AI-infrastructuur voor op bedreigingen door kwantumcomputers met post-quantum cryptografie en kwantumbeveiligde protocollen.

|   #    | Beschrijving                                                                                                                                                                                                   | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.15.1 | Controleer of de AI-infrastructuur NIST-goedgekeurde post-quantum cryptografische algoritmen (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) implementeert voor sleuteluitwisseling en digitale handtekeningen. |   3    | D/V |
| 4.15.2 | Controleer of kwantumsleutelverdeling (QKD) systemen zijn geïmplementeerd voor hoogbeveiligde AI-communicatie met kwantumveilige sleutelbeheerprotocollen.                                                     |   3    | D/V |
| 4.15.3 | Controleer of cryptografische wendbaarheidskaders een snelle migratie naar nieuwe post-kwantumalgoritmen mogelijk maken met geautomatiseerde certificaat- en sleutelrotatie.                                   |   3    | D/V |
| 4.15.4 | Controleer of kwantumdreigingsmodellering de kwetsbaarheid van AI-infrastructuur voor kwantumaanvallen beoordeelt, met gedocumenteerde migratietijdlijnen en risicobeoordelingen.                              |   3    |  V  |
| 4.15.5 | Verifieer dat hybride klassieke-quantum cryptografische systemen meerlaagse beveiliging bieden tijdens de quantumovergangsperiode met prestatiebewaking.                                                       |   3    | D/V |

---

## C4.16 Vertrouwelijke Computing & Veilige Enclaves

Bescherm AI-werkbelastingen en modelgewichten met hardwaregebaseerde vertrouwde uitvoeringsomgevingen en vertrouwelijke rekentechnologieën.

|   #    | Beschrijving                                                                                                                                                                                | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.16.1 | Controleer of gevoelige AI-modellen binnen Intel SGX-enclaves, AMD SEV-SNP of ARM TrustZone worden uitgevoerd met versleuteld geheugen en attestatieverificatie.                            |   3    | D/V |
| 4.16.2 | Controleer of vertrouwelijke containers (Kata Containers, gVisor with confidential computing) AI-workloads isoleren met hardware-enforced memory encryption.                                |   3    | D/V |
| 4.16.3 | Zorg ervoor dat de afstandsattestatie de enclave-integriteit valideert voordat AI-modellen worden geladen met cryptografisch bewijs van de authenticiteit van een uitvoeringsomgeving.      |   3    | D/V |
| 4.16.4 | Controleer of vertrouwelijke AI-inferentieservices modelextractie voorkomen door middel van versleutelde berekening met verzegelde modelgewichten en beveiligde uitvoering.                 |   3    | D/V |
| 4.16.5 | Verifieer dat de orkestratie van een vertrouwde uitvoeringsomgeving (TEE) de levenscyclus van een beveiligde enclave beheert met attestatie op afstand en versleutelde communicatiekanalen. |   3    | D/V |
| 4.16.6 | Verifieer dat veilige multi-party computation (SMPC) samenwerking bij AI-training mogelijk maakt zonder individuele datasets of modelparameters bloot te geven.                             |   3    | D/V |

---

## C4.17 Zero-kennis-infrastructuur

Implementeer nulkennisbewijssystemen voor privacybeschermende AI-verificatie en authenticatie zonder gevoelige informatie prijs te geven.

|   #    | Beschrijving                                                                                                                                                                                                       | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 4.17.1 | Controleer of bewijzen met nulkennis (ZK-SNARKs, ZK-STARKs) de integriteit van het AI-model en de herkomst van de trainingsdata verifiëren zonder de gewichten van het model of trainingsgegevens bloot te leggen. |   3    | D/V |
| 4.17.2 | Controleer of ZK-gebaseerde authenticatiesystemen privacybeschermende gebruikersverificatie voor AI-diensten mogelijk maken zonder identiteitsgerelateerde informatie bekend te maken.                             |   3    | D/V |
| 4.17.3 | Verifieer dat private set intersection (PSI) protocollen veilige gegevensvergelijking mogelijk maken voor federated AI zonder individuele datasets bloot te geven.                                                 |   3    | D/V |
| 4.17.4 | Controleer of nulkennis machine learning (ZKML) systemen verifieerbare AI-inferenties mogelijk maken met cryptografisch bewijs van correcte uitvoering.                                                            |   3    | D/V |
| 4.17.5 | Verifieer of ZK-rollups schaalbare, privacy-beschermende AI-transactieverwerking bieden met batchverificatie en verminderde rekenlast.                                                                             |   3    | D/V |

---

## C4.18 Bescherming tegen side-channel-aanvallen

Bescherm AI-infrastructuur tegen timing-aanvallen, stroomanalyse-aanvallen, elektromagnetische side-channel-aanvallen en cache-gebaseerde side-channel-aanvallen die mogelijk gevoelige informatie kunnen lekken.

|   #    | Beschrijving                                                                                                                                                              | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.18.1 | Verifieer dat de AI-inferentietijd genormaliseerd is door middel van algoritmen met constante tijd en padding om tijdsafhankelijke modelextractie-aanvallen te voorkomen. |   3    | D/V |
| 4.18.2 | Controleer of bescherming tegen stroomanalyse ruisinjectie, filtratie van voedingslijnen en gerandomiseerde uitvoeringspatronen voor AI-hardware omvat.                   |   3    | D/V |
| 4.18.3 | Controleer of de cache-gebaseerde mitigatie van zijkanalen gebruikmaakt van cache-partitionering, randomisatie en flush-instructies om informatielekken te voorkomen.     |   3    | D/V |
| 4.18.4 | Controleer of elektromagnetische emanatiebescherming afscherming, signaalfilters en gerandomiseerde verwerking omvat om TEMPEST-achtige aanvallen te voorkomen.           |   3    | D/V |
| 4.18.5 | Controleer of microarchitecturale zijkanalverdedigingen onder andere controles op speculatieve uitvoering en obfuscatie van geheugentoegangspatronen bevatten.            |   3    | D/V |

---

## C4.19 Neuromorfische & Gespecialiseerde AI-hardwarebeveiliging

Beveilig opkomende AI-hardwarearchitecturen, waaronder neuromorfe chips, FPGAs, op maat gemaakte ASICs en optische rekensystemen.

|   #    | Beschrijving                                                                                                                                                                              | Niveau | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.19.1 | Controleer of de beveiliging van neuromorfische chips versleuteling van spikepatronen, bescherming van synaptische gewichten en hardware-gebaseerde validatie van leerregels omvat.       |   3    | D/V |
| 4.19.2 | Verifieer dat FPGA-gebaseerde AI-accelerators bitstream-encryptie, anti-tamper-mechanismen en veilige configuratie-inladen met geauthenticeerde updates implementeren.                    |   3    | D/V |
| 4.19.3 | Verifieer dat maatwerk-ASIC-beveiliging on-chip beveiligingsprocessoren, hardware-root of trust en veilige sleutelopslag met tamperdetectie omvat.                                        |   3    | D/V |
| 4.19.4 | Controleer of optische computersystemen kwantumveilige optische encryptie, veilige fotonische schakeling en beschermde optische signaalverwerking implementeren.                          |   3    | D/V |
| 4.19.5 | Controleer of hybride analoog-digitaal AI-chips veilige analoge berekeningen bevatten, beschermde gewichtsopslag hebben en geauthenticeerde analoog-naar-digitaal-conversie ondersteunen. |   3    | D/V |

---

## C4.20 Privacy-Beschermende Rekeninfrastructuur

Implementeer infrastructuurcontroles voor privacybeschermende berekeningen om gevoelige gegevens te beschermen tijdens AI-verwerking en analyse.

|   #    | Beschrijving                                                                                                                                                                                                   | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.20.1 | Controleer of infrastructuur voor homomorfische encryptie versleutelde berekeningen op gevoelige AI-werkbelastingen mogelijk maakt met cryptografische integriteitsverificatie en prestatemonitoring.          |   3    | D/V |
| 4.20.2 | Verifieer dat privé-informatieopvragsystemen databasequery's mogelijk maken zonder querypatronen prijs te geven, met cryptografische bescherming van toegangspatronen.                                         |   3    | D/V |
| 4.20.3 | Verifieer dat veilige MPC-protocollen privacybeschermende AI-inferentie mogelijk maken zonder de individuele invoer of tussenliggende berekeningen bloot te leggen.                                            |   3    | D/V |
| 4.20.4 | Verifieer dat privacybeschermend sleutelbeheer gedistribueerde sleutelgeneratie, drempelcryptografie en veilige sleutelrotatie met hardware-ondersteunde bescherming omvat.                                    |   3    | D/V |
| 4.20.5 | Controleer of de prestaties van privacybeschermende berekeningen zijn geoptimaliseerd door batchverwerking, caching en hardwareversnelling, terwijl de cryptografische beveiligingsgaranties behouden blijven. |   3    | D/V |

---

## C4.15 Agent Framework Cloud Integratie Beveiliging & Hybride Implementatie

Beveiligingscontroles voor cloud-geïntegreerde agentframeworks met hybride on-premises/cloud-architecturen.

|   #    | Beschrijving                                                                                                                         | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 4.15.1 | Verifieer of de cloudopslagintegratie gebruikmaakt van end-to-end encryptie met agentgestuurd sleutelbeheer.                         |   1    | D/V |
| 4.15.2 | Verifieer of de beveiligingsgrenzen van een hybride implementatie duidelijk zijn gedefinieerd met versleutelde communicatiekanalen.  |   2    | D/V |
| 4.15.3 | Controleer of de toegang tot cloudbronnen zero-trust-verificatie omvat met continue authenticatie.                                   |   2    | D/V |
| 4.15.4 | Verifieer dat de vereisten voor gegevensresidentie worden afgedwongen door cryptografische attestatie van opslaglocaties.            |   3    | D/V |
| 4.15.5 | Verifieer dat de beveiligingsbeoordelingen van de cloudprovider agent-specifieke dreigingsmodellering en risicobeoordeling bevatten. |   3    | D/V |

---

## Referenties

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

