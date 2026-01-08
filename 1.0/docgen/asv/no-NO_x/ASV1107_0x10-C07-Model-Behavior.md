# C7 Modellatferd, Utgangskontroll og Sikkerhetsikring

## Kontrollmål

Denne kontrollkategorien sikrer at modellutdata er teknisk begrenset, validert og overvåket slik at usikre, feilaktige eller høyrisiko svar ikke kan nå brukere eller etterfølgende systemer.

---

## C7.1 Håndhevelse av utdataformat

Sørg for at modellen leverer data på en måte som bidrar til å forhindre injeksjon.

|   #   | Beskrivelse                                                                                                                                                               | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 7.1.1 | Bekreft at applikasjonen validerer alle modellutdata mot et strengt skjema (som JSON Schema) og avviser alle utdata som ikke samsvarer.                                   |  1   |  D/V  |
| 7.1.2 | Bekreft at systemet bruker "stop sequences" eller tokengrenser for å strengt avbryte genereringen før det kan føre til bufferoverløp eller utføre utilsiktede kommandoer. |  1   |  D/V  |
| 7.1.3 | Sørg for at komponenter som behandler modellutdata, håndterer dem som utrygge inndata (f.eks. ved å bruke parameteriserte spørringer eller sikre deserialisatorer).       |  2   |  D/V  |
| 7.1.4 | Bekreft at systemet logger den spesifikke feiltypen når et utdata avvises på grunn av dårlig formatering.                                                                 |  3   |   V   |

---

## C7.2 Hallusinasjonsdeteksjon og -demping

Oppdag når modellen er usikker eller lyver, og stopp den informasjonen fra å nå brukeren.

|   #   | Beskrivelse                                                                                                                                       | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 7.2.1 | Bekreft at systemet beregner en numerisk konfidensscore (for eksempel ved bruk av log-sannsynligheter) for genererte svar.                        |  1   |  D/V  |
| 7.2.2 | Bekreft at applikasjonen automatisk blokkerer svar eller bytter til en reservemelding hvis konfidenspoengsummen faller under en definert terskel. |  1   |  D/V  |
| 7.2.3 | Bekreft at hallusinasjonshendelser (svar med lav tillit) logges med inngangs-/utgangsmetadata for analyse.                                        |  2   |  D/V  |

---

## C7.3 Utgangssikkerhet og personvernfiltrering

Tekniske kontroller for å oppdage og fjerne skadelig innhold før det vises til brukeren.

|   #   | Beskrivelse                                                                                                                                       | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 7.3.1 | Bekreft at automatiserte klassifiserere skanner hvert svar og blokkerer innhold som matcher kategorier for hat, trakassering eller seksuell vold. |  1   |  D/V  |
| 7.3.2 | Bekreft at systemet skanner hvert svar for PII (som kredittkort eller e-poster) og automatisk skjuler det før visning.                            |  1   |  D/V  |
| 7.3.3 | Bekreft at data merket som "konfidensiell" i systemet forblir blokkert eller sensurert.                                                           |  2   |   D   |
| 7.3.4 | Bekreft at systemet krever et menneskelig godkjenningssteg eller re-autentisering dersom modellen genererer høy-risiko innhold.                   |  3   |  D/V  |
| 7.3.5 | Bekreft at sikkerhetsfiltre kan konfigureres forskjellig basert på brukerens rolle eller lokasjon (f.eks. strengere filtre for mindreårige).      |  3   |  D/V  |

---

## C7.4 Begrensning av utdata og handlinger

Forhindre at modellen gjør for mye, for raskt, eller får tilgang til ting den ikke skal.

|   #   | Beskrivelse                                                                                                                                                       | Nivå | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 7.4.1 | Bekreft at systemet håndhever faste grenser for forespørsler og tokens per bruker for å forhindre kostnadstopper og tjenestenekt.                                 |  1   |   D   |
| 7.4.2 | Bekreft at modellen ikke kan utføre handlinger med stor påvirkning (som å skrive filer, sende e-post eller kjøre kode) uten eksplisitt brukerbekreftelse.         |  1   |  D/V  |
| 7.4.3 | Bekreft at agentrammeverket eksplisitt konfigurerer og håndhever maksimal dybde for rekursive kall, delegasjonsgrenser, og listen over tillatte eksterne verktøy. |  2   |   D   |

---

## C7.5 Forklarbarhet og Gjennomsiktighet

Sørg for at brukeren vet hvorfor en beslutning ble tatt.

|   #   | Beskrivelse                                                                                                                     | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 7.5.1 | Bekreft at brukergrensesnittet viser en konfidenspoengsum eller "begrunnelsessammendrag" til brukeren for kritiske avgjørelser. |  2   |  D/V  |
| 7.5.2 | Bekreft at forklaringer gitt til brukeren er renset for å fjerne systeminstrukser eller bakgrunnsdata.                          |  2   |  D/V  |
| 7.5.3 | Bekreft at tekniske bevis for modellens avgjørelse (som oppmerksomhetskart eller log-sannsynligheter) blir loggført.            |  3   |   D   |

---

## C7.6 Overvåkingsintegrasjon

Sørg for at applikasjonen sender de riktige signalene for sikkerhetsteamene å overvåke.

|   #   | Beskrivelse                                                                                                                               | Nivå | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 7.6.1 | Verifiser at systemet logger sanntidsmetrikker for sikkerhetsbrudd (f.eks. "Hallusinasjon oppdaget", "PII blokkert").                     |  1   |   D   |
| 7.6.2 | Bekreft at systemet utløser en alarm hvis sikkerhetsovertredelsesraten overskrider et definert terskelnivå innenfor et bestemt tidsvindu. |  1   |   V   |
| 7.6.3 | Verifiser at logger inkluderer den spesifikke modellversjonen og andre detaljer som er nødvendige for å undersøke potensiell misbruk.     |  2   |   V   |

---

## 7.7 Generative mediesikringer

Forhindre opprettelsen av ulovlig eller falsk media.

|   #   | Beskrivelse                                                                                                                    | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 7.7.1 | Bekreft at systemet nekter å generere medier (bilder/lyd) som skildrer ekte personer uten verifisert samtykke.                 |  1   |  D/V  |
| 7.7.2 | Bekreft at inndatafiltre blokkerer forespørsler om eksplisitt eller deepfake-innhold før modellen behandler dem.               |  2   |  D/V  |
| 7.7.3 | Bekreft at systemet kontrollerer generert innhold for brudd på opphavsrett før det frigjøres.                                  |  2   |   V   |
| 7.7.4 | Bekreft at alt generert medie inkluderer et usynlig vannmerke eller kryptografisk signatur for å bevise at det er AI-generert. |  3   |  D/V  |
| 7.7.5 | Bekreft at forsøk på å omgå filtre blir oppdaget og loggført som sikkerhetshendelser.                                          |  3   |   V   |

## Referanser

* [OWASP Top 10 for LLMs: LLM07: Insecure Output Handling](https://owasp.org/www-project-top-10-for-large-language-model-applications/#llm07-insecure-output-handling)

