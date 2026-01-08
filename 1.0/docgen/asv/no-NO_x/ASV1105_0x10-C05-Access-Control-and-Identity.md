# C5 Tilgangskontroll og identitet for AI-komponenter og brukere

## Kontrollmål

Effektiv tilgangskontroll for AI-systemer krever robust identitetsforvaltning, kontekstbevisst autorisasjon og håndheving i sanntid i tråd med prinsippene for nulltillit. Disse kontrollene sikrer at mennesker, tjenester og autonome agenter kun interagerer med modeller, data og beregningsressurser innenfor eksplisitt godkjente områder, med kontinuerlig verifisering og revisjonsmuligheter.

---

## C5.1 Identitetsstyring og autentisering

Etabler kryptografisk støttede identiteter for alle enheter med multifaktorautentisering.

|   #   | Beskrivelse                                                                                                                                                                                                                  | Nivå | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 5.1.1 | Bekreft at alle menneskelige brukere og tjenesteprinsipper autentiserer gjennom en sentralisert bedriftsidentitetsleverandør (IdP) ved bruk av OIDC- og/eller SAML-protokoller.                                              |  1   |  D/V  |
| 5.1.2 | Bekreft at høy-risiko operasjoner (modellutrulling, eksport av vekter, tilgang til treningsdata, endringer i produksjonskonfigurasjon) krever flerfaktorautentisering eller trinnvis autentisering med sesjonsre-validering. |  1   |  D/V  |
| 5.1.3 | Verifiser at fødererte AI-agenter autentiserer via signerte JWT-påstander som har en maksimal levetid på 24 timer og inkluderer kryptografisk bevis på opprinnelse.                                                          |  3   |  D/V  |

---

## C5.2 Autorisasjon og policy

Implementer tilgangskontroller for alle AI-ressurser med eksplisitte tillatelsesmodeller og revisjonsspor.

|   #   | Beskrivelse                                                                                                                                                                                                                        | Nivå | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 5.2.1 | Bekreft at alle AI-ressurser (datasett, modeller, endepunkter, vektorsamlinger, innebygde indekser, beregningsinstanser) håndhever rollebaserte tilgangskontroller med eksplisitte tillatelseslister og standard avvisningsregler. |  1   |  D/V  |
| 5.2.2 | Verifiser at alle endringer i tilgangskontroll logges uforanderlig med tidsstempler, aktøridentiteter, ressursidentifikatorer og tillatelsesendringer.                                                                             |  1   |   V   |
| 5.2.3 | Bekreft at dataklassifiseringsetiketter (PII, PHI, proprietær, osv.) automatisk overføres til avledede ressurser (innbeddinger, hurtigbuffer for prompt, modellutdata).                                                            |  2   |   D   |
| 5.2.4 | Bekreft at uautoriserte tilgangsforsøk og hendelser med eskalering av rettigheter utløser sanntidsvarsler med kontekstuell metadata.                                                                                               |  2   |  D/V  |
| 5.2.5 | Bekreft at autorisasjonsbeslutninger er eksternt håndtert av en dedikert policy-motor (OPA, Cedar eller tilsvarende).                                                                                                              |  1   |  D/V  |
| 5.2.6 | Bekreft at policyer evaluerer dynamiske attributter ved kjøretid, inkludert brukerrolle eller -gruppe, ressursklassifisering, forespørselskontekst, leietakerisolasjon og tidsmessige begrensninger.                               |  1   |  D/V  |
| 5.2.7 | Bekreft at policyens hurtigbuffer levetid (TTL) ikke overstiger 5 minutter for høysensitive ressurser og 1 time for standardressurser med muligheter for hurtigbufferinvalidering.                                                 |  3   |  D/V  |

---

## C5.3 Sikkerhetshåndheving ved spørringstidspunktet

Implementer sikkerhetskontroller på databasenivå med obligatorisk filtrering og sikkerhetspolicyer på radnivå.

|   #   | Beskrivelse                                                                                                                                                                              | Nivå | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 5.3.1 | Verifiser at alle spørringer mot vektordatabasen og SQL inkluderer obligatoriske sikkerhetsfiltre (leietaker-ID, sensitivitetsetiketter, brukerscope) som håndheves på databasmotornivå. |  1   |  D/V  |
| 5.3.2 | Bekreft at policyer for radnivåsikkerhet og maskering på feltnivå er aktivert med policyarv for alle vektordatabaser, søkeindekser og treningsdatasett.                                  |  1   |  D/V  |
| 5.3.3 | Bekreft at mislykkede autorisasjonsvurderinger umiddelbart avbryter spørringer og returnerer eksplisitte autorisasjonsfeilkoder.                                                         |  2   |   D   |
| 5.3.4 | Bekreft at spørrings-omprøvingsmekanismer revurderer autorisasjonspolicyer for å ta hensyn til dynamiske endringer i tillatelser innenfor aktive brukersesjoner.                         |  3   |  D/V  |

---

## C5.4 Utdatafiltrering og datatapforebygging

Implementer etterbehandlingskontroller for å forhindre uautorisert dataeksponering i AI-generert innhold.

|   #   | Beskrivelse                                                                                                                                                                                       | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 5.4.1 | Verifiser at filtreringsmekanismer etter inferens skanner og redigerer uautorisert PII, klassifisert informasjon og proprietære data før innhold leveres til forespørselstellerne.                |  1   |  D/V  |
| 5.4.2 | Bekreft at sitater, referanser og kildehenvisninger i modellutdata blir verifisert mot innringerens rettigheter og fjernet dersom uautorisert tilgang oppdages.                                   |  1   |  D/V  |
| 5.4.3 | Bekreft at restriksjoner for utdataformat (rensemetodikk for PDF-er, metadata-fratrukne bilder, godkjente filtyper) blir håndhevet basert på brukerens tillatelsesnivåer og dataklassifiseringer. |  2   |   D   |

---

## C5.5 Fler-tenant isolasjon

Sikre kryptografisk og logisk isolasjon mellom leietakere i delt AI-infrastruktur.

|   #   | Beskrivelse                                                                                                                                                                                            | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 5.5.1 | Verifiser at minneområder, innebygde lagre, hurtigbufferoppføringer og midlertidige filer er navneområdeseparert per leietaker, med sikker sletting ved sletting av leietaker eller avslutning av økt. |  1   |  D/V  |
| 5.5.2 | Verifiser at hver API-forespørsel inneholder en autentisert leietakeridentifikator som er kryptografisk validert mot sesjonskontekst og brukertilganger.                                               |  1   |  D/V  |
| 5.5.3 | Bekreft at nettverkspolicyer implementerer standard-nekt regler for kommunikasjon på tvers av leietakere innen tjenestemesh og containerorkestreringsplattformer.                                      |  2   |   D   |
| 5.5.4 | Bekreft at krypteringsnøkler er unike per leietaker med støtte for kundestyrt nøkkel (CMK) og kryptografisk isolasjon mellom leietakerens datalagre.                                                   |  3   |   D   |

---

## C5.6 Autonom agentautorisering

Kontroller tillatelser for AI-agenter og autonome systemer gjennom avgrensede kapabilitetstoken og kontinuerlig autorisasjon.

|   #   | Beskrivelse                                                                                                                                                                             | Nivå | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 5.6.1 | Bekreft at autonome agenter mottar avgrensede kapabilitetstokener som eksplisitt angir tillatte handlinger, tilgjengelige ressurser, tidsbegrensninger og driftsmessige begrensninger.  |  1   |  D/V  |
| 5.6.2 | Bekreft at høy-risiko funksjoner (filsystemtilgang, kodeutførelse, eksterne API-kall, finansielle transaksjoner) er deaktivert som standard og krever eksplisitt godkjenning.           |  1   |  D/V  |
| 5.6.3 | Verifiser at kapabilitetstokener er bundet til brukersesjoner, inkluderer kryptografisk integritetsbeskyttelse, og sørg for at de ikke kan lagres eller gjenbrukes i offline-scenarier. |  2   |   D   |
| 5.6.4 | Bekreft at agentinitierte handlinger gjennomgår autorisasjon via en ABAC-policy motor.                                                                                                  |  2   |   V   |

---

## Referanser

* [NIST SP 800-162: Guide to Attribute Based Access Control (ABAC)](https://csrc.nist.gov/pubs/sp/800/162/final)
* [NIST SP 800-207: Zero Trust Architecture](https://csrc.nist.gov/pubs/sp/800/207/final)
* [NIST SP 800-63-3: Digital Identity Guidelines](https://csrc.nist.gov/pubs/sp/800/63/3/final)
* [NIST IR 8360: Machine Learning for Access Control Policy Verification](https://csrc.nist.gov/pubs/ir/8360/final)

