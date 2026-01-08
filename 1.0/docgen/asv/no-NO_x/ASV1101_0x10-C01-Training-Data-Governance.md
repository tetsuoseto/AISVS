# C1 Opplæring Dataforvaltning og Skjevhetshåndtering

## Kontrollmål

Treningsdata må hentes, håndteres og vedlikeholdes på en måte som ivaretar opphav, sikkerhet, kvalitet og rettferdighet. Ved å gjøre dette oppfylles juridiske forpliktelser og risikoen for skjevhet, forgiftning eller personvernbrudd som kan oppstå under trening og påvirke hele AI-livssyklusen, reduseres.

---

## C1.1 Opprinnelse for treningsdata

Oppretthold en verifiserbar oversikt over alle datasett, aksepter kun pålitelige kilder, og loggfør alle endringer for revisjonsspor.

|   #   | Beskrivelse                                                                                                                                                                                     | Nivå | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 1.1.1 | Sørg for at en oppdatert oversikt over alle treningsdatakilder (opprinnelse, ansvarlig/eier, lisens, innsamlingmetode, tiltenkte bruksbegrensninger og behandlingshistorikk) blir vedlikeholdt. |  1   |  D/V  |
| 1.1.2 | Bekreft at treningsdataprosesser utelukker unødvendige funksjoner, attributter eller felt (f.eks. ubrukt metadata, sensitiv PII, lekket testdata).                                              |  1   |  D/V  |
| 1.1.3 | Bekreft at alle endringer i datasettet er underlagt en loggført godkjenningsprosess.                                                                                                            |  2   |  D/V  |
| 1.1.4 | Verifiser at datasett eller delsett er vannmerket eller fingeravtrykt der det er mulig.                                                                                                         |  3   |  D/V  |

---

## C1.2 Sikkerhet og integritet for treningsdata

Begrens tilgangen til treningsdata, krypter den når den er lagret og under overføring, og valider integriteten for å forhindre manipulering, tyveri eller dataforgiftning.

|   #   | Beskrivelse                                                                                                                                                         | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 1.2.1 | Bekreft at tilgangskontroller beskytter lagring av treningsdata og pipelines.                                                                                       |  1   |  D/V  |
| 1.2.2 | Bekreft at all tilgang til treningsdata logges, inkludert bruker, tidspunkt og handling.                                                                            |  2   |  D/V  |
| 1.2.3 | Verifiser at treningsdatasett er kryptert under overføring og i hvile, ved bruk av bransjestandard kryptografiske algoritmer og nøkkeladministrasjonspraksis.       |  2   |  D/V  |
| 1.2.4 | Bekreft at kryptografiske hasher eller digitale signaturer brukes for å sikre dataintegritet under lagring og overføring av treningsdata.                           |  2   |  D/V  |
| 1.2.5 | Bekreft at automatiserte deteksjonsteknikker brukes for å beskytte mot uautoriserte endringer eller korrupsjon av treningsdata.                                     |  2   |  D/V  |
| 1.2.6 | Bekreft at utdatert treningsdata er sikkert slettet eller anonymisert.                                                                                              |  2   |  D/V  |
| 1.2.7 | Sørg for at alle versjoner av treningsdatasettet er entydig identifisert, lagret uforanderlig, og reviderbare for å støtte tilbakeføring og rettsmedisinsk analyse. |  3   |  D/V  |

---

## C1.3 Kvalitet, integritet og sikkerhet for merking av treningsdata

Beskytt etiketter og krev teknisk gjennomgang for kritiske data.

|   #   | Beskrivelse                                                                                                                                                                                                   | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 1.3.1 | Bekreft at kryptografiske hasher eller digitale signaturer er brukt på etikettartefakter for å sikre deres integritet og autentisitet.                                                                        |  2   |  D/V  |
| 1.3.2 | Bekreft at merkingsgrensesnitt og -plattformer håndhever sterke tilgangskontroller, opprettholder manipulasjonsbestandige revisjonslogger for alle merkingsaktiviteter, og beskytter mot uautorisert endring. |  2   |  D/V  |
| 1.3.3 | Bekreft at sensitiv informasjon i etiketter blir fjernet, anonymisert eller kryptert på datafeltnivå både i hvilemodus og under overføring.                                                                   |  3   |  D/V  |

---

## C1.4 Kvalitet på treningsdata og sikkerhetsgaranti

Kombiner automatisert validering, manuelle stikkprøver og loggførte utbedringer for å garantere datasettets pålitelighet.

|   #   | Beskrivelse                                                                                                                                                                                                                                                                                                                                                                                                   | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 1.4.1 | Bekreft at automatiserte tester fanger opp formateringsfeil og nullverdier ved hver inntasting eller betydelig datatransformasjon.                                                                                                                                                                                                                                                                            |  1   |   D   |
| 1.4.2 | Bekreft at LLM-trenings- og finjusteringspipelines implementerer forgiftningsdeteksjon og validering av dataintegritet (f.eks. statistiske metoder, outlier-deteksjon, embeddingsanalyse) for å identifisere potensielle forgiftningsangrep (f.eks. etikettbytting, innsetting av bakdørtrigger, rollebyttekommandoer, angrep via innflytelsesrike eksempler) eller utilsiktet datakorrupsjon i treningsdata. |  2   |  D/V  |
| 1.4.3 | Bekreft at automatisk genererte etiketter (f.eks. via LLM-er eller svak veiledning) er underlagt konfidensgrenser og konsistenskontroller for å oppdage hallusinerte, villedende eller lavkonfidensetiketter.                                                                                                                                                                                                 |  2   |  D/V  |
| 1.4.4 | Bekreft at hensiktsmessige forsvarsmekanismer, som adversarial trening (ved bruk av genererte adversariale eksempler), dataforsterkning med forstyrrede inndata, eller robuste optimaliseringsteknikker, er implementert og justert for relevante modeller basert på risikovurdering.                                                                                                                         |  3   |  D/V  |
| 1.4.5 | Bekreft at automatiserte tester fanger opp etikettforvrengninger ved hver innlasting eller betydelig datatransformasjon.                                                                                                                                                                                                                                                                                      |  3   |   D   |

---

## C1.5 Data Stamtavle og Sporbarhet

Spor hele reisen til hvert datapunkt fra kilde til modellinput for revisjonssporing og hendelseshåndtering.

|   #   | Beskrivelse                                                                                                                                                                                                               | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 1.5.1 | Bekreft at opprinnelsen til hvert datapunkt, inkludert alle transformasjoner, utvidelser og sammenslåinger, er dokumentert og kan rekonstrueres.                                                                          |  2   |  D/V  |
| 1.5.2 | Bekreft at slektslinjeposter er uforanderlige, sikkert lagret og tilgjengelige for revisjoner.                                                                                                                            |  2   |  D/V  |
| 1.5.3 | Verifiser at sporing av opprinnelse dekker syntetiske data generert via personvernbevarende eller generative teknikker, og at all syntetisk data er tydelig merket og skillelig fra ekte data gjennom hele prosessflyten. |  2   |  D/V  |

---

## Referanser

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [EU AI Act – Article 10: Data & Data Governance](https://artificialintelligenceact.eu/article/10/)
* [CISA Advisory: Securing Data for AI Systems](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [OpenAI Privacy Center – Data Deletion Controls](https://privacy.openai.com/policies?modal=take-control)

