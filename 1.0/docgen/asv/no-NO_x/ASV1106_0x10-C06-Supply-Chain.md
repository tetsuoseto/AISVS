# C6 Sikkerhet i forsyningskjeden for modeller, rammeverk og data

## Kontrollmål

AI-forsyningskjedeangrep utnytter tredjepartsmodeller, rammeverk eller datasett for å legge inn bakdører, skjevheter eller utnyttbar kode. Disse kontrollene gir ende-til-ende sporbarhet, håndtering av sårbarheter og overvåking for å beskytte hele modellens livssyklus.

---

## C6.1 Forhåndstreningmodellvurdering og opprinnelsesintegritet

Vurder og autentiser opprinnelsen, lisensene og skjulte atferder til tredjepartsmodeller før finjustering eller implementering.

|   #   | Beskrivelse                                                                                                                                        | Nivå | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 6.1.1 | Bekreft at alle tredjeparts modellartefakter inkluderer en signert opprinnelsespost som identifiserer kildearkivet og commit-hashen.               |  1   |  D/V  |
| 6.1.2 | Bekreft at modeller skannes for ondsinnede lag eller trojanske triggere ved hjelp av automatiserte verktøy før import.                             |  1   |  D/V  |
| 6.1.3 | Bekreft at finjustering ved overføringslæring består adversarvurdering for å oppdage skjulte atferder.                                             |  2   |   D   |
| 6.1.4 | Verifiser at modell-lisenser, eksportkontroll-merker og dataopprinnelses-erklæringer er registrert i en ML-BOM-oppføring.                          |  2   |   V   |
| 6.1.5 | Sørg for at høy-risiko modeller (offentlig opplastede vekter, uverifiserte skapere) forblir isolert inntil menneskelig gjennomgang og godkjenning. |  3   |  D/V  |

---

## C6.2 Rammeverk- og biblioteks-skanning

Kontinuerlig skanne ML-rammeverk og biblioteker for CVE-er og ondsinnet kode for å holde kjøretidsstakken sikker.

|   #   | Beskrivelse                                                                                                                                 | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 6.2.1 | Bekreft at CI-pipelines kjører avhengighetsskannere på AI-rammeverk og kritiske biblioteker.                                                |  1   |  D/V  |
| 6.2.2 | Bekreft at kritiske sårbarheter (CVSS ≥ 7.0) blokkerer forfremmelse til produksjonsbilder.                                                  |  1   |  D/V  |
| 6.2.3 | Bekreft at statisk kodeanalyse kjører på forkede eller vendoriserte ML-biblioteker.                                                         |  2   |   D   |
| 6.2.4 | Bekreft at forslag til oppgradering av rammeverket inkluderer en vurdering av sikkerhetspåvirkning som refererer til offentlige CVE-kilder. |  2   |   V   |
| 6.2.5 | Bekreft at kjøretidssensorer varsler om uventede dynamiske bibliotekinnlastinger som avviker fra den signerte SBOM.                         |  3   |   V   |

---

## C6.3 Avhengighetspinning og verifisering

Fest alle avhengigheter til uforanderlige digestverdier og gjenskap bygg for å garantere identiske, uredigerte artefakter.

|   #   | Beskrivelse                                                                                                            | Nivå | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 6.3.1 | Bekreft at alle pakkebehandlere håndhever versjonsfiksering via låse-filer.                                            |  1   |  D/V  |
| 6.3.2 | Bekreft at uforanderlige digestverdier brukes i stedet for foranderlige tagger i referanser til containere.            |  1   |  D/V  |
| 6.3.3 | Bekreft at sjekkene for reproduserbare bygg sammenligner hasher på tvers av CI-kjøringer for å sikre identiske output. |  2   |   D   |
| 6.3.4 | Bekreft at byggebekreftelser lagres i 18 måneder for revisjonssporbarhet.                                              |  2   |   V   |
| 6.3.5 | Bekreft at utløpte avhengigheter utløser automatiske PR-er for å oppdatere eller forgreine festede versjoner.          |  3   |   D   |

---

## C6.4 Håndheving av pålitelig kilde

Tillat nedlasting av artefakter kun fra kryptografisk verifiserte, organisasjonsgodkjente kilder og blokker alt annet.

|   #   | Beskrivelse                                                                                                                  | Nivå | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 6.4.1 | Bekreft at modellvekter, datasett og containere bare lastes ned fra godkjente domener eller interne registre.                |  1   |  D/V  |
| 6.4.2 | Bekreft at Sigstore/Cosign-signaturer validerer utgiveridentitet før artefakter lagres lokalt i hurtigbuffer.                |  1   |  D/V  |
| 6.4.3 | Bekreft at utgående proxyer blokkerer uautentiserte nedlastinger av artefakter for å håndheve policy for pålitelig kilde.    |  2   |   D   |
| 6.4.4 | Bekreft at reponeringens tillitslister gjennomgås kvartalsvis med bevis på forretningsmessig begrunnelse for hver oppføring. |  2   |   V   |
| 6.4.5 | Bekreft at brudd på policy utløser karantene av artefakter og tilbakestilling av avhengige pipeline-kjøringer.               |  3   |   V   |

---

## C6.5 Risiko­vurdering av tredjeparts datasett

Evaluer eksterne datasett for forgiftning, skjevhet og juridisk samsvar, og overvåk dem gjennom hele livssyklusen.

|   #   | Beskrivelse                                                                                                                            | Nivå | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 6.5.1 | Bekreft at eksterne datasett gjennomgår forgiftningsrisikovurdering (f.eks. datafingeravtrykk, avviksdeteksjon).                       |  1   |  D/V  |
| 6.5.2 | Verifiser at skjevhetsmål (demografisk paritet, lik mulighet) beregnes før datasettgodkjenning.                                        |  1   |   D   |
| 6.5.3 | Bekreft at opprinnelse, slektskap og lisensbetingelser for datasett er dokumentert i ML-BOM-poster.                                    |  2   |   V   |
| 6.5.4 | Verifiser at periodisk overvåking oppdager avvik eller korrupsjon i hostede datasett.                                                  |  2   |   V   |
| 6.5.5 | Sørg for at ikke tillatt innhold (opphavsrett, personlig identifiserbar informasjon) fjernes gjennom automatisert rensing før trening. |  3   |   D   |

---

## C6.6 Overvåking av forsyningskjedeangrep

Oppdag trusler i forsyningskjeden tidlig gjennom CVE-feeds, revisjonslogganalyse og rødt-lag simuleringer.

|   #   | Beskrivelse                                                                                                              | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 6.6.1 | Bekreft at CI/CD-revisjonslogger strømmer til SIEM-deteksjoner for unormale pakketrekk eller manipulerte byggeprosesser. |  1   |   V   |
| 6.6.2 | Bekreft at hendelsesrespons-planer inkluderer tilbakeføringsprosedyrer for kompromitterte modeller eller biblioteker.    |  2   |   D   |
| 6.6.3 | Bekreft at trussel-intel-berikelse tagger ML-spesifikke indikatorer (f.eks. modell-forgiftning IoC-er) i alarmtriage.    |  3   |   V   |

---

## C6.7 ML‑BOM for Modellartefakter

Generer og signer detaljerte ML-spesifikke SBOM-er (ML-BOM-er) slik at nedstrømsbrukere kan verifisere komponentintegriteten ved distribueringstidspunktet.

|   #   | Beskrivelse                                                                                                                    | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 6.7.1 | Bekreft at hver modellartefakt publiserer en ML-BOM som inneholder datasett, vekter, hyperparametere og lisenser.              |  1   |  D/V  |
| 6.7.2 | Bekreft at ML‑BOM-generering og Cosign-signering er automatisert i CI og kreves for sammenslåing.                              |  1   |  D/V  |
| 6.7.3 | Bekreft at ML‑BOM fullstendighetskontroller mislykkes ved bygging dersom metadata for noen komponenter (hash, lisens) mangler. |  2   |   D   |
| 6.7.4 | Bekreft at downstream-forbrukere kan hente ML-BOMer via API for å validere importerte modeller ved distribusjonstidspunktet.   |  2   |   V   |
| 6.7.5 | Bekreft at ML-BOM-er er versjonskontrollerte og differensiert for å oppdage uautoriserte endringer.                            |  3   |   V   |

---

## Referanser

* [OWASP LLM03:2025 Supply Chain](https://genai.owasp.org/llmrisk/llm032025-supply-chain/)
* [MITRE ATLAS : Supply Chain Compromise](https://atlas.mitre.org/techniques/AML.T0010)
* [SBOM Overview – CISA](https://www.cisa.gov/sbom)
* [CycloneDX – Machine Learning Bill of Materials](https://cyclonedx.org/capabilities/mlbom/)

