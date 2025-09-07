# C4-infrastructuur, configuratie- en implementatiebeveiliging

## Beheersingsdoelstelling

AI-infrastructuur moet worden versterkt tegen privilege-escalatie, supply chain-manipulatie en laterale beweging door middel van veilige configuratie, runtime-isolatie, vertrouwde distributiepijplijnen en uitgebreide monitoring. Alleen geautoriseerde, gevalideerde infrastructuurcomponenten en configuraties bereiken de productie via gecontroleerde processen die beveiliging, integriteit en controleerbaarheid waarborgen.

Kernbeveiligingsdoel: Alleen cryptografisch ondertekende, kwetsbaarheid-gescande infrastructuurcomponenten bereiken de productie via geautomatiseerde validatiepijplijnen die beveiligingsbeleid afdwingen en onveranderlijke auditsporen behouden.

---

## C4.1 Isolatie van de runtime-omgeving

Voorkom container-ontsnappingen en privilege-escalatie door middel van kernel-level isolatieprimitieven en verplichte toegangscontrolemechanismen.

|   #   | Beschrijving                                                                                                                                                                                                                          | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.1.1 | Controleer of alle AI-containers ALLE Linux-machtigingen verwijderen behalve CAP_SETUID, CAP_SETGID, en expliciet vereiste machtigingen die zijn gedocumenteerd in beveiligingsstandaarden.                                           |   1    | D/V |
| 4.1.2 | Controleer of seccomp-profielen alle systeemoproepen blokkeren behalve die in vooraf goedgekeurde toestalijsten, waarbij overtredingen leiden tot het beëindigen van de container en het genereren van beveiligingswaarschuwingen.    |   1    | D/V |
| 4.1.3 | Controleer of AI-workloads worden uitgevoerd met root-bestandssystemen in alleen-lezen modus, tmpfs voor tijdelijke gegevens, en benoemde volumes voor persistente gegevens waarbij noexec mount-opties worden afgedwongen.           |   2    | D/V |
| 4.1.4 | Controleer of op eBPF gebaseerde runtime monitoring (Falco, Tetragon of gelijkwaardig) pogingen tot privilege-escalatie detecteert en automatisch overtredende processen beëindigt binnen de reactietijdvereisten van de organisatie. |   2    | D/V |
| 4.1.5 | Verifieer dat AI-werklasten met hoog risico worden uitgevoerd in hardware-geïsoleerde omgevingen (Intel TXT, AMD SVM, of speciale bare-metal nodes) met attestatieverificatie.                                                        |   3    | D/V |

---

## C4.2 Veilige Build- en Deployment-pijplijnen

Zorg voor cryptografische integriteit en beveiliging van de toeleveringsketen door middel van reproduceerbare builds en ondertekende artefacten.

|   #   | Beschrijving                                                                                                                                                                                                                    | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.2.1 | Controleer of infrastructuur-als-code wordt gescand met tools (tfsec, Checkov of Terrascan) bij elke commit, waarbij merges worden geblokkeerd bij CRITIEKE of HOGE ernst bevindingen.                                          |   1    | D/V |
| 4.2.2 | Verifieer dat container builds reproduceerbaar zijn met identieke SHA256-hashes over verschillende builds en genereer SLSA Level 3 provenance-attesten ondertekend met Sigstore.                                                |   1    | D/V |
| 4.2.3 | Controleer dat containerafbeeldingen CycloneDX- of SPDX-SBOM's insluiten en met Cosign zijn ondertekend voordat ze naar het register worden gepusht, waarbij niet-ondertekende afbeeldingen bij implementatie worden afgewezen. |   2    | D/V |
| 4.2.4 | Verifieer dat CI/CD-pijplijnen OIDC-tokens gebruiken van HashiCorp Vault, AWS IAM-rollen of Azure Managed Identity met levensduren die de limieten van het organisatorische beveiligingsbeleid niet overschrijden.              |   2    | D/V |
| 4.2.5 | Verifieer dat Cosign-handtekeningen en SLSA-herkomst worden gevalideerd tijdens het implementatieproces vóór de uitvoering van de container en dat verificatiefouten ervoor zorgen dat de implementatie mislukt.                |   2    | D/V |
| 4.2.6 | Controleer of bouwomgevingen draaien in vluchtige containers of VM's zonder persistent opslag en met netwerkisolatie van productie-VPC's.                                                                                       |   2    | D/V |

---

## C4.3 Netwerkbeveiliging & Toegangscontrole

Implementeer zero-trust netwerken met standaard-weigerbeleid en versleutelde communicatie.

|   #   | Beschrijving                                                                                                                                                                                                       | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 4.3.1 | Controleer of Kubernetes NetworkPolicies of een equivalent standaard-deny ingress/egress toepassen met expliciete toestemmingsregels voor vereiste poorten (443, 8080, enz.).                                      |   1    | D/V |
| 4.3.2 | Controleer of SSH (poort 22), RDP (poort 3389) en cloud metadata-eindpunten (169.254.169.254) zijn geblokkeerd of certificaatgebaseerde authenticatie vereisen.                                                    |   1    | D/V |
| 4.3.3 | Controleer of uitgaand verkeer wordt gefilterd via HTTP/HTTPS-proxy's (Squid, Istio of cloud NAT-gateways) met domeintoegangsverklaringen en dat geblokkeerde verzoeken worden gelogd.                             |   2    | D/V |
| 4.3.4 | Verifieer dat inter-service communicatie gebruikmaakt van mutual TLS met certificaten die worden gewisseld volgens het organisatiebeleid en dat certificaatvalidatie wordt afgedwongen (geen skip-verify vlaggen). |   2    | D/V |
| 4.3.5 | Verifieer dat de AI-infrastructuur draait in toegewijde VPC's/VNets zonder directe internettoegang en alleen communiceert via NAT-gateways of bastion-hosts.                                                       |   2    | D/V |

---

## C4.4 Geheimen- en cryptografisch sleutelbeheer

Bescherm referenties via hardware-ondersteunde opslag en geautomatiseerde rotatie met zero-trust toegang.

|   #   | Beschrijving                                                                                                                                                                                                                                                 | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 4.4.1 | Controleer of geheimen worden opgeslagen in HashiCorp Vault, AWS Secrets Manager, Azure Key Vault of Google Secret Manager met versleuteling in rust met behulp van AES-256.                                                                                 |   1    | D/V |
| 4.4.2 | Verifieer dat cryptografische sleutels worden gegenereerd in FIPS 140-2 Level 2 HSM's (AWS CloudHSM, Azure Dedicated HSM) met sleutelrotatie volgens het cryptografisch beleid van de organisatie.                                                           |   1    | D/V |
| 4.4.3 | Verifieer dat het roteren van geheimen is geautomatiseerd met zero-downtime implementatie en onmiddellijke rotatie die wordt geactiveerd door personeelswijzigingen of beveiligingsincidenten.                                                               |   2    | D/V |
| 4.4.4 | Verifieer dat containerafbeeldingen worden gescand met tools (GitLeaks, TruffleHog of detect-secrets) die builds blokkeren die API-sleutels, wachtwoorden of certificaten bevatten.                                                                          |   2    | D/V |
| 4.4.5 | Controleer of toegang tot productiesystemen met een geheim wachtwoord multifactor-authenticatie (MFA) vereist met hardwaretokens (YubiKey, FIDO2) en dat deze wordt vastgelegd in onveranderlijke auditlogboeken met gebruikersidentiteiten en tijdstempels. |   2    | D/V |
| 4.4.6 | Controleer of geheimen worden geïnjecteerd via Kubernetes-secrets, gemonteerde volumes of init-containers en zorg ervoor dat geheimen nooit worden ingebed in omgevingsvariabelen of images.                                                                 |   2    | D/V |

---

## C4.5 AI-werkbelasting sandboxing en validatie

Isoleren van onbetrouwbare AI-modellen in beveiligde sandboxes met uitgebreide gedragsanalyse.

|   #   | Beschrijving                                                                                                                                                                                                       | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 4.5.1 | Controleer of externe AI-modellen worden uitgevoerd in gVisor, microVM's (zoals Firecracker, CrossVM) of Docker-containers met de opties --security-opt=no-new-privileges en --read-only.                          |   1    | D/V |
| 4.5.2 | Controleer of sandbox-omgevingen geen netwerkconnectiviteit hebben (--network=none) of alleen localhost-toegang met alle externe verzoeken geblokkeerd door iptables-regels.                                       |   1    | D/V |
| 4.5.3 | Controleer of de validatie van het AI-model automatische red-team tests omvat met organisatorisch gedefinieerde testdekking en gedragsanalyse voor het detecteren van achterdeurtjes.                              |   2    | D/V |
| 4.5.4 | Controleer of voordat een AI-model in productie wordt genomen, de sandbox-resultaten cryptografisch worden ondertekend door geautoriseerd beveiligingspersoneel en worden opgeslagen in onveranderlijke auditlogs. |   2    | D/V |
| 4.5.5 | Verifieer dat sandbox-omgevingen worden vernietigd en opnieuw worden gemaakt vanuit gouden images tussen evaluaties, met volledige opschoning van het bestandssysteem en geheugen.                                 |   2    | D/V |

---

## C4.6 Infrastructuurbeveiligingsbewaking

Voortdurend de infrastructuur scannen en monitoren met geautomatiseerde herstelacties en realtime waarschuwingen.

|   #   | Beschrijving                                                                                                                                                                                                         | Niveau | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.6.1 | Verifieer dat containerafbeeldingen worden gescand volgens de organisatorische schema's, waarbij CRITIEKE kwetsbaarheden de implementatie blokkeren op basis van organisatorische risicodrempels.                    |   1    | D/V |
| 4.6.2 | Verifieer dat de infrastructuur voldoet aan CIS Benchmarks of NIST 800-53-controles met door de organisatie gedefinieerde compliance drempels en automatische herstelmaatregelen voor mislukte controles.            |   1    | D/V |
| 4.6.3 | Verifieer dat kwetsbaarheden met een HOGE ernstgraad worden gepatcht volgens de tijdlijnen van het risicobeheer van de organisatie, met noodprocedures voor actief misbruikte CVE's.                                 |   2    | D/V |
| 4.6.4 | Verifieer dat beveiligingswaarschuwingen integreren met SIEM-platforms (Splunk, Elastic of Sentinel) met behulp van CEF- of STIX/TAXII-formaten met geautomatiseerde verrijking.                                     |   2    |  V  |
| 4.6.5 | Verifieer dat infrastructuurmetriekgegevens worden geëxporteerd naar monitoringsystemen (Prometheus, DataDog) met SLA-dashboards en managementrapportage.                                                            |   3    |  V  |
| 4.6.6 | Controleer of configuratieafwijkingen worden gedetecteerd met behulp van tools (Chef InSpec, AWS Config) volgens de monitoringvereisten van de organisatie, met automatische terugrol bij ongeoorloofde wijzigingen. |   2    | D/V |

---

## C4.7 AI-infrastructuur Resourcebeheer

Voorkom uitputting van middelen aanvallen en zorg voor een eerlijke toewijzing van middelen door middel van quota en monitoring.

|   #   | Beschrijving                                                                                                                                                                                                                                        | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.7.1 | Controleer of het gebruik van GPU/TPU wordt gemonitord met waarschuwingen die worden geactiveerd bij organisatiedefinieerde drempels en dat automatische schaalvergroting of load balancing wordt geactiveerd op basis van capaciteitsbeheerbeleid. |   1    | D/V |
| 4.7.2 | Verifieer dat AI-werkbelastingmetingen (inferentie-latentie, doorvoersnelheid, foutpercentages) worden verzameld volgens de monitoringsvereisten van de organisatie en gecorreleerd zijn met het gebruik van de infrastructuur.                     |   1    | D/V |
| 4.7.3 | Controleer of Kubernetes ResourceQuotas of gelijkwaardige mechanismen individuele workloads beperken volgens de resource-allocatiebeleid van de organisatie, met harde limieten die worden afgedwongen.                                             |   2    | D/V |
| 4.7.4 | Verifieer dat kostenbewaking de uitgaven per werklast/huurder volgt met waarschuwingen op basis van organisatorische budgetdrempels en geautomatiseerde controles voor budgetoverschrijdingen.                                                      |   2    |  V  |
| 4.7.5 | Controleer of capaciteitsplanning gebruikmaakt van historische gegevens met door de organisatie gedefinieerde voorspellingsperioden en geautomatiseerde resourcevoorziening op basis van vraagpatronen.                                             |   3    |  V  |
| 4.7.6 | Controleer of uitputting van middelen circuit breakers activeert volgens de organisatieresponsvereisten, inclusief snelheidsbeperking op basis van capaciteitsbeleid en werkbelastingisolatie.                                                      |   2    | D/V |

---

## C4.8 Scheiding van omgevingen en promotiecontroles

Handhaaf strikte omgevingsgrenzen met geautomatiseerde promotiepoorten en beveiligingsvalidatie.

|   #   | Beschrijving                                                                                                                                                                                                                         | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 4.8.1 | Controleer of dev/test/prod-omgevingen draaien in gescheiden VPC's/VNets zonder gedeelde IAM-rollen, beveiligingsgroepen of netwerkconnectiviteit.                                                                                   |   1    | D/V |
| 4.8.2 | Verifieer dat omgevingspromotie goedkeuring vereist van organisatorisch gedefinieerd bevoegd personeel met cryptografische handtekeningen en onveranderlijke audittrail.                                                             |   1    | D/V |
| 4.8.3 | Verifieer dat productieomgevingen SSH-toegang blokkeren, debug-eindpunten uitschakelen en veranderingsverzoeken vereisen met organisatorische voorafgaande kennisgevingsvereisten, behalve in noodgevallen.                          |   2    | D/V |
| 4.8.4 | Verifieer dat wijzigingen in infrastructure-as-code peer review vereisen met geautomatiseerde tests en beveiligingsscans voordat ze worden samengevoegd met de main branch.                                                          |   2    | D/V |
| 4.8.5 | Controleer of niet-productiegegevens geanonimiseerd zijn volgens de privacyvereisten van de organisatie, of dat synthetische gegevens gegenereerd zijn, of dat volledige gegevensmaskering met verwijdering van PII is geverifieerd. |   2    | D/V |
| 4.8.6 | Controleer of promotiepoorten geautomatiseerde beveiligingstests bevatten (SAST, DAST, container scanning) waarbij geen CRITICAL bevindingen zijn toegestaan voor goedkeuring.                                                       |   2    | D/V |

---

## C4.9 Infrastructuur Back-up & Herstel

Zorg voor veerkracht van de infrastructuur door middel van geautomatiseerde back-ups, geteste herstelprocedures en mogelijkheden voor rampenherstel.

|   #   | Beschrijving                                                                                                                                                                                             | Niveau | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.9.1 | Verifieer dat infrastructuurconfiguraties worden geback-upt volgens de back-upschema's van de organisatie naar geografisch gescheiden regio's met implementatie van de 3-2-1 back-upstrategie.           |   1    | D/V |
| 4.9.2 | Verifieer dat back-upsystemen draaien in geïsoleerde netwerken met aparte referenties en air-gapped opslag voor bescherming tegen ransomware.                                                            |   2    | D/V |
| 4.9.3 | Verifieer dat herstelprocedures worden getest en gevalideerd via geautomatiseerde tests volgens de organisatieschema's, waarbij de RTO- en RPO-doelstellingen voldoen aan de organisatorische vereisten. |   2    |  V  |
| 4.9.4 | Verifieer dat disaster recovery AI-specifieke runbooks omvat met modelgewichtherstel, GPU-cluster herbouwing en mapping van servicedependencies.                                                         |   3    |  V  |

---

## C4.10 Infrastructuurcompliance & Governance

Handhaaf regelgevende naleving door voortdurende beoordeling, documentatie en geautomatiseerde controles.

|   #    | Beschrijving                                                                                                                                                                                             | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.10.1 | Verifieer dat de naleving van de infrastructuur wordt beoordeeld volgens de organisatorische schema's aan de hand van SOC 2, ISO 27001, of FedRAMP-controles met geautomatiseerde bewijsverzameling.     |   2    | D/V |
| 4.10.2 | Verifieer dat de infrastructuurdocumentatie netwerkdiagrammen, gegevensstroomkaarten en dreigingsmodellen bevat die zijn bijgewerkt volgens de vereisten van het wijzigingsbeheer binnen de organisatie. |   2    |  V  |
| 4.10.3 | Verifieer dat infrastructuurwijzigingen een geautomatiseerde nalevings-impactbeoordeling ondergaan met goedkeuringsworkflows voor regelgeving bij hoogrisicowaarderingen.                                |   3    | D/V |

---

## C4.11 AI Hardware-beveiliging

Beveilig AI-specifieke hardwarecomponenten zoals GPU's, TPU's en gespecialiseerde AI-versnellers.

|   #    | Beschrijving                                                                                                                                                                                | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.11.1 | Verifieer dat firmware van AI-versnellers (GPU BIOS, TPU-firmware) wordt geverifieerd met cryptografische handtekeningen en bijgewerkt volgens de patchmanagementtijden van de organisatie. |   2    | D/V |
| 4.11.2 | Verifieer dat vóór de uitvoering van de werklast de integriteit van de AI-versneller wordt gevalideerd door middel van hardware-attestatie met TPM 2.0, Intel TXT of AMD SVM.               |   2    | D/V |
| 4.11.3 | Controleer of het GPU-geheugen geïsoleerd is tussen workloads met behulp van SR-IOV, MIG (Multi-Instance GPU), of gelijkwaardige hardwarepartitionering met geheugensanering tussen taken.  |   2    | D/V |
| 4.11.4 | Verifieer dat de AI-hardwareleveringsketen herkomstverificatie bevat met fabrikantcertificaten en controle van verzegelde verpakking die tekenen van knoeien aantoont.                      |   3    |  V  |
| 4.11.5 | Controleer of hardwarebeveiligingsmodules (HSM's) AI-modelgewichten en cryptografische sleutels beschermen met FIPS 140-2 Level 3- of Common Criteria EAL4+-certificering.                  |   3    | D/V |

---

## C4.12 Edge- en gedistribueerde AI-infrastructuur

Veilige gedistribueerde AI-implementaties, inclusief edge computing, gefedereerd leren en multi-site architecturen.

|   #    | Beschrijving                                                                                                                                                                                                   | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.12.1 | Controleer of edge AI-apparaten zich authenticeren bij de centrale infrastructuur met behulp van mutual TLS en dat apparaatcertificaten worden geroteerd volgens het organisatorische certificaatbeheerbeleid. |   2    | D/V |
| 4.12.2 | Controleer of randapparaten beveiligde opstart uitvoeren met geverifieerde handtekeningen en rollback-bescherming die firmware-downgradeaanvallen voorkomt.                                                    |   2    | D/V |
| 4.12.3 | Verifieer dat gedistribueerde AI-coördinatie gebruikmaakt van consensusalgoritmen die bestand zijn tegen Byzantijnse fouten, met deelnemervalidering en detectie van kwaadaardige knooppunten.                 |   3    | D/V |
| 4.12.4 | Bevestig dat communicatie van edge naar cloud bandbreedtebeperking, gegevenscompressie en offline operationele mogelijkheden met beveiligde lokale opslag omvat.                                               |   3    | D/V |

---

## C4.13 Beveiliging van Multi-Cloud en Hybride Infrastructuur

Beveilig AI-werklasten over meerdere cloudproviders en hybride cloud-on-premises implementaties.

|   #    | Beschrijving                                                                                                                                                                                  | Niveau | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.13.1 | Controleer of multi-cloud AI-implementaties cloud-agnostische identiteitsfederatie (OIDC, SAML) gebruiken met gecentraliseerd beleidsbeheer over verschillende aanbieders.                    |   2    | D/V |
| 4.13.2 | Controleer of cross-cloud datatransmissie end-to-end encryptie gebruikt met door de klant beheerde sleutels en datalocatiecontroles worden toegepast volgens de jurisdictie.                  |   2    | D/V |
| 4.13.3 | Verifieer of hybride cloud AI-workloads consistente beveiligingsbeleid implementeren over on-premise en cloudomgevingen met uniforme monitoring en waarschuwingen.                            |   2    | D/V |
| 4.13.4 | Verifieer dat het voorkomen van vendor lock-in bij cloudproviders draagbare infrastructure-as-code, gestandaardiseerde API's en data-exportmogelijkheden met formatconversietools omvat.      |   3    |  V  |
| 4.13.5 | Verifieer of multi-cloud kostenoptimalisatie beveiligingscontroles omvat die het voorkomen van resourceverspreiding en ongeautoriseerde kosten voor data-overdracht tussen clouds waarborgen. |   3    |  V  |

---

## C4.14 Infrastructuurautomatisering & GitOps-beveiliging

Beveilig infrastructuurautomatiseringspijplijnen en GitOps-workflows voor het beheer van AI-infrastructuur.

|   #    | Beschrijving                                                                                                                                                                                                          | Niveau | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.14.1 | Controleer of GitOps-repositories ondertekende commits vereisen met GPG-sleutels en branch-beschermingsregels hebben die directe pushen naar hoofdbranches voorkomen.                                                 |   2    | D/V |
| 4.14.2 | Verifieer dat infrastructuurautomatisering driftdetectie omvat met automatische herstel- en terugrolmogelijkheden die worden geactiveerd volgens de organisatorische responsvereisten voor ongeoorloofde wijzigingen. |   2    | D/V |
| 4.14.3 | Controleer of geautomatiseerde infrastructuurvoorziening beveiligingsbeleidvalidatie omvat met implementatieblokkering voor niet-conforme configuraties.                                                              |   2    | D/V |
| 4.14.4 | Verifieer dat geheimen voor infrastructuurautomatisering worden beheerd via externe geheimenoperators (External Secrets Operator, Bank-Vaults) met automatische rotatie.                                              |   2    | D/V |
| 4.14.5 | Verifieer dat zelfherstellende infrastructuur beveiligingsgebeurtenissen correleert met geautomatiseerde incidentrespons en workflows voor het informeren van belanghebbenden.                                        |   3    |  V  |

---

## C4.15 Kwantumbestendige Infrastructuurbeveiliging

Bereid AI-infrastructuur voor op bedreigingen van kwantumcomputing door middel van post-kwantumcryptografie en kwantumveilige protocollen.

|   #    | Beschrijving                                                                                                                                                                                                | Niveau | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.15.1 | Controleer of AI-infrastructuur NIST-goedgekeurde post-quantum cryptografische algoritmen (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) implementeert voor sleuteluitwisseling en digitale handtekeningen. |   3    | D/V |
| 4.15.2 | Verifieer dat quantum key distribution (QKD) systemen worden geïmplementeerd voor beveiligde AI-communicatie met quantum-veilige sleutelbeheerprotocollen.                                                  |   3    | D/V |
| 4.15.3 | Verifieer dat cryptografische wendbaarheidskaders snelle migratie naar nieuwe post-quantum algoritmen mogelijk maken met geautomatiseerde certificaat- en sleuteldraaien.                                   |   3    | D/V |
| 4.15.4 | Controleer of kwantumdreigingsmodellering de kwetsbaarheid van AI-infrastructuur voor kwantumaanvallen beoordeelt met gedocumenteerde migratietijdlijnen en risicobeoordelingen.                            |   3    |  V  |
| 4.15.5 | Verifieer dat hybride klassieke-kwantum cryptografische systemen verdedigingsdiepte bieden tijdens de kwantumovergangsperiode met prestatiemonitoring.                                                      |   3    | D/V |

---

## C4.16 Vertrouwelijk Berekenen & Veilige Enclaves

Bescherm AI-werklasten en modelgewichten met op hardware gebaseerde vertrouwde uitvoeringsomgevingen en vertrouwelijke computing-technologieën.

|   #    | Beschrijving                                                                                                                                                                              | Niveau | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.16.1 | Verifieer dat gevoelige AI-modellen worden uitgevoerd binnen Intel SGX-enclaves, AMD SEV-SNP of ARM TrustZone met versleuteld geheugen en attestatie-verificatie.                         |   3    | D/V |
| 4.16.2 | Verifieer dat vertrouwelijke containers (Kata Containers, gVisor met vertrouwelijke computing) AI-werkbelastingen isoleren met hardware-gedwongen geheugenversleuteling.                  |   3    | D/V |
| 4.16.3 | Verifieer dat remote attestation de integriteit van de enclave valideert voordat AI-modellen worden geladen, met cryptografisch bewijs van de authenticiteit van een uitvoeringsomgeving. |   3    | D/V |
| 4.16.4 | Verifieer dat vertrouwelijke AI-inferentiediensten modelextractie voorkomen door middel van versleutelde berekeningen met verzegelde modelgewichten en beschermde uitvoering.             |   3    | D/V |
| 4.16.5 | Verifieer dat de orkestratie van de vertrouwde uitvoeringsomgeving de levenscyclus van de beveiligde enclave beheert met remote attestation en versleutelde communicatiekanalen.          |   3    | D/V |
| 4.16.6 | Controleer of veilige multi-party computation (SMPC) gezamenlijke AI-training mogelijk maakt zonder individuele datasets of modelparameters bloot te stellen.                             |   3    | D/V |

---

## C4.17 Zero-Knowledge Infrastructuur

Implementeer zero-knowledge proof-systemen voor privacybewakende AI-verificatie en authenticatie zonder gevoelige informatie prijs te geven.

|   #    | Beschrijving                                                                                                                                                                                      | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.17.1 | Verifieer dat zero-knowledge proofs (ZK-SNARKs, ZK-STARKs) de integriteit van het AI-model en de herkomst van de training verifiëren zonder modelgewichten of trainingsgegevens bloot te stellen. |   3    | D/V |
| 4.17.2 | Verifieer dat op ZK gebaseerde authenticatiesystemen privacy-behoudende gebruikersverificatie voor AI-diensten mogelijk maken zonder identiteit-gerelateerde informatie prijs te geven.           |   3    | D/V |
| 4.17.3 | Verifieer dat private set intersection (PSI)-protocollen veilige gegevensmatching mogelijk maken voor federatieve AI zonder individuele datasets bloot te stellen.                                |   3    | D/V |
| 4.17.4 | Verifieer dat zero-knowledge machine learning (ZKML) systemen verifieerbare AI-afleidingen mogelijk maken met cryptografisch bewijs van correcte berekening.                                      |   3    | D/V |
| 4.17.5 | Controleer of ZK-rollups schaalbare, privacybeschermende AI-transactie verwerking bieden met batchverificatie en verminderde rekenkundige belasting.                                              |   3    | D/V |

---

## C4.18 Preventie van side-channel-aanvallen

Bescherm AI-infrastructuur tegen timing-, stroom-, elektromagnetische- en cache-gebaseerde side-channel aanvallen die gevoelige informatie kunnen lekken.

|   #    | Beschrijving                                                                                                                                                               | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.18.1 | Verifieer dat de AI-inferentietijd wordt genormaliseerd met behulp van constant-time algoritmen en opvulling om timing-gebaseerde modelextractieaanvallen te voorkomen.    |   3    | D/V |
| 4.18.2 | Verifieer dat bescherming tegen vermogenanalyse ruisinjectie, netspanningsfiltering en gerandomiseerde uitvoeringspatronen voor AI-hardware omvat.                         |   3    | D/V |
| 4.18.3 | Controleer of mitigatie van cache-gebaseerde zijkanaalaanvallen gebruikmaakt van cache-partitionering, randomisatie en flush-instructies om informatielekken te voorkomen. |   3    | D/V |
| 4.18.4 | Verifieer dat bescherming tegen elektromagnetische emissies afscherming, signaalfiltering en gerandomiseerde verwerking omvat om TEMPEST-achtige aanvallen te voorkomen.   |   3    | D/V |
| 4.18.5 | Controleer of micro-architecturale zijkanaalverdedigingen speculatieve uitvoeringscontroles en het verhullen van geheugen toegangs patronen omvatten.                      |   3    | D/V |

---

## C4.19 Neuromorfe & Gespecialiseerde AI Hardware Beveiliging

Beveilig opkomende AI-hardwarearchitecturen, waaronder neuromorfe chips, FPGA's, aangepaste ASIC's en optische computersystemen.

|   #    | Beschrijving                                                                                                                                                                     | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.19.1 | Controleer of de beveiliging van de neuromorfe chip patroonversleuteling van spikes, bescherming van synaptische gewichten en hardwaregebaseerde validatie van leerregels omvat. |   3    | D/V |
| 4.19.2 | Verifieer dat FPGA-gebaseerde AI-versnellers bitstream-encryptie, anti-tampermechanismen en veilige configuratielading met geverifieerde updates implementeren.                  |   3    | D/V |
| 4.19.3 | Verifieer dat aangepaste ASIC-beveiliging on-chip beveiligingsprocessors, een hardware root of trust en veilige sleutelopslag met detectie van manipulatie omvat.                |   3    | D/V |
| 4.19.4 | Verifieer of optische computersystemen kwantumveilige optische encryptie, veilige fotonische schakeling en beschermde optische signaalverwerking implementeren.                  |   3    | D/V |
| 4.19.5 | Controleer of hybride analoog-digitale AI-chips beveiligde analoge berekeningen, beschermde gewichtsopslag en geauthenticeerde analoog-naar-digitaal conversie bevatten.         |   3    | D/V |

---

## C4.20 Privacy-behoudende Compute-infrastructuur

Implementeer infrastructuurcontroles voor privacybewarende berekeningen om gevoelige gegevens te beschermen tijdens AI-verwerking en -analyse.

|   #    | Beschrijving                                                                                                                                                                                        | Niveau | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.20.1 | Verifieer dat de infrastructuur voor homomorfe encryptie versleutelde berekeningen op gevoelige AI-werkbelastingen mogelijk maakt met cryptografische integriteitsverificatie en prestatiebewaking. |   3    | D/V |
| 4.20.2 | Verifieer dat private informatieopvragsystemen databasequery's mogelijk maken zonder querypatronen bloot te geven, met cryptografische bescherming van toegangspatronen.                            |   3    | D/V |
| 4.20.3 | Verifieer dat veilige multi-party computation-protocollen privacy-beschermende AI-inferentie mogelijk maken zonder individuele invoer of tussenliggende berekeningen bloot te stellen.              |   3    | D/V |
| 4.20.4 | Verifieer dat privacy-beschermend sleutelhbeheer gedistribueerde sleutelgeneratie, drempelcryptografie en veilige sleutelrotatie met hardware-ondersteuning omvat.                                  |   3    | D/V |
| 4.20.5 | Verifieer dat de privacy-beschermende rekenprestaties worden geoptimaliseerd door batching, caching en hardwareversnelling, terwijl de cryptografische beveiligingsgaranties behouden blijven.      |   3    | D/V |

---

## C4.15 Agent Framework Cloud-integratiebeveiliging & Hybride implementatie

Beveiligingscontroles voor cloud-geïntegreerde agentkaders met hybride on-premises/cloud-architecturen.

|   #    | Beschrijving                                                                                                                        | Niveau | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.15.1 | Controleer of de integratie van cloudopslag end-to-end encryptie gebruikt met sleutelbeheer dat door de agent wordt gecontroleerd.  |   1    | D/V |
| 4.15.2 | Controleer of de beveiligingsgrenzen van de hybride implementatie duidelijk zijn gedefinieerd met versleutelde communicatiekanalen. |   2    | D/V |
| 4.15.3 | Verifieer dat de toegang tot cloudbronnen zero-trust verificatie omvat met continue authenticatie.                                  |   2    | D/V |
| 4.15.4 | Verifieer dat gegevensresidentie-eisen worden afgedwongen door cryptografische attestatie van opslaglocaties.                       |   3    | D/V |
| 4.15.5 | Verifieer of de beveiligingsbeoordelingen van de cloudprovider agent-specifieke dreigingsmodellering en risicobeoordeling omvatten. |   3    | D/V |

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

